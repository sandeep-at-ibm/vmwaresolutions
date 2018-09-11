---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-13"

---

# Progettazione della gestione dell'infrastruttura

La gestione dell'infrastruttura si riferisce ai componenti che stanno gestendo l'infrastruttura VMware. Questa progettazione utilizza una singola istanza PSC (Platform Services Controller) esterna e una singola istanza vCenter Server:
* vCenter Server è la piattaforma centralizzata per la gestione degli ambienti vSphere ed è uno dei componenti fondamentali di questa soluzione.
* Il PSC viene utilizzato in questa soluzione per fornire una serie di servizi di infrastruttura tra cui VMware vCenter Single Sign On, il servizio di licenza, il servizio di ricerca e VMware Certificate Authority.

Le istanze PSC e le istanze vCenter Server sono macchine virtuali (VM) separate.

## Progettazione di PSC

Questa progettazione distribuisce un singolo PSC esterno come dispositivo virtuale su una sottorete portatile nella VLAN privata associata alle VM di gestione. Il suo gateway predefinito è impostato sul BCR (back-end customer router). Il dispositivo virtuale è configurato con le specifiche indicate nella seguente tabella.

**Nota**: questi valori vengono impostati al momento della distribuzione e non possono essere modificati.

Tabella 1. Specifiche del PSC (Platform Services Controller)

| Attributo                    | Specifica                  |
|------------------------------|--------------------------------|
| Platform Services Controller | Dispositivo virtuale              |
| Numero di vCPU              | 2                              |
| Memoria                       | 4 GB                           |
| Disco                         | 114 GB sull'archivio dati VMFS locale |
| Tipo di disco                    | Thin provisioned               |

Al PSC che si trova nell'istanza primaria viene assegnato il dominio SSO predefinito `vsphere.local`.

## Progettazione di vCenter Server

Anche vCenter Server viene distribuito come dispositivo virtuale. Inoltre, vCenter Server viene installato su una sottorete portatile nella VLAN privata associata alle VM di gestione. Il suo gateway predefinito è impostato sull'indirizzo IP assegnato sul BCR per quella particolare sottorete. Il dispositivo virtuale è configurato con le specifiche indicate nella seguente tabella.

Tabella 2. Specifiche di vCenter Server Appliance

| Attributo                    | Specifica                       |
|------------------------------|-------------------------------------|
| vCenter Server               | Dispositivo virtuale                   |
| Dimensione installazione del dispositivo  | Media (fino a 400 host, 4.000 VM) |
| Platform Services Controller | Esterno                            |
| Numero di vCPU              | 8                                   |
| Memoria                       | 24 GB                               |
| Disco                         | 400 GB sull'archivio dati locale           |
| Tipo di disco                    | Thin provisioned                    |

### Database vCenter Server

La configurazione di vCenter Server utilizza un database PostgreSQL integrato e locale incluso nel dispositivo. Il database integrato viene utilizzato per rimuovere eventuali dipendenze da database e licenze esterni.

### Specifica del cluster vCenter Server

Questa progettazione ti consente di raggruppare gli host vSphere ESXi forniti tramite la soluzione. Prima che i cluster possano essere creati, tuttavia, viene creato un oggetto data center che indica l'ubicazione degli host vSphere ESXi nonché il pod all'interno del data center. Un cluster viene creato dopo la creazione dell'oggetto data center. Il cluster viene distribuito con VMware vSphere High Availability (HA) e VMware vSphere Distributed Resource Scheduler (DRS) abilitati.

### vSphere Distributed Resource Scheduler

Questa progettazione utilizza vSphere Distributed Resource Scheduling (DRS) nel cluster iniziale per posizionare le VM e utilizza DRS nei cluster aggiuntivi per migrare dinamicamente le VM per ottenere dei cluster bilanciati. Il livello di automazione è impostato sull'automazione completa in modo che le raccomandazioni di posizionamento e migrazione iniziali vengano eseguite automaticamente da vSphere. Inoltre, la soglia di migrazione è impostata su moderata in modo che vCenter applichi le raccomandazioni di priorità 1, 2, 3 per ottenere almeno un miglioramento decente nel bilanciamento del carico del cluster.

**Nota:** in questa progettazione non viene utilizzato il risparmio energia tramite la funzione **Distributed Power Management**.

### vSphere High Availability

Questa progettazione utilizza vSphere High Availability (HA) nel cluster iniziale e nei cluster aggiuntivi per rilevare gli errori di calcolo e ripristinare le VM eseguite in un cluster. La funzione vSphere HA in questa progettazione è configurata con le opzioni **Host Monitoring** e **Admission Control** abilitate all'interno del cluster. Inoltre, il cluster iniziale prenota le risorse di un nodo come capacità di riserva per la politica di controllo di ammissione.

**Nota**: sei responsabile di regolare la politica di controllo di ammissione quando il cluster viene successivamente espanso o contratto.

Per impostazione predefinita, l'opzione **VM restart priority** è impostata su medio e l'opzione **Host isolation response** è disabilitata. Inoltre, **VM monitoring** è disabilitata e la funzione **Datastore Heartbeating** è configurata per includere uno qualsiasi degli archivi dati del cluster. Questo approccio utilizza, se presenti, gli archivi dati NAS.

## Automazione

Il punto cardine di queste soluzioni è l'automazione. L'automazione offre i seguenti vantaggi:
* Riduce la complessità della distribuzione.
* Riduce drasticamente i tempi di distribuzione.
* Garantisce che l'istanza VMware sia distribuita in modo coerente.

Le VM {{site.data.keyword.IBM}} CloudBuilder, IBM CloudDriver e SDDC Manager lavorano insieme per presentare una nuova istanza VMware ed eseguire funzioni di gestione del ciclo di vita.

### IBM CloudBuilder e IBM CloudDriver

Le VSI (Virtual Server Instance) IBM CloudBuilder e IBM CloudDriver sono componenti sviluppati da IBM a cui non puoi accedere.
* IBM CloudBuilder è una VSI (Virtual Server Instance) {{site.data.keyword.cloud_notm}} temporanea che avvia la distribuzione, la configurazione e la convalida dei componenti della soluzione all'interno degli host ESXi bare metal forniti.
* La VSI IBM CloudDriver viene distribuita per la creazione di istanze e periodicamente, se necessario, con il codice di {{site.data.keyword.cloud_notm}} for VMware più recente per operazioni come la distribuzione di nodi, cluster o servizi aggiuntivi. IBM CloudDriver comunica con la console {{site.data.keyword.vmwaresolutions_short}} attraverso un gateway dei servizi edge VMware NSX distribuito esclusivamente per scopi di gestione dell'istanza e funge da agent per la manutenzione dell'istanza. IBM CloudDriver è responsabile delle azioni in corso, come l'aggiunta di nuovi host bare metal al cluster e la distribuzione di servizi aggiuntivi nell'istanza. Per le istanze Cloud Foundation, IBM CloudDriver comunica con la VM VMware SDDC Manager per eseguire funzioni come l'aggiunta di host e l'applicazione di patch.

È possibile che l'utente elimini o danneggi le VM descritte nelle seguenti sezioni. Quando una VM viene rimossa, arrestata o diventa inutilizzabile, sulla console {{site.data.keyword.vmwaresolutions_short}} vengono interrotte le seguenti operazioni di Cloud Foundation o vCenter Server:
* Visualizzazione dello stato di istanze o host
* Aggiunta o rimozione di cluster
* Aggiunta o rimozione di host ESXi
* Aggiunta o rimozione di servizi
* Installazione di patch

### SDDC Manager

Per le istanze Cloud Foundation, la VM SDDC Manager è un componente sviluppato e gestito da VMware. Rimane come parte dell'istanza durante tutto il suo ciclo di vita. È responsabile delle seguenti funzioni del ciclo di vita delle istanze:
* Gestione dei componenti VMware: vCenter Server, PSC (Platform Services Controller), vSAN e NSX, compresa l'assegnazione degli indirizzi IP e la risoluzione del nome host.
* Espansione e rimozione degli host ESXi all'interno del cluster, inclusi eventuali servizi interessati, quali VTEP NSX, vSAN, pool di risorse.

Per le istanze vCenter Server, queste attività vengono eseguite da IBM CloudDriver in quanto non esiste alcun SDDC Manager.

### Flusso di automazione

La seguente procedura descrive l'ordine degli eventi quando si ordina un'istanza VMware tramite la console {{site.data.keyword.vmwaresolutions_short}}:
1.  Ordine di VLAN e sottoreti per la rete da {{site.data.keyword.cloud_notm}}.
2.  Ordine di {{site.data.keyword.baremetal_short}} con vSphere Hypervisor installato.
3.  Se applicabile, ordine della VSI (Virtual Server Instance) di Microsoft Windows da utilizzare come controller di dominio Active Directory.
4.  Convalida della rete e dell'hardware distribuito.
5.  Se applicabile, configurazione iniziale di vSAN a singolo nodo.
6.  Se applicabile, distribuzione e configurazione di due macchine virtuali Microsoft Windows da utilizzare come controller di dominio Active Directory.
7.  Distribuzione e configurazione di vCenter, PSC e NSX.
8.  Clustering dei nodi ESXi rimanenti, espansione di vSAN (se applicabile) e configurazione dei componenti NSX (VTEP).
9.  Distribuzione della VM SDDC Manager di VMware Cloud Foundation, se applicabile, e della VSI IBM CloudDriver.
10.  Convalida dell'installazione e della configurazione dell'ambiente.
11. Rimozione della VSI CloudBuilder.
12. Distribuzione di servizi facoltativi, come il server di backup e l'archiviazione.

### Link correlati

* [Progettazione dell'infrastruttura fisica](design_physicalinfrastructure.html)
* [Progettazione dell'infrastruttura virtuale](design_virtualinfrastructure.html)
* [Progettazione di servizi comuni](design_commonservice.html)

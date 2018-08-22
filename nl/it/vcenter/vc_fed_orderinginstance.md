---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Ordine di istanze VMware Federal

Per distribuire una piattaforma virtualizzata VMware flessibile e personalizzabile che soddisfi al meglio le tue esigenze del carico di lavoro, ordina un'istanza VMware Federal che ti consente di disconnettere la connessione di gestione aperta e proteggere la tua istanza distribuita.

**Nota:** al momento, solo le istanze vCenter Server supportano VMware Federal on {{site.data.keyword.cloud}}.

## Requisiti

Assicurati di aver completato le seguenti attività:
* Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](../vmonic/useraccount.html).
* Hai esaminato le informazioni in [Requisiti e pianificazione per le istanze VMware Federal](vc_fed_planning.html).
* Hai esaminato il formato del nome di istanza e di dominio. Il nome del dominio e l'etichetta del dominio secondario vengono utilizzati per generare il nome utente e i nomi server dell'istanza.

Tabella 1. Formato del valore per i nomi di istanza e di dominio

| Nome        | Formato del valore      |
  |:------------- |:------------- |
  | Nome dominio | `<root_domain>` |  
  | Nome utente di accesso vCenter Server | `<user_id>@<root_domain>` (utente di Microsoft Active Directory) o `administrator@vsphere.local` |
  | Dome di dominio completo vCenter Server | `vcenter.<subdomain_label>.<root_domain>`. La lunghezza massima è di 50 caratteri. |
  | Nome del sito SSO (Single Sign-On) | `<subdomain_label>` |
  | Nome completo server ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove `<n>` è la sequenza del server ESXi. La lunghezza massima è di 50 caratteri. |  
  | Nome di dominio completo PSC | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. La lunghezza massima è di 50 caratteri. |

**Importante**: non modificare alcun valore che è stato impostato durante l'ordine e la distribuzione dell'istanza. Ciò potrebbe comportare l'inutilizzabilità dell'istanza. Ad esempio, la rete pubblica potrebbe arrestarsi, i server e le VSI (Virtual Server Instance) potrebbero spostarsi dietro Vyatta quando è in corso il provisioning o la VSI di IBM CloudBuilder potrebbe interrompersi o essere eliminata.

## Impostazioni di sistema

Quando ordini un'istanza VMware Federal, devi specificare le seguenti impostazioni di sistema.

### Nome istanza

Il nome dell'istanza deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome dell'istanza deve iniziare e terminare con un carattere alfanumerico.
* La lunghezza massima del nome dell'istanza è di 10 caratteri.
* Il nome dell'istanza deve essere univoco all'interno del tuo account.

### Primaria o secondaria

Ordina una nuova istanza primaria. La distribuzione di un'istanza secondaria per l'alta disponibilità non è attualmente supportata.

## Impostazioni di licenza

Licenze VMware fornite da IBM per i seguenti componenti:

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Base, Advanced o Enterprise) 6.4
* (Per i cluster vSAN) VMware vSAN Advanced o Enterprise 6.6

**Attenzione:**

* Le edizioni minime della licenza sono indicate sull'interfaccia utente. Se sono supportate edizioni diverse per i componenti, puoi selezionare l'edizione che vuoi. Sei responsabile di garantire che la chiave di licenza fornita sia corretta per ogni componente VMware selezionato.
* Per vSphere, al momento dell'ordine verrà addebitato un costo di licenza, ma tale costo verrà successivamente accreditato sul tuo account.

## Impostazioni di Bare Metal Server

Le impostazioni Bare Metal si basano sulla tua configurazione personalizzata. L'opzione per selezionare una configurazione preconfigurata non è attualmente supportata.

### Ubicazione data center

Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui deve essere ospitata l'istanza.

### Personalizzato

Specifica il modello di CPU e la RAM per il Bare Metal Server.

Tabella 2. Opzioni per i {{site.data.keyword.baremetal_short}} personalizzati

| Opzioni CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Numero di server Bare Metal

Puoi configurare il numero di server ESXi nell'intervallo 2 - 20.

Tutti i server ESXi condividono la stessa configurazione. Nella post distribuzione, puoi aggiungere altri quattro cluster. Per le impostazioni di archiviazione vSAN, sono richiesti 4 server ESXi per i cluster iniziali e di post-distribuzione. Per ulteriori informazioni sul numero minimo di server ESXi, vedi [Un'istanza vCenter Server a due nodi è altamente disponibile?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Impostazioni di archiviazione

Le impostazioni di archiviazione si basano sulla tua selezione della configurazione Bare Metal Server e sul tipo di archiviazione.

### Archiviazione vSAN

Per vSAN, specifica le seguenti opzioni di archiviazione:

* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona la capacità che soddisfa le tue esigenze di archiviazione condivisa.
* **Numero di dischi vSAN**: seleziona il numero di dischi per l'archiviazione condivisa vSAN che vuoi aggiungere. Le quantità dei dischi devono essere 2, 4, 6 o 8.
* Seleziona l'edizione della licenza VMware vSAN 6.6 (Advanced o Enterprise).

### Archiviazione NFS

Se selezioni **Storage NFS**, puoi aggiungere l'archiviazione condivisa a livello di file per la tua istanza in cui tutte le condivisioni utilizzano le stesse impostazioni o puoi specificare impostazioni di configurazione diverse per ogni condivisione file. Specifica le seguenti opzioni NFS:

**Nota:** il numero di condivisioni file deve essere compreso tra 1 e 32.

* **Configura le condivisioni singolarmente**: seleziona questa opzione per specificare diverse impostazioni di configurazione per ogni condivisione file.
* **Numero di condivisioni**: quando utilizzi la stessa impostazione di configurazione per ogni condivisione file, specifica il numero di condivisioni file per l'archiviazione condivisa NFS che vuoi aggiungere.
* **Dimensione**: seleziona la capacità che soddisfa le tue esigenze di archiviazione condivisa.
* **Prestazioni**: seleziona l'IOPS (Input/output Operations Per Second) per GB in base ai tuoi requisiti del carico di lavoro.
* **AGGIUNGI NFS**: seleziona questa opzione per aggiungere singole condivisioni file che utilizzano impostazioni di configurazione diverse.

Tabella 3. Opzioni del livello di prestazioni NFS

| Opzione        | Dettagli       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Questa opzione è progettata per i carichi di lavoro più generici. Applicazioni di esempio includono: hosting di piccoli database, backup di applicazioni web o immagini disco di macchine virtuali per un hypervisor. |
  | 4 IOPS/GB | Questa opzione è progettata per i carichi di lavoro ad alta intensità che hanno un'alta percentuale di dati attivi alla volta. Applicazioni di esempio includono: database transazionali. |
  | 10 IOPS/GB | Questa opzione è progettata per i tipi di carichi di lavoro più impegnativi, come l'analisi. Applicazioni di esempio includono: database ad alte transazioni e altri database sensibili alle prestazioni. Questo livello di prestazioni è limitato a una capacità massima di 4 TB per condivisione file. |

## Impostazioni dell'interfaccia di rete

### Prefisso nome host

Il prefisso del nome host deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  Il prefisso del nome host deve iniziare e terminare con un carattere alfanumerico.
*  La lunghezza massima del prefisso del nome host è di 10 caratteri.

### Etichetta dominio secondario

L'etichetta del dominio secondario deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  L'etichetta del dominio secondario deve iniziare e terminare con un carattere alfanumerico.
*  La lunghezza massima dell'etichetta del dominio secondario è di 10 caratteri.
*  L'etichetta del dominio secondario deve essere univoca all'interno del tuo account.

### Nome dominio

Il nome del dominio root deve rispettare i seguenti requisiti:
* Il nome del dominio deve essere composto da due o più stringhe separate da un punto (.)
* La prima stringa deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* Tutte le stringhe, tranne l'ultima, possono contenere solo caratteri alfanumerici e trattini (-).
* L'ultima stringa può contenere solo caratteri alfabetici.
* La lunghezza dell'ultima stringa deve essere compresa tra 2 e 24 caratteri.

**Nota:** la lunghezza massima del nome di dominio completo (FQDN) per gli host e le VM (macchine virtuali) è di 50 caratteri. I nomi di dominio devono essere adattati a questa lunghezza massima.

### Configurazione DNS

Seleziona la configurazione DNS (Domain Name System) per la tua istanza:

* **Singola VSI Windows pubblica per Active Directory/DNS**: viene distribuita una singola VSI di Microsoft Windows Server per Microsoft Active Directory (AD) consultabile, che funziona come DNS per l'istanza in cui sono registrati gli host e le macchine virtuali.
* **Due VM di Windows Server dedicate e altamente disponibili sul cluster di gestione**: per le release della V2.3 e versioni future, vengono distribuite due macchine virtuali di Microsoft Windows, che aiutano a migliorare la sicurezza e la solidità.

**Importante:** se configuri la tua istanza per utilizzare le due macchine virtuali Microsoft Windows, devi fornire due licenze di Microsoft Windows Server 2012 R2. Utilizza la licenza di Microsoft Windows Server 2012 R2 Standard Edition e/o la licenza di Microsoft Windows Server 2012 R2 Datacenter Edition.

Attualmente, ciascuna licenza può essere assegnata a un solo server fisico e copre fino a due processori fisici. Una licenza Standard Edition è in grado di eseguire due macchine virtuali Microsoft Windows virtualizzate per ogni server con 2 processori. Pertanto, sono necessarie due licenze poiché due macchine virtuali Microsoft Windows sono distribuite in due host diversi.

Hai 30 giorni per attivare le macchine virtuali.

Per ulteriori informazioni su come ordinare le licenze di Windows, vedi la [documentazione di Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Riepilogo ordine

In base alla configurazione che hai selezionato per l'istanza, il costo stimato viene generato e visualizzato immediatamente nella sezione **Riepilogo ordine** nel riquadro di destra. Fai clic su **Dettagli dei prezzi** nella parte inferiore del riquadro di destra per generare un documento PDF che fornisce i dettagli della stima.

## Procedura

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e quindi su **vCenter Server** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vCenter Server on IBM Cloud**, fai clic sulla scheda **vCenter Server** e quindi su **Crea**.
3. Nella pagina **vCenter Server**, immetti il nome dell'istanza.
4. Fai clic su **Istanza primaria** per distribuire una singola istanza nell'ambiente.
5. Specifica l'edizione della licenza VMware NSX.
6. Completa la configurazione di Bare Metal Server:
  1. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.
  2. Seleziona il modello CPU **Personalizzato** e la quantità di **RAM**.
7. Completa la configurazione di archiviazione.
  * Se selezioni **Storage vSAN**, specifica il **Tipo e dimensioni del disco per i dischi vSAN**, il **Numero di dischi vSAN** e come la **Licenza vSAN** deve essere fornita.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le stesse impostazioni per tutte le condivisioni file, specifica il **Numero di condivisioni**, la **Dimensione** e le **Prestazioni**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le condivisioni file singolarmente, seleziona **Configura condivisioni singolarmente**, fai clic sull'icona **+** accanto all'etichetta **Aggiungi NFS** e seleziona la **Dimensione** e le **Prestazioni** per ogni singola condivisione file. Devi selezionare almeno una condivisione file.
8. Completa la configurazione dell'interfaccia di rete.
   1. Immetti il prefisso del nome host, l'etichetta del dominio secondario e il nome del dominio root.
   2. Seleziona la configurazione DNS.
9. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
   1. Esamina le impostazioni per l'istanza.
   2. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di ordinare l'istanza.
   3. Rivedi il costo stimato dell'istanza facendo clic sul link del costo sotto **Calcola costo**. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   4. Fai clic su **Fornitura**.

## Risultati

La distribuzione dell'istanza inizia automaticamente. Riceverai la conferma che l'ordine è in fase di elaborazione e puoi controllare lo stato della distribuzione visualizzando i dettagli dell'istanza.

Una volta che l'istanza è stata distribuita correttamente, i componenti descritti in [Specifiche tecniche per le istanze VMware Federal on {{site.data.keyword.cloud_notm}}](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances) vengono installati sulla tua piattaforma virtuale VMware. I server ESXi che hai ordinato vengono raggruppati come **cluster1** per impostazione predefinita.

Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e riceverai una notifica via e-mail.

## Operazioni successive

Visualizza, gestisci o proteggi l'istanza VMware Federal che hai ordinato.

**Importante:** devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console.
Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.

**ATTENZIONE:** la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}} (installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza) dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante la rimozione di server ESXi
*  Spegnimento dei componenti

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

### Link correlati

* [Registrazione di un account {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Visualizzazione delle istanze VMware Federal](vc_fed_viewinginstance.html)
* [Espansione e contrazione della capacità per le istanze VMware Federal](vc_fed_addingremovingservers.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze VMware Federal](fed_addviewdeleteclusters.html)
* [Protezione di istanze VMware Federal](vc_fed_securinginstance.html)
* [Eliminazione di istanze VMware Federal](vc_fed_deletinginstance.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)

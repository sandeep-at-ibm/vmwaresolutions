---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di istanze vCenter Server
{: #vc_orderinginstance}

Per distribuire una piattaforma virtualizzata VMware flessibile e personalizzabile che soddisfi al meglio le tue esigenze del carico di lavoro, ordina un'istanza VMware vCenter Server. Durante l'ordine iniziale, puoi anche aggiungere servizi, come [Zerto on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) per il ripristino di emergenza.

## Requisiti
{: #vc_orderinginstance-req}

Assicurati di aver completato le seguenti attività:
* Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Gestione di account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Hai esaminato le informazioni in [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).
* Hai esaminato il formato del nome di istanza e di dominio. Il nome del dominio e l'etichetta del dominio secondario vengono utilizzati per generare il nome utente e i nomi server dell'istanza.

Tabella 1. Formato del valore per i nomi di istanza e di dominio

| Nome        | Formato del valore      |
  |:------------|:------------ |
  | Nome dominio | `<root_domain>` |  
  | Nome utente di accesso vCenter Server | `<user_id>@<root_domain>` (utente di Microsoft Active Directory) o `administrator@vsphere.local` |
  | Dome di dominio completo vCenter Server (con PSC integrato) | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. La lunghezza massima è di 50 caratteri. |
  | Nome del sito SSO (Single Sign-On) | `<subdomain_label>` |
  | Nome completo server ESXi | `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove `<n>` è la sequenza del server ESXi. La lunghezza massima è di 50 caratteri. |

Non modificare alcun valore impostato durante l'ordine o la distribuzione dell'istanza. La modifica può rendere inutilizzabile la tua istanza. Ad esempio, se la rete pubblica si interrompe, se i server e le VSI (Virtual Server Instance) vanno dietro una fornitura media di Vyatta o se la VSI di IBM CloudBuilder si arresta o viene eliminata.
{:important}

## Impostazioni di sistema
{: #vc_orderinginstance-sys-settings}

Quando ordini un'istanza vCenter Server, devi specificare le seguenti impostazioni di sistema.

### Nome istanza
{: #vc_orderinginstance-inst-name}

Il nome dell'istanza deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome dell'istanza deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* La lunghezza massima del nome dell'istanza è di 10 caratteri.
* Il nome dell'istanza deve essere univoco all'interno del tuo account.

### Licenze VMware vSphere
{: #vc_orderinginstance-vsphere-license}

Seleziona se ordinare vSphere Enterprise Plus 6.7u1 o vSphere Enterprise Plus 6.5u2.

vSphere Enterprise Plus 6.7u1 è disponibile solo per {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Broadwell e Skylake.
{:note}

### Primaria o secondaria
{: #vc_orderinginstance-primary-secondary}

Scegli se ordinare un nuova istanza primaria o un'istanza secondaria per un'istanza primaria esistente.

## Impostazioni di licenza
{: #vc_orderinginstance-licensing-settings}

Specifica le opzioni di licenza per i seguenti componenti VMware nell'istanza:
* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 o 6.7
* NSX Service Providers 6.4 (Edizione Base, Advanced o Enterprise)

Per gli utenti Business Partner, la licenza vCenter Server (Standard edition), la licenza vSphere (Enterprise Plus edition) e la licenza NSX sono incluse e acquistate per tuo conto. Tuttavia, devi specificare l'edizione per la licenza NSX.

Per gli utenti non Business Partner, puoi utilizzare le licenze VMware fornite da IBM per questi componenti selezionando **Includi con l'acquisto** o puoi utilizzare l'opzione Bring Your Own License (BYOL) selezionando **Fornita dall'utente** e immettendo le tue chiavi di licenza.

### Note di licenza
{: #vc_orderinginstance-licensing-notes}

* È richiesta una licenza con un minimo di otto CPU, che è per quattro server con due CPU per ogni server. La scelta della licenza per ogni componente VMware si applica all'istanza di base e a qualsiasi server ESXi che aggiungi all'istanza in un secondo momento. Assicurati che la tua licenza supporti la futura espansione della capacità nella tua infrastruttura.
* Le edizioni minime della licenza sono indicate sull'interfaccia utente. Se sono supportate edizioni diverse per i componenti, puoi selezionare l'edizione che vuoi. Sei responsabile di garantire che la chiave di licenza fornita sia corretta per ogni componente VMware selezionato.
* Per vSphere, viene addebitato un costo di licenza al momento dell'ordine, ma tale costo viene poi accreditato sul tuo account.
* Puoi modificare le licenze che hai fornito utilizzando il client web VMware vSphere al termine della distribuzione dell'istanza.
* Il supporto per i componenti VMware per i quali fornisci le licenze è offerto da VMware, non dal supporto IBM.

## Impostazioni di Bare Metal Server
{: #vc_orderinginstance-bare-metal-settings}

Le impostazioni di Bare Metal sono basate sulla tua selezione del data center e sulla configurazione del server bare metal.

### Ubicazione data center
{: #vc_orderinginstance-dc-location}

Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui deve essere ospitata l'istanza.

### Skylake
{: #vc_orderinginstance-skylake}

Se selezioni **Skylake**, puoi scegliere la combinazione di CPU e RAM del Bare Metal Server in base alle tue esigenze.

Tabella 2. Opzioni per Skylake {{site.data.keyword.baremetal_short}}

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

### Certificato SAP
{: #vc_orderinginstance-sap}

Se selezioni **Certificato SAP**, non puoi modificare le impostazioni di CPU o RAM.

In base ai tuoi requisiti, seleziona una configurazione di Bare Metal Server:
  * Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 192 GB RAM
  * Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 384 GB RAM
  * Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2.3 GHz / 768 GB RAM
  * Processore Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz / 512 GB di RAM
  * Processore Quad Intel Xeon E7-8890 v4 / 96 core totali, 2,2 GHz / 1024 GB di RAM
  * Processore Quad Intel Xeon E7-8890 v4 / 96 core totali, 2,2 GHz / 2048 GB di RAM
  * Processore Quad Intel Xeon E7-8890 v4 / 96 core totali, 2,2 GHz / 4096 GB di RAM

### Broadwell
{: #vc_orderinginstance-broadwell}

Se selezioni **Broadwell**, puoi scegliere la combinazione di CPU e RAM del Bare Metal Server in base alle tue esigenze.

Tabella 3. Opzioni per Broadwell {{site.data.keyword.baremetal_short}}

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 core totali, 2,0 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 core totali, 2,1 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

### Numero di server Bare Metal
{: #vc_orderinginstance-bare-metal-number}

Per il cluster iniziale nell'istanza, puoi configurare il numero di server ESXi nell'intervallo 2 - 20. Tutti i server ESXi condividono la configurazione impostata.

Dopo la distribuzione iniziale, puoi aggiungere altri quattro cluster. Se hai selezionato la configurazione **Skylake** o **Broadwell** per VMware vSAN, sono richiesti 4 server ESXi per i cluster iniziali e di post-distribuzione. Per ulteriori informazioni sul numero minimo di server ESXi, vedi [Un'istanza vCenter Server a due nodi è altamente disponibile?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

## Impostazioni di archiviazione
{: #vc_orderinginstance-storage-settings}

Le impostazioni di archiviazione si basano sulla tua selezione della configurazione Bare Metal Server e sul tipo di archiviazione.

Per le istanze V2.8 e successive, puoi aggiungere delle condivisioni di archiviazione NFS a un cluster NFS o vSAN esistente. Per ulteriori informazioni, vedi la sezione *Aggiunta dell'archiviazione NFS alle istanze vCenter Server* in [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).
{:note}

### Archiviazione vSAN
{: #vc_orderinginstance-vsan-storage}

vSAN è disponibile solo per la configurazione Bare Metal **Skylake** e **Broadwell**. Specifica le seguenti opzioni vSAN:
* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona un'opzione per i dischi di capacità di cui hai bisogno.
* **Numero di dischi vSAN**: specifica il numero di dischi di capacità che vuoi aggiungere.
* Se vuoi aggiungere dischi di capacità oltre il limite di otto, seleziona la casella **Alte prestazioni con Intel Optane**. Questa opzione fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità ed è utile per i carichi di lavoro che richiedono meno latenza e una maggiore velocità IOPS.

  L'opzione **Alte prestazioni con Intel Optane** è disponibile solo per i modelli di CPI Skylake Dual Intel Xeon Gold 5120 e Dual Intel Xeon Gold 6140.
  {:note}

* Riesamina i valori di **Tipo di disco per i dischi cache vSAN** e **Numero di dischi cache vSAN**. Questi valori dipendono dalla selezione della casella **Alte prestazioni con Intel Optane**.
* **Licenza vSAN**: utilizza la licenza VMware fornita da IBM per il componente vSAN selezionando **Includi con l'acquisto** o utilizza l'opzione BYOL (Bring Your Own License) selezionando **Fornita dall'utente** e immettendo la tua chiave di licenza.

### Archiviazione NFS
{: #vc_orderinginstance-nfs-storage}

Se selezioni **Storage NFS**, puoi aggiungere l'archiviazione condivisa a livello di file per la tua istanza in cui tutte le condivisioni utilizzano le stesse impostazioni o puoi specificare impostazioni di configurazione diverse per ogni condivisione file. Specifica le seguenti opzioni NFS:

Il numero di condivisioni file deve essere compreso tra 1 e 32.
{:note}

* **Configura le condivisioni singolarmente**: seleziona questa opzione per specificare diverse impostazioni di configurazione per ogni condivisione file.
* **Numero di condivisioni**: quando utilizzi la stessa impostazione di configurazione per ogni condivisione file, specifica il numero di condivisioni file per l'archiviazione condivisa NFS che vuoi aggiungere.
* **Prestazioni**: seleziona l'IOPS (input/output operations per second) per GB in base ai tuoi requisiti del carico di lavoro.
* **Dimensione (GB)**: seleziona la capacità che soddisfa le tue esigenze di archiviazione condivisa.
* **Aggiungi storage condiviso**: seleziona questa opzione per aggiungere singole condivisioni file che utilizzano impostazioni di configurazione diverse.

Tabella 4. Opzioni del livello di prestazioni NFS

| Opzione        | Dettagli       |
  |:------------- |:------------- |
  | 0,25 IOPS/GB | Questa opzione è progettata per i carichi di lavoro che non vengono utilizzati spesso. Applicazioni di esempio includono: dati archiviati, hosting di database di grandi dimensioni con dati legacy o immagini di dischi virtuali del sistema di memoria virtuale come backup. |
  | 2 IOPS/GB | Questa opzione è progettata per i carichi di lavoro più generici. Applicazioni di esempio includono: hosting di piccoli database, backup di applicazioni web o immagini disco di VM (Virtual Machine) per un hypervisor. |
  | 4 IOPS/GB | Questa opzione è progettata per i carichi di lavoro ad alta intensità che hanno un'alta percentuale di dati attivi alla volta. Applicazioni di esempio includono: database transazionali. |
  | 10 IOPS/GB | Questa opzione è progettata per i tipi di carichi di lavoro più impegnativi, come l'analisi. Applicazioni di esempio includono: database ad alte transazioni e altri database sensibili alle prestazioni. Questo livello di prestazioni è limitato a una capacità massima di 4 TB per condivisione file. |

### Dischi locali
{: #vc_orderinginstance-local-disks}

L'opzione dischi locali è disponibile solo per la configurazione Bare Metal del processore Quad Intel Xeon E7-8890 v4 con **Certificato SAP**. Specifica le seguenti opzioni:
* **Numero di dischi**: seleziona il numero di dischi che vuoi aggiungere.
* **Tipo di disco**: seleziona un'opzione per il tipo di disco di cui hai bisogno.

## Impostazioni dell'interfaccia di rete
{: #vc_orderinginstance-network-interface-settings}

Quando ordini un'istanza vCenter Server, devi specificare le seguenti impostazioni dell'interfaccia di rete.

### Prefisso nome host
{: #vc_orderinginstance-host-name-prefix}

Il prefisso del nome host deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  Il prefisso del nome host deve iniziare e terminare con un carattere alfanumerico.
*  La lunghezza massima del prefisso del nome host è di 10 caratteri.

### Etichetta dominio secondario
{: #vc_orderinginstance-subdomain-label}

L'etichetta del dominio secondario deve rispettare i seguenti requisiti:
*  Sono consentiti solo caratteri alfanumerici e trattini (-).
*  L'etichetta del dominio secondario deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
*  La lunghezza massima dell'etichetta del dominio secondario è di 10 caratteri.
*  L'etichetta del dominio secondario deve essere univoca all'interno del tuo account.

### Nome dominio
{: #vc_orderinginstance-domain-name}

Il nome del dominio root deve rispettare i seguenti requisiti:
* Il nome del dominio deve essere composto da due o più stringhe separate da un punto (.)
* La prima stringa deve iniziare con un carattere alfabetico e terminare con un carattere alfanumerico.
* Tutte le stringhe, tranne l'ultima, possono contenere solo caratteri alfanumerici e trattini (-).
* L'ultima stringa può contenere solo caratteri alfabetici.
* La lunghezza dell'ultima stringa deve essere compresa tra 2 e 24 caratteri.

La lunghezza massima del nome di dominio completo (FQDN) per gli host e le VM (Virtual Machine) è di 50 caratteri. I nomi di dominio devono essere adattati a questa lunghezza massima.
{:note}

### Rete pubblica o privata
{: #vc_orderinginstance-public-private-network}

Le impostazioni di abilitazione della scheda di interfaccia di rete (NIC) si basano sulla tua selezione di **Rete pubblica e privata** o **Solo rete privata**. I seguenti servizi aggiuntivi richiedono NIC pubbliche e non sono disponibili se selezioni l'opzione privata:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### VLAN
{: #vc_orderinginstance-vlans}

Le impostazioni di rete si basano sulla tua selezione di **Ordina nuove VLAN** o **Seleziona VLAN esistenti**.

Per l'ordine della tua istanza sono richieste una VLAN pubblica e due VLAN private. Le due VLAN private sono collegate a ogni Bare Metal Server.

#### Ordina nuove VLAN
{: #vc_orderinginstance-new-vlans}

Seleziona questa opzione per ordinare una nuova VLAN pubblica e due nuove VLAN private.

#### Seleziona VLAN esistenti
{: #vc_orderinginstance-existing-vlans}

A seconda del {{site.data.keyword.CloudDataCent_notm}} che hai selezionato, potrebbero essere disponibili VLAN pubbliche e private esistenti.

Se scegli di riutilizzare VLAN pubbliche e private esistenti, specifica le VLAN e le sottoreti:
* La **VLAN pubblica** serve per l'accesso alla rete pubblica.
* La **VLAN privata** serve per la connettività tra i data center e i servizi in {{site.data.keyword.cloud_notm}}.
* La **VLAN privata secondaria** serve per le funzioni di VMware come vSAN.
* La **Sottorete primaria** è assegnata agli host fisici per l'accesso alla rete pubblica.
* La **Sottorete privata primaria** è assegnata agli host fisici per il traffico di gestione.

Assicurati che la configurazione del firewall sulle VLAN selezionate non blocchi il traffico dei dati di gestione. Assicurati inoltre che tutte le VLAN selezionate si trovino nello stesso pod. I server ESXi non possono essere forniti su VLAN di pod misti.
{:important}

### Configurazione DNS
{: #vc_orderinginstance-dns-config}

Seleziona la configurazione DNS (Domain Name System) per la tua istanza:

* **Singola VSI Windows pubblica per Active Directory/DNS**: viene distribuita una singola VSI di Microsoft Windows Server per Microsoft Active Directory (AD) consultabile, che funziona come DNS per l'istanza in cui sono registrati gli host e le VM. Questa opzione è stata distribuita per impostazione predefinita per le istanze della V1.9 e successive.
* **Due VM di Windows Server dedicate e altamente disponibili sul cluster di gestione**: vengono distribuite due VM di Microsoft Windows, che aiutano a migliorare la sicurezza e la solidità.

Se configuri la tua istanza per utilizzare le due VM di Microsoft Windows, devi fornire due licenze Microsoft Windows Server 2012 R2. Utilizza la licenza Microsoft Windows Server 2012 R2 Standard Edition o la licenza Microsoft Windows Server 2012 R2 Datacenter Edition o entrambe.
{:important}

Ogni licenza può essere assegnata solo a un singolo server fisico e comprende fino a due processori fisici. Una licenza Standard Edition può eseguire due VM di Microsoft Windows virtualizzate per ogni server con 2 processori. Pertanto, sono necessarie due licenze poiché due VM di Microsoft Windows vengono distribuite in due host diversi.

Hai 30 giorni per attivare le VM.

Per ulteriori informazioni sulle licenze di Windows, vedi la [Documentazione di Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Impostazioni dei servizi
{: #vc_orderinginstance-addon-services}

Quando ordini un'istanza vCenter Server, puoi anche ordinare servizi aggiuntivi. Per ulteriori informazioni sui servizi, vedi [Servizi disponibili per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances).

## Riepilogo ordine
{: #vc_orderinginstance-order-summary}

In base alla configurazione che hai selezionato per l'istanza e i servizi aggiuntivi, il costo stimato viene generato e visualizzato immediatamente nella sezione **Riepilogo ordine** nel riquadro di destra. Fai clic su **Dettagli sui prezzi** nella parte inferiore del riquadro di destra per generare un documento PDF che fornisce i dettagli della stima.

## Procedura per ordinare le istanze vCenter Server
{: #vc_orderinginstance-procedure}

1. Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic su **VMware** nel riquadro di navigazione a sinistra e quindi su **vCenter Server** nella sezione **Data center virtuali**.
2. Nella pagina **VMware vCenter Server on IBM Cloud**, fai clic sulla scheda **vCenter Server** e quindi su **Crea**.
3. Nella pagina **vCenter Server**, immetti il nome dell'istanza.
5. Seleziona la versione di vSphere.
4. Seleziona il tipo di istanza:
   * Fai clic su **Istanza primaria** per distribuire una singola istanza nell'ambiente o per distribuire la prima istanza in una topologia multisito.
   * Fai clic su **Istanza secondaria** per connettere l'istanza a un'istanza esistente (primaria) nell'ambiente per l'alta disponibilità e completa quindi la seguente procedura:
     1. Seleziona l'istanza primaria a cui desideri collegare l'istanza secondaria.
     2. Per le istanze primarie della V2.8 o successive, immetti la password dell'amministratore vCenter Server per l'istanza primaria.
     3. Per le istanze primarie della V2.5, 2.6 o 2.7, immetti la password dell'amministratore PSC per l'istanza primaria.
     4. Per le istanze primarie della V2.4 o precedenti, verifica che il valore precompilato per la password dell'amministratore PSC per l'istanza primaria sia corretto.
6. Completa le impostazioni di licenza per i componenti dell'istanza.
   *  Per utilizzare le licenze fornite da IBM, seleziona **Includi con l'acquisto** e, se necessario, seleziona l'edizione della licenza.
   *  Per utilizzare la tua propria licenza, seleziona **Fornita dall'utente** e immetti la chiave di licenza.
7. Completa le impostazioni di Bare Metal Server.
    1. Seleziona il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.
    2. Seleziona la configurazione di Bare Metal Server.
       * Se selezioni **Skylake** o **Broadwell**, specifica il modello di CPU e la dimensione della RAM.
       * Quando selezioni **Certificato SAP**, scegli una delle configurazioni preimpostate.
    3. Specifica il numero di {{site.data.keyword.baremetal_short}}. Se intendi utilizzare vSAN come soluzione di archiviazione, sono richiesti almeno 4 {{site.data.keyword.baremetal_short}}.  
8. Completa la configurazione di archiviazione.
  * Se selezioni **Storage vSAN**, specifica i tipi di disco per i dischi di capacità e cache, il numero di dischi e l'edizione della licenza vSAN. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le stesse impostazioni in tutte le condivisioni file, specifica il **Numero di condivisioni**, le **Prestazioni** e la **Dimensione (GB)**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le condivisioni file singolarmente, seleziona **Configura condivisioni singolarmente**. Quindi, fai clic sull'icona **+** accanto all'etichetta **Aggiungi storage condiviso** e seleziona le **Prestazioni** e la **Dimensione (GB)** per ogni condivisione file. Devi selezionare almeno una condivisione file.
  * Se selezioni **Dischi locali**, specifica il numero di dischi e il tipo di disco.
9. Completa le impostazioni dell'interfaccia di rete.
   1. Immetti il prefisso del nome host, l'etichetta del dominio secondario e il nome del dominio root. Per un'istanza secondaria, il nome di dominio viene completato automaticamente.
   2. Seleziona l'impostazione di rete **Rete pubblica e privata** o **Solo rete privata**.
   3. Seleziona le impostazioni della VLAN:
      * Se vuoi ordinare nuove VLAN pubbliche e private, fai clic su **Ordina nuove VLAN**.
      * Se vuoi riutilizzare le VLAN pubbliche e private esistenti quando sono disponibili, fai clic su **Seleziona VLAN esistenti** e specifica le VLAN e le sottoreti.
   4. Specifica la configurazione DNS.

10. Seleziona i servizi aggiuntivi da distribuire nell'istanza facendo clic sulla scheda del servizio corrispondente. Se un servizio richiede la configurazione, completa le impostazioni specifiche del servizio e fai clic su **Aggiungi servizio** sulla scheda.
Per ulteriori informazioni su come fornire le impostazioni per un servizio, vedi l'argomento relativo all'ordine del servizio corrispondente.

11. Nel riquadro **Riepilogo ordine**, verifica la configurazione dell'istanza prima di effettuare l'ordine.
   1. Esamina le impostazioni per l'istanza.
   2. Esamina il costo stimato dell'istanza. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di ordinare l'istanza.
   4. Fai clic su **Fornitura**.

## Risultati dopo l'ordine di istanze vCenter Server
{: #vc_orderinginstance-results}

La distribuzione dell'istanza inizia automaticamente. Riceverai la conferma che l'ordine è in fase di elaborazione e puoi controllare lo stato della distribuzione visualizzando i dettagli dell'istanza.

Una volta che l'istanza è stata distribuita correttamente, i componenti descritti in [Specifiche tecniche per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs) vengono installati sulla tua piattaforma virtuale VMware. I server ESXi che hai ordinato vengono raggruppati come **cluster1** per impostazione predefinita. Se hai ordinato servizi aggiuntivi, la distribuzione dei servizi inizia dopo che il tuo ordine è stato completato.

Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Pronto per l'utilizzo** e riceverai una notifica via e-mail.

Se ordini un'istanza secondaria, il client web VMware vSphere per l'istanza primaria (collegata a quella secondaria) potrebbe essere riavviato una volta completato l'ordine della tua istanza secondaria.

## Operazioni successive
{: #vc_orderinginstance-next}

Visualizza e gestisci l'istanza vCenter Server che hai ordinato.

Devi gestire i componenti {{site.data.keyword.vmwaresolutions_short}} creati nel tuo account {{site.data.keyword.cloud_notm}} solo attraverso la console {{site.data.keyword.vmwaresolutions_short}}, non il {{site.data.keyword.slportal}} o qualsiasi altro mezzo all'esterno della console.
Se modifichi questi componenti al di fuori della console {{site.data.keyword.vmwaresolutions_short}}, le modifiche non saranno sincronizzate con la console.
{:important}

**ATTENZIONE:** la gestione di un qualsiasi componente {{site.data.keyword.vmwaresolutions_short}} (installato nel tuo account {{site.data.keyword.cloud_notm}} nel momento in cui hai ordinato l'istanza) dall'esterno della console {{site.data.keyword.vmwaresolutions_short}} può rendere instabile il tuo ambiente. Queste attività di gestione includono:
*  Aggiunta, modifica, restituzione o rimozione dei componenti
*  Espansione o contrazione della capacità dell'istanza mediante l'aggiunta o la rimozione di server ESXi
*  Spegnimento dei componenti
*  Riavvio dei servizi

   Le eccezioni a queste attività includono la gestione delle condivisioni file di archiviazione condivisa dal {{site.data.keyword.slportal}}. Tali attività includono: l'ordine, l'eliminazione (che potrebbe influire sugli archivi di dati, se montati), l'autorizzazione e il montaggio di condivisioni file di archiviazione condivisa.

## Link correlati
{: #vc_orderinginstance-related}

* [Registrazione di un account {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Configurazione multisito per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Eliminazione di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)

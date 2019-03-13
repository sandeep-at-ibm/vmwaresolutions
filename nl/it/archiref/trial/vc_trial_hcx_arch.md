---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Progettazione dell'architettura HCX on IBM Cloud per Single-node Trial for vCenter Server on IBM Cloud
{: #vc_trial_hcx_arch}

VMware HCX on {{site.data.keyword.cloud}} con Single-node Trial for VMware vCenter Server on {{site.data.keyword.cloud_notm}} è una nuova offerta che consente la connessione trasparente tra le istanze {{site.data.keyword.vmwaresolutions_short}} e un data center virtualizzato VMware in loco. Sebbene venga raccomandato per vCenter Server un minimo di tre nodi, la versione di prova a singolo nodo fornisce un percorso a basso costo per verificare e provare i vantaggi di un'implementazione cloud ibrida.

{{site.data.keyword.vmwaresolutions_short}} include delle distribuzioni rapide e completamente automatizzate delle configurazioni vCenter Server in {{site.data.keyword.cloud_notm}}. L'offerta Single-node Trial for vCenter Server integra l'infrastruttura in loco e consente ai carichi di lavoro esistenti o futuri di essere eseguiti in {{site.data.keyword.cloud_notm}} senza la conversione. L'offerta utilizza gli stessi strumenti, competenze e processi utilizzati in loco. Per ulteriori informazioni sull'offerta {{site.data.keyword.vmwaresolutions_short}}, consulta [IBM Architecture Center](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture).

Il servizio HCX on {{site.data.keyword.cloud_notm}} unisce le istanze vCenter Server con i data center virtualizzati in loco consentendo la creazione di estensioni di rete trasparenti e la migrazione bidirezionale dei carichi di lavoro. I componenti di HCX on IBM Cloud, distribuiti come macchine virtuali (VM) nel sito di destinazione {{site.data.keyword.cloud_notm}} VMware, consentono di stabilire una connessione con i componenti di HCX on {{site.data.keyword.cloud_notm}} installati nel sito di origine in loco peer.

Figura 1. Architettura HCX

![Architettura HCX](hcx-architecture.svg "Architettura HCX")

Le seguenti informazioni forniscono la progettazione dell'implementazione del servizio HCX on {{site.data.keyword.cloud_notm}}. Includono sia i componenti sull'istanza {{site.data.keyword.vmwaresolutions_short}} dal lato di destinazione che i componenti distribuiti sull'origine, in loco.

## Panoramica di HCX on IBM Cloud
{: #vc_trial_hcx_arch-ovw}

{{site.data.keyword.cloud_notm}} integra rapidamente le reti vSphere vCenter in loco nelle distribuzioni {{site.data.keyword.vmwaresolutions_short}}. La rete ibrida estende le reti vSphere vCenter in loco in {{site.data.keyword.cloud_notm}}, supportando la mobilità della VM bidirezionale.

HCX gestisce i processi di codifica e decodifica dell'origine e della destinazione, garantendo una protezione coerente e fornendo l'ammissione per i flussi di lavoro ibridi come la migrazione della macchina virtuale e l'estensione della rete. Questa offerta crea una WAN (Wide Area Network) definita dal software e ottimizzata per aumentare le prestazioni della rete estesa, consentendo delle prestazioni che si avvicinano alla velocità della LAN (local area network). HCX consente il carico di lavoro bidirezionale e la migrazione della politica di sicurezza VMware NSX a {{site.data.keyword.cloud_notm}}, si integra con vSphere vCenter ed è gestito dal client web vSphere.

### Estensione della rete di livello 2
{: #vc_trial_hcx_arch-layer-2-extension}

HCX consente a una condizione vSphere in loco esistente di estendere in modo sicuro una rete dal suo vCenter in loco a un {{site.data.keyword.CloudDataCent_notm}} che esegue VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} o vCenter Server. I seguenti elementi abilitano questa funzione:

* HCX fornisce un'applicazione denominata concentratore di livello 2 (L2C).
* Link delle reti estese ai dispositivi edge NSX {{site.data.keyword.cloud_notm}} distribuiti su vCenter Server.
* La possibilità di distribuire più di un concentratore di livello 2 standard per ottenere la scalabilità e aumentare la velocità effettiva dal vCenter in loco.
* Le VM che vengono migrate tramite il gateway cloud e attraverso il livello 2 esteso possono conservare i propri indirizzi IP e MAC.

### Migrazione della macchina virtuale
{: #vc_trial_hcx_arch-vm-mig}

HCX fornisce i seguenti tre metodi di spostamento della VM:

* Migrazione con basso tempo di inattività
* Migrazione vSphere vMotion
* Migrazione di tipo cold (a freddo)

#### Migrazione con basso tempo di inattività
{: #vc_trial_hcx_arch-low-downtime-mig}

La migrazione con basso tempo di inattività si basa su vSphere Replication, che è una tecnologia distribuita implementata nell'hypervisor VMware ESX o ESXi. La distribuzione HCX in loco crea una replica di una VM live in {{site.data.keyword.cloud_notm}}, esegue un cambio per spegnere la VM di origine ed accendere la VM migrata. Il percorso di migrazione è sempre tramite il gateway cloud. Il trasporto può essere internet, una rete estesa di livello 2 o una riga Direct Connect. Puoi migrare una VM più di una volta in entrambe le direzioni.

#### Migrazione vSphere vMotion
{: #vc_trial_hcx_arch-vmotion-mig}

Puoi trasferire le VM live utilizzando la migrazione vSphere vMotion attraverso una rete estesa a {{site.data.keyword.cloud_notm}}. La migrazione vMotion è anche nota come migrazione senza tempo di inattività o vMotion tra cloud.

#### Migrazione di tipo cold (a freddo)
{: #vc_trial_hcx_arch-cold-mig}

La migrazione di tipo cold (a freddo) fornisce la possibilità di trasferire una VM spenta a {{site.data.keyword.cloud_notm}} su una rete estesa creata tramite il concentratore di livello 2.

#### Funzioni di migrazione comuni
{: #vc_trial_hcx_arch-common-feat}

Sono disponibili le seguenti funzioni con tutti e tre i tipi di migrazione:

* Ottimizzazione WAN definita dal software che aumenta la velocità e la velocità effettiva della migrazione.
* Pianificare la tua migrazione in un momento specificato.
* Conservare il nome host, il nome della VM o entrambi.

### Rete
{: #vc_trial_hcx_arch-network}

Le seguenti funzioni di rete sono integrate nel gateway cloud e nei concentratori di livello 2.

#### Instradamento del flusso intelligente
{: #vc_trial_hcx_arch-intel-flow}

L'instradamento del flusso intelligente seleziona automaticamente la connessione migliore in base al percorso internet, caricando in modo efficiente l'intera connessione in modo che i carichi di lavoro vengano spostati il più velocemente possibile. Quando i flussi più grandi, come ad esempio il backup o la replica, causano un conflitto con la CPU, i flussi più piccoli vengono instradati alle CPU meno occupate, migliorando le prestazioni del traffico interattivo.

#### Instradamento di prossimità
{: #vc_trial_hcx_arch-prox-routing}

L'instradamento di prossimità garantisce che l'inoltro tra le VM connesse alle reti estese ed instradate, sia in loco che nel cloud, sia simmetrico. Questa funzione richiede che i servizi di rete avanzati con l'instradamento dinamico siano configurati tra il cloud e la locale del cliente.

Quando gli utenti estendono le loro reti al cloud, la connettività di livello 2 viene estesa nelle reti {{site.data.keyword.cloud_notm}}. Tuttavia, senza l'ottimizzazione dell'instradamento, le richieste di comunicazione di livello 3 devono ritornare all'origine della rete in loco per essere instradate. Questo percorso di ritorno viene denominato "tromboning" o "hairpinning". Il tromboning non è efficiente perché i pacchetti devono andare avanti e indietro tra la rete di origine e il cloud, anche quando sia la VM di origine che di destinazione risiedono nel cloud.

Se il percorso di inoltro include dei firewall con stato o un'altra apparecchiatura incorporata che deve vedere entrambi i lati della connessione, la comunicazione potrebbe non riuscire. Il malfunzionamento della comunicazione della VM, senza l'ottimizzazione dell'instradamento, si verifica quando il percorso in uscita verso il cloud può essere la rete di livello 2 estesa o la rete instradata dell'organizzazione. La rete in loco non conosce la "scelta rapida" della rete estesa. Questo problema viene denominato instradamento asimmetrico. La soluzione è di abilitare l'instradamento di prossimità in modo che la rete in loco possa conoscere le rotte da {{site.data.keyword.cloud_notm}}.

Il gateway cloud conserva un inventario di VM nel cloud. Conosce inoltre i seguenti stati della VM:

* Trasferita a {{site.data.keyword.cloud_notm}} con vMotion (migrazione senza tempo di inattività)
* Migrata al cloud utilizzando la replica basata sull'host (migrazione con basso tempo di inattività)
* Creata nel cloud (su una rete estesa)

#### Sicurezza
{: #vc_trial_hcx_arch-sec}

Il gateway cloud offre AES-GCM conforme con Suite B con IKEv2, offload AES-NI e controllo di ammissione basato sul flusso. HCX gestisce inoltre il processo di codifica e decodifica dell'origine e della destinazione, garantendo una protezione coerente e la gestione dei flussi di lavoro ibridi come la migrazione della VM e l'estensione della rete. Puoi migrare le politiche di sicurezza definite e assegnate a una VM in loco con la VM in {{site.data.keyword.cloud_notm}}.

Sono necessarie le seguenti condizioni per la migrazione della politica:

* Il data center in loco esegue NSX V6.2.2 o superiore.
* In vSphere, la politica di sicurezza è una sezione NSX singola che può avere molte regole.
* Puoi denominare una serie di indirizzi IP o MAC in modo che partecipino alla politica.
* Il nome della serie di IP o MAC non può superare i 218 caratteri.
* Le regole supportate specificano le serie di IP o gli indirizzi IP di livello 3 oppure le serie di MAC o di indirizzi MAC di livello 2 come l'origine o la destinazione.

### Componenti HCX
{: #vc_trial_hcx_arch-hcx-comp}

Il servizio HCX on {{site.data.keyword.cloud_notm}} distribuisce quattro applicazioni virtuali installate e configurate sul data center in loco e sulla destinazione IBM Cloud. Le seguenti informazioni descrivono ognuna delle quattro applicazioni virtuali richieste. Facoltativamente, potrebbero essere necessari dei dispositivi edge a seconda della progettazione dell'implementazione.

#### HCX Manager
{: #vc_trial_hcx_arch-hcx-manager}

L'applicazione virtuale HCX Manager è un'estensione al vCenter in loco. L'applicazione viene distribuita come una VM e la sua struttura file contiene le altre applicazioni virtuali del servizio ibride. HCX Manager controlla la distribuzione e la configurazione del gateway cloud, i concentratori di livello 2 e l'applicazione virtuale WAN Optimization sia in loco che in {{site.data.keyword.cloud_notm}}.

#### Hybrid Cloud Gateway
{: #vc_trial_hcx_arch-hcg}

Hybrid Cloud Gateway (CGW) mantiene un canale sicuro tra la condizione vSphere in loco e {{site.data.keyword.cloud_notm}}. HCX utilizza una potente crittografia per eseguire il bootstrap di una connessione site-to-site a {{site.data.keyword.cloud_notm}}. Il canale sicuro tra vSphere e {{site.data.keyword.cloud_notm}} evita problemi di sicurezza "middle mile" della rete. Il gateway cloud incorpora inoltre la tecnologia di replica vSphere per eseguire la migrazione bidirezionale.

#### WAN Optimization
{: #vc_trial_hcx_arch-wan-opt}

L'applicazione WAN Optimization è il componente che esegue il condizionamento WAN per ridurre gli effetti della latenza. Incorpora inoltre Forward Error Correction per negare gli scenari di perdita dei pacchetti e la deduplicazione dei pattern di traffico ridondanti. Complessivamente, viene ridotto l'utilizzo della larghezza di banda e garantito il migliore utilizzo della capacità di rete disponibile per velocizzare il trasferimento dei dati da/a {{site.data.keyword.cloud_notm}}.

La migrazione della VM si basa sulla combinazione dell'applicazione WAN Optimization e del gateway cloud per ottenere una mobilità ineguagliabile tra vSphere in loco e {{site.data.keyword.cloud_notm}}. Inoltre, l'estensione di livello 2 trae vantaggio dall'ottimizzazione WAN quando il percorso dei dati viene instradato tramite il gateway cloud.
{:important}

#### Concentratori di livello 2
{: #vc_trial_hcx_arch-layer-2-conc}

Le applicazioni dei concentratori di livello 2 (L2C) permettono l'estensione di una rete di livello 2 dal data center vSphere in loco a {{site.data.keyword.cloud_notm}}.

I concentratori di livello 2 hanno le seguenti interfacce:

* **Interfaccia trunk interna** questa interfaccia gestisce il traffico della macchina virtuale in loco per le reti estese utilizzando un'associazione bridge traslazionale a una rete estesa corrispondente in {{site.data.keyword.cloud_notm}}.
* **Interfaccia uplink** HCX utilizza questa interfaccia per inviare il traffico di sovrapposizione incapsulato a/da {{site.data.keyword.cloud_notm}}. I dati dell'applicazione passano attraverso l'interfaccia uplink.

### Architettura di distribuzione
{: #vc_trial_hcx_arch-deployment}

Per informazioni sulla distribuzione di HCX on {{site.data.keyword.cloud_notm}}, consulta [VMware HCX on {{site.data.keyword.cloud_notm}}
Deployment and Operations](https://www.ibm.com/cloud/garage/files/VMware-HCX-on-IBM-Cloud-Deployment-and-Operations.pdf).

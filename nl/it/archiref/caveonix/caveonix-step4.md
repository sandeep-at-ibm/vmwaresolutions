---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

# Passo 4 - Impostazione dell'applicazione
{: #caveonix-step4}

Dopo che le VM (Virtual Machine) sono state distribuite e i componenti dell'applicazione sono stati installati, la soluzione Caveonix RiskForesight è disponibile per essere impostata per il provider di servizi e il primo tenant o la prima organizzazione.

Il provider di servizi è l'organizzazione di livello superiore e ci sono uno o più tenant/organizzazioni serviti dal provider di servizi. Il provider di servizi assegna gli asset raccolti dal vCenter ai tenant o alle organizzazioni, che quindi li assegnano alle applicazioni o alle applicazioni secondarie. Queste applicazioni sono quindi soggette a un regime di conformità.

Questo passo viene inizialmente completato dall'automazione IC4VS che utilizza le informazioni fornite dal client durante il processo di ordinazione e le informazioni predefinite. Il processo di impostazione può essere avviato dal client, dopo la distribuzione, per modificare il provider di servizi o l'organizzazione tenant come richiesto, dopo l'installazione.

L'impostazione del provider di servizi si articola in otto passi secondari:
-	Passo 1: Dettagli dell'organizzazione - aggiungi i dettagli per l'organizzazione principale per il tuo provider di servizi cloud. Questa organizzazione può avere più ubicazioni fisiche e più data center. Le organizzazioni per i tuoi tenant e le tue organizzazioni secondarie per il tuo provider di servizi vengono aggiunte in un secondo momento.
-	Passo 2: Ubicazioni – Associa l'infrastruttura in "Ubicazioni” RiskForesight. Gli asset sono raggruppati in base all'ubicazione, al provider cloud e al repository di asset.
-	Passo 3: Ambienti - facoltativo. Gli ambienti sono un modo per raggruppare gli asset. Ad esempio, DevOps, sito del ripristino di emergenza (DR Site), produzione (Production).
-	Passo 4: Provider cloud - aggiungi i “provider” che forniscono l'infrastruttura su cui viene eseguita la tua applicazione.
-	Passo 5: Repository di asset - un repository di asset associa un insieme di asset a un'organizzazione, un provider cloud o un'ubicazione.
-	Passo 6: Organizzazioni - crea un'organizzazione secondaria per le tue operazioni e organizzazioni aggiuntive, una per ognuno dei tuoi tenant del provider di servizi. Ogni tenant deve eseguire il suo processo di impostazione, compresa la creazione delle proprie organizzazioni secondarie.
-	Passo 7: Utenti delle organizzazioni - crea e assegna utenti alle organizzazioni e alle organizzazioni secondarie tenant del provider di servizi.
-	Passo 8: Programma di pianificazione delle attività – configura le attività per: eseguire la sincronizzazione con il repository di asset, eseguire le scansioni di conformità e vulnerabilità SCAP, raccogliere i flussi di rete NSX, raccogliere informazioni sul software in esecuzione sugli asset monitorati e raccogliere eventi di sistema e log di sistema per gli asset.

L'impostazione di tenant od organizzazione si articola in sette passi secondari:

-	Passo 1: Organizzazione - aggiunge i dettagli per la tua organizzazione primaria. Puoi anche creare delle organizzazioni secondarie. utilizza le organizzazioni per segmentare i tuoi utenti oppure come uno dei modi per raggruppare i tuoi asset. Puoi creare ulteriori organizzazioni con una delle tue organizzazioni esistenti come elemento principale. Quando crei una nuova organizzazione, puoi selezionare il valore dell'impatto di business ("Business Impact Value"), che viene utilizzato per generare i punteggi di rischio informatico.
-	Passo 2: asset dell'organizzazione - i nuovi asset/carichi di lavoro vengono raggruppati automaticamente in base a ubicazione, provider cloud e repository di asset. Gli asset possono essere assegnati solo a una singola organizzazione per volta. Il provider di servizi deve assegnare gli asset a un'organizzazione.
-	Passo 3: associa ambiente e ubicazione – facoltativo. Gli ambienti sono definiti dal provider di servizi.
-	Passo 4 e 5: crea le applicazioni secondarie o le applicazioni – utilizzato per raggruppare gli asset nelle ubicazioni e organizzazioni e visualizzarne i flussi e le politiche associati. Crea le applicazioni che corrispondono ai servizi IT e di business. Ad esempio, Applicazione=SAP (Application=SAP), Applicazione secondaria=Front end SAP (Sub-Applications=SAP Front End), Livello medio SAP (SAP Middle Tier) e Back end SAP (SAP Back End). Il valore dell'impatto di business corrisponde a un'applicazione, i regimi di conformità si applicano a un'applicazione.
-	Passo 6: Accesso remoto - l'accesso remoto è richiesto per eseguire le scansioni sugli asset e può essere un account di servizio predefinito o un account specifico per l'asset.
-	Passo 7: Programma di pianificazione delle attività - pianifica le scansioni per l'esecuzione su una base periodica. I tipi di attività includono; Scansione SCAP-vulnerabilità (SCAP Scan-Vulnerability), Scansione SCAP--XCCDF (SCAP Scan-XCCDF), Scansione del flusso NSX (NSX Flow Scan), Scansione software (Software Scan), Scansione estratto log (Log Extract Scan).

Le seguenti informazioni vengono raccolte dall'utente al momento dell'ordine e vengono utilizzate nell'impostazione dell'applicazione.

Tabella 1. Informazioni raccolte dall'utente.

|Fase di impostazione |Parametro |
|---|---|
|Organizzazione / Repository di asset  |Nome organizzazione |
|Organizzazione |Numero di telefono |
|Organizzazione |Email |
|Organizzazione / Repository di asset |Riga 1 indirizzo |
|Provider cloud / Repository di asset |Nome |
|Provider cloud |Descrizione |
|Provider cloud |Email POC |
|Provider cloud |Tipo|
|Provider cloud |Nome POC |
|Provider cloud |Telefono POC |

Nell'impostazione dell'applicazione vengono utilizzate le seguenti informazioni predefinite.

Tabella 2. Informazioni predefinite utilizzate nell'impostazione dell'applicazione

|Fase di impostazione |Parametro |
|---|---|
|Ambiente |Il Nome ambiente (Environment Name) è impostato su “Iniziale” (Initial)|
|Ambiente | Il punteggio è impostato su 5|
|Repository di asset |Sono configurati due repository di asset: vCenter e NSX Manager. URL host impostato su https://*vCenter fqdn* e https://*NSX Manager fqdn*|
|Repository di asset |Sono configurati due repository di asset: vCenter e NSX Manager; entrambi utilizzano lo stesso nome utente. Il nome utente è impostato sul nome utente dell'amministratore vCenter|
|Repository di asset |Sono configurati due repository di asset: vCenter e NSX Manager; entrambi utilizzano la stessa password. La password è impostata sulla password dell'amministratore vCenter.
|Repository di asset |Sono configurati due repository di asset: vCenter e NSX Manager; entrambi utilizzano la stessa password. Il tipo (Type) è impostato su vCenter per un repository e NSX per l'altro
|Attività |Sono impostate quattro attività: scansione degli asset (Asset Scan), flussi NSX (NSX Flows), scansione dell'infrastruttura VMware (VMware Infrastructure Scan) e vulnerabilità WMware (VMware Vulnerability). Il nome della scansione (ScanName) è impostato su DC1AssetScan, NSXFlows, VMWInfraScan, VMWVulnScan |
|Attività |Sono impostate quattro attività: scansione degli asset (Asset Scan), flussi NSX (NSX Flows), scansione dell'infrastruttura VMware (VMware Infrastructure Scan) e vulnerabilità WMware (VMware Vulnerability). Il tipo (Type) è impostato su vCenter, NSX, VMWareInfrastructureScan, VMWareVulnerabilityScan |
|Attività |La pianificazione (Schedule) è impostata su Hourly (Oraria) per DC1AssetScan e Daily (Giornaliera) per le altre. |

## Link correlati
{: #caveonix-step4-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

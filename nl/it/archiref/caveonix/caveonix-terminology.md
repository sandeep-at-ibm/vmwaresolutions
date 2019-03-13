---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Glossario dei termini Caveonix
{: #caveonix-terminology}

Questo glossario fornisce alcune descrizioni per i termini che non sono associati alla soluzione Caveonix RiskForesight.

-	**NIST Special Publication 800-53:** un RMF (Risk Management Framework) che si occupa del controllo della sicurezza.
-	**SCAP (Security Content Automation Protocol):** un metodo per l'utilizzo di standard specifici per abilitare la misurazione e la gestione delle vulnerabilità e la valutazione della conformità alle politiche automatizzate dei sistemi distribuiti in un'organizzazione. Delle liste di controllo standardizzano e abilitano l'automazione del collegamento tra le configurazioni della sicurezza dei computer e il quadro dei controlli NIST Special Publication 800-53.
  - L'NVD (National Vulnerability Database) è il repository di contenuto del governo statunitense per SCAP.
  -	SCAP consente agli amministratori della sicurezza di eseguire scansioni di computer, software e altri dispositivi sulla base di misure di sicurezza standard predeterminate per appurare se le patch di configurazione e software sono implementate nel rispetto dello standard a cui sono confrontate.
  I componenti SCAP sono i seguenti:
  -	CVE (Common Vulnerabilities and Exposures) - un elenco di vulnerabilità della sicurezza informatica di pubblico dominio.
  -	CCE (Common Configuration Enumeration) – un elenco di problemi di configurazione del sistema correlati alla sicurezza.
  -	CPE (Common Platform Enumeration) - uno schema di denominazione strutturato per i pacchetti, il software e i sistemi IT (Information Technology).
  -	CWE (Common Weakness Enumeration) – un elenco di vulnerabilità della sicurezza del software comuni.
  -	CVSS (Common Vulnerability Scoring System) - fornisce un modo per acquisire le caratteristiche principali di una vulnerabilità e produrre un punteggio numerico che ne riflette la gravità.
  -	XCCDF (Extensible Configuration Checklist Description Format) - un linguaggio di specifica per scrivere liste di controllo della sicurezza, benchmark e tipi di documenti correlati. Un documento XCCDF rappresenta una raccolta strutturata di regole di configurazione della sicurezza per alcuni gruppi di sistemi di destinazione.
  -	OVAL (Open Vulnerability and Assessment Language) – un linguaggio utilizzato per codificare i dettagli del sistema e una gamma di repository di contenuto. Il linguaggio standardizza i tre passi principali del processo di valutazione:
      - Rappresentando le informazioni di configurazione dei sistemi per l'esecuzione di test.
      -	Analizzando il sistema (vulnerabilità, configurazione e stato delle patch).
      -	Notifica dei risultati di tale valutazione.
-	**STIG (Security Technical Implementation Guide):** una metodologia di sicurezza informatica per la standardizzazione dei protocolli di sicurezza all'interno di reti, server, computer e progettazioni logiche per migliorare la sicurezza complessiva. Queste guide, quando vengono implementate, migliorano la sicurezza per le architetture software, hardware, fisiche e logiche per ridurre ulteriormente le vulnerabilità.
-	**Provider di servizi:** l'organizzazione di livello superiore.
-	Provider cloud - fornisce l'infrastruttura in cui opera il cloud definito dal software. RiskForesight può essere configurato per più provider cloud.
-	**Organizzazioni:** organizzazioni e organizzazioni secondarie tenant del provider di servizi. Se il repository di asset è vCenter, è necessario creare manualmente l'elenco di organizzazioni/tenant.
-	**Ruoli:** ruoli preconfigurati e ruoli creati dal provider di servizi. I ruoli preconfigurati non possono essere modificati dal provider di servizi.
-	**Utenti delle organizzazioni:** gli utenti delle organizzazioni e delle organizzazioni secondarie tenant.
-	**Repository di asset:** un punto di integrazione che consente a RiskForesight di sincronizzare l'asset corrente nell'ambito della zona cliente e della zona di gestione CSP . L'attuale versione di RiskForesight supporta la sincronizzazione per VMware vCloud Director e vCenter Server. Supporta anche la raccolta di dati da VMware NSX Manager. Gli asset vengono accolti dal repository di asset. Il provider di servizi assegna gli asset raccolti da vCenter alle organizzazioni e alle organizzazioni secondarie tenant del provider di servizi. Un asset può essere assegnato solo a una singola organizzazione.
-	**Accesso remoto:** fornisce le credenziali di end machine per abilitare le scansioni per il monitoraggio di vulnerabilità e conformità e per raccogliere i log degli eventi di sistema. Il provider di servizi può abilitare l'accesso remoto solo per i suoi asset. I tenant hanno il controllo sull'accesso remoto dai loro asset.
-	**Applicazioni e applicazioni secondarie:** un modo logico per raggruppare gli asset. Applicazione di esempio: SAP, applicazione secondaria di esempio: SAP Front End, SAP Middle Tier, SAP Back End.
-	**Ubicazioni:** gli asset sono raggruppati in modo univoco in base a ubicazione, provider cloud e repository di asset.
-	**Ambienti:** un modo per raggruppare asset e applicazioni. A ogni ambiente viene assegnato un fattore di rischio da 1 a 10. Questo fattore viene applicato nel calcolo del punteggio di rischio. Il provider di servizi definisce gli ambienti
-	**Attività:** utilizzate in RiskForesight per:
  -	Sincronizzare periodicamente il repository di asset con RiskForesight.
  -	Eseguire delle scansioni di conformità e vulnerabilità SCAP.
  -	Raccogliere i flussi di rete e altre informazioni che utilizzano le scansioni NSX.
  -	Raccogliere informazioni sul software eseguito sugli asset monitorati.
  -	Raccogliere syslog ed eventi di sistema per gli asset.
-	**Tipi di attività:** sono supportate le seguenti attività:
  -	**Scansione VMware vCenter:** raccoglie gli asset da vCenter.
	- **Scansione VMware VCD:** raccoglie gli asset da VCD.
  -	**Scansione VMware NSX:** raccoglie le informazioni di rete e il flusso di rete da NSX Manager.
  - **Scansione SCAP:** questo tipo di scansione viene utilizzato per eseguire la scansione dei carichi di lavoro per la conformità e i rischi informatici. Questa scansione è basata su SCAP (Security Content Automation Protocol). Per le release future è pianificato un supporto del contento personalizzato nel formato OVAL.
  - **Scansione software:** questa scansione raccoglie l'inventario software installato sul carico di lavoro di destinazione oggetto della gestione. Questo inventario è quindi disponibile per la ricerca mediante l'opzione di ricerca nella barra superiore dell'IU.
  - **LogExtract:** questa scansione supporta la raccolta di log da carichi di lavoro Windows e Linux. Viene utilizzata per finalità di analisi e inserita mediante il machine learning per produrre delle informazioni utili.
  - **Attività AMQP:** questa attività AMQP viene utilizzata per raccogliere eventi dal vivo da VCD per abilitare la sincronizzazione in tempo reale. RiskForesight utilizza eventi di aggiunta, eliminazione e aggiornamento di asset e agisce su tali eventi. Ad esempio, se un nuovo asset viene aggiunto e ne ha ricevuto notifica tramite AMQP, RiskForesight procede ad aggiornare il database immediatamente e avvia la scansione di conformità e rischio informatico.
  - **Scansione dell'infrastruttura VMware:** questa scansione esegue una scansione dell'infrastruttura degli asset VMware.
  -	**Scansione delle vulnerabilità VMware:** questa scansione esegue una scansione delle vulnerabilità degli asset VMware.
-	**Regime di conformità:** disponibile mediante licenza; NIST, NESA, PCI, ISO, HIPAA, GDPR, Custom, FFIEC, FedRAMP Low, FedRAMP Moderate, FedRAMP High
-	**Gestore politiche:** il gestore politiche svolge la funzione di creazione delle politiche per un'organizzazione in base all'output del machine learning. Caveonix fornisce per impostazione predefinita tre tipi di lavori di machine learning per ogni organizzazione. Non sono modificabili e non sono ancora supportati dei lavori aggiuntivi. Questi ultimi saranno disponibili in una release futura. I tipi attualmente supportati di lavori di machine learning sono:
  -	Log Caveo
  -	Reti Caveo
  -	Scansione Caveo
-	**Anomalia:** in base alle anomalie rilevate nei dati, possiamo configurare le politiche per intervenire in base alle condizioni definite dall'utente. Puoi selezionare il tipo di lavoro e configurare le condizioni booleane per il punteggio di anomalie e definire l'azione nel caso in cui la condizione ricorra (sia true). Ad esempio:
  -	Lavoro: "Log Caveo" Il punteggio dell'anomalia è > 90 allora contrassegna l'asset per la quarantena e invia una notifica al canale slack.
  -	Lavoro: "Rete Caveo" Il punteggio dell'anomalia è > 95 quindi metti in quarantena l'asset e invia una notifica email e invia anche una notifica IU.

## Link correlati
{: #caveonix-terminology-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

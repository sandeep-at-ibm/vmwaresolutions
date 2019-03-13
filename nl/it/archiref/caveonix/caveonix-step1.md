---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Passo 1 - Pianificazione iniziale e prerequisiti
{: #caveonix-step1}

Ogni componente dell'applicazione Caveonix RiskForesight è debolmente accoppiato ma è gestito centralmente. Pertanto, possono essere distribuiti in un pattern di distribuzione di macchina virtuale (VM, Virtual Machine) “tutto in uno” oppure i componenti dell'applicazione possono essere “ridimensionati in modo incrementale” e distribuiti su più VM per una disponibilità, delle prestazioni e una capacità maggiori.

I pattern di distribuzione sono basati sia sui requisiti di disponibilità che sul dimensionamento per la conservazione dei dati. I nodi di distribuzione RiskForesight possono essere caratterizzati come:

-	VM di base – le VM di base ospitano i componenti dell'applicazione di cui non viene eseguito il ridimensionamento a causa della conservazione dei dati. Questi componenti sono; l'IU RiskForesight, l'applicazione RiskForesight, i plugin RiskForesight, il raccoglitore centrale, il raccoglitore remoto, l'archivio dati indice, l'archivio dati di messaggistica e l'archivio dati relazionale.
-	VM di ridimensionamento incrementale – le VM di ridimensionamento incrementale, il database e l'indice di dati eseguono il ridimensionamento in base al numero di asset e alla conservazione dei dati necessaria che crea richiesta di ulteriore spazio su disco fisso di ridimensionamento incrementale e, pertanto, più VM di ridimensionamento incrementale.

Ci sono tre modelli di distribuzione Caveonix RiskForesight:

-	“Tutto-in-uno” – Una distribuzione e una configurazione automatizzate di 1 VM che ospita tutti i componenti dell'applicazione:
  - Tutti i componenti dell'applicazione installati su una singola VM.
  - I raccoglitori remoti possono essere installati su VM separate.
  - Piccole distribuzioni – fino a 100 asset con 7 - 30 giorni di indicizzazione.
-	Distribuito in modo parziale – dopo il completamento della distribuzione automatizzata, puoi eseguire il ridimensionamento incrementale in modo manuale aumentando la RAM e il disco nella VM iniziale e aggiungere tre VM di ridimensionamento incrementale.
  - IU, applicazione, plugin, raccoglitore centrale, raccoglitore remoto, archivio dati indice, archivio dati di messaggistica e archivio dati relazionale distribuiti su una singola VM.
  - Raccoglitori remoti installati su VM separate.
  -	Nodi di dati indice distribuiti su VM separate.
  -	Distribuzioni da piccole a medie – fino a 500 asset con 30 giorni di indicizzazione.
- Completamente distribuito - aggiungi ulteriori VM di base e VM di ridimensionamento incrementale in base al numero di asset e requisiti di conservazione dei dati:
  - Componenti dell'applicazione distribuiti su VM separate per facilitare la scalabilità.
  -	Pattern di distribuzione richiesto al crescere del numero di asset nell'intervallo 500 - 100.000.
  -	Raccoglitori remoti installati su VM separate.
  -	IU su più VM.
  -	Applicazione e plugin su più VM.
  -	Raccoglitore centrale configurato in un cluster.
  -	Archivio dati relazionale distribuito in un modello primario/secondario.
  -	Archivio dati di messaggistica distribuito in un cluster.
  -	Archivio dati indice distribuito con nodi master e di dati.
  -	Ulteriori nodi di dati utilizzati per il ridimensionamento incrementale al crescere del numero di asset.

Tutti i componenti devono avere un FQDN ed essere registrati in DNS prima di qualsiasi distribuzione di VM. Questo passo viene eseguito dall'automazione IC4VS per la distribuzione "tutto-in-uno" iniziale ma è responsabilità del client quando viene eseguito il ridimensionamento della distribuzione.

## Link correlati
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

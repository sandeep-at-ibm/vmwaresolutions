---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Percorso di modernizzazione
{: #vcscontent-modjourney}

Questo è un caso di utilizzo di riferimento che descrive come viene modernizzata una classica applicazione WebSphere Application Server utilizzando {{site.data.keyword.cloud}} Private, il contenuto di IBM Middleware, {{site.data.keyword.containerlong_notm}} e VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## La modernizzazione va oltre le applicazioni
{: #vcscontent-modjourney-modernization}

Siamo tutti su un percorso cloud e a diversi punti del percorso. Questo caso di utilizzo si concentra sul modo in cui un'applicazione esistente, Stock Trader, viene modernizzata attraverso dei passi incrementali pianificati dall'architetto dell'applicazione, Jane, e dall'architetto dell'infrastruttura cloud, Todd. Questo caso di utilizzo mostra esempi che ti aiutano ad affrontare ogni passo del tuo percorso e il valore che viene realizzato per il tuo business, indipendentemente da quanto grande o piccolo sia ciascun passo.

La maggior parte della nostra attenzione in questo percorso è rivolta alla modernizzazione dell'applicazione Stock Trader. Per modernizzare completamente il tuo business in un business nativo cloud, è necessario discutere i temi relativi ad applicazioni, DevOps, integrazione e gestione. Tutti i temi operano insieme per aiutarti a raggiungere i tuoi obiettivi. Modernizzare un tema e non gli altri potrebbe creare dei problemi.

## Motivi per modernizzare
{: #vcscontent-modjourney-reasons}

### Modernizzazione dell'applicazione
{: #vcscontent-modjourney-app-mod}

L'obiettivo sono applicazioni native cloud in grado di adeguarsi e rispondere alle richieste in continua evoluzione.

* Devi modernizzare le applicazioni esistenti e creare nuove applicazioni native cloud per catturare l'immaginazione dei clienti.
* Hai bisogno di applicazioni in grado di scalare, raggiungere tutto il mondo, adattarsi alle richieste, cambiare, migliorare e rinnovarsi rapidamente.

### Modernizzazione di DevOps
{: #vcscontent-modjourney-devops-mod}

Mentre modernizzi la tua applicazione, la forma in cui distribuisci l'applicazione, l'intera pipeline di distribuzione, viene modernizzata in modo che la nuova cultura nativa cloud che i tuoi sviluppatori stanno creando possa ridimensionare il modo in cui l'applicazione viene distribuita.

* Devi modernizzare la tua cultura di Sviluppo e Operazioni (e sicurezza) mentre modernizzi le tue applicazioni.
* Hai bisogno di team DevOps in grado di scalare, raggiungere tutto il mondo, adattarsi alla domanda, cambiare, migliorare e rinnovarsi rapidamente.

###  Modernizzazione dell'integrazione
{: #vcscontent-modjourney-integration-mod}

Lungo tutto il percorso di modernizzazione, i tuoi team devono integrarsi con risorse esistenti, nuovi servizi cloud, i tuoi dati e nuove informazioni approfondite dalle analisi eseguite su tali dati.

* Devi utilizzare le tue risorse esistenti in questo percorso in modo che possano scalare, raggiungere tutto il mondo, adattarsi alla domanda, cambiare, migliorare e rinnovarsi rapidamente.
* Devi arricchire con nuovi servizi cloud in ogni fase di questo percorso.
* Devi integrare i tuoi dati e le informazioni approfondite ottenute dall'applicazione dell'analisi ai tuoi dati.

### Gestione
{: #vcscontent-modjourney-mgmt}

La modernizzazione delle procedure di gestione è un altro percorso parallelo da intraprendere mentre modernizzi le tue applicazioni. Gli strumenti, la cultura e i comportamenti principali su come gestire e mantenere un'applicazione modernizzata sono molto diversi rispetto a prima.

* Devi gestire i tuoi microservizi e il middleware inserito in contenitore utilizzando l'orchestrazione, la registrazione e il monitoraggio integrati.
* Devi gestire le tue piattaforme ibride multi-cloud in tutte le sedi mondiali in modo che possano scalare, raggiungere tutto il mondo, adattarsi alla domanda, cambiare, migliorare e rinnovarsi rapidamente.
* Devi automatizzare il modo in cui gestisci più di un cloud e le applicazioni e il middleware che vengono eseguiti su di essi.

## Conosci Todd e Jane
{: #vcscontent-modjourney-todd-jane}

Per il nostro percorso di Stock Trader, ci concentriamo su due personaggi: Todd e Jane. Todd è capo operativo per l'azienda ACME ed è responsabile dell'infrastruttura, della sicurezza, degli ambienti cloud e delle politiche che garantiscono che i carichi di lavoro eseguiti in tali ambienti rispettino le varie normative.

Jane è il lead di sviluppo per la soluzione Stock Trader ed ha ora la responsabilità di modernizzare Stock Trader, il che significa lavorare con tutti i suoi team di sviluppo per modificare gli strumenti, la cultura e le piattaforme di sviluppo, in modo che la soluzione Stock Trader monolitica esistente venga modernizzata in una soluzione nativa cloud ben gestita.

## Conosci Stock Trader
{: #vcscontent-modjourney-meet-stock-trader}

Todd e Jane hanno creato un'applicazione che viene eseguita in WebSphere chiamata Stock Trader. Sebbene abbia un'interfaccia utente di base, è un'applicazione affidabile in cui i gestori di portafoglio vanno a gestire i portafogli, compreso l'acquisto e la vendita di azioni e la visualizzazione dei livelli di fedeltà interni.

Stock Trader viene eseguito in WebSphere, è creato con alcuni file .war e utilizza un database Db2 tradizionale che viene eseguito nel loro data center da cui dipendevano da anni. Ci vuole molto tempo per migliorare questa applicazione a causa delle dipendenze tra i team di infrastruttura, team di sviluppo e team di dati.

Ma, anche se Stock Trader funziona bene, tutti in azienda vogliono qualcosa di meglio. I gestori prodotti vogliono aggiungere i social media al loro programma di fedeltà. Jane è contenta perché può eseguire il refactoring dell'applicazione in microservizi, che consente loro di fornire continuamente funzionalità migliorate con meno dipendenze. A Todd piace l'idea dell'efficienza del cloud, ma necessita ancora della governance per mantenere la conformità con le politiche aziendali.

## Passi lungo il percorso
{: #vcscontent-modjourney-steps}

Todd e Jane sanno per esperienza che un buon percorso per modernizzare le soluzioni inizia con una tabella di marcia strategica. Mentre i piani possono cambiare, è sempre bene riflettere sulla visione di insieme e definire un percorso realistico per arrivarci. Ogni passo deve apportare valore all'azienda e i passi non sono così significativi da causare costose interruzioni ai propri clienti.

Per Todd e Jane, i passi nel percorso di Stock Trader sono:
1. Migrazione delle VM Stock Trader in {{site.data.keyword.cloud_notm}}. Questo passo consente a Todd di ridurre la necessità di gestire il proprio hardware e il contenuto VMware nel data center locale.

2. Trasformazione di Stock Trader in WebSphere Application Server in Stock Trader nei contenitori. Questo passo aumenta la resilienza perché l'esecuzione di contenitori in Kubernetes porta l'orchestrazione e altri funzionamenti cloud. Ciò richiede a Todd di preparare un'istanza {{site.data.keyword.cloud_notm}} Private nel suo ambiente VMware vCenter Server on {{site.data.keyword.cloud_notm}} e quindi di lavorare con Jane e Transformation Advisor per inserire Stock Trader in contenitori.

3. Refactoring e aggiunta del middleware in {{site.data.keyword.cloud_notm}} Private. Questo passo porta il loro middleware esistente in un ambiente cloud e ottimizza i funzionamenti del cloud. Ciò semplifica anche la concessione di licenze e prepara la soluzione
a essere interamente portatile per l'uso in altri ambienti Kubernetes.

4. Arricchimento con Watson e altri servizi di cloud pubblico. Questo passo può aumentare in modo esponenziale l'esperienza di Stock Trader avvalendosi dei servizi AI e della capacità di comunicare con i data center cloud di tutto il mondo.

5. Vero ibrido con {{site.data.keyword.cloud_notm}} Kubernetes Service. Questo passo consente a Todd di avere un servizio Kubernetes gestito che si connette ancora alla stessa regione cloud della sua istanza {{site.data.keyword.cloud_notm}} Private. Consente inoltre ai team di sviluppo di Jane di disporre di un cluster di sviluppo e test in cui possono sperimentare continuando ad accedere alla stessa origine dati del loro cluster {{site.data.keyword.cloud_notm}} Private principale.

6. Modernizzazione di DevOps. Durante questo percorso, Jane migliora il modo in cui fornisce Stock Trader.

7. Modernizzazione della gestione. Todd e Jane hanno lavorato per migliorare il modo in cui gestiscono Stock Trader e la piattaforma su cui viene eseguito, anche in più di un cluster e in un ambiente cloud.

## Link correlati
{: #vcscontent-modjourney-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Introduzione a vCenter Server e IBM Kubernetes Service

Questo documento fornisce una panoramica del percorso di modernizzazione dell'applicazione a {{site.data.keyword.cloud}}, concentrandosi sugli aspetti di rete delle seguenti piattaforme per consentire l'utilizzo di un multicloud integrato per la modernizzazione dell'applicazione:

Questo documento fornisce una panoramica del percorso di modernizzazione dell'applicazione a {{site.data.keyword.cloud_notm}}, concentrandosi sui componenti di gestione cloud per consentire un multicloud integrato da utilizzare per la modernizzazione dell'applicazione:

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server è un'offerta da {{site.data.keyword.vmwaresolutions_full}} ed è una piattaforma basata su VMware di cui viene automaticamente eseguito il provisioning su {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.cloud_notm}}Private** - ICP è una piattaforma dell'applicazione per lo sviluppo e la gestione di applicazioni inserite nel contenitore, che sono distribuite su piattaforme dell'infrastruttura virtualizzate, come ad esempio VMware.
- **IBM Kubernetes Services** - IKS è un servizio gestito su {{site.data.keyword.cloud_notm}} che si avvale di Kubernetes come motore di orchestrazione per l'automazione della distribuzione, del ridimensionamento e delle operazioni dei contenitori dell'applicazione in un solo cluster tenant.
- **IBM Multi-Cluster Manager** – MCM fornisce la visibilità utente, la gestione incentrata sull'applicazione (politica, distribuzioni, integrità, operazioni) e conformità basata sulle politiche tra i cloud e i cluster. Con MCM, hai il controllo dei tuoi cluster Kubernetes.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM è un una piattaforma self-service multicloud che viene eseguita su ICP che consente agli sviluppatori e agli amministratori di soddisfare le richieste di business.

## Modernizzazione dell'applicazione su IBM Cloud
La modernizzazione dell'applicazione è un termine che descrive il processo di transizione delle applicazioni esistenti per utilizzare nuovi approcci sul cloud. I clienti oggi cercano approcci innovativi ed efficienti che li aiutino a fare questa transizione in base alla complessità aziendale e dell'applicazione.

Le pressioni economiche richiedono un tempo più veloce per il mercato. Il tuo patrimonio esistente include non solo le applicazioni, ma i dati, i processi, la logica aziendale e le interfacce utente, che devono tutti adattarsi per tenere il passo con le nuove esigenze aziendali.

I vantaggi della modernizzazione dell'applicazione includono quanto segue:
- Produttività degli sviluppatori migliorata
- Aumento dell'efficienza operativa.
- Costi ridotti per la creazione di nuove funzionalità.
- Capacità espansa consegnata in breve tempo.

IBM comprende che il 70% delle adozioni cloud private è da attribuire alla necessità di modernizzare gli ambienti dell'applicazione; tuttavia, la maggior parte delle organizzazioni si sta avvicinando all'ammodernamento dell'applicazione con un approccio a stadi, che necessita di uno scenario ibrido e multicloud, dove:
- Applicazioni legacy complesse e monolitiche che in genere vengono eseguite su mainframe o sistemi UNIX restino locali.
- Gli ambienti x86 utilizzati per i SoR (system of record), le applicazioni sensibili alla sicurezza e i carichi di lavoro regolamentati vengono collocati sull'infrastruttura virtualizzata o su un cloud privato.
- Applicazioni come SAP o il calcolo ad elevate prestazioni utilizzano risorse bare metal.
- Alcuni carichi di lavoro regolamentati e importanti per la sicurezza, che possono essere spostati nel cloud pubblico si stanno spostando negli ambienti dedicati.
- SoE (Systems of engagement) come web, mobile, IoT, AI o Video si stanno spostando sui cloud pubblici.

Ad esempio, un modello comune consiste nel disporre di applicazioni SOE di frontend distribuite come contenitori con database e middleware legacy distribuito sulle VM su un cloud privato.

Poiché le tue esigenze di infrastruttura IT e di business sono uniche, hai bisogno di un approccio alla modernizzazione che aiuti ad accelerare la distribuzione del valore commerciale, che riduca i tuoi rischi e preservi i tuoi investimenti esistenti. IBM fornisce proprio un approccio di questo tipo che può essere personalizzato per affrontare le tue esigenze di tecnologia e di business univoche correlate alla modernizzazione dell'applicazione.

Questo documento è uno dei cinque documenti che fornisce diverse panoramiche sulle tecnologie utilizzate nel percorso di modernizzazione dell'applicazione a {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - un'architettura di riferimento per la distribuzione delle seguenti piattaforme:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - un'offerta da {{site.data.keyword.vmwaresolutions_full}} ed è una piattaforma basata su VMware di cui viene automaticamente eseguito il provisioning su {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}}Private** - una piattaforma dell'applicazione per lo sviluppo e la gestione delle applicazioni inserite nei contenitori. ICP è un ambiente integrato che include l'orchestrazione del contenitore Kubernetes e un repository di immagini privato, una console di gestione, i framework di monitoraggio e un'interfaccia utente grafica che fornisce un'ubicazione centralizzata da cui puoi distribuire, gestire, monitorare e ridimensionare le tue applicazioni.
  - **{{site.data.keyword.cloud_notm}}Automation Manager** - una piattaforma IaC (infrastructure as code) pronta per le aziende che fornisce un unico pannello di controllo per eseguire il provisioning dei carichi di lavoro basati su VM insieme a carichi di lavoro basati su Kubernetes utilizzando i template archiviati e forniti di versione in un repository.
* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsiks/vcsiks-intro.html) - un'architettura di riferimento per la distribuzione delle seguenti piattaforme:
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - un'offerta da {{site.data.keyword.vmwaresolutions_full}} ed è una piattaforma basata su VMware di cui viene automaticamente eseguito il provisioning su {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}}Kubernetes Service** – servizio gestito su {{site.data.keyword.cloud_notm}} che utilizza Kubernetes come motore di orchestrazione per automatizzare la distribuzione, il ridimensionamento e le operazioni dei contenitori dell'applicazione in un cluster a singolo tenant.
* [Rete di vCenter Server](../vcsnsxt/vcsnsxt-intro.html) - si concentra sulle tecnologie di rete utilizzate in vCenter Server, ICP e IKS quali NSX-V, NSX-T e Calico.
* [Guida di VMware e Skate Advisor Concept Car](../vcscar/vcscar-intro.html) - questa architettura di riferimento è una “concept car”, cioè, un meccanismo per evidenziare e illustrare le tecnologie che risolvono problemi reali. Vogliamo dimostrare un'interazione tra l'intelligenza artificiale Watson e il machine learning in modo reale. Attraverso la cultura dello skateboarding, dimostriamo i servizi cloud in un modo unico. L'implementazione della “concept car” è un'estensione all'applicazione Acme Skateboard chiamata Skate Advisor. Skate Advisor è uno strumento, che permette agli utenti di avere conversazioni di skateboarding con un motore controllato da Watson.
* [VMware: il percorso di modernizzazione di Stock Trader](../vcscontent/vcscontent-modjourney.html) - i nostri casi di utilizzo di riferimento descrivono un'applicazione WebSphere Application Server che viene modernizzata utilizzando {{site.data.keyword.cloud_notm}} Private, il contenuto di IBM Middleware, {{site.data.keyword.cloud_notm}} Kubernetes Service e vCenter Server on {{site.data.keyword.cloud_notm}}. Siamo tutti su un percorso cloud e a diversi punti del percorso. Tramite passi incrementali da parte dell'architetto dell'applicazione, Jane, e dell'architetto dell'infrastruttura cloud, Todd, modernizziamo un'applicazione esistente chiamata Stock Trader. Mostra esempi che ti aiutano ad intraprendere ogni passo del tuo percorso e il valore realizzato dal tuo business, indipendentemente da quanto grande o piccolo sia ogni passo. Ci concentriamo su quattro temi: applicazioni, DevOps, integrazione e gestione. Ognuno viene utilizzato per aiutarti a raggiungere i tuoi obiettivi, e in realtà, a modernizzarne uno senza che gli altri creino alcun problema.

### Link correlati

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
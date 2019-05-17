---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Introduzione a VMware e Skate Advisor Concept Car
{: #vcscar-intro}

La seguente architettura di riferimento è una “concept car”, ossia un meccanismo per
evidenziare e mostrare le tecnologie che risolvono i problemi del mondo reale. La “concept car” non rappresenta in alcun modo
un servizio facilmente disponibile oggi.

L'architettura di riferimento fornisce anche le seguenti informazioni:

-   Fornisce un linguaggio comune per le varie parti interessate.
-   Fornisce coerenza nell'implementazione della tecnologia per risolvere i problemi.
-   Supporta la convalida delle soluzioni rispetto a un'architettura di riferimento
comprovata.
-   Incoraggia l'adesione a standard,
specifiche e modelli comuni.

## Informazioni su ACME Skate Advisor
{: #vcscar-intro-about}

Volevamo dimostrare un'interazione tra il machine learning e l'intelligenza
artificiale di Watson in modo reale e attraverso di essa esplorare
più in profondità la cultura dello skateboarding. Mostriamo i servizi disponibili e l'infrastruttura cloud in
modo univoco, dimostrando la capacità tecnica e i progressi in questa
area. L'implementazione della “concept car” è un'estensione
dell'applicazione dimostrativa Acme Skateboard chiamata Skate Advisor. Skate Advisor è uno strumento, che permette agli utenti di avere conversazioni di skateboarding con un motore controllato da Watson. Le seguenti citazioni sono una conversazione di esempio:

-   “Watson, mostrami le combinazioni del trick Casper”
-   “Watson, mostrami le posizioni comuni per eseguire un trick”
-   “Watson, mostrami un video del trick Casper”

Acme Skate Advisor si avvale del servizio Watson Discovery per
acquisire articoli, video, blog e altri contenuti basati su Internet per
creare un database aggiornato di trick, che può essere interrogato
dall'applicazione.

L'applicazione Skate Advisor viene implementata anche sulla piattaforma
di modernizzazione dell'applicazione, che fornisce servizi basati su contenitore attraverso
{{site.data.keyword.icpfull_notm}} ospitato sulla piattaforma {{site.data.keyword.cloud_notm}} for VMware Services.

L'applicazione Acme Skate Advisor sfrutta sia la piattaforma Watson
che la piattaforma di modernizzazione dell'applicazione.

## Casi di utilizzo
{: #vcscar-intro-use-cases}

### Dimostrazione di modernizzazione dell'applicazione
{: #vcscar-intro-app-mod-demo}

Dimostrare un'applicazione che è stata distribuita nella piattaforma
di modernizzazione dell'applicazione. La piattaforma include componenti {{site.data.keyword.icpfull_notm}}, CAM e NSX
distribuiti su {{site.data.keyword.cloud_notm}} per l'offerta VMware vCenter Server
on {{site.data.keyword.cloud_notm}}.

### Riconoscimento vocale di Watson con Watson Assistant
{: #vcscar-intro-speech}

Acme Skate Advisor comunica con gli utenti attraverso un servizio speech-to-text e
text-to-speech fornito con la piattaforma Watson.

### Utilizzo e formazione del servizio Watson Discovery
{: #vcscar-intro-watson-disc}

Acme Skate Advisor utilizza i servizi Watson Discovery per tenere
traccia di un database di trick per cui viene applicato un linguaggio di classificazione e i trick rilevati dai servizi online.

### Utilizzo dei servizi Watson
{: #vcscar-intro-watson-services}

Per creare Acme Skate Advisor sono stati utilizzati i seguenti servizi
Watson:
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## Modernizzazione dell'applicazione su IBM Cloud
{: #vcscar-intro-app-mod}

La modernizzazione dell'applicazione è un termine che descrive il processo di transizione delle applicazioni esistenti per utilizzare nuovi approcci di sviluppo e fornitura sul cloud. I clienti oggi cercano approcci innovativi ed efficienti che li aiutino a fare questa transizione in base alla complessità aziendale e dell'applicazione.

Le pressioni economiche richiedono un tempo più veloce per il mercato. Il tuo patrimonio esistente include non solo le applicazioni, ma i dati, i processi, la logica aziendale e le interfacce utente, che devono tutti adattarsi per tenere il passo con le nuove esigenze aziendali.

Il seguente elenco descrive i vantaggi della modernizzazione dell'applicazione:
- Migliora la produttività degli sviluppatori
- Aumenta l'efficienza operativa
- Riduce i costi per creare nuove funzioni
- Espande la capacità fornita in un breve periodo

IBM comprende che il 70 percento dell'adozione del cloud privato è guidato
dalla necessità di modernizzare gli ambienti dell'applicazione. Tuttavia, la maggior
parte delle organizzazioni si sta avvicinando alla modernizzazione dell'applicazione
con un approccio a più fasi, che richiede un panorama ibrido e multi-cloud, in cui:

- Le applicazioni heritage complesse e monolitiche che tipicamente vengono eseguite su mainframe o sistemi UNIX rimangono in loco.
- Gli ambienti x86 utilizzati per i SoR (System of Record), le applicazioni sensibili alla sicurezza e i carichi di lavoro regolamentati vengono collocati su un'infrastruttura virtualizzata o su un cloud privato.
- Applicazioni come SAP o il calcolo ad alte prestazioni utilizzano risorse bare
metal.
- Alcuni carichi di lavoro regolamentati e importanti per la sicurezza, che possono essere spostati nel cloud pubblico si stanno spostando negli ambienti dedicati.
- I System of Engagement (SoE) come web, mobile, IoT, AI o Video si stanno spostando sui cloud pubblici.

Ad esempio, un modello comune è quello di avere applicazioni SOE di front-end distribuite come contenitori con database e middleware heritage distribuito
sulle VM su un cloud privato.

Poiché le esigenze di infrastruttura IT e aziendali sono uniche, un approccio alla modernizzazione deve fornire le seguenti priorità:

* Accelerare il valore aziendale
* Ridurre il tempo di consegna
* Ridurre i rischi
* Preservare gli investimenti esistenti.

IBM fornisce proprio un approccio di questo tipo alla modernizzazione
dell'applicazione che può essere personalizzato per affrontare le tue esigenze
uniche di tecnologia e di business.

I seguenti documenti forniscono diversi punti di vista sulle tecnologie utilizzate nel percorso di modernizzazione dell'applicazione in {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - Un'architettura di riferimento per la distribuzione delle seguenti piattaforme.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server è un'offerta di {{site.data.keyword.vmwaresolutions_short}}, che è una piattaforma basata su VMware fornita automaticamente su {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.icpfull_notm}}** – {{site.data.keyword.icpfull_notm}} è una piattaforma dell'applicazione per lo sviluppo e la gestione delle applicazioni inserite nei contenitori. {{site.data.keyword.icpfull_notm}} è un ambiente integrato che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione, i framework di monitoraggio e un'interfaccia utente grafica. L'interfaccia utente fornisce una posizione centralizzata da cui puoi distribuire, gestire, monitorare e ridimensionare le tue applicazioni.
   - **IBM Cloud Automation Manager** – CAM è una piattaforma IaC (Infrastructure as Code) pronta per le aziende che fornisce un unico pannello di controllo per il provisioning dei carichi di lavoro basati su VM insieme ai carichi di lavoro basati su Kubernetes utilizzando modelli archiviati e forniti di versione in un repository.
* [vCenter Server e {{site.data.keyword.containerlong_notm}} Service](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - Un'architettura di riferimento per la distribuzione delle seguenti piattaforme.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server è un'offerta di {{site.data.keyword.vmwaresolutions_short}}, che è una piattaforma basata su VMware fornita automaticamente su {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.containerlong_notm}}** – {{site.data.keyword.containerlong_notm}} è un servizio gestito su {{site.data.keyword.cloud_notm}} che utilizza Kubernetes come motore di orchestrazione per automatizzare la distribuzione, il ridimensionamento e le operazioni dei contenitori dell'applicazione in un cluster a singolo tenant.
* [Rete di vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - Si concentra sulle tecnologie di rete utilizzate per l'integrazione tra vCenter Server, {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}} come NSX-V e Calico insieme a un'anteprima della tecnologia di NSX-T.
* _Guida di VMware e Skate Advisor Concept Car_ - Un'architettura di riferimento che è una “concept car”, ossia un meccanismo per evidenziare e mostrare le tecnologie che risolvono i problemi del mondo reale. Vogliamo dimostrare un'interazione tra l'intelligenza artificiale Watson e il machine learning in modo reale. Attraverso la cultura dello skateboarding, dimostriamo i servizi cloud in un modo unico. L'implementazione della “concept car” è un'estensione all'applicazione Acme Skateboard chiamata Skate Advisor. Skate Advisor è uno strumento, che permette agli utenti di avere conversazioni di skateboarding con un motore controllato da Watson.
* [VMware: il percorso di modernizzazione di Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - Un caso di utilizzo di riferimento che descrive una classica applicazione WebSphere Application Server che viene modernizzata utilizzando {{site.data.keyword.cloud_notm}} Private, il contenuto di IBM Middleware, {{site.data.keyword.containerlong_notm}} e vCenter Server on {{site.data.keyword.cloud_notm}}. Siamo tutti su un percorso nel cloud e a diversi punti del percorso. Tramite passi incrementali da parte dell'architetto dell'applicazione, Jane, e dell'architetto dell'infrastruttura cloud, Todd, modernizziamo un'applicazione esistente chiamata Stock Trader. Esamina gli esempi che ti aiutano a compiere ogni passo del tuo percorso e il valore che viene realizzato per il tuo business, indipendentemente da quanto grande o piccolo sia ciascun passo. Ci concentriamo su quattro temi: applicazioni, DevOps, integrazione e gestione. Tutti i temi operano insieme per aiutarti a raggiungere i tuoi obiettivi. Modernizzare un tema e non gli altri potrebbe creare dei problemi.

## Link correlati
{: #vcscar-intro-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Introduzione alla rete vCenter Server

Questo documento fornisce una panoramica del percorso di modernizzazione dell'applicazione a {{site.data.keyword.cloud}}, concentrandosi sugli aspetti di rete delle seguenti piattaforme per consentire l'utilizzo di un multicloud integrato per la modernizzazione dell'applicazione:

- **VMware vCenter Server on IBM Cloud** - un'offerta da {{site.data.keyword.vmwaresolutions_short}}, che è una piattaforma basata su VMware di cui viene eseguito automaticamente il provisioning su {{site.data.keyword.cloud_notm}}.
- **IBM Cloud Private** - una piattaforma applicativa per sviluppare e gestire applicazioni inserite nel contenitore, che sono distribuite su una piattaforma dell'infrastruttura virtualizzata, come VCS oppure un ambiente vSphere in loco.
- **IBM Kubernetes Services** - un servizio gestito su {{site.data.keyword.cloud_notm}} che utilizza Kubernetes come motore di orchestrazione per automatizzare la distribuzione, il ridimensionamento e le operazioni dei contenitori dell'applicazione in un cluster a singolo tenant.

Le maggiori sfide in materia di modernizzazione delle applicazioni sono la migrazione, la rete e la sicurezza. VCS, VMware HCX (Hybrid Cloud Extension), VMware NSX, IKS e ICP aiutano a risolvere alcune di queste sfide. La seguente architettura di rete descrive un approccio che utilizza Acme Skateboards come un esempio per connettere i componenti che sono suddivisi tra ambienti cloud e in loco.

L'[anteprima NSX-T](vcsnsxt-techpreview.html) è un'anteprima tecnologica per descrivere l'uso di VMware NSX-T (NSX Transformers) in una futura architettura di riferimento. NSX-T è progettato per occuparsi di architetture e framework applicativi che presentano endpoint e stack di tecnologie eterogenei. Oltre a vSphere, questi ambienti possono includere altri hypervisor, KVM, contenitori e bare metal. NSX-T consente ai team IT e di sviluppo di scegliere le tecnologie più adatte alle loro applicazioni. NSX-T è anche progettato per la gestione, le operazioni e il consumo da parte delle organizzazioni di sviluppo, oltre ai team di rete.

## Modernizzazione dell'applicazione su IBM Cloud

La modernizzazione dell'applicazione è un termine che descrive il processo di transizione delle applicazioni esistenti per utilizzare nuovi approcci di sviluppo e fornitura sul cloud. I clienti oggi cercano approcci innovativi ed efficienti che li aiutino a fare questa transizione in base alla complessità aziendale e dell'applicazione.

Le pressioni economiche richiedono un tempo più veloce per il mercato. Il tuo patrimonio esistente include non solo le applicazioni, ma i dati, i processi, la logica aziendale e le interfacce utente, che devono tutti adattarsi per tenere il passo con le nuove esigenze aziendali.

I vantaggi della modernizzazione dell'applicazione includono quanto segue:

- Migliora la produttività degli sviluppatori
- Aumenta l'efficienza operativa
- Riduce il costo per creare nuove funzionalità
- Espande la capacità fornita in un breve periodo

IBM comprende che il 70% delle adozioni cloud private è guidato dalla necessità di modernizzare gli ambienti dell'applicazione; tuttavia, la maggior parte delle organizzazioni si sta avvicinando all'ammodernamento dell'applicazione con un approccio a stadi, che necessita di uno scenario ibrido e multicloud, dove:

- Applicazioni legacy complesse e monolitiche che in genere vengono eseguite su mainframe o sistemi UNIX restino locali.
- Gli ambienti x86 utilizzati per i SoR (System of Record), le applicazioni sensibili alla sicurezza e i carichi di lavoro regolamentati vengono collocati sull'infrastruttura virtualizzata o su un cloud privato.
- Applicazioni come SAP o il calcolo ad elevate prestazioni utilizzano risorse bare metal.
- Alcuni carichi di lavoro regolamentati e importanti per la sicurezza, che possono essere spostati nel cloud pubblico si stanno spostando negli ambienti dedicati.
- I System of Engagement (SoE) come web, mobile, IoT, AI o Video si stanno spostando sui cloud pubblici.

Ad esempio, un modello comune consiste nel disporre di applicazioni SoE di frontend distribuite come contenitori con database e middleware legacy distribuito sulle VM su un cloud privato.

Poiché le tue esigenze di infrastruttura IT e di business sono uniche, hai bisogno di un approccio alla modernizzazione che acceleri il valore di business, riduca al minimo il tempo di fornitura, riduca i tuoi rischi e preservi i tuoi investimenti esistenti. IBM fornisce proprio un approccio di questo tipo alla modernizzazione dell'applicazione che può essere personalizzato per affrontare le tue esigenze uniche di tecnologia e di business.

Questo documento fornisce cinque panoramiche differenti alle tecnologie utilizzate nel percorso di modernizzazione dell'applicazione a {{site.data.keyword.cloud_notm}}:

* [vCenter Server e {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - questa guida è un'architettura di riferimento per la distribuzione delle seguenti piattaforme:
   - **VMware vCenter Server on IBM Cloud** - un'offerta da {{site.data.keyword.vmwaresolutions_short}}, che è una piattaforma basata su VMware di cui viene eseguito automaticamente il provisioning su {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Private** – ICP è una piattaforma dell'applicazione per lo sviluppo e la gestione delle applicazioni inserite nei contenitori. È un ambiente integrato che include l'orchestrazione del contenitore Kubernetes, nonché un repository di immagini privato, una console di gestione, i framework di monitoraggio e un'interfaccia utente grafica che fornisce un'ubicazione centralizzata da cui puoi distribuire, gestire, monitorare e ridimensionare le tue applicazioni.
   - **IBM Cloud Automation Manager** - CAM è una piattaforma IaC (Infrastructure as Code) pronta per le aziende che fornisce un unico pannello di controllo per eseguire il provisioning dei carichi di lavoro basati su VM insieme a carichi di lavoro basati su Kubernetes semplicemente utilizzando i modelli archiviati e forniti di versione in un repository.
* [Servizio vCenter Server e IBM Kubernetes](../vcsiks/vcsiks-intro.html) - questa guida è un'architettura di riferimento per la distribuzione delle seguenti piattaforme:
   - **VMware vCenter Server on IBM Cloud** - un'offerta da {{site.data.keyword.vmwaresolutions_short}}, che è una piattaforma basata su VMware di cui viene eseguito automaticamente il provisioning su {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Kubernetes Service** – un servizio gestito su {{site.data.keyword.cloud_notm}} che utilizza Kubernetes come motore di orchestrazione per automatizzare la distribuzione, il ridimensionamento e le operazioni dei contenitori dell'applicazione in un cluster a singolo tenant.
* _Rete di vCenter Server_ - questa guida si concentra sulle tecnologie di rete utilizzate per l'integrazione tra VCS, ICP e IKS quali NSX-V e Calico insieme a un'anteprima tecnologica di NSX-T.
* [Guida di VMware e Skate Advisor Concept Car](../vcscar/vcscar-intro.html) - questa architettura di riferimento è una “concept car”, cioè, un meccanismo per evidenziare e illustrare le tecnologie per risolvere i problemi reali. Vogliamo dimostrare un'interazione tra l'intelligenza artificiale Watson e il machine learning in modo reale. Soprattutto, attraverso la cultura dello skateboarding, dimostreremo i servizi cloud in modo unico. L'implementazione della “concept car” è un'estensione all'applicazione Acme Skateboard chiamata Skate Advisor. Skate Advisor è uno strumento, che permette agli utenti di avere conversazioni di skateboarding con un motore controllato da Watson.
* [VMware: il percorso di modernizzazione di Stock Trader](../vcscontent/vcscontent-modjourney.html) - i nostri casi di utilizzo di riferimento descrivono un'applicazione WebSphere Application Server che viene modernizzata utilizzando {{site.data.keyword.cloud_notm}} Private, il contenuto di IBM Middleware, {{site.data.keyword.cloud_notm}} Kubernetes Service e vCenter Server on {{site.data.keyword.cloud_notm}}. Siamo tutti su un percorso cloud e a diversi punti del percorso. Tramite passi incrementali da parte dell'architetto dell'applicazione, Jane, e dell'architetto dell'infrastruttura cloud, Todd, modernizziamo un'applicazione esistente chiamata Stock Trader. Mostra esempi che ti aiutano ad intraprendere ogni passo del tuo percorso e il valore realizzato dal tuo business, indipendentemente da quanto grande o piccolo sia ogni passo. Ci concentriamo su quattro temi: applicazioni, DevOps, integrazione e gestione. Ognuno viene utilizzato per aiutarti a raggiungere i tuoi obiettivi, e in realtà, a modernizzarne uno senza che gli altri creino alcun problema.

### Link correlati

* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)
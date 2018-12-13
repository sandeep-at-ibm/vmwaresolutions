---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Panoramica sulla modernizzazione dell'applicazione

Il seguente diagramma mostra l'architettura di riferimento di modernizzazione dell'applicazione che Acme Skateboards distribuisce ed è descritta approfonditamente in questa serie di documenti.

Figura 1. Panoramica dell'architettura
![Diagramma di panoramica dell'architettura](vcsnsxt-aod.svg)

Questa architettura ibrida consente ad Acme Skateboards di:
- Migrare le macchine virtuali (VM) VMware che sono in loco a {{site.data.keyword.cloud}} con poco o nessun tempo di inattività e nessuna riconfigurazione dell'applicazione.
-	Abilitarle ad avviare il percorso di modernizzazione dell'applicazione permettendo loro di concentrarsi sull'inserire nel contenitore le interfacce web più semplici e middleware, consentendo ai database più complessi di rimanere VM.
-	Utilizzare CAM (Cloud Automation Manager) per eseguire lo script dell'infrastruttura come codice (IaC) per creare e orchestrare i servizi creati sia dalle VM che dai contenitori con le relative toolchain DevOps e la loro soluzione ITSM.

Ponendo l'accento sull'architettura di rete, l'architettura di riferimento ha i seguenti componenti chiave:
- **Virtualizzazione in loco** - Questo è un cluster VMware che attualmente ospita le VM Acme Skateboards. Sono queste VM che attualmente ospitano le applicazioni che saranno modernizzate. Questo cluster è necessario per soddisfare i prerequisiti come documentato nel documento [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) in modo da poter eseguire HCX. HCX estende le reti in loco in {{site.data.keyword.cloud_notm}} consentendo ai clienti di migrare le VM nell'istanza VCS in esecuzione su {{site.data.keyword.cloud_notm}} e nell'altro senso, se necessario.
- **VMware vCenter Server on IBM Cloud** – VCS fornisce i blocchi di generazione VMware fondamentali: vSphere, vCenter Server, NSX-V e le opzioni di archiviazione che includono vSAN oppure l'archiviazione {{site.data.keyword.cloud_notm}} Endurance, che occorrono per distribuire automaticamente una soluzione VMware SDDC (Software Defined Data Center). Questo cluster VMware è la destinazione delle VM migrate così come di alcune delle applicazioni modernizzate nei contenitori ospitati in ICP.

  I componenti chiave dell'architettura sono:
 - **NSX-V** - NSX-V fornisce il livello di virtualizzazione di rete in VCS che fornisce una sovrapposizione di rete per le VM Acme Skateboards. NSX-V abilita BYOIP e isola le reti del carico di lavoro dalle reti {{site.data.keyword.cloud_notm}}  NSX-V è programmato da HCX per creare le reti che Acme Skateboards estenderà dal locale.
 - **IBM Cloud Private** - ICP è una piattaforma dell'applicazione per lo sviluppo e la gestione delle applicazioni inserite nei contenitori. È un ambiente integrato che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione, i framework di monitoraggio e un'interfaccia utente grafica che fornisce un'ubicazione centralizzata da cui Acme Skateboards può distribuire, gestire, monitorare e ridimensionare le proprie applicazioni. L'istanza VCS ospita i componenti ICP, i nodi master, i nodi di lavoro e così via, eseguendoli come VM. 
  -	**IBM Cloud Automation Manager** – CAM è una piattaforma IaC (infrastructure as code) pronta per le aziende che fornisce un singolo pannello di controllo per il provisioning di carichi di lavoro basati sulle macchine virtuali insieme a carichi di lavoro basati su Kubernetes semplicemente utilizzando i template. CAM è un'applicazione di Docker eseguita su ICP ed è strettamente integrata per l'autorizzazione, il controllo dell'accesso basato sul ruolo (RBAC) e altre funzioni.
  - **IBM Kubernetes Service** - IKS consente a Acme Skateboards di distribuire le proprie applicazioni modernizzate in contenitori Docker che vengono eseguiti in cluster Kubernetes. Le modalità principali sono gestite completamente da IBM mentre i nodi di lavoro nel pool di lavoro vengono distribuiti nello stesso account di {{site.data.keyword.cloud_notm}} dell'istanza VCS. I nodi di lavoro sono istanze bare metal, pubbliche o del server virtuale dedicate. Calico viene installato e configurato automaticamente in IKS. Calico fornisce la connettività di rete sicura per i contenitori ed è configurato in IKS per utilizzare l'incapsulamento IP-in-IP per incapsulare i pacchetti che transitano attraverso le sottoreti e utilizza NAT per connessioni in uscita dai contenitori.
  - **Direct Link** - {{site.data.keyword.cloud_notm}} Direct Link utilizza il provider WAN di Acme Skateboards per connettere il relativo data center a {{site.data.keyword.cloud_notm}} fornendo una connessione di rete sicura, a bassa latenza e affidabile. Questa connessione fornisce:
      - Accesso alle applicazioni ospitate cloud dai tuoi utenti Enterprise.
      - Traffico VM interno tra le VM in loco e cloud.
      - Traffico tra i sistemi legacy nel data center in loco e le VM cloud.

## Vantaggi chiave di Acme Skateboards

-	Fornitura accelerata di progetti IT per sviluppatori e linee di business riducendo il tempo necessario per approvvigionamento, architettura, implementazione e distribuzione di risorse da settimane, o anche mesi, ad alcune ore. Il time-to-value diminuisce se devono attendere finché i team di rete o di sicurezza potranno fornire servizi quali i programmi di bilanciamento del carico, i firewall, gli switch e i router.
-	Sicurezza migliorata con server bare metal dedicati in un cloud privato ospitato, inclusa la distribuzione dell'endpoint privato ai servizi {{site.data.keyword.cloud_notm}} quali IKS e KMIP.
-	Gestione e governance coerenti del cloud ibrido distribuito fornendo un accesso amministrativo completo alla gestione della virtualizzazione, preservando così gli strumenti, gli script e gli investimenti VMware esistenti nella formazione.
-	Competenze VMware su scala globale con i servizi professionali e gestiti di IBM disponibili in più di 30 {{site.data.keyword.CloudDataCents_notm}} in tutto il mondo.

I clienti che passano a piattaforme dell'applicazione native cloud come ICP e IKS che sono incentrate sulla velocità e l'innovazione e non sempre tengono conto della rete e della sicurezza. Questa architettura di riferimento mostra come VCS, ICP e IKS passino in modo sicuro Acme Skateboards insieme al percorso di modernizzazione dell'applicazione.

## Link correlati 

* [Panoramica di VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Panoramica sull'architettura
{: #vcsiks-arch-overview}

Le offerte {{site.data.keyword.vmwaresolutions_full}} forniscono l'automazione per distribuire
i componenti di tecnologia VMware nei {{site.data.keyword.CloudDataCents_notm}} in tutto il mondo. L'architettura consiste in una singola regione cloud e supporta la capacità di estensione in più regioni cloud che si trovano in un'altra area geografica o in un altro pod di {{site.data.keyword.cloud_notm}} all'interno dello stesso data center.

Puoi distribuire manualmente i prodotti {{site.data.keyword.icpfull_notm}} e CAM (Cloud Automation Manager) nella tua piattaforma di virtualizzazione in loco,
abilitando la gestione cloud dalle ubicazioni in loco. In alternativa, {{site.data.keyword.icpfull_notm}}
e CAM vengono offerti come estensioni di servizio a una distribuzione VMware
vCenter Server on {{site.data.keyword.cloud_notm}} nuova o esistente, tramite l'automazione, abilitando
la gestione cloud da {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.icpfull_notm}} è una piattaforma dell'applicazione per lo sviluppo e la gestione di applicazioni
inserite nei contenitori in loco. {{site.data.keyword.icpfull_notm}} è un ambiente integrato per la gestione
dei contenitori che include l'orchestrazione del contenitore Kubernetes, un
repository di immagini privato, una console di gestione e i
framework di monitoraggio.

IBM Multi-Cluster Manager fornisce visibilità utente, gestione incentrata
sull'applicazione (politica, distribuzioni, integrità, operazioni) e conformità
basata sulle politiche tra i cloud e i cluster. Con IBM Multi-Cluster Manager,
hai il controllo dei tuoi cluster Kubernetes. Puoi garantire che i tuoi
cluster siano sicuri, che funzionino in modo efficiente e che forniscano i livelli
di servizio previsti dalle applicazioni.

{{site.data.keyword.cloud_notm}} Automation Manager è una piattaforma di gestione self service multi-cloud
eseguita su {{site.data.keyword.cloud_notm}} Private che permette a sviluppatori e
amministratori di soddisfare le richieste di business. Cloud Automation Manager
Service Composer ti consente di esporre i servizi cloud ibridi nel catalogo IBM
Cloud Private.

## Piattaforma di gestione cloud lato IBM Cloud
{: #vcsiks-arch-overview-ibm-cloud-side}

Il seguente diagramma visualizza {{site.data.keyword.icpfull_notm}} e CAM distribuiti con l'infrastruttura {{site.data.keyword.cloud_notm}},
con connessioni al vCenter in loco e al servizio {{site.data.keyword.containerlong_notm}} distribuiti su {{site.data.keyword.cloud_notm}}. Gli utenti possono distribuire macchine virtuali (VM) in loco, VM nelle istanze
vCenter Server e contenitori al cluster {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}.

Figura 1. Gestione cloud dal lato cloud
![Sul cloud - gestione cloud](vcsiks-oncloud-cloudmgt.svg)

Nel diagramma, CAM crea in modo logico le connessioni cloud ai vCenter,
ai provider cloud e agli ambienti {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}. I cluster {{site.data.keyword.icpfull_notm}} devono essere
distribuiti in ciascun data center o ambiente cloud, con MCM che fornisce il
meccanismo per connettere i cluster {{site.data.keyword.icpfull_notm}} in un'unica vista di gestione.

{{site.data.keyword.icpfull_notm}} può essere distribuito con i componenti NSX-V o NSX-T. {{site.data.keyword.icpfull_notm}} con NSX-V
consente alle VM {{site.data.keyword.icpfull_notm}} l'esecuzione sulla rete VXLAN e di utilizzare
la rete interna Kubernetes Calico.

{{site.data.keyword.icpfull_notm}} con NSX-T consente agli utenti di controllare e configurare la rete,
la sottorete e le politiche dall'IU centrale (NSX-T Manager). Per informazioni sulle differenze tra NSX-V e NSX-T, vedi l'[architettura di riferimento di rete {{site.data.keyword.cloud_notm}} VCS](/docs/services/vmwaresolutions/archiref/
vcsnsxt/vcsnsxt-intro.html).

## Piattaforma di gestione cloud in loco
{: #vcsiks-arch-overview-on-premises}

Il seguente diagramma visualizza {{site.data.keyword.icpfull_notm}} e CAM distribuiti nell'infrastruttura
in loco, con connessioni a vCenter e {{site.data.keyword.containerlong_notm}} distribuiti su {{site.data.keyword.cloud_notm}}. Gli utenti possono distribuire VM e contenitori
in loco, VM nelle istanze vCenter Server e contenitori
al cluster {{site.data.keyword.containerlong_notm}}.

Figura 2. Gestione cloud dal lato locale
![In loco - gestione cloud](vcsiks-onprem-cloudmgt.svg)

La VPN strongSwan viene utilizzata per stabilire la connettività con i contenitori
{{site.data.keyword.containerlong_notm}} distribuiti. Con il tempo, strongSwan potrebbe essere sostituito con la connettività
Direct-link.

Nel diagramma, CAM crea in modo logico le connessioni cloud ai vCenter,
ai provider cloud e agli ambienti {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}. I cluster {{site.data.keyword.icpfull_notm}} devono essere
distribuiti in ciascun data center o ambiente cloud, con MCM che fornisce il
meccanismo per connettere i cluster {{site.data.keyword.icpfull_notm}} in un'unica vista di gestione.

## Link correlati
{: #vcsiks-arch-overview-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

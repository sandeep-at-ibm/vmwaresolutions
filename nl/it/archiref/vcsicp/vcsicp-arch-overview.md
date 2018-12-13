---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-15"

---

# Panoramica sull'architettura

Le offerte {{site.data.keyword.vmwaresolutions_full}} forniscono l'automazione per distribuire i componenti di tecnologia VMware nei {{site.data.keyword.CloudDataCents_notm}} in tutto il mondo.
L'architettura consiste in una singola regione cloud e supporta la capacità di estensione in più regioni cloud che si trovano in un'altra area geografica e/o in un altro pod di {{site.data.keyword.cloud_notm}} all'interno dello stesso data center.

Puoi distribuire manualmente i prodotti ICP ({{site.data.keyword.cloud_notm}} Private) e CAM (Cloud Automation Manager) nella tua piattaforma di virtualizzazione in loco, abilitando la gestione cloud dalle ubicazioni in loco. In alternativa, ICP e CAM sono offerti come estensioni del servizio a una distribuzione VMware vCenter Server on {{site.data.keyword.cloud_notm}} esistente o nuova, tramite l'automazione, abilitando la gestione cloud da {{site.data.keyword.cloud_notm}}.

ICP è una piattaforma dell'applicazione per lo sviluppo e la gestione in loco delle applicazioni inserite nei contenitori. ICP è un ambiente integrato per la gestione dei contenitori che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione e i framework di monitoraggio.

IBM Multi-Cluster Manager (MCM) fornisce la visibilità utente, la gestione incentrata sull'applicazione (politica, distribuzioni, integrità, operazioni) e conformità basata sulle politiche tra i cloud e i cluster. Con MCM, hai il controllo dei tuoi cluster Kubernetes. Puoi assicurarti che i tuoi cluster siano sicuri, funzionanti in modo efficiente e che stiano fornendo una piattaforma di gestione dei servizi che viene eseguita su ICP che consente agli sviluppatori e agli amministratori di soddisfare le richieste di business.
Utilizza Cloud Automation Manager Service Composer per visualizzare i servizi cloud ibridi nel catalogo ICP.

## Piattaforma di gestione cloud lato IBM Cloud

Il seguente diagramma è un esempio di una distribuzione ICP e CAM con l'infrastruttura {{site.data.keyword.cloud_notm}}, con connessioni al servizio vCenter in loco e al servizio IKS (IBM Kubernetes Service) distribuiti su {{site.data.keyword.cloud_notm}}. Gli utenti possono distribuire macchine virtuali (VM) in locale e VM in un'istanza vCenter Server e contenitori al cluster ICP e IKS.

Figura 1. Gestione cloud dal lato cloud

![Sul cloud - gestione cloud](vcsicp-oncloud-cloudmgt.svg)

Nel diagramma, CAM crea in modo logico le connessioni cloud ai vCenter, ai provider cloud, a ICP e agli ambienti IKS. I cluster ICP devono essere distribuiti ad ogni ambiente cloud di data center, con MCM che fornisce il meccanismo per collegare i cluster ICP in una singola vista di gestione.

Puoi distribuire ICP con componenti NSX-V o NSX-T. ICP con NSX-V, consente alle VM ICP l'esecuzione sulla rete VXLAN e di utilizzare la rete interna Kubernetes Calico.

ICP con NSX-T, consente agli utenti di controllare e configurare la rete, la sottorete, le politiche dall'IU centrale (NSX-T Manager). Consulta la [Guida di rete di vCenter Server](../vcsnsxt/vcsnsxt-intro.html) per le differenze tra NSX-V e NSX-T.

## Piattaforma di gestione cloud in loco

Il seguente diagramma è un esempio di una distribuzione ICP e CAM nell'infrastruttura in loco, con connessioni a vCenter e IKS distribuiti su {{site.data.keyword.cloud_notm}}. Gli utenti possono distribuire VM e contenitori in loco, VM nell'istanza vCenter Server e contenitori al cluster IKS.

Figura 2. Gestione cloud dal lato locale
![Gestione cloud in loco](vcsicp-onprem-cloudmgt.svg)

La VPN strongSwan viene utilizzata per stabilire la connettività con i contenitori IKS distribuiti. La VPN strongSwan potrebbe essere sostituita con la connettività Direct Link.

Nel diagramma, CAM crea in modo logico le connessioni cloud ai vCenter, ai provider cloud, a ICP e agli ambienti IKS. I cluster ICP devono essere distribuiti ad ogni ambiente cloud di data center, con MCM che fornisce il meccanismo per collegare i cluster ICP in una singola vista di gestione.

### Link correlati

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

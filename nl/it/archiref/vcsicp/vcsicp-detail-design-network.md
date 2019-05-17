---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Flussi e accesso di rete
{: #vcsicp-detail-design-network}

## Accesso all'applicazione del contenitore – IBM Cloud Private
{: #vcsicp-detail-design-network-container-icp}

Ci sono tre modi principali per ottenere il traffico esterno e l'accesso alle applicazioni del cluster Kubernetes:

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private
{: #vcsicp-detail-design-network-nodeport-icp}

Le Nodeport sono un modo semplice di esporre l'accesso esterno ad un carico di lavoro per la verifica e lo sviluppo iniziale ma non è consigliato per la produzione. Ingress o LoadBalancer sono il percorso consigliato.

### LoadBalancer - IBM Cloud Private
{: #vcsicp-detail-design-network-loadbalancer-icp}

Al momento, la piattaforma {{site.data.keyword.icpfull_notm}} supporta un LoadBalancer esterno per il carico di lavoro dell'applicazione.

### Ingress - IBM Cloud Private
{: #vcsicp-detail-design-network-ingress-icp}

Un Ingress è una raccolta di regole che consentono alle connessioni in entrata di raggiungere i servizi cluster. Può essere configurato per fornire URL raggiungibili esternamente dai servizi, il traffico di bilanciamento del carico, terminare l'SSL, offrire un host virtuale basato sul nome e altro ancora.  Il nodo Proxy nell'infrastruttura {{site.data.keyword.icpfull_notm}} esegue questa funzione.

## Accesso all'applicazione del contenitore – Servizio Kubernetes IBM Cloud
{: #vcsicp-detail-design-network-container-iks}

Ci sono tre modi principali per ottenere il traffico esterno e l'accesso alle applicazioni del cluster Kubernetes:

- NodePort
- LoadBalancer
- Ingress

### NodePort - Servizio Kubernetes IBM Cloud
{: #vcsicp-detail-design-network-nodeport-iks}

Le Nodeport sono un modo semplice di esporre l'accesso esterno ad un carico di lavoro per la verifica e lo sviluppo iniziale ma non è consigliato per la produzione. Ingress o LoadBalancer sono il percorso consigliato.

### LoadBalancer - Servizio Kubernetes IBM Cloud
{: #vcsicp-detail-design-network-loadbalancer-iks}

Ogni cluster {{site.data.keyword.containerlong_notm}} viene fornito con un programma di bilanciamento del carico dell'applicazione (ALB) pubblico o privato. L'ALB utilizza un punto di ingresso pubblico o privato sicuro e univoco per instradare le richieste in entrata alle tue applicazioni.

### Ingress - Servizio Kubernetes IBM Cloud
{: #vcsicp-detail-design-network-ingress-iks}

Un Ingress è una raccolta di regole che consentono alle connessioni in entrata di raggiungere i servizi cluster. Può essere configurato per fornire URL raggiungibili esternamente dai servizi, il traffico di bilanciamento del carico, terminare l'SSL, offrire un host virtuale basato sul nome e altro ancora.

## Flussi del traffico
{: #vcsicp-detail-design-network-traffic-flows}

Sono descritti i seguenti flussi di traffico:

- Utente esterno su internet a un livello web ospitato in un contenitore in {{site.data.keyword.icpfull_notm}}.
- Livello web ospitato in un contenitore in {{site.data.keyword.icpfull_notm}} al livello del database ospitato in una VM (Virtual Machine) in VMware vCenter Server on {{site.data.keyword.cloud_notm}}.
- Utente aziendale sull'accesso di rete aziendale a una VM in vCenter Server.

### Utente esterno su internet a un livello web ospitato in un contenitore in IBM Cloud Private
{: #vcsicp-detail-design-network-external-user}

1. L'utente esterno effettua una richiesta al livello web utilizzando l'URL.
2.	Viene utilizzato DNS per determinare l'indirizzo IP. Questo indirizzo IP è un indirizzo pubblico di {{site.data.keyword.cloud_notm}} su una sottorete portatile che è assegnata all'istanza vCenter Server.
3.	La rete pubblica inoltra automaticamente la richiesta all'host vSphere ESXi che ospita l'ESG.
4.	L'ESG inoltra la richiesta all'indirizzo IP del cluster interno e al numero di porta del servizio ALB o Ingress. Il pacchetto IP viene incapsulato in un frame VXLAN se ESG e il servizio ALB o quello Ingress si trovano su diversi host vSphere ESXi. Questo indirizzo IP del cluster interno è accessibile solo all'interno del cluster.
5.	All'interno del nodo di lavoro, kube-proxy instrada la richiesta al servizio ALB o Ingress.
6.	Se l'applicazione si trova sullo stesso nodo di lavoro, vengono utilizzate le iptable per determinare quale interfaccia interna viene utilizzata per inoltrare la richiesta. Se l'applicazione si trova su un nodo di lavoro differente, allora il Calico vRouter esegue l'instradamento verso il nodo di lavoro applicabile, utilizzando l'incapsulamento IP-in-IP. Il pacchetto IP-in-IP viene incapsulato in un frame VXLAN per il trasporto verso l'host vSphere ESXi in cui si trova il nodo di lavoro.

### Livello web ospitato in un contenitore in IBM Cloud Private al livello del database ospitato in una VM in vCenter Server
{: #vcsicp-detail-design-network-web-tier}

Il modo in cui le tabelle di instradamento nell'ESG e i vRouter vengono popolate dipende dal metodo di integrazione. Vedi l'integrazione di {{site.data.keyword.icpfull_notm}} e vCenter Server.

1.	Il livello web che viene eseguito in un contenitore in {{site.data.keyword.icpfull_notm}} effettua una richiesta a un database che viene eseguito su una VM nella stessa istanza vCenter Server.
2.	Viene utilizzato DNS per risolvere la richiesta all'indirizzo IP del database.
3.	Il contenitore invia la richiesta al Calico vRouter.
4.	Il vRouter ha una sua tabella di instradamento che viene popolata con gli intervalli di indirizzi IP ospitati nell'istanza vCenter Server.
5.	Il vRouter inoltra la richiesta ma utilizza SNAT per modificare l'indirizzo IP di origine dall'indirizzo IP del pod con l'indirizzo IP del nodo di lavoro.
6.	Il nodo di lavoro che ospita il vRouter invia la richiesta all'ESG.
7.	L'ESG la inoltra al DLR.
8.	Il DLR inserisce la richiesta nella VXLAN richiesta.
9.	La VM del database riceve la richiesta.

### Utente aziendale sull'accesso di rete aziendale a una VM in vCenter Server
{: #vcsicp-detail-design-network-enterprise-user}

1.	Un utente aziendale collegato alla rete interna aziendale effettua una richiesta di una risorsa su una VM ospitata in vCenter Server.
2.	Viene utilizzato DNS per determinare l'indirizzo IP della VM. Questo indirizzo IP si trova su una rete che è estesa a {{site.data.keyword.cloud_notm}}.
3.	Il router in loco indirizza il traffico verso l'host vSphere che ospita il concentratore L2.
4.	Il concentratore L2 incapsula la richiesta in un tunnel sicuro e la inoltra al concentratore L2 remoto ospitato in {{site.data.keyword.cloud_notm}} utilizzando l'indirizzo IP della sottorete portatile privata assegnato al dispositivo, mediante il router in loco.
5.	La rotta in loco ricerca nella sua tabella di instradamento e distingue che l'indirizzo IP del concentratore L2 remoto deve essere inviato all'interfaccia WAN, Esegue l'inoltro attraverso il WAN, tramite il router {{site.data.keyword.cloud_notm}} XCR, mediante il BCR.
6.	Il concentratore L2 riceve la richiesta e la colloca sulla VXLAN che ospita la rete estesa.
7.	La VM riceve la richiesta.

## Rete di accesso pubblica
{: #vcsicp-detail-design-network-public-access-net}

{{site.data.keyword.icpfull_notm}} e CAM, per impostazione predefinita, richiedono la connettività internet per richiamare le immagini Docker, i grafici Helm, i modelli Terraform e i gestori del pacchetto del sistema operativo.
Nelle ultime release, è ora presente il supporto per le installazioni basate sul proxy non direttamente collegate a internet e che dispongono di opzioni per l'installazione in una modalità offline.

###	Firewall NSX
{: #vcsicp-detail-design-network-nsx-firewall}

Il firewall Edge NSX {{site.data.keyword.icpfull_notm}} è configurato con le regole per poter:
*	Abilitare l'accesso alle reti VXLAN all'accesso pubblico.
*	Abilitare l'accesso alle reti VXLAN all'accesso di rete {{site.data.keyword.cloud_notm}} privata.
*	Abilitare l'accesso alla rete {{site.data.keyword.cloud_notm}} privata alle reti VXLAN.

### NAT NSX
{: #vcsicp-detail-design-network-nsx-nat}

NAT NSX {{site.data.keyword.icpfull_notm}} è configurato con i seguenti NAT:
*	SNAT per l'accesso alle reti VXLAN per l'accesso pubblico.
*	SNAT per l'accesso alle reti VXLAN per l'accesso di rete {{site.data.keyword.cloud_notm}} privata.
*	DNAT per i vIP del cluster {{site.data.keyword.icpfull_notm}}.

## Link correlati
{: #vcsicp-detail-design-network-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

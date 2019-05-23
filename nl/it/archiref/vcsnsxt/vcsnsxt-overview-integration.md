---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

# Integrazione, indirizzamento IP e flussi di rete
{: #vcsnsxt-overview-integration}

## Integrazione di IBM Cloud Private e VMware vCenter Server on IBM Cloud
{: #vcsnsxt-overview-integration-icp-vcs-integration}

{{site.data.keyword.cloud}} Private viene installato su diverse VM (Virtual Machine) su un'istanza vCenter Server. All'interno dell'istanza vCenter Server, l'istanza {{site.data.keyword.icpfull_notm}} viene distribuita con un DLR (Distributed Logical Router) ed ESG (Edge Services Gateway) NSX dedicato e utilizza una VXLAN.

L'ESG è configurato con una regola NAT di origine (SNAT) per consentire il traffico in uscita, che abilita la connettività per scaricare i prerequisiti {{site.data.keyword.icpfull_notm}} e la connessione a GitHub e Docker. In alternativa, puoi utilizzare un proxy web per la connettività internet. L'ESG è configurato con la connettività privata per accedere ai servizi DNS e NTP. L'ESG è anche configurato con una regola DNAT per abilitare l'accesso ai vIP Proxy e Master {{site.data.keyword.icpfull_notm}} dalla rete {{site.data.keyword.cloud_notm}} 10.x.

## Integrazione di IBM Cloud Kubernetes Service e vCenter Server
{: #vcsnsxt-overview-integration-iks-vcs-integration}

Attualmente, i seguenti scenari consentono di integrare la rete di {{site.data.keyword.containerlong_notm}} e vCenter Server:
- **VLAN comune** - Richiede che i nodi di lavoro {{site.data.keyword.containerlong_notm}} siano distribuiti sulla stessa VLAN dell'istanza vCenter Server. La VLAN comune consente a un ESG di essere un peer BGP per i nodi di lavoro.
- **VPN strongSwan** – Questo scenario utilizza la soluzione di connettività standard tra {{site.data.keyword.containerlong_notm}} e l'azienda. Un contenitore strongSwan fornisce un gateway VPN per il cluster che inoltra i pacchetti alle reti remote attraverso un tunnel IPSec al gateway remoto. Questo gateway remoto è un ESG sull'istanza vCenter Server. Sui gateway, le rotte sono configurate inviando tutti gli intervalli IP del cluster e del servizio al contenitore strongSwan e tutti gli indirizzi BYOIP di vCenter Server all'ESG. Gli indirizzi IP di destinazione per i gateway sono l'indirizzo IP portatile privato del servizio del programma di bilanciamento del carico assegnato al contenitore strongSwan e l'indirizzo IP portatile privato dell'ESG.
- **Rotte statiche e NAT**.
- **Peering BGP** – Il peering BGP non è un'offerta predefinita in {{site.data.keyword.cloud_notm}} e deve essere richiesta e approvata. Una volta abilitato, il peering BGP consente ai vRouter Calico e all'ESG di annunciare le rotte al BCR.

## Integrazione di IBM Cloud Kubernetes Service e IBM Cloud Private
{: #vcsnsxt-overview-integration-iks-icp-integration}

L'integrazione di {{site.data.keyword.containerlong_notm}} e {{site.data.keyword.icpfull_notm}} utilizza la connettività VPN strongSwan con un contenitore strongSwan in {{site.data.keyword.icpfull_notm}} e {{site.data.keyword.containerlong_notm}}.

## Assegnazione di indirizzi IP
{: #vcsnsxt-overview-integration-ip-address-allocation}

Da una prospettiva amministrativa, l'architettura di riferimento ha i seguenti intervalli di rete concettuali:
-	**Rete di pod {{site.data.keyword.containerlong_notm}}** - a tutti i pod distribuiti a un nodo di lavoro viene assegnato un indirizzo IP privato nell'intervallo 172.30.0.0/16 e sono instradati solo tra i nodi di lavoro. Per evitare conflitti, non utilizzare questo intervallo IP su qualsiasi nodo che comunica con i tuoi nodi di lavoro. I nodi di lavoro e i pod possono comunicare in modo protetto sulla rete privata utilizzando indirizzi IP privati. Tuttavia, quando si verifica un arresto anomalo di un pod o quando occorre creare nuovamente un nodo di lavoro, viene assegnato un nuovo indirizzo IP privato.
-	**Rete del servizio {{site.data.keyword.containerlong_notm}}** – {{site.data.keyword.containerlong_notm}} utilizza 172.21.0.0/16 per gli indirizzi del servizio all'interno del cluster. Di seguito sono riportati altri due intervalli di indirizzi IP:
    - Pubblica – una sottorete portatile pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. Questo intervallo di indirizzi IP viene utilizzato per esporre le applicazioni a Internet tramite i servizi Ingress o ALB.
    - Privata – una sottorete portatile privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. L'intervallo di indirizzi IP viene utilizzato per esporre le applicazioni alla rete privata tramite i servizi Ingress o ALB.
- **Rete di nodi di lavoro {{site.data.keyword.containerlong_notm}}** - ci sono due intervalli di indirizzi IP di rete dei nodi di lavoro:
    - Pubblica – una sottorete primaria pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}.
    - Privata – una sottorete primaria privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}.
-	**Rete host vCenter Server** - ci sono due intervalli di indirizzi IP di rete host vCenter Server:
    - Pubblica – una sottorete primaria pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}.
    - Privata – una sottorete primaria privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}.
-	**Rete ESG vCenter Server** - ci sono due intervalli di indirizzi IP di rete ESG vCenter Server:
    - Pubblica – una sottorete portatile pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}.
    - Privata – una sottorete portatile privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}.
-	**Rete VM vCenter Server** – un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}.
-	**Rete di pod {{site.data.keyword.icpfull_notm}}** – un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}. Gli intervalli di indirizzi IP di servizio e pod possono essere configurati in cluster/config.yaml.
-	**Rete del servizio {{site.data.keyword.icpfull_notm}}** – un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}. Gli intervalli di indirizzi IP di servizio e pod possono essere configurati in cluster/config.yaml.
-	**Rete di nodi di lavoro {{site.data.keyword.icpfull_notm}}** – un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}.

## Flussi di traffico di rete
{: #vcsnsxt-overview-integration-net-traffic-flows}

Sono descritti i seguenti flussi di traffico:
-	Utente esterno su internet a un livello web ospitato in un contenitore in {{site.data.keyword.containerlong_notm}}.
-	Utente esterno su internet a un livello web ospitato in un contenitore in {{site.data.keyword.icpfull_notm}}.
-	Livello web ospitato in un contenitore in {{site.data.keyword.containerlong_notm}} al livello del database ospitato in una VM in vCenter Server.
-	Livello web ospitato in un contenitore in {{site.data.keyword.icpfull_notm}} al livello del database ospitato in una VM in vCenter Server.
-	Utente aziendale sull'accesso di rete aziendale a una VM in vCenter Server.

### Utente esterno su internet a un livello web ospitato in un contenitore in IBM Cloud Kubernetes Service
{: #vcsnsxt-overview-integration-web-tier-iks}

1.	L'utente esterno effettua una richiesta al livello web utilizzando l'URL.
2.	Viene utilizzato DNS per determinare l'indirizzo IP. Questo indirizzo IP è un indirizzo pubblico di {{site.data.keyword.cloud_notm}} su una sottorete portatile assegnata al servizio ALB o Ingress.
3.	La rete pubblica inoltra automaticamente la richiesta al nodo di lavoro che ospita il servizio ALB o Ingress.
4.	Il nodo di lavoro inoltra la richiesta all'indirizzo IP del cluster interno e al numero di porta del servizio ALB o Ingress. Questo indirizzo IP del cluster interno è accessibile solo all'interno del cluster.
5.	All'interno del nodo di lavoro, kube-proxy instrada la richiesta al servizio ALB o Ingress.
6.	Se l'applicazione si trova sullo stesso nodo di lavoro, vengono utilizzate le iptable per determinare quale interfaccia interna viene utilizzata per inoltrare la richiesta. Se l'applicazione si trova su un nodo di lavoro differente, il vRouter Calico esegue l'instradamento al nodo di lavoro applicabile, utilizzando l'incapsulamento IP-in-IP solo se il nodo di lavoro si trova su una sottorete diversa.

### Utente esterno su internet a un livello web ospitato in un contenitore in IBM Cloud Private
{: #vcsnsxt-overview-integration-web-tier-icp}

1.	L'utente esterno effettua una richiesta al livello web utilizzando l'URL.
2.	Viene utilizzato DNS per determinare l'indirizzo IP. Questo indirizzo IP è un indirizzo pubblico di {{site.data.keyword.cloud_notm}} su una sottorete portatile che è assegnata all'istanza vCenter Server.
3.	La rete pubblica inoltra automaticamente la richiesta all'host vSphere ESXi che ospita l'ESG.
4.	L'ESG inoltra la richiesta all'indirizzo IP del cluster interno e al numero di porta del servizio ALB o Ingress. Il pacchetto IP viene incapsulato in un frame VXLAN se ESG e il servizio ALB o quello Ingress si trovano su diversi host vSphere ESXi. Questo indirizzo IP del cluster interno è accessibile solo all'interno del cluster.
5.	All'interno del nodo di lavoro, kube-proxy instrada la richiesta al servizio ALB o Ingress.
6.	Se l'applicazione si trova sullo stesso nodo di lavoro, vengono utilizzate le iptable per determinare quale interfaccia interna viene utilizzata per inoltrare la richiesta. Se l'applicazione si trova su un nodo di lavoro differente, allora il Calico vRouter esegue l'instradamento verso il nodo di lavoro applicabile, utilizzando l'incapsulamento IP-in-IP. Il pacchetto IP-in-IP viene incapsulato in un frame VXLAN per il trasporto verso l'host vSphere ESXi in cui si trova il nodo di lavoro.

### Livello web ospitato in un contenitore in IBM Cloud Kubernetes Service al livello del database ospitato in una VM in vCenter Server
{: #vcsnsxt-overview-integration-iks-db-tier-vcs}

Il modo in cui le tabelle di instradamento nell'ESG e i vRouter vengono popolate dipende dal metodo di integrazione. Vedi Integrazione di {{site.data.keyword.containerlong_notm}} e vCenter Server.
1.	Il livello web che è in esecuzione in un contenitore in {{site.data.keyword.containerlong_notm}} effettua una richiesta a un database in esecuzione su una VM nell'istanza vCenter Server.
2.	Viene utilizzato DNS per risolvere la richiesta all'indirizzo IP del database.
3.	Il contenitore invia la richiesta al Calico vRouter.
4.	Il vRouter ha una sua tabella di instradamento che viene popolata con gli intervalli di indirizzi IP ospitati nell'istanza vCenter Server.
5.	Il vRouter inoltra la richiesta ma utilizza SNAT per modificare l'indirizzo IP di origine dall'indirizzo IP del pod con l'indirizzo IP del nodo di lavoro.
6.	Il nodo di lavoro che ospita il vRouter invia la richiesta al BCR.
7.	Il BCR inoltra la richiesta all'ESG.
8.	L'ESG la inoltra al DLR.
9.	Il DLR inserisce la richiesta nella VXLAN richiesta.
10.	La VM del database riceve la richiesta.

### Livello web ospitato in un contenitore in IBM Cloud Private al livello del database ospitato in una VM in vCenter Server
{: #vcsnsxt-overview-integration-icp-db-tier-vcs}

Il modo in cui le tabelle di instradamento nell'ESG e i vRouter vengono popolate dipende dal metodo di integrazione. Vedi Integrazione di {{site.data.keyword.icpfull_notm}} e vCenter Server.
1.	Il livello web in esecuzione in un contenitore in {{site.data.keyword.icpfull_notm}} effettua una richiesta a un database in esecuzione su una VM nella stessa istanza vCenter Server.
2.	Viene utilizzato DNS per risolvere la richiesta all'indirizzo IP del database.
3.	Il contenitore invia la richiesta al Calico vRouter.
4.	Il vRouter ha una sua tabella di instradamento che viene popolata con gli intervalli di indirizzi IP ospitati nell'istanza vCenter Server.
5.	Il vRouter inoltra la richiesta ma utilizza SNAT per modificare l'indirizzo IP di origine dall'indirizzo IP del pod con l'indirizzo IP del nodo di lavoro.
6.	Il nodo di lavoro che ospita il vRouter invia la richiesta all'ESG.
7.	L'ESG la inoltra al DLR.
8.	Il DLR inserisce la richiesta nella VXLAN richiesta.
9.	La VM del database riceve la richiesta.

### Utente aziendale sull'accesso di rete aziendale a una VM in vCenter Server
{: #vcsnsxt-overview-integration-corporate-network-vcs}

1.	Un utente aziendale collegato alla rete interna aziendale effettua una richiesta di una risorsa che si trova su una VM ospitata in vCenter Server.
2.	Viene utilizzato DNS per determinare l'indirizzo IP della VM. Questo indirizzo IP si trova su una rete che è stata estesa a {{site.data.keyword.cloud_notm}}.
3.	Il router in loco indirizza il traffico verso l'host vSphere che ospita il concentratore L2.
4.	Il concentratore L2 incapsula la richiesta in un tunnel sicuro e la inoltra al concentratore L2 remoto ospitato in {{site.data.keyword.cloud_notm}} utilizzando l'indirizzo IP della sottorete portatile privata assegnato al dispositivo, mediante il router in loco.
5.	La rotta in loco ricerca nella sua tabella di instradamento e distingue che l'indirizzo IP del concentratore L2 remoto deve essere inviato all'interfaccia WAN e lo inoltra attraverso il WAN, tramite il router {{site.data.keyword.cloud_notm}} XCR, mediante il BCR.
6.	Il concentratore L2 riceve la richiesta e la colloca sulla VXLAN che ospita la rete estesa.
7.	La VM riceve la richiesta.

## Link correlati
{: #vcsnsxt-overview-integration-related}

* [{{site.data.keyword.cloud_notm}} global data centers](https://www.ibm.com/cloud/data-centers/){:new_window}
* [White paper dei contenitori](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf){:new_window} (Download del PDF)
* [Blog di VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/blog/announcements/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available){:new_window}
* [Scheda tecnica di VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/downloads/cas/MPVXKWNM){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Valori massimi di configurazione di NSX for vSphere 6.4.3](https://configmax.vmware.com/guest){:new_window}
* [Documentazione della piattaforma {{site.data.keyword.cloud_notm}}](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html){:new_window}
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started#getting-started)
* [Project Calico](https://www.projectcalico.org/){:new_window}
* [GitHub-Calico](https://github.com/projectcalico/calico){:new_window}
* [Kubernetes](https://kubernetes.io/){:new_window}
* [GitHub-Flannel](https://github.com/coreos/flannel/){:new_window}
* [GitHub-Canal](https://github.com/projectcalico/canal){:new_window}

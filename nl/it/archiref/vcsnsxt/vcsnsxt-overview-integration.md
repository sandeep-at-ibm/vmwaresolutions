---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# Integrazione, indirizzamento IP e flussi di rete

## Integrazione di ICP e VCS

{{site.data.keyword.cloud}} Private è installato su diverse macchine virtuali su un'istanza VCS. All'interno dell'istanza VCS, l'istanza ICP viene distribuita con un DLR (Distributed Logical Router) e ESG (Edge Services Gateway) NSX dedicato e utilizza una VXLAN.

L'ESG è configurato con una regola NAT per consentire il traffico in uscita, abilitando la connettività Internet per scaricare i prerequisiti ICP e la connettività a GitHub e Docker. Volendo, è possibile utilizzare un server proxy web per fornire la connettività Internet. L'ESG è configurato con la connettività privata per accedere ai servizi DNS e NTP. L'ESG è anche configurato con una regola DNAT per abilitare l'accesso a vIP Proxy e Master ICP dalla rete {{site.data.keyword.cloud_notm}} 10.x.

## Integrazione di IKS e VCS

Al momento, ci sono i seguenti scenari per integrare le reti IKS e VCS:
- **VLAN comune** - Questo scenario richiede che i nodi di lavoro IKS siano distribuiti sulla stessa VLAN dell'istanza VCS. Ciò consente a un ESG di essere un peer BGP per i nodi di lavoro.
- **strongSwan VPN** – Questo scenario utilizza la soluzione di connettività IKS-azienda standard. Un contenitore strongSwan fornisce un gateway VPN per il cluster che inoltra i pacchetti alle reti remote attraverso un tunnel IPSec al gateway remoto. Questo gateway remoto è un ESG sull'istanza VCS. Sui gateway, le rotte sono configurate inviando tutti gli intervalli IP di servizi e cluster al contenitore strongSwan e tutti gli indirizzi VCS BYOIP all'ESG. Gli indirizzi IP di destinazione per i gateway sono l'indirizzo IP portatile privato del servizio del programma di bilanciamento del carico assegnato al contenitore strongSwan e l'indirizzo IP portatile privato dell'ESG.
- **Rotte statiche e NAT**.
- **Peering BGP** – Il peering BGP non è un'offerta predefinita in {{site.data.keyword.cloud_notm}} e deve essere richiesta e approvata. Dopo essere stato abilitato, il peering BGP consente ai vRouter Calico e all'ESG di annunciare le rotte al BCR.

## Integrazione di IKS e ICP

L'integrazione di ICP e IKS utilizza la connettività VPN strongSwan con un contenitore strongSwan in ICP e IKS.

## Assegnazione di indirizzi IP

Da una prospettiva amministrativa, l'architettura di riferimento ha i seguenti intervalli di rete concettuali:
-	**Rete di pod IKS** - a tutti i pod distribuiti a un nodo di lavoro viene assegnato un indirizzo IP privato nell'intervallo 172.30.0.0/16 e sono instradati solo tra i nodi di lavoro. Per evitare conflitti, non utilizzare questo intervallo IP su qualsiasi nodo che comunica con i tuoi nodi di lavoro. I nodi di lavoro e i pod possono comunicare in modo protetto sulla rete privata utilizzando indirizzi IP privati. Tuttavia, quando si verifica un arresto anomalo di un pod o quando occorre creare nuovamente un nodo di lavoro, viene assegnato un nuovo indirizzo IP privato.
-	**Rete del servizio IKS** – IKS utilizza 172.21.0.0/16 per gli indirizzi di servizio all'interno del cluster. Ci sono altri due intervalli di indirizzi IP:
    - Pubblica – una sottorete portatile pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. L'intervallo di indirizzi IP viene utilizzato per esporre le applicazioni a Internet tramite i servizi Ingress o ALB.
    - Privata – una sottorete portatile privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. L'intervallo di indirizzi IP viene utilizzato per esporre le applicazioni alla rete privata tramite i servizi Ingress o ALB.
- **Rete di nodi di lavoro IKS** - ci sono due intervalli di indirizzi IP di rete di nodi di lavoro:
    - Pubblica – una sottorete primaria pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. 
    - Privata – una sottorete primaria privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. 
-	**Rete host VCS** - ci sono due intervalli di indirizzi IP di rete host VCS:
    - Pubblica – una sottorete primaria pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. 
    - Privata – una sottorete primaria privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. 
-	**Rete ESG VCS** - ci sono due intervalli di indirizzi IP di rete ESG VCS:
    - Pubblica – una sottorete portatile pubblica con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. 
    - Privata – una sottorete portatile privata con un intervallo di indirizzi IP fornito da {{site.data.keyword.cloud_notm}}. 
-	**Rete VM VCS** - un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}.
-	**Rete pod ICP** – un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}. Gli intervalli di indirizzi IP di servizio e pod possono essere configurati in cluster/config.yaml.
-	**Rete del servizio ICP** - un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}.Gli intervalli di indirizzi IP di servizio e pod possono essere configurati in cluster/config.yaml.
-	**Rete di nodi di lavoro ICP** - un intervallo di indirizzi IP aziendali che utilizza un intervallo BYOIP che non va in conflitto con alcuna sottorete fornita da {{site.data.keyword.cloud_notm}}.

## Flussi di traffico di rete

Sono descritti i seguenti flussi di traffico:
-	Utente esterno su Internet a un livello web ospitato in un contenitore in IKS.
-	Utente esterno su Internet a un livello web ospitato in un contenitore in ICP.
-	Livello web ospitato in un contenitore in IKS al livello del database ospitato in una VM in VCS.
-	Livello web ospitato in un contenitore in ICP al livello del database ospitato in una VM in VCS.
-	Utente aziendale sull'accesso di rete aziendale a una VM in VCS.

### Utente esterno su internet a un livello web ospitato in un contenitore in IKS

1.	L'utente esterno effettua una richiesta al livello web utilizzando l'URL.
2.	Viene utilizzato DNS per determinare l'indirizzo IP. Questo indirizzo IP è un indirizzo pubblico di {{site.data.keyword.cloud_notm}} su una sottorete portatile che è stata assegnata al servizio Ingress o ALB.
3.	La rete pubblica inoltrerà automaticamente la richiesta al nodo di lavoro che ospita il servizio Ingress o ALB.
4.	Il nodo di lavoro inoltrerà la richiesta all'indirizzo IP del cluster interno e al numero di porta del servizio Ingress o ALB. Questo indirizzo IP del cluster interno è accessibile solo all'interno del cluster.
5.	All'interno del nodo di lavoro, kube-proxy instrada la richiesta al servizio ALB o Ingress.
6.	Se l'applicazione si trova sullo stesso nodo di lavoro, vengono utilizzate le iptable per determinare quale interfaccia interna viene utilizzata per inoltrare la richiesta. Se l'applicazione si trova su un nodo di lavoro differente, Calico vRouter esegue l'instradamento al nodo di lavoro applicabile, utilizzando l'incapsulamento IP-in-IP solo se il nodo di lavoro si trova su una sottorete differente.

### Utente esterno su internet a un livello web ospitato in un contenitore in ICP

1.	L'utente esterno effettua una richiesta al livello web utilizzando l'URL.
2.	Viene utilizzato DNS per determinare l'indirizzo IP. Questo indirizzo IP sarà un indirizzo pubblico di {{site.data.keyword.cloud_notm}} su una sottorete portatile che è stata assegnata all'istanza VCS.
3.	La rete pubblica inoltrerà automaticamente la richiesta all'host vSphere ESXi che ospita l'ESG.
4.	L'ESG inoltrerà la richiesta all'indirizzo IP del cluster interno e al numero di porta del servizio ALB o Ingress. Il pacchetto IP verrà incapsulato in un frame VXLAN se ESG e il servizio ALB o Ingress si trovano su diversi host vSphere ESXi. Questo indirizzo IP del cluster interno è accessibile solo all'interno del cluster.
5.	All'interno del nodo di lavoro, kube-proxy instrada la richiesta al servizio ALB o Ingress.
6.	Se l'applicazione si trova sullo stesso nodo di lavoro, vengono utilizzate le iptable per determinare quale interfaccia interna viene utilizzata per inoltrare la richiesta. Se l'applicazione si trova su un nodo di lavoro differente, allora il Calico vRouter esegue l'instradamento verso il nodo di lavoro applicabile, utilizzando l'incapsulamento IP-in-IP. Il pacchetto IP-in-IP verrà incapsulato in un frame VXLAN per il trasporto verso l'host vSphere ESXi in cui si trova il nodo di lavoro.

### Livello web ospitato in un contenitore in IKS al livello del database ospitato in una VM in VCS

Il modo in cui le tabelle di instradamento nell'ESG e i vRouter vengono popolate dipende dal metodo di integrazione. Consulta l'integrazione IKS e VCS.
1.	Il livello web in esecuzione in un contenitore in IKS effettua una richiesta a un database in esecuzione su una VM nell'istanza di VCS.
2.	Viene utilizzato DNS per risolvere la richiesta all'indirizzo IP del database.
3.	Il contenitore invia la richiesta al Calico vRouter.
4.	Il vRouter ha una sua tabella di instradamento che viene popolata con gli intervalli di indirizzi IP ospitati nell'istanza VCS.
5.	Il vRouter inoltra la richiesta ma utilizza SNAT per modificare l'indirizzo IP di origine dall'indirizzo IP del pod con l'indirizzo IP del nodo di lavoro.
6.	Il nodo di lavoro che ospita il vRouter invia la richiesta al BCR.
7.	Il BCR inoltra la richiesta all'ESG.
8.	L'ESG la inoltra al DLR.
9.	Il DLR inserisce la richiesta nella VXLAN richiesta.
10.	La VM del database riceve la richiesta.

### Livello web ospitato in un contenitore in ICP al livello del database ospitato in una VM in VCS

Il modo in cui le tabelle di instradamento nell'ESG e i vRouter vengono popolate dipende dal metodo di integrazione. Consulta l'integrazione ICP e VCS.
1.	Il livello web in esecuzione in un contenitore in ICP effettua una richiesta a un database in esecuzione su una VM nella stessa istanza di VCS.
2.	Viene utilizzato DNS per risolvere la richiesta all'indirizzo IP del database.
3.	Il contenitore invia la richiesta al Calico vRouter.
4.	Il vRouter ha una sua tabella di instradamento che viene popolata con gli intervalli di indirizzi IP ospitati nell'istanza VCS.
5.	Il vRouter inoltra la richiesta ma utilizza SNAT per modificare l'indirizzo IP di origine dall'indirizzo IP del pod con l'indirizzo IP del nodo di lavoro.
6.	Il nodo di lavoro che ospita il vRouter invia la richiesta all'ESG.
7.	L'ESG la inoltra al DLR.
8.	Il DLR inserisce la richiesta nella VXLAN richiesta.
9.	La VM del database riceve la richiesta.

### Utente aziendale sull'accesso di rete aziendale a una VM in VCS

1.	Un utente aziendale collegato alla rete interna aziendale effettua una richiesta di una risorsa che si trova su una VM ospitata in VCS.
2.	Viene utilizzato DNS per determinare l'indirizzo IP della VM. Questo indirizzo IP si trova su una rete che è stata estesa a {{site.data.keyword.cloud_notm}}.
3.	Il router in loco indirizza il traffico verso l'host vSphere che ospita il concentratore L2.
4.	Il concentratore L2 incapsula la richiesta in un tunnel sicuro e la inoltra al concentratore L2 remoto ospitato in {{site.data.keyword.cloud_notm}} utilizzando l'indirizzo IP della sottorete portatile privata assegnato al dispositivo, mediante il router in loco.
5.	La rotta in loco ricerca nella sua tabella di instradamento e distingue che l'indirizzo IP del concentratore L2 remoto deve essere inviato all'interfaccia WAN e lo inoltra attraverso il WAN, tramite il router {{site.data.keyword.cloud_notm}} XCR, mediante il BCR.
6.	Il concentratore L2 riceve la richiesta e la colloca sulla VXLAN che ospita la rete estesa.
7.	La VM riceve la richiesta.

### Ulteriori risorse

* [Rete {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [White paper dei contenitori](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (Download del PDF)
* [Blog di VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Scheda tecnica di VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Valori massimi di configurazione di NSX for vSphere 6.4.3](https://configmax.vmware.com/guest)
* [Documentazione della piattaforma {{site.data.keyword.cloud_notm}}](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.cloud_notm}} Kubernetes Service](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Project Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)

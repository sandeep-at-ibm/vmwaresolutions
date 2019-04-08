---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

# Integration, IP-Adressierung und Netzflüsse
{: #vcsnsxt-overview-integration}

## Integration von IBM Cloud Private und VMware vCenter Server on IBM Cloud
{: #vcsnsxt-overview-integration-icp-vcs-integration}

{{site.data.keyword.cloud}} Private wird auf mehreren virtuellen Maschinen (VMs) in einer vCenter Server-Instanz installiert. In der vCener Server-Instanz wird die {{site.data.keyword.icpfull_notm}}-Instanz mit einem dedizierten NSX Edge Services Gateway (ESG) und dem Distributed Logical Router (DLR) bereitgestellt und verwendet ein VXLAN.

Das ESG ist mit einer Quellen-NAT-Regel (SNAT) konfiguriert, um abgehenden Datenverkehr zu ermöglichen, wodurch die Internetverbindung zum Download der {{site.data.keyword.icpfull_notm}} -Voraussetzungen und zur Konnektivität mit GitHub und Docker befähigt wird. Alternativ können Sie einen Web-Proxy für die Internetkonnektivität verwenden. Das ESG ist für den Zugriff auf DNS- und NTP-Services konfiguriert. Das ESG ist zudem mit einer DNAT-Regel konfiguriert, damit der Zugriff auf dem {{site.data.keyword.icpfull_notm}}-Master und die virtuellen Proxy-IP-Adressen aus dem Netz von {{site.data.keyword.cloud_notm}} 10.x möglich ist.

## Integration des IBM Cloud Kubernetes-Service und von vCenter Server
{: #vcsnsxt-overview-integration-iks-vcs-integration}

Derzeit bestehe für die Integration des Netzbetriebs von {{site.data.keyword.containerlong_notm}} und vCenter Server folgende Szenarios:
- **Allgemeines VLAN** - Setzt voraus, dass die {{site.data.keyword.containerlong_notm}}-Workerknoten in demselben VLAN wie die vCenter Server-Instanz bereitgestellt werden. Durch das allgemeine VLAN kann ein ESG die Funktion eines BGP-Peers für die Workerknoten übernehmen.
- **strongSwan-VPN** – Dieses Szenario verwendet die Standardlösung für die Konnektivität von {{site.data.keyword.containerlong_notm}} zum Unternehmen. Ein strongSwan-Container stellt ein VPN-Gateway für den Cluster bereit, das Pakete über einen IPSec-Tunnel zum fernen Gateway an ferne Netze weiterleitet. Dieses ferne Gateway ist eine ESG-Instanz auf der vCenter Server-Instanz. Auf den Gateways sind Routen konfiguriert, die alle Cluster- und Service-IP-Bereiche an den strongSwan-Container und alle BYOIP-Adressen von vCenter Server an die ESG-Instanz senden. Die Ziel-IP-Adressen für die Gateways sind zum einen die private portierbare IP-Adresse der Lastausgleichsfunktion, die dem strongSwan-Container zugeordnet ist, und zum zweiten die private portierbare IP-Adresse der ESG-Instanz.
- **Statische Routen und NAT**.
- **BGP-Peering** - Das BGP-Peering ist kein Standardangebot in {{site.data.keyword.cloud_notm}}; es muss angefordert und genehmigt werden. Nach der Aktivierung ermöglicht es das BGP-Peering den virtuellen Calico-Routern und dem ESG, dem BCR Routen mitzuteilen.

## Integration des IBM Cloud Kubernetes-Service und von IBM Cloud Private
{: #vcsnsxt-overview-integration-iks-icp-integration}

Die {{site.data.keyword.containerlong_notm}}- und {{site.data.keyword.icpfull_notm}}-Integration verwendet die VPN-Konnektivität von strongSwan mit einem strongSwan-Container in {{site.data.keyword.containerlong_notm}} und {{site.data.keyword.icpfull_notm}}.

## IP-Adresszuordnung
{: #vcsnsxt-overview-integration-ip-address-allocation}

Unter Verwaltungsgesichtspunkten betrachtet verfügt die Referenzarchitektur über die folgenden konzeptionellen Netzbereiche:
-	**{{site.data.keyword.containerlong_notm}}-Podnetz** - Allen Pods, die auf einem Workerknoten bereitgestellt werden, wird eine private IP-Adresse im Bereich 172.30.0.0/16 zugeordnet und ihre Weiterleitung erfolgt ausschließlich zwischen Workerknoten. Verwenden Sie zur Vermeidung von Konflikten diesen IP-Bereich auf keinen Knoten, die mit Ihren Workerknoten kommunizieren. Workerknoten und Pods können bei Verwendung von privaten IP-Adressen sicher über das private Netz kommunizieren. Wenn jedoch ein Pod ausfällt oder ein Workerknoten erneut erstellt werden muss, wird eine neue private IP-Adresse zugeordnet.
-	**{{site.data.keyword.containerlong_notm}}-Servicenetz** – {{site.data.keyword.containerlong_notm}} verwendet den Bereich 172.21.0.0/16 für Serviceadressen innerhalb des Clusters. Es gibt die folgenden zwei weiteren IP-Adressbereiche:
    - Öffentlich - Ein öffentliches portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird. Mit diesem IP-Adressbereich werden Anwendungen über ALB- oder Ingress-Services aus dem Internet zugänglich gemacht.
    - Privat - Ein privates portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird. Mit diesem IP-Adressbereich werden Anwendungen über ALB- oder Ingress-Services für das private Netz zugänglich gemacht.
- **{{site.data.keyword.containerlong_notm}}-Workerknotennetz** - Für das Workerknotennetz gibt es zwei IP-Adressbereiche:
    - Öffentlich - Ein öffentliches primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
    - Privat - Ein privates primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
-	**vCenter Server-Hostnetz** - Für das vCenter Server-Hostnetz gibt es zwei IP-Adressbereiche:
    - Öffentlich - Ein öffentliches primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
    - Privat - Ein privates primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
-	**vCenter Server-ESG-Netz** - Für das vCenter Server-ESG-Netz gibt es zwei IP-Adressbereiche:
    - Öffentlich - Ein öffentliches portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
    - Privat - Ein privates portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
-	**vCenter Server-VM-Netz** – Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden.
-	**{{site.data.keyword.icpfull_notm}}-Podnetz** – Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden. IP-Adressbereiche für Pods und Services können in der Datei "cluster/config.yaml" konfiguriert werden.
-	**{{site.data.keyword.icpfull_notm}}-Servicenetz** – Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden. IP-Adressbereiche für Pods und Services können in der Datei "cluster/config.yaml" konfiguriert werden.
-	**{{site.data.keyword.icpfull_notm}}-Workerknoten-Netz** – Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden.

## Datenflüsse des Netzverkehrs
{: #vcsnsxt-overview-integration-net-traffic-flows}

Für den Datenfluss gibt es die folgenden Möglichkeiten:
-	Von externem Benutzer im Internet an eine Webschicht, die in einem Container in {{site.data.keyword.containerlong_notm}} gehostet wird.
-	Von externem Benutzer im Internet an eine Webschicht, die in einem Container in {{site.data.keyword.icpfull_notm}} gehostet wird.
-	Von einer Webschicht, die in einem Container in {{site.data.keyword.containerlong_notm}} gehostet wird, an eine Datenbankschicht, die in einer VM in vCenter Server gehostet wird.
-	Von einer Webschicht, die in einem Container in {{site.data.keyword.icpfull_notm}} gehostet wird, an eine Datenbankschicht, die in einer VM in vCenter Server gehostet wird.
-	Von einem Benutzer im unternehmensweiten Netz an eine VM in vCenter Server

### Von externem Benutzer im Internet an eine Webschicht, die in einem Container im IBM Cloud Kubernetes-Service gehostet wird.
{: #vcsnsxt-overview-integration-web-tier-iks}

1.	Der externe Benutzer stellt über die URL eine Anforderung an die Webschicht.
2.	DNS wird verwendet, um die IP-Adresse zu ermitteln. Bei dieser IP-Adresse handelt es sich um eine öffentliche {{site.data.keyword.cloud_notm}}-Adresse in einem portierbaren Teilnetz, das dem ALB oder Ingress-Service zugeordnet ist.
3.	Das öffentliche Netz leitet die Anforderung automatisch an den Workerknoten weiter, der den ALB oder Ingress-Service hostet.
4.	Der Workerknoten leitet die Anforderung an die interne Cluster-IP-Adresse und an die Portnummer des ALB oder des Ingress-Service weiter. Diese interne Cluster-IP-Adresse ist nur innerhalb des Clusters zugänglich.
5.	Innerhalb des Workerknotens leitet "kube-proxy" die Anforderung an den ALB oder Ingress-Service weiter.
6.	Wenn sich die Anwendung auf demselben Workerknoten befindet, wird "iptables" verwendet, um zu ermitteln, welche interne Schnittstelle zum Weiterleiten der Anforderung verwendet wird. Falls sich die Anwendung auf einem anderen Workerknoten befindet, nimmt der Calico vRouter-Knoten die Weiterleitung unter Verwendung der IP-in-IP-Kapselung nur dann an den entsprechenden Workerknoten weiter, wenn sich der Workerknoten in einem anderen Teilnetz befindet.

### on externem Benutzer im Internet an eine Webschicht, die in einem Container in IBM Cloud Private gehostet wird.
{: #vcsnsxt-overview-integration-web-tier-icp}

1.	Der externe Benutzer stellt über die URL eine Anforderung an die Webschicht.
2.	DNS wird verwendet, um die IP-Adresse zu ermitteln. Bei dieser IP-Adresse handelt es sich um eine öffentliche {{site.data.keyword.cloud_notm}}-Adresse in einem portierbaren Teilnetz, das der vCenter Server-Instanz zugeordnet ist.
3.	Das öffentliche Netz leitet die Anforderung automatisch an den vSphere ESXi-Host weiter, der das ESG hostet.
4.	Das ESG leitet die Anforderung an die interne Cluster-IP-Adresse und an die Portnummer des ALB oder des Ingress-Service weiter. Das IP-Paket wird in einem VXLAN-Rahmen gekapselt, wenn sich das ESG und der ALB oder der Ingress-Service auf unterschiedlichen vSphere ESXi-Hosts befinden. Diese interne Cluster-IP-Adresse ist nur innerhalb des Clusters zugänglich.
5.	Innerhalb des Workerknotens leitet "kube-proxy" die Anforderung an den ALB oder Ingress-Service weiter.
6.	Wenn sich die Anwendung auf demselben Workerknoten befindet, wird "iptables" verwendet, um zu ermitteln, welche interne Schnittstelle zum Weiterleiten der Anforderung verwendet wird. Wenn sich die Anwendung auf einem anderen Workerknoten befindet, nimmt der Calico vRouter-Knoten die Weiterleitung an den entsprechenden Workerknoten vor und verwendet dabei IP-in-IP-Kapselung. Das IP-in-IP-Paket wird für den Transport zum vSphere ESXi-Host in einem VXLAN-Rahmen gekapselt, auf dem sich der Workerknoten befindet.

### Von einer Webschicht, die in einem Container im IBM Cloud Kubernetes-Service gehostet wird, an eine Datenbankschicht, die in einer VM in vCenter Server gehostet wird.
{: #vcsnsxt-overview-integration-iks-db-tier-vcs}

Wie die Routentabellen in den ESGs und vRoutern mit Daten gefüllt werden, hängt von der Integrationsmethode ab. Siehe "Integration von {{site.data.keyword.containerlong_notm}} und vCenter Server".
1.	Die Webschicht, die in einem Container in {{site.data.keyword.containerlong_notm}} ausgeführt wird, stellt eine Anforderung an eine Datenbank, die auf einer VM in der vCenter Server-Instanz ausgeführt wird.
2.	DNS wird verwendet, um die Anforderung an die IP-Adresse der Datenbank aufzulösen.
3.	Der Container sendet die Anfrage an den Calico vRouter.
4.	Der vRouter verfügt über eine Routentabelle, die mit den IP-Adressbereichen gefüllt ist, die in der vCenter Server-Instanz gehostet werden.
5.	Der vRouter leitet die Anforderung weiter, verwendet jedoch SNAT, um die Quellen-IP-Adresse von der IP-Adresse des Pods in die IP-Adresse des Workerknotens zu ändern.
6.	Der Workerknoten, der als Host für den vRouter fungiert, sendet die Anforderung an den BCR.
7.	Der BCR sendet die Anforderung an das ESG.
8.	Das ESG nimmt die Weiterleitung dann an den DLR vor.
9.	Der DLR stellt die Anfrage an das erforderliche VXLAN.
10.	Die Datenbank-VM empfängt die Anforderung.

### Von einer Webschicht, die in einem Container in IBM Cloud Private gehostet wird, an eine Datenbankschicht, die in einer VM in vCenter Server gehostet wird.
{: #vcsnsxt-overview-integration-icp-db-tier-vcs}

Wie die Routentabellen in den ESGs und vRoutern mit Daten gefüllt werden, hängt von der Integrationsmethode ab. Siehe "Integration von {{site.data.keyword.icpfull_notm}} und vCenter Server".
1.	Die Webschicht, die in einem Container in {{site.data.keyword.icpfull_notm}} ausgeführt wird, stellt eine Anforderung an eine Datenbank, die auf einer VM in derselben vCenter Server-Instanz ausgeführt wird.
2.	DNS wird verwendet, um die Anforderung an die IP-Adresse der Datenbank aufzulösen.
3.	Der Container sendet die Anfrage an den Calico vRouter.
4.	Der vRouter verfügt über eine Routentabelle, die mit den IP-Adressbereichen gefüllt ist, die in der vCenter Server-Instanz gehostet werden.
5.	Der vRouter leitet die Anforderung weiter, verwendet jedoch SNAT, um die Quellen-IP-Adresse von der IP-Adresse des Pods in die IP-Adresse des Workerknotens zu ändern.
6.	Der Workerknoten, der als Host für den vRouter fungiert, sendet die Anforderung an das ESG.
7.	Das ESG nimmt die Weiterleitung dann an den DLR vor.
8.	Der DLR stellt die Anfrage an das erforderliche VXLAN.
9.	Die Datenbank-VM empfängt die Anforderung.

### Von einem Benutzer im unternehmensweiten Netz an eine VM in vCenter Server
{: #vcsnsxt-overview-integration-corporate-network-vcs}

1.	Ein Unternehmensbenutzer, der mit dem internen Unternehmensnetz verbunden ist, fordert eine Ressource auf einer VM an, die in vCenter Server gehostet wird.
2.	DNS wird verwendet, um die IP-Adresse der VM zu bestimmen. Diese IP-Adresse befindet sich in einem Netz, das auf {{site.data.keyword.cloud_notm}} erweitert wurde.
3.	Der lokale Router leitet den Datenverkehr an den vSphere-Host weiter, der den L2-Konzentrator hostet.
4.	Der L2-Konzentrator kapselt die Anforderung in einem sicheren Kanal und leitet sie an den fernen L2-Konzentrator weiter, der in {{site.data.keyword.cloud_notm}} gehostet wird. Dabei wird die private portierbare IP-Teilnetzadresse verwendet, die dem Gerät zugeordnet ist. Die Weiterleitung erfolgt über den lokalen Router.
5.	Die lokale Route sucht in der zugehörigen Routing-Tabelle, bemerkt, dass die IP-Adresse für den fernen L2-Konzentrator an die WAN-Schnittstelle gesendet werden muss, und nimmt die Weiterleitung durch das WAN über den {{site.data.keyword.cloud_notm}} XCR-Router via BCR vor.
6.	Der L2-Konzentrator empfängt die Anforderung und stellt sie in das VXLAN, in dem sich das erweiterte Netz befindet.
7.	Die VM empfängt die Anforderung.

## Zugehörige Links
{: #vcsnsxt-overview-integration-related}

* [{{site.data.keyword.cloud_notm}}-Netz](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [Whitepaper für Container](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (PDF-Download)
* [Blog zu VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Datenblatt für VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Maximale Werte der Konfiguration von NSX for vSphere 6.4.3](https://configmax.vmware.com/guest)
* [Dokumentation zur {{site.data.keyword.cloud_notm}}-Plattform](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-container_index)
* [Calico-Projekt](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-12"

---

# Integration, IP-Adressierung und Netzflüsse

## ICP- und VCS-Integration

{{site.data.keyword.cloud}} Private wird auf mehreren virtuellen Maschinen in einer VCS-Instanz installiert. In der VCS-Instanz wird die ICP-Instanz mit einem dedizierten NSX Edge Services Gateway (ESG) und dem Distributed Logical Router (DLR) bereitgestellt und verwendet ein VXLAN.

Das ESG ist mit einer SNAT-Regel konfiguriert, um abgehenden Datenverkehr zu ermöglichen, wodurch die Internetverbindung zum Download der ICP-Voraussetzungen sowie die Konnektivität zu GitHub und Docker ermöglicht wird. Bei Bedarf kann die Internetkonnektivität mit einem Web-Proxy-Server bereitgestellt werden. Das ESG ist für den Zugriff auf DNS- und NTP-Services konfiguriert. Das ESG ist zudem mit einer DNAT-Regel konfiguriert, damit der Zugriff auf dem ICP-Master und die virtuellen Proxy-IP-Adressen aus dem Netz von {{site.data.keyword.cloud_notm}} 10.x möglich ist.

## IKS- und VCS-Integration

Für die Integration des IKS- und VCS-Netzbetriebs gibt es gegenwärtig die folgenden Szenarios:
- **Allgemeines VLAN** - Dies setzt voraus, dass die IKS-Workerknoten in demselben VLAN wie die VCS-Instanz bereitgestellt werden. Hierdurch kann ein ESG die Funktion eines BGP-Peers für die Workerknoten übernehmen.
- **strongSwan-VPN** - Dieses Szenario verwendet die Standardlösung für die Konnektivität von IKS zum Unternehmen. Ein strongSwan-Container stellt ein VPN-Gateway für den Cluster bereit, das Pakete über einen IPSec-Tunnel zum fernen Gateway an ferne Netze weiterleitet. Dieses ferne Gateway ist eine ESG-Instanz auf der VCS-Instanz. Auf den Gateways sind Routen konfiguriert, die alle Cluster- und Service-IP-Bereiche an den strongSwan-Container und alle BYOIP-Adressen von VCS an die ESG-Instanz senden. Die Ziel-IP-Adressen für die Gateways sind zum einen die private portierbare IP-Adresse der Lastausgleichsfunktion, die dem strongSwan-Container zugeordnet ist, und zum zweiten die private portierbare IP-Adresse der ESG-Instanz.
- **Statische Routen und NAT**.
- **BGP-Peering** - Das BGP-Peering ist kein Standardangebot in {{site.data.keyword.cloud_notm}}; es muss angefordert und genehmigt werden. Nach der Aktivierung ermöglicht es das BGP-Peering den virtuellen Calico-Routern und dem ESG, dem BCR Routen mitzuteilen. 

## IKS- und ICP-Integration

Die IKS- und ICP-Integration verwendet die VPN-Konnektivität von strongSwan mit einem strongSwan-Container in ICP und IKS.

## IP-Adresszuordnung

Unter Verwaltungsgesichtspunkten betrachtet verfügt die Referenzarchitektur über die folgenden konzeptionellen Netzbereiche:
-	**IKS-Podnetz** - Allen Pods, die auf einem Workerknoten bereitgestellt werden, wird eine private IP-Adresse im Bereich 172.30.0.0/16 zugeordnet und ihre Weiterleitung erfolgt ausschließlich zwischen Workerknoten. Verwenden Sie zur Vermeidung von Konflikten diesen IP-Bereich auf keinen Knoten, die mit Ihren Workerknoten kommunizieren. Workerknoten und Pods können bei Verwendung von privaten IP-Adressen sicher über das private Netz kommunizieren. Wenn jedoch ein Pod ausfällt oder ein Workerknoten erneut erstellt werden muss, wird eine neue private IP-Adresse zugeordnet.
-	**IKS-Servicenetz** - IKS verwendet den Bereich 172.21.0.0/16 für Serviceadressen innerhalb des Clusters. Es gibt zwei weitere IP-Adressbereiche:
    - Öffentlich - Ein öffentliches portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird. Mit diesem IP-Adressbereich werden Anwendungen über ALB- oder Ingress-Services aus dem Internet zugänglich gemacht.
    - Privat - Ein privates portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird. Mit diesem IP-Adressbereich werden Anwendungen über ALB- oder Ingress-Services für das private Netz zugänglich gemacht.
- **IKS-Workerknotennetz** - Für das Workerknotennetz gibt es zwei IP-Adressbereiche:
    - Öffentlich - Ein öffentliches primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
    - Privat - Ein privates primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
-	**VCS-Hostnetz** - Für das VCS-Hostnetz gibt es zwei IP-Adressbereiche:
    - Öffentlich - Ein öffentliches primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
    - Privat - Ein privates primäres Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
-	**VCS-ESG-Netz** - Für das VCS-ESG-Netz gibt es zwei IP-Adressbereiche:
    - Öffentlich - Ein öffentliches portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
    - Privat - Ein privates portierbares Teilnetz mit einem IP-Adressbereich, der von {{site.data.keyword.cloud_notm}} zur Verfügung gestellt wird.
-	**VCS-VM-Netz** - Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden.
-	**ICP-Podnetz** - Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden. IP-Adressbereiche für Pods und Services können in der Datei "cluster/config.yaml" konfiguriert werden.
-	**ICP-Servicenetz** - Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden. IP-Adressbereiche für Pods und Services können in der Datei "cluster/config.yaml" konfiguriert werden.
-	**ICP-Workerknotennetz** - Ein IP-Adressbereich des Unternehmens, der einen BYOIP-Bereich verwendet, von dem keine Konflikte mit einem der von {{site.data.keyword.cloud_notm}} bereitgestellten Teilnetze verursacht werden.

## Datenflüsse des Netzverkehrs

Für den Datenfluss gibt es die folgenden Möglichkeiten:
-	Von externem Benutzer im Internet an eine Webschicht, die in einem Container in IKS gehostet wird
-	Von externem Benutzer im Internet an eine Webschicht, die in einem Container in ICP gehostet wird
-	Von einer Webschicht, die in einem Container in IKS gehostet wird, an eine Datenbankschicht, die in einer VM in VCS gehostet wird
-	Von einer Webschicht, die in einem Container in ICP gehostet wird, an eine Datenbankschicht, die in einer VM in VCS gehostet wird
-	Von einem Benutzer im unternehmensweiten Netz an eine VM in VCS

### Von externem Benutzer im Internet an eine Webschicht, die in einem Container in IKS gehostet wird

1.	Der externe Benutzer stellt über die URL eine Anforderung an die Webschicht.
2.	DNS wird verwendet, um die IP-Adresse zu ermitteln. Bei dieser IP-Adresse handelt es sich um eine öffentliche {{site.data.keyword.cloud_notm}}-Adresse in einem portierbaren Teilnetz, das dem ALB oder Ingress-Service zugeordnet wurde.
3.	Das öffentliche Netz leitet die Anforderung automatisch an den Workerknoten weiter, der den ALB oder Ingress-Service hostet.
4.	Der Workerknoten leitet die Anforderung an die interne Cluster-IP-Adresse und an die Portnummer des ALB oder des Ingress-Service weiter. Diese interne Cluster-IP-Adresse ist nur innerhalb des Clusters zugänglich.
5.	Innerhalb des Workerknotens leitet "kube-proxy" die Anforderung an den ALB oder Ingress-Service weiter.
6.	Wenn sich die Anwendung auf demselben Workerknoten befindet, wird "iptables" verwendet, um zu ermitteln, welche interne Schnittstelle zum Weiterleiten der Anforderung verwendet wird. Falls sich die Anwendung auf einem anderen Workerknoten befindet, nimmt der Calico vRouter-Knoten die Weiterleitung unter Verwendung der IP-in-IP-Kapselung nur dann an den entsprechenden Workerknoten weiter, wenn sich der Workerknoten in einem anderen Teilnetz befindet.

### Von externem Benutzer im Internet an eine Webschicht, die in einem Container in ICP gehostet wird

1.	Der externe Benutzer stellt über die URL eine Anforderung an die Webschicht.
2.	DNS wird verwendet, um die IP-Adresse zu ermitteln. Bei dieser IP-Adresse handelt es sich um eine öffentliche {{site.data.keyword.cloud_notm}}-Adresse in einem portierbaren Teilnetz (der VCS-Instanz zugeordnet).
3.	Das öffentliche Netz leitet die Anforderung automatisch an den vSphere ESXi-Host weiter, der das ESG hostet.
4.	Das ESG leitet die Anforderung an die interne Cluster-IP-Adresse und an die Portnummer des ALB oder des Ingress-Service weiter. Das IP-Paket wird in einem VXLAN-Rahmen gekapselt, wenn sich das ESG und der ALB oder der Ingress-Service auf unterschiedlichen vSphere ESXi-Hosts befinden. Diese interne Cluster-IP-Adresse ist nur innerhalb des Clusters zugänglich.
5.	Innerhalb des Workerknotens leitet "kube-proxy" die Anforderung an den ALB oder Ingress-Service weiter.
6.	Wenn sich die Anwendung auf demselben Workerknoten befindet, wird "iptables" verwendet, um zu ermitteln, welche interne Schnittstelle zum Weiterleiten der Anforderung verwendet wird. Wenn sich die Anwendung auf einem anderen Workerknoten befindet, nimmt der Calico vRouter-Knoten die Weiterleitung an den entsprechenden Workerknoten vor und verwendet dabei IP-in-IP-Kapselung. Das IP-in-IP-Paket wird für den Transport zum vSphere ESXi-Host in einem VXLAN-Rahmen gekapselt, auf dem sich der Workerknoten befindet.

### Von einer Webschicht, die in einem Container in IKS gehostet wird, an eine Datenbankschicht, die in einer VM in VCS gehostet wird

Wie die Routentabellen in den ESGs und vRoutern mit Daten gefüllt werden, hängt von der Integrationsmethode ab. Siehe "IKS- und VCS-Integration".
1.	Die Webschicht, die in einem Container in IKS ausgeführt wird, stellt eine Anforderung an eine Datenbank, die auf einer VM in der VCS-Instanz ausgeführt wird.
2.	DNS wird verwendet, um die Anforderung an die IP-Adresse der Datenbank aufzulösen.
3.	Der Container sendet die Anfrage an den Calico vRouter.
4.	Der vRouter verfügt über eine Routentabelle, die mit den IP-Adressbereichen gefüllt ist, die in der VCS-Instanz gehostet werden.
5.	Der vRouter leitet die Anforderung weiter, verwendet jedoch SNAT, um die Quellen-IP-Adresse von der IP-Adresse des Pods in die IP-Adresse des Workerknotens zu ändern.
6.	Der Workerknoten, der als Host für den vRouter fungiert, sendet die Anforderung an den BCR.
7.	Der BCR sendet die Anforderung an das ESG.
8.	Das ESG nimmt die Weiterleitung dann an den DLR vor.
9.	Der DLR stellt die Anfrage an das erforderliche VXLAN.
10.	Die Datenbank-VM empfängt die Anforderung.

### Von einer Webschicht, die in einem Container in ICP gehostet wird, an eine Datenbankschicht, die in einer VM in VCS gehostet wird

Wie die Routentabellen in den ESGs und vRoutern mit Daten gefüllt werden, hängt von der Integrationsmethode ab. Siehe "ICP- und VCS-Integration".
1.	Die Webschicht, die in einem Container in ICP ausgeführt wird, stellt eine Anforderung an eine Datenbank, die auf einer VM in derselben VCS-Instanz ausgeführt wird.
2.	DNS wird verwendet, um die Anforderung an die IP-Adresse der Datenbank aufzulösen.
3.	Der Container sendet die Anfrage an den Calico vRouter.
4.	Der vRouter verfügt über eine Routentabelle, die mit den IP-Adressbereichen gefüllt ist, die in der VCS-Instanz gehostet werden.
5.	Der vRouter leitet die Anforderung weiter, verwendet jedoch SNAT, um die Quellen-IP-Adresse von der IP-Adresse des Pods in die IP-Adresse des Workerknotens zu ändern.
6.	Der Workerknoten, der als Host für den vRouter fungiert, sendet die Anforderung an das ESG.
7.	Das ESG nimmt die Weiterleitung dann an den DLR vor.
8.	Der DLR stellt die Anfrage an das erforderliche VXLAN.
9.	Die Datenbank-VM empfängt die Anforderung.

### Unternehmensbenutzer im unternehmensweiten Netzzugriff auf eine VM in VCS

1.	Ein Unternehmensbenutzer, der mit dem internen Unternehmensnetz verbunden ist, fordert eine Ressource auf einer VM an, die in VCS gehostet wird.
2.	DNS wird verwendet, um die IP-Adresse der VM zu bestimmen. Diese IP-Adresse befindet sich in einem Netz, das auf {{site.data.keyword.cloud_notm}} ausgedehnt wurde.
3.	Der lokale Router leitet den Datenverkehr an den vSphere-Host weiter, der den L2-Konzentrator hostet.
4.	Der L2-Konzentrator kapselt die Anforderung in einem sicheren Kanal und leitet sie an den fernen L2-Konzentrator weiter, der in {{site.data.keyword.cloud_notm}} gehostet wird. Dabei wird die private portierbare IP-Teilnetzadresse verwendet, die dem Gerät zugeordnet ist. Die Weiterleitung erfolgt über den lokalen Router.
5.	Die lokale Route sucht in der zugehörigen Routing-Tabelle, bemerkt, dass die IP-Adresse für den fernen L2-Konzentrator an die WAN-Schnittstelle gesendet werden muss, und nimmt die Weiterleitung durch das WAN über den {{site.data.keyword.cloud_notm}} XCR-Router via BCR vor.
6.	Der L2-Konzentrator empfängt die Anforderung und stellt sie in das VXLAN, in dem sich das erweiterte Netz befindet.
7.	Die VM empfängt die Anforderung.

### Weitere Ressourcen

* [{{site.data.keyword.cloud_notm}}-Netz](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [Whitepaper für Container](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (PDF-Download)
* [Blog zu VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [Datenblatt für VMware HCX on {{site.data.keyword.cloud_notm}}](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [Lösungsarchitektur von VMware HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [Maximale Werte der Konfiguration von NSX for vSphere 6.4.3](https://configmax.vmware.com/guest)
* [Dokumentation zur {{site.data.keyword.cloud_notm}}-Plattform](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.cloud_notm}} Kubernetes-Service](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Calico-Projekt](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)

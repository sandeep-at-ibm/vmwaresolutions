---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Netzzugriff und Datenfluss
{: #vcsicp-detail-design-network}

## Zugriff auf Containeranwendung – IBM Cloud Private
{: #vcsicp-detail-design-network-container-icp}

Es gibt im Wesentlichen drei Methoden, um einen externen Datenverkehr und Zugriff auf Ihre Kubernetes-Cluster-Anwendungen zu ermöglichen:

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Private
{: #vcsicp-detail-design-network-nodeport-icp}

NodePorts sind eine einfache Möglichkeit, externen Zugriff auf eine Workload für die Erstentwicklung und den Test zu ermöglichen, aber sie sind nicht für den Produktionsbetrieb zu empfehlen. Dafür sind Ingress oder LoadBalancer geeignet.

### LoadBalancer - IBM Cloud Private
{: #vcsicp-detail-design-network-loadbalancer-icp}

Derzeit unterstützt die {{site.data.keyword.icpfull_notm}}-Plattform eine externe Lastausgleichsfunktion (LoadBalancer) für die Anwendungsworkload.

### Ingress - IBM Cloud Private
{: #vcsicp-detail-design-network-ingress-icp}

Bei Ingress handelt es sich um eine Sammlung von Regeln, die eingehende Verbindungen ermöglichen, um die Cluster-Services zu erreichen. Ingress kann so konfiguriert werden, dass es den Services extern erreichbare URLs zur Verfügung stellt, Lastausgleich für den Datenverkehr ermöglicht, SSL beendet, namensbasiertes virtuelles Hosting anbietet usw.  Der Proxy-Knoten in der {{site.data.keyword.icpfull_notm}}-Infrastruktur führt diese Funktion aus.

## Zugriff auf Containeranwendung – IBM Cloud Kubernetes-Service
{: #vcsicp-detail-design-network-container-iks}

Es gibt im Wesentlichen drei Methoden, um einen externen Datenverkehr und Zugriff auf Ihre Kubernetes-Cluster-Anwendungen zu ermöglichen:

- NodePort
- LoadBalancer
- Ingress

### NodePort - IBM Cloud Kubernetes-Service
{: #vcsicp-detail-design-network-nodeport-iks}

NodePorts sind eine einfache Möglichkeit, externen Zugriff auf eine Workload für die Erstentwicklung und den Test zu ermöglichen, aber sie sind nicht für den Produktionsbetrieb zu empfehlen. Dafür sind Ingress oder LoadBalancer geeignet.

### LoadBalancer - IBM Cloud Kubernetes-Service
{: #vcsicp-detail-design-network-loadbalancer-iks}

Jeder {{site.data.keyword.containerlong_notm}}-Cluster wird mit einem öffentlichen oder privaten Application Load Balancer (ALB) bereitgestellt. Der ALB verwendet einen sicheren und eindeutigen öffentlichen oder privaten Eingangspunkt, um eingehende Anforderungen an Ihre Anwendungen weiterzuleiten.

### Ingress - IBM Cloud Kubernetes-Service
{: #vcsicp-detail-design-network-ingress-iks}

Bei Ingress handelt es sich um eine Sammlung von Regeln, die eingehende Verbindungen ermöglichen, um die Cluster-Services zu erreichen. Ingress kann so konfiguriert werden, dass es den Services extern erreichbare URLs zur Verfügung stellt, Lastausgleich für den Datenverkehr ermöglicht, SSL beendet, namensbasiertes virtuelles Hosting anbietet usw.

## Datenfluss
{: #vcsicp-detail-design-network-traffic-flows}

Für den Datenfluss gibt es die folgenden Möglichkeiten:

- Von externem Benutzer im Internet an eine Webschicht, die in einem Container in {{site.data.keyword.icpfull_notm}} gehostet wird
- Von einer Webschicht, die in einem Container in {{site.data.keyword.icpfull_notm}} gehostet wird, an eine Datenbankschicht, die in einer VM in VMware vCenter Server in {{site.data.keyword.cloud_notm}} gehostet wird
- Von einem Benutzer im unternehmensweiten Netz an eine VM in vCenter Server

### Von externem Benutzer im Internet an eine Webschicht, die in einem Container in IBM Cloud Private gehostet wird
{: #vcsicp-detail-design-network-external-user}

1. Der externe Benutzer stellt über die URL eine Anforderung an die Webschicht.
2.	DNS wird verwendet, um die IP-Adresse zu ermitteln. Bei dieser IP-Adresse handelt es sich um eine öffentliche {{site.data.keyword.cloud_notm}}-Adresse in einem portierbaren Teilnetz, das der vCenter Server-Instanz zugeordnet ist.
3.	Das öffentliche Netz leitet die Anforderung automatisch an den vSphere ESXi-Host weiter, der das ESG hostet.
4.	Das ESG leitet die Anforderung an die interne Cluster-IP-Adresse und an die Portnummer des ALB oder des Ingress-Service weiter. Das IP-Paket wird in einem VXLAN-Rahmen gekapselt, wenn sich das ESG und der ALB oder der Ingress-Service auf unterschiedlichen vSphere ESXi-Hosts befinden. Diese interne Cluster-IP-Adresse ist nur innerhalb des Clusters zugänglich.
5.	Innerhalb des Workerknotens leitet "kube-proxy" die Anforderung an den ALB oder Ingress-Service weiter.
6.	Wenn sich die Anwendung auf demselben Workerknoten befindet, wird "iptables" verwendet, um zu ermitteln, welche interne Schnittstelle zum Weiterleiten der Anforderung verwendet wird. Wenn sich die Anwendung auf einem anderen Workerknoten befindet, nimmt der Calico vRouter-Knoten die Weiterleitung an den entsprechenden Workerknoten vor und verwendet dabei IP-in-IP-Kapselung. Das IP-in-IP-Paket wird für den Transport zum vSphere ESXi-Host in einem VXLAN-Rahmen gekapselt, auf dem sich der Workerknoten befindet.

### Von einer Webschicht, die in einem Container in IBM Cloud Private gehostet wird, an eine Datenbankschicht, die in einer VM in vCenter Server gehostet wird
{: #vcsicp-detail-design-network-web-tier}

Wie die Routentabellen in den ESGs und vRoutern mit Daten gefüllt werden, hängt von der Integrationsmethode ab. Siehe "{{site.data.keyword.icpfull_notm}}- und vCenter Server-Integration".

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
{: #vcsicp-detail-design-network-enterprise-user}

1.	Ein Unternehmensbenutzer, der mit dem internen Unternehmensnetz verbunden ist, fordert eine Ressource auf einer VM an, die in vCenter Server gehostet wird.
2.	DNS wird verwendet, um die IP-Adresse der VM zu bestimmen. Diese IP-Adresse befindet sich in einem Netz, das auf {{site.data.keyword.cloud_notm}} erweitert ist.
3.	Der lokale Router leitet den Datenverkehr an den vSphere-Host weiter, der den L2-Konzentrator hostet.
4.	Der L2-Konzentrator kapselt die Anforderung in einem sicheren Kanal und leitet sie an den fernen L2-Konzentrator weiter, der in {{site.data.keyword.cloud_notm}} gehostet wird. Dabei wird die private portierbare IP-Teilnetzadresse verwendet, die dem Gerät zugeordnet ist. Die Weiterleitung erfolgt über den lokalen Router.
5.	Die lokale Route sucht in der zugehörigen Routing-Tabelle, bemerkt, dass die IP-Adresse für den fernen L2-Konzentrator an die WAN-Schnittstelle gesendet werden muss, und nimmt die Weiterleitung durch das WAN über den {{site.data.keyword.cloud_notm}} XCR-Router via BCR vor.
6.	Der L2-Konzentrator empfängt die Anforderung und stellt sie in das VXLAN, in dem sich das erweiterte Netz befindet.
7.	Die VM empfängt die Anforderung.

## Netz mit öffentlichem Zugang
{: #vcsicp-detail-design-network-public-access-net}

{{site.data.keyword.icpfull_notm}} und CAM erfordern standardmäßig Internetkonnektivität zum Abrufen von Docker-Images, Helm-Diagrammen, Terraform-Vorlagen und Betriebssystempaketmanagern.
In den neuesten Releases wird jetzt die Unterstützung für Proxy-basierte Installationsprozesse für Installationen unterstützt, die nicht direkt mit dem Internet verbunden sind und Optionen für die Installation in einem Offlinemodus bieten.

###	NSX-Firewall
{: #vcsicp-detail-design-network-nsx-firewall}

Die {{site.data.keyword.icpfull_notm}} NSX Edge-Firewall ist mit Regeln konfiguriert, die Folgendes zulassen:
*	VXLAN-Netzen einen öffentlichen Zugriff ermöglichen
*	VXLAN-Netzen Zugriff auf private {{site.data.keyword.cloud_notm}}-Netze ermöglichen
*	Privaten {{site.data.keyword.cloud_notm}}-Netzen Zugriff auf VXLAN-Netze ermöglichen

### NSX-NAT
{: #vcsicp-detail-design-network-nsx-nat}

Die {{site.data.keyword.icpfull_notm}} NSX NAT ist mit den folgenden NATs konfiguriert:
*	SNAT für VXLAN-Zugriff auf öffentliche Netze
*	SNAT für VXLAN-Zugriff auf private {{site.data.keyword.cloud_notm}}-Netze
*	DNAT für {{site.data.keyword.icpfull_notm}}-Cluster-vIPs

## Zugehörige Links
{: #vcsicp-detail-design-network-related}

* [Übersicht über vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

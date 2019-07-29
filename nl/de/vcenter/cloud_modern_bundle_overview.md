---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: single-node trial, migration app modernization, tech specs migration app modernization

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Single-node Trial für Migration und Anwendungsmodernisierung - Übersicht
{: #cloud_modern_bundle_overview}

Mit Single-node Trial für Migration und App-Modernisierung können Sie {{site.data.keyword.cloud_notm}} dahingehend testen, ob VMware-Workloads nach {{site.data.keyword.cloud}} migriert werden, und anschließend einfache Workloads mithilfe von Containern modernisieren.

Single-node Trial ist eine Testversion von {{site.data.keyword.cloud_notm}} Private Hosted auf VMware vCenter Server on {{site.data.keyword.cloud_notm}}, mit der die Kubernetes-Managementplattform für Container und die Single-Tenant-VMware-Plattform bereitstellt wird, die mit den gleichen Tools wie in lokalen Umgebungen verwaltet werden kann. Sie können die Geschwindigkeit und die Skalierung der Cloud nutzen und gleichzeitig das gleiche Niveau an Kontrolle und Sichtbarkeit aufrechterhalten, das Sie auch beim lokalen Betrieb erhalten.

Die Testversion ist für die Migration von bis zu 20 einfachen Entwicklungs- oder Testworkloads mit vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle und Containerisierung dieser Workloads mit der Kubernetes-basierten Anwendungsentwicklungsplattform "{{site.data.keyword.cloud_notm}} Private Hosted" konzipiert. Mittels Automatisierung wird VMware HCX in {{site.data.keyword.cloud_notm}} installiert und konfiguriert, provide ein lokaler HCX-Aktivierungsschlüssel wird bereitgestellt und eine kleine Entwicklungs- und Test-Topologie {{site.data.keyword.cloud_notm}} Private Hosted wird innerhalb weniger Stunden installiert und konfiguriert.

Single-node Trial für Migration und App-Modernisierung ist nur für den Machbarkeitsnachweis (proof of concept, POC) vorgesehen. Die Umgebung ist nicht für Workloads im Produktionsbetrieb geeignet. Managementfunktionen wie das Hinzufügen und Entfernen von Hosts und Clustern, das Bestellen von Add-on-Services und das Anwenden von Updates werden nicht unterstützt.
{:important}

Um den größtmöglichen Nutzen aus der Single-node Trial-Instanz zu ziehen, können Sie [bedarfsgerechte Beratung zu IBM Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:new_window} der [Expertenservices für IBM Analytics Cloud](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:new_window} in Anspruch nehmen. Hier finden Sie Unterstützung für die Migration Ihrer VMware-Workloads nach {{site.data.keyword.cloud_notm}}. Darüber hinaus kann [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:new_window} Sie bei der Beschleunigung der Anwendungsmodernisierung mithilfe der neuesten Cloud Native-Praktiken unterstützen.

Diese Testversion ist für eine Nutzung von bis zu 90 Tagen vorgesehen. Wenn Sie das Testen abschlossen haben, können Sie die Umgebung löschen und anschließend eine neue Umgebung einrichten, die Ihren Kapazitätsanforderungen entspricht.
{:note}

## Technische Spezifikationen für Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #cloud_modern_bundle_overview-tech-specs}

Folgende Komponenten sind in Ihrer Single-node Trial-Instanz für Migration und Anwendungsmodernisierung enthalten.

Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt wird, variieren.
{:note}

### Bare Metal Server
{: #cloud_modern_bundle_overview-bare-metal}

Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz mit 384 GB RAM) für bis zu 20 VMs

#### CPU-Overcommits
{: #cloud_modern_bundle_overview-cpu}

* 16:1-CPU-Overcommit für vCenter Server-Management, HCX und 20 VMs für Kundenworkload
* 11:1-CPU-Overcommit für {{site.data.keyword.cloud_notm}} Private

#### RAM-Overcommit
{: #cloud_modern_bundle_overview-ram}

* 1.22:1-RAM-Overcommit für eine Kundenbereitstellung von 20 Workload-VMs mit jeweils 8 GB
* 1:1 (kein Overcommit) für eine Kundenbereitstellung von 9 Workload-VMs mit jeweils 8 GB

### NFS-Speicher
{: #cloud_modern_bundle_overview-nfs-storage}

* 2 TB für Management
* 1 TB für Kundenworkload (für 20 Kunden-VMs)
* 4 TB für {{site.data.keyword.cloud_notm}} Private Hosted

### Netzspezifikationen für Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung
{: #cloud_modern_bundle_overview-networking-specs}

Die folgenden Netzkomponenten werden bestellt:
*  10-Gbps-Uplinks für öffentliche und private Netze
*  3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
*  1 VXLAN (Virtual eXtensible LAN) mit einem verteilten logischen Router (Distributed Logical Router, DLR) für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads, die mit Netzen der Schicht 2 (L2) verbunden sind. Das VXLAN wird als Muster für die Routingtopologie bereitgestellt, das Sie ändern, als Ausgangspunkt für Erstellungen verwenden oder entfernen können. Sie können außerdem Sicherheitszonen hinzufügen, indem Sie weitere VXLANs an neue logische Schnittstellen im DLR anhängen.
*  2 VMware NSX Edge Services Gateways:
  * 1 sicheres VMware NSX Edge Services Gateway (ESG) für Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Dieses ESG wird von den IBM Management-VMs für die Kommunikation mit bestimmten externen IBM Managementkomponenten verwendet, die mit der Automatisierung zusammenhängen.

    Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Falls Sie es ändern, sind Sie möglicherweise nicht in der Lage, die Single-node Trial-Instanz für Migration und Anwendungsmodernisierung über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.
    {:important}
  * 1 sicheres vom Kunden verwaltetes VMware NSX Edge Services Gateway für eingehenden und abgehenden HTTPS-Workloaddatenverkehr, das von IBM als Vorlage bereitgestellt wird und von Ihnen geändert werden kann, um den VPN-Zugriff oder den öffentlichen Zugriff zu ermöglichen.

### Virtual Server-Instanzen
{: #cloud_modern_bundle_overview-vsi}

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:

* Eine VSI für IBM CloudBuilder, die nach vollständiger Bereitstellung der Instanz abgebrochen wird.
* Eine VSI von Microsoft Windows Server für Microsoft Active Directory (AD) wird bereitgestellt und kann zur Suche verwendet werden. Die Virtual Server-Instanz (VSI) dient als DNS für die Instanz, auf der die Hosts und VMs registriert sind.

### Von IBM bereitgestellte Lizenzen und Gebühren
{: #cloud_modern_bundle_overview-license-and-fee}

Ihre Bestellung der Single-node Trial-Instanz für Migration und Anwendungsmodernisierung enthält die folgenden Lizenzen:

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Single-node Trial-Instanzen für Migration und Anwendungsmodernisierung bieten keine BYOL-Unterstützung (BYOL = Bring Your Own License; Verwendung der eigenen Lizenz).
{:note}

## Technische Spezifikationen für VMware HCX on IBM Cloud
{: #cloud_modern_bundle_overview-hcx-tech-specs}

In der Single-node Trial für Migration und Anwendungsmodernisierung ist HCX on {{site.data.keyword.cloud_notm}} enthalten. Mit dem Service "HCX on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

Lokale HCX-Instanzen schließen nur Lizenzierung und Aktivierung ein.
{:note}

### Ein Aktiv/Passiv-Paar von VMware NSX Edge Services Gateways für das HCX-Management
{: #cloud_modern_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Festplatte: 3 GB VMDK

### HCX-Management-Appliance - virtuelle Maschine
{: #cloud_modern_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Festplatte: 60 GB VMDK

Weitere HCX-Appliances werden bei der Konfiguration wie für die L2-Konnektivität, die WAN-Optimierung und Gateway-Verbindungen erforderlich bereitgestellt.

### Netzspezifikationen für HCX on IBM Cloud
{: #cloud_modern_bundle_overview-hcx-networking-specs}

* 1 öffentliches portierbares Teilnetz mit 16 IP-Adressen
* 2 private portierbare Teilnetze mit 64 IP-Adressen
* 8 IP-Adressen aus dem privaten portierbaren vMotion-Teilnetz

## Technische Spezifikationen für IBM Cloud Private Hosted
{: #cloud_modern_bundle_overview-icp-tech-specs}

{{site.data.keyword.cloud_notm}} Private Hosted 3.1.2 wird unter Verwendung der Entwicklungs-/Test-Topologie auf allen Single-Node Trial-Instanzen für Migration und Anwendungsmodernisierung installiert. Weitere Informationen zu {{site.data.keyword.cloud_notm}} Private Hosted finden Sie in [{{site.data.keyword.cloud_notm}} Private Hosted - Übersicht](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview).

## Technische Spezifikationen für IBM Cloud Automation Manager
{: #cloud_modern_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 wird unter Verwendung der Entwicklungs-/Test-Topologie auf allen Single-Node Trial-Instanzen für Migration und Anwendungsmodernisierung installiert. Weitere Informationen zu {{site.data.keyword.cloud_notm}} Automation Manager finden Sie in der [Dokumentation zu {{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: new_window}.

## Zugehörige Links
{: #cloud_modern_bundle_overview-related}

* [vCenter Server and {{site.data.keyword.cloud_notm}} Private - Leitfaden](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Ticket für {{site.data.keyword.cloud_notm}} Private öffnen](https://www.ibm.com/mysupport/s/?language=en_US){:new_window}
* [VMware HCX-Ressourcen](https://hcx.vmware.com/#/docs){:new_window}
* [Benutzerhandbuch zu VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:new_window}

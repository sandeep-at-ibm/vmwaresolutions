---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über Single-node Trial für Datenschutz und Disaster-Recovery
{: #dr_backup_bundle_overview}

Mit Single-node Trial für Datenschutz und Disaster-Recovery können Sie in {{site.data.keyword.cloud}} überprüfen, ob VMware-Workloads nach {{site.data.keyword.cloud_notm}} migriert und wiederhergestellt werden. Darüber hinaus umfasst Single-node Trial für Datenschutz und Disaster-Recovery die Services 'Veeam on {{site.data.keyword.cloud_notm}}', 'VMware HCX on {{site.data.keyword.cloud_notm}}' und 'Zerto on {{site.data.keyword.cloud_notm}}'.

Single-node Trial ist eine Testversion von VMware vCenter Server on {{site.data.keyword.cloud_notm}}, von der die Single-Tenant-VMware-Plattform bereitstellt wird, die mit den gleichen Tools wie in lokalen Umgebungen verwaltet werden kann. Sie können die Geschwindigkeit und die Skalierung der Cloud nutzen und gleichzeitig das gleiche Niveau an Kontrolle und Sichtbarkeit aufrechterhalten, das Sie auch beim lokalen Betrieb erhalten.

Die Testversion ist für die Migration von bis zu 20 einfachen Entwicklungs- oder Testworkloads mit vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle konzipiert. Mittels Automatisierung werden innerhalb weniger Stunden 'VMware HCX on {{site.data.keyword.cloud_notm}}' installiert und konfiguriert, ein lokaler HCX-Aktivierungsschlüssel bereitgestellt und 'Veeam on {{site.data.keyword.cloud_notm}}' sowie 'Zerto on {{site.data.keyword.cloud_notm}}' installiert und konfiguriert. Mit 'Veeam on {{site.data.keyword.cloud_notm}}' und 'Zerto on {{site.data.keyword.cloud_notm}}' können Sie 20 virtuelle Maschinen sichern und replizieren.

Single-node Trial für Datenschutz und Disaster-Recovery ist nur für den Machbarkeitsnachweis (proof of concept, POC) vorgesehen. Die Umgebung ist nicht für Workloads im Produktionsbetrieb geeignet. Managementfunktionen wie das Hinzufügen und Entfernen von Hosts und Clustern, das Bestellen weiterer Add-on-Services und das Anwenden von Updates werden nicht unterstützt.
{:important}

Nach der Bereitstellung der Single-node Trial-Instanz können Sie die [bedarfsgerechte Beratung zu IBM Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external} der [Expertenservices für IBM Analytics Cloud](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external} zur Unterstützung für Ihre Instanz nutzen. Darüber hinaus kann [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external} Sie bei der Beschleunigung der Anwendungsmodernisierung mithilfe der neuesten Cloud Native-Praktiken unterstützen.

Diese Testversion ist für eine Nutzung von bis zu 90 Tagen vorgesehen. Monatlich wiederkehrende Gebühren werden nicht bei der Bestellung der Instanz, sondern auf der Grundlage Ihres Abrechnungsplans in Rechnung gestellt. Wenn die Instanz nicht am oder vor dem letzten Tag des Abrechnungszyklus storniert wird, wird Sie für den nächsten Monat in Rechnung gestellt. Für eine 90-Tage-Testversion können vier Monate an Gebühren abgerechnet werden, wenn nicht vor Beginn des vierten Monats storniert wird.
{:note}

Wenn Sie das Testen abschlossen haben, können Sie die Umgebung löschen und anschließend eine neue Umgebung einrichten, die Ihren Kapazitätsanforderungen entspricht.

## Technische Spezifikationen für Single-node Trial-Instanzen für Datenschutz und Disaster-Recovery
{: #dr_backup_bundle_overview-tech-specs}

Folgende Komponenten sind in der Single-node Trial-Instanz für Datenschutz und Disaster-Recovery enthalten.

Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt wird, variieren.
{:note}

### Bare Metal Server
{: #dr_backup_bundle_overview-bare-metal}

Skylake Dual Intel Xeon Gold 5120-Prozessor / 28 Kerne insgesamt, 2,2 GHz mit 384 GB RAM für bis zu 20 VMs

#### CPU-Overcommits
{: #dr_backup_bundle_overview-cpu}

16:1-CPU-Overcommit für vCenter Server-Management, HCX und 20 VMs für Kundenworkload

#### RAM-Overcommit
{: #dr_backup_bundle_overview-ram}

* 1.22:1-RAM-Overcommit für eine Kundenbereitstellung von 20 Workload-VMs mit jeweils 8 GB
* 1:1 (kein Overcommit) für eine Kundenbereitstellung von 9 Workload-VMs mit jeweils 8 GB

### NFS-Speicher
{: #dr_backup_bundle_overview-nfs-storage}

* 2 TB für Management
* 1 TB für Kundenworkload (für 20 Kunden-VMs)

### Netzspezifikationen für Single-node Trial-Instanzen für Datenschutz und Disaster-Recovery
{: #dr_backup_bundle_overview-networking-specs}

Die folgenden Netzkomponenten werden bestellt:
*  10 Gb/s-Uplinks für öffentliche und private Netze
*  3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
*  1 VXLAN (Virtual eXtensible LAN) mit einem verteilten logischen Router (Distributed Logical Router, DLR) für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads, die mit Netzen der Schicht 2 (L2) verbunden sind. Das VXLAN wird als Muster für die Routingtopologie bereitgestellt, das Sie ändern, als Ausgangspunkt für Erstellungen verwenden oder entfernen können. Sie können außerdem Sicherheitszonen hinzufügen, indem Sie weitere VXLANs an neue logische Schnittstellen im DLR anhängen.
*  2 VMware NSX Edge Services Gateways:
  * 1 sicheres VMware NSX Edge Services Gateway (ESG) für Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Dieses ESG wird von den IBM Management-VMs für die Kommunikation mit bestimmten externen IBM Managementkomponenten verwendet, die mit der Automatisierung zusammenhängen.

    Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Falls Sie es ändern, sind Sie möglicherweise nicht in der Lage, die Single-node Trial-Instanz für Datenschutz und Disaster-Recovery über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.
    {:important}
  * 1 sicheres vom Kunden verwaltetes VMware NSX Edge Services Gateway für eingehenden und abgehenden HTTPS-Workloaddatenverkehr, das von IBM als Vorlage bereitgestellt wird und von Ihnen geändert werden kann, um den VPN-Zugriff oder den öffentlichen Zugriff zu ermöglichen.

### Virtual Server-Instanzen
{: #dr_backup_bundle_overview-vsi}

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:

* Eine VSI für IBM CloudBuilder, die nach vollständiger Bereitstellung der Instanz abgebrochen wird.
* Eine VSI von Microsoft Windows Server für Microsoft Active Directory (AD) wird bereitgestellt und kann zur Suche verwendet werden. Die Virtual Server-Instanz (VSI) dient als DNS für die Instanz, auf der die Hosts und VMs registriert sind.
* Eine VSI für Zerto on {{site.data.keyword.cloud_notm}} - Zerto Virtual Manager.
* Eine VSI mit Veeam Backup and Replication 9.5 OS Add-on und Veeam Availability Suite 9.5.

### Von IBM bereitgestellte Lizenzen und Gebühren
{: #dr_backup_bundle_overview-license-and-fee}

Ihre Bestellung der Single-node Trial-Instanz für Datenschutz und Disaster-Recovery enthält die folgenden Lizenzen:

* Die Lizenzen von vCenter Server with Hybridity Bundle:
  * VMware vSphere Enterprise Plus 6.7u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Single-node Trial-Instanzen für Datenschutz und Disaster-Recovery bieten keine BYOL-Unterstützung (BYOL = Bring Your Own License; Verwendung der eigenen Lizenz).
{:note}

## Technische Spezifikationen für VMware HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-tech-specs}

Single-node Trial für Datenschutz und Disaster-Recovery umfasst HCX on {{site.data.keyword.cloud_notm}}. Mit dem Service "HCX on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

Lokale HCX-Instanzen schließen nur Lizenzierung und Aktivierung ein.
{:note}

### Ein Aktiv/Passiv-Paar von VMware NSX Edge Services Gateways für das HCX-Management
{: #dr_backup_bundle_overview-esg}

* CPU: 6 vCPU
* RAM: 8 GB
* Festplatte: 3 GB VMDK

### HCX-Management-Appliance - virtuelle Maschine
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU: 4 vCPU
* RAM: 12 GB
* Festplatte: 60 GB VMDK

Weitere HCX-Appliances werden bei der Konfiguration wie für die L2-Konnektivität, die WAN-Optimierung und Gateway-Verbindungen erforderlich bereitgestellt.

### Netzspezifikationen für HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-networking-specs}

* 1 öffentliches portierbares Teilnetz mit 16 IP-Adressen
* 2 private portierbare Teilnetze mit 64 IP-Adressen
* 8 IP-Adressen aus dem privaten portierbaren vMotion-Teilnetz

## Technische Spezifikationen für Veeam on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-veeam-tech-specs}

Single-node Trial für Datenschutz und Disaster-Recovery umfasst Veeam on {{site.data.keyword.cloud_notm}}. Mit dem Service 'Veeam on {{site.data.keyword.cloud_notm}}' werden die folgenden Komponenten bestellt und einbezogen.

* Lizenz für 25 Pakete von Veeam Availability Suite
* 4.000 GB Speicher
* 0,25 IOPS/GB Speicherleistung
* Windows Server 2016 Standard Edition (64-Bit)
* 4 Kerne mit je 2.0 GHz
* 8 GB RAM
* Uplink zum privaten Netz mit 1 Gb/s
* 100-GB-Festplatte (SAN)

## Technische Spezifikationen für Zerto on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-zerto-tech-specs}

Single-node Trial für Datenschutz und Disaster-Recovery umfasst Zerto on {{site.data.keyword.cloud_notm}}. Mit dem Service "Zerto on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

* Lizenz für Zerto Virtual Replication Version 6.5u3
* Eine Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 Kerne mit je 2.0 GHz
* 4 GB RAM
* Windows Server 2016 Standard Edition (64-Bit)
* 100-GB-Festplatte (SAN)

## Technische Spezifikationen für IBM Cloud Automation Manager
{: #dr_backup_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 wird unter Verwendung der Entwicklungs-/Test-Topologie auf allen Single-node Trial-Instanzen für Datenschutz und Disaster-Recovery installiert. Weitere Informationen zu {{site.data.keyword.cloud_notm}} Automation Manager finden Sie in der [Dokumentation zu {{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}.

## Zugehörige Links
{: #dr_backup_bundle_overview-related}

* [VMware HCX-Ressourcen](https://hcx.vmware.com/#/docs){:external}
* [Benutzerhandbuch zu VMware HCX](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Zerto on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)

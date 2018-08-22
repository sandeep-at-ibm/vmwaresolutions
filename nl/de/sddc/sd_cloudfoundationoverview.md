---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-18"

---

# Übersicht über Cloud Foundation

Wenn Sie VMware Cloud Foundation on {{site.data.keyword.cloud}} bestellen, wird automatisch eine vollständige VMware-Umgebung bereitgestellt. Die Basisbereitstellung besteht aus vier {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen mit vorinstalliertem VMware Cloud Foundation-Stack, deren Konfiguration eine einheitliche Plattform für SDDC (Software-Defined Data Center, softwaredefiniertes Rechenzentrum) bereitstellt. Cloud Foundation integriert nativ VMware vSphere, VMware NSX sowie VMware Virtual SAN und seine Architektur basiert auf VMware-geprüften Designs.

## Cloud Foundation-Architektur

In der folgenden Abbildung sind die Gesamtarchitektur und die Komponenten der Cloud Foundation-Bereitstellung dargestellt.

Abbildung 1. Cloud Foundation-Architektur

![Cloud Foundation-Architektur](sd_architecture.svg "Cloud Foundation-Architektur")

### Physische Infrastruktur

Auf dieser Schicht wird die physische Infrastruktur (Rechen-, Speicher- und Netzressourcen) bereitgestellt, die von der virtuellen Infrastruktur genutzt wird.

### Virtualisierungsinfrastruktur (Rechenressourcen, Speicher und Netz)

Diese Schicht virtualisiert die physische Infrastruktur durch verschiedene VMware-Produkte:
* VMware vSphere virtualisiert die physischen Rechenressourcen.
* VMware Virtual SAN (vSAN) stellt auf der Basis des Speichers in den physischen Servern einen softwaredefinierten gemeinsam genutzten Speicher zur Verfügung.
* VMware NSX ist die Netzvirtualisierungsplattform, die logische Netzkomponenten und virtuelle Netze bereitstellt.

### Virtualisierungsmanagement

Diese Schicht besteht aus vCenter Server und stellt die Managementschicht für die virtualisierte Umgebung dar. Zum Verwalten der von IBM gehosteten VMware-Umgebung können Sie die geläufigen und mit der vSphere-API kompatiblen Tools und Scripts verwenden.

In der {{site.data.keyword.vmwaresolutions_short}}-Konsole können Sie die Kapazität Ihrer Instanzen mithilfe der Funktion zum Hinzufügen und Entfernen von ESXi-Servern erweitern und verringern. Darüber hinaus sind Funktionen für das Lebenszyklusmanagement wie das Anwenden von Updates und das Durchführen von Upgrades für die VMware-Komponenten in der gehosteten Umgebung verfügbar.

Ausführliche Informationen zur Architektur enthält der Abschnitt [Lösungsübersicht](../archiref/solution/solution_overview.html).

## Technische Spezifikationen für Cloud Foundation-Instanzen

Ihre Cloud Foundation-Instanz enthält die folgenden Komponenten.

**Hinweis**: Die für Hardware, Netzbetrieb, virtuelle Maschinen und Speicher anfallenden Gebühren können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt ist, variieren.

### Bare Metal Server

Sie können {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen mit einer der folgenden Konfigurationen bestellen:
*  **Angepasst**: {{site.data.keyword.baremetal_short}}-Instanzen mit dem ausgewählten CPU-Modell und der ausgewählten RAM-Größe.   
   * 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
   * 2-CPU Intel Skylake Generation (Intel Xeon 4100/5100/6100 Series)
**Hinweis:** Wenn Sie vSAN-Speicher verwenden wollen, dann benötigt die Konfiguration vier {{site.data.keyword.baremetal_short}}-Instanzen.
* **Vorkonfiguriert**: 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
  * **S (Klein)**: Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 128 GB RAM / 12 Platten
  * **L (Groß)**: Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 12 Platten

### Vernetzung

Die folgenden Netzkomponenten werden bestellt:
* 10-Gbps-Uplinks für öffentliche und private Netze
* 3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
* Sicheres VMware NSX Edge Services Gateway (ESG) für die Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Über dieses ESG kommunizieren virtuelle IBM Management-Maschinen mit bestimmten externen IBM Managementkomponenten, die mit der Automatisierung zusammenhängen. Weitere Information finden Sie im Abschnitt [Stellt das NSX Edge für Management-Services ein Sicherheitsrisiko dar?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)

  **Wichtig**: Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Falls Sie es ändern, sind Sie möglicherweise nicht in der Lage, die Cloud Foundation-Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.

* Die Funktion für EVC (Enhanced vMotion Compatibility) wird automatisch aktiviert, wenn Sie über einen vorhandenen Cluster mit ESXi-Servern verfügen, die von der aktuellen VMware vSphere-Version unterstützt werden. EVC bietet vMotion-Kompatibilität für alle ESXi-Server in einem Cluster, indem sichergestellt wird, dass alle ESXi-Server in einem Cluster die gleiche Gruppe von CPU-Funktionen für virtuelle Maschinen bereitstellen. Mithilfe von EVC können die virtuellen Maschinen zwischen allen ESXi-Servern im Cluster migriert werden. Dies gilt auch dann, wenn die eigentlichen CPUs auf den ESXi-Servern unterschiedlich sind.

### Virtual Server-Instanzen

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:
* 1 VSI für Microsoft Active Directory (AD) und DNS-Service, was für die Unterstützung von Konfigurationen mit mehreren Standorten erforderlich ist. Spezifikation dieser VSI: Windows 2012 R2 (8 GB RAM / 2 CPU-Kerne / 100 GB Plattenspeicher / Duale 1-Gbps-Uplinks für private Netze).
* 1 VSI für IBM CloudBuilder (wird nach vollständiger Bereitstellung der Instanz beendet).
* (Bei Bestellung von Veeam on {{site.data.keyword.cloud_notm}}) 1 VSI für den Veeam-Sicherungsservice wird bestellt.

### Speicher

Abhängig von der von Ihnen ausgewählten {{site.data.keyword.baremetal_short}}-Konfiguration wird der folgende Speicher bestellt:
* 2 1-TB-SATA-Bootlaufwerke
* 2 Solid-State-Cacheplatten mit 960 GB
* 1 RAID-Plattencontroller
* Nur bei Konfiguration des Typs **Angepasst**: Sie können die Anzahl der Plattenlaufwerke sowie Plattentyp und Kapazität gemäß Ihren Anforderungen festlegen.
* Nur bei Konfiguration des Typs **Vorkonfiguriert** - **S (Klein)**: 2 SSD-Kapazitätsplatten mit 1,9 TB.
* Nur bei Konfiguration des Typs **Vorkonfiguriert** - **L (Groß)**: 4 SSD-Kapazitätsplatten mit 3,8 TB.

### Lizenzen (von IBM bereitgestellt oder eigene) und Gebühren

* 4 Lizenzen für VMware vSphere Enterprise Plus 6.5u1
* 4 Lizenzen für VMware vCenter Server 6.5
* 4 Lizenzen für VMware NSX Enterprise 6.3
* 4 Lizenzen für VMware vSAN Advanced oder Enterprise 6.6
* 4 Lizenzen für SDDC Manager (nur von IBM bereitgestellt)
* 4 Support- und Servicegebühren

## Technische Spezifikationen für Cloud Foundation-Erweiterungsknoten

Jeder Cloud Foundation-Erweiterungsknoten stellt die folgenden Komponenten in Ihrem {{site.data.keyword.cloud_notm}}-Konto mit den entsprechenden anfallenden Gebühren bereit.

### Hardware für Erweiterungsknoten

1 {{site.data.keyword.cloud_notm}} Bare Metal Server mit der unter [Technische Spezifikationen für Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances) aufgeführten Konfiguration.

### Lizenzen und Gebühren für Erweiterungsknoten

* 1 Lizenz für VMware vSphere Enterprise Plus 6.5u1
* 1 Lizenz für VMware vCenter Server 6.5
* 1 Lizenz für VMware NSX Enterprise 6.3
* 1 Lizenz für VMware vSAN Advanced oder Enterprise 6.6
* 1 Lizenz für SDDC Manager
* 1 Support- und Servicegebühr

**Wichtig**: Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT**: Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben, außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

### Zugehörige Links

* [Softwareteileliste für Cloud Foundation](sd_bom.html)
* [Cloud Foundation-Instanzen planen](sd_planning.html)
* [Cloud Foundation-Instanzen bestellen](sd_orderinginstance.html)
* [VMware vSphere Documentation Center](https://pubs.vmware.com/vsphere-60/index.jsp){:new_window}
* [VMware NSX 6 Documentation Center](https://pubs.vmware.com/NSX-6/index.jsp){:new_window}
* [EVC and CPU Compatibility FAQ](https://kb.vmware.com/s/article/1005764)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Übersicht über vCenter Server

VMware vCenter Server on {{site.data.keyword.cloud}} ist eine gehostete private Cloud, die den VMware vSphere-Stack als Service bereitstellt. Die VMware-Umgebung basiert auf mindestens zwei (empfohlen drei) {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}-Instanzen, bietet einen gemeinsam genutzten NAS-Speicher sowie Optionen für dedizierten softwaredefinierten Speicher und beinhaltet die automatische Bereitstellung und Konfiguration einer auf VMware NSX basierenden, leicht zu verwaltenden logischen Edge-Firewall.

In zahlreichen Fällen kann die gesamte Umgebung in weniger als einem Tag bereitgestellt werden und die Bare-Metal-Infrastruktur kann die Rechenkapazität nach Bedarf schnell und flexibel skalieren.

Nach der Bereitstellung können Sie den gemeinsam genutzten Speicher vergrößern, indem Sie zusätzliche Dateifreigaben für NFS (Network File System) im {{site.data.keyword.slportal}} bestellen und die Freigaben manuell an alle ESXi-Server in einem Cluster anhängen. Wenn Sie dedizierten Speicher benötigen, können Sie [NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}](../netapp/np_netappoverview.html) nutzen, das sowohl in Konfigurationen mit hoher Leistung (alle mit SSD) als auch mit hoher Speicherkapazität (alle mit SATA) angeboten wird.

VMware vSAN steht ebenfalls als Option für dedizierten Speicher zur Verfügung. Wenn Sie die vSAN-basierte Speicherkapazität eines vSAN-Clusters erhöhen möchten, können Sie nach der Bereitstellung weitere ESXi-Server hinzufügen.

Falls Sie eine von IBM bereitgestellte VMware-Lizenzierung erworben haben, können Sie für VMware NSX Base Edition ein Upgrade auf Advanced oder Enterprise Edition durchführen und zusätzliche VMware-Komponenten wie VMware vRealize Operations erwerben.

Sie können IBM Managed Services hinzufügen, wenn Sie die Routineabläufe und die Wartung der Virtualisierung, des Gastbetriebssystems oder der Anwendungsschichten auslagern möchten. Das Team von {{site.data.keyword.cloud_notm}} Professional Services kann Ihnen durch Migrations-, Implementierungs-, Planungs- und Onboarding-Services ebenfalls dabei helfen, Ihren Einstieg in die Cloud zu beschleunigen.

## vCenter Server-Architektur

In der folgenden Abbildung sind die allgemeine Architektur und die Komponenten einer vCenter Server-Bereitstellung mit drei Knoten dargestellt.

Abbildung 1. Allgemeine vCenter Server-Architektur für einen Cluster mit drei Knoten

![vCenter Server-Architektur](vc_architecture.svg "Allgemeine vCenter Server-Architektur für einen Cluster mit drei Knoten")

### Physische Infrastruktur

Auf dieser Schicht wird die physische Infrastruktur (Rechen-, Speicher- und Netzressourcen) bereitgestellt, die von der virtuellen Infrastruktur genutzt wird.

### Virtualisierungsinfrastruktur (Rechenressourcen und Netz)

Diese Schicht virtualisiert die physische Infrastruktur durch verschiedene VMware-Produkte:
* VMware vSphere virtualisiert die physischen Rechenressourcen.
* VMware NSX ist die Netzvirtualisierungsplattform, die logische Netzkomponenten und virtuelle Netze bereitstellt.

### Virtualisierungsmanagement

Diese Schicht besteht aus vCenter Server Appliance (vCSA), dem NSX-Manager, zwei NSX Edge Services Gateways (ESGs), drei NSX-Controllern, der virtuellen Appliance für Platform Services Controller (PSC) und der virtuellen Serverinstanz (VSI) für IBM CloudDriver. Die CloudDriver-VSI wird bei Bedarf auf Anforderung für bestimmte Operationen, wie zum Beispiel für das Hinzufügen von Hosts zur Umgebung, bereitgestellt.

Das Basisangebot wird mit einer vCenter Server-Appliance bereitgestellt, deren Größe für die Unterstützung einer Umgebung mit bis zu 400 Hosts und bis zu 4000 VMs ausgelegt ist. Zum Verwalten der von IBM gehosteten VMware-Umgebung können Sie dieselben mit der vSphere-API kompatiblen Tools und Scripts verwenden.

Insgesamt benötigt das Basisangebot 38 virtuelle CPUs und 67 GB virtuellen RAM, die für die Virtualisierungsmanagementschicht reserviert sind. Die verbleibende Hostkapazität für Ihre VMs hängt von mehreren Faktoren ab, beispielsweise der Übersubskriptionsrate, der VM-Dimensionierung und den Anforderungen an die Workloadleistung.

Ausführliche Informationen zur Architektur enthält die [Referenzdokumentation zur Architektur von {{site.data.keyword.vmwaresolutions_short}}](../archiref/solution/solution_overview.html).

## Technische Spezifikationen für vCenter Server-Instanzen

Ihre vCenter Server-Instanz enthält die folgenden Komponenten.

**Hinweis**: Verfügbarkeit und Preisgestaltung standardisierter Hardwarekonfigurationen können abhängig vom {{site.data.keyword.CloudDataCent_notm}}, das für die Bereitstellung ausgewählt ist, variieren.

### Bare Metal Server

Sie können drei oder mehr {{site.data.keyword.baremetal_short}}-Instanzen mit einer der folgenden Konfigurationen bestellen:
*  **Angepasst**: {{site.data.keyword.baremetal_short}}-Instanzen mit dem ausgewählten CPU-Modell und der ausgewählten RAM-Größe.   
   * 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
   * 2-CPU Intel Skylake Generation (Intel Xeon 4100/5100/6100 Series)

     **Hinweis:** Wenn Sie vSAN-Speicher verwenden möchten, sind für die Konfiguration vier {{site.data.keyword.baremetal_short}}-Instanzen erforderlich.
*  **Vorkonfiguriert**: 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
   * **S (Klein)** Dual Intel Xeon E5-2620 v4 / 16 Kerne insgesamt, 2,1 GHz / 128 GB RAM / 2 Platten
   * **M (Mittel)** Dual Intel Xeon E5-2650 v4 / 24 Kerne insgesamt, 2,2 GHz / 256 GB RAM / 2 Platten
   * **L (Groß)** Dual Intel Xeon E5-2690 v4 / 28 Kerne insgesamt, 2,6 GHz / 512 GB RAM / 2 Platten

### Vernetzung

Die folgenden Netzkomponenten werden bestellt:
*  10-Gbps-Uplinks für öffentliche und private Netze
*  3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
*  1 VXLAN (Virtual eXtensible LAN) mit einem verteilten logischen Router (Distributed Logical Router, DLR) für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads, die mit Netzen der Schicht 2 (L2) verbunden sind. Das VXLAN wird als Muster für die Routingtopologie bereitgestellt, das Sie ändern, als Ausgangspunkt für Erstellungen verwenden oder entfernen können. Sie können außerdem Sicherheitszonen hinzufügen, indem Sie zusätzliche VXLANs an neue logische Schnittstellen im DLR anhängen.
*  2 VMware NSX Edge Services Gateways:
  * 1 sicheres VMware NSX Edge Services Gateway (ESG) für Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Über dieses ESG kommunizieren virtuelle IBM Management-Maschinen mit bestimmten externen IBM Managementkomponenten, die mit der Automatisierung zusammenhängen. Weitere Informationen finden Sie unter [Netz zur Verwendung des vom Kunden verwalteten ESG konfigurieren](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Wichtig**: Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Falls Sie es ändern, sind Sie möglicherweise nicht in der Lage, die vCenter Server-Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.
  * 1 sicheres vom Kunden verwaltetes VMware NSX Edge Services Gateway für eingehenden und abgehenden HTTPS-Workloaddatenverkehr, das von IBM als Vorlage bereitgestellt wird und von Ihnen geändert werden kann, um den VPN-Zugriff oder den öffentlichen Zugriff zu ermöglichen. Weitere Informationen finden Sie im Abschnitt [Stellt das vom Kunden verwaltete NSX Edge ein Sicherheitsrisiko dar?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

### Virtual Server-Instanzen

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:
* 1 VSI für IBM CloudBuilder, der nach vollständiger Bereitstellung der Instanz beendet wird.
* (Für Instanzen mit V2.2 und höher) Sie haben die Möglichkeit, die Bereitstellung einer einzigen Virtual Server-Instanz (VSI) von Microsoft Windows Server für Microsoft Active Directory (AD) oder aber von zwei virtuellen Microsoft Windows-Maschinen für die Hochverfügbarkeit im Management-Cluster auszuwählen, um die Sicherheit und Leistungsfähigkeit zu erhöhen.
* (Für Instanzen mit V1.9 bis V2.1) 1 VSI von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und virtuellen Maschinen registriert sind, wird bereitgestellt und kann zur Suche verwendet werden.
* (Für Instanzen mit V1.8 und älteren Versionen) 1 VSI für die snapshotbasierte Sicherung der Managementkomponenten, die nach Abschluss der Instanzbereitstellung weiter ausgeführt wird.

### Speicher

Während der Erstbereitstellung können Sie zwischen den Speicheroptionen "vSAN" und "NFS" wählen.

Die Option "vSAN" bietet angepasste Konfigurationen mit unterschiedlichen Optionen für Plattentyp und -menge:
* Plattenmenge: 2, 4, 6 oder 8
* Speicherplatte: 960 GB SSD SED, 1,9 TB SSD SED oder 3,8 TB SSD SED.

  Zusätzlich werden 2 Cacheplatten mit 960 GB pro Host bestellt.

  **Hinweis:** 3,8-TB-Solid-State-Platten (SSD) werden unterstützt, wenn sie in einem Rechenzentrum allgemein verfügbar gemacht werden.

Die Option "NFS" bietet angepassten gemeinsam genutzten Speicher auf Dateiebene für Workloads mit verschiedenen Optionen für Größe und Leistung:
* Größe: 1, 2, 4, 8 oder 12 TB
* Leistung: 2, 4 oder 10 IOPS/GB (E/A-Operationen pro Sekunde und GB).
* Die Dateifreigaben werden einzeln konfiguriert.

Wenn Sie die Option "NFS" auswählen, wird 1 Dateifreigabe mit 2 TB und 4 IOPS/GB für Managementkomponenten bestellt.

### Lizenzen (von IBM bereitgestellt oder eigene) und Gebühren

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4
* (Für vSAN-Cluster) VMware vSAN Advanced oder Enterprise 6.6
* Support- und Servicegebühren (1 Lizenz pro Knoten)

## Technische Spezifikationen für vCenter Server-Erweiterungsknoten

Jeder vCenter Server-Erweiterungsknoten stellt die folgenden Komponenten in Ihrem {{site.data.keyword.cloud_notm}}-Konto mit den entsprechenden anfallenden Gebühren bereit.

### Hardware für Erweiterungsknoten

1 Bare Metal Server mit der unter [Technische Spezifikationen für vCenter Server-Instanzen](vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances) aufgeführten Konfiguration.

### Lizenzen und Gebühren für Erweiterungsknoten

* 1 Lizenz für VMware vSphere Enterprise Plus 6.5u1
* 1 Lizenz für VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4
* 1 Support- und Servicegebühr
* (Für vSAN-Cluster) VMware vSAN Advanced oder Enterprise 6.6

**Wichtig**: Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT**: Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben, außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten
*  Services erneut starten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

### Zugehörige Links

* [vCenter Server-Softwareteileliste](vc_bom.html)
* [vCenter Server-Instanzen planen](vc_planning.html)
* [vCenter Server-Instanzen bestellen](vc_orderinginstance.html)
* [{{site.data.keyword.cloud_notm}} File Storage und Block Storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}

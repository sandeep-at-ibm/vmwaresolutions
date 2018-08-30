---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Übersicht über VMware Federal on IBM Cloud

VMware Federal on {{site.data.keyword.cloud}} stellt die Unterstützung für die Bestellung einer vCenter Server-Basisinstanz bereit und bietet US-Bundesbehörden die Möglichkeit, bereitgestellte vCenter Server-Instanzen zu schützen. Bei Auswahl der Option zum Schützen der bereitgestellten Instanzen werden sensible Informationen, die über die Instanz gespeichert sind, ebenso wie die offene Managementverbindung zum kontinuierlichen Zugriff auf die Instanz für Managementfunktionen wie das Hinzufügen und Entfernen von Hosts und Clustern entfernt. Nachdem Sie die Option zum Schützen ausgewählt haben, werden mit Ausnahme des vollständigen Löschens der Instanz alle Managementfunktionen inaktiviert.

Weitere Informationen zu vCenter Server on {{site.data.keyword.cloud_notm}} und die vCenter Server-Architektur finden Sie unter [Übersicht über vCenter Server](vc_vcenterserveroverview.html).

**Achtung:** VMware Federal on {{site.data.keyword.cloud_notm}} bietet nur eine Untergruppe der vCenter Server-Angebote. Konfigurationen mit mehreren Standorten, vorkonfigurierte Bare Metal Server von {{site.data.keyword.cloud_notm}}, das Verwenden eigener Lizenzen (BYOL) und die Option für die Bestellung zusätzlicher Services werden nicht unterstützt.

## Technische Spezifikationen für VMware Federal on IBM Cloud-Instanzen

Die folgenden Komponenten sind enthalten:

### Bare Metal Server

Sie können zwei oder mehr angepasste {{site.data.keyword.baremetal_short}}-Instanzen mit einer der folgenden Konfigurationen bestellen:

* 2-CPU Intel Broadwell Generation (Intel Xeon E5-2600 v4 Series)
* 2-CPU Intel Skylake Generation (Intel Xeon 4100/5100/6100 Series)

Für die NFS-Speicherkonfiguration liegt die empfohlene Anzahl von {{site.data.keyword.baremetal_short}}-Instanzen standardmäßig bei 3.

**Hinweis:** Wenn Sie vSAN-Speicher auswählen, erfordert die Konfiguration 4 {{site.data.keyword.baremetal_short}}-Instanzen.

### Vernetzung

Die folgenden Netzkomponenten werden bestellt:
*  3 VLANs (virtuelle LANs): 1 öffentliches VLAN und 2 private VLANs
*  1 VXLAN (Virtual eXtensible LAN) mit einem verteilten logischen Router (Distributed Logical Router, DLR) für die potenzielle Ost-West-Kommunikation zwischen lokalen Workloads, die mit Netzen der Schicht 2 (L2) verbunden sind. Das VXLAN wird als Muster für die Routingtopologie bereitgestellt, das Sie ändern, als Ausgangspunkt für Erstellungen verwenden oder entfernen können. Sie können außerdem Sicherheitszonen hinzufügen, indem Sie zusätzliche VXLANs an neue logische Schnittstellen im DLR anhängen.
*  2 VMware NSX Edge Services Gateways:
  * 1 sicheres VMware NSX Edge Services Gateway (ESG) für Management-Services für abgehenden HTTPS-Managementdatenverkehr, das von IBM im Rahmen der Managementnetztypologie bereitgestellt wird. Über dieses ESG kommunizieren virtuelle IBM Management-Maschinen mit bestimmten externen IBM Managementkomponenten, die mit der Automatisierung zusammenhängen. Weitere Informationen finden Sie unter [Netz zur Verwendung des vom Kunden verwalteten ESG konfigurieren](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Wichtig**: Dieses ESG ist für Sie weder zugänglich, noch können Sie es verwenden. Falls Sie es ändern, sind Sie möglicherweise nicht in der Lage, die vCenter Server-Instanz über die {{site.data.keyword.vmwaresolutions_short}}-Konsole zu verwalten. Beachten Sie außerdem, dass die Verwendung einer Firewall oder die Inaktivierung der ESG-Kommunikation mit den externen IBM Managementkomponenten dazu führt, dass {{site.data.keyword.vmwaresolutions_short}} unbrauchbar wird.
  * 1 sicheres vom Kunden verwaltetes VMware NSX Edge Services Gateway für eingehenden und abgehenden HTTPS-Workloaddatenverkehr, das von IBM als Vorlage bereitgestellt wird und von Ihnen geändert werden kann, um den VPN-Zugriff oder den öffentlichen Zugriff zu ermöglichen. Weitere Informationen finden Sie im Abschnitt [Stellt das vom Kunden verwaltete NSX Edge ein Sicherheitsrisiko dar?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)

  **Hinweis**: Das VMware NSX Edge Services Gateway (ESG) für abgehenden HTTPS-Managementdatenverkehr wird im Rahmen der Aktion zum Schutz der bereitgestellten VMware Federal-Instanz entfernt. Weitere Informationen finden Sie unter [VMware Federal-Instanzen schützen](vc_fed_securinginstance.html).

### Virtual Server-Instanzen

Die folgenden VSIs (Virtual Server-Instanzen) werden bestellt:
* 1 VSI für IBM CloudBuilder, der nach vollständiger Bereitstellung der Instanz beendet wird.
* (Für Instanzen mit V2.3 und höher) Sie haben die Möglichkeit, die Bereitstellung einer einzigen Virtual Server-Instanz (VSI) von Microsoft Windows für Microsoft Active Directory (AD) oder aber von zwei virtuellen Microsoft Windows-Maschinen für die Hochverfügbarkeit im Management-Cluster auszuwählen, um die Sicherheit und Leistungsfähigkeit zu erhöhen.
* (Für Instanzen mit V2.2) Eine VSI von Microsoft Windows Server für Microsoft Active Directory (AD), die als DNS für die Instanz dient, auf der die Hosts und virtuellen Maschinen registriert sind, wird bereitgestellt und kann zur Suche verwendet werden.

### Speicher

Während der Erstbereitstellung können Sie zwischen den Speicheroptionen "vSAN" und "NFS" wählen.

Die Option "vSAN" bietet angepasste Konfigurationen mit unterschiedlichen Optionen für Plattentyp und -menge:
* Plattenmenge: 2, 4, 6 oder 8.
* Speicherplatte: 960 GB SSD SED, 1,9 TB SSD SED oder 3,8 TB SSD SED.

  Zusätzlich werden 2 Cacheplatten mit 960 GB pro Host bestellt.

Die Option "NFS" bietet angepassten gemeinsam genutzten Speicher auf Dateiebene für Workloads mit verschiedenen Optionen für Größe und Leistung:
* Größe: 1, 2, 4, 8 oder 12 TB.
* Leistung: 2, 4 oder 10 IOPS/GB (E/A-Operationen pro Sekunde und GB).
* Die Dateifreigaben können Sie einzeln konfigurieren.

Wenn Sie die Option "NFS" auswählen, wird 1 Dateifreigabe mit 2 TB und 4 IOPS/GB für Managementkomponenten bestellt.

### Von IBM bereitgestellte Lizenzen und Gebühren

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4
* (Für vSAN-Cluster) VMware vSAN Advanced oder Enterprise 6.6

## Technische Spezifikationen für VMware Federal on IBM Cloud-Erweiterungsknoten

Jeder vCenter Server-Erweiterungsknoten stellt die folgenden Komponenten in Ihrem {{site.data.keyword.cloud_notm}}-Konto mit den entsprechenden anfallenden Gebühren bereit.

### Hardware für Erweiterungsknoten

1 Bare Metal Server mit der unter [Technische Spezifikationen für VMware Federal on {{site.data.keyword.cloud_notm}}-Instanzen](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances) aufgeführten Konfiguration.

### Lizenzen und Gebühren für Erweiterungsknoten

* 1 Lizenz für VMware vSphere Enterprise Plus 6.5u1
* 1 Lizenz für VMware NSX Service Providers Edition (Base, Advanced oder Enterprise) 6.4
* (Für vSAN-Cluster) VMware vSAN Advanced oder Enterprise 6.6

**Wichtig**: Sie dürfen die {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto erstellt werden, nur über die {{site.data.keyword.vmwaresolutions_short}}-Konsole und nicht im {{site.data.keyword.slportal}} oder über ein anderes Verfahren außerhalb der Konsole verwalten. Wenn Sie diese Komponenten außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole ändern, werden die Änderungen nicht mit der Konsole synchronisiert.

**VORSICHT**: Wenn Sie {{site.data.keyword.vmwaresolutions_short}}-Komponenten, die in Ihrem {{site.data.keyword.cloud_notm}}-Konto installiert wurden, als Sie die Instanz bestellt haben, außerhalb der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwalten, kann dies zur Instabilität Ihrer Umgebung führen. Zu diesen Managementaktivitäten gehören:
*  Komponenten hinzufügen, ändern, zurückgeben oder entfernen
*  Instanzkapazität durch das Hinzufügen oder Entfernen von ESXi-Servern erweitern oder verringern
*  Komponenten ausschalten

   Ausgenommen von diesen Aktivitäten ist unter anderem das Management der Dateifreigaben für gemeinsam genutzten Speicher im {{site.data.keyword.slportal}}. Hierzu gehört das Bestellen, Löschen (mit möglicher Auswirkung auf angehängte Datenspeicher), Berechtigen und Anhängen von Dateifreigaben für gemeinsam genutzten Speicher.

### Zugehörige Links

* [vCenter Server-Softwareteileliste](vc_bom.html)
* [Voraussetzungen und Planung für VMware Federal-Instanzen](vc_fed_planning.html)
* [VMware Federal-Instanzen bestellen](vc_fed_orderinginstance.html)
* [VMware Federal-Instanzen schützen](vc_fed_securinginstance.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [{{site.data.keyword.cloud_notm}} File Storage und Block Storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}

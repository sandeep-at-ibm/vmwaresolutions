---

copyright:

  years:  2016, 2018

lastupdated: "2017-03-08"

---

# Releaseinformationen für V1.4

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Komponentenaktualisierungen für Cloud Foundation-Instanzen

Die folgenden Komponenten sind neu verfügbar oder wurden aktualisiert:

* VC und PSC (vCenter und Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* Für den Service von Microsoft Active Directory (AD) und den DNS-Service, die in diesem Release zur Unterstützung von Konfigurationen mit mehreren Standorten erforderlich sind, wird eine neue Virtual Server-Instanz (VSI) von Windows bestellt. Diese VSI hat die folgenden Spezifikationen: Windows 2012 R2 (8 GB RAM / 2 CPU-Kerne / 100 GB Plattenspeicher / Duale 1-Gbps-Uplinks für private Netze).

Weitere Informationen enthält der Abschnitt [Übersicht über Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

## Komponentenaktualisierungen für vCenter Server-Instanzen

Die folgenden Komponenten sind neu verfügbar oder wurden aktualisiert:

### VMware NSX for vSphere 6.2.4

VMware NSX for vSphere 6.2.4 wird nun standardmäßig für alle vCenter Server-Instanzen installiert (zuvor war dies nur bei Cloud Foundation-Instanzen der Fall).

Im Rahmen der NSX-Installation wird der NSX-Manager installiert und für alle neuen Instanzen lizenziert, die bereitgestellt werden. Darüber hinaus wird NSX Edge für das Instanzmanagement erstellt. Bei Bedarf können Sie jedoch eigene NSX Edge-Komponenten erstellen. Weitere Informationen zu NSX Edge finden Sie im Abschnitt _VMware NSX Edge_ auf dieser Seite.

**Hinweis**: Der NSX-Controller wird (anders als bei Cloud Foundation-Instanzen) nicht für vCenter Server-Instanzen installiert. Falls Sie für Ihre vCenter Server-Instanzen VXLAN oder verteilte logische Router verwenden, müssen Sie den NSX-Controller selbst installieren.

Weitere Informationen zu den in VMware NSX for vSphere 6.2.4 eingeführten Erweiterungen, den Voraussetzungen und den bekannten Problemen finden Sie auf der Seite [NSX for vSphere 6.2.4 release notes](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}.

### VMware NSX Edge

NSX Edge ist jetzt im Lieferumfang der neuen vCenter Server-Instanzen enthalten, die Sie bestellen. NSX Edge stellt zur Isolierung eines virtualisierten Netzes Netzperipherieschutz und Gateway-Services bereit.

Während der Instanzbereitstellung wird durch IBM ein VMware NSX Edge Services Gateway (ESG) für das Management bereitgestellt. Dieses ESG wird von den IBM Management-VMs für die Kommunikation mit bestimmten externen IBM Managementkomponenten verwendet, die mit der Automatisierung zusammenhängen. Dieses ESG wird mit zwei Schnittstellen bereitgestellt. Eine Schnittstelle ist mit dem privaten VLAN der {{site.data.keyword.cloud_notm}} verbunden und die andere Schnittstelle ist mit dem öffentlichen VLAN der {{site.data.keyword.cloud_notm}} verbunden.

Zur Gewährleistung der Sicherheit gelten Firewallregeln, die nur abgehenden HTTPS-Datenverkehr zulassen, der durch die Management-VMs eingeleitet
wird. Dieses ESG wird in einer Konfiguration des Typs "L (Groß)" bereitgestellt; die Konfiguration kann nur durch den IBM Support geändert werden. Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Technische Spezifikationen für vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [Stellt das NSX Edge für Management-Services ein Sicherheitsrisiko dar?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### NSX-Lizenz

Pro Knoten wird eine Lizenz für VMware NSX Base for Service Providers Edition bestellt.

### Neuer Teilnetzadressenblock

Pro Knoten wird ein Teilnetzblock von 16 öffentlichen portierbaren Adressen bestellt.

## Updates des Servicegebührenmodells

Das Servicegebührenmodell wurde vereinfacht:

* Bei Cloud Foundation-Instanzen werden die Gebühren für den _VMware Cloud Foundation-Instanzservice_, den _VMware Cloud Foundation-Speicherservice_ und
   _VMware Solutions Hypervisor_ nicht mehr erhoben.
* Bei vCenter Server-Instanzen werden die Gebühren für die _VMware vCenter Server-Instanz_ und _VMware Solutions Hypervisor_ nicht mehr erhoben.
* Bei beiden Instanztypen wird künftig eine neue Gebühr für _Support und Services_ berechnet, bei der es sich um eine für jeden Knoten anfallende monatliche Gebühr handelt.

## Updates der Instanznetztopologie

Das aktuelle Release beinhaltet die folgenden Topologieerweiterungen für Ihre Instanzen:

* Bei Cloud Foundation-Instanzen und vCenter Server-Instanzen: Optimierte Netzkonfiguration, bei der nur die primären öffentlichen und privaten IP-Adressen, die durch SoftLayer® zugewiesen werden, den ESXi-Servern zugeordnet werden. Portierbare private Adressen werden für den Managementdatenverkehr nicht mehr bereitgestellt.
* Nur bei Cloud Foundation-Instanzen: Server für Windows AD SSO (Active Directory Single Sign-On) und DNS (Domain Name System)

**Hinweis**: Aufgrund dieser Änderungen können Sie Ihre vorhandenen Instanzen aus Releases vor V1.4 im aktuellen Release nicht mehr nutzen. Um die Konfiguration Ihrer vorhandenen Instanzen wiederzuverwenden, müssen Sie für die Instanzen ein Upgrade auf die neue Version durchführen. Weitere Informationen finden Sie unter [Upgrade für Instanzen aus Releases vor V1.4 durchführen](movinginstances.html).

## Unterstützung von Konfigurationen mit mehreren Standorten bei Cloud Foundation-Instanzen

Sie können nun entweder wie in früheren Releases eine einzige Cloud Foundation-Instanz bereitstellen oder zusätzlich auch sekundäre Instanzen bereitstellen, die an eine primäre Instanz angeschlossen sind. Das Konfigurationsmodell für mehrere Standorte verwendet eine Hub-Peripherie-Topologie mit einem primären Standort und maximal sieben sekundären Standorten.

Weitere Informationen finden Sie unter [Konfiguration mit mehreren Standorten für Cloud Foundation-Instanzen](../sddc/sd_multisite.html).

## Funktionale Erweiterungen bei der Bereitstellung der Disaster-Recovery mit Zerto

* Bei Cloud Foundation-Instanzen erfolgt die Bereitstellung der Disaster-Recovery mit Zerto automatisiert und wird nicht über ein Support-Ticket abgewickelt. Alle Kosten für Zerto-Komponenten (z. B. privates portierbares Teilnetz und Windows-VSI) und die Zerto-Lizenz werden bei den geschätzten Kosten aufgeführt und können von Ihnen überprüft werden, bevor Sie die Bestellung aufgeben.
* Bei vCenter Server-Instanzen erfolgt die Bereitstellung der Disaster-Recovery mit Zerto wie in den Vorgängerreleases durch ein Support-Ticket. NSX Edge und das öffentliche portierbare Teilnetz werden jedoch nicht mehr benötigt, da diese Komponenten nun Bestandteil der Basisbereitstellung sind. Die Gebühren für ein privates portierbares Teilnetz, eine Windows-VSI (Virtuelle Service-Instanz) und die Zerto-Lizenz fallen weiterhin an.

Weitere Informationen finden Sie unter [Disaster-Recovery mit Zerto](../services/addingzertodr.html).

## Instanzbestellungsprozess

Der Instanzbestellprozess wurde erheblich vereinfacht:

* Bei Cloud Foundation- und vCenter Server-Instanzen wird die Seite mit den SoftLayer-Berechtigungsnachweisen nicht mehr während des Bestellprozesses angezeigt. Die auf der Seite "Einstellungen" definierten SoftLayer-Berechtigungsnachweise werden standardmäßig verwendet. Sie werden nur dann zur Aktualisierung dieser Berechtigungsnachweise aufgefordert, wenn sie die Anforderungen nicht erfüllen.
* Darüber hinaus ist bei vCenter Server-Instanzen jetzt nur die Option **L (Groß)** für den **Hardwaretyp** und die Einstellung **10 Gb/s Dual** für die **Uplink-Port-Geschwindigkeit** verfügbar, wodurch Sie bei der Bestellung weniger Einstellungen angeben müssen.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)

## Instanzmanagement

Der Instanzmanagementprozess wurde folgendermaßen erweitert und verbessert:

* Bei Cloud Foundation-Instanzen können Sie den Benutzernamen und die Kennwörter für die einzelnen Instanzkomponenten auf der Seite mit den Instanzdetails einsehen. Entsprechende Informationen finden Sie im Abschnitt [Cloud Foundation-Instanzen anzeigen](../sddc/sd_viewinginstances.html).
* Bei vCenter Server-Instanzen können Sie künftig Software-Updates und Patches für IBM Komponenten direkt von der Konsole aus installieren. Weitere Informationen enthält der Abschnitt [Updates und Patches auf vCenter Server-Instanzen anwenden](../vcenter/vc_applyingupdates.html).

## Konsolenbenachrichtigungen

Die Konsolenbenachrichtigungen können jetzt auf der Seite **Einstellungen** von Ihnen konfiguriert werden. Standardmäßig ist die Einstellung aktiviert. Dies bedeutet, dass Sie für alle Ereignisse eine Benachrichtigung in der Konsole empfangen. Auf der Seite **Einstellungen** können Sie Benachrichtigungen für die Konsole auch inaktivieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Benutzerkonten und -einstellungen](useraccount.html)
* [Benachrichtigungen](notifications.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# Releaseinformationen für V1.3

Dieses Release stellt neue Funktionen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Gemeinsam genutzter Speicher auf Dateiebene für vCenter Server-Instanzen

Sie können nun gemeinsam genutzten NAS-Speicher (Network Attached Storage) zu vCenter Server-Instanzen hinzufügen. Die Einführung dieser Funktion versetzt Sie in die Lage, Produktionsworkloads in vCenter Server auszuführen und einen Datenverlust durch Knotenfehler zu verhindern. NFS File Storage (NFS = Network File System) wird während des Bestellablaufs für vCenter Server-Instanzen als Option angeboten. Weitere Informationen finden Sie unter [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html).

## Disaster-Recovery mit Zerto entfernen

Der Service für die Disaster-Recovery mit Zerto kann nun entfernt werden, wenn er nicht mehr benötigt wird. Hierbei ist es ohne Belang, ob Sie diesen Service zusammen mit der Instanz bestellt oder zu einer vorhandenen Instanz hinzugefügt haben. Nachdem Sie das Entfernen des Service über die Konsole angefordert haben, werden Sie vom IBM Support bei der Ausführung des Löschprozesses angeleitet.

Weitere Informationen enthalten die folgenden Abschnitte:

* [Disaster-Recovery mit Zerto entfernen](../services/removingzertodr.html)
* [Cloud Foundation-Instanzen anzeigen](../sddc/sd_viewinginstances.html)
* [vCenter Server-Instanzen anzeigen](../vcenter/vc_viewinginstances.html)

## VMware NSX Edge für Cloud Foundation-Instanzen

NSX Edge ist jetzt im Lieferumfang der neuen Cloud Foundation-Instanzen enthalten, die Sie bestellen. NSX Edge stellt zur Isolierung eines virtualisierten Netzes Netzperipherieschutz und Gateway-Services bereit.

Während der Instanzbereitstellung wird durch IBM ein NSX Edge Services Gateway (ESG) für das Management bereitgestellt. Dieses ESG wird von den IBM Management-VMs für die Kommunikation mit bestimmten externen IBM Managementkomponenten verwendet, die mit der Automatisierung zusammenhängen. Dieses ESG wird mit zwei Schnittstellen bereitgestellt. Eine Schnittstelle ist mit dem privaten VLAN der {{site.data.keyword.cloud_notm}} verbunden und die andere Schnittstelle ist mit dem öffentlichen VLAN der {{site.data.keyword.cloud_notm}} verbunden.

Zur Gewährleistung der Sicherheit gelten Firewallregeln, die nur abgehenden HTTPS-Datenverkehr zulassen, der durch die Management-VMs eingeleitet
wird. Dieses ESG wird in einer Konfiguration des Typs "L (Groß)" bereitgestellt; die Konfiguration kann nur durch den IBM Support geändert werden.

Weitere Informationen enthalten die folgenden Abschnitte:

* [Technische Spezifikationen für Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [Stellt das NSX Edge für Management-Services ein Sicherheitsrisiko dar?](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## Instanzbestellungsprozess

Der Bestellprozess für Cloud Foundation-Instanzen und vCenter Server-Instanzen wurde verbessert:

* Auf der Seite "Zusammenfassung" werden alle geltenden Vertragsbedingungen für alle bestellten Komponenten und Services angezeigt, damit Sie diese Bedingungen bequem prüfen und akzeptieren können, bevor Sie die Bestellung aufgeben.
* Die Zusammenfassung der Bestellung für Ihre Instanz können Sie speichern und drucken, bevor Sie die Bestellung aufgeben. Durch diese neue Funktion können Sie die Einstellungen und Kosten der Instanz prüfen, die bestellten Komponenten bei Bedarf ändern, eine Genehmigung anfordern und anschließend Ihre Bestellung fortsetzen.

Weitere Informationen enthalten die folgenden Abschnitte:

* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)

## Instanzmanagement

Der Instanzmanagementprozess wurde folgendermaßen erweitert und verbessert:

* Bei Cloud Foundation- und vCenter Server-Instanzen können Sie die geschätzten Kosten für Ihre ESXi-Server anzeigen und prüfen, bevor Sie sie definitiv zur Instanz hinzufügen. Nachdem Sie angegeben haben, wie viele Server hinzugefügt werden sollen, werden die geschätzten Kosten pro Server und pro Monat in der Konsole angezeigt. Weitere Informationen finden Sie unter [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](../sddc/sd_addingremovingservers.html) und [Kapazität für vCenter Server-Instanzen erweitern und verringern](../vcenter/vc_addingremovingservers.html).
* Bei Cloud Foundation- und vCenter Server-Instanzen wird oben auf der Seite "Zusammenfassung" die Gesamtzahl der Instanzen angezeigt. Sie können außerdem eine Instanz durch einen einzigen Klick ausgehend von der Seite mit der Instanzzusammenfassung bestellen. Darüber hinaus können Sie auf der Seite "Zusammenfassung" während der Bereitstellung detaillierte Informationen zum Bestellstatus einsehen. Wenn Sie den Mauszeiger auf den angezeigten Status bewegen, werden bei Verfügbarkeit weitere Details über den aktuellen Schritt oder den Fehler angezeigt.
* Bei Cloud Foundation-Instanzen wird auf der Seite mit den Instanzdetails der Bereitstellungsverlauf der Instanz zusammen mit Informationen zu den einzelnen Schritten für den Bereitstellungsstatus angezeigt. Entsprechende Informationen finden Sie im Abschnitt [Cloud Foundation-Instanzen anzeigen](../sddc/sd_viewinginstances.html).
* Bei Cloud Foundation-Instanzen wurde der Bedienungskomfort des Prozesses für Updates und Patches dadurch verbessert, dass auf der Seite **Update und Patch** mehr Details über das Update angezeigt werden. Beispiele hierfür sind die für ein Patch benötigte Ausfallzeit, der Zeitpunkt für ein geplantes Update sowie ein optischer Hinweis, falls vor dem aktuellen Patch ein erforderliches Patch angewendet werden muss. Weitere Informationen finden Sie unter [Updates und Patches auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html).

## E-Mail-Benachrichtigungen

Sie erhalten jetzt eine Benachrichtigung per E-Mail, wenn eine neue Bestellung für die Instanzbereitstellung aufgegeben bzw. ein Service in Ihrer Instanz hinzugefügt, bereitgestellt oder entfernt wurde. Die Benachrichtigungseinstellungen sind standardmäßig aktiviert. Auf der Seite **Einstellungen** können Sie Ihren Präferenzen gemäß festlegen, welche Benachrichtigungen Sie erhalten wollen. Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen](useraccount.html).

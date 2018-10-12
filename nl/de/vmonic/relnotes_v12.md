---

copyright:

  years:  2016, 2018

lastupdated: "2016-12-12"

---

# Releaseinformationen für V1.2

Dieses Release stellt neue Funktionen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Komponentenaktualisierungen

Die neue Version von VMware ESXi ist vSphere 6.0 u2 p03, aktualisiert ausgehend von ESXi 6.0 u2 in der vorherigen Version.

## Kontenzuordnung für IBMid und Bluemix

{{site.data.keyword.vmwaresolutions_full}} wird als Infrastrukturlösung im IBM Bluemix®-Katalog bereitgestellt. Sie müssen das **IBMid**-Konto einem Bluemix-Konto zuordnen, um Ihr **IBMid**-Konto zur Anmeldung bei der {{site.data.keyword.vmwaresolutions_short}}-Konsole verwenden zu können.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Einführung](../index.html)
* [Fehlerbehebung beim Zugriff auf Bluemix](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html){:new_window}

## Disaster-Recovery mit Zerto

Sowohl VMware Cloud Foundation-Instanzen als auch VMware vCenter Server-Instanzen können mit der integrierten Disaster-Recovery mit Zerto bestellt werden. Sie können die Disaster-Recovery mit Zerto auch zu Ihren vorhandenen Cloud Foundation-Instanzen und vCenter Server-Instanzen auf der Seite mit den Instanzdetails hinzufügen.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [Cloud Foundation-Instanzen anzeigen](../sddc/sd_viewinginstances.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)
* [vCenter Server-Instanzen anzeigen](../vcenter/vc_viewinginstances.html)
* [Disaster-Recovery mit Zerto](../services/addingzertodr.html)

## Preisinformationen

Sie können die geschätzten Kosten für Ihre bestellte Instanz künftig einsehen und prüfen, bevor Sie die Bestellung aufgeben. Nachdem Sie Ihre Komponenten bei der Bestellung ausgewählt haben, werden die Gesamtkosten und die detaillierte Preisstruktur für alle Komponenten auf der Seite **Zusammenfassung** angezeigt.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)

## Erweiterungen beim Instanzbestellablauf

Der Instanzbestellablauf wurde durch die folgenden funktionalen Erweiterungen erheblich verbessert:
* Für Cloud Foundation-Instanzen und vCenter Server-Instanzen werden neue Validierungsprüfungen durchgeführt, die gewährleisten, dass das von Ihnen verwendete SoftLayer®-Benutzerkonto über die erforderlichen Benutzerberechtigungen verfügt, dass die VLAN Spanning-Funktion aktiviert ist und dass der richtige API-Schlüssel angegeben wurde. Falls eine dieser Voraussetzungen nicht erfüllt ist, erhalten Sie direkt in der Benutzerschnittstelle Anweisungen für die Behebung des Problems.
*  Für vCenter Server wurde die Reihenfolge optimiert, in der die Instanzkomponenten ausgewählt werden, damit nur diejenigen Rechenzentren angezeigt werden, in denen die von Ihnen benötigten Hardwareeinrichtungen und ESXi-Server verfügbar sind. Diese Änderung verringert die Möglichkeit späterer Fehler.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Cloud Foundation-Instanzen bestellen](../sddc/sd_orderinginstance.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)

## Zusätzliche E-Mail-Benachrichtigungen

Sie erhalten künftig eine Benachrichtigung per E-Mail, wenn neue ESXi-Server zu Ihren Instanzen hinzugefügt werden und wenn vorhandene ESXi-Server entfernt werden. Außerdem werden Sie per E-Mail benachrichtigt, wenn eine Instanz gelöscht wird. Die Benachrichtigungseinstellungen sind standardmäßig aktiviert. Auf der Seite **Einstellungen** können Sie Ihren Präferenzen gemäß festlegen, welche Benachrichtigungen Sie erhalten wollen.

Weitere Informationen finden Sie unter [Benutzerkonten und Einstellungen](useraccount.html).

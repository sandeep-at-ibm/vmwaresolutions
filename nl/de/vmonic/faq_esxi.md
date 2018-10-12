---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Häufig gestellte Fragen zu ESXi-Servern

Hier finden Sie Antworten auf häufig gestellte Fragen zu den ESXi-Servern, die in der {{site.data.keyword.vmwaresolutions_full}}-Konsole verwaltet werden.

## Wie viele ESXi-Server kann ich zu meiner Instanz hinzufügen?

* Bei vCenter Server-Instanzen können Sie den Standardcluster auf bis zu 51 ESXi-Server erweitern. Jeder Cluster, bei dem es sich nicht um den Standardcluster handelt, kann auf bis zu 59 ESXi-Server erweitert werden. Da Sie bis zu 10 Cluster zu einer Instanz hinzufügen können, kann jede bereitgestellte Instanz in allen Clustern maximal 51 + 9 x 59 = 582 ESXi-Server umfassen.
* Bei Cloud Foundation-Instanzen enthält die Standardkonfiguration vier ESXi-Server. Sie können maximal 28 Server hinzufügen (also insgesamt 32 Server verwenden). Bei Cloud Foundation-Instanzen in einer Konfiguration mit mehreren Standorten können insgesamt bis zu 128 ESXi-Server in allen Instanzen verwendet werden.

  **Hinweis**: Falls Ihre Cloud Foundation-Konfiguration eine Bereitstellung mit mehreren Standorten mit mehr als 128 ESXi-Servern erforderlich macht, bitten Sie den [IBM Support](trbl_support.html) um Unterstützung.

## Wie viele ESXi-Server kann ich zu einem Cluster hinzufügen?

Bei V2.2 und höhere Releases können Sie maximal 51 ESXi-Server zu einem ersten Cluster und maximal 59 ESXi-Server zu den hinzugefügten Clustern hinzufügen.

Bei Instanzen, die in V2.1 oder früheren Releases bereitgestellt wurden, müssen Sie die erforderliche vSAN-Unterstützung aktivieren, um die Clustergröße auf über 32 zu erhöhen. Führen Sie zum Aktivieren der erforderlichen vSAN-Unterstützung die folgenden Schritte aus:

1. Führen Sie auf jedem bereitgestellten ESXi-Server die folgenden Befehle aus:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Starten Sie jeden ESXi-Server erneut. Weitere Informationen finden Sie unter [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Möglicherweise ist es nicht erforderlich, die Größe für vCenter Server zu erhöhen, damit die zusätzlichen virtuellen Maschinen und ESXi-Server aufgenommen werden können.
4. Initiieren Sie ein IBM Support-Ticket und geben Sie dabei an, dass Sie die vSAN-Änderungen manuell wie in Schritt 1 bis 3 vorgesehen vorgenommen haben. Fragen Sie im Ticket an, ob Ihre Upgradeinstanz für eine über 32 hinausgehende Anzahl von ESXi-Servern eingerichtet ist.

## Kann ich die Namen und IP-Adressen von ESXi-Servern ändern?

Die Namen und IP-Adressen von ESXi-Servern können nicht geändert werden, weil sie für die Windows-DNS-Auflösung registriert werden. Änderungen könnten dazu führen, dass während der Bereitstellung oder bei vCenter Server-Funktionen Fehler auftreten.

**Hinweis:** Versuchen Sie nicht, die Namen von ESXi-Servern mithilfe der Funktion **Einheit umbenennen** in der {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle zu ändern. Diese Funktion ändert zwar tatsächlich den vollständig qualifizierten Domänennamen des ESXi-Servers, aber die konfigurierten vCenter- und Windows-VSI-Hostregistrierungen werden hierdurch falsch und können Fehler verursachen.

## Kann ich den Rootzugriff auf meinen ESXi-Servern inaktivieren?

Es wird empfohlen, den Rootzugriff auf ESXi-Servern aktiviert zu lassen, da es andernfalls zu Störungen bei den {{site.data.keyword.vmwaresolutions_short}}-Funktionen kommen kann.

Sollte es erforderlich sein, können Sie den Rootzugriff inaktivieren, nachdem die ESXi-Server den Status **Bereit** in der {{site.data.keyword.vmwaresolutions_short}}-Konsole erreicht haben.

Für nachfolgende Automatisierungsoperationen, beispielsweise beim Hinzufügen und Entfernen von gemeinsam genutzten Dateiressourcen oder beim Installieren zusätzlicher Services wie Zerto on {{site.data.keyword.cloud_notm}}, müssen Sie den Rootzugriff erneut aktivieren.

## Kann ich statische Routen auf meinen ESXi-Servern hinzufügen, um Speicher von anderen Speicherorten anzuhängen?

Statische Routen können für Speicher hinzugefügt werden, die Operationen müssen jedoch mit äußerster Sorgfalt ausgeführt werden. Andernfalls könnten die vorhandenen, gemeinsam genutzten Ressourcen abgehängt werden.

**Hinweis**: Das Hinzufügen statischer Routen für vMotion wird nicht unterstützt. Änderungen an der vMotion-Teilnetzkonfiguration könnten zu Störungen bei den Funktionen von {{site.data.keyword.vmwaresolutions_short}} führen.

### Zugehörige Links

* [Kapazität für vCenter Server-Instanzen erweitern und verringern](../vcenter/vc_addingremovingservers.html)
* [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](../sddc/sd_addingremovingservers.html)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](../vcenter/vc_addingviewingclusters.html)
* [Cluster für Cloud Foundation-Instanzen hinzufügen, anzeigen und löschen](../sddc/sd_addingviewingclusters.html)
* [Kontaktaufnahme mit dem IBM Support](trbl_support.html)

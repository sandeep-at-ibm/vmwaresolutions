---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Häufig gestellte Fragen zu ESXi-Servern
{: #faq_esxi}

Hier finden Sie Antworten auf häufig gestellte Fragen zu den ESXi-Servern, die in der {{site.data.keyword.vmwaresolutions_full}}-Konsole verwaltet werden.

## Wie viele ESXi-Server kann ich zu meiner Instanz hinzufügen?
{: #faq_esxi-instance}
{: faq}

* Bei vCenter Server-Instanzen können Sie den Standardcluster auf bis zu 51 ESXi-Server erweitern. Jeder Cluster, bei dem es sich nicht um den Standardcluster handelt, kann auf bis zu 59 ESXi-Server erweitert werden. Da Sie bis zu 10 Cluster zu einer Instanz hinzufügen können, kann jede bereitgestellte Instanz in allen Clustern maximal 51 + 9 x 59 = 582 ESXi-Server umfassen.
* Bei Cloud Foundation-Instanzen enthält die Standardkonfiguration vier ESXi-Server. Sie können maximal 28 Server hinzufügen (also insgesamt 32 Server verwenden). Bei Cloud Foundation-Instanzen in einer Konfiguration mit mehreren Standorten können insgesamt bis zu 128 ESXi-Server in allen Instanzen verwendet werden.

  Falls Ihre Cloud Foundation-Konfiguration eine Bereitstellung mit mehreren Standorten mit mehr als 128 ESXi-Servern erforderlich macht, bitten Sie den [IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) um Unterstützung.
  {:note}

## Wie viele ESXi-Server kann ich zu einem Cluster hinzufügen?
{: #faq_esxi-cluster}
{: faq}

Bei Instanzen, die in Version 2.2 und höheren Releases bereitgestellt wurden, können Sie maximal 51 ESXi-Server zu einem ersten Cluster und maximal 59 ESXi-Server zu den hinzugefügten Clustern hinzufügen.

Bei Instanzen, die in V2.1 oder früheren Releases bereitgestellt wurden, müssen Sie die erforderliche vSAN-Unterstützung aktivieren, um die Clustergröße auf über 32 zu erhöhen. Führen Sie zum Aktivieren der erforderlichen vSAN-Unterstützung die folgenden Schritte aus:

1. Führen Sie auf jedem bereitgestellten ESXi-Server die folgenden Befehle aus:

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. Starten Sie jeden ESXi-Server erneut. Weitere Informationen finden Sie unter [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081).
3. Möglicherweise ist es nicht erforderlich, die Größe für vCenter Server zu erhöhen, damit die zusätzlichen virtuellen Maschinen und ESXi-Server aufgenommen werden können.
4. Initiieren Sie ein IBM Support-Ticket und geben Sie dabei an, dass Sie die vSAN-Änderungen manuell wie in Schritt 1 bis 3 vorgesehen vorgenommen haben. Fragen Sie im Ticket an, ob Ihre Upgradeinstanz für eine über 32 hinausgehende Anzahl von ESXi-Servern eingerichtet ist.

## Kann ich die Namen und IP-Adressen von ESXi-Servern ändern?
{: #faq_esxi-change-name-ip}
{: faq}

Die Namen und IP-Adressen von ESXi-Servern können nicht geändert werden, weil sie für die Windows-DNS-Auflösung registriert werden. Änderungen könnten dazu führen, dass während der Bereitstellung oder bei vCenter Server-Funktionen Fehler auftreten.

Versuchen Sie nicht, die Namen von ESXi-Servern mithilfe der Funktion **Einheit umbenennen** in der {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle zu ändern. Diese Funktion ändert zwar tatsächlich den vollständig qualifizierten Domänennamen des ESXi-Servers, aber die konfigurierten vCenter Server- und Windows-VSI-Hostregistrierungen werden hierdurch falsch und können Fehler verursachen.
{:note}

## Kann ich den Rootzugriff auf meinen ESXi-Servern inaktivieren?
{: #faq_esxi-disable-root}
{: faq}

Es wird empfohlen, den Rootzugriff auf ESXi-Servern aktiviert zu lassen, da es andernfalls zu Störungen bei den {{site.data.keyword.vmwaresolutions_short}}-Funktionen kommen kann.

Sollte es erforderlich sein, können Sie den Rootzugriff inaktivieren, nachdem die ESXi-Server den Status **Bereit** in der {{site.data.keyword.vmwaresolutions_short}}-Konsole erreicht haben.

Für nachfolgende Automatisierungsoperationen, beispielsweise beim Hinzufügen und Entfernen von gemeinsam genutzten Dateiressourcen oder beim Installieren zusätzlicher Services wie Zerto on {{site.data.keyword.cloud_notm}}, müssen Sie den Rootzugriff erneut aktivieren.

## Kann ich statische Routen auf meinen ESXi-Servern hinzufügen, um Speicher von anderen Speicherorten anzuhängen?
{: #faq_esxi-static-routes}
{: faq}

Sie können statische Routen für den Speicher hinzufügen, müssen aber dabei mit äußerster Sorgfalt vorgehen. Andernfalls könnten die vorhandenen, gemeinsam genutzten Ressourcen abgehängt werden.

Das Hinzufügen statischer Routen für vMotion wird nicht unterstützt. Änderungen an der vMotion-Teilnetzkonfiguration könnten zu Störungen bei den Funktionen von {{site.data.keyword.vmwaresolutions_short}} führen.
{:note}

## Zugehörige Links
{: #faq_esxi-related}

* [Kapazität für vCenter Server-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Cluster für vCenter Server-Instanzen hinzufügen, anzeigen und löschen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

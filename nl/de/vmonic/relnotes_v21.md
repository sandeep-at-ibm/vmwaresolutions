---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-16"

---

# Releaseinformationen für V2.1

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Korrektur für Spectre und Meltdown

{{site.data.keyword.vmwaresolutions_short}} hat als Reaktion auf Sicherheitslücken, die unter den Begriffen "Spectre" und "Meltdown" bekannt sind, Patches aus VMware freigegeben (CVE-2017-5753, CVE-2017-5715 und CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Weitere Informationen enthält der Abschnitt [Gegenmaßnahmen für Sicherheitslücken "Spectre" und "Meltdown"](../vmonic/trbl_fix_spectre.html).

## VMware HCX on IBM Cloud

Der Service "HCX on {{site.data.keyword.cloud_notm}}" ist nun für VMware Cloud Foundation-Instanzen und VMware vCenter Server-Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.1 oder höher bereitgestellt sind oder für die ein Upgrade auf eine entsprechende Version durchgeführt wurde. Dieser Service kann die Netze Ihrer lokalen Rechenzentren nahtlos in die {{site.data.keyword.cloud_notm}} erweitern. Dies ermöglicht die bidirektionale Migration von virtuellen Maschinen (VMs) zwischen Ihren lokalen Rechenzentren und {{site.data.keyword.cloud_notm}}, ohne dass hierzu eine Änderung erforderlich ist. Durch die Einrichtung einer Layer-2-Brücke nutzt HCX die WAN-Optimierung, -Deduplizierung, -Komprimierung und -Verschlüsselung, um Daten schneller und sicherer über eine direkte Verbindung oder einen VPN-Tunnel zu migrieren. Die Massenmigration von VMs ist mit VMware vSphere ab Version 5.1 abwärtskompatibel. Falls Sie vor Ort vSphere 6.0 oder höher verwenden, können Sie aktive (eingeschaltete) VMs von einem lokalen Standort mit vMotion in ein IBM Cloud-Rechenzentrum versetzen. Bei Verwendung von HCX ist es nicht erforderlich, dass VMware NSX in Ihrem Rechenzentrum installiert ist.

Sie können Cloud Foundation- oder vCenter Server-Instanzen bestellen, die den Service "HCX on {{site.data.keyword.cloud_notm}}" enthalten, oder diesen Service später über die Registerkarte **Services** auf der Seite mit den Instanzdetails zu Ihren vorhandenen Instanzen hinzufügen.

Sie können auch eine lokale HCX-Instanz für die Lizenzierung und Aktivierung Ihrer lokalen HCX-Installation bestellen.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Hinweise zu HCX on IBM Cloud](../services/hcx_considerations.html)
* [HCX on IBM Cloud verwalten](../services/managinghcx.html)
* [Hinweise zu lokalen HCX-Instanzen](../services/standalone_considerations.html)
* [Lokale HCX-Instanzen bestellen](../services/standalone_orderingserviceinstances.html)

## Flexibleres BYOL-Lizenzmodell für VMware Cloud Foundation und vCenter Server

Bei der Erstellung eines neuen Clusters für Cloud Foundation- und vCenter Server-Instanzen mit V2.1 und höher können Sie jetzt Ihre eigene Lizenz verwenden (Bring Your Own License, BYOL) oder von IBM bereitgestellte Lizenzen kaufen und so entweder Ihren vorhandenen Komponentenschlüssel nutzen oder die Lizenz von IBM mieten. Vor V2.1 war der Kauf einer von IBM bereitgestellten Lizenz für eine bestimmte VMware-Komponente nicht möglich, wenn Sie eine eigene Lizenz verwenden. Die Lizenzierung für einzelne Cluster ist gegenwärtig nur bei VMware vSphere und VMware vSAN möglich.

Wenn Sie Knoten zu einem Cluster hinzufügen, der mit Ihrem Schlüssel lizenziert ist, werden Sie außerdem von der Konsole aufgefordert, einen neuen Lizenzschlüssel anzugeben, falls die Anzahl der Knoten die Schlüsselkapazität überschreitet.

Weitere Informationen enthalten die folgenden Abschnitte:

* [Cluster für Cloud Foundation-Instanzen hinzufügen und anzeigen](../sddc/sd_addingviewingclusters.html)
* [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](../vcenter/vc_addingviewingclusters.html)
* [Häufig gestellte Fragen zu eigenen Lizenzen (BYOL)](../vmonic/faq_byol.html)

## Updates für Servicekomponente "Zerto on IBM Cloud"

Für den Service "Zerto on {{site.data.keyword.cloud_notm}}", der in Cloud Foundation-Instanzen und vCenter Server-Instanzen mit V2.1 und höher bereitgestellt wird, wird nun Zerto Virtual Replication 5.5u2 zur Verfügung gestellt. Zerto Virtual Replication Appliances (VRAs; dies sind Appliances für die virtuelle Replikation) werden jetzt aus Leistungsgründen im Managementdatenspeicher (entweder vSAN oder Endurance) und nicht im lokalen Datenspeicher bereitgestellt. Falls Sie vorhandene VRAs verwenden, sollten Sie zur Erzielung einer besseren Leistung eine Migration des zugehörigen Speichers auf den Managementdatenspeicher erwägen.

Weitere Informationen finden Sie im Abschnitt [Überblick zu Zerto on IBM Cloud](../services/addingzertodr.html).

## Updates für VMware vCenter Server-Instanzen

### Konfigurationseinstellungen für Netz-MTU

Für V2.1 oder höhere Releases werden neue vCenter Server-Instanzen mit der Einstellung "Public Distributed Virtual Switch (DVS) as MTU 1500" (Standardwert) bestellt. Weitere Informationen hierzu finden Sie unter _Konfigurationseinstellungen für Netz-MTU_ in [vCenter Server-Teileliste](../vcenter/vc_bom.html).

### Automatische Anwendung von VMware ESXi-Patches und -Updates auf Hosts

In V2.0 und früheren Releases von VMware vCenter Server-Instanzen wurden Patches nicht automatisch auf ESXi-Hosts angewendet, die zu einem Cluster hinzugefügt wurden.

Ab V2.1 wendet die Automatisierung Patches auf neue ESXi-Hosts an, damit das Patch-Level mit dem Patch-Level für den Bereitstellungszeitpunkt der ersten Instanz übereinstimmt. Sie müssen dafür sorgen, dass alle künftigen Patches und Updates manuell angewendet werden.
Sobald VMware-Patches und -Updates in künftigen Releases verfügbar werden, prüft die Automatisierung die ESXi-Hosts Ihrer vorhandenen Instanzen und erinnert Sie in einer E-Mail daran, dass die neuesten Patches und Updates manuell angewendet werden müssen.

Weitere Informationen enthält der Abschnitt [Updates auf vCenter Server-Instanzen anwenden](../vcenter/vc_applyingupdates.html).

### Schätzpreise für Aktualisierungen der VMware NSX-Lizenz

Bevor Sie eine Bestellung für ein Upgrade auf VMware NSX Advanced oder Enterprise Edition aufgeben, können Sie nun einen Schätzpreis einsehen. Die Preisbestimmung basiert auf der Anzahl der ESXi-Hosts in der vCenter Server-Instanz. Bei diesem Kauf wird lediglich der NSX-Lizenzschlüssel geändert und für VMware NSX Base Edition ein Upgrade auf Advanced oder Enterprise Edition durchgeführt. Ein Upgrade der NSX-Softwareversion findet durch den Kauf nicht statt.

Weitere Informationen enthält der Abschnitt [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Maximale Anzahl Server pro Cluster erhöht sich auf mehr als 32

Für den Standardcluster in einer Instanz können Sie bis zu 51 Server bereitstellen oder erweitern. Für alle nachfolgenden Cluster in einer Instanz können Sie bis zu 59 Server bereitstellen oder erweitern. Weitere Informationen finden Sie unter [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](../vcenter/vc_addingviewingclusters.html).

**Hinweis:** Diese Möglichkeit gibt es nur bei Instanzen, die in V2.1 und höher bereitgestellt werden. Instanzen, für ein Upgrade auf V2.1 ausgehend von älteren Releases durchgeführt wurde, besitzen diese Funktionalität nicht.

### Optionen für angepasste IBM Cloud Bare Metal Server-Konfiguration

Die angepasste Bare Metal Server-Konfiguration bietet nun den Dual Intel Xeon Gold 6140-Prozessor mit 36 Kernen insgesamt und 2,3 GHz.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)

### Konfigurationen für einzelne NFS-Dateifreigaben

Sie haben jetzt die Möglichkeit, die NFS-Dateifreigaben einzeln konfigurieren. Sie können die Dateigröße und die Leistungsstufe für jede Dateifreigabe individuell auswählen oder für alle bestellten Dateifreigaben dieselbe Dateigröße und Leistungsstufe verwenden.

Weitere Informationen enthalten die folgenden Abschnitte:
* [Überblick zu vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server-Instanzen bestellen](../vcenter/vc_orderinginstance.html)
* [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](../vcenter/vc_addingviewingclusters.html)

## Updates und Erweiterungen der Benutzerschnittstelle

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:

* Die Option **Instanz bestellen** wurde aus dem linken Navigationsfenster entfernt. Klicken Sie auf **Einführung**, um die Schritte zum Bestellen einer Instanz auszuführen.
* Das Feld **Unterdomänenpräfix**, das auf der Seite **Allgemein** beim Bestellen einer Instanz angezeigt wurde, heißt jetzt **Unterdomänenbezeichnung**.
* Beim Bestellen einer primären bzw. sekundären vCenter Server- oder Cloud Foundation-Instanz können Sie den Kostenvoranschlag jetzt nicht nur auf der Seite **Zusammenfassung** einsehen, sondern auch in jeder beliebigen Anzeige bei der Angabe der Details für Ihre Instanzbestellung berechnen lassen.
* Die Seite **Bereitgestellte Instanzen** wurde mit der Breadcrumb-Navigation als alternativer Navigationsmethode ausgestattet, was die Anzahl der erforderlichen Schritte zum Aufrufen von übergeordneten Seiten der entsprechenden Seiten verringert.
* Verschiedene Fehlernachrichten und QuickInfos wurden erweitert, um Ihnen bei der Auswahl der geeigneten Einstellung in der Benutzerschnittstelle zu helfen.

## Neue und aktualisierte Dokumentation

Eine neue developerWorks-Anleitung ist verfügbar, die Schritt für Schritt erläutert, wie dedizierter Speicher zu vorhandenen {{site.data.keyword.vmwaresolutions_full}}-Bereitstellungen mit NetApp ONTAP Select on IBM Cloud hinzugefügt wird. Weitere Informationen finden Sie auf der Seite [Steps to attach dedicated storage to VMware Solutions on IBM  Cloud](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/).

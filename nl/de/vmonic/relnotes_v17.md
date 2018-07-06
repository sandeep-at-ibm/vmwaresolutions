---

copyright:

  years:  2016, 2018

lastupdated: "2017-07-05"

---

# Releaseinformationen für V1.7

Dieses Release stellt neue Funktionen, Komponentenaktualisierungen, Verbesserungen des Bedienungskomforts und Fehlerkorrekturen zur Verfügung. Eine Liste mit den in den unterschiedlichen Releases behobenen Problemen, den bekannten Problemen beim Produkt sowie zusätzlichen Tipps für die Verwendung von {{site.data.keyword.vmwaresolutions_full}} finden Sie unter [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Updates für VMware Cloud Foundation-Instanzen

Mit diesem Update werden die folgenden Upgrades und Verbesserungen angewendet:
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* Stabilitätsverbesserungen für die Komponente "IBM CloudDriver"
* Der auf dem Intel-Prozessor "Haswell" (2690-V3) basierende EVC-Modus wird für VMware-Bereitstellungen aktiviert, die zum Zeitpunkt des Upgrades bereits auf V3-Servern vorhanden sind.

  **Hinweis**: Der EVC-Modus wird auf V4-Servern für vorhandene oder neue Bereitstellungen nicht aktiviert.

* VMware Cloud Foundation-Bereitstellungen, die vor dem 22. Mai bereitgestellt wurden und daher V3-Server verwenden, bestellen jetzt V4-Server, sobald ein neuer Knoten zur Instanz hinzugefügt wird. Diese Server verfügen über 256 GB Speicher. Wenn Sie nach dem Hinzufügen der Server 512 GB Speicher benötigen, öffnen Sie ein Support-Ticket, um einen Server-Upgrade auf 512 GB Speicher anzufordern. Unter [Kontaktaufnahme mit dem IBM Support](trbl_support.html) finden Sie weitere Angaben darüber, wie Sie sich mit dem IBM Support in Verbindung setzen.

Zusätzliche Informationen zu Komponenten finden Sie im Abschnitt [Komponenten der Cloud Foundation-Instanz](../sddc/sd_cloudfoundationoverview.html#cloud-foundation-instance-components).

### Voraussetzungen für Updateprozess

Abhängig davon, wie komplex Ihre Cloud Foundation-Instanzbereitstellung ist und ob Sie eine Konfiguration mit mehreren Standorten verwenden, müssen Sie beim Updateprozess möglicherweise eine Reihe von Schritten ausführen, die auf der Registerkarte **Update und Patch** in der Konsole angegeben sind. Weitere Informationen finden Sie unter [Updates auf Cloud Foundation-Instanzen anwenden](../sddc/sd_applyingupdates.html#applying-updates-to-cloud-foundation-instances).

## Updates für VMware vCenter Server-Instanzen

### Clusterunterstützung

Ab dem Release V1.7 können Sie ESXi-Server in vCenter Server-Instanzen mithilfe von Clustern verwalten und so ein besseres Ressourcenmanagement und eine hohe Verfügbarkeit erreichen. Die ESXi-Server, die Sie bei der Bestellung einer Instanz konfiguriert haben, werden standardmäßig unter **cluster1** gruppiert. Auf der neu eingeführten Registerkarte **Infrastruktur** der Seite mit den Instanzdetails können Sie die Clusterdetails anzeigen und für eine Instanz bis zu insgesamt fünf Cluster hinzufügen. Wenn Sie die Kapazität für eine Instanz erweitern oder verringern, können Sie auswählen, in welchem Cluster ESXi-Server hinzugefügt oder entfernt werden sollen. Weitere Informationen finden Sie unter [Cluster für vCenter Server-Instanzen hinzufügen und anzeigen](../vcenter/vc_addingviewingclusters.html).

### Funktionale Erweiterungen bei der Bereitstellung der Disaster-Recovery mit Zerto

Die Bereitstellung der Disaster-Recovery mit Zerto erfolgt jetzt automatisiert und wird nicht über ein Support-Ticket abgewickelt. Alle Kosten für Zerto-Komponenten (z. B. privates portierbares Teilnetz und Windows-VSI) und die Zerto-Lizenz werden bei den geschätzten Kosten aufgeführt und können von Ihnen überprüft werden, bevor Sie die Bestellung aufgeben. Weitere Informationen finden Sie unter [Bereitstellungsprozess für Disaster-Recovery mit Zerto](../services/addingzertodr.html).

### Upgradefunktionen für NSX-Lizenzen

Sie können für Ihre NSX-Lizenzedition ausgehend von der Registerkarte **Zusammenfassung** Ihrer vCenter Server-Instanz ein Upgrade durchführen. Bei der Aktualisierung der Lizenz werden alle vorhandenen NSX-SoftLayer-Lizenzen in Ihrem Konto durch die neue Lizenz ersetzt. Weitere Informationen finden Sie unter [vCenter Server-Instanzen anzeigen](../vcenter/vc_viewinginstances.html).

## Erweiterungen beim Bedienungskomfort

In der gesamten Benutzerschnittstelle wurden Verbesserungen vorgenommen:
* Die Registerkarte **Eigenschaften** auf der Seite mit den Details für Cloud Foundation-Instanzen heißt künftig **Zusammenfassung**. Auf dieser Registerkarte können Sie jetzt die Details der Instanz, die Zugriffsinformationen der instanzbezogenen Komponenten und den Bereitstellungsverlauf für die Instanz einsehen.
* Auf der Seite mit den Details für Cloud Foundation-Instanzen gibt es jetzt eine neue Registerkarte namens **Infrastruktur**. Auf dieser Registerkarte können Sie ESXi-Server anzeigen, hinzufügen oder entfernen.
* Die Dokumentation für {{site.data.keyword.vmwaresolutions_short}} besitzt ein neues Format und wurde zusammen mit dem Bluemix-Dokumentationsset vollständig in den Bluemix-Katalog integriert. Für den Zugriff auf die Dokumentation haben Sie die folgenden Möglichkeiten:
  * Klicken Sie in {{site.data.keyword.vmwaresolutions_short}} links im Banner auf **Docs**.
  * Blättern Sie im Bluemix-Dokumentationskatalog abwärts bis zum Abschnitt **Compute & Services** und klicken Sie auf **{{site.data.keyword.vmwaresolutions_short}}**.

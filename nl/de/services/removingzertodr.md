---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Löschprozess für Zerto on IBM Cloud
{: #removingzertodr}

Der Löschprozess für den Service "Zerto on {{site.data.keyword.cloud}}" ist automatisiert. Die folgenden Schritte werden für das erfolgreiche Entfernen des Service "Zerto on {{site.data.keyword.cloud_notm}}" ausgeführt.

## Zerto on IBM Cloud entfernen
{: #removingzertodr-remove}

1. Klicken Sie im linken Navigationsfenster auf **Bereitgestellte Instanzen** und klicken Sie auf die Instanz, aus der Sie den Service entfernen wollen.
2. Klicken Sie auf die Registerkarte **Services**.
3. Klicken Sie auf der Registerkarte **Installierte Services** in der rechten oberen Ecke der Servicekarte auf das Überlaufmenüsymbol und anschließend auf **Service entfernen**.
4. Prüfen Sie die gegebenenfalls im Fenster **Service entfernen** angezeigten Hinweise oder Warnungen. Klicken Sie auf **Zur Kenntnis genommen**.
5. Nachdem Ihre Anforderung zum Entfernen des Service akzeptiert wurde, ändert sich der Servicestatus in **Wird entfernt** und die folgenden Schritte zum Entfernen werden ausgeführt:   
   1. Zerto Virtual Replication Appliances, die auf allen ESXi-Servern bereitgestellt wurden, werden entfernt.
   2. Zerto Virtual Replication wird deinstalliert.
   3. Die virtuelle Serviceinstanz (VSI) von Windows, in der Zerto Virtual Replication installiert war, wird gelöscht.
   4. Das private portierbare Teilnetz, das für die Kommunikation von Zerto Virtual Replication bestellt wurde, wird an die {{site.data.keyword.cloud_notm}}-Infrastruktur zurückgegeben.   
   5. Die Gebühren für den Disaster-Recovery-Service von Zerto werden aus Ihrer {{site.data.keyword.cloud_notm}}-Abrechnungsanweisung entfernt.

      Der entfernte Disaster-Recovery-Service von Zerto wird Ihnen bis zum Ende des Abrechnungszyklus berechnet.
      {:note}

## Ergebnisse
{: #removingzertodr-results}

Nachdem das Entfernen des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Serviceeintrag wird auf der Registerkarte **Installierte Services** gelöscht.

## Zugehörige Links
{: #removingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} bestellen](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} verwalten](managingzertodr.html)
* [Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server-Instanzen](../vcenter/vc_vcenterserveroverview.html)
* [Website "zerto.com"](https://www.zerto.com){:new_window}
* [Technische Dokumentation zu Zerto (englisch)](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

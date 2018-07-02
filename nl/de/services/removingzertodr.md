---

copyright:

  years:  2016, 2018

lastupdated: "2018-04-05"

---

# Löschprozess für Zerto on IBM Cloud
<!-- Do not remove this topic. Though it's no longer in the TOC, it's referenced from the V1.3 release notes -->

Der Löschprozess für den Service "Zerto on IBM® Cloud" ist automatisiert. Die folgenden Schritte werden für das erfolgreiche Entfernen des Service "Zerto on IBM Cloud" ausgeführt.

## Zerto on IBM Cloud entfernen

1. Klicken Sie im linken Navigationsfenster auf **Bereitgestellte Instanzen** und klicken Sie auf die Instanz, aus der Sie den Service entfernen wollen.
2. Klicken Sie auf die Registerkarte **Services**.
3. Klicken Sie auf der Registerkarte **Installierte Services** in der rechten oberen Ecke der Servicekarte auf das Überlaufmenüsymbol und anschließend auf **Service entfernen**.
4. Prüfen Sie die gegebenenfalls im Fenster **Service entfernen** angezeigten Hinweise oder Warnungen. Klicken Sie auf **Zur Kenntnis genommen**.
5. Nachdem Ihre Anforderung zum Entfernen des Service akzeptiert wurde, ändert sich der Servicestatus in **Wird entfernt** und die folgenden Schritte zum Entfernen werden ausgeführt:   
   1. Zerto Virtual Replication Appliances, die auf allen ESXi-Servern bereitgestellt wurden, werden entfernt.
   2. Zerto Virtual Replication wird deinstalliert.
   3. Die virtuelle Serverinstanz (VSI) von Windows, in der Zerto Virtual Replication installiert war, wird gelöscht.
   4. Das private portierbare Teilnetz, das für die Kommunikation von Zerto Virtual Replication bestellt wurde, wird an die IBM Cloud-Infrastruktur zurückgegeben.   
   5. Die Gebühren für den Disaster-Recovery-Service von Zerto werden aus Ihrer IBM Cloud-Abrechnungsanweisung entfernt.

      **Hinweis** Der entfernte Disaster-Recovery-Service von Zerto wird Ihnen bis zum Ende des Abrechnungszyklus berechnet.

## Ergebnisse

Nachdem das Entfernen des Service erfolgreich abgeschlossen wurde, werden Sie per E-Mail benachrichtigt und der Serviceeintrag wird auf der Registerkarte **Installierte Services** gelöscht.

## Zugehörige Links

* [Zerto on IBM Cloud bestellen](zerto_ordering.html)
* [Zerto on IBM Cloud verwalten](managingzertodr.html)
* [Cloud Foundation-Instanzen](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server-Instanzen](../vcenter/vc_vcenterserveroverview.html)
* [Website "zerto.com"](https://www.zerto.com){:new_window}
* [Zerto technical documentation](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

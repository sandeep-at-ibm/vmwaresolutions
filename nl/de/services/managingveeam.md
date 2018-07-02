---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud verwalten

Bei Instanzen, die in früheren Releases als V1.8 bereitgestellt wurden, müssen Sie die virtuelle Serverinstanz für Veeam ersetzen, die in den Instanzen vorhanden ist, wenn Sie den Service "Veeam on {{site.data.keyword.cloud}}" nutzen wollen. Nachdem der Service in Ihrer Instanz bereitgestellt wurde, können Sie über RDP auf die Veeam-Konsole zugreifen, um die Sicherung und Wiederherstellung aller virtuellen Maschinen in Ihrer Umgebung zu verwalten, einschließlich der Sicherung und Wiederherstellung von Managementkomponenten. Sie können auch ein Upgrade für den Service durchführen, indem Sie die Veeam-Updates von der Veeam-Website herunterladen und installieren.

## Virtuelle Serverinstanz für Veeam in Instanzen vor V1.8 durch Veeam on IBM Cloud ersetzen

Der Service "Veeam on {{site.data.keyword.cloud_notm}}" der sowohl Managementkomponenten als auch Workloads sichern kann, ersetzt die vorherige virtuelle Serverinstanz für Veeam, die in früheren Releases als V1.8 von VMWare Cloud Foundation und VMware vCenter Server zur reinen Sicherung von Managementkomponenten integriert war. Aufgrund dieser Änderung wurde die vorherige Registerkarte **Sicherung und Wiederherstellung** auf der Seite mit den Instanzdetails entfernt und die Sicherungspunkte für die Instanzen sind in der {{site.data.keyword.vmwaresolutions_short}}-Konsole nicht mehr verfügbar, auch wenn die virtuelle Serverinstanz für Veeam in den Instanzen vor V1.8 funktioniert. Sie müssen ein {{site.data.keyword.cloud_notm}}-Support-Ticket erstellen, um Unterstützung bei einer Wiederherstellung zu erhalten. Darüber hinaus ist die Lizenz für die virtuelle Serverinstanz für Veeam in den Versionen vor V1.8 am 14. Oktober 2017 abgelaufen. Daher müssen Sie die vorherige virtuelle Serverinstanz für Veeam durch den neuen Service "Veeam on {{site.data.keyword.cloud_notm}}" ersetzen.

Führen Sie die folgenden Schritte aus:
1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf  **Bereitgestellte Instanzen** und klicken Sie dann auf die Zielinstanz.
2. Klicken Sie auf der Seite mit den Instanzdetails auf die Registerkarte **Update und Patch**. Vergewissern Sie sich, dass für die Instanz ein Upgrade auf das Release V1.8 durchgeführt worden ist.
3. Klicken Sie auf die Registerkarte **Services**.
4. Installieren Sie auf der Registerkarte **Services hinzufügen** den Service "Veeam on {{site.data.keyword.cloud_notm}}".

Nachdem der neue Service "Veeam on {{site.data.keyword.cloud_notm}}" bereitgestellt worden ist und eine erfolgreiche Sicherung Ihrer Managementkomponenten ausgeführt wurde, können Sie die vorhandene virtuelle Serverinstanz für Veeam aus Ihrem Konto entfernen, indem Sie ein {{site.data.keyword.cloud_notm}}-Support-Ticket erstellen. Vom IBM Support werden dann die vorhandene virtuelle Serverinstanz für Veeam sowie der Speicher ermittelt und gelöscht.

## Mit RDP auf die Veeam-Konsole zugreifen

Um den Service "Veeam on {{site.data.keyword.cloud_notm}}" zu verwalten, müssen Sie mit den folgenden Schritten auf die Veeam-Konsole zugreifen:
1. Stellen Sie mit RDP (Remote Desktop Protocol) eine Verbindung zu der Windows-IP-Adresse her, die auf der Seite mit den Details für den Service "Veeam on {{site.data.keyword.cloud_notm}}" zu finden ist.
2. Melden Sie sich bei der Windows-Konsole unter Verwendung der Administratorberechtigungsnachweise an, die auf der Seite mit den Details für den Service "Veeam on {{site.data.keyword.cloud_notm}}" zu finden sind.
3. Greifen Sie über die Windows-Konsole unter Verwendung der Administratorberechtigungsnachweise, die auf der Seite mit den Details für den Service "Veeam on {{site.data.keyword.cloud_notm}}" zu finden sind, auf die Veeam-Konsole zu.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](../sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_addingremovingservices.html)

## Managementkomponenten für Instanzen mit installiertem Service "Veeam on IBM Cloud" sichern und wiederherstellen

Der Service "Veeam on {{site.data.keyword.cloud_notm}}" ist mit einem Managementsicherungsjob vorkonfiguriert, der täglich automatisch ausgeführt wird, um die Managementkomponenten mit bis zu 14 Wiederherstellungspunkten zu sichern.

Mithilfe der Veeam-Konsole können Sie die Managementkomponenten auch manuell sichern. Ab Release V1.8 werden die Konfigurationsänderungen in Ihrer Umgebung nicht automatisch gesichert. Es wird daher empfohlen, eine manuelle Sicherung der Managementkomponenten auszuführen, indem Sie den vorkonfigurierten Managementsicherungsjob in der Veeam-Konsole ausführen, bevor Sie die Konfiguration Ihrer Umgebung ändern. Weitere Informationen zur Ausführung des manuellen Sicherungsjobs finden Sie auf der Seite [Veeam technical instructions](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

Wenn Fehler in den Managementkomponenten auftreten, können Sie die Managementkomponenten mithilfe der Veeam-Konsole im Zustand einer früheren Sicherung wiederherstellen. Weitere Informationen zur Ausführung des manuellen Wiederherstellungsjobs finden Sie auf der Seite [Veeam technical instructions]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Upgrade für Veeam on IBM Cloud durchführen

Wenn Sie ein Upgrade für den Service "Veeam on {{site.data.keyword.cloud_notm}}" durchführen möchten, laden Sie die Veeam-Updates von der Veeam-Website herunter, kopieren Sie die Updates in die virtuelle Serverinstanz für Veeam und installieren Sie die Updates.

## Zugehörige Links

* [Überblick zu Veeam on {{site.data.keyword.cloud_notm}}](veeam_considerations.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Website "Veeam.com"](https://www.veeam.com/)
* [Veeam technical documentation](https://www.veeam.com/documentation-guides-datasheets.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Veeam on IBM Cloud verwalten

Nachdem der Service in Ihrer Instanz bereitgestellt wurde, können Sie über RDP auf die Veeam-Konsole zugreifen, um die Sicherung und Wiederherstellung aller virtuellen Maschinen in Ihrer Umgebung zu verwalten, einschließlich der Sicherung und Wiederherstellung von Managementkomponenten. Sie können auch ein Upgrade für den Service durchführen, indem Sie die Veeam-Updates von der Veeam-Website herunterladen und installieren.

Bei Instanzen, die in früheren Releases als V1.8 bereitgestellt wurden, müssen Sie die virtuelle Serverinstanz für Veeam ersetzen, die in den Instanzen vorhanden ist, wenn Sie den Service "Veeam on {{site.data.keyword.cloud}}" nutzen wollen. Weitere Informationen finden Sie im Abschnitt _Virtuelle Serverinstanz für Veeam in Instanzen vor V1.8 durch Veeam on IBM Cloud ersetzen_.

## Mit RDP auf die Veeam-Konsole zugreifen

Greifen Sie zum Verwalten des Service "Veeam on {{site.data.keyword.cloud_notm}}" durch Ausführen der folgenden Schritte auf die Veeam-Konsole zu:
1. Stellen Sie mit RDP (Remote Desktop Protocol) eine Verbindung zu der Windows-IP-Adresse her.
2. Melden Sie sich unter Verwendung der Administratorberechtigungsnachweise bei der Windows-Konsole an.
3. Greifen Sie über die Windows-Konsole mithilfe der Administratorberechtigungsnachweise auf die Veeam-Konsole zu.

Sie finden die Windows-IP-Adresse und die Administratorberechtigungsnachweise auf der Seite mit den Details für den Service "Veeam on {{site.data.keyword.cloud_notm}}".

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)

## Managementkomponenten für Instanzen mit installiertem Service "Veeam on IBM Cloud" sichern und wiederherstellen

Der Service "Veeam on {{site.data.keyword.cloud_notm}}" kann über die Veeam-Konsole zur Sicherung der Managementkomponenten konfiguriert werden. Weitere Informationen finden Sie unter [Komponenten sichern](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html).

Instanzen, die in V1.8 oder höheren Releases bereitgestellt wurden (oder für die Upgrades auf diese Releases durchgeführt wurden), werden die Konfigurationsänderungen in Ihrer Umgebung nicht automatisch gesichert. Es wird daher empfohlen, vor jeglichen Änderungen an der Konfiguration Ihrer Umgebung eine manuelle Sicherung der Managementkomponenten auszuführen, indem Sie den Managementsicherungsjob in der Veeam-Konsole ausführen. Weitere Informationen zur manuellen Sicherung finden Sie auf der Seite [Veeam technical instructions](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

Wenn Fehler in den Managementkomponenten auftreten, können Sie die Managementkomponenten mithilfe der Veeam-Konsole im Zustand einer früheren Sicherung wiederherstellen. Weitere Informationen zur manuellen Wiederherstellung finden Sie auf der Seite [Veeam technical instructions]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Updates auf Veeam on IBM Cloud anwenden

Sie sind dafür verantwortlich, dass sich die Veeam-Software jeweils auf dem aktuellsten Versionsstand befindet.

### Anwendung von Aktualisierungen auf Instanzen, die mit öffentlichem und privatem Netz bereitgestellt wurden

Wenn der Veeam-Service auf einer Instanz mit öffentlichem und privaten Netz installiert ist, können Sie die Veeam-Software verwenden, um Updates zu suchen und herunterzuladen.

### Anwendung von Aktualisierungen auf Instanzen, die nur mit privatem Netz bereitgestellt wurden

Wenn der Veeam-Service nur auf einer Instanz mit privatem Netz installiert ist, weil die Veeam-VSI ohne öffentliche Netzzugangsberechtigung konfiguriert ist, können Sie die Veeam-Software nicht verwenden, um Updates zu suchen und herunterzuladen. Stattdessen müssen Sie Updates von der Veeam-Website herunterladen, sie an die Veeam-VM übertragen und sie anschließend installieren.

## Veeam-Lizenzen aktualisieren

### Aktualisierungen von Veeam-Lizenzen, die mit öffentlichem und privatem Netz bereitgestellt wurden

Wenn der Veeam-Service auf einer Instanz mit öffentlichem und privaten Netz installiert ist, können Sie Ihre Veeam-Lizenz entweder automatisch oder manuell aktualisieren, indem Sie den Veeam-Anweisungen im Abschnitt zur [Lizenzaktualisierung]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html) folgen.

### Aktualisierung von Veeam-Lizenzen für Instanzen, die nur mit privatem Netz bereitgestellt wurden

Wenn der Veeam-Service auf einer Instanz mit nur privatem Netz installiert ist, müssen Sie das Ablaufdatum Ihrer Lizenz notieren und sich an den [IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html) wenden, um Unterstützung bei der Aktualisierung des Lizenzschlüssels zu erhalten, wenn die Verlängerung erforderlich wird. 

## Virtuelle Serverinstanz für Veeam in Instanzen vor V1.8 durch Veeam on IBM Cloud ersetzen

Der Service "Veeam on {{site.data.keyword.cloud_notm}}" der sowohl Managementkomponenten als auch Workloads sichern kann, ersetzt die vorherige virtuelle Serverinstanz für Veeam, die in früheren Releases als V1.8 von VMware Cloud Foundation und VMware vCenter Server zur reinen Sicherung von Managementkomponenten integriert war.

Aufgrund dieser Änderung wurde die vorherige Registerkarte **Sicherung und Wiederherstellung** auf der Seite mit den Instanzdetails entfernt und die Sicherungspunkte für die Instanzen sind in der {{site.data.keyword.vmwaresolutions_short}}-Konsole nicht mehr verfügbar, auch wenn die virtuelle Serverinstanz für Veeam in den Instanzen vor V1.8 funktioniert.

Sie müssen ein {{site.data.keyword.cloud_notm}}-Support-Ticket erstellen, um Unterstützung bei einer Wiederherstellung zu erhalten. Darüber hinaus lief die Lizenz der virtuellen Serverinstanz für Veeam in Instanzen aus Releases vor V1.8 am 14. Oktober 2017 ab. Daher müssen Sie die vorherige virtuelle Serverinstanz für Veeam durch den neuen Service "Veeam on {{site.data.keyword.cloud_notm}}" ersetzen.

Führen Sie die folgenden Schritte aus:
1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen** und klicken Sie dann auf die Zielinstanz.
2. Klicken Sie auf der Seite mit den Instanzdetails auf die Registerkarte **Update und Patch**. Vergewissern Sie sich, dass für die Instanz ein Upgrade auf das Release V1.8 durchgeführt worden ist.
3. Klicken Sie auf die Registerkarte **Services**.
4. Installieren Sie auf der Registerkarte **Services hinzufügen** den Service "Veeam on {{site.data.keyword.cloud_notm}}".

Nachdem der neue Service "Veeam on {{site.data.keyword.cloud_notm}}" bereitgestellt worden ist und eine erfolgreiche Sicherung Ihrer Managementkomponenten ausgeführt wurde, können Sie die vorhandene virtuelle Serverinstanz für Veeam aus Ihrem Konto entfernen, indem Sie ein {{site.data.keyword.cloud_notm}}-Support-Ticket erstellen. Vom IBM Support werden die vorhandene virtuelle Serverinstanz für Veeam sowie der Speicher ermittelt und gelöscht.

### Zugehörige Links

* [Veeam on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions/services/veeam_considerations.html)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic/faq.html)
* [Website "Veeam.com"](https://www.veeam.com/)
* [Technische Dokumentation zu Veeam](https://www.veeam.com/documentation-guides-datasheets.html)

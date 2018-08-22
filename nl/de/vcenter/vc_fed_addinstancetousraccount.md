---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# VMware Federal-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren

VMware Federal-Instanzen, die in Version 2.5 und höheren Releases in Ihrem {{site.data.keyword.cloud}}-Konto bereitgestellt wurden, werden Ihrem Konto automatisch hinzugefügt und von {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) verwaltet. 

Bei Instanzen, die in Version 2.4 und älteren Releases bereitgestellt wurden, können Sie diese auf angegebene {{site.data.keyword.cloud_notm}}-Konten für das IAM-basierte Benutzermanagement migrieren.

## Vorgehensweise

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie in der rechten oberen Ecke der Konsole auf Ihren Avatar und klicken Sie auf das Feld **Konto**, um das Benutzerkonto auszuwählen, auf das Sie die Instanz migrieren wollen.
3. Suchen Sie die Instanz der Version vor 2.5 in der Tabelle **vCenter Server-Instanzen**.
4. Klicken Sie in der Spalte **Aktionen** auf das Überlaufmenüsymbol und anschließend auf **Instanz auf Konto migrieren**.
5. Prüfen und bestätigen Sie im Fenster **Instanz auf Konto migrieren** das Konto, auf das die Instanz migriert werden soll, und klicken Sie auf **Migrieren**.

## Ergebnisse

1. Sie empfangen eine Konsolbenachrichtigung, dass Ihre Anforderung zum Migrieren der Instanz auf das angegebene {{site.data.keyword.cloud_notm}}-Konto akzeptiert wurde. 
2. Wenn die Migration der Instanz abgeschlossen ist, wird die Instanz auf der Seite **Bereitgestellte Instanzen** unter dem Konto angezeigt, auf das sie migriert wurde. Die migrierte Instanz wird nicht mehr in dem ursprünglichen Konto angezeigt, aus dem sie migriert wurde.

### Zugehörige Links

* [Benutzerzugriff mit IAM verwalten](../vmonic/iam.html)
* [Benutzer für den Zugriff auf Services und Ressourcen einladen](../vmonic/iamuserinvite.html)
* [Was ist IBM Cloud IAM?](https://console.stage1.bluemix.net/docs/iam/index.html#iamoverview)

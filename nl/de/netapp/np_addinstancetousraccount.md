---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: NetApp migrate instance, add account NetApp ONTAP, migrate cloud account

subcollection: vmware-solutions


---

# NetApp ONTAP Select-Instanzen aus Versionen vor Version 2.5 auf IBM Cloud-Konten migrieren
{: #np_addinstancetousraccount}

NetApp ONTAP Select-Instanzen, die in Version 2.5 und höheren Releases in Ihrem {{site.data.keyword.cloud}}-Konto bereitgestellt wurden, werden Ihrem Konto automatisch hinzugefügt und von {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) verwaltet.

Bei Instanzen, die in Version 2.4 und älteren Releases bereitgestellt wurden, können Sie diese auf angegebene {{site.data.keyword.cloud_notm}}-Konten für das IAM-basierte Benutzermanagement migrieren.

## Vorbereitende Schritte
{: #np_addinstancetousraccount-prereq}

Stellen Sie sicher, dass das {{site.data.keyword.cloud_notm}}-Konto, in das die Instanz migriert werden soll, nicht ein Nur-IaaS-Konto ist. Ein Nur-IaaS-Konto ist ein Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (IBM Cloud), das keine Verbindung zu einem {{site.data.keyword.cloud_notm}}-Konto hat.

Weitere Informationen zum Verknüpfen Ihres Nur-IaaS-Kontos mit Ihrem PaaS-Konto finden Sie in [Folgen Sie diesen Schritten, um Ihr IaaS-Konto und Ihr PaaS-Konto zu verknüpfen](https://www.ibm.com/cloud/blog/follow-steps-link-iaas-paas-accounts){:new_window}.

## Vorgehensweise beim Migrieren von Instanzen
{: #np_addinstancetousraccount-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Ressourcen**.
2. Klicken Sie im Konsolenbanner auf das Symbol Ihres Benutzerkontos und klicken Sie anschließend auf das Feld **Konto**, um das Benutzerkonto auszuwählen, in das Sie die Instanz migrieren möchten.
3. Suchen Sie die Instanz der Version vor 2.5 in der Tabelle **NetApp ONTAP Select-Instanzen**.
4. Klicken Sie in der Spalte **Aktionen** auf das Überlaufmenüsymbol und anschließend auf **Instanz auf Konto migrieren**.
5. Prüfen und bestätigen Sie im Fenster **Instanz auf Konto migrieren** das Konto, auf das die Instanz migriert werden soll, und klicken Sie auf **Migrieren**.

## Ergebnisse
{: #np_addinstancetousraccount-results}

1. Sie empfangen eine Konsolbenachrichtigung, dass Ihre Anforderung zum Migrieren der Instanz auf das angegebene {{site.data.keyword.cloud_notm}}-Konto akzeptiert wurde.
2. Wenn die Instanzmigration abgeschlossen ist, wird die Instanz auf der Seite **Ressourcen** unter dem Konto angezeigt, auf das sie migriert wurde. Die migrierte Instanz wird nicht mehr in dem ursprünglichen Konto angezeigt, aus dem sie migriert wurde.

## Zugehörige Links
{: #np_addinstancetousraccount-related}

* [Benutzerzugriff mit IAM verwalten](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-iam#iam)
* [Benutzer für den Zugriff auf Services und Ressourcen einladen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Was ist IBM Cloud IAM?](/docs/iam?topic=iam-iamoverview)

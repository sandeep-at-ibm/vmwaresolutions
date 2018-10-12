---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Benutzer für den Zugriff auf Services und Ressourcen einladen

{{site.data.keyword.vmwaresolutions_full}} ist für die Zusammenarbeit unter mehreren Benutzern in {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) integriert. Nach der Registrierung für ein {{site.data.keyword.cloud_notm}}-Konto und der Anmeldung an der {{site.data.keyword.vmwaresolutions_short}}-Konsole können Sie dem {{site.data.keyword.cloud_notm}}-Konto Benutzer hinzufügen. Diese hinzugefügten Benutzer können die Services und Ressourcen, die für das Konto bereitgestellt werden, gemeinsam nutzen.

## Vorbereitende Schritte

* Stellen Sie sicher, dass Sie der Kontoeigner sind oder dass Sie die Plattformmanagementrolle **Administrator** für den Service **VMware Solutions** besitzen.
* Stellen Sie sicher, dass Sie die Benutzerrollen und Berechtigungen geprüft haben, die unter [Benutzerzugriff mit Identity and Access Management verwalten](iam.html) aufgeführt sind.

## Vorgehensweise

1. Klicken Sie auf der linken Seite des Banners auf **Verwalten > Sicherheit > Identität und Zugriff**.
2. Klicken Sie auf der Seite **Benutzer**  auf **Benutzer einladen**.
3. Geben Sie auf der Seite **Benutzer einladen** im Abschnitt **Benutzer** die E-Mail-Adressen der Benutzer, die Sie einladen wollen, in das Feld **E-Mail-Adresse** ein.
4. Erweitern Sie im Abschnitt **Zugriff** die Option **Services** und führen Sie die folgenden Tasks aus:
   1. Wählen Sie **Ressource** in der Liste **Zugriff zuweisen für** aus.
   2. Wählen Sie **VMware-Lösungen** in der Liste **Services** aus.
   3. Wählen Sie die Plattformzugriffsrolle aus, die den Benutzern zugewiesen werden soll. Mögliche Rollen sind **Administrator**, **Editor**, **Operator** und **Anzeigeberechtigter**.
5. Klicken Sie auf **Benutzer einladen**.

## Ergebnisse

Sobald die hinzugefügten Benutzer Ihre Einladung akzeptiert haben, können sie sich an der {{site.data.keyword.vmwaresolutions_short}}-Konsole anmelden und zu Ihrem Konto wechseln. Dazu klicken Benutzer in ihren Profileinstellungen auf das Symbol für das Benutzerkonto im {{site.data.keyword.vmwaresolutions_short}}-Konsolenbanner. Anschließend können die hinzugefügten Benutzer zusammenarbeiten und die Services und Ressourcen, die in Ihrem angegebenen Konto verfügbar sind, gemeinsam nutzen.

### Zugehörige Links

* [Benutzer einladen und Zugriff zuweisen](../../../iam/iamuserinv.html)
* [Identität und Zugriff verwalten](../../../iam/quickstart.html)
* [Benutzer und Zugriff verwalten](../../../iam/iamusermanage.html)
* [Was ist IAM?](../../../iam/index.html)
* [vCenter Server-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../vcenter/vc_addinstancetousraccount.html)
* [vCenter Server with Hybridity Bundle-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Cloud Foundation-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../sddc/sd_addinstancetousraccount.html)
* [NetApp ONTAP Select-Instanzen aus Versionen vor Version 2.5 auf IBM Cloud-Konten migrieren](../netapp/np_addinstancetousraccount.html)
* [VMware Federal-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../vcenter/vc_fed_addinstancetousraccount.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Benutzerzugriff mit IAM verwalten

Der Zugriff auf {{site.data.keyword.vmwaresolutions_full}}-Serviceinstanzen für die Benutzer in Ihrem Konto wird durch {{site.data.keyword.cloud}} Identity and Access Management (IAM) gesteuert. Jeder Benutzer, der auf die {{site.data.keyword.vmwaresolutions_short}}-Services in Ihrem Konto zugreift, muss über eine zugeordnete Zugriffsrichtlinie mit einer definierten IAM-Benutzerrolle verfügen.

Die Zugriffsrichtlinie bestimmt die Aktionen, die der Benutzer im Kontext des von Ihnen ausgewählten Service oder der von Ihnen ausgewählten Instanz ausführen kann. Die zulässigen Aktionen werden durch den {{site.data.keyword.cloud_notm}}-Service als Operationen angepasst und definiert, deren Ausführung im Service zulässig ist. Anschließend werden die Aktionen IAM-Benutzerrollen zugeordnet.

Richtlinien ermöglichen die Erteilung von Zugriff auf verschiedenen Ebenen. Einige der Optionen sind die folgenden Zugriffe:

* Zugriff auf alle Serviceinstanzen in Ihrem Konto
* Zugriff auf eine einzelne Serviceinstanz in Ihrem Konto
* Zugriff auf eine bestimmte Ressource innerhalb einer Instanz
* Zugriff auf alle IAM-fähigen Services in Ihrem Konto

Nach der Definition des Bereichs der Zugriffsrichtlinie weisen Sie eine Rolle zu.

Prüfen Sie die folgenden Informationen, in denen die Aktionen erläutert werden, die durch die einzelnen Rollen im {{site.data.keyword.vmwaresolutions_short}}-Service zugelassen werden.

## Plattformmanagementrollen und Berechtigungen

Plattformmanagementrollen ermöglichen Benutzern die Ausführung von Tasks auf Serviceressourcen auf Plattformebene. Sie können zum Beispiel Benutzerzugriff auf den Service erteilen, Service-IDs erstellen oder löschen, Instanzen erstellen und Instanzen an Anwendungen binden.

Die folgende Tabelle enthält Informationen zu den Aktionen, die den Plattformmanagementrollen zugeordnet sind.

Tabelle 1. Plattformmanagementrollen und zugelassene Aktionen

| Plattformmanagementrolle | Aktionen | Beispielaktionen |
|:----------------- |:----------------- |:----------------- |
| Anzeigeberechtigter (Viewer) | Aktionen unter Schreibschutz | <ul><li>Zusammenfassung der Instanzen anzeigen</li><li>Details einer Instanz anzeigen</li></ul>|
| Editor (Bearbeiter) | Bestimmte Instanz aktualisieren |<ul><li>ESXi-Server hinzufügen oder entfernen</li><li>Cluster hinzufügen oder entfernen</li><li>Services hinzufügen oder entfernen</li><li>Upgrade einer Instanz auf höhere Version durchführen</li></ul> |
| Operator | Aktionen unter Schreibschutz | <ul><li>Instanzen auflisten</li><li>Details einer Instanz anzeigen</li></ul> |
| Administrator | Vollständiger Managementzugriff |<ul><li>Neue Instanzen erstellen</li><li>Instanzen löschen</li><li>Plattformzugriff anderen Benutzern erteilen</li></ul>|

Für {{site.data.keyword.vmwaresolutions_short}} sind die folgenden Aktionen verfügbar:

Tabelle 2. Aktionsbeschreibungen und erforderliche Rollen

| Aktion | Operation für Service | Rolle |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Neue Instanzen erstellen | Administrator |
| vmware-solutions.instances.delete | Instanzen löschen | Administrator |
| vmware-solutions.instances.view | <ul><li>Instanzen auflisten</li><li>Details einer Instanz anzeigen</li></ul> | Anzeigeberechtigter, Operator, Editor und Administrator |
| vmware-solutions.instances.update | <ul><li>ESXi-Server hinzufügen oder entfernen</li><li>Cluster hinzufügen oder entfernen</li><li>Services hinzufügen oder entfernen</li><li>Upgrade einer Instanz auf höhere Version durchführen</li></ul> | Editor und Administrator |
| vmware-solutions.account.update | Kontoeinstellungen aktualisieren | Administrator |

## Zugriff für Benutzer verwalten

Sie können dem {{site.data.keyword.cloud_notm}}-Konto neue Benutzer hinzufügen, sodass diese Benutzer die Services und Ressourcen, die für das Konto zur Verfügung gestellt werden, gemeinsam nutzen können. Weitere Informationen finden Sie unter [Benutzer für den Zugriff auf Services und Ressourcen einladen](../vmonic/iamuserinvite.html).

Sie können außerdem den Zugriff für vorhandene Benutzer verwalten, indem Sie zum Beispiel den vorhandenen Zugriff ändern, einen neuen Zugriff zuweisen oder den zugewiesenen Zugriff prüfen. Zur Verwaltung des Zugriffs für Benutzer müssen Sie der Kontoeigner sein oder die Plattformmanagementrolle **Administrator** besitzen. Weitere Informationen finden Sie unter [IAM-Zugriff verwalten](../../../iam/mngiam.html).

## Vorhandene Instanzen auf IBM Cloud-Konten migrieren

Durch die Integration von {{site.data.keyword.vmwaresolutions_short}} in IAM werden Instanzen, die in V2.5 und höheren Releases in Ihrem {{site.data.keyword.cloud}}-Konto bereitgestellt werden, Ihrem Konto automatisch hinzugefügt und durch IAM verwaltet.

Ihre vorhandenen Instanzen, die in V2.4 und früheren Releases bereitgestellt wurden, können Sie auf angegebene {{site.data.keyword.cloud_notm}}-Konten migrieren, um sie mithilfe von IAM zu verwalten. Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../vcenter/vc_addinstancetousraccount.html)
* [vCenter Server with Hybridity Bundle-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Cloud Foundation-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../sddc/sd_addinstancetousraccount.html)
* [NetApp ONTAP Select-Instanzen aus Versionen vor Version 2.5 auf IBM Cloud-Konten migrieren](../netapp/np_addinstancetousraccount.html)
* [VMware Federal-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](../vcenter/vc_fed_addinstancetousraccount.html)

### Zugehörige Links

* [Identität und Zugriff verwalten](../../../iam/quickstart.html)
* [Benutzer und Zugriff verwalten](../../../iam/iamusermanage.html)
* [Was ist IAM?](../../../iam/index.html)

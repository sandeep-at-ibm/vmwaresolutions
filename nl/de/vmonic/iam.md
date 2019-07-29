---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-11"

keywords: IAM user, user role, user permission

subcollection: vmware-solutions


---

# Benutzerzugriff mit IAM verwalten
{: #iam}

Der Zugriff auf {{site.data.keyword.vmwaresolutions_full}}-Serviceinstanzen für die Benutzer in Ihrem Konto wird durch {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) gesteuert. Jeder Benutzer, der auf die {{site.data.keyword.vmwaresolutions_short}}-Services in Ihrem Konto zugreift, muss über eine zugeordnete Zugriffsrichtlinie mit einer definierten IAM-Benutzerrolle verfügen.

Die Zugriffsrichtlinie bestimmt die Aktionen, die der Benutzer im Kontext des von Ihnen ausgewählten Service oder der von Ihnen ausgewählten Instanz ausführen kann. Die zulässigen Aktionen werden durch den {{site.data.keyword.cloud_notm}}-Service als Operationen angepasst und definiert, deren Ausführung im Service zulässig ist. Anschließend werden die Aktionen IAM-Benutzerrollen zugeordnet.

Richtlinien ermöglichen die Erteilung von Zugriff auf verschiedenen Ebenen. Einige der Optionen sind die folgenden Zugriffe:

* Zugriff auf alle Serviceinstanzen in Ihrem Konto
* Zugriff auf eine einzelne Serviceinstanz in Ihrem Konto
* Zugriff auf eine bestimmte Ressource innerhalb einer Instanz
* Zugriff auf alle IAM-fähigen Services in Ihrem Konto

Nach der Definition des Bereichs der Zugriffsrichtlinie weisen Sie eine Rolle zu.

Prüfen Sie die folgenden Informationen, in denen die Aktionen erläutert werden, die durch die einzelnen Rollen im {{site.data.keyword.vmwaresolutions_short}}-Service zugelassen werden.

## Plattformmanagementrollen und Berechtigungen
{: #iam-roles}

Plattformmanagementrollen ermöglichen Benutzern die Ausführung von Tasks auf Serviceressourcen auf Plattformebene. Sie können zum Beispiel Benutzerzugriff auf den Service erteilen, Service-IDs erstellen oder löschen, Instanzen erstellen und Instanzen an Anwendungen binden.

Die folgende Tabelle enthält Informationen zu den Aktionen, die den Plattformmanagementrollen zugeordnet sind.

Tabelle 1. Plattformmanagementrollen und zugelassene Aktionen

| Plattformmanagementrolle | Aktionen | Beispielaktionen |
|:----------------- |:----------------- |:----------------- |
| Anzeigeberechtigter (Viewer) | Aktionen unter Schreibschutz | Zusammenfassung der Instanzen anzeigen<br>Details einer Instanz anzeigen |
| Editor (Bearbeiter) | Bestimmte Instanz aktualisieren | ESXi-Server hinzufügen oder entfernen<br>Cluster hinzufügen oder entfernen<br>Services hinzufügen oder entfernen<br>Upgrade einer Instanz auf höhere Version durchführen |
| Operator | Aktionen unter Schreibschutz | Instanzen auflisten<br>Details einer Instanz anzeigen |
| Administrator | Vollständiger Managementzugriff | Neue Instanzen erstellen<br>Instanzen löschen<br>Plattformzugriff anderen Benutzern erteilen|

Für {{site.data.keyword.vmwaresolutions_short}} sind die folgenden Aktionen verfügbar:

Tabelle 2. Aktionsbeschreibungen und erforderliche Rollen

| Aktion | Operation für Service | Rolle |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Neue Instanzen erstellen | Administrator |
| vmware-solutions.instances.delete | Instanzen löschen | Administrator |
| vmware-solutions.instances.view | Instanzen auflisten<br>Details einer Instanz anzeigen | Anzeigeberechtigter, Operator, Editor und Administrator |
| vmware-solutions.instances.update | ESXi-Server hinzufügen oder entfernen<br>Cluster hinzufügen oder entfernen<br>Services hinzufügen oder entfernen<br>Upgrade einer Instanz auf höhere Version durchführen | Editor und Administrator |
| vmware-solutions.account.update | Kontoeinstellungen aktualisieren | Administrator |

## Zugriff für Benutzer verwalten
{: #iam-users}

Sie können dem {{site.data.keyword.cloud_notm}}-Konto neue Benutzer hinzufügen, sodass diese Benutzer die Services und Ressourcen, die für das Konto zur Verfügung gestellt werden, gemeinsam nutzen können. Weitere Informationen finden Sie unter [Benutzer für den Zugriff auf Services und Ressourcen einladen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite).

Sie können außerdem den Zugriff für vorhandene Benutzer verwalten, indem Sie zum Beispiel den vorhandenen Zugriff ändern, einen neuen Zugriff zuweisen oder den zugewiesenen Zugriff prüfen. Zur Verwaltung des Zugriffs für Benutzer müssen Sie der Kontoeigner sein oder die Plattformmanagementrolle **Administrator** besitzen. Weitere Informationen hierzu finden Sie im Abschnitt [Zugriff auf Ressourcen verwalten](/docs/iam?topic=iam-iammanidaccser).

## Vorhandene Instanzen auf IBM Cloud-Konten migrieren
{: #iam-migrate}

Durch die Integration von {{site.data.keyword.vmwaresolutions_short}} in IAM werden Instanzen, die in V2.5 und höheren Releases in Ihrem {{site.data.keyword.cloud_notm}}-Konto bereitgestellt werden, Ihrem Konto automatisch hinzugefügt und durch IAM verwaltet.

Ihre vorhandenen Instanzen, die in V2.4 und früheren Releases bereitgestellt wurden, können Sie auf angegebene {{site.data.keyword.cloud_notm}}-Konten migrieren, um sie mithilfe von IAM zu verwalten. Weitere Informationen finden Sie in den folgenden Abschnitten:
* [vCenter Server-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [vCenter Server with Hybridity Bundle-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [NetApp ONTAP Select-Instanzen aus Versionen vor Version 2.5 auf IBM Cloud-Konten migrieren](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## Zugehörige Links
{: #iam-related}

* [Identität und Zugriff verwalten](/docs/iam?topic=iam-getstarted)
* [Benutzer einladen](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [Was ist IAM?](/docs/iam?topic=iam-iamoverview)

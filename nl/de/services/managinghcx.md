---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

# VMware HCX on IBM Cloud verwalten
{: #managinghcx}

## Auf die HCX on IBM Cloud-Managementkonsolen zugreifen
{: #managinghcx-accessing-consoles}

Um den Service "HCX on {{site.data.keyword.cloud}}" zu verwalten, müssen Sie auf die HCX-Cloudkonsole oder die Administratorkonsole des HCX-Managers zugreifen:
1. Verwenden Sie das virtuelle private Netz der {{site.data.keyword.cloud_notm}}-Infrastruktur oder einen Jump-Server, um den Zugriff auf die IP-Adresse der virtuellen Appliance für den HCX-Manager (kurz "HCX-Manager") zuzulassen. Die IP-Adresse finden Sie auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
2. Klicken Sie zum Zugriff auf die HCX-Cloudkonsole auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" auf **HCX-Cloudkonsole anzeigen** und melden Sie sich dann mit den vCenter Server-Berechtigungsnachweisen an.
3. Klicken Sie zum Zugriff auf die Administratorkonsole des HCX-Managers auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" auf **Verwaltungskonsole des HCX-Managers anzeigen** und melden Sie sich dann mit den Berechtigungsnachweisen für den HCX-Manager an, die auf derselben Servicedetailseite aufgeführt sind.

Weitere Informationen finden Sie unter [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices).

## Updates auf HCX on IBM Cloud anwenden
{: #managinghcx-updates}

HCX on {{site.data.keyword.cloud_notm}} wird mit dem neuesten getesteten Build der VMware Hybrid Cloud Extension-Technologie bereitgestellt. VMware liefert regelmäßig Updates zu diesen Builds aus, die wichtige Fixes und neue Funktionen enthalten. Diese Builds werden automatisch mit Push-Operation an HCX on {{site.data.keyword.cloud}}-Installationen sowie an lokale HCX-Installationen übertragen.

Zum Anwenden von Wartungsfixes, die mit Push-Operation an Ihre Umgebung übertragen wurden, müssen Sie die Administratorkonsole des HCX-Managers in Ihrem lokalen Rechenzentrum und Ihre vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle-Instanz verwenden.

Wenn ein erwartetes Build-Update nicht angezeigt wird, wenn Probleme mit HCX auftreten oder wenn Sie möchten, dass der neueste HCX-Build sofort mit Push-Operation an Ihr System übertragen wird, öffnen Sie ein Support-Ticket. Befolgen Sie dazu die im Abschnitt [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) beschriebenen Schritte.

## Zugehörige Links
{: #managinghcx-related}

* [HCX on {{site.data.keyword.cloud_notm}} - Übersicht](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Glossar der HCX-Begriffe](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [VMware Hybrid Cloud Extension - Übersicht](https://cloud.vmware.com/vmware-hcx)
* [Dokumentation zu VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)

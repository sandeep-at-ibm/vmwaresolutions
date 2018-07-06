---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# VMware HCX on IBM Cloud verwalten

## Auf die HCX on IBM Cloud-Managementkonsolen zugreifen

Um den Service "HCX on {{site.data.keyword.cloud}}" zu verwalten, müssen Sie auf die HCX-Cloudkonsole oder die Administratorkonsole des HCX-Managers zugreifen:
1. Verwenden Sie das virtuelle private Netz der {{site.data.keyword.cloud_notm}}-Infrastruktur oder einen Jump-Server, um den Zugriff auf die IP-Adresse der virtuellen Appliance für den HCX-Manager (kurz "HCX-Manager") zuzulassen. Die IP-Adresse finden Sie auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" in der {{site.data.keyword.vmwaresolutions_short}}-Konsole.
2. Klicken Sie zum Zugriff auf die HCX-Cloudkonsole auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" auf **HCX-Cloudkonsole anzeigen** und melden Sie sich dann mit den vCenter Server-Berechtigungsnachweisen an.
3. Klicken Sie zum Zugriff auf die Administratorkonsole des HCX-Managers auf der Seite mit den Details für den Service "HCX on {{site.data.keyword.cloud_notm}}" auf **Verwaltungskonsole des HCX-Managers anzeigen** und melden Sie sich dann mit den Berechtigungsnachweisen für den HCX-Manager an, die auf derselben Servicedetailseite aufgeführt sind.

Weitere Informationen finden Sie unter [Services für vCenter Server with Hybridity Bundle-Instanzen bestellen, anzeigen und entfernen](../vcenter/vc_hybrid_addingremovingservices.html).

## Updates auf HCX on IBM Cloud anwenden

HCX on {{site.data.keyword.cloud_notm}} wird mit dem neuesten getesteten Build der VMware Hybrid Cloud Extension-Technologie bereitgestellt. VMware liefert regelmäßig Updates zu diesen Builds aus, die wichtige Fixes und neue Funktionen enthalten. Diese Builds werden automatisch mit Push-Operation an HCX on {{site.data.keyword.cloud}}-Installationen sowie an lokale HCX-Installationen übertragen.

Zum Anwenden von Wartungsfixes, die mit Push-Operation an Ihre Umgebung übertragen wurden, müssen Sie die Administratorkonsole des HCX-Managers in Ihrem lokalen Rechenzentrum und Ihre vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle-Instanz verwenden.

Wenn ein erwartetes Build-Update nicht angezeigt wird, wenn Probleme mit HCX auftreten oder wenn Sie möchten, dass der neueste HCX-Build sofort mit Push-Operation an Ihr System übertragen wird, öffnen Sie ein Support-Ticket. Befolgen Sie dazu die im Abschnitt [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html) beschriebenen Schritte.

## Zugehörige Links

* [Überblick zu HCX on {{site.data.keyword.cloud_notm}}](hcx_considerations.html)
* [Glossar der HCX-Begriffe](hcx_glossary.html)
* [VMware Hybrid Cloud Extension overview](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension documentation](https://hcx.vmware.com/#vm-documentation)

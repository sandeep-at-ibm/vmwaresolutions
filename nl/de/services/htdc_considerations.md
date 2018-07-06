---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Überblick zu HyTrust DataControl on IBM Cloud

Der Service "HyTrust DataControl on {{site.data.keyword.cloud}}" bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service kann die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereitstellen. Dies bedeutet, dass alle Verzeichnisse, Ordner oder Dateien innerhalb einer Workload ver- und entschlüsselt werden können.

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde.

## Komponenten von HyTrust DataControl on IBM Cloud

Im Standardcluster wird ein HA-Paar (HA = High Availability; Hochverfügbarkeit) der HTDC-Appliances (HTDC = HyTrust DataControl) im Aktiv-/Aktiv-Modus bereitgestellt. Die HTDC-Appliances beinhalten eine Lizenz zur Bereitstellung der HyTrust KeyControl-Funktionalität für Ihre Workloads.

Jedes Paar der HTDC-Appliances wird auf demselben portierbaren Teilnetz bereitgestellt, das für die virtuellen Maschinen (VMs) für das Management (z. B. für den NSX-Manager, die vCenter Server-Appliances und für Platform Services Controller) angegeben wurde. Die Appliances führen die Weiterleitung über die {{site.data.keyword.cloud_notm}}-BCR (Backend Customer Routers; Back-End-Kundenrouter) durch und werden dem Gateway zugewiesen, das dem Teilnetz für die Management-VMs zugeordnet ist. Darüber hinaus werden die Appliances im Standardspeicher des Standardclusters abgelegt.

## Hinweise zum Entfernen von HyTrust DataControl on IBM Cloud

Vor dem Entfernen des Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" müssen Sie sicherstellen, dass alle Platten von DataControl verschlüsselt oder gesichert wurden. Nachdem Sie den Service entfernt haben, werden die Schlüssel möglicherweise gelöscht, sodass Sie eventuell nicht mehr auf Ihre VMs zugreifen können.

## Zugehörige Links

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} bestellen](htdc_ordering.html)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} verwalten](managinghtcc.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [HyTrust-Website](https://www.hytrust.com/)

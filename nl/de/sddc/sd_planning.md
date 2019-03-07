---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Voraussetzungen und Planung für Cloud Foundation-Instanzen
{: #sd_planning}

Überprüfen Sie die nachstehenden Voraussetzungen, bevor Sie Ihre VMware Cloud Foundation-Instanzen bestellen. Legen Sie der Planung für Ihre Instanz den Standort von {{site.data.keyword.CloudDataCent}} sowie Ihre Anforderungen an die Workloadkapazität und Ihren Bedarf an Services zugrunde.

## Voraussetzungen für IBM Cloud-Konto
{: #sd_planning-account-req}

Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Konto](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Verfügbarkeit des IBM Cloud-Rechenzentrums
{: #sd_planning-dc-availability}

Die Cloud Foundation-Bereitstellung stellt strenge Anforderungen an die physische Infrastruktur. Sie können Instanzen daher nur in {{site.data.keyword.CloudDataCents_notm}} bereitstellen, die diese Anforderungen erfüllen. Die folgenden {{site.data.keyword.CloudDataCents_notm}} stehen für die Bereitstellung von Cloud Foundation zur Verfügung:

Tabelle 1. Verfügbare {{site.data.keyword.CloudDataCents_notm}}- und {{site.data.keyword.cloud_notm}} Bare Metal Server-Konfigurationen für Cloud Foundation-Instanzen

| {{site.data.keyword.CloudDataCent_notm}} | Standort | Region | Serverkonfigurationen |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europa | Skylake, Broadwell |
| CHE01 | Chennai | Asien/Pazifik | Skylake, Broadwell |
| DAL09 | Dallas | NA Süd | Skylake, Broadwell |
| DAL10 | Dallas | NA Süd | Skylake, Broadwell |
| DAL12 | Dallas | NA Süd | Skylake, Broadwell |
| DAL13 | Dallas | NA Süd | Skylake, Broadwell |
| FRA02 | Frankfurt | Europa | Skylake, Broadwell |
| FRA04 | Frankfurt | Europa | Skylake, Broadwell |
| HKG02 | Hongkong | Asien/Pazifik | Skylake, Broadwell |
| LON02 | London | Europa | Skylake, Broadwell |
| LON04 | London | Europa | Skylake, Broadwell |
| LON06 | London | Europa | Skylake, Broadwell |
| MEL01 | Melbourne | Asien/Pazifik | Skylake, Broadwell |
| MEX01 | Queretaro | NA Süd | Skylake, Broadwell |
| MIL01 | Mailand | Europa | Skylake, Broadwell |
| MON01 | Montreal | NA Ost | Skylake, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Broadwell |
| PAR01 | Paris | Europa | Skylake, Broadwell |
| SAO01 | Sao Paulo | Südamerika | Skylake, Broadwell |
| SEO01 | Seoul | Asien/Pazifik | Skylake, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapur | Asien/Pazifik | Skylake, Broadwell |
| SYD01 | Sydney | Asien/Pazifik | Skylake, Broadwell |
| SYD04 | Sydney | Asien/Pazifik | Skylake, Broadwell |
| TOK02 | Tokio | Asien/Pazifik | Skylake, Broadwell |
| TOR01 | Toronto | NA Ost | Skylake, Broadwell |
| WDC04 | Washington, DC | NA Ost | Skylake, Broadwell |
| WDC06 | Washington, DC | NA Ost | Skylake, Broadwell |
| WDC07 | Washington, DC | NA Ost | Skylake, Broadwell |

Je nach Verfügbarkeit und Bestandsangebot ist für {{site.data.keyword.CloudDataCents_notm}} möglicherweise ein Statusanzeiger in der {{site.data.keyword.vmwaresolutions_short}}-Konsole dargestellt, der Ihnen bei der Planung Ihrer Bereitstellungen hilft.

Tabelle 2. Statusanzeiger für {{site.data.keyword.CloudDataCents_notm}} bei der Bestellung von Cloud Foundation-Instanzen

| Status | Statusdetails |
|:------------------------------|:--------------------------------------------------|
| Demnächst verfügbar                   | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Vorübergehend ohne Bestand  | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Eingeschränkter Bestand             | Das {{site.data.keyword.CloudDataCent_notm}} bietet eine begrenzte Verfügbarkeit und die Bestellung kann möglicherweise nicht ausgeführt werden. |

## Sicherung von Managementkomponenten
{: #sd_planning-backup-mgmt-components}

Sie sind für die Erhaltung und Sicherstellung der Verfügbarkeit aller Instanzkomponenten verantwortlich. Es wird empfohlen, die Sicherung oder Hochverfügbarkeit aller Managementkomponenten zu planen. Weitere Informationen finden Sie unter [Komponenten sichern](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services für Cloud Foundation-Instanzen
{: #sd_planning-addon-services}

Sie können für Ihre Instanz auf der Basis Ihrer Anforderungen Add-on-Services bestellen, zum Beispiel für die Disaster-Recovery. Weitere Informationen finden Sie unter [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices).

## Kapazitätsaspekte
{: #sd_planning-capacity-considerations}

Weitere Informationen zur Kapazität finden Sie unter [Skalierungskapazität](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Zugehörige Links
{: #sd_planning-related}

* [Übersicht über Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Cloud Foundation-Instanzen bestellen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Kapazität für Cloud Foundation-Instanzen erweitern und verringern](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Services für Cloud Foundation-Instanzen bestellen, anzeigen und entfernen](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)

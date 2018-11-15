---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Voraussetzungen und Planung für vCenter Server-Instanzen

Überprüfen Sie die nachstehenden Voraussetzungen, bevor Sie Ihre VMware vCenter Server-Instanzen bestellen. Legen Sie der Planung für Ihre Instanz den Standort von {{site.data.keyword.CloudDataCent}} sowie Ihre Anforderungen an die Workloadkapazität und Ihren Bedarf an Add-on-Services zugrunde.

## Voraussetzungen für IBM Cloud-Konto

Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Konto](../vmonic/slaccountrequirement.html).

## Verfügbarkeit des IBM Cloud-Rechenzentrums

Die vCenter Server-Bereitstellung stellt strenge Anforderungen an die physische Infrastruktur. Sie können Instanzen daher nur in {{site.data.keyword.CloudDataCents_notm}} bereitstellen, die diese Anforderungen erfüllen. Die folgenden {{site.data.keyword.CloudDataCents_notm}} stehen für die Bereitstellung von vCenter Server zur Verfügung:

Tabelle 1. Verfügbare {{site.data.keyword.CloudDataCents_notm}} für vCenter Server-Instanzen

| {{site.data.keyword.CloudDataCent_notm}} | Standort | Region | Serveroptionen |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdam | Europa | Skylake, Broadwell |
| CHE01 | Chennai | Asien/Pazifik | Skylake, Broadwell |
| DAL09 | Dallas | NA Süd | Skylake, Broadwell |
| DAL10 | Dallas | NA Süd | Skylake, Broadwell, S (Klein), M (Mittel), L (Groß) |
| DAL12 | Dallas | NA Süd | Skylake, Broadwell |
| DAL13 | Dallas | NA Süd | Skylake, Broadwell |
| FRA02 | Frankfurt | Europa | Skylake, Broadwell, S (Klein), M (Mittel), L (Groß) |
| FRA04 | Frankfurt | Europa | Skylake, Broadwell |
| HKG02 | Hongkong | Asien/Pazifik | Skylake, Broadwell |
| LON02 | London | Europa | Skylake, Broadwell |
| LON04 | London | Europa | Skylake, Broadwell |
| LON06 | London | Europa | Skylake, Broadwell, S (Klein), M (Mittel), L (Groß) |
| MEL01 | Melbourne | Asien/Pazifik | Skylake, Broadwell |
| MEX01 | Queretaro | NA Süd | Skylake, Broadwell |
| MIL01 | Mailand | Europa | Skylake, Broadwell |
| MON01 | Montreal | NA Ost | Skylake, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Broadwell |
| PAR01 | Paris | Europa | Skylake, Broadwell |
| SAO01 | Sao Paulo | Südamerika | Skylake, Broadwell |
| SEO01 | Seoul | Asien/Pazifik | Skylake, Broadwell |
| SJC03 | San Jose | NA West | Skylake, Broadwell, S (Klein), M (Mittel), L (Groß) |
| SJC04 | San Jose | NA West | Skylake, Broadwell |
| SNG01 | Singapur | Asien/Pazifik | Skylake, Broadwell |
| SYD01 | Sydney | Asien/Pazifik | Skylake, Broadwell |
| SYD04 | Sydney | Asien/Pazifik | Skylake, Broadwell |
| TOK02 | Tokio | Asien/Pazifik | Skylake, Broadwell |
| TOR01 | Toronto | NA Ost | Skylake, Broadwell, S (Klein), M (Mittel), L (Groß) |
| WDC04 | Washington, DC | NA Ost | Skylake, Broadwell, S (Klein), M (Mittel), L (Groß) |
| WDC06 | Washington, DC | NA Ost | Skylake, Broadwell |
| WDC07 | Washington, DC | NA Ost | Skylake, Broadwell |

Eine kleine Untergruppe der {{site.data.keyword.CloudDataCents_notm}} bietet für Bare Metal Server die vorkonfigurierten Optionen **S (Klein)**, **M (Mittel)** und **L (Groß)**. Je nach Verfügbarkeit und Bestandsangebot ist für {{site.data.keyword.CloudDataCents_notm}} möglicherweise ein Statusanzeiger in der {{site.data.keyword.vmwaresolutions_short}}-Konsole dargestellt, der Ihnen bei der Planung Ihrer Bereitstellungen hilft.

Tabelle 2. Statusanzeiger für {{site.data.keyword.CloudDataCents_notm}} bei der Bestellung von vCenter Server-Instanzen

| Status | Statusdetails |
|:------------------------------|:--------------------------------------------------|
| Demnächst verfügbar                   | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Vorübergehend ohne Bestand  | Das {{site.data.keyword.CloudDataCent_notm}} ist gegenwärtig nicht verfügbar. |
| Eingeschränkter Bestand             | Das {{site.data.keyword.CloudDataCent_notm}} bietet eine begrenzte Verfügbarkeit und die Bestellung kann möglicherweise nicht ausgeführt werden. |

## Sicherung von Managementkomponenten

Sie sind für die Erhaltung und Sicherstellung der Verfügbarkeit aller Instanzkomponenten verantwortlich. Es wird dringend empfohlen, die Sicherung oder Hochverfügbarkeit aller Managementkomponenten zu planen. Weitere Informationen finden Sie unter [Komponenten sichern](../archiref/solution/solution_backingup.html).

## Services für vCenter Server-Instanzen

Sie können für Ihre Instanz auf der Basis Ihrer Anforderungen Add-on-Services bestellen, zum Beispiel für die Disaster-Recovery. Weitere Informationen finden Sie unter [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](vc_addingremovingservices.html).

## Kapazitätsaspekte

Weitere Informationen zu Kapazitätsaspekten finden Sie unter [Skalierungskapazität](../archiref/solution/solution_scaling.html).

### Zugehörige Links

* [Übersicht über vCenter Server](vc_vcenterserveroverview.html)
* [vCenter Server-Instanzen bestellen](vc_orderinginstance.html)
* [Kapazität für vCenter Server-Instanzen erweitern und verringern](vc_addingremovingservers.html)
* [Services für vCenter Server-Instanzen bestellen, anzeigen und entfernen](vc_addingremovingservices.html)

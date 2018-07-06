---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Voraussetzungen und Planung für VMware vSphere on IBM Cloud

Überprüfen Sie die nachstehenden Voraussetzungen, bevor Sie VMware vSphere on {{site.data.keyword.cloud}} bestellen. Legen Sie der Planung für Ihre VMware vSphere-Cluster den Standort des {{site.data.keyword.CloudDataCent_notm}} sowie Ihre Anforderungen an Workloadkapazität zugrunde.

**Hinweis**: Für die Einrichtung der Umgebung, die Installation und die Konfiguration der verschiedenen VMware-Komponenten nach der Bereitstellung der ESXi-Server sind Sie selbst zuständig. Zu diesen Komponenten gehören u. a. VMware vCenter Server, VMware NSX und VMware vSAN.

## Voraussetzungen für IBM Cloud-Konto

Das {{site.data.keyword.cloud_notm}}-Konto, das Sie verwenden, muss bestimmte Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Voraussetzungen für das {{site.data.keyword.cloud_notm}}-Konto](../vmonic/slaccountrequirement.html).

## Verfügbarkeit des IBM Cloud-Rechenzentrums

Die vSphere-Bereitstellung stellt strenge Anforderungen an die physische Infrastruktur. Sie können Cluster daher nur in {{site.data.keyword.CloudDataCents_notm}} bereitstellen, die diese Anforderungen erfüllen. Die folgenden {{site.data.keyword.CloudDataCent_notm}} stehen für die Bereitstellung von vSphere zur Verfügung.

**Hinweis:** Falls Sie eine vSAN-Komponente auswählen, wird die Liste der Standorte nach Verfügbarkeit von SSD (Solid-State-Platten) gefiltert.

Tabelle 1. Verfügbare {{site.data.keyword.CloudDataCents_notm}} für vSphere-Cluster

| {{site.data.keyword.CloudDataCent_notm}} | Standort | Region |
|:----------------------|:---------|:-------|
| AMS03 | Amsterdam | Europa |
| CHE01 | Chennai | Asien/Pazifik |
| DAL09 | Dallas | NA Süd |
| DAL10 | Dallas | NA Süd |
| DAL12 | Dallas | NA Süd |
| DAL13 | Dallas | NA Süd |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| HKG02 | Hongkong | Asien/Pazifik |
| LON02 | London | Europa |
| LON04 | London | Europa |
| LON06 | London | Europa |
| MEL01 | Melbourne | Asien/Pazifik |
| MEX01 | Queretaro | NA Süd |
| MIL01 | Mailand | Europa |
| MON01 | Montreal | NA Ost |
| OSL01 | Oslo | Europa |
| PAR01 | Paris | Europa |
| SAO01 | Sao Paulo | Südamerika |
| SEO01 | Seoul | Asien/Pazifik |
| SJC03 | San Jose | NA West |
| SJC04 | San Jose | NA West |
| SNG01 | Singapur | Asien/Pazifik |
| SYD01 | Sydney | Asien/Pazifik |
| SYD04 | Sydney | Asien/Pazifik |
| TOK02 | Tokio | Asien/Pazifik |
| TOR01 | Toronto | NA Ost |
| WDC04 | Washington, DC | NA Ost |
| WDC06 | Washington, DC | NA Ost |
| WDC07 | Washington, DC | NA Ost |

## Zugehörige Links

* [Neue vSphere-Cluster bestellen](vs_orderinginstances.html)
* [Vorhandene Cluster skalieren](vs_scalingexistingclusters.html)
* [Außerhalb der Konsole erstellte Cluster skalieren](vs_orderingforclustersoutside.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über Zerto on IBM Cloud

Der Service "Zerto on {{site.data.keyword.cloud}}" integriert Replikations- und Disaster-Recovery-Funktionen in die Bereitstellungsangebote, um Daten in Ihrer virtuellen VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu schützen und wiederherzustellen.

Dieser Service ist nur für Instanzen verfügbar, die in V1.2 (oder höher) bereitgestellt werden. Die aktuell installierte Zerto-Version ist 6.0 Update 3.
{:note}

## Technische Spezifikationen für Zerto on IBM Cloud

Mit dem Service "Zerto on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

Komponenten von Zerto Virtual Replication Appliance (VRA, Appliance für die virtuelle Replikation) werden nur in den Standardclustern bereitgestellt.
{:note}

### VSIs

* Eine Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 Kerne mit je 2.0 GHz
* 4 GB RAM
* Windows Server 2016 Standard Edition (64-Bit)

### Speicher

100-GB-Festplatte (SAN)

### Vernetzung

* Eine primäre private IP-Adresse
* Uplink zum privaten Netz mit 1 Gb/s

### Lizenzen und Gebühren

Lizenz für Zerto Replication V6.0 Update 3

### Zugehörige Links

* [Informationen zu {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/vmonic/prod_overview.html)
* [Zerto on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services/zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services/managingzertodr.html)
* [Verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}} anfordern](/docs/services/vmwaresolutions/services/managing_zerto_services.html)
* [Website "zerto.com"](https://www.zerto.com){:new_window}
* [Technische Dokumentation zu Zerto (englisch)](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über Zerto on IBM Cloud
{: #addingzertodr}

Der Service "Zerto on {{site.data.keyword.cloud}}" integriert Replikations- und Disaster-Recovery-Funktionen in die Bereitstellungsangebote, um Daten in Ihrer virtuellen VMware-Umgebung in {{site.data.keyword.cloud_notm}} zu schützen und wiederherzustellen.

## Vorbereitende Schritte
{: #addingzertodr-req}

* Stellen Sie sicher, dass Ihr {{site.data.keyword.cloud_notm}}-Konto ein Abrechnungskonto ist und dass es mit dem {{site.data.keyword.cloud_notm}}-Infrastrukturkonto verbunden ist, in dem Ihre Instanz bereitgestellt wird. Informationen hierzu finden Sie unter [Abrechnung für Zerto-Replikation](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).
* Dieser Service ist nur für Instanzen verfügbar, die in V1.2 (oder höher) bereitgestellt werden. Die aktuell installierte Zerto-Version ist 6.5 Update 3.

## Technische Spezifikationen für Zerto on IBM Cloud
{: #addingzertodr-specs}

Mit dem Service "Zerto on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen.

Komponenten von Zerto Virtual Replication Appliance (VRA, Appliance für die virtuelle Replikation) werden nur in den Standardclustern bereitgestellt.
{:note}

### Virtuelle Serviceinstanzen
{: #addingzertodr-specs-vsi}

* Eine Virtual Service Instance (VSI) - Zerto Virtual Manager
* 2 Kerne mit je 2.0 GHz
* 4 GB RAM
* Windows Server 2016 Standard Edition (64-Bit)

### Speicher
{: #addingzertodr-specs-storage}

100-GB-Festplatte (SAN)

### Vernetzung
{: #addingzertodr-specs-network}

* VSI
  * Eine primäre private IP-Adresse
  * Uplink zum privaten Netz mit 1 Gb/s
* Virtual Replication Appliances (VRAs)
  * Ein privates portierbares Teilnetz für VRA-Bereitstellung

### Lizenzen und Gebühren
{: #addingzertodr-specs-licenses}

Lizenz für Zerto Replication V6.5 Update 3

## Zugehörige Links
{: #addingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Zerto on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Verwaltete Services für Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Website "zerto.com"](https://www.zerto.com){: external}
* [Technische Dokumentation zu Zerto (englisch)](https://www.zerto.com/myzerto/technical-documentation/){: external}

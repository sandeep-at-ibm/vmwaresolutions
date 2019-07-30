---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HyTrust KeyControl, HTKC, tech specs HTKC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über HyTrust KeyControl on IBM Cloud
{: #htkc_considerations}

Der Service "HyTrust KeyControl on {{site.data.keyword.cloud}}" vereinfacht das Management verschlüsselter Workloads. Dieser Service automatisiert und vereinfacht den Lebenszyklus von Verschlüsselungsschlüsseln, einschließlich Speicherung, Verteilung, Rotation und Widerruf von Schlüsseln. Mithilfe der FIPS 140-2-konformen Verschlüsselung kann der Service ohne großen Aufwand skalierbare Verschlüsselungsschlüssel verwalten.

Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.5 (oder höher) bereitgestellt werden oder für die ein Upgrade auf diese Versionen durchgeführt wurde. Die aktuell installierte HyTrust KeyControl-Version ist 4.3.2.
{:note}

## Technische Spezifikationen für HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-specs}

Mit dem Service "HyTrust KeyControl on {{site.data.keyword.cloud_notm}}" werden folgende Komponenten bestellt und einbezogen:

### HyTrust KeyControl-Appliance
{: #htkc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Festplatte: 20 GB VMDK auf vSAN in konvergiertem Cluster
* Netz: In VLAN-gestütztem privaten portierbaren Netz angeordnet, das für das Management spezifiziert ist

### Hochverfügbarkeit
{: #htkc_considerations-ha}

Standardmäßig werden zwei KeyControl-Appliances in einer Aktiv/Aktiv-Clusterkonfiguration bereitgestellt.

Sie können optional angeben, dass zwei KeyControl-Appliances in einer eigenständigen Konfiguration ohne Cluster bereitgestellt werden sollen.

### Lizenzen und Gebühren
{: #htkc_considerations-licenses}

Für jede Instanzinstallation wird eine HyTrust KeyControl-Lizenz bestellt.

## Hinweise zum Entfernen von HyTrust KeyControl on IBM Cloud
{: #htkc_considerations-remove}

Vor dem Entfernen des Service "HyTrust KeyControl on {{site.data.keyword.cloud_notm}}" müssen Sie alle Clients von der Verwendung von KeyContol entkoppeln. Nachdem Sie den Service entfernt haben, werden die Schlüssel möglicherweise gelöscht, sodass Sie eventuell nicht mehr auf Ihre VMs zugreifen können.

## Zugehörige Links
{: #htkc_considerations-related}

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust-Website](https://www.hytrust.com/){:external}

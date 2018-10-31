---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Übersicht über HyTrust KeyControl on IBM Cloud

Der Service "HyTrust KeyControl on {{site.data.keyword.cloud}}" vereinfacht das Management verschlüsselter Workloads. Dieser Service automatisiert und vereinfacht den Lebenszyklus von Verschlüsselungsschlüsseln, einschließlich Speicherung, Verteilung, Rotation und Widerruf von Schlüsseln. Mithilfe der FIPS 140-2-konformen Verschlüsselung kann der Service ohne großen Aufwand skalierbare Verschlüsselungsschlüssel verwalten. 

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.5 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde.

## Technische Spezifikationen für HyTrust KeyControl on IBM Cloud

Mit dem Service "HyTrust KeyControl on {{site.data.keyword.cloud_notm}}" werden folgende Komponenten bestellt und einbezogen:

### HyTrust KeyControl-Appliance

* CPU: 2 vCPU
* RAM: 8 GB
* Festplatte: 20 GB VMDK auf vSAN in konvergiertem Cluster
* Netz: In VLAN-gestütztem privaten portierbaren Netz angeordnet, das für das Management spezifiziert ist

### Hochverfügbarkeit

Standardmäßig werden zwei KeyControl-Appliances in einer Aktiv/Aktiv-Clusterkonfiguration bereitgestellt.

Sie können optional angeben, dass zwei KeyControl-Appliances in einer eigenständigen Konfiguration ohne Cluster bereitgestellt werden sollen.

### Lizenzen und Gebühren

Für jede Instanzinstallation wird eine HyTrust KeyControl-Lizenz bestellt.

## Hinweise zum Entfernen von HyTrust KeyControl on IBM Cloud

Vor dem Entfernen des Service "HyTrust KeyControl on {{site.data.keyword.cloud_notm}}" müssen Sie alle Clients von der Verwendung von KeyContol entkoppeln. Nachdem Sie den Service entfernt haben, werden die Schlüssel möglicherweise gelöscht, sodass Sie eventuell nicht mehr auf Ihre VMs zugreifen können.

### Zugehörige Links

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} bestellen](htkc_ordering.html)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} verwalten](managinghtkc.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [HyTrust-Website](https://www.hytrust.com/)

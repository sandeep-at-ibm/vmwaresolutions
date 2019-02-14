---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über HyTrust CloudControl on IBM Cloud

Der Service "HyTrust CloudControl on {{site.data.keyword.cloud}}" erzwingt und steuert die Einhaltung der Sicherheitsstandards und stellt Funktionen für die rollenbasierte Zugriffssteuerung (RBAC = Role-Based Access Control) sowie für die Genehmigung und Überprüfung zur Verfügung. In Kombination mit HyTrust DataControl kann der Service sicherstellen, dass virtuelle Maschinen und Workloaddaten eine bestimmte Region, einen bestimmten Cluster oder einen bestimmten ESXi-Server innerhalb von {{site.data.keyword.CloudDataCent_notm}} nicht verlassen.

Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 (oder höher) bereitgestellt werden oder für die ein Upgrade auf diese Versionen durchgeführt wurde. Die aktuell installierte HyTrust CloudControl-Version ist 5.4.0.
{:note}

## Technische Spezifikationen für HyTrust CloudControl on IBM Cloud

Mit dem Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### HyTrust CloudControl-Appliance

* CPU: 4 vCPU
* RAM: 16 GB
* Festplatte: 70 GB VMDK auf vSAN in konvergiertem Cluster
* Netz: In VLAN-gestütztem privaten portierbaren Netz angeordnet, das für das Management spezifiziert ist

### Hochverfügbarkeit

Zwei CloudControl-Appliances werden in einer Aktiv/Passiv-Konfiguration bereitgestellt.

### Lizenzen und Gebühren

Lizenz pro Host: Eine HyTrust CloudControl-Lizenz wird für jeden Host in der Umgebung bestellt.

## Hinweise zum Entfernen von HyTrust CloudControl on IBM Cloud

Vor dem Entfernen des Service "HyTrust CloudControl on {{site.data.keyword.cloud_notm}}" müssen Sie sicherstellen, dass das **Root Password Vaulting** inaktiviert wurde, falls diese Funktion konfiguriert wurde, und dass alle geschützten Hosts aus HyTrust CloudControl gelöscht wurden.

### Zugehörige Links

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services/htcc_ordering.html)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services/managinghtcc.html)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic/faq.html)
* [HyTrust-Website](https://www.hytrust.com/)

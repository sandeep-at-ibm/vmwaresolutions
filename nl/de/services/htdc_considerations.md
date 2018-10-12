---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-18"

---

# Übersicht über HyTrust DataControl on IBM Cloud

Der Service "HyTrust DataControl on {{site.data.keyword.cloud}}" bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service kann die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereitstellen. Dies bedeutet, dass alle Verzeichnisse, Ordner oder Dateien innerhalb einer Workload ver- und entschlüsselt werden können.

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 oder höheren Releases bereitgestellt werden oder für die ein Upgrade auf diese Releases durchgeführt wurde.

## Technische Spezifikationen für HyTrust DataControl on IBM Cloud

Mit dem Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### HyTrust DataControl-Appliance
* CPU: 2 vCPU
* RAM: 8 GB
* Festplatte: 20 GB VMDK auf vSAN in konvergiertem Cluster
* Netz: In VLAN-gestütztem privaten portierbaren Netz angeordnet, das für das Management spezifiziert ist

### Hochverfügbarkeit
Zwei DataControl-Appliances werden in einer Aktiv/Aktiv-Konfiguration bereitgestellt.

### Lizenzen und Gebühren

Lizenz pro Host: Eine HyTrust DataControl-Lizenz wird für jeden Host in der Umgebung bestellt.

## Hinweise zum Entfernen von HyTrust DataControl on IBM Cloud

Vor dem Entfernen des Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" müssen Sie sicherstellen, dass Sie alle Clients von der Verwendung von DataControl entkoppelt haben. Nachdem Sie den Service entfernt haben, werden die Schlüssel möglicherweise gelöscht, sodass Sie eventuell nicht mehr auf Ihre VMs zugreifen können.

### Zugehörige Links

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} bestellen](htdc_ordering.html)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} verwalten](managinghtdc.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [HyTrust-Website](https://www.hytrust.com/)

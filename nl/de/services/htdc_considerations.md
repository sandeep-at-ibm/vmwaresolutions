---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über HyTrust DataControl on IBM Cloud
{: #htdc_considerations}

Der Service "HyTrust DataControl on {{site.data.keyword.cloud}}" bietet eine starke Verschlüsselung mit integriertem Schlüsselmanagement, um Workloads über ihren gesamten Lebenszyklus hinweg zu sichern. Der Service stellt die Verschlüsselung sowohl auf Betriebssystemebene als auch auf Datenebene bereit. Auf diese Weise können alle Verzeichnisse, Ordner oder Dateien in einer Workload verschlüsselt und entschlüsselt werden.

Dieser Service ist nur für Instanzen verfügbar, auf denen vSphere 6.5 ausgeführt wird und die in V2.3 (oder höher) bereitgestellt werden oder für die ein Upgrade auf diese Versionen durchgeführt wurde. Die aktuell installierte HyTrust DataControl-Version ist 4.2.1.
{:note}

## Technische Spezifikationen für HyTrust DataControl on IBM Cloud
{: #technical-specifications-for-hytrust-datacontrol-on-ibm-cloud}

Mit dem Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### HyTrust DataControl-Appliance
{: #htdc_considerations-appliance}

* CPU: 2 vCPU
* RAM: 8 GB
* Festplatte: 20 GB VMDK auf vSAN in konvergiertem Cluster
* Netz: In VLAN-gestütztem privaten portierbaren Netz angeordnet, das für das Management spezifiziert ist

### Hochverfügbarkeit
{: #htdc_considerations-ha
}
Zwei DataControl-Appliances werden in einer Aktiv/Aktiv-Konfiguration bereitgestellt.

### Lizenzen und Gebühren
{: #htdc_considerations-licenses}

Lizenz pro Host: Eine HyTrust DataControl-Lizenz wird für jeden Host in der Umgebung bestellt.

## Hinweise zum Entfernen von HyTrust DataControl on IBM Cloud
{: #htdc_considerations-remove}

Vor dem Entfernen des Service "HyTrust DataControl on {{site.data.keyword.cloud_notm}}" müssen Sie alle Clients von der Verwendung von DataControl entkoppeln. Nachdem Sie den Service entfernt haben, werden die Schlüssel möglicherweise gelöscht, sodass Sie eventuell nicht mehr auf Ihre VMs zugreifen können.

## Zugehörige Links
{: #htdc_considerations-related}

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust-Website](https://www.hytrust.com/)

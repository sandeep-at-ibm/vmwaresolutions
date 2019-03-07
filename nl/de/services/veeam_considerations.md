---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über Veeam on IBM Cloud
{: #veeam_considerations}

Der Service "Veeam on {{site.data.keyword.cloud}}" wird nahtlos und direkt in Ihre VMware-Hypervisoren integriert und unterstützt so die Hochverfügbarkeit in Ihrem Unternehmen. Dieser Service stellt Wiederherstellungspunkte und Zeitziele für Ihre Anwendungen und Daten bereit. Die Wiederherstellungspunkte und Zeitziele können in weniger als 15 Minuten nach Abschluss der Konfiguration bereitgestellt werden. Durch die Verwendung dieses Service steuern Sie die Sicherung und Wiederherstellung aller virtuellen Maschinen (VMs) für Ihre Infrastruktur direkt über die Veeam-Konsole.

Dieser Service ist nur für Instanzen verfügbar, die in V1.8 (oder höher) bereitgestellt werden. Die aktuell installierte Veeam-Version ist 9.5u3.
{:note}

## Technische Spezifikationen für Veeam on IBM Cloud
{: #technical-specifications-for-veeam-on-ibm-cloud}

Mit dem Service "Veeam on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### Virtuelle Serverinstanzen (VSIs)
{: #veeam_considerations-specs-vsi}

* Einzelne VSI mit Veeam Backup and Replication 9.5 OS Add-on
* Windows Server 2016 Standard Edition (64-Bit)
* 4 Kerne mit je 2.0 GHz
* 8 GB RAM
* Uplink zum privaten Netz mit 1 Gb/s
* 100-GB-Festplatte (SAN)

### Speicher für Sicherungen
{: #veeam_considerations-specs-storage}

* Endurance iSCSI-Speicher (2000, 4000, 8000 oder 12000 GB)
* Speicherleistung (0,25, 2 oder 4 IOPS/GB)

### Vernetzung
{: #veeam_considerations-specs-networking}

Eine primäre private IP-Adresse.

### Lizenzen und Gebühren
{: #veeam_considerations-specs-licenses}

Veeam Backup and Replication 9.5 Enterprise Plus (Lizenz für 10, 25, 50, 100 oder 200 VMs).

### Management
{: #veeam_considerations-specs-mgmt}

Managementsicherungen werden standardmäßig mit bis zu fünf VMs und 2000 GB Speicher konfiguriert.

## Hinweise zur Installation von Veeam on IBM Cloud
{: #veeam_considerations-install}

Das Speicherrepository und der Veeam-Server befinden sich im ursprünglichen Pod und Rechenzentrum. Aus diesem Grund kann sich die Leistung der Sicherungsoperationen für ferne Cluster verschlechtern.

## Hinweise zum Entfernen von Veeam on IBM Cloud
{: #veeam_considerations-remove}

Durch das Entfernen des Veeam on {{site.data.keyword.cloud_notm}}-Service werden alle Sicherungen gestoppt und alle vorherigen Sicherungen gelöscht. Die Sicherungen der Management-VMs werden gestoppt und der Löschvorgang für vorherige Sicherungen kann nicht rückgängig gemacht werden. Wenn die Management-VMs beschädigt sind, können sie nicht wiederhergestellt werden.

## Zugehörige Links
{: #veeam_considerations-related}

* [Veeam on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Verwaltete Services für Veeam on {{site.data.keyword.cloud_notm}} anfordern](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam-Website](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

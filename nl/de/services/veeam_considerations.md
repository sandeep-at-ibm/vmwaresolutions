---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Übersicht über Veeam on IBM Cloud

Der Service "Veeam on {{site.data.keyword.cloud}}" wird nahtlos und direkt in Ihre VMware-Hypervisoren integriert und unterstützt so die Hochverfügbarkeit in Ihrem Unternehmen. Dieser Service kann Wiederherstellungspunkte und Zeitziele für Ihre Anwendungen und Daten bereitstellen. Die Wiederherstellungspunkte und Zeitziele können in weniger als 15 Minuten nach Abschluss der Konfiguration bereitgestellt werden. Durch die Verwendung dieses Service können Sie die Sicherung und Wiederherstellung aller virtuellen Maschinen (VMs) für Ihre Infrastruktur direkt über die Veeam-Konsole steuern.

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, die in V1.8 oder höheren Releases bereitgestellt werden.

## Technische Spezifikationen für Veeam on IBM Cloud

Mit dem Service "Veeam on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### Virtuelle Serverinstanzen (VSIs)

* Einzelne VSI mit Veeam Backup and Replication 9.5 OS Add-on
* Windows Server 2016 Standard Edition (64-Bit)
* 4 Kerne mit je 2.0 GHz
* 8 GB RAM
* Uplink zum privaten Netz mit 1 Gb/s
* 100-GB-Festplatte (SAN)

### Speicher für Sicherungen

* Endurance iSCSI-Speicher (2000, 4000, 8000 oder 12000 GB)
* Speicherleistung (0,25, 2 oder 4 IOPS/GB)

### Vernetzung

Eine primäre private IP-Adresse.

### Lizenzen und Gebühren

Veeam Backup and Replication 9.5 Enterprise Plus (Lizenz für 10, 25, 50, 100 oder 200 VMs).

### Management

Managementsicherungen werden standardmäßig mit bis zu fünf VMs und 2000 GB Speicher konfiguriert.

## Hinweise zur Installation von Veeam on IBM Cloud

Das Speicherrepository und der Veeam-Server befinden sich im ursprünglichen Pod und Rechenzentrum. Aus diesem Grund kann sich die Leistung der Sicherungsoperationen für ferne Cluster verschlechtern.

## Hinweise zum Entfernen von Veeam on IBM Cloud

Beachten Sie vor dem Entfernen des Service "Veeam on {{site.data.keyword.cloud_notm}}", dass hierdurch alle Sicherungen (inklusive der Sicherung der Management-VMs) gestoppt und alle vorherigen Sicherungen gelöscht werden (der Löschvorgang ist irreversibel). Falls die Management-VMs später beschädigt werden, ist ihre Wiederherstellung nicht möglich.

### Zugehörige Links

* [Veeam on {{site.data.keyword.cloud_notm}} bestellen](veeam_ordering.html)
* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](managingveeam.html)
* [Verwaltete Services für Veeam on {{site.data.keyword.cloud_notm}} anfordern](managing_veeam_services.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Veeam-Website](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

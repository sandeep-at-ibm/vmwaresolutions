---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Überblick zu Veeam on IBM Cloud

Der Service "Veeam on {{site.data.keyword.cloud}}" wird nahtlos und direkt in Ihre VMware-Hypervisoren integriert und fördert so die Hochverfügbarkeit in Ihrem Unternehmen. Dieser Service kann Wiederherstellungspunkte und Zeitziele für Ihre Anwendungen und Daten bereitstellen. Die Wiederherstellungspunkte und Zeitziele können innerhalb von weniger als 15 Minuten nach Abschluss der Konfiguration bereitgestellt werden. Durch die Verwendung dieses Service können Sie die Sicherung und Wiederherstelung aller virtuellen Maschinen für Ihre Infrastruktur direkt von der Veeam-Konsole aus steuern.

**Verfügbarkeit**: Dieser Service ist nur für Instanzen verfügbar, die in V1.8 oder höheren Releases bereitgestellt werden.

## Komponenten von Veeam on IBM Cloud

Mit dem Service "Veeam on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:
* 1 virtuelle Serverinstanz von Windows Server 2016 mit einer primären privaten IP-Adresse und 1-GbE-Schnittstelle
* {{site.data.keyword.cloud_notm}} Endurance Block Storage mit der von Ihnen bei der Bestellung des Service ausgewählten Größe und Leistung

## Hinweise zur Installation von Veeam on IBM Cloud

* Der Service sichert die folgenden Managementkomponenten:
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **Nur bei Cloud Foundation-Instanzen**: VMware SDDC Manager
  - **Nur bei vCenter Server-Instanzen mit HA-AD/DNS**: HA-Paar von AD/DNS-Servern

* Die Konfigurationen der ESXi-Server werden vom Service "Veeam on {{site.data.keyword.cloud_notm}}" nicht gesichert.

* Die Konfigurationen für den NSX-Controller und die NSX-Edge werden standardmäßig täglich mit dem NSX-Manager mit bis zu 14 Wiederherstellungspunkten gesichert. Für eine vollständige Wiederherstellung der NSX-Konfigurationen müssen Sie ein {{site.data.keyword.cloud_notm}}-Support-Ticket erstellen, da die Sicherungen der NSX-Konfigurationen im internen Speicher von {{site.data.keyword.vmwaresolutions_full}} abgelegt werden. Weitere Informationen zum Verwalten der NSX-Konfigurationssicherungen unter Verwendung des NSX-Managers finden Sie in den [technischen Anweisungen für VMware](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html).
* Das Repository für den Speicher und der Veeam-Server befinden sich im ursprünglichen Pod und Rechenzentrum. Aus diesem Grund kann sich die Leistung der Sicherungsoperationen für ferne Cluster verschlechtern.

## Hinweise zum Entfernen von Veeam on IBM Cloud

Beachten Sie vor dem Entfernen des Service "Veeam on {{site.data.keyword.cloud_notm}}", dass hierdurch alle Sicherungen (inklusive der Sicherung der Management-VMs) gestoppt werden und alle vorherigen Sicherungen gelöscht werden (der Löschvorgang ist irreversibel). Falls die Management-VMs später beschädigt werden, ist ihre Wiederherstellung nicht möglich.

## Zugehörige Links

* [Veeam on {{site.data.keyword.cloud_notm}} bestellen](veeam_ordering.html)
* [Veeam on {{site.data.keyword.cloud_notm}} verwalten](managingveeam.html)
* [Verwaltete Services für Veeam on {{site.data.keyword.cloud_notm}} anfordern](managing_veeam_services.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Veeam-Website](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate VA, FortiGate Virtual Appliance, tech specs FortiGate VA

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations}

Der Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud}}" stellt ein Paar von FortiGate Virtual Appliances für Ihre Umgebung bereit, mit dessen Hilfe Sie durch die Implementierung von kritischen Sicherheitsmaßnahmen in Ihrer virtuellen Infrastruktur Risiken verringern können.

Sie können je nach Bedarf mehrere Instanzen dieses Service installieren. Zur Verwaltung dieses Service können Sie FortiOS Web Client oder die Befehlszeilenschnittstelle über SSH verwenden.

Dieser Service ist nur für Instanzen verfügbar, die in V2.0 oder höheren Releases bereitgestellt werden. Die aktuell installierte Serviceversion ist 6.0.3.
{:note}

## Technische Spezifikationen für FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-specs}


Mit dem Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" werden die folgenden Komponenten bestellt und einbezogen:

### Virtuelle Maschinen
{: #fortinetvm_considerations-specs-vms}

* Alle Optionen beinhalten ein hoch verfügbares Paar virtueller Maschinen
* 2, 4 oder 8 vCPUs pro virtuelle Maschine, abhängig von der Bereitstellungsgröße und dem Subskriptionstyp
* 4, 6 oder 12 GB RAM pro virtuelle Maschine, abhängig von der Bereitstellungsgröße und dem Subskriptionstyp

### Hochverfügbarkeit
{: #fortinetvm_considerations-specs-ha}

Zwei virtuelle Maschinen (VMs) werden bereitgestellt und für die Hochverfügbarkeitskonfiguration oder die Konfiguration von Virtual Router Redundancy Protocol (VRRP) vorbereitet.

### Vernetzung
{: #fortinetvm_considerations-specs-network}

Der Zugriff auf die FortiGate®-Konsole erfolgt über das private Managementnetz.

### Lizenz und Gebühren
{: #fortinetvm_considerations-specs-license}

Lizenzgebühren für jede virtuelle Maschine werden in jedem Abrechnungszyklus abhängig von der ausgewählten Bereitstellungsgröße und dem Lizenzierungsmodell für die monatliche Subskription berechnet.

Sie können die Lizenzierungsstufe nach der Serviceinstallation nicht mehr ändern. Wenn Sie die Lizenzstufe ändern möchten, müssen Sie den vorhandenen Service entfernen und den Service anschließend mit einer anderen Lizenzoption erneut installieren.
{:important}

## Hinweise zur Installation von FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-install}

Lesen Sie die folgenden Hinweise, bevor Sie den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" installieren:
* Die FortiGate-VMs werden nur im Standardcluster bereitgestellt.
* 100% der CPU und des RAM für die zwei FortiGate-VMs sind ebenfalls reserviert, weil sich diese virtuellen Maschinen auf der Datenebene der Netzkommunikation befinden und es entscheidend ist, dass für sie noch Ressourcen verfügbar sind.

  Mit der folgenden Formel können Sie die CPU- und RAM-Reservierung für eine einzelne FortiGate-VM berechnen:
   * `CPU-Reservierung = CPU-Geschwindigkeit des ESXi-Servers * vCPU-Anzahl`
   * `RAM-Reservierung = RAM-Größe`
* Wenn Sie ein HA-Paar von FortiGate Virtual Appliances in Ihrer Instanz bereitstellen, werden im NSX Edge Services Gateway (ESG) für das Management SNAT- und Firewallregeln zusammen mit statischen Routen in FortiGate Virtual Appliances definiert, damit zur Lizenzaktivierung sowie zum Abruf der neuesten Sicherheitsrichtlinien und Inhalt abgehender HTTPS-Datenverkehr aus Ihrer Instanz in das öffentliche Netz zulässig ist.
* Sie können die Lizenzstufe nach der Serviceinstallation nicht mehr ändern. Wenn Sie die Lizenzstufe ändern möchten, müssen Sie den vorhandenen Service entfernen und den Service anschließend mit einer anderen Lizenzoption erneut installieren.
* Die folgenden Voraussetzungen müssen zur Vermeidung von Fehlern bei FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} erfüllt sein:
   * Es sind mindestens zwei aktive ESXi-Server für die beiden FortiGate-VMs verfügbar, die unter Berücksichtigung der Anti-Affinitäts-Regel bereitgestellt werden, dass sich die virtuellen Maschinen auf separaten Servern befinden müssen.
   * Auf den beiden aktiven ESXi-Servern sind ausreichend Ressourcen verfügbar, damit eine FortiGate-VM auf jedem ESXi-Server mit einer CPU- und RAM-Reservierung von 100% gehostet werden kann.
   * VMware vSphere HA besitzt ausreichend Ressourcen für das Hosting von zwei Fortigate-VMs mit 100% CPU und RAM.

  Aufgrund dieser Voraussetzungen müssen Sie den für FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} erforderlichen Speicherplatz sorgfältig planen. Fügen Sie bei Bedarf vor der Bestellung von FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 1 bis 2 ESXi-Server zu Ihrer Instanz hinzu und/oder reduzieren Sie die CPU-Reservierung der vSphere-Hochverfügbarkeit für das Failover.

## FortiGate Virtual Appliance on IBM Cloud - Bestellbeispiel
{: #fortinetvm_considerations-example}

Sie bestellen eine VMware vCenter Server-Instanz des Typs **S (Klein)** mit 2 ESXi-Servern und der folgenden Konfiguration: 16 Kerne mit 2,10 GHz und jeweils 128 GB RAM. Für FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} wählen Sie den Typ **L (Groß)** mit 8 vCPUs und 12 GB RAM als Bereitstellungsgröße sowie ein beliebiges Lizenzmodell aus.

In diesem Fall benötigt eine einzelne FortiGate-VM auf jedem Server Folgendes:
* 2,1 GHz * 8 vCPU = 16,8 GHz CPU sowie
* 12 GB RAM

Insgesamt ergibt dies 33,6 GHz für die CPU und 24 GB RAM für beide virtuellen Maschinen für FortiGate.

Jeder ESXi-Server hat eine Kapazität von 16 Kernen * 2,1 GHz, also 33,6 GHz. Die ersten beiden Anforderungen sind somit erfüllt, wenn beide Server aktiv sind und auf jedem Server mindestens 16,8 GHz CPU und 12 GB RAM verfügbar sind.

Die vSphere-Hochverfügbarkeit reserviert jedoch standardmäßig 50% von CPU und RAM für das Failover auf vCenter Server-Instanzen, die anfänglich mit 2 ESXi-Servern bereitgestellt werden, so dass nur Folgendes verfügbar ist:

`50% von 2 * 16 Kernen * 2,1 GHz = 33,6 GHz verfügbar`

Da auf den ESXi-Servern weitere Workloads wie beispielsweise VMware vCenter Server, VMware NSX Controller oder VMware NSX Edge vorhanden sind, wird bei Verwendung dieser Ressourcen die dritte Voraussetzung nicht erfüllt. Der Grund hierfür ist, dass für die beiden FortiGate-VMs 33,6 GHz CPU und 24 GB RAM erforderlich sind.

In diesem Fall schlägt die Installation von FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} fehl, sofern nicht mindestens ein ESXi-Server zur Umgebung hinzugefügt wird und die Failover-Reservierungen der vSphere-Hochverfügbarkeit entsprechend aktualisiert werden, damit ausreichend Ressourcen für die beiden FortiGate-VMs gewährleistet sind.

Wenn zur Ausführung des Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" zusätzliche Ressourcen benötigt werden, können Sie weitere ESXi-Server hinzufügen, bevor Sie den Service installieren.

## Hinweise zum Entfernen von FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_considerations-remove}

Bevor Sie den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie sicherstellen, dass die bestehende Konfiguration für FortiGate Virtual Appliances ordnungsgemäß entfernt wurde. Insbesondere muss der Netzverkehr an FortiGate Virtual Appliances vorbei und nicht durch FortiGate Virtual Appliances geleitet werden. Andernfalls kann der vorhandene Datenverkehr an Ihre Umgebung beeinträchtigt werden.

## Zugehörige Links
{: #fortinetvm_considerations-related}

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} verwalten](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [Kontaktaufnahme mit dem IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Häufig gestellte Fragen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet-Website](https://www.fortinet.com/){:external}
* [Dokumentbibliothek zu Fortinet](https://docs.fortinet.com/product/fortigate/6.2){:external}

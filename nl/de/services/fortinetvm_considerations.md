---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Überblick zu FortiGate Virtual Appliance on IBM Cloud

Der Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud}}" stellt ein Paar von FortiGate Virtual Appliances für Ihre Umgebung bereit, mit dessen Hilfe Sie durch die Implementierung von kritischen Sicherheitsmaßnahmen in Ihrer virtuellen Infrastruktur Risiken verringern können.

Sie können je nach Bedarf mehrere Instanzen dieses Service installieren. Zur Verwaltung dieses Service können Sie FortiOS Web Client oder die Befehlszeilenschnittstelle über SSH verwenden.

**Verfügbarkeit**: Dieser Service ist nur für Instanzen verfügbar, die in V2.0 und höheren Releases bereitgestellt werden.

## Komponenten von FortiGate Virtual Appliance on IBM Cloud

Wenn Sie den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" bestellen, wird ein Paar von FortiGate Virtual Appliances mit folgenden Features bereitgestellt: 
* 1 Netzschnittstelle, die für das Managementnetz konfiguriert ist,
* 9 Netzschnittstellen, die Sie nach Bedarf konfigurieren können, um den Datenverkehr zu schützen.

Die FortiGate Virtual Appliances sind nicht als Hochverfügbarkeits-Paar (High Availability, HA) vorkonfiguriert. Nach der Bereitstellung können Sie Hochverfügbarkeitseinstellungen konfigurieren, die entsprechend Ihren Anforderungen Virtual Router Redundancy Protocol (VRRP) und FortiGate Cluster Protocol (FGCP) umfassen.

## Hinweise zur Installation von FortiGate Virtual Appliance on IBM Cloud

Lesen Sie die folgenden Hinweise, bevor Sie den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" installieren:
* Die FortiGate-VMs werden nur im Standardcluster bereitgestellt.
* Basierend auf der von Ihnen getroffenen Auswahl für Bereitstellungsgröße und Lizenzmodell werden die beiden FortiGate-VMs mit einer der folgenden Konfigurationen bereitgestellt:
    * S (Klein): 2 vCPUs / 4 GB RAM
    * M (Mittel): 4 vCPUs / 6 GB RAM
    * L (Groß): 8 vCPUs / 12 GB RAM

  Außerdem sind 100% der CPU und des RAM für die zwei FortiGate-VMs ebenfalls reserviert, weil sich diese virtuellen Maschinen auf der Datenebene der Netzkommunikation befinden und es entscheidend ist, dass für sie noch Ressourcen verfügbar sind.

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

Sie bestellen eine VMware vCenter Server-Instanz des Typs **S (Klein)** mit 2 ESXi-Servern und der folgenden Konfiguration: 16 Kerne mit 2,10 GHz und jeweils 128 GB RAM. Für FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} wählen Sie den Typ **L (Groß)** mit 8 vCPUs und 12 GB RAM als Bereitstellungsgröße sowie ein beliebiges Lizenzmodell aus.

In diesem Fall benötigt eine einzelne FortiGate-VM auf jedem Server Folgendes:
* 2,1 GHz * 8 vCPU = 16,8 GHz CPU sowie
* 12 GB RAM

Insgesamt ergibt dies 33,6 GHz für die CPU und 24 GB RAM für beide virtuellen Maschinen für FortiGate.

Jeder ESXi-Server hat eine Kapazität von 16 Kernen * 2,1 GHz, also 33,6 GHz. Die ersten beiden Anforderungen sind somit erfüllt, wenn beide Server aktiv sind und auf jedem Server mindestens 16,8 GHz CPU und 12 GB RAM verfügbar sind.

Die vSphere-Hochverfügbarkeit reserviert jedoch standardmäßig 50% von CPU und RAM für das Failover auf vCenter Server-Instanzen, die anfänglich mit 2 ESXi-Servern bereitgestellt werden, so dass nur Folgendes verfügbar ist:

`50% von 2 * 16 Kernen * 2,1 GHz = 33,6 GHz verfügbar`

Da auf den ESXi-Servern weitere Workloads wie beispielsweise IBM CloudDriver, VMware NSX Controller oder VMware NSX Edge vorhanden sind, wird bei Verwendung dieser Ressourcen die dritte Voraussetzung nicht erfüllt. Der Grund hierfür ist, dass für die beiden FortiGate-VMs 33,6 GHz CPU und 24 GB RAM erforderlich sind.

In diesem Fall schlägt die Installation von FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} fehl, sofern nicht mindestens ein ESXi-Server zur Umgebung hinzugefügt wird und die Failoverreservierungen der vShpere-Hochverfügbarkeit entsprechend aktualisiert werden, damit ausreichend Ressourcen für die beiden FortiGate-VMs gewährleistet sind.

Wenn zur Ausführung des Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" zusätzliche Ressourcen benötigt werden, können Sie weitere ESXi-Server hinzufügen, bevor Sie den Service installieren.

## Hinweise zum Entfernen von FortiGate Virtual Appliance on IBM Cloud

Bevor Sie den Service "FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie sicherstellen, dass die bestehende Konfiguration für FortiGate Virtual Appliances ordnungsgemäß entfernt wurde. Insbesondere muss der Netzverkehr an FortiGate Virtual Appliances vorbei und nicht durch FortiGate Virtual Appliances geleitet werden. Andernfalls kann der vorhandene Datenverkehr an Ihre Umgebung beeinträchtigt werden.

## Zugehörige Links

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} bestellen](fortinetvm_ordering.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} verwalten](managingfortinetvm.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [Fortinet-Website](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}

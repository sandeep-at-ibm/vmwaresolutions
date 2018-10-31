---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Übersicht über F5 on IBM Cloud

Der Service "F5 on {{site.data.keyword.cloud}}" (F5 BIG-IP® Virtual Edition) stellt lokal und global einsetzbare intelligente Services für den L4-L7-Lastausgleich, einen stabilen Firewallschutz für Netze und Webanwendungen sowie einen sicheren und eingebundenen Anwendungszugriff zur Verfügung.

Sie können je nach Bedarf mehrere Instanzen dieses Service installieren.

**Verfügbarkeit:** Dieser Service ist nur für Instanzen verfügbar, die in V1.9 und höheren Releases bereitgestellt werden.

## Technische Spezifikationen für F5 on IBM Cloud

Die folgenden Komponenten werden mit dem Service "F5 on {{site.data.keyword.cloud_notm}}" einbezogen:

### Virtuelle Maschinen
* 2 virtuelle Maschinen (VMs) mit allen verfügbaren Optionen.
* 2, 4 oder 8 vCPUs pro virtuelle Maschine, abhängig von der Lizenzierungsoption.
* 4, 8 oder 16 GB RAM pro virtuelle Maschine, abhängig von der Lizenzierungsoption.

### Vernetzung
* Private Virtual Extensible LAN (VXLAN) für HA-Synchronisation (HA – High Availability).
* Zugriff auf Konsole für Traffic Management Shell (TMSH) und Management über privates Managementnetz.

### Lizenzen und Gebühren
Lizenzgebühren für jede VM werden in jedem Abrechnungszyklus abhängig von der Lizenzierungsoption (Gut, Besser oder Optimal) und der ausgewählten Bandbreite berechnet.

**Wichtig:** Sie können die Lizenzierungsstufe nach der Serviceinstallation nicht ändern. Wenn Sie die Lizenzstufe ändern möchten, müssen Sie den vorhandenen Service entfernen und den Service anschließend mit einer anderen Lizenzoption erneut installieren.

## Installationsaspekte für F5 on IBM Cloud

Lesen Sie vor der Installation des Service "F5 on {{site.data.keyword.cloud_notm}}" folgende Hinweise.

Basierend auf dem von Ihnen ausgewählten Lizenzmodell und der ausgewählten Bandbreite werden zwei virtuelle Maschinen für BIG-IP VE mit der folgenden Konfiguration bereitgestellt:

Tabelle 1. CPU- und RAM-Bereitstellungen für unterschiedliche Bandbreiten- und Lizenzmodellauswahl

| Maximale Bandbreite | Lizenzmodell: Gut | Lizenzmodell: Besser | Lizenzmodell: Optimal |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 MB/s           | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 200 MB/s          | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 1 Gb/s            | 2 vCPU, 4 GB RAM    | 4 vCPU, 8 GB RAM      | 8 vCPU, 16 GB RAM   |
| 3 Gb/s            | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |
| 5 Gb/s            | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |
| 10 Gb/s           | 8 vCPU, 16 GB RAM   | 8 vCPU, 16 GB RAM     | 8 vCPU, 16 GB RAM   |

**Hinweise:**

* F5 BIG–IP begrenzt den Appliance-Durchsatz aufgrund der von Ihnen ausgewählten maximalen Bandbreite. Da die Netzleistung durch viele Faktoren beeinflusst wird, sind möglicherweise nicht alle Konfigurationen und Topologien in der Lage, die ausgewählte maximale Bandbreite zu erzielen.
* Das Hochverfügbarkeitspaar (HA-Paar) der virtuellen Maschinen für BIG-IP VE wird nur im Standardcluster bereitgestellt.

  Außerdem sind 100% der CPU und des RAM für die zwei virtuellen Maschinen für BIG-IP VE ebenfalls reserviert, weil sich diese virtuellen Maschinen auf der Datenebene der Netzkommunikation befinden und es entscheidend ist, dass für sie immer Ressourcen verfügbar sind.

  Mit der folgenden Formel können Sie die CPU- und RAM-Reservierung für eine einzelne virtuelle Maschine für BIG-IP VE berechnen:

  `CPU-Reservierung = CPU-Geschwindigkeit des ESXi-Servers * vCPU-Anzahl` (aus Tabelle 1)

  `RAM-Reservierung = RAM-Größe` (aus Tabelle 1)

### Hinweise zu Planung
Die folgenden Voraussetzungen müssen zur Vermeidung von Fehlern bei F5 on {{site.data.keyword.cloud_notm}} erfüllt sein:
* Es sind mindestens zwei aktive ESXi-Server für die beiden virtuellen Maschinen für BIG-IP VE verfügbar, die unter Berücksichtigung der Anti-Affinitäts-Regel bereitgestellt werden, dass sich die virtuellen Maschinen auf separaten Servern befinden müssen.
* Auf den beiden aktiven ESXi-Servern sind ausreichend Ressourcen verfügbar, damit eine VM für BIG-IP VE auf jedem ESXi-Server mit einer CPU- und RAM-Reservierung von 100% gehostet werden kann.
* VMware vSphere HA besitzt ausreichend Ressourcen für das Hosting von zwei VMs für BIG-IP mit 100% CPU und RAM.

Aufgrund dieser Voraussetzungen müssen Sie den für F5 on {{site.data.keyword.cloud_notm}} erforderlichen Speicherplatz planen. Fügen Sie erforderlichenfalls vor der Bestellung von F5 on {{site.data.keyword.cloud_notm}} 1 bis 2 ESXi-Server zu Ihrer Instanz hinzu und/oder reduzieren Sie die CPU-Reservierung der vSphere-Hochverfügbarkeit für das Failover.

## F5 on IBM Cloud - Bestellbeispiel

Sie bestellen eine VMware vCenter Server-Instanz des Typs **S (Klein)** mit 2 ESXi-Servern und der folgenden Konfiguration: sechzehn Kerne mit 2,10 GHz und jeweils 128 GB RAM. Für F5 on {{site.data.keyword.cloud_notm}} wählen Sie das Lizenzmodell **Optimal** und einen Wert von 5 Gb/s für **Maximale Bandbreite** aus.

In diesem Fall benötigt eine einzelne virtuelle Maschine für BIG-IP auf jedem Server Folgendes:
* 2,1 GHz * 8 vCPU = 16,8 GHz CPU sowie
* 16 GB RAM

Insgesamt ergibt dies 33,6 GHz für die CPU und 32 GB RAM für beide virtuellen Maschinen für BIG-IP.

Jeder ESXi-Server hat eine Kapazität von 16 Kernen * 2,1 GHz, also 33,6 GHz. Die ersten beiden Anforderungen sind somit erfüllt, wenn beide Server aktiv sind und auf jedem Server mindestens 16,8 GHz CPU und 16 GB RAM verfügbar sind.

Die vSphere-Hochverfügbarkeit reserviert jedoch standardmäßig 50 Prozent von CPU und RAM für das Failover auf vCenter Server-Instanzen, die anfänglich mit 2 ESXi-Servern bereitgestellt wurden. Für dieses Beispiel ist das Folgende verfügbar:

`50% von 2 * 16 Kernen * 2,1 GHz = 33,6 GHz verfügbar`

Da auf den ESXi-Servern weitere Workloads wie beispielsweise VMware vCenter Server, VMware NSX Controller oder VMware NSX Edge verarbeitet werden, kann die dritte Voraussetzung bei Verwendung dieser Ressourcen nicht erfüllt werden, weil 33,6 GHz CPU und 32 GB RAM für die beiden virtuellen Maschinen für BIG-IP erforderlich sind.

In diesem Fall schlägt die Installation von F5 on {{site.data.keyword.cloud_notm}} fehl, sofern nicht mindestens ein ESXi-Server zur Umgebung hinzugefügt wird und die Failoverreservierungen der vShpere-Hochverfügbarkeit entsprechend aktualisiert werden, damit ausreichend Ressourcen für die beiden virtuellen Maschinen für BIG-IP VE gewährleistet sind. Wenn zur Ausführung des Service "F5 on {{site.data.keyword.cloud_notm}}" zusätzliche Ressourcen benötigt werden, können Sie weitere ESXi-Server hinzufügen, bevor Sie F5 on {{site.data.keyword.cloud_notm}} installieren.

## Hinweise zum Entfernen von F5 on IBM Cloud

Bevor Sie den Service "F5 on {{site.data.keyword.cloud_notm}}" entfernen, müssen Sie sicherstellen, dass die bestehende Konfiguration für BIG-IP VE ordnungsgemäß entfernt wurde. Insbesondere muss der Netzverkehr an BIG-IP VE vorbei und nicht durch BIG-IP VE geleitet werden. Andernfalls kann der vorhandene Datenverkehr von Ihrer Umgebung beeinträchtigt werden.

### Zugehörige Links

* [F5 on {{site.data.keyword.cloud_notm}} bestellen](f5_ordering.html)
* [F5 on {{site.data.keyword.cloud_notm}} verwalten](managing_f5.html)
* [Kontaktaufnahme mit dem IBM Support](../vmonic/trbl_support.html)
* [Häufig gestellte Fragen](../vmonic/faq.html)
* [F5-Website](https://f5.com/){:new_window}

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# Speichereinstellungen

Dieses Design unterstützt nur das Anhängen von gemeinsamem Speicher über NFS v3. NFS v4 und v4.1 werden nicht unterstützt.

**Hinweis**: Der gesamte angehängte Speicher dieses Designs ist auf den {{site.data.keyword.cloud_notm}}-Speicher beschränkt, der innerhalb desselben {{site.data.keyword.CloudDataCent_notm}} verfügbaren ist, in dem sich auch die vCenter Server-Lösung befindet. Außerdem handelt es sich bei allen im Datenspeicher gespeicherten virtuellen Platten standardmäßig um Thin-Provisioning-Einheiten.

Die Architektur gibt an, dass NFS v3-Datenspeicher unter Verwendung des DNS-Namens aus dem {{site.data.keyword.cloud_notm}}-Speicher angehängt werden, um eine Verbindung zur gemeinsam genutzten Ressource herzustellen. Darüber hinaus wird die gemeinsam genutzte NFS-Ressource auf allen Hosts im vCenter Server-Cluster angehängt und in einem Datenspeichercluster platziert, in dem die Storage DRS-Funktion aktiviert wurde.

## vSphere Storage Distributed Resource Scheduler (Storage DRS)

Storage DRS ermöglicht Ihnen das Management der aggregierten Ressourcen eines Datenspeicherclusters. Wird Storage DRS aktiviert, dann bietet die Funktion Empfehlungen für die Platzierung von virtuellen Maschinen (VMs) und die Migration an, um den verfügbaren Speicherplatz und die E/A-Ressourcen gleichmäßig auf die Datenspeicher des Datenspeicherclusters zu verteilen.

Wenn Storage DRS aktiviert wird, dann stehen die folgenden Funktionen zur Verfügung:
* Lastausgleich für Speicherbereiche zwischen den Datenspeichern eines Datenspeicherclusters
* Lastausgleich für E/A-Operationen zwischen den Datenspeichern eines Datenspeicherclusters
* Anfangsplatzierung virtueller Platten auf Basis des Speicherbereichs und der E/A-Workload

In diesem Design wird Storage DRS mit der Automatisierungsstufe **Vollständig automatisiert** aktiviert. Demzufolge werden Dateien automatisch migriert, um die Ressourcennutzung im Datencluster zu optimieren. Da der Cluster vollständig automatisiert ist, wird für alle anderen Storage DRS-Optionen die Einstellung **Clustereinstellungen verwenden** verwendet.

## Storage DRS-Laufzeiteinstellungen für NFS v3

Die Aggressivität von Storage DRS wird durch Angabe von Schwellenwerten für den verwendeten Speicherbereich und die E/A-Latenz bestimmt. Storage DRS erfasst Ressourcennutzungsinformationen für die Datenspeicher in einem Datenspeichercluster. vCenter Server verwendet diese Informationen zum Generieren von Empfehlungen für die Platzierung virtueller Platten in Datenspeichern.

Wird für einen Datenspeichercluster eine niedrige Aggressivitätsstufe festgelegt, dann empfiehlt Storage DRS Storage vMotion-Migrationen nur im Bedarfsfall. Dies ist z. B. möglich, wenn die E/A-Arbeitslast, die Speichernutzung oder deren Unausgeglichenheit hoch ist. Wird für einen Datenspeichercluster eine hohe Aggressivitätsstufe festgelegt, dann empfiehlt Storage DRS Migrationen, sobald der Datenspeichercluster vom Einsatz einer Lastausgleichsfunktion für den Speicherbereich oder die Ein-/Ausgabe profitieren kann.

Im Datenspeichercluster stehen die folgenden Schwellenwertkategorien zur Verfügung:

* Speicherbereichsnutzung: Storage DRS generiert Empfehlungen oder führt Migrationen durch, wenn der Prozentsatz der Speicherbereichsnutzung im Datenspeicher den Schwellenwert überschreitet, der in vSphere Web Client festgelegt wurde.
* E/A-Latenz: Storage DRS generiert Empfehlungen oder führt Migrationen durch, wenn das 90. Perzentil der E/A-Latenz, die im Verlauf eines Tages für den Datenspeicher gemessen wurde, den Schwellenwert überschreitet.

In diesem Design werden die Storage DRS-Laufzeiteinstellungen aktiviert und für die Schwellenwerte werden die jeweiligen Standardwerte beibehalten. Es wird dringend empfohlen, diese Werte auf Basis der Workload-E/A-Anforderungen und der Sensitivität der Latenz zu ändern.

Die folgende Tabelle enthält die Einstellungen in VMware vSphere Web Client.

Tabelle 1. Storage DRS-Laufzeiteinstellungen

| Einstellung       | Wert  |
|:--------------- |:------ |
| E/A-Metrik für SDRS-Empfehlungen aktivieren | Ausgewählt |
| Belegter Speicherbereich | Ausgewählt, auf 80% festgelegt |
| Schwellenwert für E/A-Latenz | 15 ms |

Weitere Informationen zur Konfiguration dieser Einstellungen in vSphere Web Client finden Sie im Abschnitt zum [Festlegen der Storage DRS-Laufzeitregeln in vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

## Storage I/O Control für NFS v3

Ist SIOC (Storage I/O Control) in der Umgebung aktiviert, ändert SIOC die Länge der Einheitenwarteschlange für einzelne virtuelle Maschinen (VMs). Durch die Änderung der Länge der Einheitenwarteschlange wird die Warteschlange des Speicherarrays für alle VMs auf einen gleichen Anteil reduziert und die Speicherwarteschlange gedrosselt. SIOC wird nur dann wirksam, wenn Ressourcen beschränkt sind und die E/A-Latenz des Speichers den definierten Schwellenwert überschreitet.

Damit SIOC feststellen kann, wann es für eine Speichereinheit zu einem Engpass oder einer Beschränkung kommt, ist ein definierter Schwellenwert erforderlich. Die Latenzzeit für den Engpassschwellenwert variiert bei den unterschiedlichen Speichertypen. Dieses Design dient zur Ausgabe von Empfehlungen und zur Implementierung einer Schwellenwertlatenz von 10 Millisekunden.

Sie können auch einzelne virtuelle Platten für unterschiedliche VMs beschränken oder diesen mit SIOC unterschiedliche gemeinsam genutzte Ressourcen erteilen. Die Beschränkung der Platten und die Erteilung unterschiedlicher gemeinsam genutzter Ressourcen ermöglicht Ihnen den Abgleich und die Ausrichtung der Umgebung auf die Workload anhand der angeforderten IOPS-Nummer für den Dateispeicherdatenträger. Die Begrenzung wird auf Basis von IOPS (E/A-Operationen pro Sekunde) festgelegt und es ist möglich, eine andere Gewichtung oder andere gemeinsam genutzte Ressourcen festzulegen.

Gemeinsam genutzte Ressourcen virtueller Platten, für die **Hoch** (2.000 gemeinsam genutzte Ressourcen) festgelegt ist, erhalten doppelt so hohe E/A-Volumen wie Platten, für die **Normal** (1.000 gemeinsam genutzte Ressourcen) festgelegt ist, und viermal so viele wie bei der Angabe **Niedrig** (500 gemeinsam genutzte Ressourcen). **Normal** ist für alle virtuellen Maschinen der Standardwert; Sie müssen die **Normal**-Werte also für virtuelle Maschinen, für die dies erforderlich ist, anpassen.

## Zusätzlicher Speicher für NFS v3

Wird aufgrund unzureichender Speicherplatzkapazitäten oder hoher Latenzzeiten zusätzlicher Speicher für die Umgebung benötigt, dann können Sie eine weitere gemeinsam genutzte NFS-Ressource über die Konsole bestellen. Nach der Bestellung der gemeinsam genutzten Ressource hängen Sie den Export an die vSphere ESXi-Hosts im Cluster an und platzieren Sie die Ressource im Speichercluster. Die Platzierung der neuen gemeinsam genutzten NFS-Ressource im Speichercluster skaliert den Speicher, der der Umgebung zugeordnet ist, effektiv und reibungslos in horizontaler Richtung, ohne dass es hierdurch zu einer Belastung durch Migrationen auf Speicherebene kommt.

## Erweiterte Konfigurationsparameter

Bei diesem Design werden erweiterte Konfigurationsparameter hinzugefügt, deren Verwendung von {{site.data.keyword.cloud_notm}} empfohlen wird. Demzufolge werden die folgenden Parameter auf jedem vSphere ESXi-Host festgelegt, der an die gemeinsam genutzte {{site.data.keyword.cloud_notm}}-NFS-Ressource angehängt ist.

Tabelle 2. Erweiterte NFS-Konfigurationsparameter

| Parameter       | Wert  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### Zugehörige Links

* [Lösungsübersicht](../solution/solution_overview.html)

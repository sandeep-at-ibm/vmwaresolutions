---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-17"

---

# Speichereinstellungen

Dieses Design unterstützt den Anhängen des gemeinsam genutzten Speichers über NFS v3 und NFS v4.1 (NFS v4 wird nicht unterstützt). Nach der Bestellung von VMware vCenter Server on {{site.data.keyword.cloud}} müssen Sie ermitteln, welche NFS-Version für die Umgebung verwendet werden soll.

Während in NFS v4.1 eine verbesserte Leistung und Verfügbarkeit durch Einsatz einer Lastausgleichsfunktion und des Multipathings erzielt wird, wird die Nutzung von vSphere-Funktionen einschließlich Storage DRS, Storage I/O Control und Site Recovery Manager nicht eingeschränkt.

In der folgenden Tabelle sind die NFS-Protokolle und die Unterstützung für vSphere-Funktionen bei Verwendung von vSphere 6.0 aufgeführt.

Tabelle 1. NFS-Protokolle und vSphere-Funktionen

| vSphere-Funktion | NFS v3 | NFS v4.1 |
|:--------------- |:------ |:-------- |
| vMotion und Storage vMotion | Ja | Ja |
| High Availability (HA) | Ja | Ja |
| Fehlertoleranz (FT) | Ja | Ja |
| Distributed Resource Scheduler (DRS) | Ja | Ja |
| Hostprofile | Ja | Ja |
| Storage DRS | Ja | Nein |
| Storage I/O Control (SIOC) | Ja | Nein |
| Site Recovery Manager | Ja | Nein |
| Virtuelle Datenträger | Ja | Nein |

**Hinweis**: Der gesamte angehängte Speicher dieses Designs ist auf den {{site.data.keyword.cloud_notm}}-Speicher beschränkt, der innerhalb desselben {{site.data.keyword.CloudDataCent_notm}} verfügbaren ist, in dem sich auch die vCenter Server-Lösung befindet. Außerdem werden die NFS v3- und NFS v4.1-Datenspeicher angehängt. Dazu wird auf allen Hosts dieselbe NFS-Version verwendet. Bei allen im Datenspeicher gespeicherten virtuellen Platten handelt es sich standardmäßig um Thin-Provisioning-Einheiten.

## NFS v3 für angehängten Speicher verwenden

Wird NFS v3 als bevorzugte Methode zum Anhängen der NFS-Freigabe ausgewählt, dann verwendet die Architektur eine einzelne IP-Adresse aus dem {{site.data.keyword.cloud_notm}}-Speicher, um eine Verbindung zur Freigabe herzustellen. Darüber hinaus wird die NFS-Freigabe auf allen Hosts im vCenter Server-Cluster angehängt und in einem Datenspeichercluster platziert, in dem die Storage DRS-Funktion aktiviert wurde.

### vSphere Storage Distributed Resource Scheduler (Storage DRS)

Storage DRS ermöglicht Ihnen das Management der aggregierten Ressourcen eines Datenspeicherclusters. Wird Storage DRS aktiviert, dann bietet die Funktion Empfehlungen für die Platzierung von virtuellen Maschinen (VMs) und die Migration an, um den verfügbaren Speicherplatz und die E/A-Ressourcen gleichmäßig auf die Datenspeicher des Datenspeicherclusters zu verteilen.

Wenn Storage DRS aktiviert wird, dann stehen die folgenden Funktionen zur Verfügung:
* Lastausgleich für Speicherbereiche zwischen den Datenspeichern eines Datenspeicherclusters
* Lastausgleich für E/A-Operationen zwischen den Datenspeichern eines Datenspeicherclusters
* Anfangsplatzierung virtueller Platten auf Basis des Speicherbereichs und der E/A-Workload

In diesem Design wird Storage DRS mit der Automatisierungsstufe "Vollständig automatisiert" aktiviert. Demzufolge werden Dateien nicht automatisch migriert, um die Ressourcennutzung im Datencluster zu optimieren. Hierbei ist zu beachten, dass alle anderen Storage DRS-Optionen mit der Einstellung "Clustereinstellungen verwenden" benutzt werden, da der Cluster vollständig automatisiert ist.

### Storage DRS-Laufzeiteinstellungen für NFS v3

Die Aggressivität von Storage DRS wird durch Angabe von Schwellenwerten für den verwendeten Speicherbereich und die E/A-Latenz bestimmt. Storage DRS erfasst Ressourcennutzungsinformationen für die Datenspeicher in einem Datenspeichercluster. vCenter Server verwendet diese Informationen zum Generieren von Empfehlungen für die Platzierung virtueller Platten in Datenspeichern.

Wird für einen Datenspeichercluster eine niedrige Aggressivitätsstufe festgelegt, dann empfiehlt Storage DRS Storage vMotion-Migrationen nur im Bedarfsfall. Dies ist z. B. möglich, wenn die E/A-Arbeitslast, die Speichernutzung oder deren Unausgeglichenheit hoch ist. Wird für einen Datenspeichercluster eine hohe Aggressivitätsstufe festgelegt, dann empfiehlt Storage DRS Migrationen, sobald der Datenspeichercluster vom Einsatz einer Lastausgleichsfunktion für den Speicherbereich oder die Ein-/Ausgabe profitieren kann.

Im Datenspeichercluster stehen die folgenden Schwellenwertkategorien zur Verfügung:

* Speicherbereichsnutzung: Storage DRS generiert Empfehlungen oder führt Migrationen durch, wenn der Prozentsatz der Speicherbereichsnutzung im Datenspeicher den Schwellenwert überschreitet, der in vSphere Web Client festgelegt wurde.
* E/A-Latenz: Storage DRS generiert Empfehlungen oder führt Migrationen durch, wenn das 90. Perzentil der E/A-Latenz, die im Verlauf eines Tages für den Datenspeicher gemessen wurde, den Schwellenwert überschreitet.

In diesem Design werden die Storage DRS-Laufzeiteinstellungen aktiviert und für die Schwellenwerte werden die jeweiligen Standardwerte beibehalten. Es wird dringend empfohlen, diese Werte auf Basis der Workload-E/A-Anforderungen und der Sensitivität der Latenz zu ändern.

Die folgende Tabelle enthält die Einstellungen in VMware vSphere Web Client.

Tabelle 2. Storage DRS-Laufzeiteinstellungen

| Einstellung       | Wert   |
|:--------------- |:------ |
| E/A-Metrik für SDRS-Empfehlungen aktivieren | Ausgewählt |
| Belegter Speicherbereich | Ausgewählt, auf 80% festgelegt |
| Schwellenwert für E/A-Latenz | 15 ms |

Weitere Informationen zur Konfiguration dieser Einstellungen in vSphere Web Client finden Sie im Abschnitt zum [Festlegen der Storage DRS-Laufzeitregeln in vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

### Storage I/O Control für NFS v3

Wenn Storage I/O Control (SIOC) in der Umgebung aktiviert ist, dann wirkt sich dies auf die Länge der Einheitenwarteschlange für die einzelnen virtuellen Maschinen (VMs) aus. Durch die Änderung der Länge der Einheitenwarteschlange wird die Warteschlange des Speicherarrays für alle VMs auf einen gleichen Anteil reduziert und die Speicherwarteschlange gedrosselt. SIOC wird nur dann wirksam, wenn Ressourcen beschränkt sind und die E/A-Latenz des Speichers den definierten Schwellenwert überschreitet.

Damit SIOC feststellen kann, wann es für eine Speichereinheit zu einem Engpass oder einer Beschränkung kommt, ist ein definierter Schwellenwert erforderlich. Die Latenzzeit für den Engpassschwellenwert variiert bei den unterschiedlichen Speichertypen. Dieses Design dient zur Ausgabe von Empfehlungen und zur Implementierung einer Schwellenwertlatenz von 10 Millisekunden.

Sie können auch einzelne virtuelle Platten für unterschiedliche VMs beschränken oder diesen mit SIOC unterschiedliche Freigaben erteilen. Die Beschränkung der Platten und die Erteilung unterschiedlicher Freigaben ermöglicht Ihnen den Abgleich und die Ausrichtung der Umgebung auf die Workload anhand der angeforderten IOPS-Nummer für den Dateispeicherdatenträger. Die Begrenzung wird auf Basis von IOPS (E/A-Operationen pro Sekunde) festgelegt und es ist möglich, eine andere Gewichtung oder andere Freigaben festzulegen.

Freigaben virtueller Platten, die auf "Hoch" (2.000 Freigaben) festgelegt sind, erhalten doppelt so hohe E/A-Volumen wie Platten, die auf "Normal" (1.000 Freigaben) festgelegt sind, und vier Mal so viele wie bei der Angabe "Niedrig" (500 Freigaben). "Normal" ist der Standardwert für alle VMs. Daher müssen Sie die Werte über oder unter "Normal" für die VMs anpassen, bei denen dies erforderlich ist.

### Zusätzlicher Speicher für NFS v3

Wird aufgrund unzureichender Speicherplatzkapazitäten oder hoher Latenzzeiten zusätzlicher Speicher für die Umgebung benötigt, dann können Sie eine weitere NFS-Freigabe über die Konsole bestellen. Nach Bestellung der Freigabe wird der Export automatisch an die vSphere ESXi-Hosts im Cluster angehängt und in dem zuvor angegebenen Speichercluster platziert. Die Platzierung der neuen NFS-Freigabe im Speichercluster skaliert den Speicher, der der Umgebung zugeordnet ist, effektiv und reibungslos in horizontaler Richtung, ohne dass es hierdurch zu einer Belastung durch Migrationen auf Speicherebene kommt.

## NFS v4.1 für angehängten Speicher verwenden

Wird NFS v4.1 als bevorzugte Methode zum Anhängen der NFS-Freigabe ausgewählt, dann verwendet die Architektur mehrere IP-Adressen aus dem {{site.data.keyword.cloud_notm}}-Speicher, um eine Verbindung zur Freigabe herzustellen. Während die Freigabe an alle Hosts im vCenter Server-Cluster angehängt ist, wird sie nicht in einem Datenspeichercluster platziert, da in vSphere Einschränkungen bei der Verwendung von Storage DRS mit NFS v4.1 bestehen.

**Hinweis**: NFS 4.1 mit vSphere 6.0 bietet keine Unterstützung für die Hardwarebeschleunigung. Diese Einschränkung verhindert, dass umfangreiche virtuelle Platten in NFS v4.1-Datenspeichern erstellt werden können.

### Zusätzlicher Speicher für NFV v4.1

Wird aufgrund unzureichender Speicherplatzkapazitäten oder hoher Latenzzeiten zusätzlicher Speicher für die Umgebung benötigt, dann können Sie eine weitere NFS-Freigabe über die Konsole bestellen. Nach Bestellung der Freigabe wird der Export automatisch an die vSphere ESXi-Hosts im Cluster angehängt. Anschließend müssen Sie die VMs migrieren und für die Datenspeicher die Lastausgleichsfunktion aktivieren, sodass der Speicherbereich korrekt verwendet wird und die Anforderungen hinsichtlich der Latenzzeiten erfüllt werden.

## Erweiterte Konfigurationsparameter

Unabhängig davon, ob Sie mit NFS v3 oder NFS v4.1 arbeiten wollen, fügt dieses Design erweiterte Konfigurationsparameter hinzu, deren Verwendung von {{site.data.keyword.cloud_notm}} empfohlen wird. Demzufolge werden die folgenden Parameter auf jedem vSphere ESXi-Host festgelegt, der an die  {{site.data.keyword.cloud_notm}}-NFS-Freigabe angehängt ist.

Tabelle 3. Erweiterte NFS-Konfigurationsparameter

| Parameter       | Wert   |
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

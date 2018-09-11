---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# Clustereinstellungen

Vor dem Hinzufügen des angehängten Speichers hat die vCenter Server-Lösung die erweiterten Funktionen wie z. B. vSphere Distributed Resource Scheduler (DRS) und vSphere High Availability (HA) nicht aktiviert. Durch das Hinzufügen der über NFS angehängten Speichereinheit werden diese Funktionen im Cluster mit den Einstellungen aktiviert, die in den folgenden Abschnitten aufgelistet werden.

## vSphere Distributed Resource Scheduler (DRS)

Beim Aktivieren von vSphere DRS in einem Cluster werden die beiden folgenden wichtigen Funktionen aktiviert: Lastausgleich und Energiemanagement.

### Lastausgleich

Die Lastausgleichsfunktion erlaubt die kontinuierliche Überwachung der Verteilung und Belegung von CPU- und Speicherressourcen für alle Hosts und virtuellen Maschinen (VMs) innerhalb des Clusters. DRS vergleicht diese Metriken mit einer idealen Ressourcenauslastung unter Berücksichtigung der Attribute für die Ressourcenpools und VMs des Clusters sowie des aktuellen Bedarfs und des Unausgeglichenheitsziels. Anschließend werden geeignete VM-Migrationen ausgeführt (oder vorgeschlagen).

Wird eine virtuelle Maschine (VM) zum ersten Mal eingeschaltet, dann versucht DRS, den korrekten Lastausgleich aufrechtzuerhalten, indem die VM entweder auf einem geeigneten Host platziert oder eine entsprechende Empfehlung ausgegeben wird. Die Einstellungen für Platzierungen oder Empfehlungen werden im Abschnitt für die DRS-Automatisierung in den Clustereinstellungen festgelegt.

In diesem Design wird die DRS-Automatisierungsstufe auf die Einstellung "Vollständig automatisiert" gesetzt. Wenn die VMs eingeschaltet werden, dann werden sie automatisch auf Hosts mit einer ausreichenden Kapazität platziert. Die VMs werden außerdem automatisch von einem Host auf einen anderen migriert, um für den Cluster den Lastausgleich durchzuführen. Darüber hinaus wird der Migrationsschwellenwert des DRS-Clusters auf den Mittelwert zwischen dem konservativen und aggressiven Wert gesetzt, und zwar so, dass die Empfehlungen für Priorität 1, Priorität 2 und Priorität 3 angewendet werden können. Dies bedeutet, dass vCenter Server mindestens deutliche Verbesserungen in Bezug auf den Lastausgleich des Clusters bietet.

Die folgende Tabelle enthält die Einstellungen für den vSphere-DRS-Cluster in VMware vSphere Web Client.

Tabelle 1. Einstellungen zur DRS-Automatisierung für den vSphere-DRS-Cluster

| Einstellung             | Wert   |
|:------------------- |:------ |
| vSphere DRS aktivieren | Ausgewählt |
| Automatisierungsstufe | Vollständig automatisiert |
| Migrationsschwellenwert | Empfehlungen der Priorität 1, Priorität 2 und Priorität 3 anwenden |
| Individuelle Maschinenautomatisierungsstufen aktivieren | Ausgewählt, auf 15 ms festgelegt |

Weitere Informationen zur Konfiguration dieser Einstellungen in vSphere Web Client finden Sie im Abschnitt zum [Festlegen einer angepassten Automatisierungsstufe für eine virtuelle Maschine in vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

Zusätzlich zur Automatisierungsstufe und zum Migrationsschwellenwert des Clusters ermöglicht dieses Design die VM-Automatisierung, sodass Überschreibungen für einzelne VMs festgelegt werden können. Dadurch ist eine differenziertere Steuerung der VMs und eine weiterführende Priorisierung in Bezug auf den Lastausgleich der VMs möglich.

### Energiemanagement

Wenn die Funktion VMware Distributed Power Management aktiviert wird, dann vergleicht DRS die Kapazität auf Cluster- und auf Hostebene mit den Anforderungen der Cluster-VMs unter Berücksichtigung der zuletzt ermittelten Bedarfswerte. Die Funktion versetzt Hosts in den Standby-Stromversorgungsmodus (oder empfiehlt dies), wenn genügend Überkapazitäten ermittelt werden, oder veranlasst die Zuschaltung von Hosts, wenn Kapazitätsengpässe festgestellt werden. Abhängig von den resultierenden Empfehlungen zum Stromversorgungsstatus der Hosts müssen VMs möglicherweise auf andere Hosts verlagert werden.
In diesem Design wird das Energiemanagement inaktiviert, da sich durch die Ab- oder Zuschaltung von Hosts im Cluster keine operativen oder finanziellen Vorteile ergeben.

## vSphere High Availability (HA)

vSphere stellt Hochverfügbarkeit (HA = High Availability) für VMs bereit, indem die virtuellen Maschinen und die Hosts, auf denen diese platziert wurden, in einem Cluster zusammengefasst werden. Die Hosts im Cluster werden überwacht und im Falle eines Fehlers oder Ausfalls werden die VMs auf dem fehlerhaften oder ausgefallenen Host auf einem Ausweichhost erneut gestartet. In diesem Design wird vSphere High Availability mit der Hostüberwachung und der VM-Überwachung im Cluster aktiviert.

### Hostüberwachung

Die Hostüberwachung ermöglicht den Hosts eines Clusters den Austausch von Netzheartbeats und vSphere HA die Einleitung geeigneter Aktionen, wenn ein Fehler erkannt wird. Diese Funktion wird in diesem Design aktiviert.

### Überwachung virtueller Maschinen

Die Funktion zur Überwachung virtueller Maschinen (VMs) verwendet Heartbeatinformationen, die von VMware Tools als Proxy für die Verfügbarkeit von Gastbetriebssystemen erfasst werden. Auf diese Weise kann vSphere High Availability (HA) automatisch einzelne VMs zurücksetzen oder neu starten, wenn diese Einheiten ihre Heartbeatfunktion nicht mehr ausführen können. Dieses Design ermöglicht sowohl die VM-Überwachung als auch die Anwendungsüberwachung.

#### Fehlerbedingungen und VM-Antworten

Die Fehlerbedingungen definieren die Merkmale eines VM-Ausfalls und die Antwort des Systems auf die einzelnen Fehler. In diesem Design wird die VM-Neustartpriorität auf "Mittel" gesetzt. Es wird dringend empfohlen, diesen Wert zu überprüfen und die Einstellungen entsprechend anzupassen, sodass die Neustartpriorität dem Stellenwert der Workload entspricht. Darüber hinaus wird als Antwort auf die Hostisolation "VMs ausschalten und neu starten" festgelegt, sodass die VMs nicht von einem isolierten Host im Cluster beeinträchtigt werden. Für die verbleibenden Werte dieser Einstellung werden die Standardwerte benutzt.

Die folgende Tabelle enthält die Einstellungen für den vSphere HA-Cluster in VMware vSphere Web Client.

Tabelle 2. Fehlerbedingungen und Einstellungen für VM-Antworten für vSphere HA-Cluster

| Einstellung             | Wert   |
|:------------------- |:------ |
| VM-Neustartpriorität | Mittel |
| Antwort für Hostisolation | VMs ausschalten und neu starten |
| Antwort für Datenspeicher mit Permanent Device Loss (PDL) | Inaktiviert |
| Antwort für Datenspeicher mit All Paths Down (APD) | Inaktiviert |
| Antwort für APD-Wiederherstellung nach APD-Zeitlimitüberschreitung | Inaktiviert |
| Sensitivität für VM-Überwachung | Angepasst |
| Fehlerintervall | 50 s |
| Mindestbetriebszeit | 90 s |
| Maximale Anzahl Zurücksetzungen pro VM | 10 |
| Zeitfenster für maximale Anzahl Zurücksetzungen | Innerhalb von 1 Std. |

Weitere Informationen zur Konfiguration dieser Einstellungen in vSphere Web Client finden Sie im Abschnitt zum
[Konfigurieren von VM-Antworten](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Zugangssteuerung

vCenter Server verwendet die Zugangssteuerung, um sicherzustellen, dass genügend Ressourcen in einem Cluster verfügbar sind, um einen Failover-Schutz bereitzustellen, und um zu gewährleisten, dass die VM-Ressourcenreservierungen berücksichtigt werden. In diesem Design wird die Failover-Kapazität reserviert, indem ein Prozentsatz der Clusterressourcen angegeben wird. Die definierte Failover-Kapazität wird auf 25% CPU und 25% Speicher festgelegt.

#### Datenspeicher für Austausch von Überwachungssignalen (Heartbeating)

vSphere High Availability (HA) verwendet das Heartbeating für Datenspeicher zur Unterscheidung zwischen Hosts, auf denen ein Fehler aufgetreten ist, und Hosts, die sich in einer Netzpartition befinden. Das Heartbeating für Datenspeicher erlaubt vSphere HA die Überwachung von Hosts, wenn eine Managementnetzpartition festgestellt wird, und das weitere Antworten auf möglicherweise auftretende Fehler. In diesem Design wird die Auswahlrichtlinie für das Heartbeating für Datenspeicher auf "Automatisch Datenspeicher auswählen, auf die vom Host zugegriffen werden kann" gesetzt.

### Zugehörige Links

* [Lösungsübersicht](../solution/solution_overview.html)

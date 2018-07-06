---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Cloud Foundation-Teileliste

In diesem Abschnitt erhalten Sie Informationen zur Teileliste (Bill of Materials, BOM) für VMware Cloud Foundation-Instanzen.

## VLAN-Teileliste für Cloud Foundation-Instanzen

Die folgende Tabelle enthält detaillierte Informationen zur Teileliste für die Cloud Foundation-VLANs.

Tabelle 1. Teileliste für VLANs in Cloud Foundation-Instanzen

| VLAN      | Typ      | Details      |
|:----------|:----------|:-------------|
| VLAN1     | Öffentlich, Primär | Wird physischen ESXi-Servern für den Zugriff auf öffentliche Netze zugeordnet. Wird nach der Erstbereitstellung nicht mehr verwendet. Für den Internetzugriff verfügbar. |
| VLAN2     | Privates VLAN A, Primär | Wird durch IBM Cloud zu physischen ESXi-Servern zugeordnet. Wird von der Managementschnittstelle für den VMware vSphere-Managementdatenverkehr verwendet.<br><br>Wird virtuellen Maschinen (VMs) zugeordnet, die als Managementkomponenten fungieren.<br><br>Wird zu VMware NSX VTEP (VXLAN-Tunnelendpunkt) zugeordnet. |
| VLAN3     | Privates VLAN B, Portierbar | Wird zu VMware vSAN zugeordnet, sofern verwendet.<br><br>Wird zu VMware NFS zugeordnet, sofern verwendet.<br><br>Wird zu VMware vSphere vMotion zugeordnet. |

## Softwareteileliste für Cloud Foundation-Instanzen

Die folgende Tabelle enthält detaillierte Informationen zur Teileliste für die Cloud Foundation-Softwarekomponenten.

Tabelle 2. Teileliste für Softwarekomponenten in Cloud Foundation-Instanzen

| Hersteller | Komponente                                | Version      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 U1g (ESXi 6.5u1 mit angewendetem Patch-Level ESXi650-201803001) |
| VMware       | vCenter Server Appliance                 | 6.5 Update 1g |
| VMware       | Platform Services Controller             | 6.5 Update 1g |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.3.5        |
| VMware       | SDDC Manager                             | 2.4          |
| {{site.data.keyword.IBM}} | CloudDriver                 | 2.4          |
| Microsoft    | Windows Server Standard Edition (64-Bit) | 2012R2       |

## Erweiterte Konfigurationseinstellungen für ESXi-Server

Die folgende Tabelle vermittelt Ihnen einen Überblick über die erweiterten Konfigurationseinstellungen, die auf die ESXi-Server abhängig davon angewendet werden, ob die Cloud Foundation-Instanz in V2.2 oder höher bereitgestellt oder für sie ein Upgrade von V2.1 oder einem älteren Release auf V2.2 oder höher durchgeführt wird.

Tabelle 3. Erweiterte Konfigurationseinstellungen für ESXi-Server für Cloud Foundation-Instanzen und -Cluster

| Konfigurationseinstellung | Bei Neubereitstellung in V2.2 oder höher  | Bei Upgrade aus V2.1 oder früher |   
|:------------- |:------------- |:------------- |
| TCP/IP-Heapspeichergröße | **TcpipHeapSize** = 32 | Nicht festgelegt |
| Max. TCP/IP-Heapspeicher | **TcpipHeapMax** = 1536 | Nicht festgelegt |  
| Max. Datenträger | **MaxVolumes** = 256 | **/NFS/MaxVolumes** addiert mit **/NFS41/MaxVolumes** = 256 |  
| Max. Überwachungssignalfehler | **HeartbeatMaxFailures** = 10 | Nicht festgelegt |  
| Überwachungssignalfrequenz | **HeartbeatFrequency** = 12 | Nicht festgelegt |  
| Überwachungssignalzeitlimit | **HeartbeatTimeout** = 5 | Nicht festgelegt |
| Max. Warteschlangenlänge | **MaxQueueDepth** = 64 | Nicht festgelegt |
| Stichprobengröße für volle Warteschlange | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Schwellenwert für volle Warteschlange | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

**Hinweise**:
* Die Einstellung **MaxVolumes** ist für den Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" erforderlich, weil der Service möglicherweise mehr als die Standardanzahl von NFS-Mounts auf dem ESXi-Server verwendet.
* Der Wert **Nicht festgelegt** für eine Konfigurationseinstellung gibt an, dass die neue Einstellung nicht automatisch angewendet wird, da dies einen Warmstart für die ESXi-Server erforderlich macht, der zu einer Unterbrechung des Betriebs führen könnte.

  Es wird empfohlen, die mit **Nicht festgelegt** gekennzeichneten Konfigurationseinstellungen auf die neuen Werte zu setzen, um eine instanzübergreifende Konsistenz zu erreichen und eine adäquate Unterstützung für die Speichererweiterung zu ermöglichen. IBM plant, Tests ausschließlich mit diesen neuen Einstellungen für alle Releases von {{site.data.keyword.vmwaresolutions_short}} V2.2 und höher vorzunehmen.

  Weitere Informationen finden Sie unter [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

## Zugehörige Links

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Datenblatt für VMware Cloud Foundation on IBM Cloud Protection](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Überblick zu Cloud Foundation](sd_cloudfoundationoverview.html)
* [Cloud Foundation-Instanzen planen](sd_planning.html)

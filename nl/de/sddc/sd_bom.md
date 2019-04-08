---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

# Cloud Foundation-Teileliste
{: #sd_bom}

In diesem Abschnitt erhalten Sie Informationen zur Teileliste (Bill of Materials, BOM) für VMware Cloud Foundation-Instanzen.

## VLAN-Teileliste für Cloud Foundation-Instanzen
{: #sd_bom-vlans}

Die folgende Tabelle enthält detaillierte Informationen zur Teileliste für die Cloud Foundation-VLANs.

Tabelle 1. Teileliste für VLANs in Cloud Foundation-Instanzen

| VLAN      | Typ      | Details      |
|:----------|:----------|:-------------|
| VLAN1     | Öffentlich, Primär | Wird physischen ESXi-Servern für den Zugriff auf öffentliche Netze zugeordnet. Wird nach der Erstbereitstellung nicht mehr verwendet. Für den Internetzugriff verfügbar. |
| VLAN2     | VLAN "Privat A", Primär | Wird durch {{site.data.keyword.cloud}} physischen ESXi-Servern zugeordnet. Wird von der Managementschnittstelle für den VMware vSphere-Managementdatenverkehr verwendet.<br><br>Wird virtuellen Maschinen (VMs) zugeordnet, die als Managementkomponenten fungieren.<br><br>Wird VMware NSX VTEP (VXLAN-Tunnelendpunkt) zugeordnet. |
| VLAN3     | VLAN "Privat B", Portierbar | Wird VMware vSAN zugeordnet, sofern verwendet.<br><br>Wird VMware NFS zugeordnet, sofern verwendet.<br><br>Wird VMware vSphere vMotion zugeordnet. |

## Softwareteileliste für Cloud Foundation-Instanzen
{: #sd_bom-software}

Die folgende Tabelle enthält detaillierte Informationen zur Teileliste für die Cloud Foundation-Softwarekomponenten.

Tabelle 2. Teileliste für Softwarekomponenten in Cloud Foundation-Instanzen

| Hersteller | Komponente                                | Version      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 Update EP11 (Build 6.5.0-10719125) |
| VMware       | vCenter Server Appliance                 | 6.5 U2c (Build 6.5.0-9451637) |
| VMware       | Platform Services Controller             | 6.5 U2c (Build 6.5.0-9451637) |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.4.1        |
| VMware       | SDDC Manager                             | 2.4          |
| Microsoft    | Windows Server Standard Edition (64-Bit) | 2012R2       |

## Erweiterte Konfigurationseinstellungen für ESXi-Server
{: #sd_bom-esxi-server-advance-config}

Die folgende Tabelle gibt Ihnen eine Übersicht über die erweiterten Konfigurationseinstellungen, die auf die ESXi-Server angewendet werden. Die Einstellungen unterscheiden sich, je nachdem, ob die Cloud Foundation-Instanz von einem früheren Release (Version 2.1 oder früher) in Version 2.2 oder höher installiert wurde (bzw. ein Upgrade auf diese Version durchgeführt wurde).

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

### Hinweise
{: #sd_bom-notes}

* Die Einstellung **MaxVolumes** ist für den Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" erforderlich, weil der Service möglicherweise mehr als die Standardanzahl von NFS-Mounts auf dem ESXi-Server verwendet.
* Der Wert **Nicht festgelegt** für eine Konfigurationseinstellung gibt an, dass die neue Einstellung nicht automatisch angewendet wird, da dies einen Warmstart für die ESXi-Server erforderlich macht, der zu einer Unterbrechung des Betriebs führen könnte.

  Es wird empfohlen, die mit **Nicht festgelegt** gekennzeichneten Konfigurationseinstellungen auf die neuen Werte zu setzen, um eine instanzübergreifende Konsistenz zu erreichen und eine adäquate Unterstützung für die Speichererweiterung zu ermöglichen. IBM plant, Tests ausschließlich mit diesen neuen Einstellungen für alle Releases von {{site.data.keyword.vmwaresolutions_short}} V2.2 und höher vorzunehmen.

  Weitere Informationen finden Sie unter [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

## Zugehörige Links
{: #sd_bom-related}

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [{{site.data.keyword.vmwaresolutions_short}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:new_window}
* [Übersicht über Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)

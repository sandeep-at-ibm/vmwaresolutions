---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# vCenter Server-Teileliste

In diesem Abschnitt erhalten Sie Informationen zur Teileliste (Bill of Materials, BOM) für VMware vCenter Server-Instanzen.

## VLAN-Teileliste für vCenter Server-Instanzen

Die folgende Tabelle enthält detaillierte Informationen zur Teileliste für die vCenter Server-VLANs.

Tabelle 1. Teileliste für VLANs in vCenter Server-Instanzen

| VLAN       | Typ       | Details       |
|:---------- |:---------- |:------------- |
| VLAN1     | Öffentlich, Primär | Wird physischen ESXi-Servern für den Zugriff auf öffentliche Netze zugeordnet. Wird nach der Erstbereitstellung nicht mehr verwendet. Für den Internetzugriff verfügbar. |
| VLAN2     | Privates VLAN A, Primär | Wird durch {{site.data.keyword.cloud}} physischen ESXi-Servern zugeordnet. Wird von der Managementschnittstelle für den VMware vSphere-Managementdatenverkehr verwendet.<br><br>Wird virtuellen Maschinen (VMs) zugeordnet, die als Managementkomponenten fungieren.<br><br>Wird VMware NSX VTEP (VXLAN-Tunnelendpunkt) zugeordnet. |
| VLAN3     | Privates VLAN B, Portierbar | Wird VMware vSAN zugeordnet, sofern verwendet.<br><br>Wird VMware NFS zugeordnet, sofern verwendet.<br><br>Wird VMware vSphere vMotion zugeordnet. |

## Softwareteileliste für vCenter Server-Instanzen

Die folgende Tabelle enthält detaillierte Informationen zur Teileliste für die vCenter Server-Softwarekomponenten.

Tabelle 2. Teileliste für Softwarekomponenten in vCenter Server-Instanzen

| Hersteller  | Komponente                      | Version       |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.5 U1g (ESXi 6.5u1 mit angewendetem Patch-Level ESXi650-201803001) |
| VMware       | vCenter Server Appliance        | 6.5 Update 1g |
| VMware       | Platform Services Controller    | 6.5 Update 1g |
| VMware       | vSAN                            | 6.6.1        |
| VMware       | NSX for vSphere                 | 6.4.1        |
| IBM          | CloudDriver                     | 2.4          |
| Microsoft    | Windows Server Standard Edition | 2012R2       |

**Hinweis**: VMware vSAN ist eine optionale Komponente.

## Erweiterte Konfigurationseinstellungen für ESXi-Server

Die folgende Tabelle gibt Ihnen eine Übersicht über die erweiterten Konfigurationseinstellungen, die auf die ESXi-Server abhängig davon angewendet werden, ob die vCenter Server-Instanz in V2.2 oder höher bereitgestellt oder für sie ein Upgrade von V2.1 oder einem älteren Release auf V2.2 oder höher durchgeführt wird.

Die Einstellungen gelten für neue Instanzen und neue Cluster in neuen Instanzen aus V2.2 oder höher. Die Einstellungen gelten nicht für neue Cluster in vorhandenen Instanzen aus V2.1 oder früher oder in vorhandenen Instanzen, für die ein Upgrade auf V2.2 oder höher durchgeführt wurde.

Tabelle 3. Erweiterte Konfigurationseinstellungen für ESXi-Server für vCenter Server-Instanzen und -Cluster

| Konfigurationseinstellung | Bei Neubereitstellung in V2.2 oder höher  | Bei Upgrade aus V2.1 oder früher |
|:------------- |:------------- |:------------- |
| Max. Datenträger | **MaxVolumes** = 256 | **/NFS/MaxVolumes** addiert mit **/NFS41/MaxVolumes** = 256 |
| Max. Überwachungssignalfehler | **HeartbeatMaxFailures** = 10 | Nicht festgelegt |
| Überwachungssignalfrequenz | **HeartbeatFrequency** = 12 | Nicht festgelegt |
| Überwachungssignalzeitlimit | **HeartbeatTimeout** = 5 | Nicht festgelegt |
| Max. Warteschlangenlänge | **MaxQueueDepth** = 64 | Nicht festgelegt |
| Stichprobengröße für volle Warteschlange | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Schwellenwert für volle Warteschlange | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| TCP/IP-Heapspeichergröße | **TcpipHeapSize** = 32 | Nicht festgelegt |
| Max. TCP/IP-Heapspeicher | **TcpipHeapMax** = 1536 | Nicht festgelegt |

**Hinweise**:
* Die Einstellung **MaxVolumes** ist für den Service "IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}" erforderlich, weil der Service möglicherweise mehr als die Standardanzahl von NFS-Mounts auf dem ESXi-Server verwendet.
* Der Wert **Nicht festgelegt** für eine Konfigurationseinstellung gibt an, dass die neue Einstellung nicht automatisch angewendet wird, da dies einen Warmstart für die ESXi-Server erforderlich macht, der zu einer Unterbrechung des Betriebs führen könnte.

  Es wird empfohlen, die mit **Nicht festgelegt** gekennzeichneten Konfigurationseinstellungen auf die neuen Werte zu setzen, um eine instanzübergreifende Konsistenz zu erreichen und eine adäquate Unterstützung für die Speichererweiterung zu ermöglichen. IBM plant, Tests ausschließlich mit diesen neuen Einstellungen für alle Releases von {{site.data.keyword.vmwaresolutions_short}} V2.2 und höher vorzunehmen.

  Weitere Informationen finden Sie unter [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

## Konfigurationseinstellungen für NSX und Portgruppe

Die folgende Tabelle gibt Ihnen eine Übersicht über die Konfigurationseinstellungen für VMware NSX und für Portgruppen bei vCenter Server-Instanzen sowie über die releaseabhängigen Unterschiede.

Die Einstellungen gelten für neue Instanzen und neue Cluster in neuen Instanzen aus V2.2 oder höher. Die Einstellungen gelten nicht für neue Cluster in vorhandenen Instanzen aus V2.1 oder früher oder in vorhandenen Instanzen, für die ein Upgrade auf V2.2 oder höher durchgeführt wurde.

Tabelle 4. Konfigurationseinstellungenen für NSX und Portgruppen bei vCenter Server-Instanzen

| Konfigurationseinstellung | V2.1 oder früher  | V2.2 oder höher |   
|:------------- |:------------- |:------------- |
| Teambildungsrichtlinie für NSX VXLAN-Cluster | Failover | Lastausgleich - SRCID |
| VTEP für NSX VXLAN-Cluster | 1 | 2 |
| Segment-ID-Pool für primäre Instanz | 6000-8000 | 6000-7999 |  
| Segment-ID-Pool für nachfolgende sekundäre Instanzen oder Instanzen | 6000-8000 | Vorheriger Endbereich in der Konfiguration mit mehreren Standorten + 1 bis vorheriger Endbereich in der Konfiguration mit mehreren Standorten + 2000 |  
| SDDC-DPortGroup-VSAN für Portgruppe (sofern maßgeblich) | **Aktive Uplinks** auf **uplink1** und **Standby-Uplinks** auf **uplink2** gesetzt | **Aktive Uplinks** auf **uplink2** und **Standby-Uplinks** auf **uplink1** gesetzt |  
| SDDC-DPortGroup-Mgmt für Portgruppe | **Portbindung** auf **Ephemer - keine Bindung** und **Lastausgleich** auf **Route auf Basis des virtuellen Ursprungsports** gesetzt | **Portbindung** auf **Statische Bindung** und **Lastausgleich** auf **Routenbasiert auf physischer NIC-Arbeitslast** gesetzt |  
| SDDC-DPortGroup-External für Portgruppe | **Portbindung** auf **Ephemer - keine Bindung** gesetzt | **Portbindung** auf **Statische Bindung** gesetzt |

## Konfigurationseinstellungen für Netz-MTU

Der vSphere-Cluster verwendet zwei virtuelle verteilte vSphere-Switches (VDS), von denen einer für die Konnektivität zum öffentlichen Netz und der andere für die Konnektivität zum privaten Netz verwendet wird.

Die Verbindungen zum privaten Netz sind so konfiguriert, dass Jumbo-Frames mit MTUs (Maximum Transmission Units; maximale Übertragungseinheiten) mit einer Größe von 9000 verwendet werden. Dadurch kann die Leistung für umfangreiche Datenübertragungen (z. B. für Speicher und VMware vMotion) verbessert werden. Dies ist der maximale MTU-Wert, der in VMware und durch {{site.data.keyword.cloud_notm}} zugelassen wird.

In V2.1 oder höheren Releases verwenden die Verbindungen zum öffentlichen Netz eine standardmäßige Ethernet-MTU von 1500. Diese Einstellung von 1500 muss beibehalten werden. Änderungen können zur Paketfragmentierung bei der Übertragung im Internet führen.

Die folgende Tabelle gibt Ihnen eine Übersicht über die Konfigurationseinstellungen für die Netz-MTU, die für den öffentlichen und privaten DVS (Distributed Virtual Switch) abhängig davon angewendet werden, ob die vCenter Server-Instanz in V2.1 oder höheren Releases bereitgestellt wird.

Tabelle 5. MTU-Konfigurationseinstellungen für vCenter Server-Instanzen und -Cluster je nach Version der Instanz

| VDS | V2.1 oder höher  | V2.0 oder früher (oder Upgrade von V2.0 oder früher) |
|:-------------- |:-------------- |:------------- |
| Öffentlicher Switch  | 1500 (Standardwert) | 9000 (Jumbo-Frames) |
| Privater Switch | 9000 (Jumbo-Frames) | 9000 (Jumbo-Frames) |

Die Einstellungen gelten für neue Instanzen und neue Cluster aus Instanzen, die in V2.1 oder höheren Releases bereitgestellt wurden. Die Einstellungen gelten auch für neue Cluster in übergreifenden {{site.data.keyword.CloudDataCents_notm}}, die aus Instanzen stammen, für die ein Upgrade auf V2.1 oder höhere Releases durchgeführt wurde.

Die Einstellungen gelten nicht für neue Cluster in demselben {{site.data.keyword.CloudDataCent_notm}} (Rechenzentrum), für vorhandene Instanzen mit V2.0 oder älteren Releases oder bereits vorhandene Instanzen, für die ein Upgrade auf V2.1 oder ein höheres Release durchgeführt wurde.

Für Instanzen, die in V2.0 oder älteren Releases bereitgestellt wurden, sollten Sie die MTU-Einstellung für den öffentlichen Switch auf 1500 festlegen.

### MTU-Einstellung für öffentlichen Switch aktualisieren

Führen Sie zum Aktualisieren der MTU-Einstellung für den öffentlichen Switch die folgenden Schritte in VMware vSphere Web Client aus:
1. Klicken Sie mit der rechten Maustaste auf den VDS und klicken Sie dann auf **Einstellungen bearbeiten**.
2. Wählen Sie auf der Registerkarte **Eigenschaften** die Option **Erweitert** aus.
3. Stellen Sie sicher, dass für **Maximale MTU** der Wert 1500 festgelegt ist.

   **Hinweis**: Wenn in einem verteilten vSphere-Switch (vDS) Änderungen an der MTU-Größe vorgenommen werden, werden die angehängten Uplinks (physischen NICs) herunter- und wieder hochgefahren. Aus diesem Grund kommt es bei den VMs, die den betreffenden Uplink verwenden, zu einem kurzen Ausfall. Daher wird empfohlen, die Aktualisierung der MTU-Einstellung auf eine geplante Ausfallzeit zu legen.

### Zugehörige Links

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Enabling Jumbo Frames on virtual distributed switches](https://kb.vmware.com/s/article/1038827)
* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040)
* [Übersicht über vCenter Server](vc_vcenterserveroverview.html)
* [vCenter Server-Instanzen planen](vc_planning.html)

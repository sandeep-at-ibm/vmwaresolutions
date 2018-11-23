---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-09"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Übersicht über IBM Cloud Private Hosted

Der Service "{{site.data.keyword.cloud}} Private Hosted" führt eine automatische Bereitstellung von {{site.data.keyword.cloud_notm}} Private Hosted auf Ihren VMware vCenter Server-Instanzen durch. Dieser Service stellt die Leistungsfähigkeit von Mikroservices und Containern in Ihrer VMware-Umgebung unter {{site.data.keyword.cloud_notm}} zur Verfügung. Mit diesem Service können Sie den Einsatz des bereits vertrauten VMware- und {{site.data.keyword.cloud_notm}} Private-Betriebsmodells und der zugehörigen Tools von Ihrem lokalen Standort (On-Premises) auf {{site.data.keyword.cloud_notm}}-Umgebungen ausdehnen.

Dieser Service ist für die folgenden Instanzen verfügbar:
* vCenter Server-Instanzen, die in V2.5 (oder höher) bereitgestellt werden oder für die ein Upgrade auf diese Version durchgeführt wurde
* vCenter Server with Hybridity Bundle-Instanzen, die in V2.7 (oder höher) bereitgestellt werden oder für die ein Upgrade auf diese Version durchgeführt wurde.
{:note}

## Technische Spezifikationen für IBM Cloud Private Hosted

In der folgenden Tabelle sind die Mindestvoraussetzungen für die Bestellung von IBM Cloud Private Hosted Service für die **Produktionsumgebung** und die **Entwicklungs-/Testumgebung** aufgeführt.

Tabelle 1. Mindestvoraussetzungen für Produktions- und Entwicklungs-/Testumgebungen

|Umgebung | Kerne | Speicher (GB) | Hosts | Speicher (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| Produktion | 52 | 640 | 3 | 8.000 |
| Entwicklung/Test | 30 | 200 | 3 | 4.000 |

### Ressourcenbedarf für IBM Cloud Private Hosted

In den folgenden Tabellen werden die Ressourcenanforderungen für den {{site.data.keyword.cloud_notm}} Private Hosted-Service in Produktions- und Entwicklungs-/Testumgebungen aufgelistet.

Tabelle 2. {{site.data.keyword.cloud_notm}} Private Hosted-Ressourcenanforderungen in Produktionsumgebungen

| Knotentyp  | CPU-Kerne   |  Speicher (GB) | Platte 1 (GB) | Platte 2 (GB) | Anzahl VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Boot       | 12 | 24 | 100 | 1 | 1 |   
| Management | 8 | 64 | 500 | 3 | 3 |
| Master     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Worker     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability Advisor | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| NFS-Server | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0,5 | 0,5 | 2 |
| Dokumentierte Einschränkungen | 52 | 640 |  | 8.000 |   |

Tabelle 3. {{site.data.keyword.cloud_notm}} Private Hosted-Ressourcenanforderungen in Entwicklungs-/Testumgebungen

| Knotentyp  | CPU-Kerne   |  Speicher (GB) | Platte 1 (GB) | Platte 2 (GB) | Anzahl VMs |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Boot       | 12 | 24 | 100 | 1 | 1 |   
| Management | 8 | 16 | 150 | 1 | 1 |
| Master     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Worker     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability Advisor | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| NFS-Server | 8 | 4  | 350 | 1 | 1 |
| NSX Edge Services Gateway | 2 | 1 | 0,5 | 0,5 | 2 |
| Dokumentierte Einschränkungen | 30 | 200 |  | 4.000 |  |

### Formeln für die Berechnung des Speicherbedarfs von IBM Cloud Private Hosted

Die folgenden Formeln werden verwendet, um den Speicherbedarf von IBM Cloud Private und den Managementaufwand zu berechnen.

#### Formel 1

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

Tabelle 4. Beschreibung der Variablen in Formel 1

| Variablen	| Beschreibung |	Einheit |	VSAN-Beispiel | NFS-Beispiel |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	Die Anzahl der tatsächlich für Workloads und Services in der Umgebung verfügbaren Kerne |	Kerne |	38	| 43 |
| HostCount	| Die Anzahl der Hosts im Standardcluster	| Hosts | 4	| 4 |
| HostCoreCount	| Die Anzahl der Rohkerne, die in jedem Host im Standardcluster verfügbar sind |	Kerne |	16 | 16 |
| HostOverheadCores	| Die Anzahl der Kerne, die vom ESXi-Server für Systemaufwand reserviert werden (entspricht 0,1 Kernen) | Kerne	| 0,1 |	0,1 |
| MgmtOverheadCores | Die Anzahl der Kerne, die von den vCenter Server-Managementkomponenten (vCenter Server, PSC, AD/DNS, Edges) reserviert werden (entspricht fünf Kernen)	| Kerne	| 5	| 5 |
| vSphereHAHostTolerance |	Die Anzahl der Hosts, die in der vSphere-HA-Konfiguration toleriert werden können (entspricht einem Host) |	Hosts	 | 1 | 1 |
| HostVsanOverheadCorePercentage |  Der Prozentsatz der von vSAN verwendeten Kerne eines Hosts (entspricht 10 % oder 0 % (falls der Host kein vSAN-Host ist) | % | 10% |	0% |

#### Formel 2

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

Tabelle 5. Beschreibung der Variablen in Formel 2

| Variablen	| Beschreibung |	Einheit |	VSAN-Beispiel | NFS-Beispiel |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| Der tatsächlich für Workloads und Services in der Umgebung verfügbare Speicher in GB | GB | 	693	| 860 |
| HostCount	| Die Anzahl der Hosts im Standardcluster | Hosts | 6	| 6 |
| HostMemory |	Der Rohspeicher in GB, der in jedem Host im Standardcluster verfügbar ist |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | Die Kapazität (in GB) jeder vSAN-Kapazitäts-SSD-Platte dieses Hosts, die 960, 1.946 oder 3.891 entspricht bzw. 0 GB (falls der Host kein vSAN-Host ist) | GB |	960 | 0 |
| HostOverheadMemory |	 Der Speicher in GB, der vom ESXi-Server für Systemaufwand reserviert wird (entspricht 4,6 GB) |	GB	| 4,6 |	4,6 |
| MgmtOverheadMemory |	Der Speicher in GB, der von den vCenter Server-Managementkomponenten (vCenter Server, PSC, AD/DNS, Edges) reserviert wird (entspricht 77 GB) | GB | 77 | 77 |
| vSphereHAHostTolerance |Die Anzahl der Hosts, die in der vSphere-HA-Konfiguration toleriert werden können (entspricht einem Host) | Hosts	 | 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | Der Speicher in GB, der vom vSAN-Management reserviert wird (dargestellt als Prozentsatz einer der vSAN-Kapazitätsplatten) - entspricht 2,75 % |	% | 2,75%	| 2,75% |
| HostVsanOverheadMemory | Der Speicher in GB, der vom vSAN-Management reserviert wird (unabhängig von der Plattengröße) - entspricht 7 GB oder 0 GB (falls der Host kein vSAN-Host ist)	| GB |  7	| 0 |

## Hinweise zur Installation von IBM Cloud Private Hosted

* Stellen Sie sicher, dass Sie über die erforderliche Lizenz verfügen, bevor Sie den {{site.data.keyword.cloud_notm}} Private Hosted-Service installieren. Vergewissern Sie sich, dass Ihre Lizenz nicht nur die erste {{site.data.keyword.cloud_notm}} Private Hosted-Bereitstellung unterstützt, sondern auch eine zukünftige Erweiterung Ihrer {{site.data.keyword.cloud_notm}} Private Hosted-Infrastruktur berücksichtigt.
* Für die {{site.data.keyword.cloud_notm}} Private Hosted-Bereitstellungen in einer einsatzbereiten Umgebung werden 64 GB RAM pro Host nicht unterstützt. Aus diesem Grund müssen Sie eine Option auswählen, die größer als 64 GB für **RAM** ist.
* Bevor der Service "{{site.data.keyword.cloud_notm}} Private Hosted" in Ihrer Umgebung installiert wird, wird eine Prüfung für die verfügbare Kapazität des Standardclusters in der Umgebung ausgeführt, um sicherzustellen, dass die Servicekomponenten angepasst werden können. Wenn die Kapazitätsprüfung fehlschlägt, wird der Service nicht installiert und der Servicestatus wird in der Konsole auf **Kapazitätsprüfung fehlgeschlagen** festgelegt. Darüber hinaus wird eine Konsolennachricht mit weiteren Details angezeigt und Sie werden per E-Mail benachrichtigt. Um den Service zu installieren, müssen Sie die Kapazität in Ihrem Standardcluster erhöhen, indem Sie entweder mehr Hosts hinzufügen oder Arbeitsspeicher, CPU oder Plattenspeicherplatz freigeben und anschließend den Service in der Konsole erneut hinzufügen. Danach können Sie den vorhandenen Service mit dem Status **Kapazitätsüberprüfung fehlgeschlagen** entfernen, indem Sie auf das Symbol **Löschen** neben dem Service klicken.

## Hinweise zur Deinstallation von IBM Cloud Private Hosted

* {{site.data.keyword.cloud_notm}} löscht nur die virtuellen Maschinen (VMs), die während der Erstinstallation des {{site.data.keyword.cloud_notm}} Private Hosted-Service bereitgestellt wurden. Jeder nach der Installation bereitgestellte Knoten wird nicht bereinigt.
* {{site.data.keyword.cloud_notm}} löscht das VXLAN, den DLR und das Edge-Gateway, das während der ersten Bereitstellung des {{site.data.keyword.cloud_notm}} Private Hosted-Service erstellt wurde. Die VMs, die Sie in VXLAN bereitgestellt haben, verlieren die Verbindung, sobald der {{site.data.keyword.cloud_notm}} Private Hosted-Service gestartet wird.

### Zugehörige Links

* [IBM Cloud Private Hosted bestellen](../services/icp_ordering.html)
* [vCenter Server und IBM Cloud Private - Leitfaden](../archiref/vcsicp/vcsicp-intro.html)
* [Ticket für IBM Cloud Private öffnen](https://www.ibm.com/mysupport/s/?language=en_US)

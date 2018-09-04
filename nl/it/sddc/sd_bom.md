---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Distinta base di Cloud Foundation

Esamina le informazioni relative alla distinta base (Diba) per le istanze VMware Cloud Foundation.

## Diba di VLAN per le istanze Cloud Foundation

La seguente tabella mostra in dettaglio le informazioni sulla Diba per le VLAN di Cloud Foundation.

Tabella 1. Diba per le VLAN nelle istanze Cloud Foundation

| VLAN      | Tipo      | Dettagli      |
|:----------|:----------|:-------------|
| VLAN1     | Pubblica, Primaria | Assegnata ai server ESXi fisici per l'accesso alla rete pubblica. Non utilizzata dopo la distribuzione iniziale. Disponibile per l'accesso a Internet. |
| VLAN2     | Privata A, Primaria | Assegnata da {{site.data.keyword.cloud}} ai server ESXi fisici. Utilizzata dall'interfaccia di gestione per il traffico di gestione VMware vSphere.<br><br>Assegnata alle VM (macchine virtuali) che funzionano come componenti di gestione.<br><br>Assegnata al VTEP (VXLAN Tunnel Endpoint) VMware NSX |
| VLAN3     | Privata B, Portatile | Assegnata a VMware vSAN, se utilizzato.<br><br>Assegnata a VMware NFS, se utilizzato.<br><br>Assegnata a VMware vSphere vMotion. |

## Diba di software per le istanze Cloud Foundation

La seguente tabella mostra in dettaglio le informazioni sulla Diba per i componenti software di Cloud Foundation.

Tabella 2. Diba per i componenti software nelle istanze Cloud Foundation

| Produttore | Componente                                | Versione      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 U1g (ESXi 6.5u1 con il livello di patch ESXi650-201803001 applicato) |
| VMware       | vCenter Server Appliance                 | 6.5 Aggiornamento 1g |
| VMware       | Platform Services Controller             | 6.5 Aggiornamento 1g |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX per vSphere                          | 6.3.5        |
| VMware       | SDDC Manager                             | 2.4          |
| IBM          | CloudDriver                              | 2.5          |
| Microsoft    | Windows Server Standard edition (64-bit) | 2012R2       |

## Impostazioni di configurazione avanzate per i server ESXi

Riesamina la seguente tabella per una panoramica delle impostazioni di configurazione avanzate applicate sui server ESXi a seconda che l'istanza Cloud Foundation sia distribuita nella V2.2 o successive o aggiornata alla V2.2 o successive da una release della V2.1 o precedenti.

Tabella 3. Impostazioni di configurazione avanzate dei server ESXi per le istanze e i cluster Cloud Foundation

| Impostazione di configurazione | Se appena distribuita nella V2.2 o successiva  | Se aggiornata dalla V2.1 o precedente |   
|:------------- |:------------- |:------------- |
| Dimensione heap TCP/IP | **TcpipHeapSize** = 32 | Non impostato |
| Numero massimo di heap TCP/IP | **TcpipHeapMax** = 1536 | Non impostato |  
| Numero massimo di volumi | **MaxVolumes** = 256 | Entrambi **/NFS/MaxVolumes** e **/NFS41/MaxVolumes** = 256 |  
| Numero massimo di errori heartbeat | **HeartbeatMaxFailures** = 10 | Non impostato |  
| Frequenza heartbeat | **HeartbeatFrequency** = 12 | Non impostato |  
| Timeout heartbeat | **HeartbeatTimeout** = 5 | Non impostato |
| Profondità massima della coda | **MaxQueueDepth** = 64 | Non impostato |
| Dimensione campione completa della coda | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Soglia completa della coda | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

**Note**:
* L'impostazione **MaxVolumes** è obbligatoria per il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} perché il servizio potrebbe utilizzare più del numero predefinito di montaggi NFS sul server ESXi.
* Il valore **Non impostato** per un'impostazione di configurazione indica che la nuova impostazione non viene applicata automaticamente, poiché richiede il riavvio dei server ESXi, il che potrebbe causare un'interruzione.

  Si consiglia di modificare le impostazioni di configurazione **Non impostato** nei nuovi valori per garantire coerenza tra tutte le istanze e per consentire il supporto adeguato per l'espansione dell'archiviazione. IBM prevede di eseguire test solo con queste nuove impostazioni per tutte le release di {{site.data.keyword.vmwaresolutions_short}} V2.2 e versioni successive.

  Per ulteriori informazioni, vedi [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239).

### Link correlati

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Panoramica di Cloud Foundation](sd_cloudfoundationoverview.html)
* [Pianificazione per le istanze Cloud Foundation](sd_planning.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Impostazioni cluster

Prima dell'aggiunta dell'archiviazione collegata, la soluzione vCenter Server non abilitava funzioni avanzate quali vSphere DRS (Distributed Resource Scheduler) e vSphere HA (High Availability). Con l'aggiunta del dispositivo di archiviazione collegato NFS, queste funzioni sono abilitate sul cluster con le impostazioni elencate nelle seguenti sezioni.

## vSphere Distributed Resource Scheduler

Due funzioni principali sono abilitate quando attivi vSphere DRS su un cluster: Load Balancing (Bilanciamento del carico) e Power Management (Gestione dell'alimentazione).

### Bilanciamento del carico

Con il bilanciamento del carico, la distribuzione e l'utilizzo delle risorse di CPU e memoria per tutti gli host e le macchine virtuali (VM, Virtual Machine) nel cluster sono monitorati costantemente. DRS confronta queste metriche a un utilizzo delle risorse ideale, dati gli attributi dei pool di risorse e delle VM del cluster e la domanda attuale. Completa o suggerisce quindi le migrazioni di VM come necessario.

Quando una VM viene accesa per la prima volta nel cluster, DRS prova a mantenere un corretto bilanciamento del carico posizionando la VM su un host appropriato oppure formulando un suggerimento. Le impostazioni di posizionamento o suggerimento sono impostate nella sezione DRS Automation delle impostazioni del cluster.

In questa progettazione, il livello di DRS Automation è impostato su un'indicazione di Fully Automated (Completamente automatizzato) in modo che, quando vengono accese, le VM vengono automaticamente posizionate sugli host con una capacità sufficiente. Le VM vengono anche automaticamente migrate da un host a un altro per bilanciare il carico del cluster. Inoltre, la soglia di migrazione del cluster DRS è impostata al punto intermedio tra il conservativo e l'aggressivo in modo tale che vengano applicati i suggerimenti con priorità 1, priorità 2 e priorità 3. vCenter Server fornisce almeno dei buoni miglioramenti al bilanciamento del carico del cluster.

La seguente tabella mostra le impostazioni per il cluster vSphere DRS nel client web VMware vSphere.

Tabella 1. Impostazioni di DRS Automation per il cluster vSphere DRS

| Impostazione             | Valore  |
|:------------------- |:------ |
| Turn ON vSphere DRS | Selezionato |
| Automation Level | Fully Automated |
| Migration Threshold | Applicare i suggerimenti con priorità 1, priorità 2 e priorità 3. |
| Enable individual machine automation levels | Selezionato, impostato su 15 ms |

Per ulteriori informazioni sulla configurazione di queste impostazioni nel client web vSphere, vedi [Set a Custom Automation Level for a Virtual Machine in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-C21C0609-923B-46FB-920C-887F00DBCAB9.html).

Insieme al livello di automazione e alla soglia di migrazione del cluster, questa progettazione abilita l'automazione delle VM in modo che tu possa sovrascrivere i valori per le singole VM. Un controllo più granulare delle VM abilita un'ulteriore indicazione della priorità al bilanciamento del carico delle VM.

### Power Management

Quando la funzione VMware Distributed Power Management è abilitata, DRS confronta la capacità a livello di cluster e host con le domande delle VM del cluster, inclusa la recente domanda a livello cronologico. La funzione Power Management (Gestione dell'alimentazione) mette, o suggerisce di farlo, gli host in modalità di alimentazione in standby, se viene rilevata una capacità in eccesso sufficiente, oppure in modalità di acceso, se è necessaria della capacità. A seconda dei suggerimenti relativi allo stato di alimentazione degli host risultanti, potrebbe anche essere necessario migrare le VM verso e dagli host.
In questa progettazione, la gestione dell'alimentazione è disabilitata poiché non vi è alcun vantaggio operativo o finanziario nell'accensione e spegnimento degli host nel cluster.

## vSphere High Availability

vSphere fornisce l'elevata disponibilità per le VM eseguendone il pooling, insieme agli host su cui risiedono, in un cluster. Gli host nel cluster sono monitorati e, se si verifica un malfunzionamento, le VM su un host malfunzionante vengono riavviate su host alternativi.
In questa progettazione, vSphere High Availability è abilitata con Host monitoring e VM monitoring.

### Host monitoring

Host monitoring consente agli host nel cluster di scambiare heartbeat di rete e abilita vSphere HA quando rileva dei malfunzionamenti. Questa funzione è abilitata in questa progettazione.

### VM monitoring

La funzione VM monitoring utilizza le informazioni di heartbeat acquisite da VMware Tools come un proxy per la disponibilità del sistema operativo guest. VM monitoring consente a vSphere HA di reimpostare o riavviare automaticamente le singole VM che non hanno più la loro capacità di heartbeat. Questa progettazione abilita il monitoraggio sia delle VM che delle applicazioni.

#### Failure Conditions and VM Response

Le condizioni di errore definiscono in che modo si verificano le condizioni di errore delle VM e la risposta data a ciascuna di tali condizioni. In questa progettazione, la priorità di riavvio della VM (VM restart priority) è impostata su Medium. Riesaminare questo valore e regolare le impostazioni in modo che la priorità di riavvio corrisponda all'importanza del carico di lavoro. Inoltre, la risposta per l'isolamento host (Response for Host Isolation) è impostata su “Power off and restart VMs” in modo che le VM non siano influenzate da un host isolato nel cluster. Il resto dei valori per questa impostazione sono impostati sul valore predefinito.

La seguente tabella mostra le impostazioni per il cluster vSphere HA nel client web VMware vSphere.

Tabella 2. Impostazioni delle condizioni di errore e della risposta delle VM per il cluster vSphere HA

| Impostazione             | Valore  |
|:------------------- |:------ |
| VM restart priority | Medium |
| Response for Host Isolation | Power off and restart VMs |
| Response for Datastore with Permanent Device Loss (PDL) | Disabled |
| Response for Datastore with All Paths Down (APD) | Disabled |
| Response for APD recovery after APD timeout | Disabled |
| VM monitoring sensitivity | Custom |
| Failure interval | 50 s |
| Minimum uptime | 90 s |
| Maximum per-VM resets | 10 |
| Maximum resets time window | Within 1 hrs |

Per ulteriori informazioni sulla configurazione di queste impostazioni nel client web vSphere, vedi [Configure Virtual Machine Responses](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.avail.doc/GUID-3DAED2B1-55B8-4877-BD0F-BC57C10A516C.html).

#### Admission Control

vCenter Server utilizza la funzione Admission Control (Controllo di ammissione) per garantire che siano disponibili risorse sufficienti in un cluster per fornire la protezione da failover e per garantire che le prenotazioni di risorse VM siano rispettate. In questa progettazione, la capacità di failover è riservata specificando una percentuale delle risorse del cluster. La capacità di failover definita è impostata sul 25% della CPU e il 25% della memoria.

#### Datastore Heartbeating

vSphere HA utilizza la funzione Datastore Heartbeating (Heartbeat degli archivi dati) per identificare gli host malfunzionanti e quelli che risiedono su una partizione di rete. Datastore Heartbeating consente a vSphere HA di monitorare gli host quando si verifica una partizione della rete di gestione e di continuare a rispondere alle condizioni di errore che si verificano. In questa progettazione, la politica di selezione di Datastore Heartbeating è impostata su “Automatically select datastores accessible from the host”.

### Link correlati

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)

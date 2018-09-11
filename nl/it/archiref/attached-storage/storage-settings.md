---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-17"

---

# Impostazioni di archiviazione

Questa progettazione supporta l'allegato dell'archiviazione condivisa tramite NFS v3 e NFS v4.1 (NFS v4 non è supportato). Dopo che hai ordinato VMware vCenter Server on {{site.data.keyword.cloud}}, determini quale versione NFS utilizzare per l'ambiente.

Se da una parte NFS v4.1 introduce delle prestazioni e una disponibilità migliori tramite il bilanciamento del carico e i percorsi multipli, dall'altra limita l'utilizzo delle funzioni vSphere, comprese Storage DRS, Storage I/O Control e l'uso di Site Recovery Manager.

La seguente tabella elenca i protocolli NFS e il supporto per le funzioni vSphere quando si utilizza vSphere 6.0.

Tabella 1. Protocolli NFS e funzioni vSphere

| Funzione vSphere | NFS v3 | NFS v4.1 |
|:--------------- |:------ |:-------- |
| vMotion and Storage vMotion | Sì | Sì |
| High Availability (HA) | Sì | Sì |
| Fault Tolerance (FT) | Sì | Sì |
| Distributed Resource Scheduler (DRS) | Sì | Sì |
| Host Profiles | Sì | Sì |
| Storage DRS | Sì | No |
| Storage I/O Control (SIOC) | Sì | No |
| Site Recovery Manager | Sì | No |
| Virtual Volumes | Sì | No |

**Nota**: tutta l'archiviazione collegata per questa progettazione è limitata all'archiviazione {{site.data.keyword.cloud_notm}} disponibile nello stesso {{site.data.keyword.CloudDataCent_notm}} della soluzione vCenter Server. Inoltre, gli archivi dati NFS v3 e 4.1 vengono montati utilizzando la stessa versione NFS su tutti gli host e di tutti i dischi virtuali archiviati nell'archivio dati viene eseguito, per impostazione predefinita, il thin-provisioning.

## Utilizzo di NFS v3 per l'archiviazione collegata

Quando NFS v3 viene scelto come metodo preferito per collegare la condivisione NFS, l'architettura è tale che utilizza un singolo indirizzo IP dall'archiviazione {{site.data.keyword.cloud_notm}} per stabilire la connessione alla condivisione. Inoltre, la condivisione NFS viene collegata a tutti gli host nel cluster di vCenter Server e posizionata in un cluster di archivi dati con Storage DRS abilitato.

### vSphere Storage DRS (Distributed Resource Scheduler)

Storage DRS ti consente di gestire le risorse aggregate di un cluster di archivi dati. Quando Storage DRS è attivato, fornisce suggerimenti per la migrazione e il posizionamento dei dischi delle VM (virtual machine) per bilanciare spazio e risorse di I/O tra gli archivi dati nel cluster di archivi dati.

Quando Storage DRS è attivato, sono disponibili le seguenti funzioni:
* Bilanciamento del carico dello spazio tra gli archivi dati in un cluster di archivi dati
* Bilanciamento del carico dell'I/O tra gli archivi dati in un cluster di archivi dati
* Posizione iniziale per i dischi virtuali in base allo spazio e al carico di lavoro di I/O.

In questa progettazione, Storage DRS è abilitato con il livello di automazione impostato su “Fully Automated”. Di conseguenza, i file non vengono migrati automaticamente per ottimizzare l'utilizzo delle risorse sul cluster di dati. Nota che tutte le altre opzioni di Storage DRS sono impostate su “Use cluster settings” poiché il cluster è completamente automatizzato.

### Impostazioni di runtime di Storage DRS per NFS v3

L'aggressività di Storage DRS è determinata specificando le soglie per lo spazio utilizzato e la latenza I/O. Storage DRS raccoglie le informazioni sull'utilizzo delle risorse per gli archivi dati in un cluster di archivi dati. vCenter Server utilizza queste informazioni per generare suggerimenti per il posizionamento di dischi virtuali sugli archivi dati.

Quando per un cluster di archivi dati è impostato un livello di aggressività basso, Storage DRS consiglia le migrazioni Storage vMotion solo quando necessario, ad esempio se il carico di I/O, l'utilizzo dello spazio o il loro squilibrio è elevato. Quando per un cluster di archivi dati è impostato un livello di aggressività elevato, Storage DRS consiglia le migrazioni ogni qualvolta il cluster di archivi dati può trarre vantaggio dal bilanciamento del carico di I/O e dello spazio.

Nel cluster di archivi dati sono disponibili le seguenti categorie di soglia:

* Space Utilization: Storage DRS genera i suggerimenti o esegue le migrazioni quando la percentuale di utilizzo di spazio sull'archivio dati è superiore alla soglia da te impostata nel client web vSphere.
* I/O Latency: Storage DRS genera i suggerimenti o esegue le migrazioni quando la latenza I/O novantesima percentile misurata su una giornata per l'archivio dati è superiore alla soglia.

In questa progettazione, le impostazioni di runtime di Storage DRS sono abilitate e le soglie sono mantenute ai loro rispettivi valori predefiniti. Si consiglia vivamente di modificare questi valori in base ai requisiti di I/O del carico di lavoro e alla sensibilità alla latenza.

La seguente tabella mostra le impostazioni nel client web VMware vSphere.

Tabella 2. Impostazioni di runtime di Storage DRS

| Impostazione       | Valore  |
|:--------------- |:------ |
| Enable I/O metric for SDRS recommendations | Selezionato |
| Utilized space | Selezionato, impostato su 80% |
| I/O latency threshold | 15 ms |

Per ulteriori informazioni sulla configurazione di queste impostazioni nel client web vSphere, vedi
[Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

### SIOC (Storage I/O Control) per NFS v3

Quando SIOC è abilitato nell'ambiente, modifica la lunghezza della coda del dispositivo per la singola VM. La modifica alla lunghezza della coda del dispositivo riduce la coda dell'array di archiviazione per tutte le VM a una condivisione e una frequenza uguali della coda di archiviazione. SIOC agisce solo se le risorse sono vincolate e la latenza I/O dell'archiviazione è superiore a una soglia definita.

Per determinare quando un dispositivo di archiviazione è congestionato o vincolato, SIOC richiede una soglia definita. La latenza della soglia di congestione è diversa per i vari tipi di archiviazione. Questa progettazione suggerisce e implementa una latenza di soglia di 10 millisecondi.

Puoi anche limitare i singoli dischi virtuali per le singole VM oppure concedere loro condivisioni differenti con SIOC. La limitazione di dischi e la concessione di condivisioni differenti ti consente di mettere in corrispondenza e allineare l'ambiente al carico di lavoro con il numero di IOPS di volume di archiviazione file acquisito. Il limite è impostato da IOPS e non è possibile impostare un peso o condivisioni ("Shares") differenti.

Le condivisioni di dischi virtuali impostate su "High" (2.000 condivisioni) ricevono il doppio dell'I/O di un disco impostato su "Normal" (1.000 condivisioni) e il quadruplo di uno impostato su "Low" (500 condivisioni). Normal è il valore predefinito per tutte le VM, quindi devi regolare i valori al di sopra o al di sotto di "Normal" per le VM che lo richiedono.

### Archiviazione aggiuntiva per NFS v3

Quando occorre aggiungere dell'archiviazione aggiuntiva all'ambiente a causa di spazio insufficiente o di una latenza elevata, puoi ordinare un'altra condivisione NFS dalla console. Una volta ordinata la condivisione, l'automazione collega l'esportazione agli host vSphere ESXi nel cluster e ne esegue il posizionamento nel cluster di archiviazione menzionato in precedenza. Posizionare la nuova condivisione NFS nel cluster di archiviazione ridimensiona in modo incrementale, efficacemente e senza soluzione di continuità, l'archiviazione associata all'ambiente senza lasciarti l'incombenza delle migrazioni a livello di archiviazione.

## Utilizzo di NFV v4.1 per l'archiviazione collegata

Quando NFS v4.1 viene scelto come metodo preferito per collegare la condivisione NFS, l'architettura è tale che utilizza più indirizzi IP dall'archiviazione {{site.data.keyword.cloud_notm}} per stabilire la connessione alla condivisione. La condivisione è collegata a tutti gli host nel cluster vCenter Server ma non è posizionata in un cluster di archivi dati a causa della limitazione di vSphere relativa all'utilizzo di Storage DRS con NFS v4.1.

**Nota**: NFS 4.1 con vSphere 6.0 non supporta l'accelerazione hardware. Questa limitazione non consente la creazione di dischi virtuali thick sugli archivi dati NFS v4.1.

### Archiviazione aggiuntiva per NFV v4.1

Quando occorre aggiungere dell'archiviazione aggiuntiva all'ambiente a causa di spazio insufficiente o di una latenza elevata, puoi ordinare un'altra condivisione NFS dalla console. Una volta ordinata la condivisione, l'automazione collega l'esportazione agli host vSphere ESXi nel cluster. Devi quindi migrare le VM e bilanciare il carico degli archivi dati in modo che lo spazio sia utilizzato in modo appropriato e che i requisiti di latenza siano soddisfatti.

## Parametri di configurazione avanzata

Indipendentemente dal fatto che tu scelga NFS v3 o NFS v4.1, questa progettazione aggiunge dei parametri di configurazione avanzata che sono suggeriti da {{site.data.keyword.cloud_notm}}. Di conseguenza, i seguenti parametri sono impostati su ogni host vSphere ESXi collegato alla condivisione NFS {{site.data.keyword.cloud_notm}}.

Tabella 3. Parametri di configurazione avanzata NFS

| Parametro       | Valore  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MazQueueDepth | 64 |

### Link correlati

* [Panoramica della soluzione](../solution/solution_overview.html)

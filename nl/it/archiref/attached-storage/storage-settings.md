---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configurazione e impostazioni per l'archiviazione collegata

Questa progettazione supporta il collegamento dell'archiviazione condivisa solo tramite NFS v3. NFS v4 e v4.1 non sono supportati.

L'archiviazione collegata per questa progettazione è limitata all'archiviazione {{site.data.keyword.cloud_notm}} disponibile nello stesso {{site.data.keyword.CloudDataCent_notm}} della soluzione vCenter Server. Inoltre, tutti i dischi virtuali memorizzati nell'archivio dati sono forniti con thin-provisioning per impostazione predefinita.
{:note}

L'architettura specifica che gli archivi dati NFS v3 vengono collegati utilizzando il nome DNS dall'archiviazione {{site.data.keyword.cloud_notm}} per connettersi alla condivisione. La condivisione NFS viene collegata a tutti gli host nel cluster di vCenter Server e posizionata in un cluster di archivi dati con Storage DRS abilitato.

## vSphere Storage DRS (Distributed Resource Scheduler)

Utilizza Storage DRS per gestire le risorse aggregate di un cluster di archivi dati. Quando Storage DRS è attivato, fornisce suggerimenti per la migrazione e il posizionamento dei dischi delle macchine virtuali (VM) per bilanciare spazio e risorse di I/O tra gli archivi dati nel cluster di archivi dati.

Quando Storage DRS è attivato, sono disponibili le seguenti funzioni:
* Bilanciamento del carico dello spazio tra gli archivi dati in un cluster di archivi dati
* Bilanciamento del carico dell'I/O tra gli archivi dati in un cluster di archivi dati
* Posizione iniziale per i dischi virtuali in base allo spazio e al carico di lavoro di I/O.

In questa progettazione, Storage DRS è abilitato con il livello di automazione impostato su **Fully Automated**. Di conseguenza, i file vengono migrati automaticamente per ottimizzare l'utilizzo delle risorse nel cluster di dati. Poiché il cluster è completamente automatizzato, tutte le altre opzioni di Storage DRS sono impostate su **Use cluster settings**.

## Impostazioni di runtime di Storage DRS per NFS v3

L'aggressività di Storage DRS è determinata specificando le soglie per lo spazio utilizzato e la latenza I/O. Storage DRS raccoglie le informazioni sull'utilizzo delle risorse per gli archivi dati in un cluster di archivi dati. vCenter Server utilizza queste informazioni per generare suggerimenti per il posizionamento di dischi virtuali sugli archivi dati.

Quando per un cluster di archivi dati è impostato un livello di aggressività basso, Storage DRS consiglia le migrazioni Storage vMotion solo quando necessario. Ad esempio, se il carico di I/O, l'utilizzo dello spazio o il loro squilibrio è elevato, Storage DRS consiglia una migrazione. Se per un cluster di archivi dati è impostato un livello di aggressività elevato, Storage DRS consiglia le migrazioni ogni qualvolta il cluster di archivi dati può trarre vantaggio dal bilanciamento del carico di I/O e dello spazio.

Nel cluster di archivi dati sono disponibili le seguenti categorie di soglia.

* Space Utilization: Storage DRS genera i suggerimenti o esegue le migrazioni quando la percentuale di utilizzo di spazio sull'archivio dati è superiore alla soglia da te impostata nel client web vSphere.
* I/O Latency: Storage DRS genera i suggerimenti o esegue le migrazioni quando la latenza I/O novantesima percentile misurata su una giornata per l'archivio dati è superiore alla soglia.

In questa progettazione, le impostazioni di runtime di Storage DRS sono abilitate e le soglie sono mantenute ai loro rispettivi valori predefiniti. Modifica questi valori in base ai requisiti di I/O del carico di lavoro e alla sensibilità alla latenza.

La seguente tabella mostra le impostazioni nel client web VMware vSphere.

Tabella 1. Impostazioni di runtime di Storage DRS

| Impostazione       | Valore  |
|:--------------- |:------ |
| Enable I/O metric for SDRS recommendations | Selezionato |
| Utilized space | Selezionato, impostato su 80% |
| I/O latency threshold | 15 ms |

Per ulteriori informazioni sulla configurazione di queste impostazioni nel client web vSphere, vedi
[Set Storage DRS Runtime Rules in the vSphere Web Client](https://docs.vmware.com/en/VMware-vSphere/5.5/com.vmware.vsphere.resmgmt.doc/GUID-AD2D13CE-539B-48C3-BBC9-E55A834874F0.html).

## SIOC (Storage I/O Control) per NFS v3

Quando SIOC (Storage I/O Control) viene abilitato nell'ambiente, modifica la lunghezza della coda del dispositivo per la singola VM. La modifica alla lunghezza della coda del dispositivo riduce la coda dell'array di archiviazione per tutte le VM a una condivisione e una frequenza uguali della coda di archiviazione. SIOC si collega solo se le risorse sono vincolate e la latenza dell'I/O di archiviazione è superiore a una soglia definita.

Per determinare quando un dispositivo di archiviazione è congestionato o vincolato, SIOC richiede una soglia definita. La latenza della soglia di congestione è diversa per i vari tipi di archiviazione. Questa progettazione suggerisce e implementa una latenza di soglia di 10 millisecondi.

Puoi limitare i singoli dischi virtuali per le singole VM oppure concedere loro condivisioni differenti con SIOC. La limitazione di dischi e la concessione di condivisioni differenti ti consente di mettere in corrispondenza e allineare l'ambiente al carico di lavoro con il numero di IOPS di volume di archiviazione file acquisito. Il limite è impostato da IOPS ed è possibile impostare un peso o condivisioni differenti.

Le condivisioni di dischi virtuali impostate su **High** (2000 condivisioni) ricevono il doppio di I/O di un disco impostato su **Normal** (1.000 condivisioni) e quattro volte di più rispetto a un disco impostato su **Low** (500 condivisioni). **Normal** è il valore predefinito per tutte le VM, pertanto devi regolare le impostazioni di **Normal** per le VM che lo richiedono.

## Archiviazione aggiuntiva per NFS v3

Quando occorre aggiungere dell'ulteriore archiviazione all'ambiente a causa di spazio insufficiente o di una latenza elevata, puoi ordinare un'altra condivisione NFS dalla console. Dopo aver ordinato la condivisione, collega l'esportazione agli host vSphere ESXi nel cluster e posizionale nel cluster di archiviazione. Posizionare la nuova condivisione NFS nel cluster di archiviazione ridimensiona in modo incrementale, efficacemente e senza soluzione di continuità, l'archiviazione associata all'ambiente senza lasciarti l'incombenza delle migrazioni a livello di archiviazione.

## Parametri di configurazione avanzata

Questa progettazione aggiunge parametri di configurazione avanzata consigliati da {{site.data.keyword.cloud_notm}}. Di conseguenza, i seguenti parametri sono impostati su ogni host vSphere ESXi collegato alla condivisione NFS {{site.data.keyword.cloud_notm}}.

Tabella 2. Parametri di configurazione avanzata di NFS

| Parametro       | Valore  |
|:--------------- |:------ |
| Net.TcpipHeapSize | 32 |
| Net.TcpipHeapMax | 512 |
| NFS.MaxVolumes | 256 |
| NFS.HeartbeatMaxFailures | 10 |
| NFS.HeartbeatFrequency  | 12 |
| NFS.HeartbeatTimeout | 5 |
| NFS.MaxQueueDepth | 64 |

### Link correlati

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)

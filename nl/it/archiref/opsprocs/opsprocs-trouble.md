---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# Risoluzione dei problemi
{: #opsprocs-trouble}

Per risolvere i problemi dell'istanza vCenter Server, gli amministratori di sistema devono identificare i sintomi del problema, determinare quali componenti della soluzione sono interessati, ricercare e proporre una correzione o una soluzione temporanea e verificare la correzione.

* Identificazione dei sintomi - Una serie di possibili cause potrebbero portare a prestazioni insufficienti o nulle della tua istanza. Il primo passo in un'efficiente risoluzione dei problemi è quello di identificare esattamente cosa non va. Questi sintomi possono essere segnalati da: eventi e allarmi vSphere, Operations Management in 	{{site.data.keyword.cloud}} o tramite il tuo service desk da uno dei tuoi utenti.
* Isolamento dei componenti interessati - Dopo aver identificato i sintomi del problema, devi identificare i componenti software o hardware interessati e che potrebbero causare il problema e i componenti che non sono coinvolti. Strumenti come vCenter Operations Management in {{site.data.keyword.cloud_notm}} aiutano in questo passo.
* Proposta di una correzione o soluzione temporanea - Una volta compresi i sintomi e aver isolato i componenti, puoi ricercare possibili correzioni e soluzioni temporanee. Gli amministratori di sistema utilizzano anche il portale {{site.data.keyword.cloud_notm}}, inclusi gli scenari di risoluzione dei problemi indicati in questo documento nonché IBM ServiceNow e VMware Knowledgebase. Inoltre, ci sono molte pagine wiki e blog che potrebbero aiutarti. Per risoluzioni ancora più rapide, Operations Management in {{site.data.keyword.cloud_notm}} include una serie di rimedi per i problemi identificati.
* Verifica delle possibili soluzioni - Una volta che conosci i sintomi del problema, quali componenti sono coinvolti e hai proposto una correzione o soluzione temporanea, gli amministratori di sistema verificano sistematicamente le soluzioni fino a quando il problema non viene risolto.

vSphere include un sottosistema di eventi e allarmi configurabile dall'utente che tiene traccia degli eventi che si verificano all'interno dell'ambiente vSphere e memorizza i dati nei file di log e nel database vCenter. Questo sottosistema consente inoltre agli amministratori di sistema di specificare le condizioni in base alle quali vengono attivati gli allarmi. Gli allarmi cambiano lo stato da avvertenza ad allarmi più gravi man mano che cambiano le condizioni del sistema e possono attivare azioni di allarme automatizzate come inviare un messaggio email al team di amministratori di sistema. Questa funzionalità è utile se vuoi essere informato, o agire immediatamente, quando si verificano determinati eventi o condizioni per un oggetto di inventario specifico o per un gruppo di oggetti.

Ulteriori strumenti come quelli incorporati nell'architettura di Operations Management on {{site.data.keyword.cloud_notm}} forniscono una maggiore assistenza per: identificare i sintomi, isolare i componenti interessati e proporre una correzione o soluzione temporanea.

## Linee guida
{: #opsprocs-trouble-guidelines}

Le seguenti linee guida sono considerate procedure ottimali per la risoluzione dei problemi relativi a {{site.data.keyword.vmwaresolutions_short}}:
* Utilizza un approccio sistematico per la risoluzione dei problemi.
* Identifica se i sintomi sono correlati a disponibilità, utilizzo o configurazione:
 *  Disponibilità - Questi sintomi si riferiscono alla disponibilità dei componenti hardware e software e sono caratterizzati da una mancata risposta. Spesso la progettazione ad alta disponibilità maschera questi problemi in modo che non incidano direttamente sui carichi di lavoro e sugli utenti.
 * Utilizzo - Questi sintomi si riferiscono alla capacità e alle prestazioni e sono caratterizzati da lenta esecuzione o inabilità di caricamento. La gestione proattiva della capacità riduce drasticamente questi problemi.
 * Configurazione - Questi problemi vengono in genere rilevati nel provisioning di nuovi servizi o in seguito all'applicazione di una modifica. Le impostazioni errate possono apparire come sintomi di disponibilità o di utilizzo. Ad esempio, un indirizzo IP non corretto viene visualizzato come problema di disponibilità, mentre le impostazioni RAM della macchina virtuale (VM) troppo basse causano sintomi di utilizzo.
* Prova a isolare il problema a un componente nell'ambiente.
* Prendi nota in modo da poter tracciare i tuoi passi.
* Comprendi e documenta le tue versioni software.
* Documenta le tue sottoreti e l'utilizzo degli indirizzi IP, inclusi gli indirizzi VIP e NAT.
* Crea diagrammi della tua rete. Hai bisogno di diversi diagrammi che mostrino i livelli fisici (sottostanti) e logici (sovrapposizione). 
* Comprendi eventuali modifiche recenti apportate all'ambiente.
* Cerca l'impatto della correzione, non escludere alcuna interfaccia di gestione.
* Assicurati di avere i backup di tutti i componenti chiave, nel caso debbano essere ricaricati o reimpostati.
* Non modificare più di una cosa alla volta.
* Documenta ogni modifica e il suo risultato.
* Quando effettui una richiesta di supporto, assicurati di documentare attentamente e fornire informazioni pertinenti. Sii molto chiaro nel descrivere i sintomi che stai notando e nell'identificare i componenti che ritieni non funzionino nel modo appropriato. Assicurati di utilizzare la terminologia corretta. Cerca di minimizzare ogni confusione o ambiguità nella scelta delle parole.
* I file di configurazione di vSphere ESXi e vCenter Server controllano il comportamento del sistema; scopri dove si trovano. La maggior parte delle impostazioni dei file di configurazione vengono impostate durante l'installazione, ma possono essere modificate dopo l'installazione.
* I file di log acquisiscono i messaggi generati dal kernel e da diversi sottosistemi e servizi. I servizi vSphere ESXi e vCenter mantengono i file di log separati; scopri dove si trovano e come potervi accedere.
* Comprendi come utilizzare i popolari strumenti di gestione del sistema per assistenza nella diagnostica.

Per ulteriori informazioni, vedi [Troubleshooting Guidelines KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}.

## Risoluzione dei problemi con i file di log
{: #opsprocs-trouble-logs}

I file di log sono un'ottima fonte di informazioni per la risoluzione dei problemi, tuttavia, in pratica, il numero di file di log e la grande quantità di voci in ogni log rendono difficile questa operazione. La sezione [Troubleshooting with Log Files KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} indica dove si trovano questi file di log nell'ambiente VMware. A causa del numero di file di log e della grande quantità di voci in ciascun log, dovresti considerare gli strumenti in Operations Management on {{site.data.keyword.cloud_notm}} come ausilio nell'acquisizione e nell'analisi dei log di evento.

## Scenari comuni di risoluzione dei problemi
{: #opsprocs-trouble-common}

Come ausilio per isolare i componenti interessati, questa documentazione sugli scenari comuni di risoluzione dei problemi è stata classificata come segue:

* Macchine virtuali - questi argomenti di risoluzione dei problemi forniscono indicazioni su potenziali problemi relativi alle VM.
* Host - questi argomenti di risoluzione dei problemi forniscono indicazioni sui problemi relativi agli host vSphere ESXi.
* Cluster - questi argomenti di risoluzione dei problemi forniscono indicazioni sulla disponibilità e sulla gestione delle risorse.
* Archiviazione - questi argomenti di risoluzione dei problemi forniscono indicazioni sulla risoluzione dei problemi di archiviazione di vSAN e NFS.
* Rete - questi argomenti di risoluzione dei problemi forniscono indicazioni sulla risoluzione dei problemi di rete.
* vCenter - questi argomenti di risoluzione dei problemi forniscono indicazioni sulla risoluzione dei problemi di vCenter.
* Licenze - questi argomenti di risoluzione dei problemi forniscono indicazioni sulla risoluzione dei problemi di licenza. Questi in genere riguardano i clienti che hanno portato le proprie licenze in {{site.data.keyword.cloud_notm}}.

### VM (Virtual Machine)
{: #opsprocs-trouble-common-vm}

Tabella 1. Risoluzione dei problemi relativi alle macchine virtuali

| Titolo | Descrizione |
|---|---|
| Risoluzione dei problemi generici della VM | Per ulteriori informazioni, vedi [Troubleshooting Virtual Machines](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}. |
| Problemi di prestazioni della VM | Per informazioni sulla risoluzione dei problemi relativi alle prestazioni delle VM, quali avvio lento del sistema operativo guest, scarse prestazioni delle applicazioni, eccessivi tempi di avvio per le applicazioni o applicazioni che smettono di rispondere, vedi [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}. |
| Ripristina VM orfana | Per informazioni sul ripristino di VM orfane, che sono VM esistenti nel database vCenter, ma non riconosciute dall'host vSphere ESXi, vedi [Knowledge - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}. |
| La VM non si accende | Per ulteriori informazioni, vedi [Troubleshooting a virtual machine that is unable to power on (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}. |
| La VM non si accende dopo la clonazione o la distribuzione da un template | L'[articolo VMware](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window} esamina i problemi che influiscono su una VM dopo che è stata clonata o distribuita da un template. |
| VMware Tools scaduto o non installato - VMware Tools deve essere installato sulle VM e mantenuto aggiornato. | [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} fornisce indicazioni su questa attività. |
| Vecchi dispositivi di rete della VM | Se i dispositivi di rete della VM non vengono mantenuti aggiornati, le prestazioni di rete e, di conseguenza, le prestazioni delle applicazioni potrebbero risentirne. Per ulteriori informazioni sulla distribuzione di un nuovo dispositivo e driver di rete virtuale, vedi [Choosing a network adapter for your virtual machine (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}. |
| Limite di memoria della macchina virtuale | I limiti di memoria vengono utilizzati spesso, tuttavia, se un sistema operativo guest non può accedere alla memoria di cui ha bisogno, le applicazioni all'interno del sistema operativo guest potrebbero non funzionare correttamente. Per ulteriori informazioni sulla risoluzione del problema, vedi [Configuring Resource Allocation Settings](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}. |
| Istantanee VM | Sebbene le istantanee siano molto utili, la quantità e la durata delle istantanee di una VM influiscono direttamente sulle prestazioni di tale VM. Per informazioni sulla risoluzione del problema, vedi [Consolidate Snapshots](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}. |
| Registrazione VM | Se la registrazione non è stata configurata correttamente, la capacità dell'archivio dati potrebbe essere influenzata negativamente. Per informazioni sulla risoluzione del problema, vedi [Configuring Logging Levels for the Guest Operating System](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}. |
| Risoluzione dei problemi di connessione di rete | I sintomi possono includere errori di connessione della VM alla rete o nessuna connettività di rete da o verso una singola VM. Per informazioni sulla risoluzione del problema, vedi [Troubleshooting virtual machine network connection issues (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}.  |
| Determinare se più CPU virtuali causano problemi di prestazioni  | Per informazioni sulla risoluzione dei problemi relativi alle prestazioni delle VM quando sono configurate con più CPU, vedi [Determining if multiple virtual CPUs are causing performance issues (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. Questi problemi possono includere una scarsa velocità di trasferimento durante la copia dei dati da o verso una VM, timeout dei lavori di backup o esecuzione dei lavori molto lenta o scarso rendimento di una VM.  |
| Una VM è stata spenta o riavviata  | Per informazioni sulla risoluzione del problema, vedi [Determining why a virtual machine was powered off or restarted (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}. |
| Una o più macchine virtuali hanno un tempo di risposta inadeguato |  Per informazioni sull'isolamento di un problema di prestazioni su un host vSphere ESXi, vedi [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. I problemi di prestazioni possono essere causati da restrizioni della CPU, uso eccessivo di memoria, latenza di archiviazione o latenza di rete. |

### Host vSphere ESXi
{: #opsprocs-trouble-common-host}

Tabella 2. Risoluzione dei problemi tipici degli host vSphere ESXi

| Titolo | Descrizione |
|---|---|
| Comandi ESXI |Per una panoramica delle interfacce della riga di comando in vSphere, dei comandi della shell ESXi e dei comandi della CLI (Command-Line Interface) VMware vSphere, vedi [Getting Started with vSphere Command-Line Interfaces](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}. |
| Stati degli host vSphere HA | Se vCenter riporta uno stato dell'host vSphere HA che indica una condizione di errore sull'host, è necessario effettuare una correzione in quanto questo problema può impedire a vSphere HA di riavviare le VM dopo un errore. Per ulteriori informazioni, vedi [Troubleshooting vSphere HA Host States](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}. |
| L'host vSphere ESXi è in uno stato di nessuna risposta | Per informazioni sulla risoluzione dei problemi di un host vSphere ESXi che non risponde, è disconnesso o le cui VM sembrano disabilitate in vCenter, vedi [ESX/ESXi hosts do not respond and is grayed out (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}. |
| Quando si accende una VM, viene visualizzato un errore File not found  | Per informazioni sulla ricreazione di un file di descrizione del disco virtuale (VMDK) perso, vedi [Recreating a missing virtual machine disk descriptor file (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}. |
| Problemi di prestazioni della VM |  Per informazioni sull'isolamento di un problema di prestazioni su un host vSphere ESXi, vedi [Troubleshooting ESX/ESXi virtual machine performance issues (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}. I problemi di prestazioni possono essere causati da restrizioni della CPU, uso eccessivo di memoria, latenza di archiviazione o latenza di rete. |
|  Bare Metal Server è inattivo | Se il Bare Metal Server che esegue vSphere ESXi non risponde o non è attivo, accedi all'IU o alla console di gestione {{site.data.keyword.cloud_notm}} e controlla lo stato. Se necessario, apri un caso di supporto per ottenere assistenza con il tuo Bare Metal Server. Per ulteriori informazioni, vedi [Gestione dei casi di supporto](/docs/get-support?topic=get-support-open-case#open-case){:new_window}. |
| L'host vSphere ESXi è in uno stato disconnesso o nessuna riposta  | Per ulteriori informazioni, vedi [Troubleshooting an ESXi/ESX host in non responding state (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}. |
| PSOD (Purple screen of death)  | Il PSOD (Purple Screen of Death) è un errore grave (panic) del kernel e il kernel vSphere ESXi (vmkernel) attiva questa misura di sicurezza in risposta a un evento/errore che è irreversibile e indica che la continuazione dell'esecuzione potrebbe comportare un rischio elevato per i servizi e le VM. Quando si verifica l'errore grave e l'host vSphere ESXi si arresta, l'host termina tutti i servizi in esecuzione su di esso insieme a tutte le VM ospitate. Le VM non si arrestano normalmente, ma piuttosto si spengono improvvisamente. Se l'host fa parte di un cluster e hai configurato l'HA, queste VM vengono riavviate sugli altri host nel cluster. Per ulteriori informazioni, vedi [Knowledge - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}. |

### Archiviazione
{: #opsprocs-trouble-common-storage}

Tabella 3. Risoluzione dei problemi tipici dell'archiviazione

| Titolo | Descrizione |
|---|---|
| Risoluzione dei problemi dell'archiviazione | Per ulteriori informazioni su prestazioni scarse, errori imprevedibili, danneggiamento del disco o danneggiamento della VM, vedi [Troubleshooting storage issues when using VMware products (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}. |
| Risoluzione dei problemi di vSAN | Per ulteriori informazioni, vedi [Failure Handling in vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}.  |
| Errore del disco vSAN | Per ulteriori informazioni sull'identificazione di un disco guasto e sulla richiesta di sostituzione, vedi [A hard disk/magnetic disk in a VMware vSAN disk group fails (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}. |
| Cancella i problemi di integrità vSAN | Nella pagina Monitor del client web VMware vSphere, potresti vedere avvisi e avvertenze relativi ai problemi di integrità vSAN. Per informazioni sulla cancellazione di questi problemi, vedi [Avvertenze e avvisi di integrità di Virtual SAN](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}.|
| Ribilanciamento di vSAN | Se i dischi segnalano errori nel controllo di integrità che indicano che il cluster non è bilanciato e che ci sono dei dischi che utilizzano molto spazio mentre altri ne hanno molto poco, devi eseguire un ribilanciamento proattivo. Questo avvia manualmente un ribilanciamento degli oggetti in un cluster vSAN. Per ulteriori informazioni sul ribilanciamento proattivo di vSAN e su quando potrebbe essere applicabile, vedi [vSAN proactive rebalance (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}. |
| Avvia test di integrità vSAN | Se sospetti che ci sia un problema con vSAN, puoi avviare un test di integrità per verificare che i componenti del cluster funzionino come previsto. L'esecuzione del test di creazione della VM crea una VM su ciascun host nel cluster e poi la elimina. Se queste attività hanno esito positivo, i componenti del cluster funzionano come previsto e il cluster è funzionale. Quindi viene utilizzato il test delle prestazioni di rete per rilevare e diagnosticare i problemi di connettività e per garantire che la larghezza di banda di rete tra gli host sia adeguata. Per ulteriori informazioni, vedi [Proactive Tests](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}. |
| Monitoraggio delle prestazioni vSAN | Per ulteriori informazioni, vedi [Monitoring vSAN Performance](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}. Sono disponibili grafici delle prestazioni per cluster, host, dischi fisici, VM e dischi virtuali. |
| Risoluzione dei problemi di vSAN | Per ulteriori informazioni, vedi [Handling Failures and Troubleshooting vSAN](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}. |


### Rete
{: #opsprocs-trouble-common-network}

Tabella 4. Risoluzione dei problemi tipici della rete

| Titolo | Descrizione |
|---|---|
|  La partizione /var/log di edge NSX è quasi piena sull'edge attivo | Per informazioni su una soluzione temporanea nel caso in cui ti venga segnalato che il disco Edge si sta riempiendo e rilevi che la partizione /var/log è quasi piena, vedi [NSX Edge /var/log is getting full on active Edge (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}.  |
| Verifica della larghezza di banda HCX  | Per informazioni sull'utilizzo di 'perftest' per trovare la larghezza di banda disponibile all'interno dei tunnel HCX se ritieni di avere un problema di larghezza di banda di rete con HCX, vedi [Steps to Run Perftest in HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}. Vengono eseguiti test bidirezionali per ogni perftest. Per la coppia di gateway, uno è all'interno del data center di origine, che chiamiamo OnPrem, e l'altro è in {{site.data.keyword.cloud_notm}}. Il modo in cui funziona la velocità effettiva di perftest è quello di far sì che il mittente tenti di inviare alla stessa velocità supportata dal link. Pertanto, per ogni test, vedrai una velocità del "mittente" superiore a quella del "destinatario" e puoi considerare la velocità del "destinatario" come il numero del risultato della velocità effettiva unidirezionale.|
| Risoluzione dei problemi di HCX | Per ulteriori informazioni, vedi [Risoluzione dei problemi di HCX](/docs/services/vmwaresolutions?topic=vmware-solutions-vcshcx-troubleshooting#vcshcx-troubleshooting){:new_window}. |
| Stato di sincronizzazione HCX con 0% di avanzamento e 0 byte con stato Error | Per ulteriori informazioni, vedi [HCX replication are in Syncing state with 0% progress and 0 bytes with status Error (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}. |
| Scarse prestazioni della rete VM | Esamina le impostazione della NIC virtuale della VM. VMware consiglia le NIC virtuali VMXNET 3 per le VM poiché è l'ultima generazione di schede NIC paravirtualizzate progettate da zero per le prestazioni. Controlla la compatibilità di VMXNET 3 utilizzando l'elenco di compatibilità VMware e, se supportato, modifica la NIC virtuale per ulteriori prestazioni di rete. Per ulteriori informazioni, vedi [Troubleshooting Networking](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}. |

### vCenter
{: #opsprocs-trouble-common-vcenter}

Tabella 5. Risoluzione dei problemi tipici di vCenter

| Titolo | Descrizione |
|---|---|
| Accesso alla console della macchina virtuale | Per ulteriori informazioni, vedi [Knowledge - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}. |
| Il nuovo certificato di vCenter Server non viene caricato | Dopo la sostituzione dei certificati vCenter Server predefiniti, è possibile che i nuovi certificati non vengano caricati. Per ulteriori informazioni, vedi [New vCenter Server Certificate Does Not Appear to Load](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}. |
| Impossibile connettere vCenter Server agli host gestiti | Dopo la sostituzione dei certificati vCenter Server predefiniti e il riavvio del sistema, vCenter Server non riesce a connettersi agli host gestiti. Per ulteriori informazioni, vedi [vCenter Server Cannot Connect to Managed Hosts](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}. |
| Impossibile configurare vSphere HA quando si utilizzano certificati SSL personalizzati | Dopo l'installazione dei certificati SSL personalizzati, i tentativi di abilitare vSphere High Availability (HA) non riescono. Per ulteriori informazioni, vedi [Cannot Configure vSphere HA When Using Custom SSL Certificates](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}. |

### Licenze
{: #opsprocs-trouble-common-licenses}

Tabella 6. Risoluzione dei problemi tipici delle licenze

| Titolo | Descrizione |
|---|---|
|  Configurazione della licenza incompatibile o non corretta | Per ulteriori informazioni, vedi [Troubleshooting Host Licensing](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}. |
| La VM non si accende | Potrebbe esserci un problema di licenza se non riesci ad accendere una VM su un host vSphere ESXi e ricevi il messaggio ``The 60-day evaluation period of the host is expired or the license of the host is expired``. Per ulteriori informazioni, vedi [Unable to Power On a Virtual Machine](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}. |
| Una funzione non è disponibile o non è possibile modificare una configurazione  | Per ulteriori informazioni, vedi [Unable to Configure or Use a Feature](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}.  |


## Link correlati
{: #opsprocs-trouble-links}
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [Linee guida per la risoluzione dei problemi - KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}
* [Risoluzione dei problemi con i file di log - KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [Raccolta di log di supporto](https://kb.vmware.com/s/article/1010705){:new_window}
* [Monitoraggio di eventi, allarmi e azioni automatizzate](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [File di log di sistema vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [Considerazioni sulla modifica delle risorse vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-30"

---

# Introduzione alle procedure operative
{: #opsprocs-intro}

Molte organizzazioni IT documentano le proprie procedure operative in un runbook. Un runbook è un insieme di documenti, riferimenti e procedure standardizzati che illustrano le attività IT ricorrenti più comuni. Lo staff IT fa riferimento al runbook per svolgere il proprio lavoro in modo ottimale. I runbook migliorano l'efficienza organizzativa attraverso la standardizzazione e favoriscono una migliore incorporazione dei dipendenti. Esistono in genere due tipi di runbook:

1. Una documentazione generale utilizzata per acquisire procedure, guide e attività. Solitamente è di natura generale e fa riferimento alla documentazione esistente fornita dai venditori.
2. Una documentazione specializzata scritta per l'azienda. Questa documentazione è specifica per un sistema, un'applicazione o una suite di applicazioni e non è inclusa nella documentazione dei fornitori. Quando documenti la tua documentazione specializzata, è consigliata la seguente struttura:

 * Panoramica - Una panoramica del servizio con sezioni che descrivono:
    * Qual è il servizio e perché il servizio è necessario all'azienda?
    * Chi sono i contatti principali per il servizio?
    * Come segnalare problemi con il servizio.
 * Build - Questa sezione si concentra sui team di sviluppo, sui principali componenti software del servizio e su come viene creato il servizio. Informazioni su prodotti software, posizioni di OVA, supporti di distribuzione o posizione del codice sorgente. I passi richiesti per l'assemblaggio o la distribuzione della release. Include tutte le istruzioni necessarie allo sviluppatore per iniziare a lavorare.
 * Distribuzione - Questa sezione si concentra sul team delle operazioni e su come distribuire il software. Include dettagli sull'hardware e sull'infrastruttura virtualizzata e su come creare le macchine virtuali (VM), tra cui: requisiti di vCPU, RAM e disco, versione e configurazione del sistema operativo e configurazione, middleware o pacchetti da installare. 
 * Procedure - Istruzioni dettagliate per attività comuni quali: aggiunta, modifica ed eliminazione, problemi comuni e relative soluzioni, consigli per la risoluzione dei problemi.
 * Risoluzione dei problemi - Un elenco di avvisi comuni dal sistema di monitoraggio, comprese le attività dettagliate per questi avvisi e le indicazioni generiche sulla risoluzione dei problemi del servizio.
 * Piani e procedure di ripristino di emergenza - Dettagli su come ripristinare il servizio in un'altra ubicazione a causa di un'emergenza nell'ubicazione principale.
 * SLA (service level agreement) - I parametri di servizio concordati quali gli accordi sui livelli operativi, gli indicatori dei punti chiave, gli obiettivi di disponibilità, gli obiettivi del punto di ripristino e gli obiettivi del tempo di ripristino.

La maggior parte delle organizzazioni IT dispone di più runbook che fungono da manuali di riferimento. Questa serie di documentazione è progettata per essere utilizzata come runbook generale per la tua organizzazione che utilizza le istanze vCenter Server. Mentre il contenuto di ciascun runbook è specifico per le esigenze dell'organizzazione, la metodologia di creazione del runbook è abbastanza standard e in due fasi:

1. La prima fase consiste nel decidere quali procedure devono essere documentate e, una volta elencate, documentare ciascuna di esse con dettagli sufficienti.
2. La seconda fase è continuativa e consiste nel gestire, aggiornare e correggere queste procedure, aggiungere nuove procedure e ritirare quelle che non sono più necessarie.

{{site.data.keyword.vmwaresolutions_full}} ti consente di utilizzare le competenze, le serie di strumenti e i runbook esistenti del tuo team in loco per gestire le tue istanze in {{site.data.keyword.cloud_notm}}. Come indicazione, la seguente documentazione generale copre le attività, le guide e le procedure comuni.

* Attività di configurazione - Queste sono le attività comuni che gli amministratori di sistema devono eseguire per personalizzare l'ambiente in base alle esigenze aziendali e rispondere alle richieste di servizio come: aggiungere nuove VM e aumentare la capacità. Queste attività sono raggruppate nella seguente struttura:
 * Indicazioni generiche
 * Procedure per VM
 * Procedure per vCenter
 * Procedure per host vSphere ESXi
 * Procedure per l'archiviazione
 * Procedure per la rete
* Allarmi - vSphere include un sottosistema di eventi e allarmi che tiene traccia degli eventi che si verificano nell'ambiente vSphere e rende disponibili queste informazioni in vCenter. Questa sezione descrive tale sottosistema e come abilitare e utilizzare gli allarmi nella tua azienda.
* Controlli giornalieri proattivi - Questi controlli consentono agli amministratori di sistema di mantenere integro l'ambiente. Se effettuati giornalmente, dovrebbero impedire che molti problemi comuni relativi alla capacità e alle prestazioni incidano sui carichi di lavoro.
* Risoluzione dei problemi - Anche quando si effettuano controlli giornalieri proattivi, si verificano dei problemi che influiscono sui carichi di lavoro. Pertanto, devi risolvere il problema sottostante il più rapidamente possibile. Queste guide alla risoluzione dei problemi e alcuni scenari di risoluzione dei problemi comuni aiutano gli amministratori di sistema a individuare e risolvere rapidamente tali problemi.
* Conformità - La guida alla conformità fornisce alcune informazioni approfondite su come mantenere la conformità dell'ambiente rispetto a un regime di conformità normativa o a una procedura ottimale del settore. Questa guida si concentra sulla guida di protezione VMware, che include una serie di elenchi documentati di procedure ottimali per un ambiente VMware.

Molte delle attività precedenti sono automatizzate in Operations Management on {{site.data.keyword.cloud_notm}} e, per quelle attività che non lo sono, questi strumenti rendono i processi manuali più facili per gli amministratori dei sistemi. È fondamentale che i tuoi componenti principali dell'ambiente VMware siano monitorati; in Operations Management on {{site.data.keyword.cloud_notm}}, questo si ottiene come segue:

## Operations Management on IBM Cloud
{: #opsprocs-intro-ops-mgmt}

Potresti disporre di strumenti aziendali che puoi utilizzare per monitorare e gestire la tua istanza vCenter Server. La Tabella 1 descrive i componenti principali dell'ambiente vCenter Server, perché devono essere monitorati e come vengono monitorati utilizzando Operations Management on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi la documentazione dell'architettura di riferimento.

Tabella 1. Componenti principali dell'ambiente vCenter Server

| Componente | Perché | Monitorato da  |
|---|---|---|
| vCenter | vCenter è il componente di gestione dell'infrastruttura che gestisce gli host vSphere e i costrutti virtualizzati come il cluster. vSAN viene monitorato tramite vCenter. La rete vSphere come gli switch distribuiti e i gruppi di porte vengono monitorati tramite vCenter. | vRealize Operations Manager (vROps) e VMware SDDC Health Management Pack. vRealize Log Insights (vRLI) raccoglie i dati di log da vCenter e il pacchetto di contenuti per vSphere aggiunge una comprensione specifica ai log e, a sua volta, invia gli avvisi a vROPs. |
| Host vSphere | Gli host vSphere forniscono CPU, RAM e rete virtualizzate alle VM di calcolo. | vROps tramite vCenter. vRLI raccoglie i dati di log |
| vSAN | vSAN fornisce un archivio dati consolidando l'archiviazione negli host per l'utilizzo da parte delle VM. I problemi che influiscono sulla capacità e sulle prestazioni influenzano le applicazioni in esecuzione su queste VM. |vROps e il Management Pack per vSAN forniscono dashboard aggiuntivi per facilitare il monitoraggio di vSAN. I controlli dell'integrità di vCenter vSAN vengono raccolti tramite vROps. vRLI raccoglie i dati di log da vCenter. |
| NSX | NSX fornisce i componenti di rete virtualizzati utilizzati dalle VM di calcolo; eventuali errori di rete possono influire sulle applicazioni in esecuzione su queste VM. | vROps e vROps Management Pack per VMware NSX forniscono visibilità sulla topologia di rete. vRLI raccoglie i dati di log dai componenti NSX come controller, ESG e switch logici. vRealize Network Insight (vRNI) fornisce una risoluzione approfondita dei problemi di rete. |

Oltre al monitoraggio, Operations Management on {{site.data.keyword.cloud_notm}} aiuta con la configurazione, la conformità e molte delle attività proattive descritte in questa documentazione.


## Link correlati
{: #opsprocs-intro-links}

* [vSphere Monitoring](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-A8B06BE0-E5FC-435C-B12F-A31618B21E2C.html){:new_window}
* [Guida di protezione avanzata di VMware](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro){:new_window}
* [Considerazioni sulla modifica delle risorse vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

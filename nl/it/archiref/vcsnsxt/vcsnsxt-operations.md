---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Considerazioni operative per la rete vCenter Server
{: #vcsnsxt-operations}

## Backup
{: #vcsnsxt-operations-backup}

### Backup di VMware vCenter Server on IBM Cloud
{: #vcsnsxt-operations-vcs-backup}

Come parte di {{site.data.keyword.vmwaresolutions_full}}, il software di backup Veeam viene facoltativamente distribuito su una VSI (Virtual Server Instance) {{site.data.keyword.cloud_notm}} utilizzando l'archiviazione di {{site.data.keyword.cloud_notm}} al di fuori del cluster VMware. Lo scopo di questo software è di eseguire il backup dei componenti di gestione nella soluzione. La [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) fornisce dettagli sull'offerta.

Il backup di tutti i componenti NSX è fondamentale per ripristinare il sistema al suo stato operativo in caso di malfunzionamento. Non è sufficiente eseguire il backup dei dispositivi virtuali NSX, è necessario utilizzare la funzione di backup NSX all'interno di NSX Manager per un backup efficace. Questa operazione richiede che venga specificato un server FTP o SFTP per il repository dei dati di backup NSX.

Il backup di NSX Manager contiene tutta la configurazione NSX, inclusi controller, entità di commutazione logica e instradamento, sicurezza, regole del firewall e tutto ciò che configuri all'interno dell'interfaccia utente o dell'API NSX Manager. I backup del database vCenter e degli elementi correlati come gli switch virtuali devono essere eseguiti separatamente. Per i dettagli, vedi [Backup basato su file di NSX](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#nsx-file-based-backup). La configurazione NSX deve essere sottoposta a backup insieme a un [backup basato su file di vCenter](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#vcenter-file-based-backup).

### Backup e ripristino di emergenza per IBM Cloud Private
{: #vcsnsxt-operations-backup-dr-icp}

I backup per una distribuzione {{site.data.keyword.icpfull_notm}} sono fondamentali per ripristinare il sistema al suo stato operativo in caso di malfunzionamento. Per un backup VM tradizionale, esiste un punto critico: ogni nodo master {{site.data.keyword.icpfull_notm}} esegue un servizio *etcd* e la documentazione di *etcd* indica chiaramente di non utilizzare il backup VM tradizionale per eseguirne il ripristino.

Per {{site.data.keyword.cloud_notm}} Private a livello di piattaforma, dovrai eseguire il backup dei seguenti componenti.
- **etcd** - etcd è utilizzato per memorizzare le risorse Kubernetes e le informazioni sullo stato di Calico.
- **Docker Registry** - Questo registro di immagini privato viene utilizzato per archiviare i file di immagine del contenitore.
- **MongoDB** - Questo database è utilizzato dal servizio di misurazione, dal server del repository Helm, dal server API Helm, dalla configurazione LDAP, dal tenant (spazio dei nomi) e dalle configurazioni del ruolo team/user/usergroup.
- **MariaDB** - Questo database è utilizzato da OIDC.
-	**Elasticsearch** - memorizza i log di sistema e dell'applicazione.
-	**Prometheus** - memorizza i dati per il monitoraggio.
-	**Persistent Storage** - utilizzato per i servizi di gestione che utilizzano il volume persistente di {{site.data.keyword.cloud_notm}} Private o Kubernetes e il provider di archiviazione.

Puoi utilizzare la tecnologia di backup o ripristino fornita dal provider di archiviazione. Un processo simile può essere esteso anche all'applicazione del tuo utente. Per ulteriori informazioni, vedi il [blog How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) o  [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/).

### Backup e ripristino di emergenza per CAM
{: #vcsnsxt-operations-backup-dr-cam}

I backup di una distribuzione CAM sono fondamentali per ripristinare il sistema al suo stato operativo in caso di malfunzionamento. Il backup di CAM richiede al cliente di eseguire il backup dei seguenti componenti:
-	**Database Mongo** – Il database CAM principale.
-	**Database Maria** - Utilizzato da CAM Blueprint Designer.
-	**File system NFS/Gluster** - I dati CAM risiedono in quattro volumi persistenti.

### Backup e DR per IBM Cloud Kubernetes Service
{: #vcsnsxt-operations-backup-dr-iks}

Il backup del database etcd viene fornito al cliente come parte del servizio gestito, tuttavia il cliente deve eseguire il backup dei dati dell'applicazione.

## Scalabilità
{: #vcsnsxt-operations-scalability}

### Scalabilità di vCenter Server
{: #vcsnsxt-operations-vcs-scalability}

Dopo la distribuzione degli host iniziali, gli utenti possono ridimensionare la capacità di calcolo dall'interno del portale {{site.data.keyword.cloud_notm}} for VMware.

Il ridimensionamento dell'ambiente segue uno di questi percorsi:
-	Aggiunta di nuovi siti gestiti da vCenter Server separati.
-	Aggiunta di nuovi cluster.
-	Aggiunta di nuovi host a un cluster esistente.

#### Distribuzioni multisito
{: #vcsnsxt-operations-multi-site}

VMware on {{site.data.keyword.cloud_notm}} può utilizzare la presenza di data center {{site.data.keyword.cloud_notm}} in tutto il mondo e il backbone di rete integrato per consentire la distribuzione e il funzionamento di vari casi di utilizzo di più aree geografiche in solo una frazione del tempo che servirebbe a costruire da zero un'infrastruttura di questo tipo. Per ulteriori informazioni, vedi [Configurazione multisito per le istanze vCenter Server on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite).

#### Ridimensionamento con il nuovo cluster
{: #vcsnsxt-operations-scale-out-new-cluster}

Gli utenti possono anche ridimensionare la capacità di calcolo creando un nuovo cluster dalla console ordinando gli host e i nuovi host vengono automaticamente aggiunti al nuovo cluster. Questa opzione crea un cluster separato nell'ambiente e offre agli utenti la possibilità di separare fisicamente e logicamente i carichi di lavoro di gestione dai carichi di lavoro dell'applicazione, la possibilità di separare i carichi di lavoro in base ad altre caratteristiche (ad esempio, il cluster di database Microsoft SQL) e la possibilità di distribuire le applicazioni in topologie ad alta disponibilità. Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

#### Ridimensionamento del cluster esistente
{: #vcsnsxt-operations-scale-out-existing-cluster}

L'utente può ridimensionare un cluster esistente ordinando gli host dall'interno della console e i nuovi host che vengono aggiunti automaticamente al cluster. Per ulteriori informazioni, vedi [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers). Potresti dover regolare la politica di prenotazione dell'alta disponibilità (HA) per il cluster in base ai requisiti di prenotazione.

### Scalabilità di IBM Cloud Private e IBM Cloud Kubernetes Service
{: #vcsnsxt-operations-icp-iks-scalability}

In base alla capacità di calcolo disponibile presso le ubicazioni in loco o in cloud, gli utenti possono ridimensionare l'architettura del nodo dal nodo di avvio inizialmente distribuito. Per ridimensionare l'ambiente:
-	Espandere i nodi di lavoro {{site.data.keyword.icpfull_notm}}.
-	Espandere e utilizzare l'offerta {{site.data.keyword.containerlong_notm}}.

#### Espansione IBM Cloud Private
{: #vcsnsxt-operations-icp-expansion}

I nodi della VM (Virtual Machine) del nodo di lavoro {{site.data.keyword.icpfull_notm}} vengono ridimensionati per espandere il calcolo e l'applicazione:
- Il cliente esegue il provisioning di una nuova VM (Virtual Machine) nella stessa VXLAN in cui viene distribuito {{site.data.keyword.icpfull_notm}}.
- I clienti possono ridimensionare i nodi di lavoro eseguendo il provisioning di nuove VM (Virtual Machine), accedendo al nodo di avvio ed eseguendo un comando per portare i nuovi nodi nel cluster. Per ulteriori dettagli, vedi [Adding or removing cluster nodes](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html).
- Utilizza CAM per automatizzare il provisioning della VM e l'esecuzione dei comandi per aggiungerla al cluster {{site.data.keyword.icpfull_notm}}.

#### Espansione di IBM Cloud Kubernetes Service
{: #vcsnsxt-operations-iks-expansion}

Gli utenti possono eseguire il provisioning di un ambiente {{site.data.keyword.containerlong_notm}} utilizzando il portale {{site.data.keyword.cloud_notm}} per estendere e utilizzare un ambiente contenitore. Per ulteriori informazioni, vedi [Hybrid enhancements across {{site.data.keyword.cloud_notm}} Private and {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

Le distribuzioni dell'applicazione in {{site.data.keyword.containerlong_notm}} sono possibili utilizzando i seguenti metodi:
-	La connessione e i servizi {{site.data.keyword.containerlong_notm}} sono sviluppati in CAM e pubblicati nel catalogo {{site.data.keyword.icpfull_notm}}.
- Multi Cloud Manager, un miglioramento futuro per gestire le istanze {{site.data.keyword.containerlong_notm}}.
- Riga di comando Helm.

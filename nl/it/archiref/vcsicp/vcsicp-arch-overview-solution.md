---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Componenti della soluzione
{: #vcsicp-arch-overview-solution}

## Componenti di VMware vCenter Server on IBM Cloud
{: #vcsicp-arch-overview-solution-vcs-comp}

Figura 1. Diagramma dell'ambiente vCenter Server
![Ambiente VCS](vcsicp-vcsenv.svg)

### Controller servizio piattaforma
{: #vcsicp-arch-overview-solution-psc}

La distribuzione vCenter Server utilizza un solo controller di servizi della piattaforma esterno installato su una sottorete portatile nella VLAN privata associata alle VM (Virtual Machine) di gestione. Il suo gateway predefinito è impostato sul BCR (backend customer router).

### vCenter Server
{: #vcsicp-arch-overview-solution-vcs}

Come il controller dei servizi della piattaforma, il vCenter Server viene distribuito come un'applicazione. Inoltre, vCenter Server viene installato su una sottorete portatile nella VLAN privata associata alle VM di gestione. Il suo gateway predefinito è impostato sull'indirizzo IP assegnato sul BCR per quella particolare sottorete.

### NSX Manager
{: #vcsicp-arch-overview-solution-nsx-manager}

NSX Manager viene distribuito sul cluster iniziale. Inoltre, a NSX Manager viene assegnato un indirizzo IP di backend della VLAN dal blocco di indirizzi portatile privato progettato per i componenti di gestione e configurato con i server DNS e NTP

### Controller NSX
{: #vcsicp-arch-overview-solution-nsx-controllers}

L'automazione di {{site.data.keyword.cloud}} distribuisce tre controller NSX all'interno del cluster iniziale. Ai controller viene assegnato un indirizzo IP di backend della VLAN dalla sottorete portatile privata progettato per i componenti di gestione.

### Edge NSX / DLR
{: #vcsicp-arch-overview-solution-nsx-edge}

Vengono distribuite coppie di gateway dei servizi edge (ESG) NSX. In tutti i casi, una coppia di gateway viene utilizzata per il traffico in uscita dai componenti di automazione che risiedono sulla rete privata. Per vCenter Server e {{site.data.keyword.icpfull_notm}}, un secondo gateway noto come edge gestito da ICP, viene distribuito e configurato con un uplink alla rete pubblica e un'interfaccia che è assegnata alla rete privata. Tutti i componenti NSX necessari, come Distributed Logical Router (DLR), switch logici e firewall possono essere configurati dall'amministratore. La [Guida di rete di vCenter Server](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) fornisce maggiori dettagli sulla progettazione della rete.

La seguente tabella riepiloga le specifiche ESG / DLR {{site.data.keyword.icpfull_notm}}.

Tabella 1. Specifiche ESG {{site.data.keyword.icpfull_notm}}

Attributo  |  Specifica
--|--
Gateway servizio edge  |  Dispositivo virtuale
Dimensione edge	Large |   Numero di vCPUs	2
Memoria	| Disco 1-GB	| 1000 GB sul datastore locale

Tabella 2. Specifiche DLR {{site.data.keyword.icpfull_notm}}

Attributo  |  Specifica
--|--|
Router logico distribuito | 	Dispositivo virtuale
Dimensione edge	Compact | Numero di vCPUs	1
Memoria	| Disco 512-MB	| 1000 GB sul datastore locale

## Componenti IBM Cloud Private
{: #vcsicp-arch-overview-solution-icp-comp}

{{site.data.keyword.icpfull_notm}} è una piattaforma dell'applicazione per lo sviluppo e la gestione di applicazioni
inserite nei contenitori in loco. È un ambiente integrato per la gestione dei contenitori che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione e i framework di monitoraggio.

Figura 2. Distribuzione {{site.data.keyword.icpfull_notm}} virtuale con vCenter Server
![Distribuzione {{site.data.keyword.icpfull_notm}} virtuale con VCS](vcsicp-virtual-icp-deployment-vcs.svg)

###	Nodo di avvio
{: #vcsicp-arch-overview-solution-boot-node}

Un nodo di avvio o bootstrap (facoltativo) viene utilizzato per l'esecuzione dell'installazione, della configurazione, della scalabilità del nodo e degli aggiornamenti del cluster. Per ogni cluster è necessario un solo nodo di avvio. Puoi utilizzare un singolo nodo per il master e per l'avvio.

### Nodo master
{: #vcsicp-arch-overview-solution-master-node}

Un nodo master fornisce servizi di gestione e controlla i nodi di lavoro in un cluster. I nodi master ospitano i processi che sono responsabili dell'allocazione delle risorse, della manutenzione dello stato, della pianificazione e del monitoraggio. Poiché un ambiente ad elevata disponibilità (HA) presenta più di un singolo nodo master, se il nodo master principale ha un malfunzionamento, la logica di failover promuove automaticamente un nodo differente al ruolo master. Gli host che possono funzionare come master sono detti candidati master.

###	Nodo di lavoro
{: #vcsicp-arch-overview-solution-worker-node}

Un nodo di lavoro è un nodo che fornisce un ambiente contenitore per l'esecuzione delle attività. Man mano che la domanda aumenta, è possibile aggiungere più nodi di lavoro al cluster in modo da migliorare le prestazioni e l'efficienza. Un cluster può contenere un qualsiasi numero di nodi di lavoro, ma ne è necessario almeno uno.

### Nodo proxy
{: #vcsicp-arch-overview-solution-proxy-node}

Un nodo proxy è un nodo che trasmette una richiesta esterna ai servizi creati all'interno del proprio cluster. Poiché un ambiente ad elevata disponibilità (HA) presenta più di un singolo nodo proxy, se il nodo proxy principale ha un malfunzionamento, la logica di failover promuove automaticamente un nodo differente al ruolo proxy. Sebbene tu possa utilizzare un singolo nodo sia come master che come proxy, utilizza i nodi proxy dedicati per ridurre il carico sul nodo master. Un cluster deve avere almeno un nodo proxy se al suo interno è necessario il bilanciamento del carico.

### Nodo di gestione
{: #vcsicp-arch-overview-solution-mgmt-node}

Un nodo di gestione è un nodo facoltativo che ospita solo i servizi di gestione come il monitoraggio, la misurazione e la registrazione. Configurando i nodi di gestione dedicati, puoi evitare che il nodo master diventi sovraccaricato. Puoi abilitare il nodo di gestione solo durante l'installazione di {{site.data.keyword.icpfull_notm}}.

###	Nodo Controllo vulnerabilità
{: #vcsicp-arch-overview-solution-va-node}

Un nodo Controllo vulnerabilità è un nodo facoltativo utilizzato per l'esecuzione dei servizi del Controllo vulnerabilità. I servizi del Controllo vulnerabilità sono intensivi per le risorse. Se utilizzi il servizio Controllo vulnerabilità, specifica un nodo VA dedicato.

Le seguenti specifiche di VM sono richieste per un'istanza {{site.data.keyword.icpfull_notm}} ad elevata disponibilità:

Tabella 3. Specifiche VM (Virtual Machine) {{site.data.keyword.icpfull_notm}}

Nodo | 	Istanze	| IP	| CPU	| RAM (GB)	| DISK (GB)
:-----|------------:|:----|----:|----------:|----------:|
Master|	3	| IP (x3) VIP (x1)	| 4	| 64	| 200
Gestione	|3	| IP (x3)	|8	|64	|500
Proxy	| 3	| IP (x3)VIP (x1)	|2	|4	|150
Controllo vulnerabilità	|3	| IP (x3)	| 4	| 16	|500
GlusterFS	| 3	| IP (x3)	|8	|16	|150
Di lavoro	| 3-6	| IP (x3)	|4-8	|4	|150

CAM richiede che i nodi di lavoro abbiano una configurazione di vCPU e memoria superiore.

Tabella 4. Specifiche VM (Virtual Machine) {{site.data.keyword.icpfull_notm}}

Nodo | 	Istanze	| IP	| CPU	| RAM (GB)	| DISK (GB)
:-----|------------:|:----|----:|----------:|----------:|
worker  |  3 | IP (x3)  |  4-8 |16-20   |  150

## Componenti CAM
{: #vcsicp-arch-overview-solution-cam-comp}

CAM ({{site.data.keyword.cloud_notm}} Automation Manager) è una piattaforma di gestione self-service multicloud che viene eseguita su {{site.data.keyword.icpfull_notm}} che consente agli sviluppatori e agli amministratori di soddisfare le richieste di business.

Fig 3. Riferimento del componente CAM
![Riferimento del componente CAM](vcsicp-cam-component-ref.svg)

### Proxy CAM
{: #vcsicp-arch-overview-solution-cam-proxy}

Fornisce un accesso proxy nginx in CAM.

### Interfaccia utente CAM
{: #vcsicp-arch-overview-solution-cam-ui}

I componenti dell'interfaccia utente sono suddivisi su più di un singolo contenitore. I componenti sono inclusi nell'interfaccia utente connessioni cloud, nell'interfaccia utente libreria di modelli e nell'interfaccia utente istanze distribuite.

### API CAM
{: #vcsicp-arch-overview-solution-cam-api}

Le API CAM sono suddivise su più di un singolo contenitore.

### Helm
{: #vcsicp-arch-overview-solution-helm}

Un contenitore con i file binari richiesti per distribuire i grafici helm nei cluster Kubernetes.

### Terraform
{: #vcsicp-arch-overview-solution-terraform}

Un contenitore con i file binari richiesti per distribuire le risorse Terraform su più di un singolo cloud.

### Log
{: #vcsicp-arch-overview-solution-logs}

L'ubicazione dei log del contenitore.

### Database Mongo
{: #vcsicp-arch-overview-solution-mongo-db}

Il database Core per l'applicazione CAM.

### Redis
{: #vcsicp-arch-overview-solution-redis}

Il database Redis viene utilizzato per archiviare la memorizzazione nella cache delle sessioni e i blocchi all'interno di CAM.

### Designer modello
{: #vcsicp-arch-overview-solution-template-designer}

Una GUI (graphical user interface) per creare modelli Terraform, con una funzione di trascinamento dei moduli Terraform.

### Database Maria
{: #vcsicp-arch-overview-solution-maria-db}

Il database per l'applicazione designer del modello.

## Link correlati
{: #vcsicp-arch-overview-solution-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

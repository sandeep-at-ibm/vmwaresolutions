---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

{{site.data.keyword.icpfull_notm}} è una piattaforma dell'applicazione per lo sviluppo e la gestione di applicazioni inserite nei contenitori. È un ambiente integrato che include l'orchestrazione del contenitore Kubernetes, un repository di immagini privato, una console di gestione, i framework di monitoraggio e un'interfaccia utente grafica che fornisce una posizione centralizzata da cui puoi distribuire, gestire, monitorare e ridimensionare le tue applicazioni.

{{site.data.keyword.cloud_notm}} Private ha le seguenti funzioni:
-	**Programma di installazione unificato** – Il programma di installazione configura rapidamente un cluster basato su Kubernetes con i nodi master, di lavoro e proxy utilizzando un programma di installazione basato su Ansible.
-	**Console di gestione di {{site.data.keyword.cloud_notm}} Private** – Gestisci, monitora e risolvi i problemi delle tue applicazioni e del tuo cluster da una singola console di gestione centralizzata e sicura.
-	**Registro di immagini Docker privato** - Questo registro locale ha tutte le stesse funzioni di Docker Hub ma ti consente anche di limitare gli utenti che possono visualizzare o estrarre le immagini.
-	**Catalogo di software e servizi inseriti in contenitore** - Il catalogo fornisce una posizione centralizzata da cui puoi cercare e installare i pacchetti nel tuo cluster. I pacchetti per prodotti IBM aggiuntivi sono disponibili in repository curati inclusi nell'elenco di repository predefinito di {{site.data.keyword.cloud_notm}} Private.
-	**Reti tenant isolate** - Calico offre prestazioni migliorate e isolamento della rete all'interno del tuo cluster. Con Calico, puoi creare una sottorete isolata per ogni progetto all'interno del tuo cluster. Questo isolamento della rete ti fornisce maggiore sicurezza durante la trasmissione dei dati e riduce le possibilità di compromettere le applicazioni e i loro dati. Calico facilita inoltre la creazione di nuove politiche di rete che possono abilitare il controllo dettagliato sulla condivisione di oggetti all'interno di un singolo spazio dei nomi.
-	**Monitoraggio e registrazione solidi con lo stack ELK** - {{site.data.keyword.cloud_notm}} Private utilizza Elasticsearch, Logstash, Filebeat ed Heapster per la raccolta, l'archiviazione e l'esecuzione di query di log e metriche. Questo processo di monitoraggio e registrazione fornisce un archivio centralizzato per tutti i log e le metriche, prestazioni migliori e una maggiore stabilità quando accedi ed esegui query di log e metriche.

## Componenti IBM Cloud Private
{: #vcsnsxt-overview-icp-comp}

Un cluster {{site.data.keyword.cloud_notm}} Private ha quattro classi principali di nodi: di avvio, master, di lavoro e proxy. Puoi facoltativamente specificare i nodi di gestione, VA (Vulnerability Advisor) ed etcd nel tuo cluster.
-	**Nodo di avvio** - Un nodo di avvio viene utilizzato per eseguire l'installazione, la configurazione, il ridimensionamento dei nodi e gli aggiornamenti del cluster.
-	**Nodo master** - Un nodo master fornisce servizi di gestione e controlla i nodi di lavoro in un cluster. I nodi master ospitano i processi che sono responsabili dell'allocazione delle risorse, della manutenzione dello stato, della pianificazione e del monitoraggio.
-	**Nodo di lavoro** - Un nodo di lavoro è un nodo che fornisce un ambiente contenitore per l'esecuzione delle attività. Man mano che la domanda aumenta, è possibile aggiungere più nodi di lavoro al cluster in modo da migliorare le prestazioni e l'efficienza.
-	**Nodo proxy** - Un nodo proxy è un nodo che trasmette richieste esterne ai servizi creati all'interno del tuo cluster.
-	**Nodo di gestione** - Un nodo di gestione è un nodo facoltativo che ospita solo i servizi di gestione come monitoraggio, misurazione e registrazione. Configurando i nodi di gestione dedicati, puoi evitare che il nodo master diventi sovraccaricato.
-	**Nodo Va (Vulnerability Advisor)** - Un nodo VA è un nodo facoltativo utilizzato per l'esecuzione dei servizi Vulnerability Advisor.
-	Nodo **etcd** - Un nodo etcd è un nodo facoltativo utilizzato per l'esecuzione dell'archivio chiave/valore distribuito etcd.

## Rete di IBM Cloud Private
{: #vcsnsxt-overview-icp-networking}

La gestione della rete di {{site.data.keyword.icpfull_notm}} è facilitata dall'uso di Calico.
Calico utilizza il livello 3 o il livello di rete, del modello OSI (Open System Interconnection). Calico utilizza BGP (Border Gateway Protocol) per creare tabelle di instradamento che facilitano la comunicazione tra i nodi agent.

Per ulteriori informazioni sulla rete di Calico, vedi [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks).

## Link correlati
{: #vcsnsxt-overview-icp-related}

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle
](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

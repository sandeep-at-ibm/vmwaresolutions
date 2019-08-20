---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# Backup, ripristino di emergenza e scalabilità
{: #vcsicp-detail-design-resiliency}

## Backup e DR
{: #vcsicp-detail-design-resiliency-backup-dr}

### Backup di VMware vCenter Server on IBM Cloud
{: #vcsicp-detail-design-resiliency-vcs-backup}

Come parte di {{site.data.keyword.vmwaresolutions_full}}, il software di backup Veeam viene facoltativamente distribuito su una VSI (Virtual Server Instance) {{site.data.keyword.cloud_notm}} che utilizza {{site.data.keyword.cloud_notm}} Endurance Storage al di fuori del cluster VMware. Lo scopo di questo software è di eseguire il backup dei componenti di gestione in questa soluzione.

### Backup NSX
{: #vcsicp-detail-design-resiliency-nsx-backup}

Un corretto backup di tutti i componenti NSX è fondamentale per ripristinare il sistema al suo stato operativo in caso di malfunzionamento. Non è sufficiente eseguire il backup delle VM (Virtual Machine) NSX). Per un backup corretto, occorre invece utilizzare la funzione di backup NSX in NSX Manager. È necessario specificare un server FTP o SFTP per il repository di dati di backup NSX.
Il backup NSX Manager contiene tutta la configurazione NSX, inclusi i controller, le entità di commutazione e di instradamento logiche, la sicurezza, le regole del firewall e qualsiasi altra cosa configuri all'interno dell'IU o dell'API NSX Manager. Il database vCenter e gli elementi correlati, come ad esempio gli switch virtuali, devono essere sottoposti a backup separatamente. La configurazione NSX deve essere sottoposta a backup insieme a un backup di vCenter.

### Backup e DR per IBM Cloud Private
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

I backup per una distribuzione {{site.data.keyword.icpfull_notm}} sono cruciali per ripristinare il sistema al suo stato di lavoro se si verifica un errore. Oltre a un tradizionale backup VM, ogni nodo master {{site.data.keyword.icpfull_notm}} esegue etcd. La documentazione etcd indica chiaramente di non utilizzare il backup VM tradizionale per eseguirne il ripristino.

Per {{site.data.keyword.icpfull_notm}} al livello di piattaforma, devi eseguire il backup di questi componenti:
- **Etcd** viene utilizzato per archiviare risorse Kubernetes e informazioni relative agli stati di Calico.
- **Docker Registry** registro di immagini privato utilizzato per archiviare i file dell'immagine contenitore in un repository di immagini.
- **MongoDB** database utilizzato dal servizio di misurazione, dal server del repository Helm, dal server dell'API Helm, dalla configurazione LDAP, dal tenant (spazio dei nomi) e dalle configurazioni di ruolo team/user/usergroup.
- **MariaDB** database utilizzato da OIDC.
- **Elasticsearch** archivia i log di sistema e dell'applicazione.
- **Prometheus** archivia i dati per il monitoraggio.
- **Persistent Storage** utilizzato per i servizi di gestione che utilizzano il volume persistente {{site.data.keyword.icpfull_notm}} o Kubernetes e il provider di archiviazione. Puoi utilizzare la tecnologia di backup o ripristino fornita dal provider di archiviazione. Un processo simile può essere esteso anche all'applicazione del tuo utente.

### Backup e DR per CAM
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

Il backup per una distribuzione CAM è cruciale per ripristinare il sistema al suo stato di lavoro se si verifica un errore. Il backup di CAM richiede al cliente di eseguire il backup dei seguenti componenti:
- Il **database Mongo** è il database CAM principale.
- Il **database Maria** è il database che viene utilizzato da CAM Blueprint Designer.
- **NFS/GlusterFS** è dove risiedono i dati CAM in quattro volumi persistenti.

### Backup e DR per IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

I backup del database etcd vengono forniti al cliente come parte del servizio gestito, devi eseguire il backup di tutti i dati dell'applicazione.

## Scalabilità
{: #vcsicp-detail-design-resiliency-scalability}

### Scalabilità di VCS
{: #vcsicp-detail-design-resiliency-vcs-scalability}

Dopo la distribuzione degli host iniziali, l'utente può ridimensionare la capacità di calcolo dall'interno del portale {{site.data.keyword.cloud_notm}} for VMware.

Questo ridimensionamento dell'ambiente segue uno di questi tre percorsi:
- Aggiunta di nuovi siti gestiti da vCenter Server separati.
- Aggiunta di nuovi cluster.
- Aggiunta di nuovi host a un cluster esistente.

#### Distribuzioni multisito
{: #vcsicp-detail-design-resiliency-multi-site}

VMware on {{site.data.keyword.cloud_notm}} può utilizzare la presenza di data center IBM Cloud in tutto il mondo e il backbone di rete integrato per consentire la distribuzione e il funzionamento di vari casi di utilizzo di più aree geografiche in solo una frazione del tempo che servirebbe a costruire da zero un'infrastruttura di questo tipo.

#### Ridimensionamento con il nuovo cluster
{: #vcsicp-detail-design-resiliency-scale-out-new}

L'utente può anche ridimensionare in modo incrementale la capacità di calcolo creando un nuovo cluster dall'interno della console, ordinando gli host e i nuovi host che vengono automaticamente aggiunti al nuovo cluster. Questa opzione crea un cluster separato nell'ambiente e dà agli utenti la possibilità di separare in modo logico e fisico i carichi di lavoro di gestione da quelli di applicazione, la capacità di separare i carichi di lavoro in base ad altre caratteristiche (ad esempio, il cluster di database Microsoft SQL) e la capacità di distribuire le applicazioni in topologie ad elevata disponibilità.

#### Ridimensionamento del cluster esistente
{: #vcsicp-detail-design-resiliency-scale-out-existing}

L'utente può ridimensionare un cluster esistente ordinando gli host dall'interno della console e i nuovi host che vengono aggiunti automaticamente al cluster. Gli utenti potrebbero dover regolare la politica di prenotazione dell'alta disponibilità (HA) per il cluster in base ai loro requisiti di prenotazione.

### Scalabilità IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-scalability}

In base alla capacità di calcolo disponibile presso le ubicazioni cloud e in loco, l'utente può ridimensionare in modo incrementale l'architettura del nodo dal nodo di avvio inizialmente distribuito.

Il ridimensionamento dell'ambiente permette di:
- Espandere i nodi di lavoro {{site.data.keyword.icpfull_notm}}.
- Espandere e utilizzare l'offerta {{site.data.keyword.containerlong_notm}}.

#### Espansione IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-expansion}

I nodi VM del nodo di lavoro {{site.data.keyword.icpfull_notm}} vengono ridimensionati per espandere il calcolo o l'applicazione:
- Il cliente fornisce una nuova VM, nella stessa VXLAN in cui viene distribuito {{site.data.keyword.icpfull_notm}}.
- I clienti possono ridimensionare i nodi di lavoro, eseguendo il provisioning di nuove VM, accedendo al nodo di avvio ed eseguendo un comando per portare i nuovi nodi nel cluster.
- Utilizza CAM per automatizzare il provisioning della VM ed eseguire i comandi per l'aggiunta al cluster {{site.data.keyword.icpfull_notm}}.

###  Espansione di IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-resiliency-iks-expansion}

Gli utenti possono eseguire il provisioning di un ambiente {{site.data.keyword.containerlong_notm}} mediante il portale {{site.data.keyword.cloud_notm}} per estendere o utilizzare un ambiente contenitore.

Utilizza quanto segue per le distribuzioni dell'applicazione in {{site.data.keyword.containerlong_notm}}:
- La connessione o i servizi {{site.data.keyword.containerlong_notm}} sono sviluppati in CAM e pubblicati nel catalogo {{site.data.keyword.icpfull_notm}}.
- Miglioramento futuro di Multi-Cloud Manager per gestire le istanze {{site.data.keyword.containerlong_notm}}
- Interfaccia riga di comando Helm.
- Utilizza i cluster a più zone per incrementare l'elevata disponibilità.

## Link correlati
{: #vcsicp-detail-design-resiliency-related}

* [Adding or removing cluster nodes](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Aggiunta di nodi di lavoro ridimensionando un pool di nodi di lavoro esistente](/docs/containers?topic=containers-clusters)
* [How to back up and restore {{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [{{site.data.keyword.icpfull_notm}} backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)

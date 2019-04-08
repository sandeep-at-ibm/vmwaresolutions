---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-13"

subcollection: vmwaresolutions


---

# Informazioni sull'archiviazione collegata per vCenter Server
{: #storage-benefits}

L'archiviazione collegata è un'estensione dell'offerta VMware vCenter Server on {{site.data.keyword.cloud}}. L'architettura della soluzione di archiviazione collegata per VMware vCenter Server on {{site.data.keyword.cloud_notm}} indica in dettaglio i componenti della soluzione e la configurazione di alto livello di ciascun componente nella progettazione.

Per ulteriori informazioni sulla progettazione di vCenter Server, vedi [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Vantaggi chiave dell'archiviazione collegata per vCenter Server
{: #storage-benefits-key-benefits}

Se da una parte l'archiviazione collegata non è un prerequisito per gli ambienti VMware, dall'altra il suo utilizzo come un dispositivo di archiviazione condivisa fornisce molti vantaggi agli utenti per le operazioni IT. L'utilizzo di dispositivi di archiviazione condivisa può aiutarti a ottenere un'elevata disponibilità, DRS (Distributed Resource Scheduler), un utilizzo efficiente della capacità di archiviazione e una gestione semplificata mediante l'abilitazione delle funzioni vSphere descritte nella seguente tabella.

Tabella 1. Descrizione delle funzioni per l'archiviazione collegata per vCenter Server

| Funzione | Descrizione |
|:------- |:----------- |
| vSphere Distributed Resource Scheduler and Resource Pools | Questa funzione consente l'astrazione e la gestione flessibile delle risorse tramite il bilanciamento del carico di lavoro e il posizionamento delle VM (Virtual Machine). I pool di risorse possono essere raggruppati in gerarchie e utilizzati per partizionare in modo gerarchico le risorse di memoria e CPU disponibili. |
| vSphere High Availability | Questa funzione fornisce l'elevata disponibilità (HA, High Availability) per le VM (eseguendone il pooling) e per gli host che risiedono in un cluster. Gli host nel cluster sono monitorati. Se si verifica un errore, le VM su un host malfunzionante vengono riavviate su host alternativi. |
| vSphere Datastore Clusters | Questa funzione fornisce una raccolta di archivi dati con risorse condivise e un'interfaccia di gestione condivisa. |
| vSphere Fault Tolerance | Questa funzione fornisce una disponibilità continua per le VM, eliminando i tempi di inattività e le interruzioni, anche se si verifica un malfunzionamento host completo. |

## Link correlati
{: #storage-benefits-related}

* [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)

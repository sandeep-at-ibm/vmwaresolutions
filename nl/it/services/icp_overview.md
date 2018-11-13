---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica su IBM Cloud Private Hosted

Il servizio {{site.data.keyword.cloud}} Private Hosted distribuisce automaticamente {{site.data.keyword.cloud_notm}} Private Hosted nelle tue istanze VMware vCenter Server. Questo servizio porta la potenza dei microservizi e dei contenitori al tuo ambiente VMware su {{site.data.keyword.cloud_notm}}. Con questo servizio, puoi estendere lo stesso modello operativo e gli stessi strumenti VMware e {{site.data.keyword.cloud_notm}} Privato con cui hai dimestichezza da una situazione in loco a {{site.data.keyword.cloud_notm}}.

Questo servizio è disponibile per:
* Istanze vCenter Server distribuite in o aggiornate alla V2.5 e successive
* Istanze vCenter Server with Hybridity Bundle distribuite in o aggiornate alla V2.7 e successive.
{:note}

## Specifiche tecniche per IBM Cloud Private Hosted

La seguente tabella elenca i requisiti minimi per ordinare il servizio IBM Cloud Private Hosted per l'ambiente **Pronto per la produzione** e **Sviluppo/Test**.

Tabella 1. Requisiti minimi per gli ambienti Pronto per la produzione e Sviluppo/Test

|Ambiente | Core | Memoria | Host | Archiviazione |
|:---------- |:---- |:------ |:---- |:------- |
| Pronto per la produzione | 52 | 640 | 3 | 8000 |
| Sviluppo/Test | 30 | 200 | 3 | 4000 |

### Requisiti della risorsa di IBM Cloud Privato Hosted

Le seguenti tabelle elencano i requisiti della risorsa del servizio {{site.data.keyword.cloud_notm}} Private Hosted negli ambienti Pronto per la produzione e Sviluppo/Test.

Tabella 2. Requisiti della risorsa di {{site.data.keyword.cloud_notm}} Private Hosted nell'ambiente Pronto per la produzione

| Tipo di nodo  | Core CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Numero di VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Avvio       | 8 | 16 | 100 | 1 | 1 |   
| Gestione | 8 | 64 | 500 | 3 | 3 |
| Master     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Di lavoro     | 4 | 16 | 200 | 300 | 6 |
| Controllo vulnerabilità| 8 | 16 | 500 | 3 | 3 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Server NFS| 8 | 4  | 350 | 1 | 1 |
| Edge | 2 | 1 | 0.5 | 0.5 | 2 |
| Totale | 162 | 642 | 6401 | 1951 | 26 |
| Vincoli documentati | 52 | 640 |  | 8000 |   |
|   | Rapporto 1:3 | Rapporto 1:1 |  | Rapporto 1:1 |  |

Tabella 3. Requisiti della risorsa di {{site.data.keyword.cloud_notm}} Private Hosted nell'ambiente Sviluppo/Test

| Tipo di nodo  | Core CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Numero di VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Avvio       | 8 | 16 | 100 | 1 | 1 |   
| Gestione | 8 | 16 | 150 | 1 | 1 |
| Master     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Di lavoro     | 4 | 16 | 200 | 300 | 3 |
| Controllo vulnerabilità| 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 | 32 | 250 | 1 | 1 |
| Server NFS| 8 | 4  | 350 | 1 | 1 |
| Edge | 1 | 0.5 | 0.5 | 2 | 2 |
| Totale | 96 | 201 | 2401 | 1050 | 15 |
| Vincoli documentati | 30 | 200 |  | 4000 |  |
|  | Rapporto 1:3 | Rapporto 1:1 |  | Rapporto 1:1 |  |

### Formule per il calcolo dei requisiti di spazio di IBM Cloud Private Hosted

Le seguenti formule vengono utilizzate per calcolare i requisiti di spazio di IBM Cloud Private e le spese generali di gestione.

Formula 1: `AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

Tabella 4. Descrizione delle variabili nella formula 1

| Variabili	| Descrizione |	 Unità|	Esempio vSAN | Esempio NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	Il numero di core effettivi disponibili per i carichi di lavoro e i servizi nell'ambiente |	core |	38	| 43 |
| HostCount	| Il numero di host nel cluster predefinito	| host | 4	| 4 |
| HostCoreCount	| Il numero di core non elaborati disponibili in ogni host nel cluster predefinito |	core |	16 | 16 |
| HostOverheadCores	| Il numero di core riservati dal server ESXi come sovraccarico, che equivale a 0,1 core	| core	| 0.1 |	0.1 |
| MgmtOverheadCores | Il numero di core riservati dai componenti di gestione vCenter Server (vCenter Server, PSC, AD/DNS, Edge), che corrisponde a 5 core	| core	| 5	| 5 |
| vSphereHAHostTolerance |	Il numero di host da tollerare nella configurazione vSphere HA, che equivale a 1 host |	host	 | 1 | 1 |
| HostVsanOverheadCorePercentage | La percentuale di core di un host utilizzata da vSAN, che è uguale al 10% o al 0% se l'host non è vsan	| % | 10% |	0% |

Formula 2: `AvailableMemory = [ HostMemory - HostOverheadMemory - HostVsanOverheadMemory - ( HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadMemory`

Tabella 5. Descrizione delle variabili nella formula 2

| Variabili	| Descrizione |	Unità|	Esempio vSAN | Esempio NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	|Il numero di GB di memoria disponibili per i carichi di lavoro e i servizi nell'ambiente | GB | 	693	| 860 |
| HostCount	| Il numero di host nel cluster predefinito	| host | 6	| 6 |
| HostMemory |	 Il numero di GB non elaborati disponibili in ogni host nel cluster predefinito |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | Il numero di GB di una capacità di ogni disco SSD di capacità vSAN su questo host, che è uguale a 960, 1946 o 3891, o uguale a 0 GB se non VSAN | GB |	960 | 0 |
| HostOverheadMemory |	 Il numero di GB di memoria riservati dal server ESXi come sovraccarico, che equivale a 4,6 GB	|	GB	| 4.6 |	4.6 |
| MgmtOverheadMemory |	 Il numero di GB di memoria riservati dai componenti di gestione vCenter Server (vCenter Server, PSC, AD/DNS, Edge), che corrisponde a 77 GB	| GB | 77 | 77 |
| vSphereHAHostTolerance |Il numero di host da tollerare nella configurazione vSphere HA, che equivale a 1 host |host	 | 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | Il numero di GB di memoria riservati dalla gestione vSAN (rappresentata come percentuale di uno dei dischi vSAN di capacità), che equivale al 2,75% |	% | 2.75%	| 2.75% |
| HostVsanOverheadMemory | Il numero di GB di memoria riservati dalla gestione vSAN indipendentemente dallo spazio disco, che è equivalente a 7 GB o a 0 GB se non VSAN| GB |  7	| 0 |

## Considerazioni quando installi IBM Cloud Private Hosted

Ottieni la licenza richiesta prima di installare il servizio {{site.data.keyword.cloud_notm}} Private Hosted. Ti consigliamo di assicurarti che la tua licenza possa supportare non solo la distribuzione iniziale di {{site.data.keyword.cloud_notm}} Private Hosted, ma anche l'espansione futura della dimensione di {{site.data.keyword.cloud_notm}} Private Hosted nella tua infrastruttura.

## Considerazioni quando rimuovi IBM Cloud Private Hosted

* {{site.data.keyword.cloud_notm}} elimina solo le macchine virtuali (VM) che sono state distribuite durante l'installazione iniziale del servizio {{site.data.keyword.cloud_notm}} Private Hosted. Tutti i nodi che sono stati distribuiti dopo l'installazione non saranno eliminati.
* {{site.data.keyword.cloud_notm}} eliminerà la VXLAN, il DLR e il gateway edge creati durante la distribuzione iniziale del servizio {{site.data.keyword.cloud_notm}} Private Hosted. Le VM che hai distribuito su VXLAN perderanno la connettività una volta avviata la rimozione del servizio {{site.data.keyword.cloud_notm}} Private Hosted.

### Link correlati

* [Ordine di IBM Cloud Private Hosted](../services/icp_ordering.html)
* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf) (download PDF)
* [Apri un ticket per IBM Cloud privato](https://www.ibm.com/mysupport/s/?language=en_US)

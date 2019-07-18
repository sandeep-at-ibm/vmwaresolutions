---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: IBM Cloud Private, ICP, tech specs ICP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica su IBM Cloud Private Hosted
{: #icp_overview}

Il servizio {{site.data.keyword.cloud}} Private Hosted distribuisce automaticamente {{site.data.keyword.cloud_notm}} Private Hosted e {{site.data.keyword.cloud_notm}} Automation Manager nelle tue istanze VMware vCenter Server. Questo servizio porta la potenza dei microservizi e dei contenitori al tuo ambiente VMware su {{site.data.keyword.cloud_notm}}. Con questo servizio, puoi estendere lo stesso modello operativo e gli stessi strumenti VMware e {{site.data.keyword.cloud_notm}} Privato con cui hai dimestichezza da una situazione in loco a {{site.data.keyword.cloud_notm}}.

Questo servizio è disponibile per le seguenti istanze:
* Istanze vCenter Server with Hybridity Bundle distribuite o di cui è stato eseguito l'upgrade alla V2.7 e successive
* Istanze vCenter Server distribuite o di cui è stato eseguito l'upgrade alla V2.5 e successive

L'attuale versione di IBM Cloud Private installata è la 3.1.2. {{site.data.keyword.cloud_notm}} Automation Manager viene distribuito anche come parte dell'ordine del servizio {{site.data.keyword.cloud}} Private Hosted.
{:note}


## Specifiche tecniche per IBM Cloud Private Hosted
{: #icp_overview-specs}

La seguente tabella elenca i requisiti minimi per ordinare il servizio IBM Cloud Private Hosted per l'ambiente **Pronto per la produzione** e **Sviluppo/Test**.

|Ambiente | Core | Memoria (GB) | Host | Memoria (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| Pronto per la produzione | 52 | 640 | 3 | 8.000 |
| Sviluppo/Test | 30 | 200 | 3 | 4.000 |
{: caption="Tabella 1. Requisiti minimi per gli ambienti Pronto per la produzione e Sviluppo/Test" caption-side="top"}

### Requisiti della risorsa di IBM Cloud Private Hosted
{: #icp_overview-resource-req}

La seguente tabella elenca i requisiti di risorse del servizio {{site.data.keyword.cloud_notm}} Private Hosted nell'ambiente pronto per la produzione.

| Tipo di nodo  | Core CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Numero di VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Avvio       | 12 | 24 | 100 | 1 | 1 |   
| Gestione | 8 | 64 | 500 | 3 | 3 |
| Master     | 8 | 64 | 200 | 3 | 3 |  
| Proxy      | 2 | 4  | 150 | 3 | 3 |
| Di lavoro     | 4 | 16 | 200 | 300 | 6 |
| Controllo vulnerabilità | 8 | 16 | 500 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Server NFS | 8 | 4  | 350 | 1 | 1 |
| Gateway dei servizi edge NSX | 2 | 1 | 0.5 | 0.5 | 2 |
| Vincoli documentati | 52 | 640 |  | 8.000 |   |
{: caption="Tabella 2. Ambiente pronto per la produzione" caption-side="top"}

La seguente tabella elenca i requisiti di risorse del servizio {{site.data.keyword.cloud_notm}} Private Hosted negli ambienti di sviluppo e test.

| Tipo di nodo  | Core CPU   |  Memoria (GB) | Disco 1 (GB) | Disco 2 (GB) | Numero di VM |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| Avvio       | 12 | 24 | 100 | 1 | 1 |   
| Gestione | 8 | 16 | 150 | 1 | 1 |
| Master     | 8 | 16 | 200 | 1 | 1 |  
| Proxy      | 2 | 4  | 150 | 1 | 1 |
| Di lavoro     | 4 | 16 | 200 | 300 | 3 |
| Controllo vulnerabilità | 8 | 16 | 150 | 1 | 1 |
| GlusterFS  | 8 | 16 | 150 | 50 | 3 |
| Server NFS | 8 | 4  | 350 | 1 | 1 |
| Gateway dei servizi edge NSX | 2 | 1 | 0.5 | 0.5 | 2 |
| Vincoli documentati | 30 | 200 |  | 4.000 |  |
{: caption="Tabella 3. Ambienti di sviluppo e test {{site.data.keyword.cloud_notm}}" caption-side="top"}

### Formule per il calcolo dei requisiti di spazio di IBM Cloud Private Hosted
{: #icp_overview-formulas}

Le seguenti formule vengono utilizzate per calcolare i requisiti di spazio di IBM Cloud Private e le spese generali di gestione.

#### Formula per calcolare il numero di core disponibili
{: #icp_overview-formulas-1}

La seguente tabella elenca le variabili nella formula 1:

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

| Variabili | Descrizione | Unità | Esempio vSAN | Esempio NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores | Il numero di core effettivi disponibili per i carichi di lavoro e i servizi nell'ambiente | Core | 38 | 43 |
| HostCount | Il numero di host nel cluster predefinito | Host | 4 | 4 |
| HostCoreCount | Il numero di core non elaborati disponibili in ogni host nel cluster predefinito | Core | 16 | 16 |
| HostOverheadCores | Il numero di core riservati dal server ESXi come sovraccarico, che equivale a 0,1 core | Core | 0.1 | 0.1 |
| MgmtOverheadCores | Il numero di core riservati dai componenti di gestione vCenter Server (vCenter Server, PSC, AD/DNS, Edge), che corrisponde a cinque core | Core | 5 | 5 |
| vSphereHAHostTolerance | Il numero di host da tollerare nella configurazione vSphere HA, che equivale a un host |	Host	 | 1 | 1 |
| HostVsanOverheadCorePercentage | La percentuale di core di un host utilizzata da vSAN, che è uguale al 10% o al 0% se l'host non è vsan | % | 10% | 0% |
{: caption="Tabella 4. Descrizione delle variabili nella formula 1" caption-side="top"}

#### Formula per calcolare la memoria disponibile
{: #icp_overview-formulas-2}

La seguente tabella elenca le variabili nella formula 2:

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

| Variabili | Descrizione | Unità | Esempio vSAN | Esempio NFS |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory | Il numero di GB di memoria disponibili per i carichi di lavoro e i servizi nell'ambiente | GB | 693 | 860 |
| HostCount | Il numero di host nel cluster predefinito | Host  | 6 | 6 |
| HostMemory | Il numero di GB non elaborati disponibili in ogni host nel cluster predefinito | GB | 192 | 192 |
| HostVsanCapacityDiskSize | Il numero di GB di una capacità di ogni disco SSD di capacità vSAN su questo host, che è uguale a 960, 1.946 o 3.891, o uguale a 0 GB se non VSAN | GB | 960 | 0 |
| HostOverheadMemory | Il numero di GB di memoria riservati dal server ESXi come sovraccarico, che equivale a 4,6 GB | GB | 4.6 | 4.6 |
| MgmtOverheadMemory | Il numero di GB di memoria riservati dai componenti di gestione vCenter Server (vCenter Server, PSC, AD/DNS, Edge), che corrisponde a 77 GB | GB | 77 | 77 |
| vSphereHAHostTolerance | Il numero di host da tollerare nella configurazione vSphere HA, che equivale a un host | Host	| 1 | 1 |
| HostVsanOverheadMemoryDiskPercentage | Il numero di GB di memoria riservati dalla gestione vSAN (rappresentata come percentuale di uno dei dischi vSAN di capacità), che equivale al 2,75% | % | 2.75% | 2.75% |
| HostVsanOverheadMemory | Il numero di GB di memoria riservati dalla gestione vSAN indipendentemente dallo spazio disco, che è equivalente a 7 GB o a 0 GB se non VSAN | GB |  7 | 0 |
{: caption="Tabella 5. Descrizione delle variabili nella formula 2" caption-side="top"}

## Considerazioni quando installi IBM Cloud Private Hosted
{: #icp_overview-install}

* Ottieni le licenze richieste prima di installare il servizio {{site.data.keyword.cloud_notm}} Private Hosted. Ciò include sia la licenza di {{site.data.keyword.cloud_notm}} Private che quella di {{site.data.keyword.cloud_notm}} Automation Manager. Assicurati che le licenze supportino non solo la distribuzione iniziale del servizio, ma anche l'espansione futura della dimensione nella tua infrastruttura.
* Per le distribuzioni di {{site.data.keyword.cloud_notm}} Private Hosted negli ambienti pronti per la produzione, la dimensione di 64 GB di RAM per host non è supportata. Pertanto, devi selezionare un'opzione che sia superiore a 64 GB di **RAM**.
* Prima che il servizio {{site.data.keyword.cloud_notm}} Private Hosted sia installato nel tuo ambiente, viene eseguito un controllo sulla capacità disponibile del cluster predefinito nell'ambiente per garantire che i componenti del servizio possano essere installati. Se il controllo della capacità ha esito negativo, il servizio non viene installato e il suo stato viene impostato su **Capacity Validation Failed** nella console. Inoltre, viene visualizzato un messaggio della console con maggiori dettagli e ti viene inviata una notifica per email. Per installare il servizio, devi aumentare la capacità nel tuo cluster predefinito aggiungendo più host o liberando RAM, CPU o spazio su disco e quindi aggiungere nuovamente il servizio nella console. Dopo di che, puoi rimuovere il servizio esistente nello stato **Capacity Validation Failed** facendo clic sull'icona **Delete** accanto a esso.
* Se vuoi distribuire dei nodi aggiuntivi, vedi [Distribuzione di nodi aggiuntivi](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering-deploy-nodes#icp_ordering-deploy-nodes).

## Considerazioni quando rimuovi IBM Cloud Private Hosted
{: #icp_overview-remove}

* Vengono eliminate solo le VM (virtual machine) distribuite durante l'installazione iniziale del servizio {{site.data.keyword.cloud_notm}} Private Hosted. Tutti i nodi distribuiti dopo l'installazione non verranno eliminati.
* {{site.data.keyword.cloud_notm}} eliminerà la VXLAN, il DLR e il Gateway edge creati durante la distribuzione iniziale di {{site.data.keyword.cloud_notm}} Private Hosted. Le VM che hai distribuito su VXLAN perderanno la connettività una volta avviata la rimozione del servizio {{site.data.keyword.cloud_notm}} Private Hosted.

## Link correlati
{: #icp_overview-related}

* [Ordine di {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)
* [Guida di vCenter Server e {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [Apri un ticket per {{site.data.keyword.cloud_notm}} privato](https://www.ibm.com/mysupport/s/?language=en_US){:external}
* [{{site.data.keyword.cloud_notm}} Automation Manager licensing](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/licensing.html){:external}
* [{{site.data.keyword.cloud_notm}} Automation Manager components](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_managed_components.html){:external}

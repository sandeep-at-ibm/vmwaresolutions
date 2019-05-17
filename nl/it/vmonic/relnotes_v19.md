---

copyright:

  years:  2016, 2017

lastupdated: "2017-10-13"

subcollection: vmware-solutions


---

# Note sulla release per la V1.9
{: #relnotes_v19}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vSphere on IBM Cloud
{: #relnotes_v19-vss}

Questa release introduce l'offerta VMware vSphere on {{site.data.keyword.cloud_notm}}. Questa offerta ti consente di creare il tuo proprio ambiente virtuale VMware ospitato su IBM personalizzando e ordinando le risorse di calcolo, archiviazione e rete compatibili con VMware in base ai componenti VMware selezionati. Anche se vSphere on {{site.data.keyword.cloud_notm}} non automatizza l'installazione, la configurazione e l'apertura dei componenti VMware facoltativi, hai la massima flessibilità per progettare e architettare un ambiente che risponda al meglio alle tue esigenze aziendali. Inizia creando un nuovo cluster vSphere di server ESXi o ridimensionando un cluster vSphere esistente in un {{site.data.keyword.CloudDataCent_notm}}.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ridimensionamento di cluster vSphere esistenti](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)

## NetApp ONTAP Select on IBM Cloud
{: #relnotes_v19-netapp}

Questa release introduce l'offerta NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}, un dispositivo virtuale per l'archiviazione definita dal software, che implementa NetApp ONTAP Select come servizio sui {{site.data.keyword.baremetal_short}} dedicati di IBM Cloud. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} è offerto sia in configurazioni ad alte prestazioni (tutti gli SSD) che ad alta capacità (tutti i SATA).
Questa offerta ospita la tua archiviazione sull'infrastruttura dedicata e fornisce le funzionalità di NetApp, come la deduplicazione, la compressione e la crittografia dei dati inattivi. Fornisci risorse di archiviazione con agilità e flessibilità mentre proteggi i dati utilizzando funzioni avanzate di gestione dei dati. Ad esempio, utilizza le copie NetApp Snapshot®, le copie FlexClone® e la replica SnapMirror® rapide ed efficienti.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [Ordine di istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Servizio F5 on IBM Cloud
{: #relnotes_v19-f5}

Il servizio F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} è ora disponibile sia per le istanze VMware Cloud Foundation che per le istanze VMware vCenter Server. Questo servizio fornisce servizi intelligenti di bilanciamento del carico L4-L7 e di gestione del traffico su scala locale e globale, una solida protezione firewall per reti e applicazioni web e accesso sicuro e federato alle applicazioni.
Ordina istanze con il servizio F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} incluso quando ordini la tua istanza oppure aggiungi questo servizio alle tue istanze esistenti in un secondo momento utilizzando la scheda **Servizi** nella pagina dei dettagli delle proprietà dell'istanza della console {{site.data.keyword.vmwaresolutions_short}}. A seconda dei tuoi requisiti, puoi selezionare una delle tre opzioni di licenza per BIG-IP VE.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Considerazioni su F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [Gestione di F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)

## Servizi gestiti da IBM Integrated Managed Infrastructure
{: #relnotes_v19-imi}

I servizi gestiti da IBM IMI (Integrated Managed Infrastructure) sono ora disponibili per le istanze VMware Cloud Foundation. IMI può semplificare la gestione dell'infrastruttura virtuale VMware con servizi modulari e può fungere da unico provider attendibile per ridurre la complessità del monitoraggio e della gestione delle infrastrutture IT virtuali. Scarica alcune operazioni quotidiane a IMI, come il monitoraggio, in modo che tu possa concentrarti su iniziative di valore più elevato.

Puoi richiedere una consultazione e una stima in qualsiasi momento dalla pagina **Introduzione**.
Per ulteriori informazioni, vedi [Richiesta di servizi gestiti da IMI](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_imi#requesting-managed-services-from-imi).

## Limitazioni sui nomi delle istanze vCenter Server e NetApp ONTAP Select
{: #relnotes_v19-inst-name}

I nomi di istanza immessi in {{site.data.keyword.vmwaresolutions_short}} quando ordini le tue istanze non possono includere caratteri speciali (come il carattere trattino). Sono consentiti solo caratteri alfanumerici. Questa limitazione non si applica alle istanze Cloud Foundation.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Ordine di istanze NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Aggiornamenti per le istanze VMware Cloud Foundation
{: #relnotes_v19-vcf}

### Personalizza la CPU e la memoria della tua istanza
{: #relnotes_v19-custom-cpu}

Insieme alle opzioni Small e Standard precostruite e testate, è disponibile un'opzione di server personalizzabile dall'utente. Per abbinare al meglio il rapporto CPU-RAM dei carichi di lavoro con l'hardware compatibile con VMware, puoi ora selezionare in modo indipendente il numero totale di core su un server a doppia CPU e la quantità di RAM. L'archiviazione locale non è personalizzabile.

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v19-vcs}

### Supporto cluster in più data center
{: #relnotes_v19-cross-dc}

Per migliorare il ridimensionamento del tuo ambiente VMware ospitato, puoi ora creare un nuovo cluster in un altro pod dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) o in un {{site.data.keyword.CloudDataCent_notm}} diverso rispetto al cluster iniziale distribuito nell'istanza.

Per ulteriori informazioni, vedi [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

### Modifica dei componenti
{: #relnotes_v19-change-comp}

Questa release elimina l'impatto sulle operazioni all'interno della console {{site.data.keyword.vmwaresolutions_short}} quando l'amministratore del Single Sign-On modifica alcune risorse di vCenter Server da uno strumento VMware nativo. Ad esempio, puoi ora modificare i nomi del data center virtuale, del cluster, degli switch, dei gruppi di porte e degli archivi dati di VMware dal client web VMware vSphere per personalizzare le distribuzioni in convenzioni di denominazione aziendale o personale e senza alcun impatto successivo sulle operazioni dall'interno della console {{site.data.keyword.vmwaresolutions_short}}.

Per ulteriori informazioni, vedi [Impatti della modifica di componenti per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact).

### Ulteriori dimensioni della RAM
{: #relnotes_v19-ram-sizes}

Quando ordini le istanze vCenter Server o aggiungi cluster per le istanze vCenter Server, puoi ora scegliere tra più dimensioni di RAM per abbinare meglio il rapporto CPU-RAM del carico di lavoro con l'hardware. Quando ordini un server dalla console {{site.data.keyword.vmwaresolutions_short}}, nell'opzione di configurazione **Personalizzato dall'utente**, sono disponibili le seguenti opzioni: 64 GB, 128 GB, 256 GB, 384 GB, 512 GB, 768 GB, 1,5 TB.

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Aggiornamento della versione NFS (Network File System)

La versione 4.1 di NFS (Network File System) non è più disponibile come impostazione di archiviazione dall'interfaccia utente. Tutte le istanze vCenter Server vengono distribuite con NFS V3. Sebbene NFS V3 sia una versione precedente del protocollo, abilita funzioni avanzate sugli ambienti VMware con supporto per VMware SDRS (Storage Distributed Resource Scheduler) e SIOC (Storage I/O Control).

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Nome del dominio Domain Name Server per un singolo sito
{: #relnotes_v19-single-site-dns}

Durante un ordine, puoi ora fornire il nome del dominio DNS (Domain Name Server) per un'istanza vCenter Server. Viene distribuita una VSI (Virtual Server Instance) di Microsoft Windows Server consultabile, che funziona come DNS per l'istanza in cui sono registrati gli host e le VM (Virtual Machine). Microsoft Active Directory (AD) è anche configurato sulla VSI di Microsoft Windows e il nome del dominio DNS è il nome root dell'insieme di strutture del dominio AD. Questa VSI di Microsoft Windows è disponibile solo nella V1.9 e successive.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)

## Requisiti per l'istallazione automatica degli aggiornamenti di Windows Server
{: #relnotes_v19-win-server}

Microsoft Active Directory (AD) / Domain Name Server (DNS) è configurato automaticamente solo per scaricare gli aggiornamenti. Non installa e riavvia automaticamente questi aggiornamenti. Devi installare gli aggiornamenti manualmente ed eseguire il riavvio a un orario pianificato che eviti interruzioni della configurazione del server Active Directory in corso e di altri lavori di backup. Per applicare gli aggiornamenti di Windows, installa gli aggiornamenti manualmente.

## Documentazione nuova e aggiornata
{: #relnotes_v19-new-docs}

* Impara a salvaguardare le tue istanze Cloud Foundation multisito private mentre estendi le tue applicazioni VMware per utilizzare i servizi {{site.data.keyword.cloud_notm}} pubblici. Per ulteriori informazioni, vedi [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}.
* Viene fornita ulteriore documentazione per la configurazione di firewall che consentono tutte le comunicazioni di protocollo dalle VM (Virtual Machine) IBM CloudDriver e SDDC Manager. Per ulteriori informazioni, vedi [Componenti e considerazioni per Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations).

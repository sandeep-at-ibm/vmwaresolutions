---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Note sulla release per la V3.0
{: #relnotes_v30}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Fine del supporto per VMware Cloud Foundation on IBM Cloud
{: #relnotes_v30-vcf-eos}

Nel tentativo di consolidare le nostre offerte per una migliore esperienza del cliente, la piattaforma {{site.data.keyword.vmwaresolutions_short}} non offrirà più VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a partire dal 13 maggio 2019.

Nel corso del tempo, tutti i clienti verranno indirizzati a VMware vCenter Server on {{site.data.keyword.cloud_notm}}, la nostra soluzione di punta di data center definito dal software VMware su {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

I clienti esistenti che utilizzano VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} saranno assistiti nella conversione a VMware vCenter Server on {{site.data.keyword.cloud_notm}} entro la data di fine supporto del 13 maggio 2019.

Dopo il 13 maggio, le capacità di gestione per VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} verranno bloccate nella console {{site.data.keyword.vmwaresolutions_short}} fino a quando non verranno convertite a VMware vCenter Server on {{site.data.keyword.cloud_notm}}. I clienti che hanno scelto di non migrare o convertire la loro istanza VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a VMware vCenter Server on {{site.data.keyword.cloud_notm}}, possono accedere alle loro istanze dalla console dell'infrastruttura {{site.data.keyword.cloud_notm}}.

## Rimosso il supporto per i server Broadwell 2-CPU
{: #relnotes_v30-broadwell}

A partire dalla release V3.0, i server Broadwell 2-CPU non sono più disponibili per la distribuzione per i nuovi cluster e le nuove istanze vCenter Server, vCenter Server with Hybridity Bundle, vCenter Server with NSX-T e vSphere on {{site.data.keyword.cloud_notm}}. Puoi ancora aggiungere server ai cluster esistenti.

## Miglioramenti alle operazioni di NFS (network file system)
{: #relnotes_v30-nfs}

A partire dalla release V3.0, puoi aggiungere o rimuovere simultaneamente l'archiviazione NFS e i server ESXi sui cluster nello stato **Ready to Use** (Pronto per l'utilizzo). Ad esempio, puoi aggiungere o rimuovere un server ESXi in un cluster e aggiungere o rimuovere l'archiviazione NFS in un altro cluster. Ciò si applica a tutte le istanze vCenter Server e vCenter Server with NSX-T.

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v30-vcs}

Questa release applica i seguenti aggiornamenti e miglioramenti:

* vSphere ESXi 6.7 Aggiornamento 1 (build 6.7.0-13004448)
* vSphere ESXi 6.5 Aggiornamento 2 (build 6.5.0-13004031)
* vCenter Server Appliance 6.7 Aggiornamento 1b (build 6.7.0-11727113)
* Platform Services Controller 6.7 Aggiornamento 1b (build 6.7.0-11727113) 

Per ulteriori informazioni, vedi [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

Viene eseguito l'upgrade del software Windows ordinato per i servizi Microsoft Active Directory (AD) e DNS (Domain Name System) a Windows Server 2016 per entrambe le opzioni di configurazione: le VSI (Virtual Server Instances) e le due VM Windows altamente disponibili. Per ulteriori informazioni sulla selezione dei tuoi componenti VMware, vedi [Diba di software per le istanze vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software).

### Miglioramenti all'archiviazione vSAN
{: #relnotes_v30-vcs-vsan}

* Ora, quando utilizzi l'archiviazione vSAN, il numero di server Bare Metal che puoi ordinare può essere superiore a quattro. Ciò si applica a tutte le istanze vCenter Server, vCenter Server with Hybridity e vCenter Server with NSX-T.
* A partire dalla release V3.0, viene ordinata una SSD (solid state drive) M.2 con la tua istanza di archiviazione vSAN. Puoi ordinare fino a 10 dischi di capacità o un totale di 12 dischi di capacità se selezioni l'opzione **Alte prestazioni con Intel Optane**.

Per ulteriori informazioni, vedi la sezione *Impostazioni di archiviazione* in:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [Ordine di istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [Ordine di istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

Nella release corrente, HyTrust CloudControl 5.5 è installato su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in HyTrust CloudControl 5.5, vedi [What's New in HyTrust CloudControl Version 5.5](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

La release corrente installa HyTrust DataControl 4.3 su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in HyTrust DataControl 4.3, vedi [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

La release corrente installa HyTrust KeyControl 4.3 su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in HyTrust KeyControl 4.3, vedi [What's New in KeyControl and DataControl Version 4.3](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

La release corrente installa {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2, insieme a {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, su tutte le istanze di nuova distribuzione.

Per ulteriori informazioni sulle nuove funzioni in {{site.data.keyword.cloud_notm}} Private v3.1.2, vedi [What's new in {{site.data.keyword.cloud_notm}} Private v3.1.2](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}.
Per ulteriori informazioni sulle nuove funzioni in {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2, vedi [What's new in {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

Ora, sono disponibili due nuovi endpoint a Londra e negli Stati Uniti Est per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Configurazione del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config).

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

La release corrente installa IBM Spectrum Protect™ Plus V10.1.3 su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni di IBM Spectrum Protect Plus V10.1.3, vedi [IBM Spectrum Protect Plus updates](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

Ora puoi aggiungere Zerto on {{site.data.keyword.cloud_notm}} su tutte le istanze che sono solo private. Se scegli di installare Zerto sulle istanze solo private, devi configurare il tuo server proxy e anche la funzione Call Home per Zerto. Per ulteriori informazioni, vedi [Ordine di Zerto on {{site.data.keyword.cloud_notm}} per le istanze che sono solo con rete privata](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only).

## Documentazione nuova e aggiornata

* Ora è disponibile la documentazione per assisterti nell'upgrade dei componenti {{site.data.keyword.vmwaresolutions_short}} a VMware vSphere 6.7. Questo upgrade è necessario se vuoi continuare a trarre vantaggio dall'automazione {{site.data.keyword.vmwaresolutions_short}}. Per ulteriori informazioni, vedi [Upgrade del software vCenter Server vSphere da VMware vSphere 6.5 a 6.7](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade).
* Ora è disponibile la documentazione di riferimento per fornirti gli ID utente conservati da {{site.data.keyword.vmwaresolutions_short}} per essere utilizzati dall'automazione {{site.data.keyword.cloud_notm}}. Anche i possibili messaggi che vengono visualizzati nei log della cronologia della tua istanza sono disponibili per essere esaminati. Per ulteriori informazioni, vedi [ID utente IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids) e [Messaggi della cronologia dell'istanza](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_messages).
* L'autorizzazione **Riavvia/Controlla** è stata aggiunta alla tabella che descrive le autorizzazioni necessarie per l'account dell'infrastruttura IBM. Per ulteriori informazioni, vedi [Autorizzazioni per l'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions).
* È disponibile una nuova documentazione di riferimento per le seguenti API. Per ulteriori informazioni, vedi [Riferimento API](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}.
  * Elenca tutti i messaggi della cronologia per un'istanza VMware vCenter Server specificata
  * Aggiunge le archiviazioni condivise a un cluster specificato
  * Elimina le archiviazioni NFS da un cluster specificato

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v30-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

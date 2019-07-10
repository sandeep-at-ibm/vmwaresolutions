---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Note sulla release per la V2.9
{: #relnotes_v29}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## VMware vCenter Server on IBM Cloud with NSX-T
{: #relnotes_v29-vcs-nsx-t}

Questa release introduce l'offerta VMware vCenter Server on {{site.data.keyword.cloud_notm}} with NSX-T come un'offerta di test sandbox o una prova di utilizzo PoC (proof of concept). vCenter Server with NSX-T è un cloud ospitato privatamente che ti consente di eseguire un test drive della piattaforma di rete di prossima generazione di Vmware, NSX-T-

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Panoramica di vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview)
* [Ordine di istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Fine del supporto per VMware Cloud Foundation on IBM Cloud
{: #relnotes_v29-vcf-eos}

Per consolidare le nostre offerte per una migliore esperienza del cliente, {{site.data.keyword.cloud_notm}} non fornirà più il supporto per VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} a partire dal 13 maggio 2019.  
 
Nel corso del tempo, tutti i clienti verranno indirizzati a VMware vCenter Server on {{site.data.keyword.cloud_notm}}, che offre maggiore flessibilità per quanto riguarda le opzioni di archiviazione e licenza.
I clienti esistenti che utilizzano VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} saranno assistiti nella migrazione a VMware vCenter Server on {{site.data.keyword.cloud_notm}} entro la data di fine supporto del 13 maggio 2019.

Dopo il 13 maggio, le capacità di gestione per VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} saranno rimosse dalla console {{site.data.keyword.vmwaresolutions_short}}. È possibile accedere alle istanze che non sono state migrate a VMware vCenter Server on {{site.data.keyword.cloud_notm}} mediante la console dell'infrastruttura IBM Cloud.

I clienti verranno contattati dal supporto {{site.data.keyword.cloud_notm}} prima del 25 marzo 2019 per iniziare la migrazione da VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni sulle opzioni di migrazione per i clienti esistenti, vedi la [pagina wiki di {{site.data.keyword.vmwaresolutions_short}}](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/Wf58c4c538dbf_45b4_b7a7_5003d0ceb79b/page/IBM%20Cloud%20for%20VMware%20Solutions){:new_window}.
 
I clienti possono visualizzare la loro istanza VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} esistente nella [console {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/infrastructure/vmware-solutions/console/gettingstarted).

## Supporto di VMware vSphere 6.7 Aggiornamento 1
{: #relnotes_v29-vsphere}

Ora disponi dell'opzione di ordinare VMware vSphere versione 6.7 Aggiornamento 1 con le tue istanze VMware vCenter Server, VMware vCenter Server with Hybridity Bundle e VMware vSphere on {{site.data.keyword.cloud_notm}}.

Inoltre, le istanze Single-node Trial for Migration and App Modernization sono ora ordinate con vSphere Enterprise Plus 6.7u1.

vSphere Enterprise Plus 6.7u1 è disponibile solo per {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Broadwell e Skylake.

Per ulteriori informazioni, vedi le sezioni _Impostazioni di licenza_ in:

* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Ordine di istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Supporto per le API (Application Programming Interface)
{: #relnotes_v29-api}

Le API (Application Programming Interface) sono ora disponibili per la distribuzione e l'eliminazione di istanze e l'aggiunta e la rimozione di cluster e server ESXi.

La documentazione dell'API REST è disponibile anche nella sezione *Riferimento* della documentazione dell'utente. Per ulteriori informazioni, vedi il documento relativo all'[API {{site.data.keyword.vmwaresolutions_short}}](https://cloud.ibm.com/apidocs/vmware-solutions).

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v29-vcs}

Questa release applica i seguenti aggiornamenti e miglioramenti:

* vSphere ESXi 6.7 Aggiornamento 1 (build 6.7.0-11675023)
* vSphere ESXi 6.5 Aggiornamento 2 (build 6.5.0-11925212)
* vSphere 6.7 Distributed vSwitch 6.6.0
* vSphere 6.5 Distributed vSwitch 6.5.0
* vCenter Server Appliance 6.7 U1 (build 6.7.0-10244745)
* vSAN 6.7.0 U1
* NSX for vSphere 6.4.4 (build 11197766)
* NSX-T for vSphere 2.4

Per ulteriori informazioni sulla selezione dei tuoi componenti VMware, vedi [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Aggiornamenti ai data center
{: #relnotes_v29-dc}

I seguenti nuovi data center sono disponibili per la distribuzione: **FRA-05 - Francoforte** e **LON-05 - Londra**. Per ulteriori informazioni, vedi [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning).

### Miglioramenti del server ESXi
{: #relnotes_v29-vcs-esxi}

* Il protocollo SSH (Secure Shell) è ora disabilitato per i server ESXi prima della fornitura dell'istanza. Se vuoi abilitare SSH, vedi [Enable SSH from the vSphere Web Client](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vcli.getstart.doc%2FGUID-C3A44A30-EEA5-4359-A248-D13927A94CCE.html).
* A partire dalla release V2.9, sono disponibili le seguenti operazioni server ESXi:

   * Aggiungi nuovi server ESXi a un cluster esistente mentre i server sono in modalità di manutenzione. Le VM non vengono migrate ai nuovi server finché non ne esegui la rimozione dalla modalità di manutenzione.
   * Aggiungi o rimuovi simultaneamente dei server ESXi in più cluster nella tua istanza.

Per ulteriori informazioni, vedi [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers).

### Dimensione di archiviazione di Network File System
{: #relnotes_v29-vcs-nfs}

Per gli ordini dell'istanza vCenter Server, puoi ora aggiungere fino a 24 TB di archiviazione condivisa NFS (Network File System) per i livelli di prestazioni di 0,25, 2 e 4 IOPS/GB.

Il livello di prestazioni di 10 IOPS/GB è ancora limitato a una capacità massima di 4 TB per condivisione file.
{:note}

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v29-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v29-services-caveonix}

Il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware vCenter Server distribuite nelle, o di cui è stato eseguito l'upgrade alle, release V2.9 o successive. Questo servizio può aiutare a gestire i rischi informatici e di conformità con un monitoraggio proattivo e dei controlli di difesa automatizzati per proteggere da minacce e soddisfare le normative del settore e quelle governative.

Puoi ordinare le istanze vCenter Server con il servizio Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} includo oppure aggiungere questo servizio alle tue istanze vCenter Server esistenti in un secondo momento dalla scheda **Servizi** nella pagina dei dettagli dell'istanza.

Puoi anche ordinare una licenza Caveonix RiskForesight autonoma senza associarla ad alcuna istanza VMware per la concessione della licenza e l'attivazione dei tuoi carichi di lavoro in loco.

Per ulteriori informazioni, vedi:
* [Considerazioni per Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Ordine di Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Considerazioni per le licenze Caveonix](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_considerations)
* [Ordine di licenze Caveonix](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_license_ordering)

### F5 on IBM Cloud
{: #relnotes_v29-services-f5}

Nella release corrente, F5-BigIP VE V14.1.0.2 è installato su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in F5-BigIP VE V14.1.0.2, vedi [Release Note: BIG-IP 14.1.0 New and Installation](https://techdocs.f5.com/kb/en-us/products/big-ip_ltm/releasenotes/product/relnote-bigip-14-1-0.html){:new_window}.

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v29-services-htcc}

Nella release corrente, HyTrust CloudControl 5.4.2 è installato su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in HyTrust CloudControl 5.4.2, vedi [HyTrust CloudControl Release Notes Version 5.4.2](https://docs.hytrust.com/CloudControl/5.4.2/Online/index.html#HTCC_Admin_Guide/_FrontMatter/Whats-New.html%3FTocPath%3D_____2){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v29-services-kmip}

Due nuovi endpoint sono ora disponibili a Sydney per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Configurazione del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering#kmip_standalone_ordering-config).

(Aggiornato il 9 aprile 2019) In precedenza, KMIP for VMware on {{site.data.keyword.cloud_notm}} ha utilizzato IBM Key Protect for {{site.data.keyword.cloud_notm}} per creare, crittografare e decrittografare le chiavi di crittografia. A partire dalla release V2.9, KMIP for VMware on {{site.data.keyword.cloud_notm}} può utilizzare anche {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services, una serie completa di servizi di crittografia e gestione delle chiavi, per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Panoramica di KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) e [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](/docs/services/hs-crypto?topic=hs-crypto-get-started).

### Veeam on IBM Cloud
{: #relnotes_v29-services-veeam}

Nella release corrente, Veeam Backup and Replication 9.5 Aggiornamento 4 è installato su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in Veeam 9.5u4, vedi [Release information for Veeam Backup and Replication 9.5 Update 4](https://www.veeam.com/kb2878){:new_window}.

### Zerto on IBM Cloud
{: #relnotes_v29-services-zerto}

Nella release corrente, Zerto Virtual Replication 6.5 aggiornamento 3 è installato su tutte le istanze di nuova distribuzione. Per ulteriori informazioni sulle nuove funzioni in Zerto Virtual Replication 6.5 aggiornamento 3, vedi [Release notes for Zerto Virtual Replication V6.5 Update 3](http://s3.amazonaws.com/zertodownload_docs/Latest/Zerto%20Virtual%20Replication%20Release%20Notes.pdf){:new_window}.

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v29-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* Nella pagina **Infrastruttura**, una nuova tabella **Interfaccia di rete** fornisce i dettagli di VLAN, sottorete e indirizzo IP per il tuo cluster.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

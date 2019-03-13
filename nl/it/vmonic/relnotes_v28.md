---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

---

# Note sulla release per la V2.8
{: #relnotes_v28}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Istanze Single-node Trial for Migration and App Modernization
{: #relnotes_v28-single-node-trial}

Single-node Trial for Migration and App Modernization è un modo rapido per eseguire un test drive di {{site.data.keyword.cloud_notm}} per migrare i carichi di lavoro VMware in {{site.data.keyword.cloud_notm}} e quindi modernizzare i carichi di lavoro utilizzando i contenitori. Questa prova è una versione di {{site.data.keyword.icpfull_notm}} Hosted su VMware vCenter Server on {{site.data.keyword.cloud_notm}} che fornisce la piattaforma di gestione di Kubernetes per i contenitori e la piattaforma VMware a singolo tenant che può essere gestita utilizzando gli stessi strumenti familiari degli ambienti in loco.

Per ulteriori informazioni, vedi [Panoramica di Single-node Trial for Migration and App Modernization](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-single-node-trial-for-migration-and-app-modernization-overview).

## Aggiunta e rimozione dell'archiviazione NFS (Network File System)
{: #relnotes_v28-nfs}

A partire dalla release della V2.8, puoi ora aggiungere condivisioni di archiviazione NFS (Network File System) a un cluster vCenter Server NFS o vSAN esistente e rimuovere condivisioni file NFS da un cluster vCenter Server esistente.

Le seguenti opzioni per l'archiviazione al livello del file condivisa e personalizzata non sono disponibili:

* Dimensioni di condivisione NFS a partire da 20GB fino a 12TB a incrementi di GB singoli
* 0,25 IOPS/GB

Per ulteriori informazioni, vedi le sezioni *Aggiunta dell'archiviazione NFS alle istanze vCenter Server* e *Rimozione dell'archiviazione NFS dalle istanze vCenter Server* in [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).

## Supporto server Broadwell E5-2690 e E7-8890 con certificato SAP
{: #relnotes_v28-broadwell-e5-e7}

A partire dalla release della V2.8, i seguenti nuovi modelli di CPU {{site.data.keyword.baremetal_short_sing}} {{site.data.keyword.cloud_notm}} sono disponibili per la distribuzione per le istanze e i cluster di VMware vCenter Server on {{site.data.keyword.cloud_notm}} e di VMware vSphere on {{site.data.keyword.cloud_notm}}:

* Processore Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,60 GHz / 512 GB di RAM
* Processore Quad Intel Xeon E7-8890 v4 / 96 core totali, 2,20 GHz / 1024 GB di RAM
* Processore Quad Intel Xeon E7-8890 v4 / 96 core totali, 2,20 GHz / 2048 GB di RAM
* Processore Quad Intel Xeon E7-8890 v4 / 96 core totali, 2,20 GHz / 4096 GB di RAM

Per ulteriori informazioni, vedi la sezione *Impostazioni di {{site.data.keyword.baremetal_short_sing}}* in:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Supporto server Broadwell E7-4820 e E7-4850
{: #relnotes_v28-broadwell-e7}

A partire dalla release della V2.8, i seguenti nuovi modelli di CPU {{site.data.keyword.baremetal_short_sing}} {{site.data.keyword.cloud_notm}} sono disponibili per la distribuzione per le istanze e i cluster di vCenter Server, vCenter Server with Hybridity Bundle, Cloud Foundation e vSphere on {{site.data.keyword.cloud_notm}}:

* Quad Intel Xeon E7-4820 v4 / 40 core totali, 2,0 GHz
* Quad Intel Xeon E7-4850 v4 / 64 core totali, 2,1 GHz

Per ulteriori informazioni, vedi la sezione *Impostazioni di {{site.data.keyword.baremetal_short_sing}}* in:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [Ordine di istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [Ordine di istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance#bare-metal-server-settings)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Platform Services Controller (PSC) integrato
{: #relnotes_v28-psc}

A partire dalla release della V2.8, vCenter Server viene distribuito con un PSC (Platform Services Controller) integrato, ovvero vCenter Server, i componenti di vCenter Server e il PSC vengono distribuiti su una singola macchina virtuale. Questa modifica si applica a tutte le istanze vCenter Server, vCenter Server with Hybridity e NetApp appena distribuite.

Per le istanze che vengono aggiornate da un release precedente alla V2.8, il PSC non è integrato in vCenter Server. Se vuoi utilizzare il PSC integrato, devi eseguire autonomamente la conversione dal PSC esterno al PSC integrato.

In una configurazione multisito in cui l'istanza primaria è un'istanza aggiornata per la quale il PSC è stato convertito manualmente da esterno a integrato, tutte le istanze secondarie della V2.8 appena distribuite avranno il PSC integrato.

Per ulteriori informazioni, vedi la sezione *Architettura di vCenter Server* in [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture).

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v28-vcs}

Questa release applica i seguenti aggiornamenti e miglioramenti:

* vSphere ESXi 6.5 Aggiornamento P3 (build 6.5.0-10884925)
* vCenter Server 6.5 U2d (build 6.5.0-10964411)
* Platform Services Controller 6.5 U2d (build 6.5.0-10964411)

## Aggiornamenti per le istanze VMware Cloud Foundation
{: #relnotes_v28-cf}

Questa release applica i seguenti aggiornamenti e miglioramenti:

* vSphere ESXi 6.5 Aggiornamento EP11 (build 6.5.0-10719125)
* vCenter Server 6.5 U2c (build 6.5.0-9451637)
* Platform Services Controller 6.5 U2c (build 6.5.0-9451637)

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

La release corrente installa IBM Spectrum Protect™ Plus V10.1.2 su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di IBM Spectrum Protect Plus V10.1.2, vedi [Aggiornamenti di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

In precedenza, potevi ordinare un'istanza Cloud Foundation o vCenter Server con il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} incluso o aggiungere il servizio a un'istanza Cloud Foundation o vCenter Server esistente dopo la distribuzione iniziale.

A partire dalla release della V2.8, il servizio è disponibile come servizio autonomo senza essere associato a un'istanza VMware. Ogni istanza del servizio può servire una o più istanze Cloud Foundation, istanze vCenter Server o cluster vSphere.

Per ulteriori informazioni, vedi [Panoramica di KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations).

## Documentazione dell'architettura di riferimento
{: #relnotes_v28-ref}

(Aggiornato l'8 febbraio 2019) La seguente documentazione tecnica è ora disponibile nella sezione *Riferimento* della documentazione dell'utente:

* [{{site.data.keyword.vmwaresolutions_short}} con architettura NSX-T](/docs/services/vmwaresolutions/archiref/vcsarch?topic=vmware-solutions-vcsarch-overview)
* [Architettura di riferimento Caveonix RiskForesight](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [Guida operativa e per la distribuzione di HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/vcshcx?topic=vmware-solutions-vcshcx-intro)

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v28-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

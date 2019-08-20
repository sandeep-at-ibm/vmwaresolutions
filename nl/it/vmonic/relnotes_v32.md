---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: release notes, what's new, version 3.2

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Note sulla release per la V3.2
{: #relnotes_v32}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Disponibilità di VMware HCX for IBM Cloud
{: #relnotes_v32-HCX}

A partire dalla release 3.2, hai ora l'opzione di ordinare il servizio VMware HCX on {{site.data.keyword.cloud_notm}} con le istanze VMware vCenter Server. Precedentemente, potevi ordinare solo il servizio HCX on {{site.data.keyword.cloud_notm}} tramite l'istanza VMware vCenter Server with Hybridity Bundle. L'istanza vCenter Server with Hybridity Bundle non è più disponibile.

È richiesto un impegno a termine di 12 mesi quando ordini il servizio HCX on {{site.data.keyword.cloud_notm}}. Dopo la scadenza dell'impegno a termine di 12 mesi, puoi installare e disinstallare il servizio HCX on {{site.data.keyword.cloud_notm}} e puoi aggiungere e rimuovere gli host e i cluster senza limitazioni. Gli addebiti sul tuo account verranno poi fatti su una base mensile e puoi recedere in qualsiasi momento.

Per ulteriori informazioni, vedi [Panoramica di VMware HCX on IBM Cloud](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations).

## Supporto di VMware vSphere 6.7 Aggiornamento 2
{: #relnotes_v32-vsphere-v67}

Ora disponi dell'opzione di ordinare VMware vSphere versione 6.7 Aggiornamento 2 con le tue istanze VMware vCenter Server, VMware vCenter Server with NSX-T Bundle e VMware vSphere on IBM Cloud. vSphere Enterprise Plus 6.7u2 sostituisce l'opzione di ordinare vSphere Enterprise Plus 6.7u1 con le nuove istanze. Inoltre, le istanze Single-node Trial for Migration and App Modernization and Single-node Trial for Data Protection and Disaster Recovery vengono ora ordinate con vSphere Enterprise Plus 6.7u2.

vSphere Enterprise Plus 6.7u2 è disponibile per Skylake, Cascade Lake e Broadwell {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

Se hai un'istanza esistente con vSphere Enterprise Plus 6.7u1, hai l'opzione di aggiungere nuovi host con vSphere Enterprise Plus 6.7u1 o vSphere Enterprise Plus 6.7u2. Tuttavia, l'aggiunta di un nuovo host 6.7u1 non è sicura. Si consiglia di aggiornare i tuoi host all'ultima versione del server ESXi il prima possibile.
{:note}

## Supporto Cascade Lake
{: #relnotes_v32-cascade}

A partire dalla release della V3.2, i seguenti nuovi modelli di CPU {{site.data.keyword.baremetal_short_sing}} sono disponibili per la distribuzione con le istanze e i cluster con VMware vSphere 6.7 Aggiornamento 2. Questo si applica a vCenter Server, vCenter Server with NSX-T e VMware vSphere.

* Processore Dual Intel Xeon Gold 4210 / 20 core totali, 2,3 GHz
* Processore Dual Intel Xeon Gold 5218 / 32 core totali, 2,3 GHz
* Processore Dual Intel Xeon Gold 6248 / 40 core totali, 2,5 GHz

Cascade Lake {{site.data.keyword.baremetal_short}} sono disponibili in una regione multizona {{site.data.keyword.CloudDataCents_notm}}. Per ulteriori informazioni, vedi [Panoramica della regione multizona (o MZR, Multi-Zone Region)
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Per ulteriori informazioni sulle impostazioni {{site.data.keyword.baremetal_short_sing}}, vedi:

* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-cascade)
* [Ordine di istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-cascade)
* [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstance-cascade)

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v32-vcs}

Questa release applica gli upgrade e i miglioramenti di seguito indicati per le istanze, i cluster e gli host appena distribuiti.

* VMware NSX for vSphere 6.4.5 (build 13282012)
* vSphere ESXi 6.7 EP 10 (build 6.7.0-13981272)
* vCenter Server Appliance 6.7 Aggiornamento 2b (6.7.0.-13843469)
* Platform Services Controller 6.7 Aggiornamento 2b (6.7.0.-13843469)

Per ulteriori informazioni, vedi [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Denominazione del cluster iniziale
{: #relnotes_v32-vcs-initial-cluster}

Puoi ora specificare il nome del tuo cluster iniziale in modo che venga creato contemporaneamente a quando inserisci il tuo ordine dell'istanza. Per ulteriori informazioni, vedi:

* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance)
* [Ordine di istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_orderinginstance)

## Aggiornamenti per le istanze VMware vSphere
{: #relnotes_v32-vss}

Una VLAN pubblica non è più necessaria quando ordini un nuovo cluster vSphere solo con una rete privata.

Per ulteriori informazioni, vedi la sezione *Impostazioni dell'interfaccia di rete* in [Ordine di nuovi cluster vSphere
](/docs/services/vmwaresolutions?topic=vmware-solutions-vs_orderinginstances#vs_orderinginstances-network-interface-settings).

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v32-services}

Questa release installa le seguenti versioni del servizio sulle istanze appena distribuite.

* F5 on {{site.data.keyword.cloud_notm}} 15.0.0
* Veeam on {{site.data.keyword.cloud_notm}} 9.5 Aggiornamento 4b
* VMware HCX on {{site.data.keyword.cloud_notm}} 3.5.1-14222959
* Zerto on {{site.data.keyword.cloud_notm}} 6.5 Aggiornamento 4

### VMware vRealize Operations and vRealize Log Insight on IBM Cloud
{: #relnotes_v32-services-vrealize}

Il servizio vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware vCenter Server distribuite nelle, o di cui è stato eseguito l'upgrade alle, release V3.2 o successive.

Questo servizio fornisce VMware vRealize Log Insight (vRLI) integrato con vRealize Operations Manager (vROps), per aiutarti a monitorare e gestire in modo proattivo l'integrità e le prestazioni del tuo ambiente virtualizzato, nonché di eseguire l'analisi della causa principale di un problema filtrando e eseguendo una ricerca tramite i log.

Puoi ordinare le istanze vCenter Server con vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}} incluso oppure aggiungere questo servizio alle tue istanze esistenti in un secondo momento dalla scheda Servizi nella pagina dei dettagli dell'istanza.

Puoi anche utilizzare le tue licenze vRealize Operations and vRealize Log Insight aziendali nel cloud (per CPU o OSI) oppure puoi noleggiare delle licenze da IBM Cloud.

Per ulteriori informazioni, vedi [Panoramica di VMware vRealize Operations and vRealize Log Insight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vrops_overview).

## Documentazione nuova e aggiornata
{: #relnotes_v32-updated-doc}

* La documentazione di Activity Tracker è aggiornata. Per ulteriori informazioni, vedi [Eventi di Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v32-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* I requisiti del nome dell'istanza sono stati modificati. Per ulteriori informazioni, vedi l'argomento appropriato per il tipo di istanza che stai ordinando.
* Il formato del server ESXi completo è stato modificato. Per ulteriori informazioni, vedi l'argomento appropriato per il tipo di istanza che stai ordinando.
* Sono stati aggiunti degli zeri iniziali ai nomi dell'host e del cluster per consentire un ordinamento corretto.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

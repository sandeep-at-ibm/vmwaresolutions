---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-16"

keywords: release notes, what's new, version 3.1

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Note sulla release per la V3.1
{: #relnotes_v31}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:external}.

## Istanze Single-node Trial for Data Protection and Disaster Recovery
{: #relnotes_v31-dr-bundle}

Single-node Trial for Data Protection and Disaster Recovery è un modo rapido per eseguire un test drive di {{site.data.keyword.cloud_notm}} per migrare e recuperare carichi di lavoro VMware in {{site.data.keyword.cloud_notm}}. Questa prova è una versione di VMware vCenter Server on IBM Cloud, una piattaforma VMware a singolo tenant che può essere gestita utilizzando gli stressi strumenti familiari degli ambienti in loco. Questa prova include i servizi Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, vedi [Panoramica di Single-node Trial for Disaster Recovery](/docs/services/vmwaresolutions?topic=vmware-solutions-dr_backup_bundle_overview).

## IBM Cloud Expert Services
{: #relnotes_v31-expert-services}

Puoi ora coinvolgere IBM Expert Services per lavorare insieme al tuo team interno per distribuire, migrare e gestire la tua soluzione {{site.data.keyword.cloud_notm}} dalla pianificazione alla modernizzazione o qualsiasi stadio intermedio.

Puoi aggiungere {{site.data.keyword.cloud_notm}} Expert Services al tuo ordine dell'istanza in qualsiasi momento richiedendo una consultazione dalla pagina **Introduzione**. Per ulteriori informazioni, vedi [Richiesta di {{site.data.keyword.cloud_notm}} Expert Services](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_ices).

## Integrazione con lo stimatore di costi di IBM Cloud

Puoi ora stimare il costo delle tue risorse {{site.data.keyword.vmwaresolutions_short}} nello strumento di stima unificato fornito dal framework {{site.data.keyword.cloud_notm}}. Con questa funzione, puoi salvare un'istantanea delle risorse in tutto il catalogo {{site.data.keyword.cloud_notm}} ed eseguirne il salvataggio in un singolo file PDF che puoi scaricare per fare riferimento a esso in un secondo momento. Lo stimatore dei costi non è un contratto o una quotazione irrevocabile bensì solo una stima del tuo costo totale.

Per ulteriori informazioni sullo stimatore di costi, vedi [Stima dei costi](/docs/billing-usage?topic=billing-usage-cost).

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v31-vcs}

Questa release applica gli upgrade e i miglioramenti di seguito indicati per le istanze, i cluster e gli host appena distribuiti.

* vSphere ESXi 6.5 Aggiornamento 2 (build 6.5.0-13635690)
* vCenter Server Appliance 6.5 Aggiornamento 2g (build 6.5.0-13638625)

Per ulteriori informazioni, vedi [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom).

### Configurazione del server ESXi alternativa per i cluster
{: #relnotes_v31-esxi-config}

Puoi ora aggiungere dei nuovi server ESXi a un cluster esistente selezionando una configurazione esistente oppure una configurazione alternativa rispetto agli host esistenti nel cluster. Quando ordini dei nuovi server dalla finestra **Aggiungi server**, puoi selezionare istantaneamente una configurazione esistente nel cluster oppure scegliere una nuova configurazione {{site.data.keyword.baremetal_short_sing}}. Ciò si applica a tutte le istanze vCenter Server, vCenter Server with Hybridity e vCenter Server with NSX-T.

Per evitare problemi di prestazioni o di stabilità, ti consigliamo di fare in modo che i cluster utilizzino la stessa configurazione, oppure una simile, per quanto riguarda la CPU, la RAM e l'archiviazione. Questa funzionalità è utile per gli aggiornamenti hardware all'interno dello stesso cluster.

Per ulteriori informazioni, vedi [Espansione e contrazione della capacità per le istanze vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers).

### Aggiornamenti per le configurazioni della politica
{: #relnotes_v31-policy-config}

La password vCenter generata per le istanze primarie vCenter Server ha ora una lunghezza di 15 caratteri e ha le seguenti configurazioni di politica di password e blocco:

* La lunghezza minima per la politica della password vCenter è ora di 15 caratteri.
* La politica di blocco vCenter ora consente un massimo di 3 tentativi di accesso non riusciti.
* La politica di blocco vCenter ora consente un intervallo di tempo di 900 secondi tra i tentativi non riusciti.

La password NSX Manager generata per le istanze primarie vCenter Server ha ora una lunghezza di 15 caratteri. In precedenza, la password generata aveva una lunghezza di otto caratteri.

 Per ulteriori informazioni, vedi [Informazioni sulla conformità per le istanze vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_compl_info#vc_compl_info-default-policy-config).

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v31-services}

### Caveonix RiskForesight on IBM Cloud
{: #relnotes_v31-services-caveonix}

La release corrente installa Caveonix RiskForesight 2.2.1 su tutte le istanze di nuova distribuzione. Per ulteriori informazioni su Caveonix RiskForesight, vedi il [sito web di Caveonix](https://www.caveonix.com){:external}.

### Rinnovo automatico per le licenze HyTrust
{: #relnotes_v31-services-ht}

{{site.data.keyword.vmwaresolutions_short}} ora fornisce un supporto di rinnovo automatico per le licenze HyTrust che hanno la funzione Call Home abilitata. Questo supporto è fornito a partire da:

* HyTrust CloudControl 5.5.1 e versioni successive
* HyTrust DataControl 4.3.2 e versioni successive
* HyTrust KeyControl 4.3.2 e versioni successive

Devi completare la procedura per abilitare l'accesso a internet per le tue macchine virtuali VM (Virtual Machine) HyTrust per garantire il rinnovo automatico della tua licenza. Se non completi questa procedura, la tua licenza continua a scadere annualmente.
{:important}

Per ulteriori informazioni, vedi:

* [Abilitazione dell'accesso a internet per le VM HyTrust CloudControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc#managinghtcc-internet-access)
* [Abilitazione dell'accesso a internet per le VM HyTrust DataControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc#managinghtdc-internet-access)
* [Abilitazione dell'accesso a internet per la VM HyTrust KeyControl](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc#managinghtkc-internet-access)

### Veeam on IBM Cloud
{: #relnotes_v31-services-veeam}

Nella release corrente, Veeam Availability Suite 9.5 è installato su tutte le istanze di nuova distribuzione. Vengono inoltre apportati diversi aggiornamenti alle VSI Veeam e ai repository di configurazione Veeam. Per ulteriori informazioni, vedi [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations).

### Zerto on IBM Cloud
{: #relnotes_v31-services-zerto}

Per le nuove istanze distribuite nella V3.1 e successive, le installazioni di Zerto on {{site.data.keyword.cloud_notm}} richiedono un account {{site.data.keyword.cloud_notm}} fatturabile. Il costo della replica VM utilizza ora un piano fatturabile {{site.data.keyword.cloud_notm}} invece della fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}.

Per ordinare Zerto on {{site.data.keyword.cloud_notm}}, il tuo account {{site.data.keyword.cloud_notm}} deve soddisfare dei requisiti specifici. Se hai un'installazione di Zerto on {{site.data.keyword.cloud_notm}} esistente, puoi convertire in fatturabile il tuo tipo di fatturazione VM Zerto. Per ulteriori informazioni, vedi [Fatturazione per la replica Zerto](/docs/services/vmwaresolutions?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing).

## Documentazione nuova e aggiornata
{: #relnotes_v31-updated-doc}

* Gli eventi di gestione dell'istanza Activity Tracker e gli eventi per il servizio KMIP for VMware on IBM Cloud sono stati aggiornati. Per ulteriori informazioni, vedi [Eventi di Activity Tracker](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events).
* La documentazione di riferimento degli ID utente è stata aggiornata con gli ID utente utilizzati per l'installazione e la configurazione dei servizi da parte dell'automazione dei servizi {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi la sezione relativa all'*ID utente di servizio* in [ID utente IBM](/docs/services/vmwaresolutions?topic=vmware-solutions-audit_user_ids).
* È disponibile della documentazione di riferimento per la nuova API ``Retrieve the detailed network interface of a cluster``. Per ulteriori informazioni, vedi [Riferimento API](https://cloud.ibm.com/apidocs/vmware-solutions){:external}.
* I seguenti documenti tecnici sono nuovi nella sezione *Riferimento* della documentazione dell'utente:
  * [Gestione delle operazioni](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)
  * [Procedure operative successive](/docs/services/vmwaresolutions?topic=vmware-solutions-opsprocs-intro)

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v31-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:
* La pagina dei dettagli **Clusters** ora visualizza il tipo di archiviazione utilizzato dal cluster.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

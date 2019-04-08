---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Note sulla release per la V2.3
{: #relnotes_v23}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown
{: #relnotes_v23-spectre}

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware vCenter Server on IBM Cloud with Hybridity Bundle
{: #relnotes_v23-vcs-hybrid}

Questa release introduce l'offerta VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle. vCenter Server with Hybridity Bundle è un cloud privato ospitato che consente di estendere in modo semplice e rapido la tua infrastruttura in loco nel cloud. L'ambiente VMware è basato sulle licenze Software Defined Data Center VMware fornite da IBM e comprende il servizio VMware HCX on {{site.data.keyword.cloud_notm}} che connette in modo semplice e sicuro un ambiente vSphere 5.0+ in loco con i siti {{site.data.keyword.cloud_notm}} per un'ibridità dell'infrastruttura senza interruzioni e una reale mobilità dell'applicazione.

Il servizio HCX on {{site.data.keyword.cloud_notm}} è disponibile solo attraverso l'istanza vCenter Server with Hybridity Bundle. Puoi aggiornare la tua istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle dopo aver applicato l'aggiornamento del software vCenter Server V2.3 di base. Per ulteriori informazioni, vedi [Applicazione di aggiornamenti alle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates).

Per ulteriori informazioni su vCenter Server with Hybridity Bundle, vedi i seguenti argomenti:

* [Panoramica di vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Ordine di istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## Supporto per l'eliminazione di cluster nelle istanze vCenter Server e Cloud Foundation
{: #relnotes_v23-delete-cluster}

Puoi ora eliminare i cluster da un'istanza senza dover eliminare l'intera istanza. Per i cluster distribuiti nelle istanze della V2.2 o precedenti, devi aggiornare l'istanza alla V2.3 per poter eliminare i cluster che hai aggiunto all'istanza.

Per ulteriori informazioni, vedi [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances).

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v23-vcs}

Questa release applica i seguenti aggiornamenti e miglioramenti:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 con il livello di patch ESXi650-201803001 applicato)
*	VMware vCenter Server 6.5 Aggiornamento 1g

A partire dalla release della V2.3, per la distribuzione sono disponibili i seguenti nuovi modelli di CPU quando scegli l'impostazione Bare Metal **Personalizzato**:
* Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz
* Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## Aggiornamenti per le istanze VMware Cloud Foundation
{: #relnotes_v23-vcf}

Questa release applica i seguenti aggiornamenti e miglioramenti:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 con il livello di patch ESXi650-201803001 applicato)
*	VMware vCenter Server 6.5 Aggiornamento 1g
*	VMware NSX for vSphere 6.3.5

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v23-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v23-htcc}

Il servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive. Il servizio applica e controlla la conformità rispetto agli standard di sicurezza e fornisce il controllo degli accessi in base al ruolo (RBAC). Se combinato con HyTrust DataControl, il servizio può garantire che le VM (Virtual Machine) e i dati del carico di lavoro non lascino una particolare regione, cluster o server ESXi all'interno del data center {{site.data.keyword.cloud_notm}}.

Puoi ordinare le istanze con il servizio incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Componenti e considerazioni per HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [Gestione di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud
{: #relnotes_v23-htdc}

Il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive. Il servizio offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio può fornire la crittografia sia a livello di sistema operativo che a livello di dati, il che significa che è possibile crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.

Puoi ordinare le istanze con il servizio incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Componenti e considerazioni per HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [Gestione di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v23-spp}

La release corrente installa IBM Spectrum Protect&trade; Plus V10.1.1, come servizio di backup predefinito, su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di IBM Spectrum Protect Plus V10.1.1, vedi [Aggiornamenti di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentazione nuova e aggiornata
{: #relnotes_v23-new-docs}

È disponibile una nuova indicazione di developerWorks con istruzioni dettagliate su come aggiungere archiviazione a IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} dopo la distribuzione. Per ulteriori informazioni, vedi [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v23-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:
* **Coerenza**: l'interfaccia utente ora fornisce un aspetto coerente con gli altri servizi su {{site.data.keyword.cloud_notm}}.
* **Facilità di accesso**: puoi ora accedere alle offerte VMware direttamente dal **Catalogo** di {{site.data.keyword.cloud_notm}}.
* **Esperienza di ordinazione fluida e semplificata**: puoi ora completare l'ordine di un'istanza VMware e la distribuzione dei suoi servizi aggiuntivi in una singola interfaccia. Inoltre, il costo stimato viene calcolato e visualizzato immediatamente nella stessa interfaccia in modo da poter regolare la tua configurazione in base al tuo piano dei costi.
* L'opzione BYOL (Bring Your Own License) durante l'ordine di istanze o l'aggiunta di cluster non è disponibile per gli utenti Business Partner.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

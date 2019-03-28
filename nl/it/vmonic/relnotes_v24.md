---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Note sulla release per la V2.4
{: #relnotes_v24}

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown
{: #relnotes_v24-spectre}

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## NLS (National Language Support)
{: #relnotes_v24-nls}

A partire dalla release della V2.4, è disponibile il supporto della lingua nazionale (o NLS, National Language Support) per {{site.data.keyword.vmwaresolutions_short}}.
Tutte le funzioni della console, inclusa la documentazione per l'utente, sono disponibili in più lingue.

Oltre all'inglese, sono supportate le seguenti lingue:
* Tedesco
* Spagnolo
* Francese
* Italiano
* Giapponese
* Coreano
* Portoghese brasiliano
* Cinese semplificato
* Cinese tradizionale

## Supporto CPU Skylake Xeon
{: #relnotes_v24-skylake}

A partire dalla release della V2.4, i seguenti nuovi modelli di CPU Bare Metal Server sono disponibili per la distribuzione per le istanze e i cluster VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} e VMware vSphere on {{site.data.keyword.cloud_notm}}:

* Processore Dual Intel Skylake Xeon Silver 4110 / 16 core totali, 2,1 GHz
* Processore Dual Intel Skylake Xeon Gold 5120 / 28 core totali, 2,2 GHz
* Processore Dual Intel Skylake Xeon Gold 6140 / 36 core totali, 2,3 GHz

Per ulteriori informazioni, vedi la sezione *Impostazioni di Bare Metal Server* in [Ordine di nuovi cluster vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings).

## Aggiornamenti per le istanze VMware vCenter Server
{: #relnotes_v24-vcs}

### Miglioramento delle prestazioni di NFS (Network File System)
{: #relnotes_v24-nfs}

Il livello di prestazioni di 10 IOPS/GB, progettato per i tipi di carichi di lavoro più impegnativi, non è più limitato a specifici {{site.data.keyword.CloudDataCent_notm}}, ma è ora disponibile per tutti. Per ulteriori informazioni, vedi la sezione *Archiviazione* in [Panoramica di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#technical-specifications-for-vcenter-server-instances).

## Aggiornamenti per i servizi aggiuntivi
{: #relnotes_v24-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v24-spp}

La release corrente installa IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1, su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di IBM Spectrum Protect Plus V10.1.1 Patch 1, vedi [Aggiornamenti di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud
{: #relnotes_v24-hcx}

È ora disponibile una nuova opzione che ti consente di scegliere tra la rete pubblica e la rete privata per le interconnessioni HCX quando ordini questo servizio. Per ulteriori informazioni, vedi [Ordine di VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering).

## Documentazione nuova e aggiornata
{: #relnotes_v24-new-docs}

### Documentazione dell'architettura di riferimento
{: #relnotes_v24-ref-archi}

Il documento dell'architettura {{site.data.keyword.vmwaresolutions_short}} è ora disponibile nella sezione *Riferimento* della documentazione dell'utente. Per ulteriori informazioni, vedi [Panoramica della soluzione](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

### Documentazione dei servizi
{: #relnotes_v24-docs-services}

Le informazioni sui servizi sono ristrutturate e la navigazione è migliorata per individuare facilmente le informazioni rilevanti quando ordini i servizi.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Ordine di F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [Ordine di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_ordering)
* [Ordine di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)
* [Ordine di Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_ordering)
* [Ordine di Hytrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_ordering)
* [Ordine di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)

## Aggiornamenti e miglioramenti dell'interfaccia utente
{: #relnotes_v24-ui}

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* I riquadri di aggiunta cluster e di aggiunta servizio utilizzano ora un formato pagina, con una migliore organizzazione del layout, che ti consente di completare le attività in modo più efficiente.
* La funzionalità della pagina **Risorse** è stata migliorata con funzioni di ricerca, impaginazione e ordinamento. Questi miglioramenti ti consentono di individuare rapidamente le tue istanze.
* La pagina dei dettagli dell'istanza ora utilizza un menu di navigazione a sinistra, che ti consente di accedere alle informazioni dell'istanza in modo semplice e rapido.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

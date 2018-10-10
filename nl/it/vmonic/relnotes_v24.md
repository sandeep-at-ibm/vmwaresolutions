---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Note sulla release per la V2.4

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Per ulteriori informazioni, vedi [Risoluzione delle vulnerabilità Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## NLS (National Language Support)

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

**Nota**: i documenti dell'architettura di riferimento sono disponibili solo in inglese.

## Supporto CPU Skylake Xeon

A partire alla release V2.4, i seguenti nuovi modelli di CPU Bare Metal Server sono disponibili per la distribuzione per le istanze e i cluster di VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}, VMware vSphere on {{site.data.keyword.cloud_notm}} e VMware Federal on {{site.data.keyword.cloud_notm}}:

* Processore Dual Intel Skylake Xeon Silver 4110 / 16 core totali, 2,1 GHz
* Processore Dual Intel Skylake Xeon Gold 5120 / 28 core totali, 2,2 GHz
* Processore Dual Intel Skylake Xeon Gold 6140 / 36 core totali, 2,3 GHz

Per ulteriori informazioni, vedi la sezione *Impostazioni di Bare Metal Server* in:

* [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html#bare-metal-server-settings)
* [Ordine di nuovi cluster vSphere](../vsphere/vs_orderinginstances.html#bare-metal-server-settings)
* [Ordine di istanze VMware Federal](../vcenter/vc_fed_orderinginstance.html#bare-metal-server-settings)

## Aggiornamenti per le istanze VMware vCenter Server

### Miglioramento delle prestazioni di NFS (Network File System)

Il livello di prestazioni di 10 IOPS/GB, progettato per i tipi di carichi di lavoro più impegnativi, non è più limitato a specifici {{site.data.keyword.CloudDataCent_notm}}, ma è ora disponibile per tutti. Per ulteriori informazioni, vedi la sezione *Archiviazione* in [Panoramica di vCenter Server](../vcenter/vc_vcenterserveroverview.html#technical-specifications-for-vcenter-server-instances).

## Aggiornamenti per le istanze VMware Federal

### Nuova opzione di data center IBM Cloud

Puoi ora distribuire le istanze VMware Federal al {{site.data.keyword.CloudDataCent_notm}} DAL08 - Dallas, TX. Per ulteriori informazioni, vedi la sezione *Disponibilità dei data center IBM Cloud* in [Requisiti e pianificazione per le istanze VMware Federal](../vcenter/vc_fed_planning.html#ibm-cloud-data-center-availability).

## Aggiornamenti per i servizi aggiuntivi

### IBM Spectrum Protect Plus on IBM Cloud

La release corrente installa IBM Spectrum Protect&trade; Plus V10.1.1 Patch 1, su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di IBM Spectrum Protect Plus V10.1.1 Patch 1, vedi [Aggiornamenti di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

### VMware HCX on IBM Cloud

È ora disponibile una nuova opzione che ti consente di scegliere tra la rete pubblica e la rete privata per le interconnessioni HCX quando ordini questo servizio. Per ulteriori informazioni, vedi [Ordine di VMware HCX on {{site.data.keyword.cloud_notm}}](../services/hcx_ordering.html).

## Documentazione nuova e aggiornata

### Documentazione dell'architettura di riferimento

Il documento dell'architettura {{site.data.keyword.vmwaresolutions_short}} è ora disponibile nella sezione *Riferimento* della documentazione dell'utente. Il documento dell'architettura di riferimento è disponibile solo in inglese. Per ulteriori informazioni, vedi [Panoramica della soluzione](../archiref/solution/solution_overview.html).

### Documentazione dei servizi

Le informazioni sui servizi sono ristrutturate e la navigazione è migliorata per individuare facilmente le informazioni rilevanti quando ordini i servizi.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Ordine di F5 on {{site.data.keyword.cloud_notm}}](../services/f5_ordering.html)
* [Ordine di FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](../services/fsa_ordering.html)
* [Ordine di FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_ordering.html)
* [Ordine di Hytrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_ordering.html)
* [Ordine di Hytrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_ordering.html)
* [Ordine di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](../services/spp_ordering.html)
* [Ordine di KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_ordering.html)
* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](../services/veeam_ordering.html)
* [Ordine di Zerto on {{site.data.keyword.cloud_notm}}](../services/zerto_ordering.html)

## Aggiornamenti e miglioramenti dell'interfaccia utente

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* I riquadri di aggiunta cluster e di aggiunta servizio utilizzano ora un formato pagina, con una migliore organizzazione del layout, che ti consente di completare le attività in modo più efficiente.
* La funzionalità della pagina **Istanze distribuite** è stata migliorata con funzioni di ricerca, impaginazione e ordinamento. Questi miglioramenti ti consentono di individuare rapidamente le tue istanze.
* La pagina dei dettagli dell'istanza ora utilizza un menu di navigazione a sinistra, che ti consente di accedere alle informazioni dell'istanza in modo semplice e rapido.
* Sono disponibili vari messaggi di errore e miglioramenti delle descrizioni a comparsa per aiutarti a selezionare le impostazioni appropriate nell'interfaccia utente.

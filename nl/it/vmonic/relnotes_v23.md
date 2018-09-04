---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

# Note sulla release per la V2.3

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e ulteriori suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Per ulteriori informazioni, vedi [Risoluzione delle vulnerabilità Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## VMware vCenter Server on IBM Cloud with Hybridity Bundle

Questa release introduce l'offerta VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle. vCenter Server with Hybridity Bundle è un cloud privato ospitato che consente di estendere in modo semplice e rapido la tua infrastruttura in loco nel cloud. L'ambiente VMware è basato sulle licenze Software Defined Data Center VMware fornite da IBM e comprende il servizio VMware HCX on {{site.data.keyword.cloud_notm}} che connette in modo semplice e sicuro un ambiente vSphere 5.0+ in loco con i siti {{site.data.keyword.cloud_notm}} per un'ibridità dell'infrastruttura senza interruzioni e una reale mobilità dell'applicazione.

Il servizio HCX on {{site.data.keyword.cloud_notm}} è disponibile solo attraverso l'istanza vCenter Server with Hybridity Bundle. Puoi aggiornare la tua istanza vCenter Server esistente a un'istanza vCenter Server with Hybridity Bundle dopo aver applicato l'aggiornamento del software vCenter Server V2.3 di base. Per ulteriori informazioni, vedi [Applicazione di aggiornamenti alle istanze vCenter Server](../vcenter/vc_applyingupdates.html).

Per ulteriori informazioni su vCenter Server with Hybridity Bundle, vedi i seguenti argomenti:

* [Panoramica di vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_overview.html)
* [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_planning.html)
* [Ordine di istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_orderinginstance.html)

## Supporto per l'eliminazione di cluster nelle istanze vCenter Server e Cloud Foundation

Puoi ora eliminare i cluster da un'istanza senza dover eliminare l'intera istanza. Per i cluster distribuiti nelle istanze della V2.2 o precedenti, devi aggiornare l'istanza alla V2.3 per poter eliminare i cluster che hai aggiunto all'istanza.

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html#deleting-clusters-from-vcenter-server-instances)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze Cloud Foundation](../sddc/sd_addingviewingclusters.html#deleting-clusters-from-cloud-foundation-instances)

## Aggiornamenti per le istanze VMware vCenter Server

Questa release applica i seguenti aggiornamenti e miglioramenti:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 con il livello di patch ESXi650-201803001 applicato)
*	VMware vCenter Server 6.5 Aggiornamento 1g

### Miglioramenti per le istanze e i cluster di vCenter Server

A partire dalla release della V2.3, per la distribuzione sono disponibili i seguenti nuovi modelli di CPU quando scegli l'impostazione Bare Metal **Personalizzato**:
* Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz
* Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz

Per ulteriori informazioni, consulta i seguenti argomenti:

* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](../vcenter/vc_addingviewingclusters.html)

## Aggiornamenti per le istanze VMware Cloud Foundation

Questa release applica i seguenti aggiornamenti e miglioramenti:
*	VMware vSphere ESXi 6.5 U1g (ESXi 6.5u1 con il livello di patch ESXi650-201803001 applicato)
*	VMware vCenter Server 6.5 Aggiornamento 1g
*	VMware NSX for vSphere 6.3.5

## Aggiornamenti per le istanze VMware Federal

### Configurazione DNS per le istanze VMware Federal

Ora hai la possibilità di selezionare la distribuzione di una singola VSI (Virtual Server Instance) di Microsoft Windows Server per Microsoft Active Directory (AD) o due macchine virtuali Microsoft Windows ad alta disponibilità nel cluster di gestione. Per la V2.2, la singola VSI di Microsoft Windows per Microsoft AD veniva distribuita automaticamente per impostazione predefinita. La nuova opzione per selezionare due macchine virtuali Microsoft Windows offre maggiore privacy e la possibilità di eseguire il backup e il ripristino delle macchine virtuali mediante il servizio Veeam.

**Nota:** se configuri la tua istanza per utilizzare le due macchine virtuali Microsoft Windows, devi fornire due licenze di Microsoft Windows Server 2012 R2. Utilizza la licenza di Microsoft Windows Server 2012 R2 Standard Edition e/o la licenza di Microsoft Windows Server 2012 R2 Datacenter Edition. Hai 30 giorni per attivare le macchine virtuali.

Per ulteriori informazioni, vedi la sezione *Impostazioni dell'interfaccia di rete* in [Ordine di istanze VMware Federal](../vcenter/vc_fed_orderinginstance.html#network-interface-settings)​.

### Supporto per l'aggiunta ed eliminazione di cluster per le istanze VMware Federal

Puoi ora utilizzare i cluster per gestire i server ESXi nelle istanze VMware Federal distribuite nelle release della V2.3 e successive per una migliore gestione delle risorse e alta disponibilità. I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **cluster1** per impostazione predefinita. Puoi visualizzare i dettagli del cluster nella pagina di panoramica dell'istanza o aggiungere fino a un totale di 10 cluster a un'istanza. Quando espandi o contrai la capacità di un'istanza, puoi selezionare il cluster a cui aggiungere o da cui rimuovere i server ESXi.

Hai anche l'opzione per eliminare uno o più cluster dall'istanza senza eliminare l'intera istanza.

Per ulteriori informazioni, vedi [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze VMware Federal](../vcenter/fed_addviewdeleteclusters.html).

## Aggiornamenti per i servizi aggiuntivi

### HyTrust CloudControl on IBM Cloud

Il servizio HyTrust CloudControl on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive. Il servizio applica e controlla la conformità rispetto agli standard di sicurezza e fornisce il controllo degli accessi in base al ruolo (RBAC). Se combinato con HyTrust DataControl, il servizio può garantire che le macchine virtuali e i dati del carico di lavoro non lascino una particolare regione, cluster o server ESXi all'interno del data center {{site.data.keyword.cloud_notm}}.

Puoi ordinare le istanze con il servizio incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Componenti e considerazioni per HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/htcc_considerations.html)
* [Gestione di HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](../services/managinghtcc.html)

### HyTrust DataControl on IBM Cloud

Il servizio HyTrust DataControl on {{site.data.keyword.cloud_notm}} è ora disponibile per le istanze VMware Cloud Foundation e VMware vCenter Server che eseguono vSphere 6.5 e che sono distribuite o aggiornate alle release della V2.3 o successive. Il servizio offre una potente crittografia con gestione delle chiavi integrata per proteggere i carichi di lavoro per tutto il loro ciclo di vita. Il servizio può fornire la crittografia sia a livello di sistema operativo che a livello di dati, il che significa che è possibile crittografare e decrittografare qualsiasi directory, cartella o file all'interno di un carico di lavoro.

Puoi ordinare le istanze con il servizio incluso al momento dell'ordine della tua istanza o aggiungere questo servizio alle tue istanze esistenti in un secondo momento.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Componenti e considerazioni per HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/htdc_considerations.html)
* [Gestione di HyTrust DataControl on {{site.data.keyword.cloud_notm}}](../services/managinghtdc.html)

### IBM Spectrum Protect Plus on IBM Cloud

La release corrente installa IBM Spectrum Protect&trade; Plus V10.1.1, come servizio di backup predefinito, su tutte le istanze appena distribuite. Per ulteriori informazioni sulle nuove funzioni di IBM Spectrum Protect Plus V10.1.1, vedi [Aggiornamenti di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}.

## Documentazione nuova e aggiornata

È disponibile una nuova indicazione di developerWorks con istruzioni dettagliate su come aggiungere archiviazione a IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} dopo la distribuzione. Per ulteriori informazioni, vedi [Adding storage to IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/).

## Aggiornamenti e miglioramenti dell'interfaccia utente

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:
* **Coerenza**: l'interfaccia utente ora fornisce un aspetto coerente con gli altri servizi su {{site.data.keyword.cloud_notm}}.
* **Facilità di accesso**: puoi ora accedere alle offerte VMware direttamente dal **Catalogo** di {{site.data.keyword.cloud_notm}}.
* **Esperienza di ordinazione fluida e semplificata**: puoi ora completare l'ordine di un'istanza VMware e la distribuzione dei suoi servizi aggiuntivi in una singola interfaccia. Inoltre, il costo stimato viene calcolato e visualizzato immediatamente nella stessa interfaccia in modo da poter regolare la tua configurazione in base al tuo piano dei costi.
* L'opzione BYOL (Bring Your Own License) durante l'ordine di istanze o l'aggiunta di cluster non è disponibile per gli utenti Business Partner.
* Sono stati apportati vari miglioramenti ai messaggi di errore e alle descrizioni a comparsa per aiutarti a selezionare l'impostazione appropriata nell'interfaccia utente.

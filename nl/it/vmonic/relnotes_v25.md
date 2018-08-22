---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-31"

---

# Note sulla release per la V2.5

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e ulteriori suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Correzione Spectre e Meltdown

{{site.data.keyword.vmwaresolutions_short}} ha rilasciato patch da VMware in risposta alle vulnerabilità note come Spectre e Meltdown (CVE-2017-5753, CVE-2017-5715 e CVE-2017-5754).

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

Per ulteriori informazioni, vedi [Risoluzione delle vulnerabilità Spectre e Meltdown](../vmonic/trbl_fix_spectre.html).

## Aggiornamento dei componenti NSX

Questa release installa VMware NSX for vSphere 6.4.1 per le nuove distribuzioni di VMware vCenter Server on {{site.data.keyword.cloud_notm}}, VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle, NetApp ONTAP Select e VMware Federal on {{site.data.keyword.cloud_notm}}.

## Rimozione della configurazione di backup predefinita

{{site.data.keyword.vmwaresolutions_short}} offre due servizi aggiuntivi integrati per il backup: IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} e Veeam on {{site.data.keyword.cloud_notm}}. Questi servizi ti consentono di pianificare e fornire il ripristino sia della tua infrastruttura di gestione che del tuo carico di lavoro. Inoltre, IBM Resiliency Services offre servizi gestiti per i backup Veeam.

A partire dalla release della V2.5, i servizi IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} e Veeam on {{site.data.keyword.cloud_notm}}, quando distribuiti, non preconfigurano più il backup di alcuna VM. Questa modifica ti consente di garantire una corretta configurazione di tutti gli aspetti dei lavori di backup, tra cui pianificazione, periodo di conservazione, utilizzo della deduplicazione, monitoraggio e avvisi e gestione delle chiavi di crittografia. Inoltre, la VM IBM CloudDriver non è più configurata come file server persistente per i backup NSX.

Sei responsabile della configurazione, della gestione e del monitoraggio di tutti i componenti software, inclusi il backup e la disponibilità dei carichi di lavoro e dell'infrastruttura di gestione. Per ulteriori informazioni, vedi [Backup dei componenti](../archiref/solution/solution_backingup.html#backing-up-components).

**Nota:** questa modifica non influisce sulle istanze distribuite prima della V2.5 che già hanno installato il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} o Veeam on {{site.data.keyword.cloud_notm}}.

## Resilienza di IBM CloudDriver

Per le istanze distribuite o aggiornate alle release della V2.5 o successive, il componente IBM CloudDriver non è più configurato come macchina virtuale (VM) all'interno del cluster vSphere. Viene invece distribuito, secondo necessità, come VSI (Virtual Server Instance) dell'infrastruttura {{site.data.keyword.cloud_notm}} con il codice di {{site.data.keyword.cloud_notm}} for VMware più recente per operazioni come la distribuzione di nodi, cluster o servizi aggiuntivi. Inoltre, IBM CloudDriver viene modificato per comunicare con il piano di gestione di {{site.data.keyword.cloud_notm}} utilizzando la rete privata {{site.data.keyword.cloud_notm}} in modo che le regole del firewall del gateway dei servizi edge (ESG) NSX di gestione e le regole NAT (Network Address Translation) che permettono a IBM CloudDriver di comunicare in uscita sulla rete pubblica vengano rimosse.

Alcuni servizi aggiuntivi come F5 on {{site.data.keyword.cloud_notm}}, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} e Zerto on {{site.data.keyword.cloud_notm}} richiedono ancora l'accesso alla rete pubblica, quindi l'ESG NSX di gestione rimane distribuito in tutte le istanze.

## Gestione di utenti e accesso con abilitazione IAM

A partire dalla release della V2.5, {{site.data.keyword.vmwaresolutions_short}} è integrato con IBM Identity and Access Management (IAM) per fornire un approccio unificato per la gestione degli account e dell'accesso degli utenti all'interno del tuo account {{site.data.keyword.cloud_notm}}. Per cui:
* Puoi ora aggiungere più utenti al tuo account {{site.data.keyword.cloud_notm}} per la collaborazione e puoi gestirne l'accesso a servizi e risorse forniti nel tuo account assegnando loro differenti ruoli di accesso alla piattaforma.  
* Le istanze distribuite nelle release della V2.5 e successive vengono collegate direttamente all'account utente utilizzato durante l'ordine dell'istanza. 
* Le istanze distribuite nelle release della V2.4 e precedenti, possono essere migrate a un account {{site.data.keyword.cloud_notm}} specificato e gestite utilizzando IAM.

Per ulteriori informazioni, vedi:
* [Come invitare gli utenti ad accedere a servizi e risorse](../vmonic/iamuserinvite.html)
* [Gestione dell'accesso utente con IAM](../vmonic/iam.html)

## Modifiche ad account e gruppi di utenti per le istanze VMware vCenter Server e VMware Cloud Foundation

Il gruppo di utenti **ic4v-vCenter** è stato creato sul server Microsoft Active Directory e aggiunto alle autorizzazioni globali su vCenter Server e ai gruppi di utenti per NSX Manager. Il gruppo contiene l'account utente di **automazione** per le istanze vCenter Server e gli account utente specifici del servizio per le istanze vCenter Server e Cloud Foundation.

Non modificare le autorizzazioni globali del gruppo **ic4v-vCenter** nella pagina **Utenti e gruppi** del client web VMware vSphere. Ciò potrebbe influire sulle operazioni di gestione.

Per le istanze Cloud Foundation, utilizza l'ID utente host **customerroot** al posto dell'ID utente host **root**. Continua a utilizzare l'ID utente host **root** per le istanze vCenter Server.

Per ulteriori informazioni sugli account utente, vedi:

* [Considerazioni sulla modifica delle risorse vCenter Server](../vcenter/vcenter_chg_impact.html)
* [Considerazioni sulla modifica delle risorse Cloud Foundation](../sddc/cf_chg_impact.html)

## Aggiornamenti per i servizi aggiuntivi

### IBM Spectrum Protect Plus on IBM Cloud

A partire dalla release della V2.5, il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} viene distribuito come due VM separate in base alle procedure consigliate, con una VM che esegue il server Spectrum Protect Plus e l'altra VM che esegue il server vSnap e il proxy VADP.

Puoi ora ordinare fino a dieci archivi dati di backup, consentendo fino a 120 TB di archiviazione di backup. Le VM vSnap e VADP sono dimensionate in base alla dimensione dell'archiviazione di backup da te selezionata e alle informazioni contenute in [IBM Spectrum Protect Plus Blueprints](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints).

### KMIP for VMware on IBM Cloud

Un nuovo endpoint è ora disponibile in Germania per il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, vedi [Configurazione del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}](../services/kmip_ordering.html#kmip-for-vmware-on-ibm-cloud-service-configuration).

## Documentazione nuova e aggiornata

### Documentazione sull'archiviazione collegata

Il documento tecnico relativo all'architettura collegata per vCenter Server on IBM Cloud è ora disponibile nella sezione *Riferimento* della documentazione dell'utente. Questo documento di architettura di riferimento è disponibile solo in inglese. Per ulteriori informazioni, vedi [Attached storage for vCenter Server on IBM Cloud](../archiref/attached-storage/storage-benefits.html).

### Specifiche tecniche

Le specifiche tecniche per tutti i tipi di istanze e i tipi di servizio sono ora disponibili nella documentazione dell'utente e collegate dall'interfaccia utente. Per ulteriori informazioni, vedi l'argomento di panoramica appropriato per l'istanza e il servizio.

### Documentazione dei servizi

Le informazioni sui servizi sono state migliorate per identificare facilmente il supporto del servizio in base al numero di release in cui è stato reso disponibile.

Per ulteriori informazioni, vedi:

* [Servizi disponibili per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html#available-services-for-vcenter-server-instances)
* [Servizi disponibili per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html#available-services-for-vcenter-server-with-hybridity-bundle-instances)
* [Servizi disponibili per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html#available-services-for-cloud-foundation-instances)

## Aggiornamenti e miglioramenti dell'interfaccia utente

L'interfaccia utente è aggiornata e fornisce i seguenti miglioramenti:

* Se hai un account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) collegato al tuo account {{site.data.keyword.cloud_notm}}, puoi ora fare clic sul nuovo pulsante **Recupera** nella pagina **Impostazioni** per ottenere automaticamente il nome utente e la chiave API per il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer).
* È stata aggiunta una nuova scheda **Cronologia distribuzione** nel riquadro di navigazione a sinistra della pagina dei dettagli dell'istanza che ti consente di verificare la cronologia di distribuzione di un'istanza.
* Sono stati apportati vari miglioramenti ai messaggi di errore e alle descrizioni a comparsa per aiutarti a selezionare l'impostazione appropriata nell'interfaccia utente.

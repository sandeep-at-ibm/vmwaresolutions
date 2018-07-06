---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Gestione di IBM Spectrum Protect Plus on IBM Cloud

## Accesso alla console di gestione IBM Spectrum Protect Plus

Per gestire il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}}, devi accedere alla console di gestione IBM Spectrum Protect Plus completando la seguente procedura:
1. Utilizza la VPN dell'infrastruttura {{site.data.keyword.cloud_notm}} o un server jump per consentire l'accesso all'indirizzo IP della macchina virtuale (VM) IBM Spectrum Protect Plus. Puoi trovare l'indirizzo IP nella pagina dei dettagli del servizio di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} nella console {{site.data.keyword.vmwaresolutions_short}}.
2. Per accedere alla console di gestione IBM Spectrum Protect Plus, fai clic su **Visualizza console di IBM Spectrum Protect Plus** nella pagina dei dettagli del servizio di IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} ed esegui quindi l'accesso utilizzando le credenziali elencate nella stessa pagina dei dettagli del servizio.

## Applicazione degli aggiornamenti a IBM Spectrum Protect Plus on IBM Cloud 

Sei responsabile di mantenere IBM Spectrum Protect Plus aggiornato alla versione più recente. Puoi scaricare gli aggiornamenti richiesti dalla pagina di [Supporto di IBM Spectrum Protect Plus](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus).

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)

## Aggiornamento del sistema operativo della VM IBM Spectrum Protect Plus 

Per aggiornare il sistema operativo della VM IBM Spectrum Protect Plus, devi effettuare l'accesso come utente **root**. La password dell'utente **root** è la stessa password dalla pagina dei dettagli del servizio per IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. 

## Backup e ripristino dei componenti di gestione per le istanze in cui è installato IBM Spectrum Protect Plus on IBM Cloud

**Nota**: le seguenti informazioni si applicano alle installazioni di IBM Spectrum Protect Plus sulle istanze distribuite o aggiornate alla V2.3 o successive. Per le istanze della V2.2, questo servizio fornisce la protezione dei dati solo per le VM del carico di lavoro.

Il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} è preconfigurato con un lavoro di backup di gestione che viene eseguito automaticamente. Questo lavoro effettua il backup dei seguenti componenti di gestione con un massimo di sette punti di ripristino: 
* VMware vCenter Server
* PSC (Platform Services Controller)
* IBM CloudDriver
* **Solo per le istanze Cloud Foundation**: VMware SDDC Manager
* **Solo per le istanze vCenter Server con AD/DNS HA**: coppia ad alta disponibilità di AD/DNS

Se si verificano errori nei componenti di gestione, puoi aprire un ticket [contattando il supporto IBM](../vmonic/trbl_support.html) per richiedere un ripristino dei componenti a un backup precedente.

## Link correlati

* [Panoramica di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [Documentazione di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)

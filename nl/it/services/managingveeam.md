---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Gestione di Veeam on IBM Cloud

Una volta che il servizio è stato distribuito nella tua istanza, puoi accedere alla console Veeam utilizzando RDP per gestire il backup e il ripristino di tutte le macchine virtuali nel tuo ambiente, compreso il backup e il ripristino dei componenti di gestione. Puoi anche aggiornare il servizio scaricando e installando gli aggiornamenti di Veeam dal sito web Veeam.

Per le istanze che sono state distribuite in release precedenti alla V1.8, se vuoi utilizzare il servizio Veeam on {{site.data.keyword.cloud}}, devi sostituire la VSI Veeam esistente nelle istanze. Per ulteriori informazioni, vedi la sezione _Sostituzione della VSI Veeam delle istanze precedenti alla V1.8 con Veeam on IBM Cloud_ in questo argomento.

## Accesso alla console Veeam mediante RDP

Per gestire il servizio Veeam on {{site.data.keyword.cloud_notm}}, accedi alla console Veeam completando la seguente procedura: 
1. Utilizza l'RDP (Remote Desktop Protocol) per connetterti all'indirizzo IP di Windows. 
2. Accedi alla console di Windows utilizzando le credenziali di amministratore. 
3. Accedi alla console Veeam dalla console di Windows utilizzando le credenziali di amministratore. 

Puoi trovare l'indirizzo IP di Windows IP e le credenziali di amministratore nella pagina dei dettagli del servizio Veeam on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)

## Backup e ripristino dei componenti di gestione per le istanze in cui è installato Veeam on IBM Cloud

Il servizio Veeam on {{site.data.keyword.cloud_notm}} è preconfigurato con un lavoro di backup di gestione che viene eseguito automaticamente. Questo lavoro effettua il backup giornaliero dei componenti di gestione con un massimo di 14 punti di ripristino. 

Puoi anche eseguire manualmente il backup dei componenti di gestione utilizzando la console Veeam.

Per le istanze distribuite in o aggiornate alle release V1.8 o successive, le modifiche alla configurazione del tuo ambiente non vengono automaticamente sottoposte a backup. Pertanto, prima di modificare la configurazione del tuo ambiente, si consiglia di eseguire il backup dei componenti di gestione manualmente eseguendo il lavoro di backup di gestione preconfigurato nella console Veeam. Per ulteriori informazioni sul backup manuale, consulta le [istruzioni tecniche di Veeam](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

Quando si verificano errori nei componenti di gestione, puoi ripristinare tali componenti a un backup precedente utilizzando la console Veeam. Per ulteriori informazioni sul ripristino manuale, consulta le [istruzioni tecniche di Veeam]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Applicazione degli aggiornamenti a Veeam on IBM Cloud 

Sei responsabile di mantenere Veem aggiornato alla versione più recente. Per aggiornare Veeam all'ultima versione, scarica gli aggiornamenti dal sito web di Veeam, copia gli aggiornamenti nella VSI Veeam e quindi installali.

## Sostituzione della VSI Veeam delle istanze precedenti alla V1.8 con Veeam on IBM Cloud

Il servizio Veeam on {{site.data.keyword.cloud_notm}}, che può eseguire il backup sia dei componenti di gestione che dei carichi di lavoro, sostituisce la precedente VSI Veeam che era stata integrata in VMware Cloud Foundation e VMware vCenter Server nelle release precedenti alla V1.8 per il backup dei soli componenti di gestione.

A causa di questa modifica, la precedente scheda **Backup e ripristino** nella pagina dei dettagli dell'istanza è stata rimossa e i punti di backup per le istanze non sono più disponibili nella console {{site.data.keyword.vmwaresolutions_short}}, sebbene la VSI Veeam nelle istanze precedenti alla V1.8 continui a funzionare. 

Devi creare un ticket di supporto {{site.data.keyword.cloud_notm}} per ottenere assistenza con un ripristino. Inoltre, la licenza della VSI Veeam nelle istanze precedenti alla V1.8 è scaduta il 14 ottobre 2017. Pertanto, devi sostituire la VSI Veeam precedente con il nuovo servizio Veeam on {{site.data.keyword.cloud_notm}}.

Completa la seguente procedura:
1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra e seleziona l'istanza di destinazione.
2. Nella pagina dei dettagli dell'istanza, fai clic sulla scheda **Aggiorna e applica patch**. Assicurati di aver aggiornato l'istanza alla release della V1.8.
3. Fai clic sulla scheda **Servizi**.
4. Nella scheda **Aggiungi servizi**, installa il servizio Veeam on {{site.data.keyword.cloud_notm}}.

Una volta distribuito il nuovo servizio Veeam on {{site.data.keyword.cloud_notm}} e terminato un backup dei tuoi componenti di gestione, puoi rimuovere la VSI Veeam esistente dal tuo account creando un ticket di supporto {{site.data.keyword.cloud_notm}}. Il supporto IBM identificherà ed eliminerà la VSI Veeam e archiviazione esistenti.

## Link correlati

* [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](veeam_considerations.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)
* [Domande frequenti](../vmonic/faq.html)
* [Sito web Veeam.com](https://www.veeam.com/)
* [Documentazione tecnica di Veeam](https://www.veeam.com/documentation-guides-datasheets.html)

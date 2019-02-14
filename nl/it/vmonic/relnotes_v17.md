---

copyright:

  years:  2016, 2019

lastupdated: "2017-07-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Note sulla release per la V1.7

Questa release include nuove funzioni, aggiornamenti dei componenti, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Aggiornamenti per le istanze VMware Cloud Foundation

Questo aggiornamento applica i seguenti potenziamenti e miglioramenti:
* VMware SDDC Manager 2.3
* VMware NSX per vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* Miglioramenti della stabilità per il componente IBM CloudDriver
* La modalità EVC (basata sul processore Intel “Haswell” 2690-V3) è abilitata sulle distribuzioni VMware preesistenti che si trovano sui server della V3 al momento dell'aggiornamento.

  La modalità EVC non è abilitata per le distribuzioni nuove o esistenti sui server della V4.
  {:note}

* Le distribuzioni di VMware Cloud Foundation che sono state distribuite prima del 22 maggio e che pertanto utilizzano server della V3 ordineranno adesso i server della V4 durante l'aggiunta di un nuovo nodo all'istanza. Questi server hanno 256 GB di memoria; se ti servono 512 GB di memoria, dopo aver aggiunto i server, apri un ticket di supporto per richiedere l'aggiornamento del server a 512 GB di memoria. Per ulteriori informazioni su come contattare il supporto IBM, vedi [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html).

Per ulteriori informazioni sui componenti, vedi [Specifiche tecniche per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances).

### Requisiti del processo di aggiornamento

A seconda della complessità della distribuzione della tua istanza Cloud Foundation e se disponi di una configurazione multisito, il processo di aggiornamento potrebbe richiedere una sequenza di passi che devi completare come visualizzato nella scheda **Aggiorna e applica patch** sulla console. Per ulteriori informazioni, vedi [Applicazione di aggiornamenti alle istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html#applying-updates-to-cloud-foundation-instances).

## Aggiornamenti per le istanze VMware vCenter Server

### Supporto cluster

A partire dalla release della V1.7, puoi utilizzare i cluster per gestire i server ESXi nelle istanze vCenter Server per una migliore gestione delle risorse e alta disponibilità. I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **cluster1** per impostazione predefinita. Puoi visualizzare i dettagli del cluster o aggiungere fino a un totale di cinque cluster a un'istanza dalla scheda **Infrastruttura** appena introdotta nella pagina dei dettagli dell'istanza. Quando espandi o contrai la capacità di un'istanza, puoi selezionare il cluster a cui aggiungere o da cui rimuovere i server ESXi. Per ulteriori informazioni, vedi [Aggiunta e visualizzazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html).

### Miglioramenti alla distribuzione del ripristino di emergenza Zerto

La distribuzione del ripristino di emergenza Zerto è ora automatizzata anziché gestita tramite un ticket di supporto. Tutti i componenti di Zerto, come una sottorete portatile privata, una VSI (Virtual Service Instance) di Windows e i costi di licenza Zerto vengono elencati sotto il costo stimato, quindi puoi esaminarli prima di effettuare l'ordine. Per ulteriori informazioni, vedi [Processo di distribuzione del ripristino di emergenza Zerto](/docs/services/vmwaresolutions/services/addingzertodr.html).

### Funzionalità di aggiornamento delle licenze NSX

Puoi aggiornare l'edizione della licenza NSX dalla scheda **Riepilogo** della tua istanza vCenter Server. L'aggiornamento della licenza sostituisce tutte le licenze NSX SoftLayer esistenti nel tuo account con la nuova licenza. Per ulteriori informazioni, vedi [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_viewinginstances.html).

## Miglioramenti dell'usabilità

Sono stati apportati miglioramenti in tutta l'interfaccia utente:
* La scheda **Proprietà** nella pagina dei dettagli dell'istanza Cloud Foundation è stata rinominata in **Riepilogo**. In questa scheda puoi ora visualizzare i dettagli dell'istanza, le informazioni di accesso dei componenti relativi all'istanza e la cronologia di distribuzione dell'istanza.
* Viene introdotta una nuova scheda **Infrastruttura** nella pagina dei dettagli dell'istanza Cloud Foundation. In questa scheda, puoi visualizzare, aggiungere o rimuovere i server ESXi.
* La documentazione di {{site.data.keyword.vmwaresolutions_short}} ha un nuovo formato ed è ora completamente integrata nel catalogo Bluemix, insieme alle documentazioni Bluemix. Puoi accedere alla documentazione in uno dei seguenti modi:
  * Da {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Documenti** alla sinistra del banner.
  * Dal catalogo della documentazione Bluemix, scorri verso il basso fino alla sezione **Calcolo e servizi** e fai clic su **{{site.data.keyword.vmwaresolutions_short}}**.

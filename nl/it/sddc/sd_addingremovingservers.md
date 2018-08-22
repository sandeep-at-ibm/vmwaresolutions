---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Espansione e contrazione della capacità per le istanze Cloud Foundation

Puoi espandere o contrarre la capacità della tua istanza VMware Cloud Foundation in base alle tue esigenze aziendali, aggiungendo o rimuovendo i server ESXi.

Un'istanza Cloud Foundation può avere fino a 5 cluster, uno dei quali è il predefinito. Ogni cluster iniziale può avere fino a 51 server ESXi e i cluster aggiuntivi possono averne un massimo di 59.

## Prima di iniziare

* Non aggiungere o rimuovere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web VMware vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* La piattaforma di base che hai ordinato ha 4 server ESXi per impostazione predefinita. Puoi espandere la piattaforma a un massimo di 32 server ESXi. Tuttavia, il numero di {{site.data.keyword.baremetal_short}} che puoi aggiungere alla volta è il seguente:
   * Per le configurazioni **Small** e **Large**, puoi aggiungere da 1 a 10 server ESXi alla volta.
   * Per la configurazione **Personalizzato**, puoi aggiungere da 1 a 20 server ESXi alla volta.
* Puoi rimuovere i server ESXi che hai aggiunto, ma non puoi rimuovere i server ESXi predefiniti.
* Prima di rimuovere i server ESXi con il servizio F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installato, devi migrare le VM di F5 BIG-IP e FortiGate su un server ESXi diverso rispetto a quello che ospita attualmente le VM.
* Prima di rimuovere i server ESXi con il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} installato, assicurati che non vi siano operazioni di backup o ripristino attive (non riuscite o in corso), poiché queste operazioni attive potrebbero impedire la rimozione dei server ESXi.

## Procedura

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza per la quale vuoi espandere o contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere o da cui vuoi rimuovere i server ESXi.
5. Per aggiungere i server ESXi, completa la seguente procedura:
   1. Nella sezione **Server ESXi**, fai clic su **Aggiungi**.
   2. Nella finestra **Aggiungi server**, immetti il numero di server che vuoi aggiungere, esamina il costo stimato e fai quindi clic su **Aggiungi**.
6. Per rimuovere i server ESXi, seleziona i server che vuoi rimuovere nella sezione **Server ESXi** e fai quindi clic su **Rimuovi**.

## Risultati

Dopo l'avvio dell'operazione di aggiunta o rimozione, si potrebbe verificare un leggero ritardo nel passaggio dello stato dell'istanza da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare ulteriori modifiche all'istanza.

All'aggiunta o rimozione dei tuoi server ESXi, riceverai una notifica tramite e-mail. Quando rimuovi i server, nota che i server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

**Attenzione**: per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}.

Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

### Link correlati

* [Distinta base di Cloud Foundation](sd_bom.html)
* [Requisiti e pianificazione per le istanze Cloud Foundation](sd_planning.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze Cloud Foundation](sd_addingviewingclusters.html)
* [Metti un host in modalità di manutenzione](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

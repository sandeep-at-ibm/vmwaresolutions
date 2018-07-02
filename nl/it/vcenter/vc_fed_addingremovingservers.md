---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Espansione e contrazione della capacità per le istanze VMware Federal

Puoi espandere o contrarre la capacità della tua istanza VMware Federal in base alle tue esigenze aziendali, aggiungendo o rimuovendo i server ESXi.

Se il tuo cluster primario ha vSAN come archiviazione, l'aggiunta di uno o più server ESXi dopo la distribuzione può aumentare la capacità di archiviazione del cluster.

**Nota:** questa funzione è disponibile solo per le istanze VMware Federal che non sono state protette.

## Prima di iniziare

* Non aggiungere o rimuovere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* Un'istanza VMware Federal con l'archiviazione NFS deve avere almeno 2 server ESXi. Puoi espandere il cluster predefinito per avere fino a 51 server ESXi. Ciascuno dei cluster non predefiniti può essere espanso per avere fino a 59 server ESXi.
* Un'istanza VMware Federal con l'archiviazione vSAN deve avere almeno 4 server ESXi.
*  Quando rimuovi i server ESXi, i server vengono messi in modalità di manutenzione e, successivamente, tutte le macchine virtuali (VM) in esecuzione sui server vengono migrate prima di essere rimosse da vCenter Server. Per il massimo controllo sulla ricollocazione delle VM, si consiglia di mettere in modalità di manutenzione i server ESXi da rimuovere e di migrare manualmente le VM in esecuzione sui server utilizzando il client web VMware vSphere. Dopo di che, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_full}}.

## Procedura

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere o contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere o da cui vuoi rimuovere i server ESXi.
5. Per aggiungere i server ESXi, completa la seguente procedura:
   1. Nella tabella **Server ESXi**, fai clic su **Aggiungi**.
   2. Nella finestra **Aggiungi server**, seleziona il numero di server che vuoi aggiungere, fai clic sul link del prezzo per esaminare il costo stimato e fai quindi clic su **Aggiungi**.
6. Per rimuovere i server ESXi, seleziona i server che vuoi rimuovere nella tabella **Server ESXi** e fai quindi clic su **Rimuovi**.

## Risultati

Dopo l'avvio dell'operazione di aggiunta o rimozione, si potrebbe verificare un leggero ritardo nel passaggio dello stato dell'istanza da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare ulteriori modifiche all'istanza.

Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiungere o rimuovere i server ESXi è in fase di elaborazione. Lo stato del cluster associato ai server ESXi viene modificato in **In fase di modifica**. Quando rimuovi i server, nota che i server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

**Attenzione:** per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}.

Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

## Link correlati

* [Requisiti e pianificazione per le istanze VMware Federal](vc_fed_planning.html)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze VMware Federal](fed_addviewdeleteclusters.html)
* [Metti un host in modalità di manutenzione](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

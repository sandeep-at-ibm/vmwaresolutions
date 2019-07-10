---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers}

Puoi espandere o contrarre la capacità della tua istanza VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle in base alle tue esigenze aziendali, aggiungendo o rimuovendo i server ESXi.

A partire dalla release V3.1, puoi aggiungere dei nuovi server ESXi a un cluster esistente selezionando una configurazione esistente oppure una configurazione alternativa rispetto agli host esistenti nel cluster. Le configurazioni esistenti sono disponibili per la selezione istantanea quando ordini il tuo nuovo server. Per evitare problemi di prestazioni o di stabilità, ti consigliamo di fare in modo che i cluster utilizzino la stessa configurazione, oppure una simile, per quanto riguarda la CPU, la RAM e l'archiviazione. Questa funzionalità è utile per gli aggiornamenti hardware all'interno dello stesso cluster. Un cluster può avere solo un singolo tipo di archiviazione.

A partire dalla release V2.9, puoi aggiungere dei nuovi server ESXi a un cluster mentre il cluster è in modalità di manutenzione. Inoltre, puoi aggiungere o rimuovere simultaneamente i server ESXi in più cluster. Sono disponibili le seguenti operazioni simultanee:

* Aggiungi host a un cluster e aggiungi host a cluster aggiuntivi.
* Rimuovi host da un cluster e rimuovi host da cluster aggiuntivi.
* Aggiungi host a un cluster e rimuovi host da cluster aggiuntivi.
* Rimuovi host da un cluster e aggiungi host a cluster aggiuntivi.

Poiché il tuo cluster iniziale ha vSAN come archiviazione, l'aggiunta di uno o più server ESXi dopo la distribuzione può aumentare la capacità di archiviazione del cluster.

## Aggiunta di server ESXi alle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers-adding}

### Prima di aggiungere i server ESXi
{: #vc_hybrid_addingremovingservers-adding-prereq}

* Quando possibile, aggiungi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_full}}, poiché le modifiche che apporti al client web VMware vSphere non sono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. Pertanto, aggiungi i server ESXi a vCenter Server solo per i server ESXi in loco o per i server ESXi che non puoi gestire o che non gestirai nella console {{site.data.keyword.vmwaresolutions_short}}.
* L'archiviazione vSAN richiede almeno 4 server ESXi.

## Procedura per aggiungere i server ESXi
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere i server ESXi.
5. Nella tabella **Server ESXi**, fai clic su **Aggiungi**.
6. Nella finestra **Aggiungi server**, immetti il numero di server che desideri aggiungere.
7. Facoltativamente, seleziona la casella di spunta per aggiungere i server durante la modalità di manutenzione. La casella di spunta è selezionata per impostazione predefinita.

   Quando esegui il provisioning del nuovo server, le VM (Virtual Machine) vengono immediatamente migrate ai nuovi server se non selezioni la casella di spunta **Modalità di manutenzione**. Non ricevi un messaggio di conferma prima che la migrazione inizi.
   {:important}

8. Completa la configurazione Bare Metal.
   * Seleziona una configurazione dagli host esistenti nel cluster.
   * Seleziona una nuova configurazione {{site.data.keyword.baremetal_short_sing}} e specifica il modello di CPU e la dimensione della RAM.
9. Completa la configurazione di archiviazione. Specifica i tipi di disco per i dischi di capacità e cache, il numero di dischi e l'edizione della licenza vSAN. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
10. Esamina il costo stimato e fai clic su **Aggiungi**.

  Puoi anche aggiungere le risorse di cui è stato eseguito il provisioning allo strumento di stima {{site.data.keyword.cloud_notm}} facendo clic su **Aggiungi alla stima**. Ciò è utile se desideri stimare il costo delle risorse {{site.data.keyword.vmwaresolutions_short}} selezionate insieme ad altre risorse {{site.data.keyword.cloud_notm}} di cui potresti prendere in considerazione l'acquisto.

### Risultati dopo l'aggiunta dei server ESXi
{: #vc_hybrid_addingremovingservers-adding-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiunta dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi diventa **In fase di modifica**.
3. Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

Se stai aggiungendo dei server ESXi durante la modalità di manutenzione, le VM non vengono migrate ai nuovi server finché non rimuovi il cluster dalla modalità di manutenzione.   
{:important}

## Rimozione di server ESXi dalle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservers-removing}

### Prima di rimuovere i server ESXi
{: #vc_hybrid_addingremovingservers-removing-prereq}

* Quando possibile, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_full}}, poiché le modifiche che apporti al client web VMware vSphere non sono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. Pertanto, rimuovi i server ESXi da vCenter Server solo per i server ESXi in loco o per i server ESXi che non puoi gestire o che non gestirai nella console {{site.data.keyword.vmwaresolutions_short}}.
* L'archiviazione vSAN richiede almeno 4 server ESXi.
* Prima di rimuovere i server ESXi con il servizio F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installato, devi migrare le VM di F5 BIG-IP e FortiGate in un server ESXi diverso rispetto a quello che ospita le VM.
* Prima di rimuovere i server ESXi con il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} installato, assicurati che non vi siano operazioni di backup o ripristino attive (non riuscite o in corso), poiché queste operazioni attive potrebbero impedire la rimozione dei server ESXi.
* Quando rimuovi i server ESXi, i server vengono messi in modalità di manutenzione e, successivamente, tutte le VM (Virtual Machine) in esecuzione sui server vengono migrate prima di essere rimosse da vCenter Server. Per il massimo controllo sulla ricollocazione delle VM, si consiglia di mettere in modalità di manutenzione i server ESXi da rimuovere e di migrare manualmente le VM in esecuzione sui server utilizzando il client web VMware vSphere. Dopo di che, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_short}}.

## Procedura per rimuovere i server ESXi
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere i server ESXi.
5. Nella tabella **Server ESXi**, seleziona i server che vuoi rimuovere e fai clic su **Rimuovi**.

### Risultati dopo la rimozione dei server ESXi
{: #vc_hybrid_addingremovingservers-removing-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare ulteriori modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di rimozione dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi cambia in **In fase di modifica**.
3. I server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
   {:note}

## Link correlati
{: #vc_hybrid_addingremovingservers-related}

* [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisiti e pianificazione per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Metti un host in modalità di manutenzione](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/s/article/1003212){:new_window}

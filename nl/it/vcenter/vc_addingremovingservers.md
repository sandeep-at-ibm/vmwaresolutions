---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: vCenter Server add host, add server vCenter Server, remove host vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Espansione e contrazione della capacità per le istanze vCenter Server
{: #vc_addingremovingservers}

Puoi espandere o contrarre la capacità della tua istanza VMware vCenter Server in base alle tue esigenze aziendali, aggiungendo o rimuovendo i server ESXi o l'archiviazione NFS (network file system).

* A partire dalla release V3.1, puoi aggiungere dei nuovi server ESXi a un cluster esistente selezionando una configurazione esistente oppure una configurazione alternativa rispetto agli host esistenti nel cluster. Le configurazioni esistenti sono disponibili per la selezione istantanea quando ordini il tuo nuovo server. Per evitare problemi di prestazioni o di stabilità, ti consigliamo di fare in modo che i cluster utilizzino la stessa configurazione, oppure una simile, per quanto riguarda la CPU, la RAM e l'archiviazione. Questa funzionalità è utile per gli aggiornamenti hardware all'interno dello stesso cluster. Un cluster può avere solo un singolo tipo di archiviazione.
* A partire dalla release V3.0, puoi aggiungere o rimuovere simultaneamente l'archiviazione NFS e i server ESXi sui cluster nello stato **Ready to Use** (Pronto per l'utilizzo). Ad esempio, puoi aggiungere o rimuovere un server ESXi in un cluster e aggiungere o rimuovere l'archiviazione NFS in un altro cluster.
* A partire dalla release V2.9, puoi aggiungere dei nuovi server ESXi a un cluster mentre i server sono in modalità di manutenzione. Inoltre, puoi aggiungere o rimuovere simultaneamente i server ESXi in più cluster.

**Note**:
* Se il tuo cluster iniziale ha vSAN come archiviazione, l'aggiunta di uno o più server ESXi dopo la distribuzione può aumentare la capacità di archiviazione del cluster.
* Puoi aggiungere o rimuovere condivisioni di archiviazione NFS in un cluster vCenter Server NFS o vSAN esistente.

## Aggiunta di server ESXi alle istanze vCenter Server
{: #vc_addingremovingservers-adding}

### Prima di aggiungere i server ESXi
{: #vc_addingremovingservers-adding-prereq}

* Quando possibile, aggiungi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_full}}, poiché le modifiche che apporti al client web VMware vSphere non sono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. Pertanto, aggiungi i server ESXi a vCenter Server solo per i server ESXi in loco o per i server ESXi che non puoi gestire o che non gestirai nella console {{site.data.keyword.vmwaresolutions_short}}.
* Un'istanza vCenter Server con l'archiviazione NFS deve avere almeno 2 server ESXi. Per le istanze distribuite nella V2.1 o successive, puoi espandere il cluster predefinito per avere fino a 51 server ESXi. Ciascuno dei cluster non predefiniti può essere espanso per avere fino a 59 server ESXi.
* Un'istanza vCenter Server con l'archiviazione vSAN deve avere almeno 4 server ESXi.
* Per le istanze vCenter Server distribuite nella V2.0 o precedenti, puoi espandere ciascun cluster per avere fino a 32 server ESXi.
* Puoi aggiungere da 1 a 20 server ESXi alla volta. Per ulteriori informazioni sul numero minimo di server ESXi, vedi [Un'istanza vCenter Server a due nodi è altamente disponibile?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)

### Procedura per aggiungere i server ESXi
{: #vc_addingremovingservers-adding-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere i server ESXi.
5. Nella sezione **Server ESXi**, fai clic su **Aggiungi**.
6. Nella finestra **Aggiungi server**, seleziona il numero di server che desideri aggiungere.
7. Facoltativamente, seleziona la casella di spunta per aggiungere i server durante la modalità di manutenzione. La casella di spunta è selezionata per impostazione predefinita.

   Quando esegui il provisioning del nuovo server, le VM (Virtual Machine) vengono immediatamente migrate ai nuovi server se non selezioni la casella di spunta **Modalità di manutenzione**. Non ricevi un messaggio di conferma prima che la migrazione inizi.
   {:important}

8. Completa la configurazione Bare Metal.
   * Seleziona una configurazione dagli host esistenti nel cluster.
   * Seleziona una nuova configurazione {{site.data.keyword.baremetal_short_sing}}.
      * Per **Skylake** o **Broadwell**, specifica il **Modello CPU**, la quantità di **RAM** e il **Numero di {{site.data.keyword.baremetal_short}}**.     
      * Per **Certificato SAP**, specifica il **Modello CPU e RAM** e il **Numero di {{site.data.keyword.baremetal_short}}**.
9. Completa la configurazione di archiviazione. Specifica i tipi di disco per i dischi di capacità e cache, il numero di dischi e l'edizione della licenza vSAN. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
10. Esamina il costo stimato e fai clic su **Aggiungi**.

  Puoi anche aggiungere le risorse di cui è stato eseguito il provisioning allo strumento di stima {{site.data.keyword.cloud_notm}} facendo clic su **Aggiungi alla stima**. Ciò è utile se desideri stimare il costo delle risorse {{site.data.keyword.vmwaresolutions_short}} selezionate insieme ad altre risorse {{site.data.keyword.cloud_notm}} di cui potresti prendere in considerazione l'acquisto.

### Risultati dopo l'aggiunta dei server ESXi
{: #vc_addingremovingservers-adding-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiunta dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi diventa **In fase di modifica**.
3. Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.
4. Devi utilizzare la console ZVM (Zerto Virtual Manager) e l'indirizzo IP VRA (Virtual Replication Appliance) Zerto precompilato per distribuire manualmente la virtual machine VRA nelle seguenti circostanze:
   * Se aggiungi dei server ESXi a un cluster predefinito mentre i server sono in modalità di manutenzione e Zerto for {{site.data.keyword.cloud_notm}} è installato.
   * Se aggiungi Zerto for {{site.data.keyword.cloud_notm}} a un'istanza vCenter Server che ha un server ESXi che è in modalità di manutenzione.

Se stai aggiungendo dei server ESXi durante la modalità di migrazione, le VM non vengono migrate ai nuovi server finché non rimuovi la modalità di manutenzione.   
{:important}

## Rimozione di server ESXi dalle istanze vCenter Server
{: #vc_addingremovingservers-removing}

### Prima di rimuovere i server ESXi
{: #vc_addingremovingservers-removing-prereq}

* Quando possibile, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_full}}, poiché le modifiche che apporti al client web VMware vSphere non sono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. Pertanto, rimuovi i server ESXi da vCenter Server solo per i server ESXi in loco o per i server ESXi che non puoi gestire o che non gestirai nella console {{site.data.keyword.vmwaresolutions_short}}.
* Un'istanza vCenter Server con l'archiviazione NFS deve avere almeno 2 server ESXi e un'istanza vCenter Server con l'archiviazione vSAN deve avere almeno 4 server ESXi.
* Prima di rimuovere i server ESXi con il servizio F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installato, devi migrare le VM di F5 BIG-IP e FortiGate in un server ESXi diverso rispetto a quello che ospita le VM.
* Prima di rimuovere i server ESXi con il servizio IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} installato, assicurati che non vi siano operazioni di backup o ripristino attive (non riuscite o in corso), poiché queste operazioni attive potrebbero impedire la rimozione dei server ESXi.
* Quando rimuovi i server ESXi, i server vengono messi in modalità di manutenzione e, successivamente, tutte le VM in esecuzione sui server vengono migrate prima di essere rimosse da vCenter Server. Per il massimo controllo sulla ricollocazione delle VM, si consiglia di mettere in modalità di manutenzione i server ESXi da rimuovere e di migrare manualmente le VM in esecuzione sui server utilizzando il client web VMware vSphere. Dopo di che, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_short}}.

### Procedura per rimuovere i server ESXi
{: #vc_addingremovingservers-removing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere i server ESXi.
5. Nella sezione **Server ESXi**, seleziona i server che vuoi rimuovere e fai clic su **Rimuovi**.

### Risultati dopo la rimozione dei server ESXi
{: #vc_addingremovingservers-removing-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di rimozione dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi diventa **In fase di modifica**.
3. I server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
   {:note}

## Aggiunta dell'archiviazione NFS alle istanze vCenter Server
{: #section-adding-nfs-storage-to-vcenter-server-instances}

### Prima di aggiungere l'archiviazione NFS
{: #vc_addingremovingservers-adding-nfs-storage-prereq}

Non aggiungere l'archiviazione NFS dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. IBM non gestirà le condivisioni file NFS che aggiungi manualmente a un'istanza.

### Procedura per aggiungere l'archiviazione NFS
{: #vc_addingremovingservers-adding-nfs-storage-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere l'archiviazione NFS.
5. Nella sezione **Storage**, fai clic su **Aggiungi**.
6. Nella finestra **Storage**, completa la configurazione di archiviazione.
   * Se vuoi aggiungere e configurare le stesse impostazioni in tutte le condivisioni file, specifica il **Numero di condivisioni**, le **Prestazioni** e la **Dimensione (GB)**.
   * Se vuoi aggiungere e configurare singolarmente le condivisioni file, seleziona **Configura condivisioni singolarmente**, quindi fai clic sull'icona **+** accanto all'etichetta **Aggiungi storage condiviso** e seleziona le **Prestazioni** e la **Dimensione (GB)** per ogni singola condivisione file. Devi selezionare almeno una condivisione file.
7. Esamina il costo stimato e fai clic su **Aggiungi archiviazione NFS**.

  Puoi anche aggiungere le risorse di cui è stato eseguito il provisioning allo strumento di stima {{site.data.keyword.cloud_notm}} facendo clic su **Aggiungi alla stima**. Ciò è utile se desideri stimare il costo delle risorse {{site.data.keyword.vmwaresolutions_short}} selezionate insieme ad altre risorse {{site.data.keyword.cloud_notm}} di cui potresti prendere in considerazione l'acquisto.

### Risultati dopo l'aggiunta dell'archiviazione NFS
{: #vc_addingremovingservers-adding-nfs-storage-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiunta dell'archiviazione NFS è in fase di elaborazione. Sulla console, lo stato del cluster associato all'archiviazione NFS diventa **In fase di modifica**.
3. Se non vedi la nuova archiviazione NFS aggiunta all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

## Rimozione dell'archiviazione NFS dalle istanze vCenter Server
{: #vc_addingremovingservers-removing-nfs-storage}

### Prima di rimuovere l'archiviazione NFS
{: #vc_addingremovingservers-removing-nfs-storage-prereq}

* Non rimuovere l'archiviazione NFS dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* Prima di rimuovere l'archiviazione NFS, assicurati di aver rimosso tutte le VM che risiedono sull'archiviazione.
* Assicurati che le condivisioni che pensi di rimuovere siano associate all'istanza vCenter Server corretta.
* Lo stato del cluster deve essere **Pronto per l'utilizzo**.

### Procedura per rimuovere l'archiviazione NFS
{: #vc_addingremovingservers-removing-nfs-storage-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere l'archiviazione NFS.
5. Nella sezione **Storage**, seleziona la condivisione di archiviazione che vuoi rimuovere e fai clic su **Elimina**.
6. Fai clic su **Rimuovi** nella finestra **Rimuovi storage**.

### Risultati dopo la rimozione dell'archiviazione NFS
{: #vc_addingremovingservers-removing-nfs-storage-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di rimozione dell'archiviazione NFS è in fase di elaborazione. Sulla console, lo stato del cluster associato all'archiviazione NFS diventa **In fase di modifica**.
3. L'archiviazione NFS viene completamente recuperata dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per l'archiviazione NFS rimossa ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
   {:note}

## Link correlati
{: #vc_addingremovingservers-related}

* [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [Metti un host in modalità di manutenzione](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/s/article/1003212){:external}

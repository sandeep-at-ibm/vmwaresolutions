---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Espansione e contrazione della capacità per le istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers}

Puoi espandere o contrarre la capacità della tua istanza VMware vCenter Server with NSX-T in base alle tue esigenze aziendali, aggiungendo o rimuovendo server ESXi o archiviazione NFS (network file system).

Puoi aggiungere dei nuovi server ESXi a un cluster mentre il cluster è in modalità di manutenzione. Inoltre, puoi aggiungere o rimuovere simultaneamente i server ESXi in più cluster. Sono disponibili le seguenti operazioni simultanee:

* Aggiungi host a **cluster1** e aggiungi host a cluster aggiuntivi.
* Rimuovi host da **cluster1** e rimuovi host da cluster aggiuntivi.
* Aggiungi host a **cluster1** e rimuovi host da cluster aggiuntivi.
* Rimuovi host da **cluster1** e aggiungi host a cluster aggiuntivi.

Puoi aggiungere o rimuovere condivisioni di archiviazione NFS in un cluster vCenter Server with NSX-T NFS o vSAN esistente.
{:note}

Se il tuo cluster iniziale ha vSAN come archiviazione, l'aggiunta di uno o più server ESXi dopo la distribuzione può aumentare la capacità di archiviazione del cluster.

## Aggiunta di server ESXi alle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-adding}

### Prima di aggiungere i server ESXi
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* Non aggiungere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_full}}.
* Un'istanza vCenter Server with NSX-T con l'archiviazione NFS deve avere almeno 3 server ESXi. Puoi espandere il cluster predefinito per avere fino a 51 server ESXi. Ciascuno dei cluster non predefiniti può essere espanso per avere fino a 59 server ESXi.
* Un'istanza vCenter Server with NSX-T con l'archiviazione vSAN deve avere almeno 4 server ESXi. 

### Procedura per aggiungere i server ESXi
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere i server ESXi.
5. Nella sezione **Server ESXi**, fai clic su **Aggiungi**.
6. Nella finestra **Aggiungi server**, immetti il numero di server che desideri aggiungere.
7. Facoltativamente, seleziona la casella di spunta per aggiungere i server durante la modalità di manutenzione.
8. Esamina il costo stimato e fai clic su **Aggiungi**.

### Risultati dopo l'aggiunta dei server ESXi
{: #vc_nsx-t_addingremovingservers-adding-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiunta dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi diventa **In fase di modifica**.
3. Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

Se stai aggiungendo dei server ESXi durante la modalità di manutenzione, le VM non vengono migrate ai nuovi server finché non rimuovi il cluster dalla modalità di manutenzione.   
{:important}

## Rimozione di server ESXi dalle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-removing}

### Prima di rimuovere i server ESXi
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* Non rimuovere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* Un'istanza vCenter Server with NSX-T con archiviazione NFS deve avere almeno 3 server ESXi e un'istanza vCenter Server with NSX-T con archiviazione vSAN deve avere almeno 4 server ESXi.
* Quando rimuovi i server ESXi, i server vengono messi in modalità di manutenzione e, successivamente, tutte le VM in esecuzione sui server vengono migrate prima di essere rimosse da vCenter Server. Per il massimo controllo sulla ricollocazione delle VM, si consiglia di mettere in modalità di manutenzione i server ESXi da rimuovere e di migrare manualmente le VM in esecuzione sui server utilizzando il client web VMware vSphere. Dopo di che, rimuovi i server ESXi utilizzando la console {{site.data.keyword.vmwaresolutions_short}}.

### Procedura per rimuovere i server ESXi
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere i server ESXi.
5. Nella sezione **Server ESXi**, seleziona i server che vuoi rimuovere e fai clic su **Rimuovi**.

### Risultati dopo la rimozione dei server ESXi
{: #vc_nsx-t_addingremovingservers-removing-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di rimozione dei server ESXi è in fase di elaborazione. Sulla console, lo stato del cluster associato ai server ESXi diventa **In fase di modifica**.
3. I server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
   {:note}

## Aggiunta di archiviazione NFS alle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### Prima di aggiungere l'archiviazione NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

Non aggiungere l'archiviazione NFS dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. IBM non gestirà le condivisioni file NFS che aggiungi manualmente a un'istanza.

### Procedura per aggiungere l'archiviazione NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere l'archiviazione NFS.
5. Nella sezione **Storage**, fai clic su **Aggiungi**.
6. Nella finestra **Storage**, completa la configurazione di archiviazione.
   * Se vuoi aggiungere e configurare le stesse impostazioni in tutte le condivisioni file, specifica il **Numero di condivisioni**, le **Prestazioni** e la **Dimensione (GB)**.
   * Se vuoi aggiungere e configurare singolarmente le condivisioni file, seleziona **Configura condivisioni singolarmente**, quindi fai clic sull'icona **+** accanto all'etichetta **Aggiungi storage condiviso** e seleziona le **Prestazioni** e la **Dimensione (GB)** per ogni singola condivisione file. Devi selezionare almeno una condivisione file.
7. Fai clic su **Aggiungi storage NFS**.

### Risultati dopo l'aggiunta dell'archiviazione NFS
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di aggiunta dell'archiviazione NFS è in fase di elaborazione. Sulla console, lo stato del cluster associato all'archiviazione NFS diventa **In fase di modifica**.
3. Se non vedi la nuova archiviazione NFS aggiunta all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

## Rimozione dell'archiviazione NFS dalle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### Prima di rimuovere l'archiviazione NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* Non rimuovere l'archiviazione NFS dal client web VMware vSphere. Le modifiche che apporti al client web vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* Prima di rimuovere l'archiviazione NFS, assicurati di aver rimosso tutte le VM che risiedono sull'archiviazione.
* Assicurati che le condivisioni che pensi di rimuovere siano associate all'istanza vCenter Server corretta.
* Lo stato del cluster deve essere **Pronto per l'utilizzo**.

### Procedura per rimuovere l'archiviazione NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere l'archiviazione NFS.
5. Nella sezione **Storage**, seleziona la condivisione di archiviazione che vuoi rimuovere e fai clic su **Elimina**.
6. Fai clic su **Rimuovi** nella finestra **Rimuovi storage**.

### Risultati dopo la rimozione dell'archiviazione NFS
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Ti viene inviata una notifica via e-mail che indica che la richiesta di rimozione dell'archiviazione NFS è in fase di elaborazione. Sulla console, lo stato del cluster associato all'archiviazione NFS diventa **In fase di modifica**.
3. L'archiviazione NFS viene completamente recuperata dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per l'archiviazione NFS rimossa ti vengono addebitati costi fino alla fine del ciclo di fatturazione dell'infrastruttura di {{site.data.keyword.cloud_notm}}.
   {:note}

## Link correlati
{: #vc_nsx-t_addingremovingservers-related}

* [Distinta base di vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Requisiti e pianificazione per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Ordine di istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_deletinginstance)
* [Metti un host in modalità di manutenzione](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

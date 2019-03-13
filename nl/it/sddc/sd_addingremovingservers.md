---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Espansione e contrazione della capacità per le istanze Cloud Foundation
{: #sd_addingremovingservers}

Puoi espandere o contrarre la capacità della tua istanza VMware Cloud Foundation in base alle tue esigenze aziendali, aggiungendo o rimuovendo i server ESXi.

Un'istanza Cloud Foundation può avere fino a cinque cluster, uno dei quali è il predefinito. Ogni cluster iniziale può avere fino a 51 server ESXi e gli altri cluster possono averne un massimo di 59.

## Aggiunta di server ESXi alle istanze Cloud Foundation
{: #sd_addingremovingservers-adding}

### Prima di aggiungere i server ESXi
{: #sd_addingremovingservers-adding-prereq}

* Non aggiungere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web VMware vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_full}}.
* La piattaforma di base che hai ordinato ha 4 server ESXi per impostazione predefinita. Puoi espandere la piattaforma a un massimo di 32 server ESXi. Tuttavia, il numero di {{site.data.keyword.baremetal_short}} che puoi aggiungere alla volta è il seguente:
   * Per le configurazioni **Small** e **Large**, puoi aggiungere da 1 a 10 server ESXi alla volta.
   * Per le configurazioni **Skylake** e **Broadwell**, puoi aggiungere da 1 a 20 server ESXi alla volta.

## Procedura per aggiungere i server ESXi
{: #sd_addingremovingservers-adding-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza per la quale vuoi espandere la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster a cui vuoi aggiungere i server ESXi.
5. Nella sezione **Server ESXi**, fai clic su **Aggiungi**.
6. Nella finestra **Aggiungi server**, immetti il numero di server che vuoi aggiungere, esamina il costo stimato e fai quindi clic su **Aggiungi**.

### Risultati dopo l'aggiunta dei server ESXi
{: #sd_addingremovingservers-adding-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare ulteriori modifiche all'istanza.
2. All'aggiunta dei tuoi server ESXi, riceverai una notifica tramite e-mail.
3. Se non vedi i nuovi server ESXi aggiunti all'elenco nel cluster, controlla le notifiche e-mail o della console per trovare ulteriori dettagli sull'errore.

## Rimozione di server ESXi dalle istanze Cloud Foundation
{: #sd_addingremovingservers-removing}

### Prima di rimuovere i server ESXi
{: #sd_addingremovingservers-removing-prereq}

* Non rimuovere i server ESXi dal client web VMware vSphere. Le modifiche che apporti al client web VMware vSphere non vengono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}.
* La piattaforma di base che hai ordinato ha 4 server ESXi per impostazione predefinita. Puoi rimuovere i server ESXi che hai aggiunto, ma non puoi rimuovere i server ESXi predefiniti.
* Prima di rimuovere i server ESXi con il servizio F5 on {{site.data.keyword.cloud_notm}} o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} installato, devi migrare le VM di F5 BIG-IP e FortiGate in un server ESXi diverso rispetto a quello che ospita le VM.
* Prima di rimuovere i server ESXi con il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} installato, assicurati che non ci siano operazioni di backup o ripristino attive. Le operazioni attive, non riuscite o in corso, potrebbero impedire la rimozione dei server ESXi.

## Procedura per rimuovere i server ESXi
{: #sd_addingremovingservers-removing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza per la quale vuoi contrarre la capacità.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra.
4. Nella tabella **CLUSTER**, fai clic sul cluster da cui vuoi rimuovere i server ESXi.
6. Nella sezione **Server ESXi**, seleziona i server che vuoi rimuovere e fai clic su **Rimuovi**.

### Risultati dopo la rimozione dei server ESXi
{: #sd_addingremovingservers-removing-results}

1. Si potrebbe verificare un leggero ritardo sulla console mentre lo stato dell'istanza cambia da **Pronto per l'utilizzo** a **In fase di modifica**. Consenti il completamento dell'operazione prima di apportare altre modifiche all'istanza.
2. Alla rimozione dei tuoi server ESXi, riceverai una notifica tramite e-mail.
3. I server ESXi vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud_notm}} alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni.

   Per i server ESXi rimossi ti vengono addebitati costi fino alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}.
   {:note}

## Link correlati
{: #sd_addingremovingservers-related}

* [Distinta base di Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
* [Requisiti e pianificazione per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_planning)
* [Aggiunta, visualizzazione ed eliminazione di cluster per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-and-viewing-clusters-for-cloud-foundation-instances)
* [Metti un host in modalità di manutenzione](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Supporto del processore EVC (Enhanced vMotion Compatibility)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

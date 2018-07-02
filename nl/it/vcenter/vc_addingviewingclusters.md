---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server

I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **cluster1** per impostazione predefinita.

Puoi aggiungere i tuoi propri cluster alle istanze VMware vCenter Server per espandere la capacità di calcolo e archiviazione. All'interno di un cluster, puoi gestire i server ESXi per una migliore allocazione delle risorse e alta disponibilità. Quando non sono più necessari, puoi eliminare i cluster aggiunti dalle tue istanze.

**Disponibilità**: la funzione di eliminazione cluster è disponibile solo per le istanze che sono state distribuite o aggiornate alle release della V2.3 e successive.

## Aggiunta di cluster alle istanze vCenter Server

Il numero di cluster che possono essere aggiunti a un'istanza dipende dalla versione dell'istanza:
* Per le istanze che sono state distribuite o aggiornate alle release della V2.2 e successive, puoi aggiungere fino a 10 cluster.
* Per le istanze che sono state distribuite nelle release della V2.2 o precedenti, puoi aggiungere fino a 5 cluster.

### Impostazioni di sistema

Quando aggiungi un cluster a un'istanza vCenter Server, devi specificare le seguenti impostazioni.

#### Nome cluster

Il nome del cluster deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome del cluster deve iniziare e terminare con un carattere alfanumerico.
* La lunghezza massima del nome del cluster è di 30 caratteri.
* Il nome del cluster deve essere univoco all'interno dell'istanza vCenter Server.

#### Ubicazione data center

L'ubicazione del {{site.data.keyword.CloudDataCent}} del cluster è impostata sul {{site.data.keyword.CloudDataCent_notm}} dell'istanza vCenter Server per impostazione predefinita. Puoi distribuire il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso rispetto a quello dell'istanza distribuita, ma devi assicurarti che la latenza di rete tra i due {{site.data.keyword.CloudDataCents_notm}} sia inferiore a 150 ms. Per controllare la latenza di rete, puoi utilizzare uno strumento come [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Se distribuisci il cluster in un diverso {{site.data.keyword.CloudDataCent_notm}} o pod dell'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate tre VLAN aggiuntive da utilizzare con i {{site.data.keyword.baremetal_short}} ordinati.

### Impostazioni di Bare Metal Server

Puoi scegliere **Preconfigurato** o **Personalizzato**.

#### Preconfigurato

Per l'impostazione **Preconfigurato**, puoi scegliere una **Configurazione Bare Metal Server** in base ai tuoi requisiti:
* Small (Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz / 128 GB di RAM / 2 dischi)
* Medium (Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz / 256 GB di RAM / 2 dischi)
* Large (Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz / 512 GB di RAM / 2 dischi)

#### Personalizzato

Per l'impostazione **Personalizzato**, hai una serie di opzioni per il **Modello CPU** e la **RAM**. Le opzioni disponibili potrebbero variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

Tabella 1. Opzioni per i {{site.data.keyword.baremetal_short}} personalizzati

| Opzioni CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Numero di server Bare Metal

Per un cluster, è richiesto un minimo di due {{site.data.keyword.baremetal_short}}.

Per le istanze vCenter Server distribuite nelle release della V2.1 o successive, puoi aggiungere fino a 59 {{site.data.keyword.baremetal_short}} per un cluster e aggiungere da 1 a 59 server ESXi alla volta.

Per le istanze vCenter Server distribuite nelle release della V2.0 o precedenti, puoi aggiungere fino a 32 {{site.data.keyword.baremetal_short}} per un cluster. Il numero di {{site.data.keyword.baremetal_short}} che puoi aggiungere alla volta è il seguente:
* Per le configurazioni **Small**, **Medium** e **Large** di Bare Metal Server, puoi aggiungere da 1 a 10 server ESXi alla volta.
* Per la configurazione **Personalizzato** di Bare Metal Server, puoi aggiungere da 1 a 20 server ESXi alla volta.

Dopo la distribuzione, puoi creare fino a quattro ulteriori cluster. Se selezioni la configurazione **Personalizzato** di Bare Metal Server con l'archiviazione vSAN VMware, sono richiesti 4 server per il cluster iniziale e i cluster di post-distribuzione.

### Impostazioni di archiviazione

Per la tua archiviazione, puoi utilizzare **vSAN** o **NFS**.

#### Archiviazione vSAN

vSAN è disponibile solo per la configurazione Bare Metal personalizzata. Puoi personalizzare l'archiviazione vSAN VMware specificando il numero di dischi vSAN (2, 4, 6 o 8), il tipo e la dimensione del disco che soddisfano le tue esigenze di archiviazione e l'opzione di licenza vSAN.

Se il tuo cluster iniziale era un cluster vSAN, qualsiasi ulteriore cluster vSAN utilizza la stessa licenza vSAN e ha la stessa configurazione di quello iniziale. Questo vale anche se in qualsiasi cluster (iniziale o aggiuntivo) dell'istanza è stato scelto di distribuire vSAN. La prima volta, ti viene richiesta la licenza vSAN (BYOL o acquistata) e l'edizione. La prossima volta che selezioni vSAN per un cluster aggiuntivo, viene riutilizzata la licenza scelta inizialmente.

#### Archiviazione NFS

Se selezioni **Storage NFS**, puoi aggiungere l'archiviazione condivisa a livello di file per la tua istanza in cui tutte le condivisioni utilizzano le stesse impostazioni o puoi specificare impostazioni di configurazione diverse per ogni condivisione file. Specifica le seguenti opzioni NFS:

**Nota:** il numero di condivisioni file deve essere compreso tra 1 e 32.

* **Configura le condivisioni file singolarmente**: seleziona questa opzione per specificare diverse impostazioni di configurazione per ogni condivisione file.
* **Numero di condivisioni**: quando utilizzi la stessa impostazione di configurazione per ogni condivisione file, specifica il numero di condivisioni file per l'archiviazione condivisa NFS che vuoi aggiungere.
* **Dimensione**: seleziona la capacità che soddisfa le tue esigenze di archiviazione condivisa.
* **Prestazioni**: seleziona l'IOPS (Input/output Operations Per Second) per GB in base ai tuoi requisiti del carico di lavoro.
* **AGGIUNGI NFS**: seleziona questa opzione per aggiungere singole condivisioni file che utilizzeranno impostazioni di configurazione diverse.

Tabella 2. Opzioni del livello di prestazioni NFS

| Opzione        | Dettagli       |
  |:------------- |:------------- |
  | 2 IOPS/GB | Questa opzione è progettata per i carichi di lavoro più generici. Applicazioni di esempio includono: hosting di piccoli database, backup di applicazioni web o immagini disco di macchine virtuali per un hypervisor. |
  | 4 IOPS/GB | Questa opzione è progettata per i carichi di lavoro ad alta intensità che hanno un'alta percentuale di dati attivi alla volta. Applicazioni di esempio includono: database transazionali. |
  | 10 IOPS/GB | Questa opzione è progettata per i tipi di carichi di lavoro più impegnativi, come l'analisi. Applicazioni di esempio includono: database ad alte transazioni e altri database sensibili alle prestazioni. Questo livello di prestazioni è limitato a una capacità massima di 4 TB per condivisione file. |

### Impostazioni di licenza

Specifica l'opzione di licenza per il componente VMware vSphere nel cluster:
* Per gli utenti Business Partner, la licenza vSphere (Enterprise Plus edition) viene inclusa e acquistata per tuo conto.
* Per gli utenti non Business Partner, puoi utilizzare le licenze VMware fornite da IBM per questo componente selezionando **Includi con l'acquisto** o puoi utilizzare l'opzione Bring Your Own License (BYOL) selezionando **Fornita dall'utente** e immettendo la tua propria chiave di licenza.

### Riepilogo ordine

In base alla configurazione che hai selezionato per il cluster, il costo stimato viene generato e visualizzato immediatamente nel riquadro **Riepilogo ordine** sulla destra.

## Procedura per aggiungere i cluster alle istanze vCenter Server

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza a cui vuoi aggiungere i cluster.

   **Nota**: assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. In caso contrario, non potrai aggiungere i cluster all'istanza.

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra e quindi su **Aggiungi** nell'angolo superiore destro della tabella **CLUSTER**.
4. Nella pagina **Aggiungi cluster**, immetti il nome del cluster.
5. Se vuoi ospitare il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso da quello in cui è ospitata l'istanza, in **Bare Metal Server**, seleziona la casella di spunta **Seleziona un'ubicazione differente** e scegli il {{site.data.keyword.CloudDataCent_notm}} per ospitare l'istanza.
6. Completa la configurazione Bare Metal.
   * Se hai selezionato **Preconfigurato**, specifica la **Configurazione Bare Metal Server** e il **Numero di {{site.data.keyword.baremetal_short}}**. Se intendi utilizzare vSAN come soluzione di archiviazione, ricorda che sono richiesti un minimo di 4 {{site.data.keyword.baremetal_short}}.
   * Se hai selezionato **Personalizzato**, specifica il **Modello CPU**, la quantità di **RAM** e il **Numero di {{site.data.keyword.baremetal_short}}**.
7. Completa la configurazione di archiviazione.
   * Se selezioni **Storage vSAN**, specifica il **Numero di dischi vSAN**, il **Tipo e dimensioni del disco per i dischi vSAN** e come deve essere fornita la **Licenza vSAN**.
   * Se selezioni **Storage NFS**, specifica il **Numero di condivisioni**, la **Dimensione** e le **Prestazioni**.
   * Per aggiungere e configurare le condivisioni file singolarmente, seleziona la scheda **Storage NFS personalizzato**, fai clic sull'icona **+** accanto all'etichetta **Aggiungi NFS** e seleziona la **Dimensione** e le **Prestazioni** per ogni condivisione file. Devi selezionare almeno una condivisione file.
8. Specifica come viene fornita la chiave di licenza vSphere:
  * Per gli utenti Business Partner, la licenza vSphere (Enterprise Plus edition) viene inclusa e acquistata per tuo conto.
  * Per gli utenti non Business Partner, puoi selezionare una delle seguenti opzioni:
      * Se vuoi acquistare nuove licenze per tuo conto, seleziona **Includi con l'acquisto** per il componente.
      * Se vuoi utilizzare la tua propria licenza VMware per il componente, seleziona **Fornita dall'utente** e immetti la relativa chiave di licenza.
9. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster prima di aggiungerlo.
   1. Esamina le impostazioni per il cluster.
   2. Esamina il costo stimato del cluster. Fai clic su **Dettagli dei prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di aggiungere il cluster.
   4. Fai clic su **Fornitura**.

### Risultati dopo l'aggiunta dei cluster alle istanze vCenter Server

1. La distribuzione del cluster viene avviata automaticamente e lo stato del cluster viene modificato in **Inizializzazione**. Puoi controllare lo stato della distribuzione visualizzando la cronologia di distribuzione dalla pagina **Riepilogo** dell'istanza.
2. Quando il cluster è pronto per l'uso, il suo stato viene modificato in **Pronto per l'utilizzo**. Il cluster appena aggiunto viene abilitato con vSphere High Availability (HA) e vSphere Distributed Resource Scheduler (DRS).

**Importante**: non puoi modificare il nome del cluster. La modifica del nome del cluster potrebbe comportare errori nelle operazioni di aggiunta o rimozione dei server ESXi nel cluster.

## Visualizzazione dei cluster nelle istanze vCenter Server

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic su un'istanza per visualizzare i cluster al suo interno.
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, visualizza il riepilogo dei cluster:
  * **Nome**: il nome del cluster.
  * **Server ESXi**: il numero di server ESXi nel cluster.
  * **CPU**: la specifica CPU dei server ESXi nel cluster.
  * **Dischi vSAN personalizzati**: il numero di dischi vSAN nel cluster, incluso il tipo di disco e la capacità.
  * **Memoria**: la dimensione totale della memoria dei server ESXi nel cluster.
  * **Ubicazione Data Center **: il {{site.data.keyword.CloudDataCent_notm}} in cui è ospitato il cluster.
  * **Pod**: il pod in cui è distribuito il cluster.
  * **Stato**: lo stato del cluster. Lo stato può assumere uno dei seguenti valori:
    <dl class="dl">
        <dt class="dt dlterm">Inizializzazione</dt>
        <dd class="dd">Il cluster è in fase di creazione e configurazione.</dd>
        <dt class="dt dlterm">In fase di modifica</dt>
        <dd class="dd">Il cluster è in fase di modifica.</dd>
        <dt class="dt dlterm">Pronto per l'utilizzo</dt>
        <dd class="dd">Il cluster è pronto per l'uso.</dd>
        <dt class="dt dlterm">In fase di eliminazione</dt>
        <dd class="dd">Il cluster è in fase di eliminazione.</dd>
        <dt class="dt dlterm">Eliminato</dt>
        <dd class="dd">Il cluster è stato eliminato.</dd>
    </dl>
  * **Azioni**: fai clic sull'icona **Elimina** per eliminare il cluster.
4. Fai clic sul nome di un cluster per visualizzare i dettagli dei server ESXi e di archiviazione:

  * Dettagli dei server ESXi:
     * **Nome**: il nome del server ESXi è nel formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, dove:

       `host_prefix` è il prefisso del nome host,

       `n` è la sequenza del server,

       `subdomain_label` è l'etichetta del dominio secondario e

       `root_domain` è il nome del dominio root.

     * **Versione**: la versione del server ESXi.
     * **Credenziali**: il nome utente e la password per accedere al server ESXi.
     * **IP privato**: l'indirizzo IP privato del server ESXi.
     * **Stato**: lo stato del server ESXi, che può assumere uno dei seguenti valori:
        <dl class="dl">
        <dt class="dt dlterm">Aggiunto</dt>
        <dd class="dd">Il server ESXi è stato aggiunto ed è pronto per l'uso. </dd>
        <dt class="dt dlterm">In fase di aggiunta</dt>
        <dd class="dd">Il server ESXi è in fase di aggiunta. </dd>
        <dt class="dt dlterm">In fase di eliminazione</dt>
        <dd class="dd">Il server ESXi è in fase di eliminazione.</dd>
        </dl>
  * Dettagli di archiviazione:
    * **Nome**: il nome dell'archivio dati.
    * **Dimensione**: la capacità di archiviazione.
    * **IOPS/GB**: il livello di prestazioni dell'archiviazione.
    * **Protocollo NFS**: la versione NFS dell'archiviazione.

## Eliminazione di cluster dalle istanze vCenter Server

Potresti voler eliminare un cluster da un'istanza quando non è più necessario.

### Prima di eliminare

* Utilizza questa procedura per eliminare i cluster dalle istanze distribuite nelle release della V2.3 o successive.
* Per i cluster distribuiti nelle istanze della V2.2 o precedenti, devi aggiornare l'istanza alla V2.3 per poter eliminare i cluster che hai aggiunto all'istanza.
* Puoi eliminare un singolo cluster alla volta. Per eliminare più cluster, devi farlo in sequenza: attendere che il cluster precedente venga eliminato prima di tentare di eliminare quello successivo.
* Assicurati che tutti i nodi in un cluster siano accesi e operativi prima di eliminare il cluster.
* Quando elimini un cluster, verranno eliminate anche tutte le VM (macchine virtuali) dal cluster e non potranno essere ripristinate. Se vuoi mantenere le VM, migrale in altri cluster.
* Non è possibile eliminare il cluster predefinito.

## Procedura per eliminare i cluster dalle istanze vCenter Server

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da cui vuoi eliminare i cluster.

   **Nota**: assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. Altrimenti, non potrai eliminare i cluster dall'istanza.

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, individua il cluster che vuoi eliminare e fai clic sull'icona **Elimina** nella colonna **Azioni**.
4. Conferma di aver completato la migrazione delle macchine virtuali in altri cluster, se necessario, e di voler eliminare il cluster.

## Link correlati

* [Visualizzazione delle istanze vCenter Server](vc_viewinginstances.html)
* [Espansione e contrazione della capacità per le istanze vCenter Server](vc_addingremovingservers.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: vCenter Server NSX-T add cluster, view cluster vCenter Server NSX-T, delete cluster vCenter Server NSX-T

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingviewingcluster}

Puoi aggiungere i tuoi cluster alle istanze VMware vCenter Server with NSX-T per espandere la capacità di calcolo e archiviazione. All'interno di un cluster, puoi gestire i server ESXi per una migliore assegnazione delle risorse e alta disponibilità. Quando non sono più necessari, elimina i cluster aggiunti dalle tue istanze.

## Aggiunta di cluster alle istanze vCenter Server
{: #vc_nsx-t_addingviewingclusters-adding}

### Prima di aggiungere i cluster
{: #vc_nsx-t_addingviewingclusters-before-add}

* Quando possibile, aggiungi i cluster utilizzando la console {{site.data.keyword.vmwaresolutions_full}}, poiché le modifiche che apporti al client web VMware vSphere non sono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. Pertanto, aggiungi i cluster a vCenter Server solo per i cluster in loco o per i cluster che non puoi gestire o che non gestirai nella console {{site.data.keyword.vmwaresolutions_short}}.
* Il numero di cluster, host e VM (Virtual Machine) determina il limite massimo per il numero di cluster che puoi aggiungere. Devi rispettare le direttive e i limiti di dimensionamento VMware per la tua distribuzione. Per ulteriori informazioni sui limiti massimi, vedi [Valori massimi di configurazione di VMware](https://configmax.vmware.com/home){:external}.

### Impostazioni di sistema
{: #vc_nsx-t_addingviewingclusters-adding-sys-settings}

Quando aggiungi un cluster per un'istanza vCenter Server with NSX-T, devi specificare le seguenti impostazioni.

#### Nome cluster
{: #vc_nsx-t_addingviewingclusters-adding-cluster-name}

Il nome del cluster deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfabetici minuscoli, numerici e trattini (-).
* Il nome del cluster deve iniziare con un carattere alfabetico minuscolo.
* Il nome del cluster deve terminare con un carattere alfabetico minuscolo o un carattere numerico.
* La lunghezza massima del nome del cluster è di 30 caratteri.
* Il nome del cluster deve essere univoco all'interno dell'istanza vCenter Server with NSX-T.

#### Ubicazione data center
{: #vc_nsx-t_addingviewingclusters-adding-dc-location}

L'ubicazione del {{site.data.keyword.CloudDataCent}} del cluster è impostata sul {{site.data.keyword.CloudDataCent_notm}} dell'istanza vCenter Server per impostazione predefinita. Puoi distribuire il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso rispetto a quello dell'istanza distribuita, ma devi assicurarti che la latenza di rete tra i due {{site.data.keyword.CloudDataCents_notm}} sia inferiore a 150 ms. Per controllare la latenza di rete, puoi utilizzare uno strumento come [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

Se distribuisci il cluster in un diverso {{site.data.keyword.CloudDataCent_notm}} o pod dell'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate tre VLAN supplementari da utilizzare con i {{site.data.keyword.baremetal_short}} ordinati.

### Impostazioni di Bare Metal Server
{: #vc_nsx-t_addingviewingclusters-bare-metal-settings}

Puoi scegliere **Skylake**, **Cascade** o **Broadwell**. 

#### Skylake
{: #vc_nsx-t_addingviewingclusters-adding-skylake}

Per l'impostazione **Skylake**, hai opzioni per il **Modello CPU** e la **RAM**. Le opzioni disponibili potrebbero variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
{: caption="Tabella 1. Opzioni per Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Cascade
{: #vc_nsx-t_addingviewingclusters-adding-cascade}

Per l'impostazione **Cascade**, hai opzioni per il **Modello CPU** e la **RAM**.

Cascade {{site.data.keyword.baremetal_short}} sono disponibili solo per le istanze di VMware vSphere Enterprise Plus 6.7 U2.
{:note}

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Gold 4210 / 20 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Processore Dual Intel Xeon Gold 5218 / 32 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
| Processore Dual Intel Xeon Gold 6248 / 40 core totali, 2,5 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 768 GB, 1.5 TB |
{: caption="Tabella 2. Opzioni per Cascade {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Broadwell
{: #vc_nsx-t_addingviewingclusters-adding-broadwell}

Per l'impostazione **Broadwell**, hai una serie di opzioni per il **Modello CPU** e la **RAM**. Le opzioni disponibili potrebbero variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4 / 40 core totali, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 core totali, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
{: caption="Tabella 3. Opzioni per Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Numero di server Bare Metal
{: #vc_nsx-t_addingviewingclusters-adding-bare-metal-number}

* Tutti i server che ordini hanno la stessa configurazione.
* Per l'archiviazione vSAN, puoi ordinare da 4 a 59 server.
* Per l'archiviazione NFS, puoi ordinare da 2 a 59 server. Tuttavia, per i carichi di lavoro di produzione, ti consigliamo un numero minimo di 3 server. Per ulteriori informazioni, vedi [Un'istanza vCenter Server a due nodi è altamente disponibile?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

### Impostazioni di archiviazione
{: #vc_nsx-t_addingviewingclusters-adding-storage-settings}

Le impostazioni di archiviazione si basano sulla tua selezione della configurazione Bare Metal Server e sul tipo di archiviazione.

#### Archiviazione vSAN
{: #vc_nsx-t_addingviewingclusters-adding-vsan-storage}

Specifica le seguenti opzioni vSAN:
* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona un'opzione per i dischi di capacità di cui hai bisogno.
* **Numero di dischi vSAN**: specifica il numero di dischi di capacità che vuoi aggiungere.
* Se vuoi aggiungere dischi di capacità oltre il limite di 10, seleziona la casella **Alte prestazioni con Intel Optane**. Questa opzione fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 12 dischi di capacità ed è utile per i carichi di lavoro che richiedono meno latenza e una maggiore velocità IOPS.

  L'opzione **Alte prestazioni con Intel Optane** è disponibile solo per i modelli di CPU Skylake e Cascade.
  {:note}

* Riesamina i valori di **Tipo di disco per i dischi cache vSAN** e **Numero di dischi cache vSAN**. Questi valori dipendono dalla selezione della casella **Alte prestazioni con Intel Optane**.
* **Licenza vSAN**: utilizza la licenza VMware fornita da IBM per il componente vSAN selezionando **Includi con l'acquisto** o utilizza l'opzione BYOL (Bring Your Own License) selezionando **Fornita dall'utente** e immettendo la tua chiave di licenza.

Se il tuo cluster iniziale era un cluster vSAN, qualsiasi ulteriore cluster vSAN utilizza la stessa licenza vSAN e ha la stessa configurazione di quello iniziale. Questo vale anche se in qualsiasi cluster (iniziale o aggiuntivo) dell'istanza è stato scelto di distribuire vSAN. La prima volta, ti viene richiesta la licenza vSAN (BYOL o acquistata) e l'edizione. La prossima volta che selezioni vSAN per un nuovo cluster, viene riutilizzata la licenza scelta inizialmente.

#### Archiviazione NFS
{: #vc_nsx-t_addingviewingclusters-adding-nfs-storage}

Se selezioni **Storage NFS**, puoi aggiungere l'archiviazione condivisa a livello di file per la tua istanza in cui tutte le condivisioni utilizzano le stesse impostazioni o puoi specificare impostazioni di configurazione diverse per ogni condivisione file. Specifica le seguenti opzioni NFS:

Il numero di condivisioni file deve essere compreso tra 1 e 32.
{:note}

* **Configura le condivisioni singolarmente**: seleziona questa opzione per specificare diverse impostazioni di configurazione per ogni condivisione file.
* **Numero di condivisioni**: se vuoi utilizzare la stessa impostazione di configurazione per ogni condivisione file, specifica il numero di condivisioni file per l'archiviazione condivisa NFS che vuoi aggiungere.
* **Dimensione**: seleziona la capacità che soddisfa le tue esigenze di archiviazione condivisa.
* **Prestazioni**: seleziona l'IOPS (input/output operations per second) per GB in base ai tuoi requisiti del carico di lavoro.
* **AGGIUNGI NFS**: seleziona questa opzione per aggiungere singole condivisioni file con diverse impostazioni di configurazione.

Dettagli del livello di prestazioni:

| Opzione        | Dettagli       |
|:------------- |:------------- |
| 0,25 IOPS/GB | Questa opzione è progettata per i carichi di lavoro che non vengono utilizzati spesso. Applicazioni di esempio includono: dati archiviati, hosting di database di grandi dimensioni con dati legacy o immagini di dischi virtuali del sistema di memoria virtuale come backup. |
| 2 IOPS/GB | Questa opzione è progettata per i carichi di lavoro più generici. Applicazioni di esempio includono: hosting di database di piccole dimensioni, backup di applicazioni web o immagini di dischi di VM (Virtual Machine) per un hypervisor. |
| 4 IOPS/GB | Questa opzione è progettata per i carichi di lavoro ad alta intensità che hanno un'alta percentuale di dati attivi alla volta. Applicazioni di esempio includono: database transazionali. |
| 10 IOPS/GB | Questa opzione è progettata per i tipi di carichi di lavoro più impegnativi, come l'analisi. Applicazioni di esempio includono: database ad alte transazioni e altri database sensibili alle prestazioni. Questo livello di prestazioni è limitato a una capacità massima di 4 TB per condivisione file. |
{: caption="Tabella 4. Opzioni del livello di prestazioni NFS" caption-side="top"}

### Impostazioni di licenza
{: #vc_nsx-t_addingviewingclusters-adding-licensing-settings}

Specifica l'opzione di licenza per il componente VMware vSphere nel cluster:
* Per gli utenti Business Partner, la licenza vSphere (Enterprise Plus edition) viene inclusa e acquistata per tuo conto.
* Per gli utenti non Business Partner, puoi utilizzare le licenze VMware fornite da IBM per questo componente selezionando **Includi con l'acquisto** o puoi utilizzare l'opzione Bring Your Own License (BYOL) selezionando **Fornita dall'utente** e immettendo la tua propria chiave di licenza.

### Impostazioni dell'interfaccia di rete
{: #vc_nsx-t_addingviewingclusters-adding-network-interface-settings}

Le impostazioni di abilitazione della scheda di interfaccia di rete (NIC) si basano sulla tua selezione di **Rete pubblica e privata** o **Solo rete privata**.

### Riepilogo ordine
{: #vc_nsx-t_addingviewingclusters-adding-order-summary}

In base alla configurazione che hai selezionato per il cluster, il costo stimato viene generato e visualizzato istantaneamente nel riquadro **Riepilogo ordine** sulla destra. Fai clic su **Dettagli sui prezzi** per generare un documento PDF con il riepilogo del costo per le risorse {{site.data.keyword.vmwaresolutions_short}}.

Puoi anche aggiungere le risorse di cui è stato eseguito il provisioning allo strumento di stima {{site.data.keyword.cloud_notm}} facendo clic su **Aggiungi alla stima**. Ciò è utile se desideri stimare il costo delle risorse {{site.data.keyword.vmwaresolutions_short}} selezionate insieme ad altre risorse {{site.data.keyword.cloud_notm}} di cui potresti prendere in considerazione l'acquisto.

## Procedura per aggiungere i cluster alle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingviewingclusters-adding-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza a cui vuoi aggiungere i cluster.

   Assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. In caso contrario, non potrai aggiungere i cluster all'istanza.
   {:note}
3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra e quindi su **Aggiungi** nell'angolo superiore destro della tabella **CLUSTER**.
4. Nella pagina **Aggiungi cluster**, immetti il nome del cluster.
5. Se vuoi ospitare il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso da quello in cui è ospitata l'istanza, in **Bare Metal Server**, seleziona la casella di spunta **Seleziona un'ubicazione differente** e scegli il {{site.data.keyword.CloudDataCent_notm}} per ospitare l'istanza.
6. Completa la configurazione Bare Metal. Specifica il **Modello CPU**, la quantità di **RAM** e il **Numero di {{site.data.keyword.baremetal_short}}**.
7. Completa la configurazione di archiviazione.
  * Se selezioni **Storage vSAN**, specifica i tipi di disco per i dischi di capacità e cache, il numero di dischi e l'edizione della licenza vSAN. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le stesse impostazioni in tutte le condivisioni file, specifica il **Numero di condivisioni**, le **Prestazioni** e la **Dimensione (GB)**.
  * Se selezioni **Storage NFS** e vuoi aggiungere e configurare le condivisioni file singolarmente, seleziona **Configura condivisioni singolarmente**. Quindi, fai clic sull'icona **+** accanto all'etichetta **Aggiungi storage condiviso** e seleziona le **Prestazioni** e la **Dimensione (GB)** per ogni condivisione file. Devi selezionare almeno una condivisione file.
8. Completa le impostazioni dell'interfaccia di rete.
8. Specifica come viene fornita la chiave di licenza vSphere:
  * Per gli utenti Business Partner, la licenza vSphere (Enterprise Plus edition) viene inclusa e acquistata per tuo conto.
  * Per gli utenti che non sono Business Partner, puoi selezionare una delle seguenti opzioni:
      * Se vuoi acquistare nuove licenze per tuo conto, seleziona **Includi con l'acquisto** per il componente.
      * Se vuoi utilizzare la tua propria licenza VMware per il componente, seleziona **Fornita dall'utente** e immetti la tua chiave di licenza.
9. Seleziona l'impostazione di rete **Rete pubblica e privata** o **Solo rete privata**.
10. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster prima di aggiungerlo.
   1. Esamina le impostazioni per il cluster.
   2. Esamina il costo stimato del cluster. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo
del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di aggiungere il cluster.
   4. Fai clic su **Fornitura**.

### Risultati dopo che hai aggiunto cluster alle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingviewingclusters-adding-results}

1. La distribuzione del cluster viene avviata automaticamente e lo stato del cluster viene modificato in **Inizializzazione**. Puoi controllare lo stato della distribuzione visualizzando la cronologia di distribuzione dalla pagina **Riepilogo** dell'istanza.
2. Quando il cluster è pronto per l'uso, il suo stato viene modificato in **Pronto per l'utilizzo**. Il cluster appena aggiunto viene abilitato con vSphere HA (High Availability) e vSphere DRS (Distributed Resource Scheduler).

Non puoi modificare il nome del cluster. La modifica del nome del cluster potrebbe comportare errori nelle operazioni di aggiunta o rimozione dei server ESXi nel cluster.
{:important}

## Procedura per visualizzare i cluster nelle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingviewingclusters-viewing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
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
4. Fai clic sul nome di un cluster per visualizzare i dettagli del server ESXi, dell'archiviazione e dell'interfaccia di rete:

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Nome | Il nome del server ESXi è nel seguente formato: `<data_center>-<host_prefix><n>.<subdomain_label>.<root_domain>`, dove `n` è la sequenza del server ESXi. |
| Versione | La versione del server ESXi. |
| Credenziali | Il nome utente e la password per accedere al server ESXi. |
| IP privato | L'indirizzo IP privato del server ESXi. |
| Stato | Lo stato del server ESXi, che può assumere uno dei seguenti valori:<br> **Aggiunto** Il server ESXi è stato aggiunto ed è pronto per l'uso.<br> **In fase di aggiunta** Il server ESXi è in fase di aggiunta.<br> **In fase di eliminazione** Il server ESXi è in fase di eliminazione. |
{: caption="Tabella 5. Dettagli del server ESXi" caption-side="top"}

Visualizza i dettagli di archiviazione:

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Nome | Il nome dell'archivio dati. |
| Dimensione | La capacità di archiviazione. |
| IOPS/GB | Il livello di prestazioni dell'archiviazione. |
| Protocollo NFS | La versione NFS dell'archiviazione. |
{: caption="Tabella 6. Dettagli dell'archiviazione" caption-side="top"}

Visualizza i dettagli dell'interfaccia di rete:

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Numero VLAN | Il numero VLAN univoco.  |
| Descrizione | La descrizione della VLAN.  |
| Ubicazione | L'ubicazione del data center. |
| Rotta primaria | La rotta primaria della VLAN. |
{: caption="Tabella 7. Interfaccia di rete - Dettagli della VLAN" caption-side="top"}

Fai clic su **View Resource** per accedere ai dettagli della VLAN.

Visualizza i dettagli della sottorete:

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Nome | Il nome della sottorete. Fai clic sul nome per accedere ai dettagli della sottorete. |
| Tipo | Il tipo di sottorete: primaria o portatile. |
| Descrizione | La descrizione della sottorete. |
{: caption="Tabella 8. Interfaccia di rete - Dettagli della sottorete" caption-side="top"}

Visualizza i dettagli IP:

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| IP | L'indirizzo IP. |
| Stato | Lo stato dell'indirizzo IP. |
| Descrizione |La descrizione dell'indirizzo IP.  |
{: caption="Tabella 9. Interfaccia di rete - Dettagli IP" caption-side="top"}

## Eliminazione di cluster dalle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingviewingclusters-deleting}

Potresti voler eliminare un cluster da un'istanza quando non è più necessario.

### Prima di eliminare
{: #vc_nsx-t_addingviewingclusters-deleting-prereq}

* Quando possibile, elimina i cluster utilizzando la console {{site.data.keyword.vmwaresolutions_full}}, poiché le modifiche che apporti al client web VMware vSphere non sono sincronizzate con la console {{site.data.keyword.vmwaresolutions_short}}. Pertanto, elimina i cluster da vCenter Server solo per i cluster in loco o per i cluster che non puoi gestire o che non gestirai nella console {{site.data.keyword.vmwaresolutions_short}}.
* Puoi eliminare un singolo cluster alla volta. Per eliminare più di un cluster, devi farlo in sequenza. Attendi che il cluster precedente venga eliminato prima di eliminare quello successivo.
* Assicurati che tutti i nodi in un cluster siano accesi e operativi prima di eliminare il cluster.
* Quando elimini un cluster, da questo vengono eliminate anche tutte le VM e non potranno essere ripristinate. Se vuoi mantenere le VM, migrale in altri cluster.
* Il cluster predefinito non può essere eliminato.

### Procedura per eliminare i cluster dalle istanze vCenter Server with NSX-T
{: #vc_nsx-t_addingviewingclusters-deleting-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da cui vuoi eliminare i cluster.

   Assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. Altrimenti, non puoi eliminare i cluster dall'istanza.
   {:note}

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, individua il cluster che vuoi eliminare e fai clic sull'icona **Elimina** nella colonna **Azioni**.
4. Conferma di aver completato la migrazione delle VM ad altri cluster e, se necessario, di voler eliminare il cluster.

## Link correlati
{: #vc_nsx-t_addingviewingclusters-related}

* [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Espansione e contrazione della capacità per le istanze vCenter Server with NSX-T](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_addingremovingservers)

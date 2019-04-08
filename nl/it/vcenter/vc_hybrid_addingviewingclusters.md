---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-18"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aggiunta, visualizzazione ed eliminazione di cluster per le istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters}

I server ESXi che hai configurato quando hai ordinato un'istanza vengono raggruppati sotto forma di **cluster1** per impostazione predefinita.

Puoi aggiungere cluster alla tua istanza VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle per espandere la capacità di calcolo e archiviazione. All'interno di un cluster, gestisci i server ESXi per una migliore allocazione delle risorse e alta disponibilità. Quando non sono più necessari, elimina i cluster aggiunti dalla tua istanza.

## Aggiunta di cluster alle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding}

Il numero di cluster che possono essere aggiunti a un'istanza dipende dalla versione dell'istanza:
* Per le istanze che sono state distribuite o aggiornate alla V2.5 e versioni successive, il numero di cluster, host e VM determina il limite massimo per il numero di cluster che puoi aggiungere. Devi rispettare le direttive e i limiti di dimensionamento VMware per la tua distribuzione.
* Per le istanze che sono state distribuite o aggiornate alla V2.3 e versioni successive, puoi aggiungere fino a 10 cluster.

Per ulteriori informazioni sui limiti massimi, vedi [Valori massimi di configurazione di VMware](https://configmax.vmware.com/home){:new_window}.

### Impostazioni di sistema
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

Quando aggiungi un cluster a un'istanza vCenter Server with Hybridity Bundle, devi specificare le seguenti impostazioni.

#### Nome cluster
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

Il nome del cluster deve rispettare i seguenti requisiti:
* Sono consentiti solo caratteri alfanumerici e trattini (-).
* Il nome del cluster deve iniziare e terminare con un carattere alfanumerico.
* La lunghezza massima del nome del cluster è di 30 caratteri.
* Il nome del cluster deve essere univoco all'interno dell'istanza vCenter Server with Hybridity Bundle.

#### Ubicazione data center
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

L'ubicazione del {{site.data.keyword.CloudDataCent_notm}} del cluster è impostata sul {{site.data.keyword.CloudDataCent_notm}} dell'istanza vCenter Server per impostazione predefinita. Puoi distribuire il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso rispetto a quello dell'istanza distribuita, ma devi assicurarti che la latenza di rete tra i due {{site.data.keyword.CloudDataCents_notm}} sia inferiore a 150 ms. Per controllare la latenza di rete, utilizza uno strumento come [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Se distribuisci il cluster in un diverso {{site.data.keyword.CloudDataCent_notm}} o pod dell'infrastruttura {{site.data.keyword.cloud_notm}}, vengono ordinate altre tre VLAN da utilizzare con i {{site.data.keyword.baremetal_short}} ordinati.

### Impostazioni di Bare Metal Server
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

Puoi scegliere **Skylake** o **Broadwell**. Le opzioni possono variare in base alla versione in cui è stata inizialmente distribuita la tua istanza.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

Se selezioni **Skylake**, puoi scegliere la combinazione di CPU e RAM in base alle tue esigenze.

Tabella 1. Opzioni per i server bare metal Skylake

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Processore Dual Intel Xeon Silver 4110 / 16 core totali, 2,1 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 5120 / 28 core totali, 2,2 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |
| Processore Dual Intel Xeon Gold 6140 / 36 core totali, 2,3 GHz | 64 GB, 96 GB, 128 GB, 192 GB, 384 GB, 768 GB, 1,5 TB |

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

Se selezioni **Broadwell**, puoi scegliere la combinazione di CPU e RAM in base alle tue esigenze.

Tabella 2. Opzioni per i server bare metal Broadwell

| Opzioni del modello CPU        | Opzioni RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4 / 16 core totali, 2,1 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2650 v4 / 24 core totali, 2,2 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Dual Intel Xeon E5-2690 v4 / 28 core totali, 2,6 GHz | 64 GB, 128 GB, 256 GB, 512 GB, 768 GB, 1,5 TB |
| Quad Intel Xeon E7-4820 v4 / 40 core totali, 1,9 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |
| Quad Intel Xeon E7-4850 v4 / 64 core totali, 2,2 GHz | 128 GB, 256 GB, 512 GB, 1 TB, 2 TB, 3 TB |

#### Numero di server Bare Metal
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

Per un cluster, sono richiesti almeno due {{site.data.keyword.baremetal_short}}.

Puoi aggiungere fino a 59 {{site.data.keyword.baremetal_short}} per un cluster e puoi aggiungere da 1 a 59 server ESXi alla volta.

Dopo la distribuzione, puoi creare fino a quattro ulteriori cluster. Per l'archiviazione VMware vSAN, sono richiesti quattro server sia per il cluster iniziale che per i cluster di post-distribuzione.

### Impostazioni di archiviazione vSAN
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

VMware vSAN 6.6 è incluso con il tuo ordine dell'istanza vCenter Server with Hybridity Bundle. Specifica le seguenti opzioni vSAN:
* **Tipo e dimensioni del disco per i dischi vSAN**: seleziona un'opzione per i dischi di capacità di cui hai bisogno.
* **Numero di dischi vSAN**: specifica il numero di dischi di capacità che vuoi aggiungere.
* Se vuoi aggiungere dischi di capacità oltre il limite di otto, seleziona la casella **Alte prestazioni con Intel Optane**. Questa opzione fornisce due alloggiamenti per dischi di capacità supplementari per un totale di 10 dischi di capacità ed è utile per i carichi di lavoro che richiedono meno latenza e una maggiore velocità IOPS.

  L'opzione **Alte prestazioni con Intel Optane** è disponibile solo per i modelli di CPU Skylake Dual Intel Xeon Gold 5120 e Dual Intel Xeon Gold 6140.
  {:note}

* Riesamina i valori di **Tipo di disco per i dischi cache vSAN** e **Numero di dischi cache vSAN**. Questi valori dipendono dalla selezione della casella **Alte prestazioni con Intel Optane**.
* **Licenza vSAN**: seleziona l'edizione della licenza VMware vSAN 6.6 (Advanced o Enterprise).

### Impostazioni di licenza
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

Licenze fornite da IBM per i seguenti componenti VMware:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (Edizione Advanced o Enterprise)

### Impostazioni dell'interfaccia di rete
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

Le impostazioni della scheda di interfaccia di rete (NIC) si basano sulla tua selezione di **Rete pubblica e privata** o **Solo rete privata**. I seguenti servizi aggiuntivi richiedono NIC pubbliche e non sono disponibili con l'opzione privata:

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Riepilogo ordine
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

In base alla configurazione che hai selezionato per il cluster, il costo stimato viene generato e visualizzato immediatamente nel riquadro **Riepilogo ordine** sulla destra.

## Procedura per aggiungere i cluster alle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per visualizzare i cluster al suo interno.

   Assicurati che lo stato dell'istanza sia **Pronto per l'utilizzo**. Altrimenti, non puoi aggiungere i cluster all'istanza.
   {:note}

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra e quindi su **Aggiungi** nell'angolo superiore destro della tabella **CLUSTER**.
4. Nella pagina **Aggiungi cluster**, immetti il nome del cluster.
5. Puoi ospitare il cluster in un {{site.data.keyword.CloudDataCent_notm}} diverso da quello in cui è ospitata l'istanza. Per farlo, in **Bare Metal Server**, seleziona la casella di spunta **Seleziona un'ubicazione differente** e scegli il {{site.data.keyword.CloudDataCent_notm}} in cui ospitare l'istanza.
6. Seleziona il **Modello CPU**, la quantità di **RAM** e il **Numero di server Bare Metal** per la configurazione Bare Metal.
7.  Seleziona **Storage vSAN** e specifica i tipi di disco per i dischi di capacità e cache e il numero di dischi. Se vuoi più spazio di archiviazione, seleziona la casella **Alte prestazioni con Intel Optane**.
8. Seleziona l'edizione della licenza di VMware vSAN per la configurazione della licenza.
9. Seleziona l'impostazione di rete **Rete pubblica e privata** o **Solo rete privata**.
10. Nel riquadro **Riepilogo ordine**, verifica la configurazione del cluster prima di aggiungerlo.
   1. Esamina le impostazioni per il cluster.
   2. Esamina il costo stimato del cluster. Fai clic su **Dettagli sui prezzi** per generare un riepilogo in formato PDF. Per salvare o stampare il riepilogo del tuo ordine, fai clic sull'icona **Stampa** o **Download** nella parte superiore destra della finestra PDF.
   3. Fai clic sul link o sui link dei termini che si applicano al tuo ordine e conferma di accettare questi termini prima di aggiungere il cluster.
   4. Fai clic su **Fornitura**.

### Risultati dopo l'aggiunta di cluster alle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding-results}

1. La distribuzione del cluster viene avviata automaticamente e lo stato del cluster viene modificato in **Inizializzazione**. Puoi controllare lo stato della distribuzione visualizzando la cronologia di distribuzione nella pagina **Riepilogo** dell'istanza.
2. Quando il cluster è pronto per l'uso, il suo stato viene modificato in **Pronto per l'utilizzo**. Il cluster appena aggiunto viene abilitato con vSphere High Availability (HA) e vSphere Distributed Resource Scheduler (DRS).

Non puoi modificare il nome del cluster. La modifica del nome del cluster potrebbe comportare errori nelle operazioni di aggiunta o rimozione dei server ESXi nel cluster.
{:important}

## Procedura per visualizzare i cluster nelle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza per visualizzare i cluster al suo interno.
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
4. Fai clic sul nome di un cluster per visualizzare i dettagli dei server ESXi, dell'archiviazione e dell'interfaccia di rete.

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
  * Interfaccia di rete - Dettagli VLAN:
    * **Numero VLAN**: il numero VLAN univoco.
    * **Descrizione**: la descrizione della VLAN.
    * **Ubicazione**: l'ubicazione del data center.
    * **Rotta primaria**: la rotta primaria della VLAN.
    Fai clic su **View Resource** per accedere ai dettagli della VLAN.
  * Interfaccia di rete - Dettagli sottorete:
    * **Nome**: il nome della sottorete. Fai clic sul nome per accedere ai dettagli della sottorete. 
    * **Tipo**: il tipo di sottorete: primaria o portatile.
    * **Descrizione**: la descrizione della sottorete.
  * Interfaccia di rete - Dettagli IP:
    * **IP**: l'indirizzo IP.
    * **Stato**: lo stato dell'indirizzo IP. 
    * **Descrizione**: la descrizione dell'indirizzo IP.

## Eliminazione di cluster dalle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-deleting}

Potresti voler eliminare un cluster da un'istanza quando non è più necessario.

### Prima di eliminare
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* Puoi eliminare un singolo cluster alla volta. Per eliminare più cluster, devi farlo in sequenza: attendi che il cluster precedente venga eliminato prima di eliminare quello successivo.
* Assicurati che tutti i nodi in un cluster siano accesi e operativi prima di eliminare il cluster.
* Quando elimini un cluster, da questo vengono eliminate anche tutte le VM (Virtual Machine) e non possono essere ripristinate. Se vuoi mantenere le VM, migrale in altri cluster.
* Il cluster predefinito non può essere eliminato.

## Procedura per eliminare i cluster dalle istanze vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Nella tabella **Istanze vCenter Server**, fai clic sull'istanza da cui vuoi eliminare i cluster.

   Assicurati che l'istanza sia nello stato **Pronto per l'utilizzo**. Altrimenti, non potrai rimuovere i cluster dall'istanza.
   {:note}

3. Fai clic su **Infrastruttura** nel riquadro di navigazione a sinistra. Nella tabella **CLUSTER**, individua il cluster che vuoi eliminare e fai clic sull'icona **Elimina** nella colonna **Azioni**.

## Link correlati
{: #vc_hybrid_addingviewingclusters-related}

* [Visualizzazione delle istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Espansione e contrazione della capacità per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)

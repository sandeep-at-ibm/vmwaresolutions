---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione delle risorse Shared
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared viene fornito come un'offerta sperimentale.
{:note}

I clienti gestiscono il ciclo di vita dei data center virtuali utilizzando l'offerta {{site.data.keyword.vmwaresolutions_short}}.

Le seguenti funzioni sono supportate, utilizzando l'IU web o l'API pubblica:
- Visualizza le istanze del data center virtuale
- Accesso alla console di gestione vCloud
- Ridimensiona le istanze del data center virtuale
- Elimina le istanze del data center virtuale
- Aggiunta e rimozione dei servizi VMware alle/dalle istanze del data center virtuale (**in futuro**)

## Visualizzazione delle istanze del data center virtuale
{: #shared_managing-viewing}

Per visualizzare un riepilogo di tutte le istanze del data center virtuale fornite per un account utente, completa la seguente procedura:

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Dal banner della console, fai clic sull'icona del tuo account utente e quindi sul campo **Account** per selezionare l'account utente per il quale vuoi controllare le istanze.  
3. Nella tabella **IBM Cloud VMware Solutions Shared**, visualizza l'elenco delle istanze fornite nell'account utente selezionato.

| Elemento        | Descrizione       |  
|:------------- |:------------- |
| Nome | Il nome dell'istanza |
| Tipo | Il tipo di data center virtuale |
| Ubicazione | Il {{site.data.keyword.CloudDataCent_notm}} in cui è ospitata l'istanza |  
| Data/ora di creazione | La data e ora di creazione dell'istanza |
| Stato | Lo stato dell'istanza |

{: caption="Tabella 1. Voci dell'istanza del data center virtuale" caption-side="top"}

L'istanza può avere una serie di stati.

| Stato        | Descrizione       |
|:------------- |:------------- |
| In fase di creazione | L'istanza è in fase di creazione. |
| Pronto per l'utilizzo | L'istanza è pronta per l'uso. |
| In fase di modifica | L'istanza è in fase di modifica. |
| In fase di eliminazione | L'istanza è in fase di eliminazione. |
| Eliminato | L'istanza è stata eliminata. |

{: caption="Tabella 2. Descrizioni dello stato per le istanze del data center virtuale" caption-side="top"}

## Procedura per visualizzare i dettagli del data center virtuale
{: #vc_viewinginstances-procedure-view-vdc-details}

Per visualizzare i dettagli delle proprietà di un'istanza:

1. Nella tabella **IBM Cloud VMware Solutions Shared**, fai clic sul nome di un'istanza.
2. In **Proprietà**, visualizza i dettagli dell'istanza.

| Proprietà        | Descrizione       |
|:------------- |:------------- |
| Nome | Il nome dell'istanza. |
| Tipo | Il tipo di data center virtuale. |
| Ubicazione | Il {{site.data.keyword.CloudDataCent_notm}} in cui è ospitata l'istanza. |
| ID | L'ID dell'istanza. |
| Ora di creazione | La data e ora di creazione dell'istanza, ossia quando inizia la fatturazione. |
| vCPU | La quantità di CPU limitata o riservata che può essere utilizzata in qualsiasi momento dal data center virtuale.  |
| RAM | La quantità di memoria limitata o riservata che può essere utilizzata in qualsiasi momento dal data center virtuale.  |
| IP pubblico| Ogni data center virtuale viene fornito con cinque indirizzi IP pubblici che possono essere utilizzati per la connessione di vApp e VM a internet. |

{: caption="Tabella 3. Proprietà del data center virtuale" caption-side="top"}

## Accesso alla console di gestione vCloud Director
{: #shared_managing-accessing}

Gestisci il data center virtuale tramite la console di gestione vCloud Director.

Il primo accesso alla console di gestione vCloud Director viene effettuato tramite la credenziale **admin**. Genera una password nella pagina dei dettagli del data center virtuale con il link **Reset Location Password**. Questa azione genera una password casuale complessa iniziale, che può essere reimpostata in qualsiasi momento.

L'offerta {{site.data.keyword.vmwaresolutions_short}} non archivia la password **admin**. Dopo che una password è stata generata, devi acquisirla. Se la password viene persa, deve essere generata una nuova password.

Tutti i data center virtuali nella stessa ubicazione hanno la stessa password **admin**. La reimpostazione della password su un'istanza del data center virtuale, reimposta la password **admin** per l'accesso alla console di gestione vCloud Director per tutte le istanze del data center virtuale nella stessa ubicazione.

Dopo la generazione della prima password **admin**, il pulsante **vCloud Director Portal** diventa disponibile nell'angolo in alto a destra della pagina dei dettagli. Fai clic su **vCloud Director Portal** per accedere alla console di gestione vCloud Director. Per accedere, utilizza il nome utente e la password **admin** ottenuti con il link **Reset Location Password**.

## Ridimensionamento delle istanze del data center virtuale
{: #shared_managing-resizing}

In qualsiasi momento quando un'istanza del data center virtuale è nello stato **Ready To Use**, puoi modificare la quantità di risorse assegnate a un data center virtuale. 

Ridimensiona le risorse di vCPU o RAM per un'istanza del data center virtuale nella pagina dei dettagli del data center virtuale. Fai clic sull'icona a matita accanto a **Resources** sulla pagina dei dettagli e modifica i valori delle proprietà vCPU o RAM.

Infine, verifica la configurazione e i costi stimati prima di inserire il tuo ordine.

  La modifica alla configurazione ha esito negativo se le risorse di vCPU e RAM sono in uso mentre vengono ridotte a un livello inferiore all'utilizzo di risorse al momento attivo.
  {:note}

L'istanza del data center virtuale entra nello stato **Modifying** mentre viene apportata la modifica. Quando le risorse sono pronte per l'utilizzo, lo stato viene modificato con **Ready to Use**.

## Eliminazione delle istanze del data center virtuale
{: #shared_managing-deleting}

Un'istanza del data center virtuale può essere eliminata quando è nello stato **Ready To Use**. Esegui l'operazione di eliminazione dalla pagina dei dettagli del data center virtuale o dalla tabella IBM Cloud VMware Solutions Shared Resource.

Dalla pagina dei dettagli, fai clic sull'icona **Delete** nell'opzione di menu di overflow all'estrema destra della pagina dei dettagli. Successivamente, conferma di voler eliminare l'istanza.

Dalla tabella IBM Cloud VMware Solutions Shared Resource, individua l'istanza che vuoi eliminare e fai clic sull'icona **Delete** nella colonna **Actions**. Successivamente, conferma di voler eliminare l'istanza.

## Link correlati
{: #shared_managing-related}

* [Panoramica di {{site.data.keyword.cloud_notm}} for VMware Solutions Shared](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [Ordinazione di Shared On-demand](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [Ordinazione di Shared Reserved](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}

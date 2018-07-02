---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-13"

---

# Ordine di IBM Spectrum Protect Plus on IBM Cloud

Puoi ordinare il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} mentre ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di IBM Spectrum Protect Plus on IBM Cloud per una nuova istanza

Puoi ordinare una nuova istanza con IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_full}}, quando ordini una nuova istanza, seleziona **IBM Spectrum Protect Plus on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **Servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di IBM Spectrum Protect Plus on IBM Cloud per un'istanza esistente

Puoi aggiungere il servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi servizio**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **Servizio IBM Spectrum Protect Plus on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

## Configurazione del servizio IBM Spectrum Protect Plus on IBM Cloud

Quando ordini il servizio, fornisci le seguenti impostazioni.

### Numero di volumi di storage

Il numero di volumi che soddisfano le tue esigenze di archiviazione.

### Dimensione storage per volume

La capacità di archiviazione per ogni volume. Per la gestione, è richiesto un minimo di 500 GB per volume.

### Prestazioni Storage

L'IOPS (Input/output Operations Per Second) per GB in base ai tuoi requisiti del carico di lavoro.
* Se vuoi ordinare le licenze per IBM Spectrum Protect Plus, specifica il **Numero di VM per cui acquisire una Licenza** nella scheda **Ordina licenze**. È richiesto un minimo di 10 VM per la gestione delle licenze.
* Se vuoi utilizzare l'opzione BYOL (Bring Your Own License), fai clic sulla scheda **Licenze IBM Spectrum Protect Plus** e quindi su **Aggiungi file di licenza** per caricare i file di licenza di IBM Spectrum Protect Plus di tua proprietà.

## Processo di distribuzione per IBM Spectrum Protect Plus on IBM Cloud

La distribuzione di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} è automatizzata. Sia che tu scelga di ordinare un'istanza con questo servizio incluso o di distribuire il servizio nella tua istanza in un secondo momento, i seguenti passi sono completati dal processo di automazione {{site.data.keyword.vmwaresolutions_short}}:

1. Ordina l'archiviazione NFS Endurance dall'infrastruttura {{site.data.keyword.cloud_notm}} per il repository di backup di IBM Spectrum Protect Plus in base agli input dell'utente.
2. Ordina un numero specifico di licenze per IBM Spectrum Protect Plus dall'infrastruttura {{site.data.keyword.cloud_notm}} in base agli input dell'utente. Le licenze sono ordinate in incrementi di 10 pacchetti di licenze VM, in base al numero di VM che l'utente specifica per la licenza al momento dell'ordine del servizio IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. Se l'utente sceglie di portare una licenza IBM Spectrum Protect Plus esistente, non viene effettuato alcun ordine di licenza dall'infrastruttura {{site.data.keyword.cloud_notm}}.
3. Monta tutta l'archiviazione NFS ordinata per questo servizio su tutti i server ESXi nel cluster predefinito dell'istanza, inclusa l'aggiunta di rotte statiche corrette su ciascun server ESXi alla sottorete privata dell'archiviazione.
4. Crea archivi dati NFS in vCenter Server per tutti i volumi di archiviazione NFS montati sui server ESXi.
5. Distribuisci, attiva e configura la macchina virtuale IBM Spectrum Protect Plus nel cluster predefinito dell'istanza.
6. Collega tutta l'archiviazione NFS ordinata per questo servizio alla macchina virtuale IBM Spectrum Protect Plus e configura il repository di backup.
7. Registra il nome host e l'indirizzo IP della macchina virtuale IBM Spectrum Protect Plus con il server DNS dell'istanza.
8. (Per le istanze della V2.3 e successive) Crea un lavoro di backup di gestione predefinito in IBM Spectrum Protect Plus. Per ulteriori informazioni, vedi [Gestione di IBM Spectrum Protect Plus on IBM Cloud](managingspp.html).

## Link correlati

* [Panoramica di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](spp_considerations.html)
* [IBM Spectrum Protect Plus on IBM Cloud Preventive Service Planning](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [Gestione di IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [Documentazione di IBM Spectrum Protect Plus](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)

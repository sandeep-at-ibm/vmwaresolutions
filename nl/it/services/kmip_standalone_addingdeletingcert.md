---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aggiunta, visualizzazione ed eliminazione di certificati per le istanze KMIP for VMware on IBM Cloud

Una volta che la tua istanza KMIP for VMware on {{site.data.keyword.cloud}} è pronta, devi aggiungere i certificati. Quando non hai più bisogno di un certificato, eliminalo dalla tua istanza.

## Procedura per aggiungere i certificati alle istanze KMIP for VMware on IBM Cloud

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** dal riquadro di navigazione a sinistra.
2. Scorri fino alla tabella **Istanze KMIP for VMware on IBM Cloud** e fai clic sull'istanza per la quale vuoi aggiungere i certificati.
3. Fai clic su **Aggiungi**.
4. Nella finestra **Aggiungi certificato SSL del client**, immetti il nome e il contenuto del certificato.

   Il nome del certificato non può essere riutilizzato all'interno della tua istanza selezionata. Il contenuto del certificato deve essere valido e contenere le tag BEGIN CERTIFICATE ed END CERTIFICATE e il certificato non può essere riutilizzato nella regione selezionata in cui è distribuita l'istanza.
   {:note}
5. Fai clic su **Aggiungi**.

## Procedura per visualizzare i certificati per le istanze KMIP for VMware on IBM Cloud

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** dal riquadro di navigazione a sinistra.
2. Scorri fino alla tabella **Istanze KMIP for VMware on IBM Cloud** e fai clic sull'istanza per la quale visualizzare i certificati.
3. Visualizza l'elenco dei certificati aggiunti sotto la sezione **Certificati SSL del client**.
4. Per visualizzare il contenuto di un particolare certificato, fai clic su **Scarica**.

## Procedura per eliminare i certificati dalle istanze KMIP for VMware on IBM Cloud

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Istanze distribuite** dal riquadro di navigazione a sinistra.
2. Scorri fino alla tabella **Istanze KMIP for VMware on IBM Cloud** e fai clic sull'istanza dalla quale vuoi eliminare i certificati.
3. Nella tabella **Certificati SSL del client**, individua il certificato che vuoi eliminare e fai clic sull'icona **Elimina**.

   Il client perde immediatamente l'accesso a tutte le chiavi per scopi di crittografia e decrittografia dei dati o di backup dei dati. Affinché il client possa ottenere nuovamente l'accesso, devi aggiungere di nuovo il certificato SSL del client.
   {:note}

### Link correlati

* [Visualizzazione delle istanze KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [Ordine di istanze KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html)
* [Eliminazione di istanze KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Eventi di Activity Tracker](/docs/services/vmwaresolutions/vmonic/at-events.html)

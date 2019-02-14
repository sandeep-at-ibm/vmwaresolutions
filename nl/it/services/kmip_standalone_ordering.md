---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# Ordine di istanze KMIP for VMware on IBM Cloud

Puoi ordinare un'istanza KMIP for VMware on {{site.data.keyword.cloud}} senza associarla ad alcuna istanza VMware per una gestione flessibile del servizio e delle istanze.

## Prima di iniziare

Assicurati di aver completato le seguenti attività:
*  Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Hai esaminato tutte le considerazioni in [Considerazioni sull'istallazione delle istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html).

## Ordine di istanze KMIP for VMware on IBM Cloud

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Introduzione** dal riquadro di navigazione a sinistra.
2. Nell'area **Ordina servizi aggiuntivi**, fai clic su **KMIP for VMware on IBM Cloud**.
3. Nella pagina **KMIP for VMware on IBM Cloud**, configura le impostazioni del servizio come necessario.
4. Fai clic su **Fornitura**.

## Configurazione del servizio KMIP for VMware on IBM Cloud

Quando ordini questo servizio, fornisci le seguenti impostazioni:

### Nome istanza

Specifica un nome per la tua istanza KMIP for VMware {{site.data.keyword.cloud_notm}}.

### Regione servizio

Seleziona la regione {{site.data.keyword.cloud_notm}} in cui dovrà essere ospitata la tua istanza KMIP for VMware {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} mantiene un endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} altamente disponibile in ciascuna regione in cui il servizio è disponibile.

Tabella 1. Regioni degli endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Regione         | Endpoint               |
|:---------------|:-----------------------|
| Germania        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokyo          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Stati Uniti Sud       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### Chiave API per ID servizio

Immetti la chiave API per l'ID del servizio {{site.data.keyword.cloud_notm}} utilizzato per accedere all'istanza del servizio IBM Key Protect.

### Istanza Key Protect

Fai clic su **Recupera** per ottenere l'elenco delle istanze del servizio IBM Key Protect disponibili e seleziona quella da utilizzare per la gestione delle chiavi.

### Chiave root del cliente

Fai clic su **Recupera** per ottenere la chiave root del cliente memorizzata nella tua istanza IBM Key Protect selezionata.

## Risultati

L'ordine dell'istanza si avvia automaticamente. Riceverai la conferma che l'ordine è in fase di elaborazione e puoi controllare lo stato dell'ordine visualizzando i dettagli dell'istanza.

Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Installato** e ricevi una notifica via email.

## Operazioni successive

Aggiungi i certificati client per l'istanza KMIP for VMware on {{site.data.keyword.cloud_notm}} che hai ordinato. Per ulteriori informazioni, vedi [Aggiunta, visualizzazione ed eliminazione di certificati per le istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html).

### Link correlati

* [Visualizzazione delle istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [Eliminazione di istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Eventi di Activity Tracker](/docs/services/vmwaresolutions/vmonic/at-events.html)

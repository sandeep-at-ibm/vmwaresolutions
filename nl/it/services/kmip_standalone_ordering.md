---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

# Ordine di istanze KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering}

Puoi ordinare un'istanza KMIP for VMware on {{site.data.keyword.cloud}} senza associarla ad alcuna istanza VMware per una gestione flessibile del servizio e delle istanze.

## Prima di iniziare
{: #kmip_standalone_ordering-req}

Assicurati di aver completato le seguenti attività:
* Hai configurato le credenziali dell'infrastruttura {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni**. Per ulteriori informazioni, vedi [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Hai esaminato tutte le considerazioni in [Considerazioni sull'installazione delle istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install).

## Procedura per ordinare le istanze KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering-procedure}

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Introduzione** dal riquadro di navigazione a sinistra.
2. Nell'area **Ordina servizi aggiuntivi**, fai clic su **KMIP for VMware on IBM Cloud**.
3. Nella pagina **KMIP for VMware on IBM Cloud**, configura le impostazioni del servizio come necessario.
4. Fai clic su **Fornitura**.

## Configurazione del servizio KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering-config}

Quando ordini questo servizio, fornisci le seguenti impostazioni:

### Nome istanza
{: #kmip_standalone_ordering-config-instance-name}

Specifica un nome per la tua istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}.

### Regione servizio
{: #kmip_standalone_ordering-config-service-region}

Seleziona la regione {{site.data.keyword.cloud_notm}} in cui dovrà essere ospitata la tua istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} mantiene un endpoint del servizio di rete KMIP for VMware on {{site.data.keyword.cloud_notm}} altamente disponibile in ciascuna regione in cui il servizio è disponibile.

Tabella 1. Regioni degli endpoint del servizio di rete KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Regione         | Endpoint               |
|:---------------|:-----------------------|
| Germania        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Sydney        |  <ul><li><code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokyo          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Regno Unito Sud| <ul><li><code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Stati Uniti Est| <ul><li><code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Stati Uniti Sud       | <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### Chiave API per ID servizio
{: #kmip_standalone_ordering-config-api-key}

Immetti la chiave API per l'ID del servizio {{site.data.keyword.cloud_notm}} utilizzato per accedere all'istanza del servizio di Key Protect o Hyper Protect Crypto Services.

### Istanza del gestore chiavi
{: #kmip_standalone_ordering-config-key-protect}

Fai clic su **Recupera** per ottenere l'elenco delle istanze del gestore chiavi disponibili e seleziona quella da utilizzare per la gestione delle chiavi. 

### Chiave root del cliente
{: #kmip_standalone_ordering-config-root-key}

Fai clic su **Recupera** per ottenere la chiave root del cliente archiviata nella tua istanza del gestore chiavi selezionata.

## Risultati
{: #kmip_standalone_ordering-results}

L'ordine dell'istanza KMIP for VMware on {{site.data.keyword.cloud_notm}} viene avviato automaticamente. Riceverai la conferma che l'ordine è in fase di elaborazione e puoi controllare lo stato dell'ordine visualizzando i dettagli dell'istanza.

Quando l'istanza è pronta per l'uso, lo stato dell'istanza viene modificato in **Installato** e ricevi una notifica via email.

## Operazioni successive
{: #kmip_standalone_ordering-next}

Aggiungi i certificati client per l'istanza KMIP for VMware on {{site.data.keyword.cloud_notm}} che hai ordinato. Per ulteriori informazioni, vedi [Aggiunta, visualizzazione ed eliminazione di certificati per le istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert).

## Link correlati
{: #kmip_standalone_ordering-related}

* [Visualizzazione delle istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Eliminazione di istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Eventi di Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)

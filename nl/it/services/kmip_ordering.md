---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# Ordine di KMIP for VMware on IBM Cloud

Puoi ordinare il servizio KMIP for VMware on {{site.data.keyword.cloud}} mentre ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di KMIP for VMware on IBM Cloud per una nuova istanza

Puoi ordinare una nuova istanza con KMIP for VMware on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **KMIP for VMware on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **KMIP for VMware on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di KMIP for VMware on IBM Cloud per un'istanza esistente

Puoi aggiungere il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **KMIP for VMware on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

## Configurazione del servizio KMIP for VMware on IBM Cloud

Quando ordini questo servizio, fornisci le seguenti impostazioni:

### Regione servizio

Seleziona la regione {{site.data.keyword.cloud_notm}} in cui dovrà essere ospitata la tua istanza del servizio KMIP for VMware {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} mantiene un endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} altamente disponibile in ciascuna regione in cui il servizio è disponibile.

### Certificato SSL del client

Per vCenter Server, devi configurare un cluster KMS (Key Management Server). L'endpoint nella tua regione selezionata si collega in modo sicuro al KMS tramite il certificato SSL del client. Vedi la seguente tabella per l'endpoint in ciascuna regione. Questi endpoint utilizzano certificati autofirmati che vengono gestiti dal team {{site.data.keyword.vmwaresolutions_short}}. L'impronta digitale per i certificati è `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Tabella 1. Regioni degli endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Regione         | Endpoint               |
|:---------------|:-----------------------|
| Germania        |  `161.156.68.107:5696` |
| Sydney         |  `130.198.73.134:5696` |
| Regno Unito |  `158.175.93.122:5696` |
| Stati Uniti Sud       |  `169.60.185.42:5696`  |

Questa impostazione è facoltativa al momento della configurazione iniziale. Puoi lasciare vuoto questo campo perché il certificato client del KMS in vCenter Server è noto dopo la distribuzione dell'istanza. Tuttavia, devi immettere il certificato dopo che la tua istanza viene distribuita in modo che la connessione di vCenter Server al KMS possa essere completata correttamente.

### Chiave API per ID servizio

Immetti la chiave API per l'ID del servizio {{site.data.keyword.cloud_notm}} utilizzato per accedere all'istanza del servizio IBM Key Protect.

### Istanza Key Protect

Fai clic su **Recupera** per ottenere l'elenco delle istanze del servizio IBM Key Protect disponibili e seleziona quella da utilizzare per la gestione delle chiavi.

### Chiave root del cliente

Fai clic su **Recupera** per ottenere la chiave root del cliente memorizzata nella tua istanza IBM Key Protect selezionata.



### Link correlati

* [Panoramica di KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_considerations.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Domande frequenti](../vmonic/faq.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)

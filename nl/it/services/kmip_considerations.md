---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Panoramica di KMIP for VMware on IBM Cloud

Il servizio KMIP for VMware on {{site.data.keyword.cloud}} fornisce un servizio altamente disponibile 24x7 per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Questo servizio offre funzionalità di runtime per consentire ai clienti di creare, recuperare, attivare, revocare e distruggere le chiavi di crittografia e fornisce inoltre funzionalità di gestione per mantenere le associazioni tra le credenziali del client e quelle chiavi di crittografia.

**Disponibilità**: questo servizio è disponibile solo per le istanze distribuite nelle release della V2.2 o successive.

## Considerazioni sull'istallazione di KMIP for VMware on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} utilizza il servizio IBM Key Protect for IBM Cloud per creare, crittografare e decrittografare le chiavi di crittografia. Pertanto, prima di installare il servizio, assicurati di aver ordinato un servizio Key Protect utilizzabile. Nel frattempo, è stato creato un ID del servizio {{site.data.keyword.cloud_notm}} seguendo la procedura in [Creazione di un ID servizio](https://console.bluemix.net/docs/iam/serviceid.html#creating-a-service-id) per accedere all'istanza del servizio Key Protect che hai creato.

Assicurati di concedere i seguenti livelli di accesso per l'ID servizio:
* A livello di accesso alla piattaforma: autorizzazione di Visualizzatore nella tua istanza IBM Key Protect.
* A livello di accesso al servizio: autorizzazione di Scrittore nella tua istanza IBM Key Protect.

La chiave API per l'ID servizio creato è richiesta quando ordini il servizio.

Il servizio presuppone che tu abbia già creato almeno una chiave root del cliente (CRK) dall'interfaccia utente di Key Protect seguendo la procedura in [Creazione delle chiavi root](https://console.bluemix.net/docs/services/keymgmt/keyprotect_create_root.html#create_root_keys) o utilizzando l'API RESTful in [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect).

Non puoi ordinare il servizio senza le CRK. Si consiglia vivamente di utilizzare il metodo per creare una CRK utilizzando materiale della chiave esistente ed eseguire il backup del materiale della chiave che stai creando. In questo modo, garantisci di poter recuperare le tue chiavi in caso di un errore totale del data center in cui viene applicato IBM Key Protect per memorizzare le tue CRK.

## Considerazioni sull'utilizzo di KMIP for VMware on IBM Cloud

* Per utilizzare un servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} ordinato come KMS (Key Management Server) registrato su VMware vCenter Server, devi assicurarti che le configurazioni siano applicate in modo che la connettività di rete da vCenter Server all'endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} ordinato sia funzionale.
* Per utilizzare il servizio per la crittografia VMware vSAN, devi assicurarti che la connettività di rete tra gli host sul vSAN di destinazione e l'endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} ordinato sia funzionale.


## Considerazioni sulla rimozione di KMIP for VMware on IBM Cloud

Il certificato pubblico VMware che hai fornito durante l'ordine o l'utilizzo del servizio viene usato come certificato client per comunicare con l'istanza del servizio. Quando il servizio viene rimosso, tutte le chiavi di crittografia create da questa istanza del servizio per il certificato pubblico VMware associato vengono rimosse insieme.

Pertanto, prima di rimuovere il servizio, devi assicurarti che nessuna macchina virtuale o vSAN venga crittografata utilizzando le chiavi create dal servizio KMIP.

## Link correlati

* [Ordine di KMIP for VMware on IBM Cloud](kmip_ordering.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/services/keymgmt/index.html#getting-started-with-key-protect)
* [IBM Key Protect](https://console.bluemix.net/apidocs/639-ibm-key-protect?&language=javascript_jquery#introduction)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Domande frequenti](../vmonic/faq.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)

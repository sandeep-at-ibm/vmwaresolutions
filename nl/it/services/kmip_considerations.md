---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Panoramica di KMIP for VMware on IBM Cloud - Obsoleto
{: #kmip_considerations}

La versione corrente di KMIP for VMware on IBM Cloud è obsoleta. Per ulteriori informazioni, [contatta il supporto IBM](../vmonic/trbl_support.html).
{:deprecated}

Il servizio KMIP for VMware on {{site.data.keyword.cloud}} fornisce un servizio altamente disponibile 24x7 per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Questo servizio offre funzionalità di runtime per consentire ai clienti di creare, recuperare, attivare, revocare e distruggere le chiavi di crittografia. Fornisce inoltre funzionalità di gestione per mantenere le associazioni tra le credenziali del client e le chiavi di crittografia.

## Specifiche tecniche per KMIP for VMware on IBM Cloud
{: #kmip_considerations-specs}

Con il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} sono incluse le seguenti specifiche:

* Un KMIP (Key Management Interoperability Protocol) compatibile con VMware
* Un servizio gestito
* Disponibile in più regioni geografiche in tutto il mondo
* Un endpoint del servizio KMIP altamente disponibile in ogni regione

## Considerazioni sull'istallazione di KMIP for VMware on IBM Cloud
{: #kmip_considerations-install}

KMIP for VMware on {{site.data.keyword.cloud_notm}} utilizza il servizio IBM Key Protect for {{site.data.keyword.cloud_notm}} per creare, crittografare e decrittografare le chiavi di crittografia. Pertanto, prima di installare KMIP for VMware on {{site.data.keyword.cloud_notm}}, assicurati che:
* Hai ordinato un servizio Key Protect utilizzabile.
* È stato creato un ID servizio {{site.data.keyword.cloud_notm}} seguendo la procedura in [Creazione di un ID servizio](../../../iam/serviceid.html). Questo ID servizio viene utilizzato per accedere all'istanza del servizio Key Protect che hai creato.
* Hai concesso i seguenti livelli di accesso per l'ID servizio:
   * A livello di accesso alla piattaforma: autorizzazione di Visualizzatore nella tua istanza IBM Key Protect.
   * A livello di accesso al servizio: autorizzazione di Scrittore nella tua istanza IBM Key Protect.
* Hai una chiave API per l'ID servizio creato. La chiave viene richiesta quando ordini il servizio.
* Hai creato almeno una chiave root del cliente (CRK) dall'interfaccia utente di Key Protect seguendo la procedura in [Creazione delle chiavi root](../../keymgmt/keyprotect_create_root.html) o utilizzando l'API REST in [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect).

   **Importante:** non puoi ordinare il servizio senza le CRK. Si consiglia vivamente di utilizzare il metodo per creare una CRK utilizzando materiale della chiave esistente ed eseguire il backup del materiale della chiave che stai creando. In questo modo, garantisci di poter recuperare le tue chiavi in caso di un errore del data center in cui viene applicato IBM Key Protect per memorizzare le tue CRK.

## Considerazioni sull'utilizzo di KMIP for VMware on IBM Cloud
{: #kmip_considerations-use}

* Per utilizzare un servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} ordinato come KMS (Key Management Server) registrato su VMware vCenter Server, assicurati che la connettività di rete da vCenter Server all'endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} ordinato sia funzionale.
* Per utilizzare il servizio con la crittografia VMware vSAN, assicurati che la connettività di rete tra gli host sul vSAN di destinazione e l'endpoint del servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} ordinato sia funzionale.
* Quando utilizzi KMIP for VMware con la crittografia VMware, il controllo di integrità vSAN può emettere delle avvertenze periodiche in cui attesta di non potersi connettere al cluster KMS da uno o più dei tuoi host vSphere. Queste avvertenze si verificano perché la connessione del controllo di integrità vSAN va in timeout troppo velocemente. Puoi ignorare queste avvertenze.

## Considerazioni sulla rimozione di KMIP for VMware on IBM Cloud
{: #kmip_considerations-remove}

Il certificato pubblico VMware che hai fornito durante l'ordine o l'utilizzo del servizio viene usato come certificato client per comunicare con l'istanza del servizio. Quando il servizio viene rimosso, vengono rimosse anche tutte le chiavi di crittografia che sono state create da questa istanza del servizio per il certificato pubblico VMware associato.

Pertanto, prima di rimuovere il servizio, assicurati che non venga crittografata alcuna macchina virtuale o vSAN utilizzando le chiavi create dal servizio KMIP.

## Link correlati
{: #kmip_considerations-related}

* [Ordine di KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_ordering.html)
* [Eventi di {{site.data.keyword.cloudaccesstrailshort}}](../vmonic/at-events.html)
* [IBM Key Protect for {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [vSphere Security](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Domande frequenti](../vmonic/faq.html)
* [Come contattare il supporto IBM](../vmonic/trbl_support.html)

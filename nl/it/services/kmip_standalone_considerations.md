---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

Il servizio KMIP for VMware on {{site.data.keyword.cloud}} fornisce un servizio altamente disponibile 24x7 per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Questo servizio offre funzionalità di runtime per consentire ai clienti di creare, recuperare, attivare, revocare e distruggere le chiavi di crittografia. Fornisce inoltre funzionalità di gestione per mantenere le associazioni tra le credenziali del client e le chiavi di crittografia.

Il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} è disponibile come servizio autonomo senza essere associato a un'istanza VMware. Ogni istanza del servizio può servire una o più istanze Cloud Foundation, istanze vCenter Server o cluster vSphere.

## Specifiche tecniche per KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

Con il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} sono incluse le seguenti specifiche:

* Un KMIP (Key Management Interoperability Protocol) compatibile con VMware
* Un servizio gestito
* Disponibile in più regioni geografiche in tutto il mondo
* Due endpoint del servizio KMIP forniti in ciascuna regione per l'alta disponibilità

## Considerazioni sull'istallazione delle istanze KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations-install}

Esamina le seguenti considerazioni prima di installare un'istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} utilizza il servizio IBM Key Protect for {{site.data.keyword.cloud_notm}} per creare, crittografare e decrittografare le chiavi di crittografia. Pertanto, prima di installare KMIP for VMware on {{site.data.keyword.cloud_notm}}, assicurati che:
   * Hai ordinato un servizio Key Protect nella regione {{site.data.keyword.cloud_notm}} in cui dovrà essere ospitata la tua istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Provisioning del servizio](/docs/services/key-protect?topic=key-protect-provision).
   * È stato creato un ID servizio {{site.data.keyword.cloud_notm}} seguendo la procedura in [Creazione di un ID servizio](/docs/iam?topic=iam-serviceids). Questo ID servizio viene utilizzato per accedere all'istanza del servizio Key Protect che hai creato.
   * Hai concesso i seguenti livelli di accesso per l'ID servizio:
      * A livello di accesso alla piattaforma: autorizzazione di Visualizzatore nella tua istanza IBM Key Protect
      * A livello di accesso al servizio: autorizzazione di Gestore nella tua istanza IBM Key Protect
   * Hai una chiave API per l'ID servizio creato. La chiave viene richiesta quando ordini il servizio.
   * Hai creato almeno una chiave root del cliente (CRK) dall'interfaccia utente di Key Protect seguendo la procedura in [Creazione delle chiavi root](/docs/services/keymgmt/keyprotect_create_root.html) o utilizzando l'API REST in [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect).

     **Importante:** non puoi ordinare il servizio senza le CRK. Si consiglia vivamente di utilizzare il metodo per creare una CRK utilizzando materiale della chiave esistente ed eseguire il backup del materiale della chiave che stai creando. In questo modo, garantisci di poter recuperare le tue chiavi in caso di un errore del data center in cui viene applicato IBM Key Protect per memorizzare le tue CRK.
* Assicurati che il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} sia abilitato per VRF (Virtual Routing and Forwarding) e per la connettività agli endpoint del servizio. Per ulteriori informazioni, vedi:
   * [Panoramica di VRF (Virtual Routing and Forwarding) su IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Abilitazione del tuo account per l'utilizzo degli endpoint del servizio utilizzando la CLI IBM Cloud](/docs/services/service-endpoint?topic=services/service-endpoint-getting-started#getting-started)
* Poiché è supportata solo la connessione privata, non è necessario configurare alcuna regola firewall o SNAT in vCenter Server per la connettività di rete da vCenter Server all'endpoint dell'istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni, vedi [Architettura della soluzione KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview).

## Considerazioni sull'eliminazione delle istanze KMIP for VMware on IBM Cloud
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

Tutti i dati protetti dal servizio KMIP for VMware on IBM Cloud, inclusi i backup crittografati, non possono essere decrittografati dopo aver rimosso il servizio.

## Link correlati
{: #kmip_standalone_considerations-related}

* [Ordine di istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [Aggiunta, visualizzazione ed eliminazione di certificati per le istanze KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [Visualizzazione delle istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Eliminazione di istanze KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Eventi di Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

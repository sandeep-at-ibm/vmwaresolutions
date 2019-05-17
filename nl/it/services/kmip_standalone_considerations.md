---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Panoramica di KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations}

Il servizio KMIP for VMware on {{site.data.keyword.cloud}} fornisce un servizio altamente disponibile 24x7 per gestire le chiavi di crittografia utilizzate da VMware in {{site.data.keyword.cloud_notm}}. Questo servizio offre funzionalità di runtime per consentire ai clienti di creare, recuperare, attivare, revocare e distruggere le chiavi di crittografia. Fornisce inoltre funzionalità di gestione per mantenere le associazioni tra le credenziali del client e le chiavi di crittografia.

Il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} è disponibile come servizio autonomo senza essere associato a un'istanza VMware. Ogni istanza del servizio può servire una o più istanze vCenter Server o uno o più cluster vSphere. 

## Specifiche tecniche per KMIP for VMware on IBM Cloud
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

Con il servizio KMIP for VMware on {{site.data.keyword.cloud_notm}} sono incluse le seguenti specifiche:

* Un KMIP (Key Management Interoperability Protocol) compatibile con VMware
* Due servizi gestiti: [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/catalog/services/key-protect) e [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services)
* Disponibile in più regioni geografiche in tutto il mondo
* Due endpoint del servizio di rete KMIP forniti in ciascuna regione per l'alta disponibilità

## Considerazioni sull'installazione delle istanze KMIP for VMware on IBM Cloud
{: #kmip_standalone_considerations-install}

Esamina le seguenti considerazioni prima di installare un'istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}:

* KMIP for VMware on {{site.data.keyword.cloud_notm}} utilizza il servizio IBM Key Protect for {{site.data.keyword.cloud_notm}} (Key Protect) o il servizio {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services (HPCS) per creare, crittografare e decrittografare le chiavi di crittografia. Pertanto, prima di installare KMIP for VMware on {{site.data.keyword.cloud_notm}}, assicurati che:
   * Hai ordinato un'istanza del servizio Key Protect o HPCS utilizzabile nella regione {{site.data.keyword.cloud_notm}} in cui deve essere ospitata la tua istanza KMIP for VMware on {{site.data.keyword.cloud_notm}}:
      * Per ulteriori informazioni sulla creazione di un'istanza di Key Protect, vedi [Provisioning del servizio](/docs/services/key-protect?topic=key-protect-provision).
      * Per ulteriori informazioni sulla creazione di un'istanza di HPCS, vedi [Provisioning del servizio](/docs/services/hs-crypto?topic=hs-crypto-provision#provision). Oltre al provisioning del servizio HPCS, devi anche [inizializzare la tua istanza di crittografia](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm) in modo che HPCS possa fornire le funzioni correlate alla chiave.
   * È stato creato un ID servizio {{site.data.keyword.cloud_notm}} seguendo la procedura in [Creazione di un ID servizio](/docs/iam?topic=iam-serviceids). Questo ID servizio viene utilizzato per accedere all'istanza del servizio Key Protect o HPCS che hai creato. 
   * Hai concesso i seguenti livelli di accesso per l'ID servizio:
      * A livello di accesso alla piattaforma: autorizzazione di Visualizzatore nella tua istanza del servizio Key Protect o HPCS
      * A livello di accesso al servizio: autorizzazione di Gestore nella tua istanza del servizio Key Protect o HPCS
   * Hai una chiave API per l'ID servizio creato. La chiave viene richiesta quando ordini il servizio.
   * Hai creato almeno una chiave root del cliente (CRK) utilizzando la GUI o l'API di Key Protect o HPCS:
      * Per ulteriori informazioni sulla creazione delle chiavi root con la GUI o l'API di Key Protect, vedi [Creazione delle chiavi root](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) o [IBM Key Protect API](https://cloud.ibm.com/apidocs/key-protect).
      * Per ulteriori informazioni sulla creazione di chiavi root con la GUI o l'API di HPCS, vedi [Creazione delle chiavi root](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys) o [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hp-crypto).

     **Importante:** non puoi ordinare il servizio senza le CRK. Si consiglia vivamente di utilizzare il metodo per creare una CRK utilizzando materiale della chiave esistente ed eseguire il backup del materiale della chiave che stai creando. In questo modo, ti assicuri di poter recuperare le tue chiavi in caso di malfunzionamento del data center in cui viene applicato Key Protect o HPCS per memorizzare le tue CRK.
* Assicurati che il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} sia abilitato per VRF (Virtual Routing and Forwarding) e per la connettività agli endpoint del servizio. Per ulteriori informazioni, vedi:
   * [Panoramica di VRF (Virtual Routing and Forwarding) su IBM Cloud](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [Abilitazione del tuo account per l'utilizzo degli endpoint del servizio utilizzando la CLI IBM Cloud](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)
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

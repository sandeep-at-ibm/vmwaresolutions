---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# Ordine di IBM Cloud Private Hosted
{: #icp_ordering}

Puoi ordinare il servizio {{site.data.keyword.cloud}} Private Hosted quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di IBM Cloud Private Hosted per una nuova istanza
{: #icp_ordering-new}

Puoi ordinare una nuova istanza con il servizio {{site.data.keyword.cloud_notm}} Private Hosted utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **IBM Cloud Private Hosted** nella sezione **Servizi facoltativi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **IBM Cloud Private Hosted**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di IBM Cloud Private Hosted per un'istanza esistente
{: #icp_ordering-existing}

Puoi aggiungere il servizio {{site.data.keyword.cloud_notm}} Private Hosted in un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **IBM Cloud Private Hosted**, specifica le impostazioni del servizio e seleziona **Aggiungi a un'istanza esistente**.

## Configurazione del servizio IBM Cloud Private Hosted
{: #icp_ordering-config}

Quando ordini il servizio, fornisci le seguenti impostazioni:
* Seleziona **Pronto per la produzione** o **Sviluppo/Test** in base alle tue esigenze.
* Seleziona la casella di spunta richiesta per certificare che hai già ottenuto la licenza richiesta per distribuire il servizio {{site.data.keyword.cloud_notm}} Private Hosted.

## Distribuzione di nodi aggiuntivi
{: #icp_ordering-deploy-nodes}

Se vuoi distribuire dei nodi aggiuntivi, esamina le seguenti informazioni:
* Utilizza il modello {{site.data.keyword.cloud_notm}} Private Ubuntu (Ubuntu1604) distribuito con la tua installazione iniziale di {{site.data.keyword.cloud_notm}} Private Hosted.
* Per trovare il modello Ubuntu, nel client web VMware vSphere, vai alla scheda **VMs and Templates**, nella cartella `cam`.
* La password predefinita per il modello Ubuntu è `icponcloud`. Ti consigliamo di modificare questa password prima di utilizzare il modello.
* {{site.data.keyword.vmwaresolutions_short}} non offre supporto per l'applicazione di aggiornamenti e patch per il modello Ubuntu. Devi monitorare e applicare autonomamente questi aggiornamenti.

## Link correlati
{: #icp_ordering-related}

* [Panoramica su IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Ordine, visualizzazione e rimozione dei servizi per le istanze vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

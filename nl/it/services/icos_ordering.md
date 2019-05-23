---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordinazione e configurazione di IBM Cloud Object Storage con Veeam
{: #icos_ordering}

Con la release di Veeam Availability Suite 9.5 Update 4, Veeam è compatibile con IBM Cloud Object Storage (ICOS). L'ordinazione di IBM Cloud Object Storage non è automatizzata quando ordini Veeam su IBM Cloud, ma può essere aggiunto dopo la distribuzione.

Per ordinare IBM Cloud Object Storage, completa le seguenti attività nell'ordine specificato.

## Creazione di un'istanza Object Storage
{: #icos_ordering-obj}

Per creare un'istanza Object Storage, vedi [Creazione di una nuova istanza del servizio](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance). Segui le istruzioni e ritorna in questa sezione per continuare con le attività seguenti.

## Creazione di un bucket
{: #icos_ordering-bucket}

Per creare un bucket, vedi [Create some buckets to store your data](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets). Segui le istruzioni e ritorna in questa sezione per continuare con le attività seguenti.

## Creazione delle credenziali del sevizio
{: #icos_ordering-service-cred}

Per creare le credenziali del servizio, incluse le credenziali HMAC, vedi [Credenziali del servizio](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Segui le istruzioni e ritorna in questa sezione per continuare con le attività seguenti.

## Aggiunta di un repository di ridimensionamento incrementale
{: #icos_ordering-scale-repo}

Per aggiungere un repository di ridimensionamento incrementale in Veeam, vedi [Adding scale-Out repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}. Segui le istruzioni e ritorna in questa sezione per continuare con le attività seguenti.

## Manutenzione e gestione del tuo livello cloud
{: #icos_ordering-manage-cloud}

Per informazioni sulla manutenzione e gestione del tuo livello cloud, vedi [Managing capacity tier data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}.

## Link correlati
{: #icos_ordering-related}

* [Panoramica di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Ordine di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestione di Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Richiesta di servizi gestiti per Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

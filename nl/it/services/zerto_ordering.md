---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di Zerto on IBM Cloud
{: #zerto_ordering}

Puoi ordinare il servizio Zerto on {{site.data.keyword.cloud}} quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Ordine di Zerto on IBM Cloud per una nuova istanza
{: #zerto_ordering-new}

Puoi ordinare una nuova istanza con Zerto on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **Zerto on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **Zerto on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di Zerto on IBM Cloud per un'istanza esistente
{: #zerto_ordering-existing}

Puoi aggiungere il servizio Zerto on {{site.data.keyword.cloud_notm}} a un'istanza esistente utilizzando uno dei seguenti metodi: 
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza per la quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, seleziona **Zerto on IBM Cloud**, specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

Se aggiungi Zerto for {{site.data.keyword.cloud_notm}} a un'istanza vCenter Server che ha un server ESXi che è in modalità di manutenzione, devi utilizzare la console ZVM (Zerto Virtual Manager) e l'indirizzo IP VRA (Virtual Replication Appliance) Zerto precompilato per distribuire manualmente la VM (Virtual Machine) VRA.
{:note}

## Ordine di Zerto on IBM Cloud per le istanze solo private
{: #zerto_ordering-private-only}

Se vuoi aggiungere Zerto on {{site.data.keyword.cloud_notm}} a un'istanza solo privata, assicurati che vengano soddisfatti i seguenti requisiti:
* Sei responsabile della configurazione del tuo server proxy per collegarti a internet. Per ulteriori informazioni, vedi [Connettività di rete pubblica](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Devi anche configurare la funzione Call Home per Zerto. Per ulteriori informazioni sulla funzione Call Home di Zerto, vedi [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:new_window}.

## Link correlati
{: #zerto_ordering-related}

* [Panoramica di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Richiesta di servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sito web zerto.com](https://www.zerto.com){:new_window}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

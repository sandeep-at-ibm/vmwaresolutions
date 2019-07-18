---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Zerto, Zerto replication billing, order Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordine di Zerto on IBM Cloud
{: #zerto_ordering}

Puoi ordinare il servizio Zerto on {{site.data.keyword.cloud}} quando ordini una nuova istanza con il servizio incluso o aggiungendo il servizio alla tua istanza esistente.

## Fatturazione per la replica Zerto
{: #zerto_ordering-billing}

Le VM che vengono replicate utilizzando Zerto sono misurate da Zerto e {{site.data.keyword.cloud_notm}}. La tua fattura per questo utilizzo viene addebitata mediante un account fatturabile {{site.data.keyword.cloud_notm}} invece di un account dell'infrastruttura {{site.data.keyword.cloud_notm}}.

Prima di ordinare Zerto on {{site.data.keyword.cloud_notm}}, assicurati che il tuo account {{site.data.keyword.cloud_notm}} sia un account fatturabile e che sia collegato allo stesso account dell'infrastruttura {{site.data.keyword.cloud_notm}} dove è distribuita la tua istanza.

Se hai un'installazione di Zerto on {{site.data.keyword.cloud_notm}} dalla V3.0 o antecedente, i tuoi costi di replica di VM continuano a essere fatturati utilizzando la fatturazione dell'infrastruttura {{site.data.keyword.cloud_notm}}. Se i tuoi account e le tue impostazioni di fatturazione soddisfano i requisiti elencati in precedenza, puoi convertire il tuo metodo di fatturazione in fatturabile.

Nella console {{site.data.keyword.vmwaresolutions_short}}, ti viene richiesto di eseguire la conversione dal piano dell'infrastruttura {{site.data.keyword.cloud_notm}} a un piano fatturabile e di eseguire l'upgrade del tuo account {{site.data.keyword.cloud_notm}} a un account fatturabile, se necessario.

* Per informazioni sugli account gratuiti e fatturabili, vedi [Tipi di account](/docs/account?topic=account-accounts).
* Per informazioni sull'esecuzione dell'upgrade a un account fatturabile, vedi [Upgrade del tuo account](/docs/account?topic=account-upgrading-account).
* Per informazioni sul collegamento del tuo {{site.data.keyword.cloud_notm}} e dei tuoi account dell'infrastruttura {{site.data.keyword.cloud_notm}}, vedi [Passaggio all'ID IBM e collegamento degli account](/docs/account?topic=account-unifyingaccounts).

## Ordine di Zerto on IBM Cloud per una nuova istanza
{: #zerto_ordering-new}

Puoi ordinare una nuova istanza con Zerto on {{site.data.keyword.cloud_notm}} utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, quando ordini una nuova istanza, seleziona **Zerto on IBM Cloud** nella sezione **Servizi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic sull'icona **VMware** nel riquadro di navigazione a sinistra e quindi sulla scheda **Zerto on IBM Cloud** nella sezione **VMware Services**. Specifica le impostazioni del servizio e seleziona **Aggiungi alla nuova istanza**.

## Ordine di Zerto on IBM Cloud per un'istanza esistente
{: #zerto_ordering-existing}

Puoi aggiungere il servizio Zerto on {{site.data.keyword.cloud_notm}} a un'istanza esistente utilizzando uno dei seguenti metodi:
* Dalla console {{site.data.keyword.vmwaresolutions_short}}, visualizza l'istanza alla quale vuoi aggiungere il servizio, fai clic su **Servizi** nel riquadro di navigazione a sinistra e quindi su **Aggiungi**.
* Dal catalogo {{site.data.keyword.cloud_notm}}, fai clic sull'icona **VMware** nel riquadro di navigazione a sinistra e quindi sulla scheda **Zerto on IBM Cloud** nella sezione **VMware Services**. Specifica le impostazioni del servizio e seleziona **Aggiungi all'istanza esistente**.

Se aggiungi Zerto on {{site.data.keyword.cloud_notm}} a un'istanza vCenter Server che ha un server ESXi che è in modalità di manutenzione, devi utilizzare la console ZVM (Zerto Virtual Manager) e l'indirizzo IP VRA (Virtual Replication Appliance) Zerto precompilato per distribuire manualmente la VM (Virtual Machine) VRA.
{:note}

## Ordine di Zerto on IBM Cloud per le istanze solo private
{: #zerto_ordering-private-only}

Se vuoi aggiungere Zerto on {{site.data.keyword.cloud_notm}} a un'istanza solo privata, assicurati che vengano soddisfatti i seguenti requisiti:
* Sei responsabile della configurazione del tuo server proxy per collegarti a internet. Per ulteriori informazioni, vedi [Connettività di rete pubblica](/docs/services/vmwaresolutions/services?topic=vmware-solutions-design_virtualinfrastructure#public-network-connectivity).
* Devi anche configurare la funzione Call Home per Zerto. Per ulteriori informazioni sulla funzione Call Home di Zerto, vedi [Zerto Reporting for Enterprise environments (Call Home)](https://www.zerto.com/myzerto/knowledge-base/zerto-reporting-for-enterprise-environments-call-home/){:external}.

## Link correlati
{: #zerto_ordering-related}

* [Panoramica di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Gestione di Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Servizi gestiti per Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [Sito web zerto.com](https://www.zerto.com){:external}
* [Documentazione tecnica di Zerto](https://www.zerto.com/myzerto/technical-documentation/){:external}

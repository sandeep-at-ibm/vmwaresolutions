---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# Gestione di account utente e impostazioni

{{site.data.keyword.vmwaresolutions_full}} comunica con l'infrastruttura {{site.data.keyword.cloud_notm}} attraverso chiamate {{site.data.keyword.slapi_short}}. Per accedere a {{site.data.keyword.slapi_short}} in modo sicuro, devi collegare le credenziali del tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) al tuo account {{site.data.keyword.cloud_notm}}.

**Nota:** l'account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) era precedentemente noto come account IBM SoftLayer.

Puoi anche specificare se vuoi ricevere notifiche via e-mail o via console per i vari eventi.

## Prima di iniziare

* Puoi collegare un solo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) a un account utente {{site.data.keyword.cloud_notm}}.
* L'account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).
* Se la chiave API per il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) cambia, devi aggiornare la chiave nella pagina **Impostazioni** nella console {{site.data.keyword.vmwaresolutions_short}}.

   **Importante:** è tua responsabilità garantire che la chiave API salvata nella pagina **Impostazioni** sia corretta e aggiornata. Altrimenti, le operazioni che richiedono la convalida della chiave API potrebbero non riuscire.

## Procedura per gestire account utente e impostazioni

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Impostazioni** dal riquadro di navigazione a sinistra.
2. Nell'area **Notifiche**, specifica le impostazioni di notifica.
   * Se vuoi ricevere una notifica via e-mail quando si verificano degli eventi, fai clic su **Abilita notifiche via e-mail**.
   * Se vuoi ricevere una notifica tramite la console quando si verificano degli eventi, fai clic su **Abilita notifiche via console**.
3. Nell'area **Credenziali infrastruttura IBM Cloud**, immetti il nome utente e la chiave API del tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer):
   * Se il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) e il tuo account {{site.data.keyword.cloud_notm}} sono collegati, fai clic su **Recupera** per immettere le credenziali automaticamente.
   * Se il tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) e il tuo account {{site.data.keyword.cloud_notm}} non sono collegati, devi collegarli. Accedi al [portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}}](https://control.softlayer.com/) e segui le istruzioni sulla console per ottenere le credenziali, quindi immettile.
   * Se non disponi di un account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer), [registrane uno](../vmonic/signing_softlayer_account.html) e segui le istruzioni sulla console per ottenere le credenziali, quindi immettile.
4. Fai clic su **Salva credenziali**.

## Risultati

Dopo aver collegato l'account {{site.data.keyword.cloud_notm}} e l'account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer), la console recupera automaticamente le credenziali dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) per comunicare con il tuo ambiente VMware su {{site.data.keyword.cloud_notm}}.

Le credenziali dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}} (SoftLayer) memorizzate vengono utilizzata nelle operazioni future che richiedono l'interazione con l'infrastruttura {{site.data.keyword.cloud_notm}}.

Se sono state abilitate le notifiche via e-mail o console per determinati eventi dell'istanza, verrai avvisato tramite messaggi e-mail o di console quando si verificano questi eventi.

### Link correlati

* [Domande frequenti](faq.html)
* [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)
* [Notifiche](notifications.html)
* [API SoftLayer](../../../customer-portal/cpapi.html){:new_window}

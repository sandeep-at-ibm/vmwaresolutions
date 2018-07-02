---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# Gestione di account utente e impostazioni

{{site.data.keyword.vmwaresolutions_full}} comunica con l'infrastruttura {{site.data.keyword.cloud_notm}} attraverso chiamate {{site.data.keyword.slapi_short}}. Per accedere a {{site.data.keyword.slapi_short}} in modo sicuro, devi associare le credenziali del tuo account {{site.data.keyword.cloud_notm}} al tuo account utente {{site.data.keyword.vmwaresolutions_short}}.

**Nota**: l'account {{site.data.keyword.cloud_notm}} era precedentemente noto come account IBM SoftLayer.

Nella console {{site.data.keyword.vmwaresolutions_short}}, puoi anche specificare se desideri ricevere notifiche e-mail per i vari eventi.

## Prima di iniziare

* Puoi associare un solo account {{site.data.keyword.cloud_notm}} al tuo account utente {{site.data.keyword.vmwaresolutions_short}}.
* L'account {{site.data.keyword.cloud_notm}} che utilizzi deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti dell'account {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).
* Se la chiave API del tuo account {{site.data.keyword.cloud_notm}} cambia, devi aggiornare la chiave nel tuo account utente {{site.data.keyword.vmwaresolutions_short}}.

   **Importante**: è tua responsabilità garantire che la chiave API salvata nella pagina **Impostazioni** sia corretta e aggiornata.
   Altrimenti, le operazioni che richiedono la convalida della chiave API potrebbero non riuscire.

Per associare l'account {{site.data.keyword.vmwaresolutions_short}} all'account {{site.data.keyword.cloud_notm}}, immetti le credenziali dell'account {{site.data.keyword.cloud_notm}} nella pagina **Impostazioni** della console {{site.data.keyword.vmwaresolutions_short}}.

Dopo aver associato l'account {{site.data.keyword.cloud_notm}}, la console recupera automaticamente le credenziali dell'account {{site.data.keyword.cloud_notm}} per comunicare con il tuo ambiente VMware su {{site.data.keyword.cloud_notm}}.

## Procedura

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Impostazioni** nel riquadro di navigazione a sinistra.
2. Se vuoi ricevere una notifica via e-mail quando si verificano nuovi eventi, seleziona la casella di spunta **Abilita notifiche via e-mail**.
3. Se vuoi ricevere una notifica tramite la console quando si verificano nuovi eventi, seleziona la casella di spunta **Abilita notifiche via console**.
4. Nell'area **Credenziali infrastruttura IBM Cloud**, immetti il nome utente del tuo account {{site.data.keyword.cloud_notm}} e quindi segui le istruzioni sulla console per immettere la chiave {{site.data.keyword.slapi_short}}.
5. Fai clic su **Salva credenziali**.

## Risultati

Le credenziali dell'account {{site.data.keyword.cloud_notm}} memorizzate vengono utilizzata nelle operazioni future che richiedono l'interazione con l'infrastruttura {{site.data.keyword.cloud_notm}}. Se sono state abilitate le notifiche via e-mail o console per determinati eventi dell'istanza, verrai avvisato tramite messaggi e-mail o di console quando questi eventi si verificano.

## Link correlati

* [Domande frequenti](faq.html)
* [Ordine di istanze Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Ordine di istanze vCenter Server](../vcenter/vc_orderinginstance.html)
* [Notifiche](notifications.html)
* [API SoftLayer](../../../customer-portal/cpapi.html){:new_window}

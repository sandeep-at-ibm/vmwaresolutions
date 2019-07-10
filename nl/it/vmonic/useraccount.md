---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: set credentials, user credentials, set notifications

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestione di account utente e impostazioni
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} comunica con l'infrastruttura {{site.data.keyword.cloud_notm}} attraverso chiamate {{site.data.keyword.slapi_short}}. Per accedere a {{site.data.keyword.slapi_short}} in modo sicuro, devi collegare le credenziali del tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} al tuo account {{site.data.keyword.cloud_notm}}.

Puoi anche specificare se vuoi ricevere notifiche via e-mail o via console per i vari eventi.

## Prima di iniziare
{: #useraccount-reqs}

* Puoi collegare solo un account dell'infrastruttura {{site.data.keyword.cloud_notm}} a un account utente {{site.data.keyword.cloud_notm}}.
* L'account dell'infrastruttura {{site.data.keyword.cloud_notm}} che stai utilizzando deve soddisfare determinati requisiti. Per ulteriori informazioni, vedi [Requisiti dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).
* Se la chiave API del tuo account dell'infrastruttura {{site.data.keyword.cloud_notm}} cambia, devi aggiornare la chiave nella pagina **Impostazioni** nella console {{site.data.keyword.vmwaresolutions_short}}.

   È tua responsabilità garantire che la chiave API salvata nella pagina **Impostazioni** sia corretta e aggiornata. Altrimenti, le operazioni che richiedono la convalida della chiave API potrebbero non riuscire.
   {:important}

## Procedura per impostare le notifiche
{: #useraccount-set-notif}

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Impostazioni** dal riquadro di navigazione a sinistra.
2. Se vuoi ricevere una notifica via e-mail quando si verificano degli eventi, fai clic su **Abilita notifiche via e-mail**.
3. Se vuoi ricevere una notifica tramite la console quando si verificano degli eventi, fai clic su **Abilita notifiche via console**.

## Procedura per impostare le credenziali dell'account utente
{: #useraccount-set-cred}

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Impostazioni** dal riquadro di navigazione a sinistra.
2. Nell'area **Credenziali infrastruttura IBM Cloud**, esamina le informazioni per la procedura che devi eseguire.
3. Se hai sia un account dell'infrastruttura {{site.data.keyword.cloud_notm}} che un account {{site.data.keyword.cloud_notm}} collegati, fai clic su **Richiama** per completare le credenziali automaticamente. 
4. Se hai sia un account dell'infrastruttura {{site.data.keyword.cloud_notm}} che un account {{site.data.keyword.cloud_notm}} che non sono collegati, devi collegarli. Attieniti alle istruzioni contenute in [Collegamento di account ID IBM](/docs/account?topic=account-unifyingaccounts#link_accounts) e fai quindi clic su **Richiama** per completare le credenziali automaticamente.
5. Se non hai un account dell'infrastruttura {{site.data.keyword.cloud_notm}} e non hai un account {{site.data.keyword.cloud_notm}} fatturabile, prima [esegui l'upgrade del tuo account](/docs/account?topic=account-upgrading-account) e quindi [crea una chiave API dell'infrastruttura classica](/docs/iam?topic=iam-classic_keys).
6. Se non hai un account dell'infrastruttura {{site.data.keyword.cloud_notm}} e hai un account {{site.data.keyword.cloud_notm}} fatturabile, devi [creare una chiave API dell'infrastruttura classica](/docs/iam?topic=iam-classic_keys).
7. Fai clic su **Salva credenziali**.

## Risultati
{: #useraccount-results}

Dopo aver collegato l'account {{site.data.keyword.cloud_notm}} e l'account dell'infrastruttura {{site.data.keyword.cloud_notm}}, la console recupera automaticamente le credenziali dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}} per comunicare con il tuo ambiente VMware su {{site.data.keyword.cloud_notm}}.

Le credenziali dell'account dell'infrastruttura {{site.data.keyword.cloud_notm}} memorizzate vengono utilizzate nelle operazioni future che richiedono l'interazione con l'infrastruttura {{site.data.keyword.cloud_notm}}.

Se sono state abilitate le notifiche via e-mail o console per determinati eventi dell'istanza, verrai avvisato tramite messaggi e-mail o di console quando si verificano questi eventi.

## Link correlati
{: #useraccount-related}

* [Domande frequenti](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Notifiche](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [API SoftLayer](/docs/customer-portal?topic=customer-portal-customerportal_api)

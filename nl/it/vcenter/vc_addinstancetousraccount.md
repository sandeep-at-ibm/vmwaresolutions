---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

# Migrazione di istanze vCenter Server precedenti alla V2.5 agli account IBM Cloud
{: #vc_addinstancetousraccount}

Le istanze VMware vCenter Server che sono state distribuite nelle release della V2.5 e successive nel tuo account {{site.data.keyword.cloud}} vengono aggiunte automaticamente al tuo account e gestite da {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

Le istanze che sono state distribuite nelle release della V2.4 e precedenti, possono essere migrate ad account {{site.data.keyword.cloud_notm}} specificati per la gestione utente abilitata a IAM.

## Prima di iniziare
{: #vc_addinstancetousraccount-prereq}

Assicurati che l'account {{site.data.keyword.cloud_notm}} a cui vuoi migrare l'istanza non sia un account solo IaaS. Un account solo IaaS è un account dell'infrastruttura {{site.data.keyword.cloud_notm}} che non è collegato a un account {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni su come collegare il tuo account solo IaaS al tuo account PaaS, vedi [Follow these steps to link your IaaS and PaaS accounts](https://www.ibm.com/cloud/blog/follow-steps-link-iaas-paas-accounts){:new_window}.

## Procedura per migrare le istanze
{: #vc_addinstancetousraccount-procedure}

1. Nella console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** dal riquadro di navigazione a sinistra.
2. Dal banner della console, fai clic sull'icona del tuo account utente e quindi sul campo **Account** per selezionare l'account utente in cui vuoi migrare l'istanza.
3. Nella tabella **Istanze vCenter Server**, trova l'istanza precedente alla V2.5.
4. Nella colonna **Azioni**, fai clic sull'icona del menu di overflow e seleziona **Migra istanza nell'account**.
5. Nella finestra **Migra istanza nell'account**, conferma l'account a cui migrare l'istanza e fai clic su **Migra**.

### Risultati
{: #vc_addinstancetousraccount-results}

1. Viene visualizzata una notifica della console che indica che la richiesta di migrazione dell'istanza all'account {{site.data.keyword.cloud_notm}} specificato è stata accettata.
2. Al termine della migrazione dell'istanza, questa viene visualizzata nella pagina **Risorse** nell'account a cui è stata migrata. L'istanza migrata non viene più visualizzata nell'account originale dal quale è stata migrata.

## Link correlati
{: #vc_addinstancetousraccount-related}

* [Gestione dell'accesso utente con IAM](/docs/services/vmwaresolutions/services?topic=vmware-solutions-iam#iam)
* [Come invitare gli utenti ad accedere a servizi e risorse](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Cos'è IBM Cloud IAM](/docs/iam?topic=iam-iamoverview)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

# Come invitare gli utenti ad accedere a servizi e risorse
{: #iamuserinvite}

{{site.data.keyword.vmwaresolutions_full}} è integrato con {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) per la collaborazione tra più utenti. Dopo aver registrato un account {{site.data.keyword.cloud_notm}} ed eseguito l'accesso alla console {{site.data.keyword.vmwaresolutions_short}}, puoi aggiungere utenti all'account {{site.data.keyword.cloud_notm}}. Questi utenti aggiunti possono condividere i servizi e le risorse forniti per l'account.

## Prima di iniziare
{: #iamuserinvite-reqs}

* Assicurati di essere il proprietario dell'account o che il tuo ruolo di gestione della piattaforma per il servizio **VMware Solutions** sia **Amministratore**.
* Assicurati di aver esaminato i ruoli e le autorizzazioni utente in [Gestione dell'accesso utente con Identity and Access Management](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam).

## Procedura per invitare gli utenti ad accedere a servizi e risorse
{: #iamuserinvite-procedure}

1. Sul lato sinistro del banner, fai clic su **Gestisci > Sicurezza > Identità e accesso**.
2. Nella pagina **Utenti**, fai clic su **Invita utenti**.
3. Nella sezione **Utenti** della pagina **Invita utenti**, immetti l'indirizzo e-mail degli utenti che vuoi invitare nel campo **Indirizzo email**.
4. Nella sezione **Accesso**, espandi **Servizi** e completa quindi le seguenti attività:
   1. Seleziona **Risorsa** dall'elenco **Assegna accesso a**.
   2. Seleziona **VMware Solutions** dall'elenco **Servizi**.
   3. Seleziona il ruolo di accesso alla piattaforma che vuoi assegnare agli utenti. Può essere **Amministratore**, **Editor**, **Operatore** o **Visualizzatore**.
5. Fai clic su **Invita utenti**.

## Risultati
{: #iamuserinvite-results}

Dopo che gli utenti aggiunti hanno accettato il tuo invito, possono accedere alla console {{site.data.keyword.vmwaresolutions_short}} e passare al tuo account. Per farlo, nelle impostazioni del loro profilo, gli utenti fanno clic sull'icona del proprio account utente nel banner della console {{site.data.keyword.vmwaresolutions_short}}. Quindi, gli utenti aggiunti possono collaborare e condividere i servizi e le risorse disponibili nel tuo account specificato.

## Link correlati
{: #iamuserinvite-related}

* [Invito di utenti e assegnazione dell'accesso](/docs/iam?topic=iam-iamuserinv)
* [Gestione di identità e accesso](/docs/iam?topic=iam-getstarted)
* [Invito di utenti](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [Cos'è IAM](/docs/iam?topic=iam-iamoverview)
* [Migrazione di istanze vCenter Server precedenti alla V2.5 agli account IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [Migrazione di istanze vCenter Server with Hybridity Bundle precedenti alla V2.5 agli account IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [Migrazione di istanze NetApp ONTAP Select precedenti alla V2.5 agli account IBM Cloud](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

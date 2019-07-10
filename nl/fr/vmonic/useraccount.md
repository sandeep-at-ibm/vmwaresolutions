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

# Gestion des paramètres et comptes utilisateur
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} communique avec l'infrastructure {{site.data.keyword.cloud_notm}} via des appels {{site.data.keyword.slapi_short}}. Pour accéder en toute sécurité à {{site.data.keyword.slapi_short}}, vous devez associer les données d'identification de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} à votre compte {{site.data.keyword.cloud_notm}}.

Vous pouvez également indiquer si vous voulez recevoir des notifications par courrier électronique et par console concernant divers événements.

## Avant de commencer
{: #useraccount-reqs}

* Vous ne pouvez lier qu'un seul compte d'infrastructure {{site.data.keyword.cloud_notm}} à un compte utilisateur {{site.data.keyword.cloud_notm}}.
* Le compte d'infrastructure {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences concernant le compte d'infrastructure {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).
* Si la clé d'API de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} change, vous devez mettre à jour la clé sur la page **Paramètres** de la console {{site.data.keyword.vmwaresolutions_short}}.

   Il vous incombe de vérifier que la clé d'API sauvegardée sur la page **Paramètres** est correcte et à jour. Sinon, les opérations qui nécessitent la clé d'API risquent d'échouer.
   {:important}

## Procédure de définition des notifications
{: #useraccount-set-notif}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Paramètres** dans le panneau de navigation de gauche.
2. Si vous voulez être prévenu par courrier électronique de la survenue d'événements, cliquez sur **Activer les notifications par courrier électronique**.
3. Si vous voulez être prévenu sur la console de la survenue d'événements, cliquez sur **Activer les notifications par console**.

## Procédure de définition des données d'identification de compte d'utilisateur 
{: #useraccount-set-cred}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Paramètres** dans le panneau de navigation de gauche.
2. Dans la zone **Données d'identification d'infrastructure IBM Cloud**, examinez les informations relatives aux étapes à suivre. 
3. Si vous disposez d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} et d'un compte {{site.data.keyword.cloud_notm}} liés, cliquez sur **Extraire** pour compléter automatiquement les données d'identification.
4. Si vous disposez d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} et d'un compte {{site.data.keyword.cloud_notm}} qui ne sont pas liés, vous devez les lier. Suivez les instructions de la section [Liaison des comptes IBMid](/docs/account?topic=account-unifyingaccounts#link_accounts), puis cliquez sur **Extraire** pour compléter les données d'identification automatiquement. 
5. Si vous ne possédez pas de compte d'infrastructure {{site.data.keyword.cloud_notm}} et si vous ne possédez pas de compte {{site.data.keyword.cloud_notm}} facturable, [mettez d'abord à niveau votre compte](/docs/account?topic=account-upgrading-account), puis [créez une clé d'API d'infrastructure classique](/docs/iam?topic=iam-classic_keys).
6. Si vous ne possédez pas de compte d'infrastructure {{site.data.keyword.cloud_notm}} et si vous possédez un compte {{site.data.keyword.cloud_notm}} facturable, vous devez [créer une clé d'API d'infrastructure classique](/docs/iam?topic=iam-classic_keys).
7. Cliquez sur **Sauvegarder les données d'identification**.

## Résultats
{: #useraccount-results}

Une fois que le compte {{site.data.keyword.cloud_notm}} et le compte d'infrastructure {{site.data.keyword.cloud_notm}} sont liés, la console extrait automatiquement les données d'identification du compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) pour communiquer avec votre environnement VMware sur {{site.data.keyword.cloud_notm}}.

Les données d'identification stockées pour le compte d'infrastructure {{site.data.keyword.cloud_notm}} sont utilisées dans les opérations ultérieures qui nécessitent une interaction avec l'infrastructure {{site.data.keyword.cloud_notm}}.

Si les notifications par courrier électronique ou sur la console sont activées pour certains événements d'instance, des messages par courrier électronique ou sur la console vous aviseront lorsque ces événements se produisent.

## Liens connexes
{: #useraccount-related}

* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Notifications](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [API SoftLayer](/docs/customer-portal?topic=customer-portal-customerportal_api)

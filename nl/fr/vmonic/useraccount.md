---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gestion des paramètres et comptes utilisateur
{: #useraccount}

{{site.data.keyword.vmwaresolutions_full}} communique avec l'infrastructure {{site.data.keyword.cloud_notm}} via des appels {{site.data.keyword.slapi_short}}. Pour accéder en toute sécurité à {{site.data.keyword.slapi_short}}, vous devez associer les données d'identification de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) à votre compte {{site.data.keyword.cloud_notm}}.

Auparavant, le compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) était appelé compte IBM SoftLayer.
{:note}

Vous pouvez également indiquer si vous voulez recevoir des notifications par courrier électronique et par console concernant divers événements.

## Avant de commencer
{: #useraccount-reqs}

* Vous ne pouvez lier qu'un seul compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) à un compte utilisateur {{site.data.keyword.cloud_notm}}.
* Le compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences concernant le compte d'infrastructure {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).
* Si la clé d'API de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) change, vous devez mettre à jour la clé sur la page **Paramètres** de la console {{site.data.keyword.vmwaresolutions_short}}.

   **Important :** il vous incombe de vérifier que la clé d'API sauvegardée sur la page **Paramètres** est correcte et à jour. Sinon, les opérations qui nécessitent la clé d'API risquent d'échouer.

## Procédure à utiliser pour gérer les paramètres et les comptes utilisateur
{: #useraccount-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Paramètres** dans le panneau de navigation de gauche.
2. Dans la zone **Notifications**, spécifiez vos paramètres de notification.
   * Si vous voulez être prévenu par courrier électronique de la survenue d'événements, cliquez sur **Activer les notifications par courrier électronique**.
   * Si vous voulez être prévenu sur la console de la survenue d'événements, cliquez sur **Activer les notifications par console**.
3. Dans la zone **Données d'identification d'infrastructure IBM Cloud**, entrez le nom d'utilisateur et la clé d'API de votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) :
   * Si votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) et votre compte {{site.data.keyword.cloud_notm}} sont liés, cliquez sur **Extraire** pour activer la saisie automatique des données d'identification.
   * Si ce n'est déjà fait, vous devez lier votre compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) et votre compte {{site.data.keyword.cloud_notm}}. Connectez-vous au [portail client de l'infrastructure {{site.data.keyword.cloud_notm}}](https://control.softlayer.com/) et suivez les instructions sur la console pour obtenir les données d'identification, puis entrez ces informations.
   * Si vous ne disposez pas d'un compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer), [souscrivez à un compte](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account) et suivez les instructions sur la console pour obtenir les données d'identification, puis entrez ces informations.
4. Cliquez sur **Sauvegarder les données d'identification**.

## Résultats
{: #useraccount-results}

Une fois que le compte {{site.data.keyword.cloud_notm}} et le compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) sont liés, la console extrait automatiquement les données d'identification du compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) pour communiquer avec votre environnement VMware sur {{site.data.keyword.cloud_notm}}.

Les données d'identification stockées pour le compte d'infrastructure {{site.data.keyword.cloud_notm}} (SoftLayer) sont utilisées dans les opérations ultérieures qui nécessitent une interaction avec l'infrastructure {{site.data.keyword.cloud_notm}}.

Si les notifications par courrier électronique ou sur la console sont activées pour certains événements d'instance, des messages par courrier électronique ou sur la console vous aviseront lorsque ces événements se produisent.

## Liens connexes
{: #useraccount-related}

* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Notifications](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [API SoftLayer](/docs/customer-portal?topic=customer-portal-customerportal_api){:new_window}

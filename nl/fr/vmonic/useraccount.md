---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# Gestion des paramètres et comptes utilisateur

{{site.data.keyword.vmwaresolutions_full}} communique avec l'infrastructure {{site.data.keyword.cloud_notm}} via des appels {{site.data.keyword.slapi_short}}. Pour accéder en toute sécurité à {{site.data.keyword.slapi_short}}, vous devez associer les données d'identification de votre compte {{site.data.keyword.cloud_notm}} à votre compte utilisateur {{site.data.keyword.vmwaresolutions_short}}.

**Remarque** : le compte {{site.data.keyword.cloud_notm}} était précédemment nommé compte IBM SoftLayer.

Sur la console {{site.data.keyword.vmwaresolutions_short}}, vous pouvez également indiquer si vous voulez recevoir des notifications par courrier électronique concernant divers événements.

## Avant de commencer

* Vous ne pouvez associer qu'un seul compte {{site.data.keyword.cloud_notm}} à votre compte utilisateur {{site.data.keyword.vmwaresolutions_short}}.
* Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).
* Si la clé d'API de votre compte {{site.data.keyword.cloud_notm}} change, vous devez mettre à jour la clé dans votre compte utilisateur {{site.data.keyword.vmwaresolutions_short}}.

   **Important** : il vous incombe de vérifier que la clé d'API enregistrée sur la page **Paramètres** est correcte et à jour.
   Sinon, les opérations qui nécessitent la clé d'API risquent d'échouer.

Pour associer le compte {{site.data.keyword.vmwaresolutions_short}} au compte {{site.data.keyword.cloud_notm}}, entrez les identifiants du compte {{site.data.keyword.cloud_notm}} sur la page **Paramètres** de la console {{site.data.keyword.vmwaresolutions_short}}.

Une fois le compte {{site.data.keyword.cloud_notm}} associé, la console extrait automatiquement les identifiants du compte {{site.data.keyword.cloud_notm}} pour communiquer avec votre environnement VMware sur {{site.data.keyword.cloud_notm}}.

## Procédure

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Paramètres** dans le panneau de navigation de gauche.
2. Si vous voulez être prévenu par courrier électronique de la survenue de nouveaux événements, cochez la case **Activer les notifications par courrier électronique**.
3. Si vous voulez être prévenu sur la console de la survenue de nouveaux événements, cochez la case **Activer les notifications par console**.
4. Dans la zone **Données d'identification d'infrastructure IBM Cloud**, entrez le nom d'utilisateur de votre compte {{site.data.keyword.cloud_notm}}, puis suivez les instructions affichées sur la console pour entrer la clé {{site.data.keyword.slapi_short}}.
5. Cliquez sur **Sauvegarder les données d'identification**.

## Résultats

Les identifiants stockés du compte {{site.data.keyword.cloud_notm}} sont utilisés dans les opérations ultérieures qui nécessitent une interaction avec l'infrastructure {{site.data.keyword.cloud_notm}}. Si les notifications par courrier électronique ou sur la console pour certains événements d'instance, vous recevez des messages par courrier électronique ou sur la console lorsque ces événements se produisent.

## Liens connexes

* [Foire aux questions](faq.html)
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Notifications](notifications.html)
* [API SoftLayer](../../../customer-portal/cpapi.html){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# Commande des instances KMIP for VMware on IBM Cloud

Vous pouvez commander une instance KMIP for VMware on {{site.data.keyword.cloud}} sans l'associer à une instance VMware pour une gestion flexible du service et des instances.

## Avant de commencer

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Vous avez passé en revue toutes les remarques énoncées dans la rubrique [Remarques relatives à l'installation des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html).

## Commande des instances KMIP for VMware on IBM Cloud

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Initiation** dans le panneau de navigation de gauche.
2. Dans la zone **Commander des services supplémentaires**, cliquez sur **KMIP for VMware on IBM Cloud**.
3. Sur la page **KMIP for VMware on IBM Cloud**, configurez les paramètres de service comme il convient.
4. Cliquez sur **Mettre à disposition**.

## Configuration du service KMIP for VMware on IBM Cloud

Lorsque vous commandez ce service, indiquez les paramètres suivants :

### Nom d'instance

Indiquez un nom pour votre instance KMIP for VMware {{site.data.keyword.cloud_notm}}.

### Région de service

Sélectionnez la région {{site.data.keyword.cloud_notm}} où votre instance KMIP for VMware {{site.data.keyword.cloud_notm}} doit être hébergée.

{{site.data.keyword.cloud_notm}} gère un noeud final de service KMIP for VMware on {{site.data.keyword.cloud_notm}} à haute disponibilité dans chaque région où le service est disponible.

Tableau 1. Régions de noeud final de service KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Région         | Noeuds finaux               |
|:---------------|:-----------------------|
| Allemagne        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokyo          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Sud des Etats-Unis       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### Clé d'API pour ID de service

Entrez la clé d'API pour l'ID de service {{site.data.keyword.cloud_notm}} qui est utilisé afin d'accéder à l'instance de service IBM Key Protect.

### Instance Key Protect

Cliquez sur **Extraire** pour obtenir la liste d'instances de service IBM Key Protect disponibles et sélectionnez celle qui sera utilisée pour la gestion de clés.

### Clé racine de client

Cliquez sur **Extraire** pour obtenir la clé racine de client qui est stockée dans votre instance IBM Key Protect sélectionnée.

## Résultats

La commande de l'instance commence automatiquement. Vous recevez une confirmation que la commande est en cours de traitement et vous pouvez vérifier l'état de la commande en affichant les détails de l'instance.

Lorsque l'instance est prête pour utilisation, l'instance prend le statut **Installé** et vous recevez une notification par courrier électronique.

## Etape suivante

Ajoutez les certificats clients pour l'instance KMIP for VMware on {{site.data.keyword.cloud_notm}} que vous avez commandée. Pour plus d'informations, voir [Ajout, affichage et suppression de certificats pour des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html).

### Liens connexes

* [Affichage des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [Suppression des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Evénements du service Activity Tracker](/docs/services/vmwaresolutions/vmonic/at-events.html)

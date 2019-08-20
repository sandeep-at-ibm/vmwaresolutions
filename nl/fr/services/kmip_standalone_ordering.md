---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-21"

keywords: KMIP for VMware, order KMIP stand-alone, KMIP for VMware configuration

subcollection: vmware-solutions


---

# Commande des instances KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering}

Vous pouvez commander une instance KMIP for VMware on {{site.data.keyword.cloud}} sans l'associer à une instance VMware pour une gestion flexible du service et des instances.

## Avant de commencer
{: #kmip_standalone_ordering-req}

Assurez-vous que :
* Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* Vous avez passé en revue toutes les remarques énoncées dans la rubrique [Remarques relatives à l'installation d'instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install).

## Procédure de commande d'instances KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Initiation** dans le panneau de navigation de gauche.
2. Dans la section **Services VMware**, cliquez sur **KMIP for VMware on IBM Cloud**.
3. Sur la page **KMIP for VMware on IBM Cloud**, configurez les paramètres de service comme il convient.
4. Cliquez sur **Mettre à disposition**.

## Configuration du service KMIP for VMware on IBM Cloud
{: #kmip_standalone_ordering-config}

Lorsque vous commandez ce service, indiquez les paramètres suivants :

### Nom d'instance
{: #kmip_standalone_ordering-config-instance-name}

Indiquez un nom pour votre instance KMIP for VMware on {{site.data.keyword.cloud_notm}}.

### Emplacement de service
{: #kmip_standalone_ordering-config-service-region}

Sélectionnez l'emplacement {{site.data.keyword.cloud_notm}} où votre instance KMIP for VMware on {{site.data.keyword.cloud_notm}} doit être hébergée.

{{site.data.keyword.cloud_notm}} gère un noeud final de service de réseau KMIP for VMware on {{site.data.keyword.cloud_notm}} à haute disponibilité dans chaque emplacement où le service est disponible.

| Emplacement         | Noeuds finaux               |
|:---------------|:-----------------------|
| Dallas | <<code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code><br>et<br><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Francfort | <code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code><br>et<br><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code> |
| Londres | <code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code><br>et<br><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Sydney | <code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code><br>et<br><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code> |
| Tokyo | <code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code><br>et<br><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code> |
| Washington DC | <code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code><br>et<br><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code> |
{: caption="Tableau 1. Emplacements de noeud final de service de réseau KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

### Clé d'API pour ID de service
{: #kmip_standalone_ordering-config-api-key}

Entrez la clé d'API pour l'ID de service {{site.data.keyword.cloud_notm}} qui est utilisé pour accéder à l'instance de service de Key Protect ou Hyper Protect Crypto Services.

### Instance Key Manager
{: #kmip_standalone_ordering-config-key-protect}

Cliquez sur **Extraire** pour obtenir la liste des instances du gestionnaire de clés disponibles et sélectionnez celle qui sera utilisée pour la gestion de clés.

### Clé racine de client
{: #kmip_standalone_ordering-config-root-key}

Cliquez sur **Extraire** pour obtenir la clé racine de client qui est stockée dans votre instance de gestionnaire de clés sélectionnée.

## Résultats
{: #kmip_standalone_ordering-results}

La commande de l'instance KMIP for VMware on {{site.data.keyword.cloud_notm}} démarre automatiquement. Vous recevez une confirmation que la commande est en cours de traitement et vous pouvez vérifier l'état de la commande en affichant les détails de l'instance.

Lorsque l'instance est prête pour utilisation, l'instance prend le statut **Installé** et vous recevez une notification par courrier électronique.

## Etape suivante
{: #kmip_standalone_ordering-next}

Ajoutez les certificats clients pour l'instance KMIP for VMware on {{site.data.keyword.cloud_notm}} que vous avez commandée. Pour plus d'informations, voir [Ajout, affichage et suppression de certificats pour des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert).

## Liens connexes
{: #kmip_standalone_ordering-related}

* [Affichage des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Suppression des instances KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Evénements du service Activity Tracker](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)

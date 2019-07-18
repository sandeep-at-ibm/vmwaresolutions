---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande et configuration d'IBM Cloud Object Storage avec Veeam
{: #icos_ordering}

Avec l'édition Veeam Availability Suite 9.5 Update 4, Veeam est compatible avec IBM Cloud Object Storage (ICOS). La commande d'IBM Cloud Object Storage n'est pas automatique lors de la commande de Veeam on IBM Cloud, mais le produit peut être ajouté après le déploiement.

Pour commander IBM Cloud Object Storage, effectuez les opérations suivantes, dans l'ordre indiqué.

## Création d'une instance Object Storage
{: #icos_ordering-obj}

Pour créer une instance Object Storage, voir [Création d'une instance de service](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance). Suivez la procédure puis revenez à cette section pour passer aux autres tâches.

## Création d'un compartiment
{: #icos_ordering-bucket}

Pour créer un compartiment, voir [Création de compartiments pour stocker vos données](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets). Suivez la procédure puis revenez à cette section pour passer aux autres tâches.

## Création de données d'identification de service
{: #icos_ordering-service-cred}

Pour créer des données d'identification de service, y compris des données d'identification HMAC, voir [Données d'identification du service](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Suivez la procédure puis revenez à cette section pour passer aux autres tâches.

## Ajout d'un référentiel d'extension
{: #icos_ordering-scale-repo}

* Dans le cadre de l’installation et de la configuration du service Veeam, un référentiel de sauvegarde évolutif portant le nom `IC4V Scale-Out Repository` est créé. `IC4V Default VM Backup Repository` est ajouté au référentiel d'extension en tant qu'extension.
* Lorsque vous créez le travail de sauvegarde, vous devez sélectionner `IC4V Scale-Out Repository` comme référentiel de sauvegarde, et non `IC4V Default Config Backup Repository`. Ce dernier référentiel est destiné aux sauvegardes de configuration Veeam.
* Vous pouvez ajouter plusieurs référentiels à ce référentiel par défaut, tels qu'un référentiel de sauvegarde de type Object Storage. Pour plus d'informations, voir [Adding scale-Out repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:external}. Suivez la procédure puis revenez à cette section pour passer aux autres tâches.

## Maintenance et gestion de votre niveau de cloud
{: #icos_ordering-manage-cloud}

Pour plus d'informations, voir [Managing capacity tier data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:external}.

## Liens connexes
{: #icos_ordering-related}

* [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Commande de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Services gérés pour Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: Veeam, Veeam configuration, order Veeam

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de Veeam on IBM Cloud
{: #veeam_ordering}

Vous pouvez commander le service Veeam on {{site.data.keyword.cloud}} lors de la commande d'une nouvelle instance avec le service inclus ou en ajoutant le service à votre instance existante.

## Commande de Veeam on IBM Cloud pour une nouvelle instance
{: #veeam_ordering-new}

Vous pouvez commander une nouvelle instance avec Veeam on {{site.data.keyword.cloud_notm}} en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **Veeam on IBM Cloud** dans la section **Services**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis cliquez sur **Veeam on IBM Cloud** dans la section **Services VMware**. Spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande de Veeam on IBM Cloud pour une instance existante
{: #veeam_ordering-existing}

Vous pouvez ajouter le service Veeam on {{site.data.keyword.cloud_notm}} dans une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis cliquez sur **Veeam on IBM Cloud** dans la section **Services VMware**. Spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service Veeam on IBM Cloud
{: #veeam_ordering-config}

Lorsque vous commandez le service, indiquez les paramètres suivants :

### Nombre de machines virtuelles pour lesquelles concéder une licence
{: #veeam_ordering-config-vms}

Un minimum de 10 machines virtuelles est requis pour la gestion des licences.

### Taille de stockage
{: #veeam_ordering-config-storage-size}

Capacité répondant à vos besoins en matière de stockage. Pour toute question concernant l'estimation de la taille de l'espace de stockage, voir [Estimation de la capacité de référentiel](https://bp.veeam.expert/repository_server/repository_planning/repository_planning_sizing){:external}.

### Performances de stockage
{: #veeam_ordering-config-storage-performance}

Valeur IOPS (opérations d'entrée/sortie par seconde) par Go adaptée à vos besoins en matière de charge de travail.

## Liens connexes
{: #veeam_ordering-related}

* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Services gérés pour Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Site Web Veeam](https://www.veeam.com/){:external}
* [Centre d'information Veeam](https://www.veeam.com/documentation-guides-datasheets.html){:external}

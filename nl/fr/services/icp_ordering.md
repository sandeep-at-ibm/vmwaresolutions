---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: IBM Cloud Private Hosted, ICP configuration, order Cloud Private

subcollection: vmware-solutions


---

# Commande d'IBM Cloud Private Hosted
{: #icp_ordering}

Vous pouvez commander le service {{site.data.keyword.cloud}} Private Hosted lors de la commande d'une nouvelle instance avec le service inclus ou vous pouvez ajouter le service à votre instance existante.

## Commande d'IBM Cloud Private Hosted pour une nouvelle instance
{: #icp_ordering-new}

Vous pouvez commander une nouvelle instance avec le service {{site.data.keyword.cloud_notm}} Private Hosted inclus en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, lorsque vous commandez une nouvelle instance, sélectionnez **IBM Cloud Private Hosted** dans la section **Services facultatifs**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis cliquez sur **IBM Cloud Private Hosted** dans la section **Services VMware**. Spécifiez les paramètres de service et sélectionnez **Ajouter à une nouvelle instance**.

## Commande d'IBM Cloud Private Hosted pour une instance existante
{: #icp_ordering-existing}

Vous pouvez ajouter le service {{site.data.keyword.cloud_notm}} Private Hosted dans une instance existante en utilisant l'une des méthodes suivantes :
* Depuis la console {{site.data.keyword.vmwaresolutions_short}}, affichez l'instance pour laquelle vous souhaitez ajouter le service, cliquez sur **Services** dans le panneau de navigation de gauche, puis cliquez sur **Ajouter**.
* Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur l'icône **VMware** dans le panneau de navigation de gauche, puis cliquez sur **IBM Cloud Private Hosted** dans la section **Services VMware**. Spécifiez les paramètres de service et sélectionnez **Ajouter à une instance existante**.

## Configuration du service IBM Cloud Private Hosted
{: #icp_ordering-config}

Lorsque vous commandez le service, indiquez les paramètres suivants :
* Sélectionnez **Prêt pour la production** ou **Développement/Test** selon vos besoins.
* Cochez la case requise pour certifier que vous possédez déjà la licence qui est obligatoire pour déployer le service {{site.data.keyword.cloud_notm}} Private Hosted.

## Déploiement de noeuds supplémentaires
{: #icp_ordering-deploy-nodes}

Si vous souhaitez déployer des noeuds supplémentaires, passez en revue les informations suivantes :
* Utilisez le modèle {{site.data.keyword.cloud_notm}} Private Ubuntu (Ubuntu1604) qui est déployé avec votre installation {{site.data.keyword.cloud_notm}} Private Hosted initiale.
* Pour trouver le modèle Ubuntu, dans le client Web VMware vSphere, accédez à l'onglet **VMs and Templates**, sous le dossier `cam`.
* Le mot de passe par défaut du modèle Ubuntu est `icponcloud`. Il est recommandé de changer ce mot de passe avant d'utiliser le modèle.
* {{site.data.keyword.vmwaresolutions_short}} ne prend pas en charge l'application des mises à jour et correctifs pour les composants Ubuntu. Vous devez surveiller et appliquer ces mises à jour vous-même.

## Liens connexes
{: #icp_ordering-related}

* [Présentation d'IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

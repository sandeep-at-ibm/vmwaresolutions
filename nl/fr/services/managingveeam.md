---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Veeam console, Veeam backup restore, update Veeam license

subcollection: vmware-solutions


---

# Gestion de Veeam on IBM Cloud
{: #managingveeam}

Une fois le service déployé dans votre instance, vous pouvez accéder à la console Veeam à l'aide de RDP afin de gérer la sauvegarde et la restauration de toutes les machines virtuelles de votre environnement, y compris la sauvegarde et la restauration des composants de gestion. Vous pouvez également effectuer une mise à niveau du service en téléchargeant et en installant les mises à jour Veeam depuis le site Web Veeam.

Si vous voulez utiliser le service Veeam on {{site.data.keyword.cloud}} pour des instances déployées dans des éditions antérieures à la version 1.8, vous devez remplacer l'instance de serveur virtuel Veeam existante dans les instances. Pour plus d'informations, voir la section [Remplacement des instances de serveur virtuel Veeam antérieures à V1.8 par Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam#managingveeam-replace-vsi).

## Accès à la console Veeam à l'aide du protocole RDP
{: #managingveeam-accessing}

Pour gérer le service Veeam on {{site.data.keyword.cloud_notm}}, accédez à la console Veeam en procédant comme suit :
1. Utilisez le protocole RDP (Remote Desktop Protocol) pour vous connecter à l'adresse IP Windows.
2. Connectez-vous à la console Windows à l'aide des données d'identification d'administrateur.
3. Accédez à la console Veeam depuis la console Windows à l'aide des données d'identification d'administrateur.

Vous trouverez l'adresse IP Windows et les données d'identification d'administrateur sur la page des détails du service Veeam on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir[Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Sauvegarde et restauration de composants de gestion pour des instances sur lesquelles le service Veeam on IBM Cloud est installé
{: #managing-veeam-backup-and-replication}

Le service Veeam on {{site.data.keyword.cloud_notm}} peut être configuré pour sauvegarder les composants de gestion à l'aide de la console Veeam. Pour plus d'informations, voir [Sauvegarde des composants](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

Pour les instances déployées dans (ou mises à niveau vers) la version 1.8 ou des éditions ultérieures, les modifications de configuration que vous apportez à votre environnement ne sont pas sauvegardées automatiquement. Par conséquent, avant de modifier la configuration de votre environnement, nous vous recommandons d'effectuer une sauvegarde manuelle des composants de gestion en exécutant la tâche de sauvegarde de gestion dans la console Veeam. Pour plus d'informations sur l'exécution d'une tâche de sauvegarde manuelle, voir les [instructions techniques Veeam](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

En cas d'incidents sur les composants de gestion, vous pouvez les restaurer à partir d'une sauvegarde antérieure depuis la console Veeam. Pour plus d'informations sur l'exécution d'une tâche de restauration manuelle, voir les [instructions techniques Veeam]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Application de mises à jour à Veeam on IBM Cloud
{: #managingveeam-updates}

C'est à vous qu'il incombe de faire en sorte que le logiciel Veeam soit toujours utilisé dans sa version la plus récente.

### Application des mises à jour pour les instances déployées avec un réseau public ou privé
{: #managingveeam-updates-public-private}

Si le service Veeam est installé sur une instance avec un réseau public ou privé, vous pouvez rechercher et télécharger des mises à jour à l'aide du logiciel Veeam proprement dit.

### Application des mises à jour pour les instances déployées avec un réseau privé uniquement
{: #managingveeam-updates-private}

Si le service Veeam est installé sur une instance avec un réseau privé uniquement, dans la mesure où l'instance de serveur virtuel Veeam est configuré sans accès de réseau public, vous ne pouvez pas rechercher ou télécharger de mises à jour à l'aide du logiciel Veeam proprement dit. Au lieu de cela, vous devez télécharger des mises à jour à partir du site Web Veeam, les transférer vers la machine virtuelle Veeam, puis les installer.

## Mise à jour de licences Veeam
{: #managingveeam-update-license}

### Mise à jour des licences Veeam pour les instances déployées avec un réseau public ou privé
{: #managingveeam-update-license-public-private}

Si le service Veeam est installé sur une instance avec un réseau public et un réseau privé, vous pouvez mettre à jour votre licence Veeam automatiquement ou manuellement en suivant les instructions Veeam décrites dans [Updating license]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html).

### Mise à jour des licences Veeam pour les instances déployées avec un réseau privé uniquement
{: #managingveeam-update-license-private}

Si le service Veeam est installé sur une instance avec un réseau privé uniquement, vous devez noter la date d'expiration de votre licence et [contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) pour obtenir de l'aide relative à la mise à jour de la clé de licence lorsque le renouvellement est nécessaire.

## Remplacement des instances de serveur virtuel Veeam antérieures à V1.8 par Veeam on IBM Cloud
{: #managingveeam-replace-vsi}

Le service Veeam on {{site.data.keyword.cloud_notm}}, capable de sauvegarder aussi bien des composants de gestion que des charges de travail, remplace les instances de serveur virtuel Veeam précédentes intégrées à VMware vCenter Server dans les éditions antérieures à la version 1.8 uniquement pour les composants de sauvegarde et de gestion.

En raison de cette modification, l'onglet **Sauvegarde et restauration** de la page des détails de l'instance a été retiré et les points de sauvegarde des instances ne sont plus disponibles sur la console {{site.data.keyword.vmwaresolutions_short}}. Cela dit, l'instance de serveur virtuel Veeam des instances de version antérieure à 1.8 fonctionne toujours.

Vous devez créer un ticket de demande de service {{site.data.keyword.cloud_notm}} pour obtenir de l'aide concernant une restauration. De plus, la licence des instances de serveur virtuel Veeam antérieures à la version 1.8 a expiré le 14 octobre 2017. Par conséquent, vous devez remplacer l'ancienne instance de serveur virtuel Veeam par le nouveau service Veeam on {{site.data.keyword.cloud_notm}}.

Effectuez les opérations suivantes :
1. Sur la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche, puis cliquez sur l'instance cible.
2. Sur la page des détails de l'instance, cliquez sur l'onglet **Mise à jour et module de correction**. Assurez-vous que l'instance est au niveau de version 1.8.
3. Cliquez sur l'onglet **Services**.
4. Dans l'onglet **Ajouter des services**, installez le service Veeam on {{site.data.keyword.cloud_notm}}.

Une fois le nouveau service Veeam on {{site.data.keyword.cloud_notm}} déployé et une sauvegarde réussie de vos composants de gestion effectuée, vous pouvez supprimer de votre compte l'instance de serveur virtuel Veeam existante en créant un ticket de demande de service {{site.data.keyword.cloud_notm}}. Le support IBM identifie et supprime l'instance de serveur virtuel et le stockage Veeam existants.

## Liens connexes
{: #managingveeam-related}

* [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Site Web Veeam.com](https://www.veeam.com/)
* [Documentation technique Veeam](https://www.veeam.com/documentation-guides-datasheets.html)

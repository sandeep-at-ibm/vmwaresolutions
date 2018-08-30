---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-15"

---

# Gestion de Veeam on IBM Cloud

Une fois le service déployé dans votre instance, vous pouvez accéder à la console Veeam à l'aide de RDP afin de gérer la sauvegarde et la restauration de toutes les machines virtuelles de votre environnement, y compris la sauvegarde et la restauration des composants de gestion. Vous pouvez également effectuer une mise à niveau du service en téléchargeant et en installant les mises à jour Veeam depuis le site Web Veeam.

Si vous voulez utiliser le service Veeam on {{site.data.keyword.cloud}} pour des instances déployées dans des éditions antérieures à la version 1.8, vous devez remplacer l'instance de serveur virtuel Veeam existante dans les instances. Pour plus d'informations, voir la section _Remplacement des instances de serveur virtuel Veeam antérieures à V1.8 par Veeam on IBM Cloud_ dans cette rubrique.

## Accès à la console Veeam à l'aide du protocole RDP

Pour gérer le service Veeam on {{site.data.keyword.cloud_notm}}, accédez à la console Veeam en procédant comme suit :
1. Utilisez le protocole RDP (Remote Desktop Protocol) pour vous connecter à l'adresse IP Windows.
2. Connectez-vous à la console Windows à l'aide des données d'identification d'administrateur.
3. Accédez à la console Veeam depuis la console Windows à l'aide des données d'identification d'administrateur.

Vous trouverez l'adresse IP Windows et les données d'identification d'administrateur sur la page des détails du service Veeam on {{site.data.keyword.cloud_notm}}.

Pour plus d'informations, voir les rubriques suivantes :
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)

## Sauvegarde et restauration de composants de gestion pour des instances sur lesquelles le service Veeam on IBM Cloud est installé

Le service Veeam on {{site.data.keyword.cloud_notm}} peut être configuré pour sauvegarder les composants de gestion à l'aide de la console Veeam. Pour plus d'informations, voir [Sauvegarde des composants](../archiref/solution/solution_backingup.html).

Pour les instances déployées dans (ou mises à niveau vers) la version 1.8 ou des éditions ultérieures, les modifications de configuration que vous apportez à votre environnement ne sont pas sauvegardées automatiquement. Par conséquent, avant de modifier la configuration de votre environnement, nous vous recommandons d'effectuer une sauvegarde manuelle des composants de gestion en exécutant la tâche de sauvegarde de gestion dans la console Veeam. Pour plus d'informations sur l'exécution d'une tâche de sauvegarde manuelle, voir les [instructions techniques Veeam](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

En cas d'incidents sur les composants de gestion, vous pouvez les restaurer à partir d'une sauvegarde antérieure depuis la console Veeam. Pour plus d'informations sur l'exécution d'une tâche de restauration manuelle, voir les [instructions techniques Veeam]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Application de mises à jour à Veeam on IBM Cloud

Il vous incombe de maintenir Veeam à sa version la plus récente en le mettant à jour. Pour effectuer une mise à niveau de Veeam vers la version la plus récente, téléchargez les mises à jour Veeam depuis le site Web Veeam, copiez-les dans l'instance de serveur virtuel Veeam, puis installez-les.

## Mise à jour de licences Veeam

Vous pouvez mettre à jour manuellement votre licence Veeam à la demande en procédant ainsi :
1. [Accédez à la console Veeam Backup and Replication sous RDP](../services/managingveeam.html#accessing-the-veeam-console-by-using-rdp).
2. Dans le menu principal, cliquez sur **Licence**.
3. Dans la fenêtre **Informations sur la licence**, cliquez sur **Mettre à jour maintenant**.
4. Pour examiner les statistiques de la procédure de mise à jour manuelle de la licence, ouvrez la vue **Historique**, puis cliquez sur le noeud **Système**.

Pour plus d'informations, voir [Updating License Manually](https://helpcenter.veeam.com/docs/backup/vsphere/license_update_manual.html?ver=95).

## Remplacement des instances de serveur virtuel Veeam antérieures à V1.8 par Veeam on IBM Cloud

Le service Veeam on {{site.data.keyword.cloud_notm}}, capable de sauvegarder aussi bien des composants de gestion que des charges de travail, remplace les instances de serveur virtuel Veeam précédentes intégrées à VMware Cloud Foundation et VMware vCenter Server dans les éditions antérieures à la version 1.8 uniquement pour les composants de sauvegarde et de gestion.

En raison de cette modification, l'onglet **Sauvegarde et restauration** de la page des détails de l'instance a été retiré et les points de sauvegarde des instances ne sont plus disponibles sur la console {{site.data.keyword.vmwaresolutions_short}}. Cela dit, l'instance de serveur virtuel Veeam des instances de version antérieure à 1.8 fonctionne toujours.

Vous devez créer un ticket de demande de service {{site.data.keyword.cloud_notm}} pour obtenir de l'aide concernant une restauration. De plus, la licence de l'instance de serveur virtuel Veeam des instances de version antérieure à 1.8 a expiré le 14 octobre 2017. Par conséquent, vous devez remplacer l'ancienne instance de serveur virtuel Veeam par le nouveau service Veeam on {{site.data.keyword.cloud_notm}}.

Effectuez les opérations suivantes :
1. Sur la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche, puis cliquez sur l'instance cible.
2. Sur la page des détails de l'instance, cliquez sur l'onglet **Mise à jour et module de correction**. Assurez-vous que l'instance est au niveau de version 1.8.
3. Cliquez sur l'onglet **Services**.
4. Dans l'onglet **Ajouter des services**, installez le service Veeam on {{site.data.keyword.cloud_notm}}.

Une fois le nouveau service Veeam on {{site.data.keyword.cloud_notm}} déployé et une sauvegarde réussie de vos composants de gestion effectuée, vous pouvez supprimer de votre compte l'instance de serveur virtuel Veeam existante en créant un ticket de demande de service {{site.data.keyword.cloud_notm}}. Le support IBM identifiera alors et supprimera l'instance de serveur virtuel et le stockage Veeam existants.

### Liens connexes

* [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](veeam_considerations.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Foire aux questions](../vmonic/faq.html)
* [Site Web Veeam.com](https://www.veeam.com/)
* [Documentation technique Veeam](https://www.veeam.com/documentation-guides-datasheets.html)

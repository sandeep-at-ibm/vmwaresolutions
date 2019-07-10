---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: NetApp migrate instance, add account NetApp ONTAP, migrate cloud account

subcollection: vmware-solutions


---

# Migration d'instances NetApp ONTAP Select antérieures à la version 2.5 vers des comptes IBM Cloud
{: #np_addinstancetousraccount}

Les instances NetApp ONTAP Select qui sont déployées dans la version 2.5 et dans des éditions ultérieures dans votre compte {{site.data.keyword.cloud}} sont ajoutées automatiquement à votre compte et sont gérées par {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

Quant aux instances déployées dans la version 2.4 et dans des éditions antérieures, vous pouvez les faire migrer vers des comptes {{site.data.keyword.cloud_notm}} spécifiés pour la gestion des utilisateurs activée pour IAM.

## Avant de commencer
{: #np_addinstancetousraccount-prereq}

Assurez-vous que le compte {{site.data.keyword.cloud_notm}} vers lequel vous souhaitez faire migrer l'instance n'est pas un compte IaaS-only. Un compte IaaS-only est un compte d'infrastructure {{site.data.keyword.cloud_notm}} (IBM Cloud) qui n'est pas lié à un compte {{site.data.keyword.cloud_notm}}.

Pour savoir comment lier votre compte Iaas-only à votre compte PaaS, voir [Follow these steps to link your IaaS and PaaS accounts](https://www.ibm.com/cloud/blog/follow-steps-link-iaas-paas-accounts){:new_window}.

## Procédure de migration des instances
{: #np_addinstancetousraccount-procedure}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. A partir de la bannière de la console, cliquez sur l'icône de votre compte utilisateur, puis cliquez dans la zone **Compte** pour sélectionner le compte utilisateur vers lequel vous souhaitez faire migrer l'instance.
3. Sur le tableau **Instances NetApp ONTAP Select**, recherchez l'instance antérieure à la version V2.5.
4. Dans la colonne **Actions**, cliquez sur l'icône de menu déroulant dynamique, puis cliquez sur **Migrer une instance vers un compte**.
5. Dans la fenêtre **Migrer une instance vers un compte**, confirmez le compte vers lequel vous souhaitez faire migrer l'instance, puis cliquez sur **Migrer**.

## Résultats
{: #np_addinstancetousraccount-results}

1. Vous obtenez une notification par console vous confirmant que votre demande de migration de l'instance vers le compte {{site.data.keyword.cloud_notm}} spécifié est acceptée.
2. Lorsque la migration de l'instance est terminée, l'instance apparaît sur la page **Ressources** sous le compte vers lequel elle a migré. L'instance migrée n'apparaît plus dans le compte source de la migration.

## Liens connexes
{: #np_addinstancetousraccount-related}

* [Gestion des accès utilisateur à l'aide d'IAM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-iam#iam)
* [Invitation des utilisateurs à accéder à des services et des ressources](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Présentation d'IBM Cloud IAM](/docs/iam?topic=iam-iamoverview)

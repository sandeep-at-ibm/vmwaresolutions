---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# Migration d'instances Cloud Foundation Select antérieures à la version 2.5 vers des comptes IBM Cloud

Les instances VMware Cloud Foundation qui sont déployées dans la version 2.5 et dans des éditions ultérieures dans votre compte {{site.data.keyword.cloud}} sont ajoutées automatiquement à votre compte et sont gérées par {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM).

Quant aux instances déployées dans la version 2.4 et dans des éditions antérieures, vous pouvez les faire migrer vers des comptes {{site.data.keyword.cloud_notm}} spécifiés pour la gestion des utilisateurs activée pour IAM. 


## Procédure

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche. 
2. Dans l'angle supérieur droit de la console, cliquez sur votre avatar, puis cliquez dans la zone **Compte** pour sélectionner le compte utilisateur vers lequel vous souhaitez faire migrer l'instance. 
3. Dans le tableau **Instances Cloud Foundation**, recherchez l'instance antérieure à la version 2.5. 
4. Dans la colonne **Actions**, cliquez sur l'icône de menu déroulant dynamique, puis cliquez sur **Migrer une instance vers un compte**. 
5. Dans la fenêtre **Migrer une instance vers un compte**, confirmez le compte vers lequel vous souhaitez faire migrer l'instance, puis cliquez sur **Migrer**.

## Résultats

1. Vous obtenez une notification par console vous confirmant que votre demande de migration de l'instance vers le compte {{site.data.keyword.cloud_notm}} spécifié est acceptée.
2. Lorsque la migration d'instance est terminée, l'instance apparaît sur la page **Instances déployées** sous le compte cible de la migration. L'instance migrée n'apparaît plus dans le compte source de la migration. 

### Liens connexes

* [Gestion des accès utilisateur à l'aide d'IAM](../vmonic/iam.html)
* [Invitation des utilisateurs à accéder à des services et des ressources](../vmonic/iamuserinvite.html)
* [Présentation d'IBM Cloud IAM](https://console.stage1.bluemix.net/docs/iam/index.html#iamoverview)

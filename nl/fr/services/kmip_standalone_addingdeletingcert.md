---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ajout, affichage et suppression de certificats pour des instances KMIP for VMware on IBM Cloud

Une fois votre instance KMIP for VMware on {{site.data.keyword.cloud}} prête, vous devez lui ajouter des certificats. Lorsque vous n'avez plus besoin d'un certificat, supprimez-le de votre instance.

## Procédure pour l'ajout de certificats à vos instances KMIP for VMware on IBM Cloud

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Faites défiler jusqu'au tableau **KMIP for VMware on IBM Cloud Instances**, cliquez sur l'instance à laquelle vous voulez ajouter des certificats.
3. Cliquez sur **Add**.
4. Dans la fenêtre **Add Client SSL Certificate**, entrez le nom de et le contenu du certificat.

   Le nom du certificat ne peut pas être réutilisé dans votre instance sélectionnée. Le contenu du certificat doit être valide et contenir les balises BEGIN CERTIFICATE et END CERTIFICATE, et le certificat ne peut pas être réutilisé dans la région sélectionnée où l'instance est déployée.
   {:note}
5. Cliquez sur **Add**.

## Procédure pour l'affichage de certificats pour les instances KMIP for VMware on IBM Cloud

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Faites défiler jusqu'au tableau **KMIP for VMware on IBM Cloud Instances**, cliquez sur l'instance pour laquelle afficher les certificats.
3. Consultez la liste des certificats ajoutés sous la section **Client SSL Certificates**.
4. Pour afficher le contenu d'un certificat particulier, cliquez sur **Download**.

## Procédure pour la suppression de certificats des instances KMIP for VMware on IBM Cloud

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Faites défiler jusqu'au tableau **KMIP for VMware on IBM Cloud Instances**, cliquez sur l'instance dont vous voulez supprimer des certificats.
3. Dans le tableau **Client SSL Certificates**, recherchez le certificat que vous voulez supprimer et cliquez sur l'icône **Delete**.

   Le client perd immédiatement l'accès à toutes les clés destinées au chiffrement et au déchiffrement des données ou des données de sauvegarde. Pour que le client puisse de nouveau obtenir l'accès, vous devez ajouter de nouveau le certificat SSL client.
   {:note}

### Liens connexes

* [Affichage des instances KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [Commande des instances KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html)
* [Suppression des instances KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Evénements du service Activity Tracker](/docs/services/vmwaresolutions/vmonic/at-events.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-16"

---

# Suppression d'instances NetApp ONTAP Select

Pour libérer les composants commandés dans le cadre d'une instance NetApp ONTAP Select, supprimez celle-ci.

Lorsque vous supprimez une instance NetApp ONTAP Select, les composants suivants sont libérés, dans cet ordre :
1. Machines virtuelles en cluster NetApp ONTAP Select déployées et machine virtuelle NetApp ONTAP Select Deploy
2. Frais de support et de services
3. Licences de produit VMware
4. Serveurs ESXi
5. Sous-réseaux
6. Réseaux locaux virtuels

En raison des dépendances de ressource, les composants de votre instance ne sont pas libérés immédiatement lorsque vous supprimez cette dernière. Par exemple, les sous-réseaux et les réseaux locaux virtuels ne peuvent pas être supprimés tant que l'infrastructure {{site.data.keyword.cloud}} n'a pas récupéré tous les serveurs ESXi, opération qui s'effectue en fin de cycle de facturation d'{{site.data.keyword.cloud_notm}}. A la fin du cycle de facturation, qui est généralement de 30 jours, les sous-réseaux et les réseaux locaux virtuels sont récupérés et la suppression de l'instance est effective.

**Attention :** l'instance supprimée vous est facturée jusqu'à échéance du cycle de facturation.

## Suppression d'instances depuis la page Instances déployées

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances NetApp ONTAP Select**, recherchez l'instance à supprimer.
3. Dans la colonne **Actions**, cliquez sur l'icône Supprimer.
   L'instance prend le statut **Suppression en cours**. Une fois que l'instance est supprimée et qu'elle prend le statut **Supprimé**, cliquez de nouveau sur l'icône de suppression dans la colonne
   **Actions**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Dans la colonne **Actions**, cliquez à nouveau sur l'icône Supprimer.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

## Suppression d'instances depuis la page des details d'instance

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances NetApp ONTAP Select**, cliquez sur l'instance à supprimer.
3. Cliquez sur l'icône de menu déroulant dynamique à droite de **Console NetApp**, puis cliquez sur **Supprimer une instance**.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Cliquez sur l'icône de menu déroulant dynamique à droite de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

## Liens connexes

* [Commande d'instances NetApp ONTAP Select](np_orderinginstances.html)
* [Affichage des instances NetApp ONTAP Select](np_viewinginstances.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)

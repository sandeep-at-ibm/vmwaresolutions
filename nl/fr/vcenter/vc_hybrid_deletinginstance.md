---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Suppression des instances vCenter Server with Hybridity Bundle

Pour libérer les composants que vous avez commandés dans le cadre d'une instance VMware vCenter Server with Hybridity Bundle, supprimez celle-ci.

Lorsque vous supprimez une instance vCenter Server with Hybridity Bundle, les composants suivants sont libérés, dans cet ordre :
1. Tous les services déployés
2. Frais de support et de services
3. Licences de produit VMware
4. Serveurs ESXi
5. Sous-réseaux
6. Réseaux locaux virtuels

En raison des dépendances de ressource, les composants de votre instance ne sont pas libérés immédiatement lorsque vous supprimez cette dernière. Par exemple, les sous-réseaux et les réseaux locaux virtuels ne peuvent pas être supprimés tant que l'infrastructure {{site.data.keyword.cloud}} n'a pas récupéré tous les serveurs ESXi, opération qui s'effectue en fin de cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}. A la fin du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}, qui est généralement de 30 jours, les sous-réseaux et les réseaux locaux virtuels sont supprimés et la suppression de l'instance est effective.

L'instance supprimée vous est facturée jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
{:note}

## Procédure de suppression d'instances dans la page Instances déployées

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, recherchez l'instance à supprimer.
3. Dans la colonne **Actions**, cliquez sur l'icône Supprimer.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Dans la colonne **Actions**, cliquez à nouveau sur l'icône Supprimer.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

## Procédure de suppression d'instances dans la page des détails de l'instance

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à supprimer.
3. Cliquez sur l'icône de menu déroulant dynamique en regard de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Cliquez à nouveau sur l'icône de menu déroulant dynamique en regard de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

### Liens connexes

* [Suppression d'instances vCenter Server with Hybridity Bundle dans une configuration multisite](/docs/services/vmwaresolutions/vcenter/vc_hybrid_deletinginstance_multi.html)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_orderinginstance.html)
* [Affichage des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_viewinginstances.html)
* [Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter/vc_hybrid_addingremovingservers.html)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)

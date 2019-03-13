---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Suppression d'instances Cloud Foundation
{: #sd_deletinginstance}

Pour libérer les composants commandés dans le cadre d'une instance VMware Cloud Foundation, supprimez celle-ci.

Lorsque vous supprimez une instance Cloud Foundation, les composants suivants sont libérés, dans cet ordre :
1. Tous les services déployés
2. Frais de support et de services
3. Licences de produit VMware
4. Serveurs ESXi
5. Sous-réseaux
6. Réseaux locaux virtuels

En raison des dépendances de ressource, les composants de votre instance ne sont pas libérés immédiatement lorsque vous supprimez cette dernière. Par exemple, les sous-réseaux et les réseaux locaux virtuels ne peuvent pas être supprimés tant que l'infrastructure {{site.data.keyword.cloud}} n'a pas récupéré tous les serveurs ESXi, opération qui s'effectue en fin de cycle de facturation d'{{site.data.keyword.cloud_notm}}. A la fin du cycle de facturation d'{{site.data.keyword.cloud_notm}}, qui est généralement de 30 jours, les sous-réseaux et les réseaux locaux virtuels sont supprimés et la suppression de l'instance est effective.

L'instance supprimée vous est facturée jusqu'à échéance du cycle de facturation d'{{site.data.keyword.cloud_notm}}.
{:note}

## Procédure de suppression d'instances dans la page Instances déployées
{: #sd_deletinginstance-procedure1}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, recherchez l'instance à supprimer.
3. Dans la colonne **Actions**, cliquez sur l'icône Supprimer.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Dans la colonne **Actions**, cliquez à nouveau sur l'icône Supprimer.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

## Procédure de suppression d'instances dans la page des détails de l'instance
{: #sd_deletinginstance-procedure2}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance à supprimer.
3. Cliquez sur l'icône de menu déroulant dynamique en regard de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Cliquez à nouveau sur l'icône de menu déroulant dynamique en regard de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

## Liens connexes
{: #sd_deletinginstance-related}

* [Suppression d'instances Cloud Foundation dans une configuration multisite](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Commande d'instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Affichage d'instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Extension et réduction de capacité pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Suppression de configurations multisite](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

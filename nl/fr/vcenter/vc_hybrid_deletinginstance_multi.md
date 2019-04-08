---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Suppression d'instances vCenter Server with Hybridity Bundle dans une configuration multisite
{: #vc_hybrid_deletinginstance_multi}

Vous devez tenir compte de certaines remarques lorsque vous planifiez la suppression d'instances VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle qui font partie d'une configuration multisite.

Lorsque vous supprimez une instance vCenter Server with Hybridity Bundle, les composants suivants sont libérés, dans cet ordre :
1. Tous les services déployés
2. Frais de support et de services
3. Licences de produit VMware
4. Serveurs ESXi
5. Sous-réseaux
6. Réseaux locaux virtuels

En raison des dépendances de ressource, les composants de votre instance ne sont pas libérés immédiatement lorsque vous supprimez cette dernière. Par exemple, les sous-réseaux et les réseaux locaux virtuels ne peuvent pas être supprimés tant que l'infrastructure {{site.data.keyword.cloud_notm}} n'a pas récupéré tous les serveurs ESXi, opération qui s'effectue en fin de cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}. A la fin du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}, qui est généralement de 30 jours, les sous-réseaux et les réseaux locaux virtuels sont supprimés et la suppression de l'instance est effective.

L'instance supprimée vous est facturée jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
{:note}

## Procédure de suppression d'instances vCenter Server with Hybridity Bundle dans une configuration multisite
{: #vc_hybrid_deletinginstance_multi-procedure}

1. Retirez tous les services de l'instance vCenter Server with Hybridity Bundle secondaire.
2. Vérifiez qu'aucun objet NSX n'est développé dans l'instance secondaire que vous voulez supprimer.
3. Supprimez le vCenter Server secondaire du domaine SSO (Single Sign-On) principal. Pour plus d'informations, voir [Désenregistrement du serveur vCenter Server de la connexion unique](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Démontez l'instance de service virtuel (VSI, Virtual Service Instance) du contrôleur de domaine local. Pour plus d'informations, voir [Démontage des contrôleurs de domaine et des domaines](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Supprimez l'instance vCenter Server with Hybridity Bundle secondaire depuis la console {{site.data.keyword.vmwaresolutions_short}}.
6. Répétez les étapes 1 à 5 pour toutes les instances vCenter Server with Hybridity Bundle secondaires de votre configuration multisite.
7. Après avoir supprimé toutes les instances secondaires, vous pouvez également supprimer l'instance principale de la console {{site.data.keyword.vmwaresolutions_short}}.

## Liens connexes
{: #vc_hybrid_deletinginstance_multi-related}

* [Suppression des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)

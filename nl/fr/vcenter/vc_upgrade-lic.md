---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-24"

keywords: NSX license upgrade, upgrade license hybridity, hybridity license

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mise à niveau des licences pour les instances vCenter Server
{: #vc_upgrade-lic}

Vous pouvez mettre à niveau votre licence NSX pour les instances en version 2.1 ou ultérieure.

## Procédure de mise à niveau de votre licence NSX
{: #vc_upgrade-lic-nsx}

Cette procédure s'applique aux instances déployées en version 2.1 et ultérieures. Pour les instances qui sont déployées dans la version 2.0 et les versions antérieures, vous devez mettre à niveau la licence NSX manuellement.

Vous pouvez mettre à niveau la licence NSX de votre instance vers une édition ultérieure. Les rétromigrations d'édition de licence ne sont pas prises en charge.

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance pour laquelle vous souhaitez mettre à niveau l'instance NSX.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.

   Si aucun détail n'est affiché, cela indique probablement un problème de connectivité avec l'instance de serveur virtuel IBM CloudDriver, lié à une règle de pare-feu ou à un problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à niveau risque d'échouer.

4. Cliquez sur **Mise à jour et module de correction** sur le panneau de navigation de gauche et cliquez sur **Mettre à niveau**. Dans la fenêtre **Mettre à niveau l'édition de licence NSX**, sélectionnez l'édition voulue et cliquez sur **Mettre à niveau**.

   La mise à niveau de licence remplace toutes les licences NSX existantes sur l'instance. Des frais supplémentaires peuvent découler d'un chevauchement entre les anciennes et les nouvelles licences si vous effectuez la mise à niveau en cours de cycle de facturation. Pour éviter des frais supplémentaires, il est recommandé d'effectuer la mise à niveau de la licence à la fin du cycle de facturation.
   {:note}

## Liens connexes
{: #vc_upgrade-lic-related}

* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

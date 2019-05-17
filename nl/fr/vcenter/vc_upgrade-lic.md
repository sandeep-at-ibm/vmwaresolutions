---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mise à niveau des licences pour les instances vCenter Server
{: #vc_upgrade-lic}

Vous pouvez uniquement mettre à niveau votre instance VMware vCenter Server vers vCenter Server with Hybridity Bundle si votre instance correspond à la version 2.3 ou à une version ultérieure.

Les utilisateurs IBM Business Partner n'ont pas la possibilité de passer à Hybridity Bundle.
{:note}

## Avant de mettre à niveau votre licence à Hybridity Bundle
{: #vc_upgrade-lic-upgrade-prereq}

Vous devez prendre les mesures suivantes pour passer à Hybridity Bundle :

* Si votre instance de vCenter Server est équipée avec l'édition VMware NSX Base, votre licence NSX sera automatiquement mise à niveau vers l'édition NSX Advanced.
* Si votre instance de vCenter Server dispose d'un stockage NFS, vous ne serez pas facturé pour le stockage VMware vSAN. Cependant, vous serez facturé pour la licence vSAN qui est fournie avec Hybridity Bundle.

## Procédure de mise à niveau à Hybridity Bundle (instances de la version 2.3 ou ultérieures)
{: #vc_upgrade-lic-procedure-upgrade-to-hybridity}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à mettre à niveau à Hybridity Bundle.
3. Sur la page **Récapitulatif**, vérifiez que tous les détails d'instance sont correctement affichés. Cliquez ensuite sur **Infrastructure** dans le panneau de navigation de gauche pour vérifier les détails sur la page **Infrastructure**.

   Si aucun détail n'est affiché, cela indique probablement un problème de connectivité avec l'instance de serveur virtuel IBM CloudDriver, lié à une règle de pare-feu ou à un autre problème de réseau. Résolvez le problème avant de passer à l'étape suivante, sinon la mise à niveau risque d'échouer.

4. Cliquez sur **Mise à jour et module de correction** dans le panneau de navigation de gauche.
5. Pour appliquer la mise à niveau de licence à Hybridity Bundle, dans le tableau **Mises à niveau de licence**, cliquez sur **Mettre à niveau** dans la colonne **Action**. Passez en revue le coût estimé et cliquez sur **Mettre à niveau**.
6. Si vous le souhaitez, vous pouvez déployer le service VMware HCX on {{site.data.keyword.cloud_notm}}. Lorsque Hybridity Bundle est activé dans le tableau **Mises à niveau de licence**, procédez comme suit :
  1. Dans le tableau **Mises à niveau de licence**, cliquez sur **Déployer HCX on {{site.data.keyword.cloud_notm}}** dans la colonne **Action**.
  2. Faites défiler l'écran jusqu'à la carte **HCX on {{site.data.keyword.cloud_notm}}** et cliquez sur **Sélectionner un service**.
  3. Faites défiler l'écran et spécifiez les paramètres requis pour le service, puis cliquez sur **Suivant**.
  4. Passez en revue les conditions qui s'appliquent au service, ainsi que le coût estimé, puis cliquez sur **Passer une commande**.

## Procédure de mise à niveau de votre licence NSX (instances de la version 2.1 ou ultérieures)
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

* [Présentation de vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Foire aux questions](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

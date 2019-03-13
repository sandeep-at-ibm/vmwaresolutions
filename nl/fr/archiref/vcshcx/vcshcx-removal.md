---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# Suppression de HCX
{: #vcshcx-removal}

La suppression de HCX suppose que les réseaux étendus ne sont plus utilisés. Pour supprimer HCX, procédez comme suit.

1. Réduisez tous les réseaux étendus.
2. Dans l'interface utilisateur du client, supprimez tous les dispositifs L2C. Attendez que les dispositifs L2C disparaissent de l'interface utilisateur Web.
3. Supprimez la passerelle cloud. Ceci supprime également l'optimiseur de réseau WAN. Attendez que la passerelle cloud et l'optimiseur de réseau WAN soit supprimés.
4. Arrêtez et supprimez les machines virtuelles du dispositif HCX Manager côté client et côté cloud.
5. Supprimez la passerelle ESG d'HCX de NSX côté cloud.
6. Utilisez le navigateur vCenter Mob pour supprimer le snap-in HCX.

## Liens connexes
{: #vcshcx-removal-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Types de mises à jour logicielles VMware
{: #vum-type-updates}

VMware utilise les termes suivants pour décrire les mises à jour logicielles.

Tableau 1. Termes et définitions de mise à jour logicielle VMware

| Terme | Définition |
|:------- |:----------- |
| Bulletin |	Groupement d'un ou plusieurs bundles VIB. Les bulletins sont définis dans les métadonnées. |
| Depot |	Groupement logique de VIB et des métadonnées associées qui est publié en ligne. |
| Host upgrade image |	Image ESXi que vous pouvez importer dans le référentiel d'Update Manager et utiliser pour la mise à niveau des hôtes ESXi 5.5 ou ESXi 6.0 vers ESXi 6.5. |
| Extension | 	Bulletin qui définit un groupe de bundles VIB pour ajouter un composant facultatif à un hôte ESXi. Une extension est en principe fournie par un tiers qui est également chargé des correctifs et des mises à jour de cette extension. |
| Metadata |	Données supplémentaires qui définissent les informations de dépendance, les textes de description, les configurations système et les bulletins. |
| Offline bundle compressed file |	Archive qui encapsule les bundles VIB et les métadonnées correspondantes dans un package autonome utile pour l'application de correctifs hors connexion. Vous ne pouvez pas utiliser les bundles hors connexion de tiers ou des bundles hors connexion que vous avez générés à partir d'ensembles de bundles VIB personnalisés pour la mise à niveau des hôtes de ESXi 5.5 ou ESXi 6.0 vers ESXi 6.5. |
| Patch |	Bulletin qui regroupe un ou plusieurs bundles VIB pour traiter un problème ou une amélioration particulière. |
| Roll-up |	Collection de correctifs regroupés pour faciliter le téléchargement et le déploiement. |
| VA upgrade |	Mise à niveau d'un dispositif virtuel, que le fournisseur considère comme une mise à niveau. |
| VIB |	VIB est un package de logiciel unique. |

## Liens connexes
{: #vum-type-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [Démonstrations {{site.data.keyword.vmwaresolutions_full}}](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (démonstrations)

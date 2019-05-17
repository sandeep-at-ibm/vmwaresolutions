---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# Mise à niveau des composants HCX
{: #vcshcx-upgrade}

La mise à niveau de HCX est un processus simple qui utilise l'interface utilisateur Web du client pour la mise à jour du gestionnaire HCX côté client et l'interface utilisateur Web du cloud pour la mise à jour du gestionnaire HCX côté cloud. Vous devez mettre à niveau les deux côtés car toute mise à jour d'un composant de flotte entraîne un redéploiement des composants de flotte avec le niveau de code installé par le gestionnaire d'un côté et de l'autre. Si le support VMware vous demande l'ID du système, fournissez ces informations pour le côté client et le côté cloud. Utilisez SSH dans le gestionnaire HCX (client ou cloud) et exécutez `cat
/common/location` pour localiser l'ID du système.

## Liens connexes
{: #vcshcx-upgrade-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

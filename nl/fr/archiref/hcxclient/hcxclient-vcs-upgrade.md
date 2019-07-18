---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# Mise à niveau des composants HCX
{: #hcxclient-vcs-upgrade}

La mise à niveau de HCX est un processus simple qui utilise l'interface utilisateur Web du client pour la mise à jour du gestionnaire HCX côté client et l'interface utilisateur Web du cloud pour la mise à jour du gestionnaire HCX côté cloud.

Vous devez mettre à niveau les deux côtés car toute mise à jour d'un composant de flotte entraîne un redéploiement des composants de flotte avec le niveau de code installé sur HCX Manager.

Si le Support VMware vous demande l'ID du système, fournissez ces informations pour le côté client et le côté cloud. Utilisez SSH dans le gestionnaire HCX (client ou cloud) et exécutez `cat /common/location` pour localiser l'ID du système.

## Liens connexes
{: #hcxclient-vcs-upgrade-related}

* [Glossaire des composants et des termes HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [Préparation de l'environnement d'installation](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [Déploiement du client HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [Maillage de services sur site HCX ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [Migrations de VMware Hybrid Cloud ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [Paramètres et composants de surveillance](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [Traitement des incidents dans HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Déploiement partiellement distribué
{: #caveonix-partially}

Une fois le déploiement automatisé terminé, vous pouvez effectuer une mise à l'échelle manuelle en augmentant la mémoire RAM et le disque dans la machine virtuelle initiale et ajouter trois machines virtuelles d'extension. Le script de configuration de Riskforesight peut être exécuté pour activer et configurer les composants d'application sur les quatre machines virtuelles.

Ce modèle de déploiement est prévu pour desservir jusqu'à 500 actifs avec jusqu'à 30 jours d'indexation des données.

Sélectionnez les prochaines adresses IP disponibles du réseau portable privé {{site.data.keyword.cloud}}. Configurez les noms de domaine complets dans ADDNS.

Le dimensionnement des machines virtuelles est le suivant :

Tableau 1. Paramètres de base

|Paramètre	|Valeur|
|---|---|
|Type	|Base|
|Nombre de machines virtuelles	|1|
|vCPU	|16|
|RAM	|64 Go|
|Disque	|1000 Go|
|Système d'exploitation	|CentOS 7|
|Composants d'application installés	|Interface utilisateur, application, plug-in, collecteur central, magasin de données d'index, magasin de données de messagerie, magasin de données relationnel, collecteur distant|

Les caractéristiques des machines virtuelles d'extension sont les suivantes :

Tableau 2. Paramètres des machines virtuelles d'extension

| Paramètre	| Valeur |
|---|---|
| Type	| Extension |
| Nombre de machines virtuelles	| 3 |
| vCPU	| 8 |
| RAM	| 16 Go |
| Disque	| 4 To |
| Système d'exploitation	| CentOS 7 |
| Composants d'application installés	| Noeuds de données (extension) |

Le tableau suivant décrit les caractéristiques des machines virtuelles du collecteur distant.

Tableau 3. Paramètres du collecteur distant

|Paramètre	|Valeur|
|---|---|
|Nombre de machines virtuelles	|Selon les besoins|
|vCPU	|8|
|RAM	|8 Go|
|Disque	|1 To|
|Système d'exploitation	|CentOS 7|
|Composants d'application installés	|Collecteur distant|

## Liens connexes
{: #caveonix-partially-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Déploiement tout en un
{: #caveonix-allinone}

Le déploiement "tout en un" désigne le déploiement et la configuration automatisés d'une machine virtuelle unique hébergeant tous les composants de l'application RiskForesight. Ce modèle de déploiement convient aux petits déploiements, jusqu'à 100 actifs avec 7 à 30 jours d'indexation. Le tableau suivant décrit les caractéristiques des machines virtuelles d'un déploiement “tout en un” :

Tableau 1. Paramètres tout en un

|Paramètre	|Valeur|
|---|---|
|Type	|Base|
|Nombre de machines virtuelles	|1|
|vCPU	|16|
|RAM	|32 Go|
|Disque	|80 Go|
|Système d'exploitation	|CentOS 7|
|Composants d'application installés|	Interface utilisateur, application, plug-in, collecteur central, magasin de données d'index, magasin de données de messagerie, magasin de données relationnel, contrôleur distant|

Le tableau suivant décrit les caractéristiques des machines virtuelles du collecteur distant additionnel.

Tableau 2. Collecteur distant

|Paramètre	|Valeur|
|---|---|
|Nombre de machines virtuelles	|Selon les besoins|
|vCPU	|8|
|RAM	|8 Go|
|Disque	|1 To|
|Système d'exploitation	|CentOS 7|
|Composants d'application installés	|Collecteur distant|

## Liens connexes
{: #caveonix-allinone-related}

*   [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

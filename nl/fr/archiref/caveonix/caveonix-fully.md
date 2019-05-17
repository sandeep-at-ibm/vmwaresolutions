---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# Déploiement entièrement distribué
{: #caveonix-fully}

Des machines virtuelles de base et des machines virtuelles d'extension supplémentaires sont ajoutées en fonction du nombre d'actifs et des exigences de conservation des données.

Tableau 1. Machines virtuelles de base - interface utilisateur

|Paramètre	|Valeur|
|---|---|
|Type	|Base|
|Nombre de machines virtuelles	|2|
|vCPU	|2|
|RAM	|6 Go|
|Disque	|60 Go|
|Système d'exploitation	|CentOS 7|
|Composants d'application installés	|Interface utilisateur|

Tableau 2. Machines virtuelles de base - Applications et plug-in

|Paramètre	|Valeur|
|---|---|
|Type	|Base|
|Nombre de machines virtuelles	|2|
|vCPU	|8|
|RAM	|16 Go|
|Disque	|500 Go|
|Système d'exploitation	|CentOS 7|
|Composants d'application installés	|Application, Plug-in|

Tableau 3. Machines virtuelles de base - Collecteur central

|Paramètre	|Valeur |
|---|---|
|Type	|Base |
|Nombre de machines virtuelles	|3 |
|vCPU	|8 |
|RAM	|16 Go |
|Disque	|500 Go |
|Système d'exploitation	|CentOS 7 |
|Composants d'application installés	|Collecteur central (cluster) |

Tableau 4. Machines virtuelles de base - Base de données relationnelle

|Paramètre	|Valeur |
|---|---|
|Type	|Base |
|Nombre de machines virtuelles	|2 |
|vCPU	|8 |
|RAM	|16 Go |
|Disque	|1 To |
|Système d'exploitation|CentOS 7 |
|Composants d'application installés	|Magasin de données relationnel (principal / secondaire) |

Tableau 5. Machines virtuelles de base - Magasin de données de messagerie

|Paramètre	|Valeur |
|---|---|
|Type	|Base |
|Nombre de machines virtuelles	|3 |
|vCPU	|8 |
|RAM	|16 Go |
|Disque	|1 To |
|Système d'exploitation	|CentOS 7 |
|Composants d'application installés	|Magasin de données de messagerie (cluster) |

Tableau 6. Machines virtuelles de base - Magasin de données d'index (noeuds maître)

|Paramètre	|Valeur |
|---|---|
|Type	|Base |
|Nombre de machines virtuelles	|3 |
|vCPU	|8 |
|RAM	|16 Go |
|Disque	|1 To |
|Système d'exploitation	|CentOS 7 |
|Composants d'application installés	|Magasin de données d'index (noeuds maître) |

Tableau 7. Base de données - Magasin de données d'index (noeuds de données)

|Paramètre	|Valeur |
|---|---|
|Type	|Base |
|Nombre de machines virtuelles	|5 |
|vCPU	|8 |
|RAM	|16 Go |
|Disque	|4 To |
|Système d'exploitation	|CentOS 7 |
|Composants d'application installés	|Magasin de données d'index (noeuds de données) |

Le tableau suivant décrit les caractéristiques des machines virtuelles d'extension.

Tableau 8. Machines virtuelles d'extension - Noeuds de données

|Paramètre	|Valeur |
|---|---|
|Type	|Extension |
|Nombre de machines virtuelles  28 |
|vCPU	|8 |
|RAM	|16 Go |
|Disque	|4 To |
|Système d'exploitation	|CentOS 7 |
|Composants d'application installés	|Noeuds de données (extension) |

Le tableau suivant décrit les caractéristiques des machines virtuelles du collecteur distant.

Tableau 9. Collecteur distant

|Paramètre	|Valeur |
|---|---|
|Nombre de machines virtuelles	|Selon les besoins |
|vCPU	|8 |
|RAM	|8 Go |
|Disque	|1 To |
|Système d'exploitation	|CentOS 7 |
|Composants d'application installés	|Collecteur distant |

## Liens connexes
{: #caveonix-fully-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

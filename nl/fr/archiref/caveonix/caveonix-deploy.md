---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Modèles de déploiement de Caveonix RiskForesight
{: #caveonix-deploy}

Cette section décrit les modèles de déploiement de Caveonix RiskForesight ainsi que le processus d'installation de la solution.

Lorsque vous sélectionnez l'option {{site.data.keyword.vmwaresolutions_full}} RiskForesight, vous n'avez pas à suivre toutes les étapes du déploiement car les étapes initiales sont automatisées. Cependant, pour bien comprendre tous les aspects du déploiement et de l'architecture, et pour ceux qui souhaitent étendre la solution après le déploiement initial, une compréhension plus approfondie est nécessaire.

L'installation de RiskForesight comprend les principales étapes suivantes :

1. [Planification initiale et pré-requis](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) – Connaissance et sélection d'une option de déploiement, configuration du DNS pour fournir une résolution FQDN/IP pour les composants d'application.
2. [Déploiement de machine virtuelle](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) – Déploiement de machines virtuelles à partir d'un modèle OVF. La machine virtuelle a tous les composants d'applications installés sur elle.
3. [Configuration d'application](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) – Exécution du script de configuration Caveonix qui configure le composant d'application sur chacune des machines virtuelles.
4. [Paramétrage d'application](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) – Configuration du fournisseur de service et d'un locataire ou d'une organisation pour que l'application devienne accessible aux utilisateurs.

L'installation automatique met à disposition une machine virtuelle et configure tous les composants d'application sur cette machine virtuelle.
{:note}

## Dimensionnement du déploiement
{: #caveonix-deploy-sizing}

Le dimensionnement du déploiement est calculé à l'aide de volumes suivants.

Tableau 1. Volumes

|Type de données	|Volume |
|---|---|
|Analyses par jour	|1 |
|Données d'analyse (Mo)	|20 |
|Données de journal (Mo)	|500 |
|Données de flux (Mo)	|200 |
|Données d'actif (Mo)	|46 |
|Stockage total par actif par jour (Mo)	|766 |
|Coefficient de réplication des données	|2 |
|Stockage d'index total/actif/jour (Mo)	|1532 |

Le coefficient de réplication de données est défini sur 2 car le magasin d'index (Elastic Search) utilise par défaut une réplication des index de n+1.
{:note}

Le nombre de machines virtuelle de mise à l'échelle est calculé en fonction du nombre d'actifs et du nombre de jours pendant lesquels les données doivent être indexées.

Tableau 2. Mise à l'échelle des paramètres de machine virtuelle

|Nombre d'actifs	|100	|500	|5000 |
|---|---|---|---|
|Jours de données	|30	|30	|30 |
|Stockage d'index total/actif/jour (Mo)	|1532	|1532	|1532 |
|Stockage d'index total/actif/30 jours (TB)	|4	|22	|219 |
|Données prises en charge par noeud de mise à l'échelle (To)	|0	|8	|8 |
|Machines virtuelles de mise à l'échelle requises	|0	|3	|27 |

La quantité de stockage requise est calculée comme suit :

Tableau 3. Paramètres de stockage

|Nombre d'actifs	|100	|500	|5000 |
|---|---|---|---|
|Conservation des données à long terme (mois)	|8	|8	|8 |
|Stockage total par actif par jour (Mo)	|766	|766	|766 |
|Jours de données	|30	|30	|30 |
|Conservation des données à court terme (To)	|7	|33	|329 |
|Conservation des données à long terme (To)	|18	|88	|877 |

Les données sont utilisées comme suit :

-	Les données d'analyse sont utilisées dans Gestion de la conformité
-	Les données de journal sont utilisées dans la gestion contextuelle
-	Les données de politique et de flux sont utilisées dans la gestion des risques et les données de flux sont uniquement disponible dans NSX Manager

Le stockage des données offre trois niveaux :

-	Répliqué
-	Court terme
-	Long terme

Le tableau suivant offre un récapitulatif des déploiements :

Tableau 4. Récapitulatif

|Modèle de déploiement	|“tout en un”	|Partiellement distribué	|Entièrement distribué |
|---|---|---|---|
|Nombre d'actifs	|100	|500	|5000 |
|Données en ligne générées en 30 jours (To)	|4	|22	|219 |
|Conservation de données quasi en ligne (90 jours) (To)	|7	|33	|329 |
|Conservation des données hors ligne (8 mois) (To)	|18	|88	|877 |
|Conservation du stockage de données total (1 an) (To)	|28	|142	|1425 |
|Machines virtuelles de base	|1	|1	|20 |
|Machines virtuelles de mise à l'échelle	|0	|3	|28 |
|Nombre total de machines virtuelles	|1	|4	|48 |

**Remarques :**
Lorsque vous retirez le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}, l'automatisation {{site.data.keyword.vmwaresolutions_short}} supprime uniquement la seule machine virtuelle Caveonix "tout-en-un" qui a été déployée et le sous-réseau privé dédié qui a été commandé pour elle. Par conséquent,
* si vous avez scindé la machine virtuelle Caveonix en plusieurs machines virtuelles, ces dernières ne sont pas retirées.
* Si vous avez utilisé les adresses IP du sous-réseau privé dédié sur des machines virtuelles supplémentaires, de nouvelles adresses IP doivent être affectées à ces dernières pour qu'elles puissent continuer à fonctionner.
* Si vous supprimez l'instance vCenter Server A avec le service Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} installé et que vous avez utilisé les adresses IP du sous-réseau privé dédié commandé pour le service dans l'instance vCenter Server B, le sous-réseau privé dédié est annulé lors de la suppression de l'instance vCenter Server A.

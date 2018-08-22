---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---

# Présentation de la solution

Les offres {{site.data.keyword.vmwaresolutions_full}} vous permettent d'étendre votre centre de données virtuel VMware existant dans {{site.data.keyword.cloud_notm}} ou d'héberger vos applications natives en cloud. 

La solution prend en charge des cas d'utilisation, tels que l'extension de capacité dans le cloud (et la contraction le cas échéant), la migration vers le cloud, la reprise après incident vers le cloud et la sauvegarde dans le cloud. Avec la solution, vous pouvez créer un environnement de cloud dédié pour le développement, les tests, la formation, les laboratoires ou la production.

Consultez ces informations pour la conception des offres {{site.data.keyword.vmwaresolutions_short}}, y compris VMware Cloud Foundation et VMware vCenter Server, dont les charges de travail cible requièrent des niveaux élevés de disponibilité et d'évolutivité. 

Cette conception sert d'architecture de référence pour les autres composants internes ou spécifiques des fournisseurs qui doivent être ajoutés pour des cas d'utilisation spécifiques. 

## Présentation de VMware on IBM Cloud

Figure 1. Présentation de VMware on {{site.data.keyword.cloud_notm}}
![Présentation de VMware on {{site.data.keyword.cloud_notm}}](solution_overview.svg "La solution virtualise les ressources de calcul, de réseau et éventuellement de stockage qui seront consommées par les machines virtuelles sur lesquelles vous pouvez exécuter vos applications.")

## Principaux avantages

VMware Cloud Foundation et vCenter Server on {{site.data.keyword.cloud_notm}} fournissent les blocs de construction fondamentaux, notamment VMware vSphere, vCenter Server, NSX, et les options de stockage partagé, telles que vSAN, nécessaires pour concevoir avec flexibilité l'architecture d'une solution SDDC (centre de données défini par logiciel) VMware la mieux adaptée à vos charges de travail. En appliquant l'automatisation avancée et l'infrastructure bare metal à service exclusif, vous pouvez rapidement déployer l'ensemble de l'environnement VMware sur l'{{site.data.keyword.cloud_notm}} et accéder à votre environnement virtuel à l'aide de vos outils favoris en seulement quelques heures. A ce stade, vous pouvez accéder à l'environnement hébergé par IBM et le gérer via les clients VMware natifs, l'interface de ligne de commande, les scripts existants ou d'autres outils compatibles API vSphere familiers. 

Après le déploiement, vous pouvez ajouter des noeuds d'hôte ESXi et gérer la sauvegarde et l'application de correctifs pour certains composants de gestion. Les services professionnels et gérés d'{{site.data.keyword.cloud_notm}} sont également disponibles pour vous aider à accélérer votre transition vers le cloud en vous offrant des services de migration, d'implémentation et d'intégration.

Les offres VMware on {{site.data.keyword.cloud_notm}} présentent les avantages suivants :

* Une **livraison plus rapide** des projets informatiques pour les développeurs et les secteurs d'activité. Le temps nécessaire à l'approvisionnement, à l'architecture, à l'implémentation et au déploiement des ressources passe de quelques semaines ou quelques mois à quelques heures. 
* Une **sécurité renforcée** au moyen de serveurs bare metal dédiés dans un cloud privé hébergé, y compris le chiffrement des données au repos. 
* Une **gestion et une gouvernance cohérentes** du cloud hybride déployé grâce à des droits d'accès administrateur complets à la gestion de la virtualisation, ce qui permet de préserver vos outils et vos scripts VMware existants, ainsi que les efforts réalisés en matière de formation. 
* Une **optimisation de l'expertise VMware à l'échelle mondiale** grâce aux services professionnels et gérés d'IBM qui couvrent plus de 30 {{site.data.keyword.CloudDataCents_notm}} dans le monde entier. 

### Liens connexes

* [Présentation de la conception](design_overview.html)
* [Mise à l'échelle de la capacité](solution_scaling.html)
* [Sauvegarde des composants](solution_backingup.html)

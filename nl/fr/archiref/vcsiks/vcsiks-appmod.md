---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-21"

---

# Présentation de la modernisation des applications
{: #vcsiks-appmod}

Le diagramme ci-après présente l'architecture de référence de la modernisation des applications qui est déployée par Acme Skateboards et qui est décrite en détail dans cette documentation.

Figure 1. Diagramme général de l'architecture
![Diagramme général de l'architecture](vcsiks-aod.svg)

Cette architecture hybride permet à Acme Skateboards de :
- faire migrer des machines virtuelles VMware sur site vers {{site.data.keyword.cloud}} avec peu ou aucune durée d'indisponibilité et aucune reconfiguration d'application ;
- démarrer le parcours de modernisation des applications en lui permettant de se focaliser sur la conteneurisation des interfaces Web et des logiciels intermédiaires plus simples tout en permettant que d'autres bases de données plus complexes conservent leur statut de machines virtuelles ;
- se servir de Cloud Automation Manager (CAM) pour écrire un script IaC (Infrastructure as Code) afin de composer et d'orchestrer les services qui sont réalisés à partir de machines virtuelles et de conteneurs en vue de les intégrer à ses chaînes d'outils DevOps et sa solution ITSM.

L'architecture de référence est composée des principaux composants suivants :
- **Virtualisation sur site** – Cluster VMware qui héberge actuellement les machines virtuelles Acme Skateboards. Ces machines virtuelles hébergent actuellement les applications qui doivent être modernisées. Ce cluster doit respecter les prérequis de l'architecture [VMware HCX on {{site.data.keyword.cloud_notm}} Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf) de manière à pouvoir exécuter HCX.

HCX étend les réseaux locaux à {{site.data.keyword.cloud_notm}} afin de permettre aux clients de faire migrer des machines virtuelles dans l'instance VMware vCenter Server on {{site.data.keyword.cloud_notm}} qui s'exécute sur {{site.data.keyword.cloud_notm}}, et dans l'autre sens si besoin.
- **{{site.data.keyword.cloud_notm}} for VMware Solutions** – L'instance vCenter Server fournit les blocs de construction VMware fondamentaux, tels que vSphere, vCenter Server, NSX-V, et des options de stockage, telles que vSAN ou {{site.data.keyword.cloud_notm}} Endurance, nécessaires pour déployer automatiquement une solution VMware Software Defined Data Center (SDDC). Le cluster VMware est la cible des machines virtuelles migrées et certaines des applications modernisées dans les conteneurs hébergés dans {{site.data.keyword.icpfull_notm}}. Les principaux composants de vCenter Server sont les suivants :
  - **NSX-V** - NSX-V fournit la couche de virtualisation de réseau dans vCenter Server offrant un réseau dissocié pour les machines virtuelles Acme Skateboards. NSX-V permet le mode BYOIP et isole les réseaux de charge de travail des réseaux {{site.data.keyword.cloud_notm}}. NSX-V est programmé par HCX pour créer les réseaux qui sont étendus par Acme Skateboards à partir de l'environnement local.
  - **NSX-T** - NSX-T fournit un jeu commun d'outils de gestion du réseau et de la sécurité sur les conteneurs et les machines virtuelles. NSX-T est entièrement compatible avec l'interface Container Networking Interface (CNI) Kubernetes et s'intègre à celle-ci pour fournir une mise en réseau de conteneur. NSX-T fournit le réseau dissocié que les applications modernisées utilisent et il remplace Calico, qui est utilisé de façon native par {{site.data.keyword.icpfull_notm}} et {{site.data.keyword.containerlong_notm}}.

- **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} est une plateforme applicative pour le développement et la gestion d'applications conteneurisées. Il s'agit d'un environnement intégré qui inclut l'orchestrateur de conteneurs Kubernetes, un référentiel d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance et une interface graphique à partir de laquelle Acme Skateboards peut déployer, gérer, surveiller et mettre à l'échelle ses applications de façon centralisée. L'instance vCenter Server héberge les composants {{site.data.keyword.icpfull_notm}}, les noeuds maître, les noeuds worker, etc. et les exécute en tant que machines virtuelles. Hôtes {{site.data.keyword.icpfull_notm}} :
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM est une plateforme IaC (Infrastructure as Code) prête pour l'entreprise qui permet à partir d'un point unique de mettre à disposition des charges de travail de machine virtuelle, sur site ou sur vCenter Server, ainsi que des charges de travail Kubernetes, dans {{site.data.keyword.icpfull_notm}} ou {{site.data.keyword.containerlong_notm}}, à l'aide de modèles. CAM est une application Docker qui s'exécute sur {{site.data.keyword.icpfull_notm}} et est étroitement intégrée pour l'autorisation, le contrôle d'accès à base de rôles (RBAC) et d'autres fonctions.
    - Les applications Acme Skateboards conteneurisées que les clients veulent déployer dans cet environnement.

- **{{site.data.keyword.containerlong_notm}}** – {{site.data.keyword.containerlong_notm}} permet à l'entreprise Acme Skateboards de déployer ses applications modernisées dans des conteneurs Docker qui s'exécutent dans des clusters Kubernetes. Les modes maître sont entièrement gérés par IBM tandis que les noeuds worker présents dans le pool worker sont déployés dans le même compte {{site.data.keyword.cloud_notm}} que leur instance vCenter Server. Les noeuds worker peuvent être des instances de serveur virtuel dédié, public ou bare metal. Calico est installé et configuré automatiquement dans {{site.data.keyword.containerlong_notm}}. Calico fournit une connectivité de réseau sécurisée pour les conteneurs et est configuré dans {{site.data.keyword.containerlong_notm}}afin d'utiliser l'encapsulation IP-in-IP pour les paquets qui transitent par des sous-réseaux et afin d'utiliser NAT pour les connexions sortantes à partir des conteneurs.

- **Direct Link** – {{site.data.keyword.cloud_notm}} Direct Link utilise le fournisseur WAN d'Acme Skateboard pour connecter son centre de données à {{site.data.keyword.cloud_notm}} afin de fournir une connexion réseau sécurisée, à faible temps d'attente et fiable. Cette connexion fournit :
  - Un accès aux applications hébergées par le cloud à partir de vos utilisateurs d'entreprise.
  - Le trafic entre les machines virtuelles sur site et les machines virtuelles du cloud.
  - Le trafic entre les systèmes existants du centre de données sur site et les machines virtuelles du cloud.

## Principaux avantages pour l'entreprise Acme Skateboards
{: #vcsiks-appmod-benefits}

vCenter Server fournit les blocs de construction fondamentaux qui incluent notamment VMware vSphere, vCenter Server, NSX, et des options de stockage partagé, telles que vSAN, nécessaires pour concevoir avec souplesse une solution VMware Software Defined Data Center (SDDC) la mieux adaptée à vos charges de travail.

En résumé, les avantages des offres {{site.data.keyword.cloud_notm}} for VMware sont les suivants :
* Une livraison plus rapide des projets informatiques pour les développeurs et les secteurs d'activité. En effet, le temps nécessaire à l'approvisionnement, à l'architecture, à l'implémentation et au déploiement des ressources passe de quelques semaines ou quelques mois à quelques heures.
* Une sécurité renforcée au moyen de serveurs bare metal dédiés dans un cloud privé hébergé, y compris le déploiement de noeud final de service de réseau privé dans des services {{site.data.keyword.cloud_notm}}, tels qu'{{site.data.keyword.containerlong_notm}} et KMIP.
* Une gestion et une gouvernance cohérentes du cloud hybride déployé grâce à des droits d'accès administrateur complets à la gestion de la virtualisation. La gestion permet de préserver vos outils et vos scripts VMware existants, ainsi que les efforts réalisés en matière de formation.
* Une expertise VMware à l'échelle mondiale grâce aux services professionnels et gérés d'IBM qui couvrent plus de 30 centres de données {{site.data.keyword.CloudDataCents_notm}} dans le monde entier.

{{site.data.keyword.containerlong_notm}} est une offre gérée par Kubernetes qui fournit de puissants outils de gestion, une expérience utilisateur intuitive et une sécurité et un isolement intégrés pour une livraison rapide des applications, tout en utilisant Cloud Services, y compris les fonctions cognitives de Watson. IBM est membre platine de la fondation CNCF (Cloud Native Computing Foundation) et notre offre est conforme au programme de test de conformité Kubernetes de la fondation CNCF.

{{site.data.keyword.containerlong_notm}} fournit des fonctionnalités Kubernetes natives, telles que les suivantes :
- Une planification intelligente optimise l'utilisation des ressources de cluster sous-jacentes en déployant des applications de telle manière que les pods qui consomment une quantité importante d'UC et de mémoire RAM sont colocalisés.
- La réparation spontanée des applications et des microservices conteneurisés garantit que ces composants sont redéployés automatiquement si quelque chose disparaît.
- La mise à l'échelle horizontale vous permet de configurer une stratégie de déploiement dont l'orchestrateur se sert pour s'assurer que les charges de travail possèdent la capacité requise.
- La reconnaissance de service et l'équilibrage de charge fournissent un serveur de noms de domaine simple au sein du cluster Kubernetes qui permet aux services de s'enregistrer eux-mêmes, et éliminent le recours au codage statique de vos microservices. L'équilibrage de charge distribue des demandes entrantes aux instances qui s'exécutent dans votre architecture.
- Des déploiements et des récupérations en amont automatisés viennent en soutien aux équipes qui déploient de nouvelles fonctions et de nouveaux correctifs de manière contrôlée. En cas de problème, nous pouvons automatiquement récupérer en amont la version précédente de l'image notoirement correcte.
- Gestion des secrets et des configurations. Les secrets représentent un objet contenu dans Kubernetes qui sert à stocker des données sensibles, telles qu'un mot de passe, un jeton ou une clé. Ces secrets sont chiffrés par défaut et garantissent que l'accès à ces données sensibles est contrôlé.

Les clients qui se tournent vers des plateformes applicatives natives en cloud, telles qu'{{site.data.keyword.icpfull_notm}} et {{site.data.keyword.containerlong_notm}}, se concentrent sur la vitesse et l'innovation et perdent parfois de vue la sécurité et la mise en réseau. Attendre que les équipes dédiées à la mise en réseau ou à la sécurité commandent des services, tels que les équilibreurs de charge, les pare-feux, les commutateurs et les routeurs, a pour conséquence de réduire leur délai de rentabilisation.

Cette architecture de référence montre comment VCS, {{site.data.keyword.icpfull_notm}} et {{site.data.keyword.containerlong_notm}} permettent à l'entreprise Acme Skateboards de se déplacer en toute sécurité tout au long de son parcours de modernisation des applications.

## Liens connexes
{: #vcsiks-appmod-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# Présentation de l'architecture

Les offres IBM Cloud for VMware fournissent l'automatisation du déploiement des composants de technologie VMware dans les centres de données IBM Cloud situés dans le monde entier. L'architecture est composée d'une région de cloud et a la capacité de s'étendre dans des régions de cloud supplémentaires situées dans une autre zone géographique et/ou dans un autre pod IBM Cloud au sein du même centre de données. 

Les produits IBM Cloud Private (ICP) et Cloud Automation Manager (CAM) peuvent être déployés manuellement dans votre plateforme de virtualisation sur site, permettant ainsi la gestion du cloud à partir d'emplacements locaux. Sinon, ICP et CAM sont offerts en tant qu'extensions de service à un déploiement VMware vCenter Server on IBM Cloud (VCS) nouveau ou existant, via l'automatisation, permettant ainsi la gestion du cloud à partir d'IBM Cloud.

ICP est une plateforme applicative pour le développement et la gestion sur site d'applications conteneurisées. Il s'agit d'un environnement intégré pour la gestion de conteneurs qui inclut l'orchestrateur de conteneurs Kubernetes, un référentiel d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance.

IBM Multi-Cluster Cloud Manager (MCM) fournit la visibilité utilisateur, la gestion orientée applications (règles, déploiements, santé, opérations) et la conformité basée sur les règles sur les clouds et les clusters. MCM vous permet de contrôler vos clusters Kubernetes. Vous pouvez vous assurer que vos clusters sont sécurisés, qu'ils fonctionnent correctement et qu'ils fournissent une plateforme de gestion de service qui s'exécute sur ICP et permet aux développeurs et aux administrateurs de répondre aux besoins de l'entreprise. Cloud Automation Manager Service Composer vous permet d'exposer des services cloud hybrides dans le catalogue ICP. 

## Plateforme de gestion du cloud côté IBM Cloud

Figure 1. Gestion du cloud côté IBM Cloud

![Gestion du cloud côté IBM Cloud](vcsicp-oncloud-cloudmgt.svg)

Le diagramme ci-dessus représente ICP et CAM déployés avec l'infrastructure IBM Cloud, avec des connexions aux services vCenter et IBM Kubernetes Service (IKS) locaux déployés sur IBM Cloud. Les utilisateurs peuvent déployer des machines virtuelles sur site, des machines virtuelles dans l'instance VCS et des conteneurs sur le cluster ICP et IKS. 

Dans le diagramme, CAM crée des connexions de cloud aux services vCenter, aux fournisseurs de cloud et aux environnements ICP et IKS de façon logique. Des clusters ICP doivent être déployés dans chaque centre de données/environnement de cloud, MCM fournissant le mécanisme de connexion aux clusters ICP dans une seule vue de gestion. 

ICP peut être déployé avec des composants NSX-V ou NSX-T. ICP avec NSX-V permet d'exécuter les machines virtuelles ICP sur le réseau VXLAN et d'utiliser la mise en réseau interne Kubernetes Calico. 

ICP avec NSX-T permet aux utilisateurs de contrôler et configurer la mise en réseau, le sous-réseau et les règles à partir d'une interface utilisateur centralisée (NSX-T Manager). Pour savoir ce qui distingue NSX-V de NSX-T, voir la rubrique [Architecture de référence de la mise en réseau VCS pour IBM Cloud](../vcsnsxt/vcsnsxt-intro.html). 

## Plateforme de gestion du cloud sur site

Figure 2. Gestion du cloud sur site

![Gestion du cloud sur site](vcsicp-onprem-cloudmgt.svg)

Le diagramme ci-dessus représente ICP et CAM déployés dans l'infrastructure sur site, avec des connexions aux services vCenter et IKS déployés sur IBM Cloud. Les utilisateurs peuvent déployer des machines virtuelles et des conteneurs sur site, des machines virtuelles dans l'instance vCenter Center et des conteneurs sur le cluster IKS. 

Le réseau privé virtuel strongSwan est utilisé pour établir une connectivité avec les conteneurs IKS déployés, tôt ou tard, cela pourra être remplacé par la connectivité Direct Link. 

Dans le diagramme, CAM crée des connexions de cloud aux services vCenter, aux fournisseurs de cloud et aux environnements ICP et IKS de façon logique. Des clusters ICP doivent être déployés dans chaque centre de données/environnement de cloud, MCM fournissant le mécanisme de connexion aux clusters ICP dans une seule vue de gestion. 

### Liens connexes

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

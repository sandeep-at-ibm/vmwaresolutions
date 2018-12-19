---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Introduction à VMware vCenter Server on IBM Cloud et à IBM Cloud Private

Ce document fournit une vue du parcours de modernisation des applications vers {{site.data.keyword.cloud}}, en mettant l'accent sur les composants de gestion du cloud afin de permettre l'optimisation d'un environnement multi-cloud intégré pour la modernisation des applications :

- **vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server est une offre d'{{site.data.keyword.vmwaresolutions_short}}. Il s'agit d'une plateforme basée sur VMware qui est automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
- **{{site.data.keyword.cloud_notm}} Private** - ICP est une plateforme applicative pour le développement et la gestion d'applications conteneurisées, qui sont déployées sur des plateformes d'infrastructure virtuelles, telles que VMware. 
- **IBM Kubernetes Services** - IKS est un service géré sur {{site.data.keyword.cloud_notm}} qui utilise Kubernetes comme moteur d'orchestration pour l'automatisation du déploiement, la mise à l'échelle et les opérations de conteneurs d'applications sur un cluster à service exclusif.
- **IBM Multi-Cluster Manager** – MCM fournit la visibilité utilisateur, la gestion orientée applications (règles, déploiements, santé, opérations) et la conformité basée sur les règles sur les clouds et les clusters. MCM vous permet de contrôler vos clusters Kubernetes.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM est une plateforme de gestion libre-service multi-cloud qui s'exécute sur ICP et permet aux développeurs et aux administrateurs de répondre aux besoins de l'entreprise. 

## Modernisation des applications sur IBM Cloud

La modernisation des applications fait référence au processus de transition d'applications existantes pour utiliser de nouvelles approches sur le cloud. Aujourd'hui, les clients recherchent des approches innovantes et efficaces qui les aident à effectuer cette transition en tenant compte de la complexité de leur activité et de leurs applications.

Les pressions économiques imposent des commercialisations plus rapides. Votre patrimoine existant inclut non seulement des applications, mais également des données, des processus, une logique métier et des interfaces utilisateur, qui doivent tous être adaptés aux nouveaux besoins commerciaux.

Les avantages de la modernisation des applications sont les suivants :

- Amélioration de la productivité des développeurs
- Accroissement de l'efficacité opérationnelle
- Réduction des coûts liés à la création des nouvelles fonctionnalités
- Accroissement de la capacité fournie en peu de temps

IBM comprend que dans 70 % des cas, l'adoption d'un cloud privé est motivée par la nécessité de moderniser les environnements d'application. Toutefois, la plupart des organisations envisagent la modernisation des applications de façon progressive, ce qui nécessite un paysage hybride et multi-cloud, dans lequel :

- des applications complexes et monolithiques qui s'exécutent généralement sur des grands systèmes ou des systèmes UNIX demeurent sur site ;
- les environnements x86 utilisés pour des systèmes d'enregistrement (SoR), ou les applications qui sont des charges de travail sensibles à la sécurité ou régulées, sont placés sur une infrastructure virtuelle ou un cloud privé ;
- les applications, telles que SAP ou des applications de calcul hautes performances, consomment des ressources bare metal ;
- les charges de travail sensibles à la sécurité ou certaines charges de travail régulées, qui peuvent être déplacées sur le cloud public, sont déplacées vers des environnements dédiés ;
- les systèmes d'engagement (SoE), tels que Web, mobile, IoT, AI ou Video, sont déplacés vers des clouds publics.

Par exemple, un modèle commun consiste à avoir des applications SOE frontales qui sont déployées en tant que conteneurs avec des bases de données et des logiciels intermédiaires existants déployés sur des machines virtuelles sur un cloud privé.

Votre infrastructure informatique et vos besoins métier étant uniques, votre approche de la modernisation doit vous permettre d'accélérer l'apport de valeur métier, de réduire les risques et de préserver vos investissements existants. IBM fournit uniquement une approche que vous pouvez personnaliser en fonction de vos besoins métier et technologiques spécifiques par rapport à la modernisation des applications.

Issu d'un ensemble de cinq documents, ce document fournit différentes vues des technologies utilisées dans le parcours de modernisation des applications vers {{site.data.keyword.cloud_notm}} :

* _vCenter Server et IBM Cloud Private_ - Guide en cours, qui constitue une architecture de référence pour le déploiement des plateformes suivantes :
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - Offre d'{{site.data.keyword.vmwaresolutions_short}}. Il s'agit d'une plateforme basée sur VMware qui est automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Private** – Plateforme applicative pour le développement et la gestion d'applications conteneurisées. ICP est un environnement intégré qui inclut l'orchestrateur de conteneurs Kubernetes, un registre d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance et une interface graphique à partir de laquelle vous pouvez déployer, gérer, surveiller et mettre à l'échelle vos applications de façon centralisée.
  - **{{site.data.keyword.cloud_notm}} Automation Manager** – Plateforme IaC (Infrastructure as Code) prête pour l'entreprise qui permet à partir d'un point unique de mettre à disposition des charges de travail basées sur des machines virtuelles, ainsi que des charges de travail Kubernetes en utilisant des modèles qui sont stockés et dont la version est gérée dans un référentiel.
* [vCenter Server et IBM Kubernetes Service](../vcsiks/vcsiks-intro.html) - Architecture de référence pour le déploiement des plateformes suivantes : 
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - Offre d'{{site.data.keyword.vmwaresolutions_short}}. Il s'agit d'une plateforme basée sur VMware qui est automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
  - **{{site.data.keyword.cloud_notm}} Kubernetes Service** – Service géré sur {{site.data.keyword.cloud_notm}} qui utilise Kubernetes comme moteur d'orchestration pour l'automatisation du déploiement, la mise à l'échelle et les opérations de conteneurs d'applications sur un cluster à service exclusif.
* [Mise en réseau de vCenter Server](../vcsnsxt/vcsnsxt-intro.html) - Ce guide met l'accent sur les technologies de réseau utilisées au sein de vCenter Server, ICP et IKS, par exemple, NSX-V, NSX-T et Calico. 
* [Guide Concept Car pour VMware et Skate Advisor](../vcscar/vcscar-intro.html) - Cette architecture de référence est un “concept car”, autrement dit, un mécanisme qui met en évidence et affiche les technologies permettant de résoudre les problèmes du monde réel. Nous avons voulu démontrer qu'il existe véritablement une interaction entre l'intelligence artificielle de Watson et l'apprentissage automatique. Au travers de la culture du skateboard, nous illustrons des services de cloud de manière unique. L'implémentation du “concept car” est une extension de l'application Acme Skateboard nommée Skate Advisor. Skate Advisor est un outil qui permet aux utilisateurs d'avoir des conversations sur les astuces en matière de skateboard avec un moteur entraîné par Watson.
* [VMware : Le parcours de modernisation de Stock Trader](../vcscontent/vcscontent-modjourney.html) - Notre cas d'utilisation de référence décrit une application WebSphere Application Server classique qui fait l'objet d'une modernisation à l'aide d'ICP, de contenu IBM Middleware, d'{{site.data.keyword.cloud_notm}} Kubernetes Service et de vCenter Server. Nous sommes tous engagés sur un parcours de cloud et nous sommes tous à différents stades de ce parcours. Au travers d'étapes incrémentielles planifiées par Jane et Todd, respectivement architecte d'application et architecte d'infrastructure de cloud, nous modernisons une application existante nommée Stock Trader. Ce cas d'utilisation illustre des exemples qui vous permettent de franchir chaque étape de votre parcours, et d'apporter de la valeur à votre entreprise, quelle que soit la taille de chaque étape. Nous nous concentrons sur quatre thèmes : applications, DevOps, intégration et gestion. Ces thèmes sont indissociables pour vous permettre d'atteindre vos objectifs, et de fait, en moderniser un sans vous soucier des autres engendrera des problèmes. 

### Liens connexes

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

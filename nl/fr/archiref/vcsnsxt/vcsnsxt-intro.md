---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Introduction à la mise en réseau de vCenter Server
{: #vcsnsxt-intro}

Ce document présente le parcours de modernisation des applications vers {{site.data.keyword.cloud}}, en mettant l'accent sur les aspects réseau des plateformes suivantes afin de permettre l'optimisation d'un environnement multi-cloud intégré pour la modernisation des applications :

- **VMware vCenter Server on IBM Cloud** - Offre d'{{site.data.keyword.vmwaresolutions_short}}. Il s'agit d'une plateforme basée sur VMware qui est automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
- **IBM Cloud Private** - Plateforme applicative pour le développement et la gestion d'applications conteneurisées, qui sont déployées sur une plateforme d'infrastructure virtuelle, telle que vCenter Server ou un environnement vSphere sur site.
- **{{site.data.keyword.containerlong_notm}}** - Service géré sur {{site.data.keyword.cloud_notm}} qui utilise Kubernetes comme moteur d'orchestration pour l'automatisation du déploiement, la mise à l'échelle et les opérations de conteneurs d'applications sur un cluster à service exclusif.

Les plus grands défis posés par la modernisation des applications sont la migration, la mise en réseau et la sécurité. vCenter Server, VMware Hybrid Cloud Extension (HCX), VMware NSX, {{site.data.keyword.containerlong_notm}} et {{site.data.keyword.icpfull_notm}} permettent de relever certains de ces défis. L'architecture de réseau ci-après décrit une approche qui utilise Acme Skateboards pour illustrer la connexion de composants répartis sur des environnements de cloud et sur site.

L'[aperçu NSX-T](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-techpreview) est un aperçu technologique permettant de décrire l'utilisation de transformateurs NSX-T (VMware NSX Transformer) dans une future architecture de référence. NSX-T a été conçu pour prendre en charge les structures et les architectures d'application comportant des points finaux et des piles technologiques hétérogènes. En plus de vSphere, ces environnements peuvent inclure d'autres hyperviseurs, KVM, des conteneurs et des serveurs bare metal. NSX-T permet aux équipes informatiques et aux équipes de développement de choisir les technologies les mieux adaptées à leurs applications. NSX-T est également conçu pour être géré, exploité et consommé par les organisations de développement en plus des équipes de mise en réseau.

## Modernisation des applications sur IBM Cloud
{: #vcsnsxt-intro-app-mod}

La modernisation des applications fait référence au processus de transition d'applications existantes pour utiliser de nouvelles approches de développement et de distribution sur le cloud. Aujourd'hui, les clients recherchent des approches innovantes et efficaces qui les aident à effectuer cette transition en tenant compte de la complexité de leur activité et de leurs applications.

Les pressions économiques imposent des commercialisations plus rapides. Votre patrimoine existant inclut non seulement des applications, mais également des données, des processus, une logique métier et des interfaces utilisateur, qui doivent tous être adaptés aux nouveaux besoins commerciaux.

Les avantages de la modernisation des applications sont les suivants :

- Amélioration de la productivité des développeurs
- Augmentation de l'efficacité opérationnelle
- Réduction du coût lié à la création de nouvelles fonctionnalités
- Extension de la capacité fournie en peu de temps

IBM comprend que dans 70 % des cas, l'adoption d'un cloud privé est motivée par la nécessité de moderniser les environnements d'application, toutefois, la plupart des organisations envisagent la modernisation des applications de façon progressive, ce qui nécessite un paysage hybride et multi-cloud, dans lequel :

- des applications complexes et monolithiques qui s'exécutent généralement sur des grands systèmes ou des systèmes UNIX demeurent sur site ;
- les environnements x86 utilisés pour des systèmes d'enregistrement (SoR), ou les applications qui sont des charges de travail sensibles à la sécurité ou régulées, sont placés sur une infrastructure virtuelle ou un cloud privé ;
- les applications, telles que SAP ou des applications de calcul hautes performances, consomment des ressources bare metal ;
- les charges de travail sensibles à la sécurité ou certaines charges de travail régulées, qui peuvent être déplacées sur le cloud public, sont déplacées vers des environnements dédiés ;
- les systèmes d'engagement (SoE), tels que Web, mobile, IoT, AI ou Video, sont déplacés vers des clouds publics.

Par exemple, un modèle commun consiste à avoir des applications SoE frontales qui sont déployées en tant que conteneurs avec des bases de données et des logiciels intermédiaires existants déployés sur des machines virtuelles sur un cloud privé.

Votre infrastructure informatique et vos besoins métier étant uniques, votre approche de la modernisation doit vous permettre d'accélérer l'apport de valeur métier, de réduire les délais de livraison, de réduire vos risques et de préserver vos investissements existants. IBM fournit ce type d'approche pour la modernisation des applications et vous pouvez la personnaliser en fonction de vos besoins métier et technologiques spécifiques.

Ce document fournit différentes vues des technologies utilisées dans le parcours de modernisation des applications vers {{site.data.keyword.cloud_notm}} :

* [vCenter Server et {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - Architecture de référence pour le déploiement des plateformes suivantes :
   - **VMware vCenter Server on IBM Cloud** - Offre d'{{site.data.keyword.vmwaresolutions_short}}. Il s'agit d'une plateforme basée sur VMware qui est automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.icpfull_notm}}** – {{site.data.keyword.icpfull_notm}} est une plateforme applicative pour le développement et la gestion d'applications conteneurisées. Il s'agit d'un environnement intégré qui inclut l'orchestrateur de conteneurs Kubernetes, un registre d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance et une interface graphique à partir de laquelle vous pouvez déployer, gérer, surveiller et mettre à l'échelle vos applications de façon centralisée.
   - **IBM Cloud Automation Manager** – CAM est une plateforme IaC (infrastructure as code) prête pour l'entreprise qui permet à partir d'un point unique de mettre à disposition des charges de travail basées sur des machines virtuelles, ainsi que des charges de travail Kubernetes en utilisant des modèles qui sont stockés et dont la version est gérée dans un référentiel.
* [vCenter Server et {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - Architecture de référence pour le déploiement des plateformes suivantes :
   - **VMware vCenter Server on IBM Cloud** - Offre d'{{site.data.keyword.vmwaresolutions_short}}. Il s'agit d'une plateforme basée sur VMware qui est automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
   - **{{site.data.keyword.containerlong_notm}}** – service géré sur {{site.data.keyword.cloud_notm}} qui utilise Kubernetes comme moteur d'orchestration pour l'automatisation du déploiement, la mise à l'échelle et les opérations de conteneurs d'applications sur un cluster à service exclusif.
* _Mise en réseau de vCenter Server_ - Le guide met l'accent sur les technologies de réseau utilisées pour l'intégration entre vCenter Server, {{site.data.keyword.icpfull_notm}} et {{site.data.keyword.containerlong_notm}}, par exemple, NSX-V et Calico, ainsi que sur l'aperçu technologique NSX-T.
* [Guide Concept Car pour VMware et Skate Advisor](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro) - Cette architecture de référence est un “concept car”, autrement dit, un mécanisme qui met en évidence et affiche les technologies permettant de résoudre les problèmes du monde réel. Nous avons voulu démontrer qu'il existe véritablement une interaction entre l'intelligence artificielle de Watson et l'apprentissage automatique. Au travers de la culture du skateboard, nous illustrons des services de cloud de manière unique. L'implémentation du “concept car” est une extension de l'application Acme Skateboard nommée Skate Advisor. Skate Advisor est un outil qui permet aux utilisateurs d'avoir des conversations sur les astuces en matière de skateboard avec un moteur entraîné par Watson.
* [VMware : Le parcours de modernisation de Stock Trader](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - Notre cas d'utilisation de référence décrit une application WebSphere Application Server classique qui fait l'objet d'une modernisation à l'aide d'{{site.data.keyword.cloud_notm}} Private, de contenu IBM Middleware, d'{{site.data.keyword.containerlong_notm}} et de vCenter Server on {{site.data.keyword.cloud_notm}}. Nous sommes tous engagés sur un parcours de cloud et nous sommes tous à différents stades de ce parcours. Au travers d'étapes incrémentielles planifiées par Jane et Todd, respectivement architecte d'application et architecte d'infrastructure de cloud, nous modernisons une application existante nommée Stock Trader. Ce cas d'utilisation illustre des exemples qui vous permettent de franchir chaque étape de votre parcours, et d'apporter de la valeur à votre entreprise, quelle que soit la taille de chaque étape. Nous nous concentrons sur quatre thèmes : applications, DevOps, intégration et gestion. Tous les thèmes sont indissociables pour vous permettre d'atteindre vos objectifs. En moderniser un thème, sans vous soucier des autres engendrera des problèmes.

## Liens connexes
{: #vcsnsxt-intro-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

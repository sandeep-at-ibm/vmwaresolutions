---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# Parcours de modernisation
{: #vcscontent-modjourney}

Cas d'utilisation de référence qui décrit la façon dont une application WebSphere Application Server classique est modernisée à l'aide d'{{site.data.keyword.cloud}} Private, de contenu IBM Middleware, d'{{site.data.keyword.containerlong_notm}} et de VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## La modernisation ne se limite pas aux applications
{: #vcscontent-modjourney-modernization}

Nous sommes tous engagés sur un parcours de cloud et nous sommes tous à différents stades de ce parcours. Ce cas d'utilisation se concentre sur la façon dont une application existante nommée Stock Trader est modernisée via des étapes incrémentielles planifiées par Jane et Todd, respectivement architecte d'application et architecte d'infrastructure de cloud. Ce cas d'utilisation illustre des exemples qui vous permettent de franchir chaque étape de votre parcours, et d'apporter de la valeur à votre entreprise, quelle que soit la taille de chaque étape.

Tout au long de ce parcours, nous allons concentrer nos efforts sur la modernisation de l'application Stock Trader. Pour moderniser complètement votre entreprise et en faire une entreprise native en cloud, les thèmes relatifs aux applications, à DevOps, à l'intégration et à la gestion doivent être examinés. Tous les thèmes sont indissociables pour vous permettre d'atteindre vos objectifs. En moderniser un thème, sans vous soucier des autres engendrera des problèmes.

## Motifs de modernisation
{: #vcscontent-modjourney-reasons}

### Modernisation des applications
{: #vcscontent-modjourney-app-mod}

L'objectif est de créer des applications natives en cloud qui évoluent et s'adaptent rapidement à l'évolution des demandes.

* Vous avez besoin de moderniser vos applications existantes et de créer de nouvelles applications natives en cloud afin de capturer l'imagination de vos clients.
* Vous avez besoin d'applications capables d'évoluer, d'atteindre une envergure mondiale, de s'adapter aux demandes, de changer, de s'améliorer et de basculer rapidement.

### Modernisation de DevOps
{: #vcscontent-modjourney-devops-mod}

Lorsque vous modernisez votre application, la façon dont vous distribuez cette application, le pipeline de distribution dans son ensemble, est modernisée de sorte que la nouvelle culture native en cloud qui est créée par vos développeurs soit appliquée au mode de distribution de l'application.

* Vous devez moderniser votre culture de développement et d'exploitation (et de sécurité) en même temps que vous modernisez vos applications.
* Il vous faut des équipes DevOps capables d'évoluer, d'atteindre une envergure mondiale, de s'adapter aux demandes, de changer, de s'améliorer et de basculer rapidement.

###  Modernisation de l'intégration
{: #vcscontent-modjourney-integration-mod}

Tout au long du parcours de modernisation, vos équipes doivent intégrer des actifs existants, de nouveaux services de cloud, vos données et de nouvelles connaissances obtenues à partir des analyses réalisées sur ces données.

* Lors de ce parcours, vous devez utiliser vos actifs existants de telle manière qu'ils puissent évoluer, atteindre une envergure mondiale, s'adapter aux demandes, changer, s'améliorer et basculer rapidement.
* Vous devez vous enrichir de nouveaux services cloud à chaque étape de ce parcours.
* Vous devez intégrer vos données et les connaissances obtenues à partir des analyses réalisées sur vos données.

### Gestion
{: #vcscontent-modjourney-mgmt}

Tout en modernisant vos applications, vous devez parallèlement moderniser vos pratiques de gestion. Les outils, la culture et les comportements de base relatifs à la gestion et à la maintenance d'une application modernisée sont très différents de ce qu'ils étaient.

* Vous devez gérer vos microservices et vos logiciels intermédiaires conteneurisés en utilisant les fonctions d'orchestration, de journalisation et de surveillance intégrées.
* Vous devez gérer vos plateformes hybrides multi-cloud dans le monde entier de telle manière qu'elles puissent évoluer, atteindre une envergure mondiale, s'adapter aux demandes, changer, s'améliorer et basculer rapidement.
* Vous devez automatiser la gestion de plusieurs clouds et les applications et les logiciels intermédiaires qui s'exécutent dessus.

## Présentation de Todd et de Jane
{: #vcscontent-modjourney-todd-jane}

Deux personnes sont au centre de notre parcours Stock Trader : Jane et Todd. Todd est en charge des opérations chez ACME et il est responsable des environnements d'infrastructure, de sécurité et de cloud, ainsi que des politiques visant à garantir que les charges de travail qui s'exécutent dans ces environnements soient conformes à différentes réglementations.

Responsable du développement pour la solution Stock Trader, Jane est à présent chargée de moderniser cette solution, autrement dit, elle doit collaborer avec ses équipes de développement pour modifier les outils, la culture et les plateformes de développement afin de remplacer la solution Stock Trader monolithique par une solution native en cloud bien gérée.

## Présentation de Stock Trader
{: #vcscontent-modjourney-meet-stock-trader}

Todd et Jane ont créé une application nommée Stock Trader qui s'exécute dans WebSphere. Bien qu'elle comporte une interface utilisateur basique, il s'agit d'une application fiable que les gestionnaires de portefeuille utilisent pour gérer leurs portefeuilles, notamment pour l'achat et la vente d'actions et l'affichage de niveaux de fidélité internes.

Stock Trader s'exécute dans WebSphere, repose sur un petit nombre de fichiers .war et utilise une base de données Db2 traditionnelle qui s'exécute dans le centre de données qu'ils utilisent depuis de nombreuses années. L'extension de cette application prend un certain temps en raison des dépendances entre les équipes d'infrastructure, les équipes de développement et les équipes qui gèrent les données.

Mais, si Stock Trader est parfait, toute l'entreprise aspire à quelque chose de mieux. Les gestionnaires produit veulent ajouter des médias sociaux à leur programme de fidélité. Jane est contente car elle peut restructurer l'application en microservices, et continuer de fournir des fonctions améliorées avec moins de dépendances. Todd est séduit par la notion de performances offertes par le cloud, mais il a encore besoin d'une gouvernance pour maintenir la conformité avec les politiques de l'entreprise.

## Etapes du parcours
{: #vcscontent-modjourney-steps}

Todd et Jane savent par expérience que pour obtenir un bon parcours de modernisation de solutions, il faut commencer par établir une feuille de route. Même si les plans sont sujets à modification, il est toujours bon d'avoir une vision à long terme de la solution que l'on souhaite obtenir et de définir une voie réaliste pour y parvenir. Chaque étape doit offrir une valeur ajoutée à l'entreprise, mais les étapes ne sont pas importantes au point d'entraîner de coûteuses interruptions aux clients.

Les étapes de Todd et de Jane tout au long du parcours Stock Trader sont les suivantes :
1. Migration des machines virtuelles Stock Trader dans {{site.data.keyword.cloud_notm}}. Grâce à cette étape, Todd aura moins besoin de gérer son propre matériel et le contenu VMware dans le centre de données local.

2. Transformation de la charge de travail Stock Trader issue de WebSphere Application Server en charge de travail Stock Trader dans des conteneurs. Cette étape augmente la résilience car le fait d'exécuter des conteneurs dans Kubernetes permet d'obtenir de l'orchestration et d'autres comportements spécifiques du cloud. Pour cela, Todd doit impérativement préparer une instance {{site.data.keyword.cloud_notm}} Private dans son environnement VMware vCenter Server on {{site.data.keyword.cloud_notm}}, puis travailler avec Jane et utiliser Transformation Advisor pour conteneuriser Stock Trader.

3. Restructuration et ajout des logiciels intermédiaires dans {{site.data.keyword.cloud_notm}} Private. Cette étape permet l'ajout de leurs logiciels intermédiaires existants dans un environnement de cloud et l'optimisation des comportements spécifiques du cloud. Elle permet également de rationaliser l'octroi de licence et de préparer la solution à être entièrement portable afin de pouvoir être utilisée dans d'autres environnements Kubernetes.

4. Enrichissement grâce à Watson et à d'autres services cloud publics. Cette étape peut valoriser considérablement l'expérience Stock Trader en faisant appel à des services d'intelligence artificielle et grâce à la possibilité de communiquer avec les centres de données de cloud présents dans le monde entier.

5. Création d'une véritable application hybride avec {{site.data.keyword.cloud_notm}} Kubernetes Service. Cette étape permet à Todd de disposer d'un service Kubernetes géré qui continue de se connecter à la même région de cloud que son instance {{site.data.keyword.cloud_notm}} Private. Elle permet également aux équipes de développement de Jane de disposer d'un cluster de développement et de test dont ils peuvent se servir à titre expérimental tout continuant d'accéder à la même source de donnes que leur cluster {{site.data.keyword.cloud_notm}} Private principal.

6. Modernisation de DevOps. Tout au long de ce parcours, Jane améliore sa façon de distribuer Stock Trader.

7. Modernisation de la gestion. Todd et Jane ont conjugué leurs efforts pour améliorer leur façon de gérer l'application Stock Trader et la plateforme sur laquelle elle s'exécute, y compris sur plusieurs environnements de cluster et de cloud.

## Liens connexes
{: #vcscontent-modjourney-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

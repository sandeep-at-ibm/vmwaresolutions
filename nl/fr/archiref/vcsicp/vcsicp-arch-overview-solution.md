---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Composants de la solution

## Composants VCS

Figure 1. Diagramme de l'environnement VCS
![Environnement VCS](vcsicp-vcsenv.svg)

### Contrôleur PSC (Platform Service Controller)

Le déploiement VCS utilise un seul contrôleur PSC externe installé sur un sous-réseau portable dans le réseau VLAN privé qui est associé à des machines virtuelles de gestion. Le routeur BCR (Back-end Customer Router) lui sert de passerelle par défaut.

### vCenter Server

A l'instar du contrôleur PSC, vCenter Server est déployé en tant que dispositif. De plus, vCenter Server est installé sur un sous-réseau portable sur le réseau VLAN privé qui est associé à des machines virtuelles de gestion. L'adresse IP affectée sur le routeur BCR pour ce sous-réseau spécifique lui sert de passerelle par défaut.

### NSX Manager

NSX Manager est déployé sur le cluster initial. De plus, NSX Manager se voit affecter une adresse IP VLAN provenant du bloc d'adresses portables privées conçu pour les composants de gestion et configuré avec les serveurs DNS et NTP

### Contrôleurs NSX

L'automatisation d'{{site.data.keyword.cloud}} déploie trois contrôleurs NSX dans le cluster initial. Les contrôleurs se voient affecter une adresse IP VLAN provenant du sous-réseau portable destiné aux composants de gestion.

### NSX Edge/DLR

Des paires de passerelles NSX ESG (Edge Services Gateway) sont déployées. Dans tous les cas, une paire de passerelles est utilisée pour le trafic sortant des composants d'automatisation qui résident sur le réseau privé. Pour vCenter Server et ICP, une seconde passerelle, appelée serveur de périphérie géré ICP, est déployée et configurée avec une liaison montante au réseau public et une interface qui est affectée au réseau privé. Les composants NSX requis, tels que le routeur DLR (Distributed Logical Router), les commutateurs logiques et les pare-feu peuvent être configurés par l'administrateur. Le [guide de mise en réseau de vCenter Server](../vcsnsxt/vcsnsxt-intro.html) contient davantage de détails relatifs à la conception du réseau. 

Le tableau ci-après répertorie les spécifications ESG/DLR pour ICP.

Tableau 1. Spécifications ESG pour ICP

Attribut  |  Spécification
--|--
Edge Service Gateway  |  Dispositif virtuel
Edge size	Large |   Nombre de vCPU	2
Memory	| Disque 1 Go	| 1000 Go sur magasin de données local

Tableau 2. Spécifications DLR pour ICP

Attribut  |  Spécification
--|--|
Distributed Logical Router | 	Dispositif virtuel
Edge size	Compact | Nombre de vCPU	1
Memory	| Disque de 512 Mo	| 1000 Go sur magasin de données local

## Composants ICP
{{site.data.keyword.cloud_notm}} Private est une plateforme applicative pour le développement et la gestion sur site d'applications conteneurisées. Il s'agit d'un environnement intégré pour la gestion de conteneurs qui inclut l'orchestrateur de conteneurs Kubernetes, un registre d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance.

Figure 2. Déploiement ICP virtuel avec VCS
![Déploiement ICP virtuel avec VCS](vcsicp-virtual-icp-deployment-vcs.svg)

###	Noeud d'amorçage

Un noeud d'amorçage (facultatif) est utilisé pour exécuter l'installation, la configuration, la mise à l'échelle du noeud et les mises à jour de cluster. Un seul noeud d'amorçage est requis pour un cluster. Vous pouvez utiliser un noeud unique pour le maître et l'amorçage.

### Noeud maître

Un noeud maître fournit des services de gestion et contrôle les noeuds worker dans un cluster. Les noeuds maître hébergent les processus responsables de l'allocation des ressources, de la maintenance des états, de la planification et de la surveillance. Parce qu'un environnement à haute disponibilité comporte plusieurs noeuds maître, en cas de défaillance du noeud maître principal, une logique de basculement promeut automatiquement un autre noeud dans le rôle de maître. Les hôtes qui peuvent servir de maître sont appelés candidats maître.

###	Noeud worker

Un noeud worker est un noeud qui fournit un environnement conteneurisé pour exécuter des tâches. Lorsque le nombre de demandes augmente, d'autres noeuds worker peuvent facilement être ajoutés à votre cluster afin d'améliorer les performances et l'efficience. Un cluster peut comporter tout nombre de noeuds worker, mais au moins un noeud worker est requis.

### Noeud proxy

Un noeud proxy est un noeud qui transmet une demande externe aux services créés dans votre cluster. Parce qu'un environnement à haute disponibilité comporte plusieurs noeuds proxy, en cas de défaillance du noeud proxy principal, une logique de basculement promeut automatiquement un autre noeud dans le rôle de proxy. Bien que vous puissiez utiliser un noeud unique comme maître et proxy, il est conseillé d'utiliser des noeuds proxy dédiés afin de réduire la charge sur le noeud maître. Un cluster doit comporter au moins un noeud proxy si l'équilibrage de charge est nécessaire dans le cluster.

### Noeud de gestion

Un noeud de gestion est un noeud facultatif qui héberge uniquement des services de gestion, tels que la surveillance, le décompte et la consignation. Configurer des noeuds de gestion dédiés, vous permet d'éviter que le noeud maître ne soit en surcharge. Vous pouvez activer le noeud de gestion uniquement lors de l'installation d'{{site.data.keyword.cloud_notm}} Private. 

###	Noeud VA

Un noeud VA (Vulnerability Advisor) est un noeud facultatif, utilisé pour l'exécution des services Vulnerability Advisor. Les services Vulnerability Advisor consomment un grand nombre de ressources. Si vous utilisez des services Vulnerability Advisor, spécifiez un noeud VA dédié.

Spécifications de machine virtuelle requises pour une instance ICP à haute disponibilité :

Tableau 3. Spécifications de machine virtuelle ICP

Noeud | 	Instances	| IP	| UC	| Mémoire RAM (Go)	| Disque (Go)
:-----|------------:|:----|----:|----------:|----------:|
Maître|	3	| IP (x3) VIP (x1)	| 4	| 64	| 200
Gestion	|3	| IP (x3)	|8	|64	|500
Proxy	| 3	| IP (x3)VIP (x1)	|2	|4	|150
Vulnerability Advisor	|3	| IP (x3)	| 4	| 16	|500
GlusterFS	| 3	| IP (x3)	|8	|16	|150
Worker	| 3-6	| IP (x3)	|4-8	|4	|150

CAM requiert une configuration d'UC virtuelle et de mémoire plus élevée pour les noeuds worker.

Tableau 4. Spécifications de machine virtuelle ICP

Noeud | 	Instances	| IP	| UC	| Mémoire RAM (Go)	| Disque (Go)
:-----|------------:|:----|----:|----------:|----------:|
worker  |  3 | IP (x3)  |  4-8 |16-20   |  150

## Composants CAM

{{site.data.keyword.cloud_notm}} Automation Manager (CAM) est une plateforme de gestion libre-service multi-cloud qui s'exécute sur ICP et permet aux développeurs et aux administrateurs de répondre aux besoins de l'entreprise. 

Fig 3. Référence des composants CAM
![Référence des composants CAM](vcsicp-cam-component-ref.svg)

### Proxy CAM

Fournit un accès proxy nginx dans CAM.

### Interface utilisateur CAM

Les composants de l'interface utilisateur sont répartis entre plusieurs conteneurs : interface utilisateur de connexions en cloud, bibliothèque d'interface utilisateur de modèles et interfaces utilisateur d'instances déployées.

### API CAM

Les API CAM sont réparties entre plusieurs conteneurs.

### Helm

Conteneur avec les fichiers binaires requis pour déployer des graphiques helm dans des clusters Kubernetes.

### Terraform

Conteneur avec les fichiers binaires requis pour déployer des ressources Terraform dans plusieurs clouds.

### Journaux

Emplacement des journaux de conteneur.

### Base de données Mongo

Base de données Core pour l'application CAM.

### Redis

La base de données Redis est utilisée pour stocker la mise en cache de sessions et les verrous dans CAM.

### Template Designer

Interface graphique permettant de créer des modèles Terraform, avec des fonctions glisser-déposer de modules Terraform.

### BD Maria

Base de données de l'application Template Designer.

### Liens connexes

* [Présentation de VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

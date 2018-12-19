---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Considérations opérationnelles

## Sauvegarde

### Sauvegarde VCS

Dans le cadre d'{{site.data.keyword.vmwaresolutions_full}}, le logiciel de sauvegarde Veeam peut éventuellement être déployé sur une instance de serveur virtuel {{site.data.keyword.cloud_notm}} à l'aide du stockage {{site.data.keyword.cloud_notm}} Endurance en dehors du cluster VMware. La finalité de ce logiciel est de sauvegarder les composants de gestion dans la solution. Pour plus d'informations sur l'offre, voir [Présentation de Veeam on {{site.data.keyword.cloud_notm}}](../../services/veeam_considerations.html). 

Il est essentiel de sauvegarder tous les composants NSX afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. Il ne suffit pas de sauvegarder les dispositifs virtuels NSX et la fonction de sauvegarde NSX dans NSX Manager doit être utilisée pour effectuer une sauvegarde appropriée. Pour ce faire, un serveur FTP ou SFTP doit être spécifié pour le référentiel des données de sauvegarde NSX. 

La sauvegarde NSX Manager contient toute la configuration NSX, y compris les contrôleurs, les entités de routage et de commutation logiques, la sécurité, les règles de pare-feu et tout ce que vous configurez dans l'interface utilisateur ou l'API NSX Manager. La base de données vCenter et les éléments connexes, tels que des commutateurs virtuels, doivent être sauvegardés séparément. Pour plus d'informations, voir [Sauvegarde de niveau fichier NSX](../solution/solution_backingup.html#nsx-file-based-backup). La sauvegarde de la configuration NSX doit être effectuée en même temps qu'une [sauvegarde de niveau fichier vCenter](../solution/solution_backingup.html#vcenter-file-based-backup). 

### Sauvegarde et reprise après incident pour IBM Cloud Private

Il est essentiel d'effectuer les sauvegardes d'un déploiement ICP afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. A noter le désaccord majeur suivant concernant la sauvegarde de machine virtuelle traditionnelle : chaque noeud maître ICP exécute un service *etcd*, or, la documentation *etcd* stipule clairement qu'il ne faut pas utiliser une sauvegarde de machine virtuelle traditionnelle pour restaurer le système.

Au niveau de la plateforme {{site.data.keyword.cloud_notm}} Private, vous devez sauvegarder les composants suivants :
- **etcd** - Utilisé pour stocker les ressources Kubernetes et les informations d'état Calico.
- **Docker Registry** - Référentiel d'images privé qui est utilisé pour stocker des fichiers image de conteneur. 
- **MongoDB** - Base de données qui est utilisée par le service de décompte, le serveur de référentiel Helm, le serveur d'API Helm, la configuration LDAP, le titulaire (espace de nom) et les configurations de rôle équipe/utilisateur/groupe d'utilisateurs.
- **MariaDB** - Base de données qui est utilisée par OIDC.
-	**Elasticsearch** - Stocke les journaux système et d'application.
-	**Prometheus** - Stocke les données de surveillance.
-	**Stockage de persistance** - Utilisé pour les services de gestion qui ont recours au fournisseur de stockage et de volume persistant {{site.data.keyword.cloud_notm}} Private ou Kubernetes. 

Vous pouvez utiliser la technologie de sauvegarde ou de restauration qui est fournie par le fournisseur de stockage. Un processus similaire peut également être appliqué à une application de votre utilisateur. Pour plus d'informations, voir [How to back up and restore {{site.data.keyword.cloud_notm}} Private blog](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8) ou [icp-backup GitHub](https://github.com/ibm-cloud-architecture/icp-backup/).

### Sauvegarde et reprise après incident pour CAM

Il est essentiel d'effectuer les sauvegardes d'un déploiement CAM afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. Dans le cadre de la sauvegarde CAM, le client doit impérativement sauvegarder les composants suivants :
-	**MongoDB** - Principale base de données CAM.
-	**MariaDB** - Utilisée par CAM Blueprint Designer.
-	**Systèmes de fichiers NFS/Gluster** - Les données CAM résident dans quatre volumes persistants.

### Sauvegarde et reprise après incident pour IKS

Une sauvegarde de la base de données etcd est fournie au client dans le cadre du service géré, mais il incombe au client de sauvegarder toutes les données d'application.

## Evolutivité

### Evolutivité VCS

Après le déploiement des hôtes initiaux, l'utilisateur peut ajouter de la capacité de calcul depuis le portail {{site.data.keyword.cloud_notm}} for VMware. 

Cette opération d'ajout à l'environnement peut être effectuée de l'une des façons suivantes :
-	Ajout de nouveaux sites gérés par des serveurs vCenter Server distincts.
-	Ajout de nouveaux clusters.
-	Ajout de nouveaux hôtes à un cluster existant.

#### Déploiements multisite

VMware on {{site.data.keyword.cloud_notm}} peut utiliser la présence de centres de données {{site.data.keyword.cloud_notm}} partout dans le monde et un réseau principal intégré pour déployer et rendre opérationnels divers scénarios d'utilisation multi-régions en une fraction du temps que prendrait la construction d'une telle infrastructure. Pour plus d'informations, voir la rubrique [Configuration multisite pour des instances vCenter Server on {{site.data.keyword.cloud_notm}}](../../vcenter/vc_multisite.html).

#### Ajout d'un nouveau cluster

L'utilisateur peut également ajouter de l'activité de calcul en créant un nouveau cluster à partir de la console et en commandant des hôtes qui seront ajoutés automatiquement au nouveau cluster. Cette option crée un cluster distinct dans l'environnement et offre aux utilisateurs la possibilité de dissocier physiquement et logiquement des charges de travail de gestion des charges de travail d'application, de dissocier des charges de travail en fonction d'autres caractéristiques (par exemple, un cluster de base de données Microsoft SQL) et de déployer des applications dans des topologies hautement disponibles. Pour plus d'informations, voir [Commande d'instances vCenter Server](../../vcenter/vc_orderinginstance.html).

#### Ajout à un cluster existant

L'utilisateur peut effectuer un ajout à un cluster existant en commandant des hôtes à partir de la console qui seront ajoutés automatiquement au nouveau cluster. Pour plus d'informations, voir [Extension et réduction de capacité pour des instances vCenter Server](../../vcenter/vc_addingremovingservers.html). L'utilisateur devra peut-être ajuster la règle de réservation haute disponibilité pour le cluster en fonction de ses exigences de réservation.

### Evolutivité ICP et IKS

En fonction de la capacité de calcul disponible sur site ou sur le cloud, l'utilisateur peut faire évoluer l'architecture de noeud à partir du noeud d'amorçage déployé initialement. Pour faire évoluer l'environnement, procédez comme suit :
-	Développez les noeuds worker ICP.
-	Développez et utiliser l'offre IKS. 

#### Développement ICP

Les noeuds de machine virtuelle worker ICP sont mis à l'échelle pour développer la capacité de calcul/l'application :
- Le client met à disposition une nouvelle machine virtuelle dans le même réseau VXLAN que celui où ICP est déployé.
- Les clients peuvent mettre à l'échelle des noeuds worker en mettant à disposition de nouvelles machines virtuelles, puis en se connectant au noeud d'amorçage et en exécutant une commande pour amener les nouveaux noeuds dans le cluster. Pour plus d'informations, voir [Ajout ou retrait de noeuds de cluster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html). 
- Utilisez CAM pour automatiser la mise à disposition de la machine virtuelle et l'exécution des commandes permettant de l'ajouter au cluster ICP.

#### Développement IKS

Les utilisateurs peuvent mettre à disposition un environnement IKS en utilisant le portail {{site.data.keyword.cloud_notm}} pour étendre et utiliser un environnement de conteneur. Pour plus d'informations, voir [Hybrid enhancements across {{site.data.keyword.cloud_notm}} Private and {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Hybrid_Enhancements_Across_IBM_Cloud_Private_and_IBM_Public_Cloud?lang=en_us).

Les déploiements d'application dans IKS peuvent être effectués à l'aide des méthodes suivantes :
-	Le développement de la connexion et des services IKS dans CAM et leur publication dans le catalogue ICP.
-	L'apport d'améliorations à Multi Cloud Manager pour la gestion des instances IKS.
-	L'interface de ligne de commande Helm.

### Liens connexes

* [Présentation de VCS Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

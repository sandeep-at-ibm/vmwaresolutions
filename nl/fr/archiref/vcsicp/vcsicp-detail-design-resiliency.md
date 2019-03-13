---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# Sauvegarde, reprise après incident et évolutivité
{: #vcsicp-detail-design-resiliency}

## Sauvegarde et reprise après incident
{: #vcsicp-detail-design-resiliency-backup-dr}

### Sauvegarde de VMware vCenter Server on IBM Cloud
{: #vcsicp-detail-design-resiliency-vcs-backup}

Dans le cadre d'{{site.data.keyword.vmwaresolutions_full}}, le logiciel de sauvegarde Veeam peut éventuellement être déployé sur une instance de serveur virtuel {{site.data.keyword.cloud_notm}} à l'aide d'{{site.data.keyword.cloud_notm}} Endurance Storage en dehors du cluster VMware. La finalité de ce logiciel est de sauvegarder les composants de gestion dans cette solution.

### Sauvegarde NSX
{: #vcsicp-detail-design-resiliency-nsx-backup}

Il est essentiel de sauvegarder correctement tous les composants NSX afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. Sauvegarder les machines virtuelles NSX ne suffit pas. En revanche, la fonction de sauvegarde NSX dans NSX Manager doit être utilisée pour effectuer une sauvegarde appropriée. Un serveur FTP ou SFTP doit être spécifié pour le référentiel des données de sauvegarde NSX.
La sauvegarde NSX Manager contient toute la configuration NSX, y compris les contrôleurs, les entités de routage et de commutation logiques, la sécurité, les règles de pare-feu et tout ce que vous configurez dans l'interface utilisateur ou l'API NSX Manager. La base de données vCenter et les éléments connexes, tels que des commutateurs virtuels, doivent être sauvegardés séparément. La sauvegarde de la configuration NSX doit être effectuée en même temps qu'une sauvegarde vCenter.

### Sauvegarde et reprise après incident pour IBM Cloud Private
{: #vcsicp-detail-design-resiliency-backup-dr-icp}

Il est essentiel d'effectuer les sauvegardes d'un déploiement {{site.data.keyword.icpfull_notm}} afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. En plus d'une sauvegarde de machine virtuelle traditionnelle, chaque noeud maître {{site.data.keyword.icpfull_notm}} exécute etcd. la documentation etcd stipule clairement qu'il ne faut pas utiliser une sauvegarde de machine virtuelle traditionnelle pour restaurer le système.

Au niveau de la plateforme {{site.data.keyword.icpfull_notm}}, vous devez sauvegarder les composants suivants :
- **Etcd** - Utilisé pour stocker les ressources Kubernetes et les informations d'état Calico.
- **Docker Registry** - Référentiel d'images privé qui est utilisé pour stocker des fichiers image de conteneur dans un référentiel d'images.
- **MongoDB** - Base de données qui est utilisée par le service de décompte, le serveur de référentiel Helm, le serveur d'API Helm, la configuration LDAP, le locataire (espace de nom) et les configurations de rôle équipe/utilisateur/groupe d'utilisateurs.
- **MariaDB** - Base de données qui est utilisée par OIDC.
- **Elasticsearch** - Stocke les journaux système et d'application.
- **Prometheus** - Stocke les données de surveillance.
- **Stockage de persistance** - Utilisé pour les services de gestion qui utilisent le fournisseur de stockage et de volume persistant {{site.data.keyword.icpfull_notm}} ou Kubernetes. Vous pouvez utiliser la technologie de sauvegarde ou de restauration qui est fournie par le fournisseur de stockage. Un processus similaire peut également être appliqué à une application de votre utilisateur.

### Sauvegarde et reprise après incident pour CAM
{: #vcsicp-detail-design-resiliency-backup-dr-cam}

Il est essentiel d'effectuer la sauvegarde d'un déploiement CAM afin de pouvoir restaurer l'état opérationnel du système dans l'éventualité d'une panne. Dans le cadre de la sauvegarde CAM, le client doit impérativement sauvegarder les composants suivants :
- **MongoDB** - Principale base de données CAM.
- **MariaDB** - Utilisée par CAM Blueprint Designer.
- **NFS/GlusterFS** - Les données CAM résident dans quatre volumes persistants.

### Sauvegarde et reprise après incident pour IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-resiliency-backup-dr-iks}

Des sauvegardes de la base de données etcd sont fournies au client dans le cadre du service géré, mais il incombe au client de sauvegarder toutes les données d'application.

## Evolutivité
{: #vcsicp-detail-design-resiliency-scalability}

### Evolutivité VCS
{: #vcsicp-detail-design-resiliency-vcs-scalability}

Après le déploiement des hôtes initiaux, l'utilisateur peut ajouter de la capacité de calcul depuis le portail {{site.data.keyword.cloud_notm}} for VMware.

Cette opération d'ajout à l'environnement peut être effectuée de l'une des trois façons suivantes :
- Ajout de nouveaux sites gérés par des serveurs vCenter Server distincts.
- Ajout de nouveaux clusters.
- Ajout de nouveaux hôtes à un cluster existant.

#### Déploiements multisite
{: #vcsicp-detail-design-resiliency-multi-site}

VMware on {{site.data.keyword.cloud_notm}} peut utiliser la présence de centres de données IBM Cloud partout dans le monde et un réseau principal intégré pour déployer et rendre opérationnels divers scénarios d'utilisation multi-régions en une fraction du temps que prendrait la construction d'une telle infrastructure.

#### Ajout d'un nouveau cluster
{: #vcsicp-detail-design-resiliency-scale-out-new}

L'utilisateur peut ajouter de l'activité de calcul en créant un nouveau cluster à partir de la console et en commandant des hôtes qui seront ajoutés automatiquement au nouveau cluster. Cette option crée un cluster distinct dans l'environnement et offre aux utilisateurs la possibilité de dissocier physiquement et logiquement des charges de travail de gestion des charges de travail d'application, de dissocier des charges de travail en fonction d'autres caractéristiques (par exemple, un cluster de base de données Microsoft SQL) et de déployer des applications dans des topologies hautement disponibles.

#### Ajout à un cluster existant
{: #vcsicp-detail-design-resiliency-scale-out-existing}

L'utilisateur peut effectuer un ajout à un cluster existant en commandant des hôtes à partir de la console qui seront ajoutés automatiquement au nouveau cluster. Les utilisateurs devront peut-être ajuster la règle de réservation haute disponibilité pour le cluster en fonction de leurs exigences de réservation.

### Evolutivité d'IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-scalability}

En fonction de la capacité de calcul disponible sur site ou sur le cloud, l'utilisateur peut faire évoluer l'architecture de noeud à partir du noeud d'amorçage déployé initialement.

Pour faire évoluer l'environnement, procédez comme suit :
- Développez les noeuds worker {{site.data.keyword.icpfull_notm}}.
- Développez et utilisez l'offre {{site.data.keyword.containerlong_notm}}.

#### Extension d'IBM Cloud Private
{: #vcsicp-detail-design-resiliency-icp-expansion}

Les noeuds de machine virtuelle worker {{site.data.keyword.icpfull_notm}} sont mis à l'échelle pour développer la capacité de calcul/l'application :
- Le client met à disposition une nouvelle machine virtuelle dans le même réseau VXLAN que celui où {{site.data.keyword.icpfull_notm}} est déployé.
- Les clients peuvent mettre à l'échelle des noeuds worker en mettant à disposition une nouvelle machine virtuelle, puis en se connectant au noeud d'amorçage et en exécutant une commande pour amener les nouveaux noeuds dans le cluster.
- Utilisez CAM pour automatiser la mise à disposition de la machine virtuelle et l'exécution des commandes à ajouter au cluster {{site.data.keyword.icpfull_notm}}.

###  Extension d'IBM Cloud Kubernetes Service
{: #vcsicp-detail-design-resiliency-iks-expansion}

Les utilisateurs peuvent mettre à disposition un environnement {{site.data.keyword.containerlong_notm}} via le portail {{site.data.keyword.cloud_notm}} pour étendre ou utiliser un environnement de conteneur.

Utilisez les éléments suivants pour les déploiements d'application dans {{site.data.keyword.containerlong_notm}} :
- Le développement de la connexion/des services {{site.data.keyword.containerlong_notm}} dans CAM et leur publication dans le catalogue {{site.data.keyword.icpfull_notm}}.
- L'apport d'améliorations à Multi-Cloud Manager pour la gestion des instances {{site.data.keyword.containerlong_notm}}.
- L'interface de ligne de commande Helm.
- L'utilisation de clusters multizone pour augmenter la haute disponibilité.

## Liens connexes
{: #vcsicp-detail-design-resiliency-related}

* [Ajout ou retrait de noeuds de cluster](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0.3/installing/modify_cluster.html)
* [Ajout de noeuds worker en redimensionnant un pool de noeuds worker existant](/docs/containers?topic=containers-clusters)
* [Procédure de sauvegarde et de restauration d'{{site.data.keyword.cloud_notm}} Private](https://medium.com/ibm-cloud/how-to-backup-and-restore-ibm-cloud-private-part-1-b6300dc1d7d8)
* [Sauvegarde {{site.data.keyword.icpfull_notm}} GitHub](https://github.com/ibm-cloud-architecture/icp-backup/)
* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

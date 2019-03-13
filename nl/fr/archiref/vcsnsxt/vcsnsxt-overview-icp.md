---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# IBM Cloud Private
{: #vcsnsxt-overview-icp}

{{site.data.keyword.icpfull_notm}} est une plateforme applicative pour le développement et la gestion d'applications conteneurisées. Il s'agit d'un environnement intégré qui inclut l'orchestrateur de conteneurs Kubernetes, un registre d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance et une interface graphique à partir de laquelle vous pouvez déployer, gérer, surveiller et mettre à l'échelle vos applications de façon centralisée.

{{site.data.keyword.cloud_notm}} Private propose les fonctions suivantes :
-	**Programme d'installation unifié** – Installation et configuration rapides d'un cluster basé sur Kubernetes avec des noeuds maître, worker et proxy à l'aide d'un programme d'installation Ansible.
-	**Console de gestion {{site.data.keyword.cloud_notm}} Private** – Vous permet de gérer, surveiller et traiter les incidents liés à vos applications et à votre cluster à partir d'une console de gestion unique, centralisée et sécurisée.
-	**Registre d'images Docker privé** - Ce registre local possède les mêmes fonctions que Docker Hub à ceci près qu'il vous permet également de limiter les utilisateurs qui peuvent afficher ou extraire des images.
-	**Catalogue de logiciels et de services conteneurisés** - Le catalogue fournit un emplacement centralisé à partir duquel vous pouvez rechercher et installer des packages dans votre cluster. Des packages pour des produits IBM supplémentaires sont disponibles à partir de référentiels organisés qui sont inclus dans la liste de référentiels {{site.data.keyword.cloud_notm}} Private.
-	**Réseaux de locataires isolés** - Calico permet d'améliorer les performances et l'isolement du réseau au sein de votre cluster. Avec Calico, vous pouvez créer un sous-réseau isolé pour chaque projet au sein de votre cluster. Cet isolement du réseau offre une sécurité accrue lors de la transmission des données et réduit les risques de compromettre des applications et leurs données. Calico facilite également la création de politiques réseau permettant d'activer un contrôle à granularité fine sur le partage d'objets au sein d'un espace de nom unique.
-	**Surveillance et journalisation robustes avec la pile ELK** - {{site.data.keyword.cloud_notm}} Private utilise Elasticsearch, Logstash, Filebeat et Heapster pour la collecte, le stockage et l'interrogation des journaux et des métriques. Ce processus de surveillance et de journalisation fournit un magasin centralisé pour tous les journaux et métriques, de meilleures performances, ainsi qu'une stabilité accrue lorsque vous accédez à et analysez des journaux et métriques.

## Composants IBM Cloud Private
{: #vcsnsxt-overview-icp-comp}

Un cluster {{site.data.keyword.cloud_notm}} Private comporte quatre classes de noeuds : amorçage, maître, worker et proxy. Vous pouvez éventuellement spécifier des noeuds de gestion, Vulnerability Advisor et etcd dans votre cluster.
-	**Noeud d'amorçage** - Un noeud d'amorçage est utilisé pour exécuter l'installation, la configuration, la mise à l'échelle du noeud et les mises à jour de cluster.
-	**Noeud maître** - Un noeud maître fournit des services de gestion et contrôle les noeuds worker dans un cluster. Les noeuds maître hébergent les processus responsables de l'allocation des ressources, de la maintenance des états, de la planification et de la surveillance.
-	**Noeuds worker** - Un noeud worker est un noeud qui fournit un environnement conteneurisé pour exécuter des tâches. Lorsque le nombre de demandes augmente, d'autres noeuds worker peuvent facilement être ajoutés à votre cluster afin d'améliorer les performances et l'efficience.
-	**Noeud proxy** - Un noeud proxy est un noeud qui transmet une demande externe aux services créés dans votre cluster.
-	**Noeud de gestion** - Un noeud de gestion est un noeud facultatif qui héberge uniquement des services de gestion, tels que la surveillance, le décompte et la journalisation. Configurer des noeuds de gestion dédiés vous permet d'éviter que le noeud maître ne soit en surcharge.
-	**Noeud Vulnerability Advisor (VA)** - Un noeud VA est un noeud facultatif, utilisé pour l'exécution des services Vulnerability Advisor.
-	Noeud **etcd** - Un noeud etcd est un noeud facultatif, utilisé pour l'exécution du magasin de valeurs de clé distribuées etcd.

## Mise en réseau IBM Cloud Private
{: #vcsnsxt-overview-icp-networking}

La gestion de réseau {{site.data.keyword.icpfull_notm}} est facilitée par l'utilisation de Calico.
Calico utilise la couche 3 ou la couche réseau du modèle Open System Interconnection (OSI). Calico utilise le protocole BGP (Border Gateway Protocol) pour créer des tables de routage qui facilitent la communication entre les noeuds worker.

Pour plus d'informations sur la mise en réseau Calico, voir [{{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-overview-iks).

## Liens connexes
{: #vcsnsxt-overview-icp-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

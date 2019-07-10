---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-15"

subcollection: vmware-solutions


---

# Mise à jour des clusters vSAN
{: #vum-updating-vsan}

vSAN génère des lignes de base de système et des groupes de lignes de base pour les utiliser avec vSphere Update Manager (VUM). Vous pouvez vous servir de ces lignes de base recommandées pour mettre à jour des logiciels, des correctifs et des extensions pour les hôtes vSphere ESXi figurant dans votre instance VMware vCenter Server on {{site.data.keyword.cloud_notm}} à l'aide de vSAN. vSAN 6.6.1 (et versions ultérieures) génère des recommandations de build automatisées pour les clusters vSAN. vSAN combine les informations du guide de compatibilité VMware et du catalogue de versions de vSAN avec des informations sur les versions de vSphere ESXi installées.

Ces mises à jour recommandées offrent la meilleure édition disponible pour conserver votre matériel dans un état pris en charge.
* **Lignes de base de système vSAN** - Les recommandations de build vSAN sont fournies à l'aide de lignes de base de système vSAN pour VUM. vSAN génère un groupe de lignes de base pour chaque cluster vSAN. Ces lignes de base sont répertoriées dans le panneau Baselines de l'onglet Baselines and Groups. VUM analyse automatiquement chaque cluster vSAN pour vérifier la conformité par rapport au groupe de lignes de base. Cependant, pour mettre à niveau votre cluster vSAN, vous devez manuellement corriger la ligne de base de système via VUM. Vous pouvez corriger une ligne de base de système vSAN sur un hôte unique ou sur l'ensemble du cluster.
* **Catalogue de versions vSAN** - Le catalogue de versions vSAN contient des informations sur les versions disponibles, sur l'ordre de préférence des versions et sur les correctifs critiques nécessaires pour chaque version. vSAN nécessite une connexion à Internet pour accéder au catalogue de versions. Vous n'avez pas besoin d'être inscrit au programme d'amélioration de l'expérience client (CEIP) de vSAN pour accéder au catalogue des versions.
* Utilisation des **recommandations de build vSAN** - VUM vérifie les versions vSphere ESXi installées par rapport aux informations de la liste de compatibilité du matériel (HCL) du Guide de compatibilité VMware. Il détermine le chemin de mise à niveau correct pour chaque cluster vSAN, en fonction du catalogue de versions de vSAN actuel. vSAN comprend également les pilotes et les mises à jour de correctifs pour la version recommandée dans sa ligne de base de système. Les recommandations de build vSAN permettent de garantir que chaque cluster vSAN reste à l'état actuel ou supérieur en terme de compatibilité du matériel. Si le matériel du cluster vSAN ne figure pas dans la liste HCL, vSAN recommande d'effectuer la mise à niveau vers la version la plus récente.

La mise à niveau du cluster vSAN s'effectue selon la séquence de tâches suivante :
* **Activation de vSAN Online Health Workflow** – Ce workflow active les lignes de base vSAN dans VUM de sorte que les mises à jour puissent être consultées et corrigées. Il doit être réalisé uniquement au début pour activer vSAN avec VUM
* **Prérequis** – Familiarisez-vous avec les prérequis, le processus et les restrictions
* **Mise à niveau de vCenter Server Appliance**. Pour plus d'informations, voir [Mise à jour de VCSA et instances vCenter liées à SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).
* **Mise à niveau des hôtes vSphere ESXi** – Pour plus d'informations, voir [Création de lignes de base et association à des objets d'inventaire](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines).
* **Mise à niveau du format de disque vSAN** - Reportez-vous à Mise à jour du format de disque vSAN. La mise à niveau du format de disque est facultative mais pour obtenir les meilleurs résultats, mettez à niveaux les objets pour utiliser la version la plus récente. Le format de disque expose votre environnement à la panoplie complète des fonctions de vSAN.

## Activation de vSAN Online Health Workflow
{: #vum-updating-vsan-enable-vsan-workflow}

Exécutez les tâches présentées dans cette section pour rendre les lignes de base vSAN disponibles dans VUM. vSAN 6.6.1 (et versions ultérieures) fournit un processus de mise à jour automatisé sans faille pour garantir qu'un cluster vSAN est à jour avec la meilleure version disponible pour que votre instance VMware vCenter Server on {{site.data.keyword.cloud_notm}} reste dans un état pris en charge selon les recommandations suivantes :
* **Recommandations de version vSAN** - ces recommandations sont automatiquement générées à l'aide des informations du Guide de compatibilité VMware, du catalogue des versions de vSAN et en tenant compte de la configuration matérielle sous-jacente. Cela comprend également les pilotes et les mises à jour de correctifs nécessaires pour la version recommandée dans sa ligne de base de système.
* **Recommandations de build vSAN** - ces recommandations garantissent que les clusters restent à l'état de compatibilité actuel ou amélioré du matériel.

Vérifiez que VCSA correspond à vCenter 6.5 Patch 2 ou une version plus récente avant de continuer car ces versions corrigent des erreurs liées à l'utilisation d'un proxy. Pour plus d'informations, voir [Mise à jour de VCSA et instances vCenter liées à SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).

Pour voir les mises à jour de vSAN dans VUM et vérifier que le workflow vSAN online Health est suivi, procédez comme suit. Par conséquent, vSAN Online Health doit se connecter aux sites `vcsa.vmware.com` et `vmware.com` pour effectuer ces contrôles de santé en ligne. Pour activer vSAN Online Health Workflow, nous devons :
* Configurer VCSA pour utiliser le proxy.
* Configurer vSAN pour utiliser le proxy.
* Activer le programme d'amélioration de l'expérience client (CEIP).
* Effectuer un test de téléchargement et confirmer que le chargement a abouti.

La première étape consiste à ajouter vos données d'identification my.vmware.com au moteur des recommandations de build de vSAN (vSAN Build Recommendation Engine). Lorsque la connexion est établie, vSAN génère un groupe de lignes de base de mises à jour recommandées pour chaque cluster vSAN. Les lignes de base de système vSAN sont répertoriées dans le panneau Baselines de l'onglet Baselines and Groups.

### Configuration de VCSA pour utiliser le proxy
{: #vum-updating-vsan-config-vcsa-proxy}

1.	Dans le navigateur de votre serveur intermédiaire, connectez-vous à l'interface de gestion de VCSA `https://<vCenter ip>:5480`
2.	En utilisant les données d'identification de la console BM Cloud for VMware Solutions, connectez-vous à l'interface de gestion VCSA en tant qu'utilisateur racine (root).
3.	Dans l'interface de gestion de dispositif de vCenter Server, cliquez sur **Networking**, puis sur **Manage**.
4.	Pour configurer un serveur proxy, dans le panneau Paramètres proxy, cliquez sur **Edit**.
5.	Sélectionnez **Use a proxy server**, entrez les paramètres du serveur proxy et cliquez sur **OK**.

Il existe des rapports dans lesquels les informations de proxy sont définies uniquement pour HTTP et pas pour HTTPS. Pour configurer les informations de proxy pour le trafic HTTPS, vous devez d'abord activer cette option. Une fois connecté à VCSA via SSH, utilisez la commande proxy.get pour afficher la configuration et confirmer que les paramètres HTTPS ne sont pas définis.

Si les paramètres HTTPS ne sont pas définis, utilisez la commande suivante :
  `proxy.set --protocol https --server ``<proxy ip>`` --port 3128`

### Configuration de vSAN pour utiliser le proxy
{: #vum-updating-vsan-config-vsan-proxy}

1. Accédez à **Home** > **Hosts and Clusters**, sélectionnez **vSAN cluster** dans le panneau de navigation, puis sélectionnez l'onglet **Configure** et accédez à **vSAN**, puis à **General**. Faites défiler l'écran jusqu'à la section **Internet Connectivity** et cliquez sur **Edit**.
2. Entrez l'adresse IP et le numéro de port du proxy, puis cliquez sur **OK**.

### Activation du programme d'amélioration de l'expérience client (CEIP)
{: #vum-updating-vsan-enable-ceip}

Cette étape est facultative. En utilisant le client vSphere Web Client, accédez à **Home** > **Administration** > **Customer Experience Improvement Program**, puis cliquez sur **Join**.

### Effectuer un test de téléchargement et confirmer que le téléchargement a abouti
{: #vum-updating-vsan-complete-upload}

1. Dans vSphere Web Client, accédez à **Home** > **Hosts and Clusters**. Sélectionnez le cluster nécessaire, puis sélectionnez l'onglet **Monitor** et la page **vSAN**, puis cliquez sur **Health**. Cliquez sur **Enable Online Health**.
2. Cliquez sur le bouton **Retest** et patientez jusqu'à la fin du processus.
3. Une nouvelle vérification apparaît dans Health pour _Online health connectivity_ et le bouton **Enable Online Health** devient **Retest with Online Health**.
4. Cliquez sur **Retest with Online Health** pour démarrer le premier téléchargement et patientez jusqu'à la fin du processus en examinant le statut dans le panneau Recent Tasks. Le nom du test devient Online health (Last check: just now).
5. A la fin du processus, dans la fenêtre Health, faites défiler l'écran vers le bas et développez vSAN Build Recommendation, puis cliquez sur **vSAN Build Recommendation Engine Health**.
6. Cliquez sur **Login to my.vmware.com** et entrez vos données d'identification. Une fois le processus terminé, la zone **Test Result** passe à l'état **Passed**.
7. Cliquez sur l'onglet **Update Manager** et le cluster vSAN est ajouté aux lignes de base.

## Prérequis
{: #vum-updating-vsan-prereq}

Avant de lancer le processus de mise à niveau de vSAN, vérifiez que les conditions requises suivantes sont remplies :
* Consultez les articles de la base de connaissances de VMware, ainsi que les problèmes de compatibilité connus entre votre version actuelle de vSAN et la version vSAN cible souhaitée
* **L'environnement vSphere est à jour** :
  - VCSA doit être au niveau de correctif supérieur ou égal aux hôtes vSphere ESXi. Mettez à jour VCSA si nécessaire
  - Tous les hôtes doivent exécuter la même génération d'ESXi. Si les versions de l'hôte vSphere ESXi ne correspondent pas, effectuez une mise à jour
* **Tous les disques vSAN doivent être sains** :
  - Aucun disque n'est à l'état d'échec ou absent. Vous pouvez le vérifier via la vue **vSAN Disk Management** dans le client vSphere Web Client. Accédez à **Home** > **Hosts and Clusters**, sélectionnez **vSAN Cluster** et cliquez sur l'onglet **vSAN** puis sur **Physical Disks**. Faites défiler tous les disques et consultez le statut vSAN Health Status.
  - Aucun objet vSAN n'est inaccessible. Vous pouvez le vérifier avec le service **vSAN Health Service** en cliquant sur **Home** > **Hosts and Clusters**, puis en sélectionnant **vSAN Cluster**. Cliquez sur l'onglet **Monitor**, **vSAN**, puis sur **Health**. Consultez les résultats de test.
  - Il n'y a aucune resynchronisation active au lancement du processus de mise à niveau. Cliquez sur **Home** > **Hosts and Clusters**, sélectionnez **vSAN Cluster** et cliquez sur l'onglet **vSAN** puis sur **Resync Components**. _Le nombre de composants de resynchronisation doit être 0_. Une activité de resynchronisation est attendue lors du processus de mise à niveau, car les données doivent être synchronisées après les redémarrages d'hôte.
* **Préparation de l'hôte vSphere ESXi** - Lorsque vous placez un hôte en mode maintenance dans un cluster vSAN, vous disposez de trois options au choix :
  - **No data migration** - Si vous sélectionnez cette option, vSAN n'évacue aucune données en provenance de cet hôte. Si vous mettez hors tension ou retirez l'hôte du cluster, certaines machines virtuelles risquent de ne plus être accessibles.
  - **Ensure availability** - Si vous sélectionnez cette option, vSAN vous permet de placer l'hôte en mode maintenance plus rapidement qu'avec l'option Full data migration et autorise l'accès aux machines virtuelles dans l'environnement.
  - **Full data migration**
* **Sortie du mode maintenance et resynchronisation** - Lorsque l'hôte vSphere ESXi est mis à niveau et n'est plus en mode maintenance, une resynchronisation est effectuée. Vous pouvez le voir sur le client Web. Vérifiez qu'elle est terminée avant de passer à l'hôte suivant. Une resynchronisation se produit lorsque l'hôte qui a été mis à jour peut contribuer à nouveau au magasin de données vSAN. Il est essentiel d'attendre la fin de la resynchronisation pour garantir qu'il n'y a aucune perte de données.
* **Après avoir lancé la mise à niveau d'un cluster vSAN** :
  - N'essayez pas de mettre à niveau un cluster en introduisant de nouvelles versions dans le cluster et en migrant des charges de travail.
  - Si vous introduisez de nouveaux hôtes, vérifiez qu'ils ont la même version initiale et mettez-les à niveau en même temps que le reste du cluster.
  - Si vous ajoutez ou remplacez des disques lors d'une mise à niveau, vérifiez qu'ils sont formatés avec la version de format sur disque existante, le cas échéant.
  - Par conséquent, certains changements de comportement de vSAN sont contrôlés par le format sur disque et il est important que des versions de format sur disque plus récentes ne soient pas introduites dans un cluster avec un mélange de versions.

## Mise à niveau de vCenter Server Appliance
{: #vum-updating-vsan-upgrade-vcsa}

Pour plus d'informations, voir [Mise à jour de VCSA et instances vCenter liées à SSO](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vcsa).

##	Mise à niveau des hôtes vSphere ESXi
{: #vum-updating-vsan-upgrade-hosts}

Pour plus d'informations, voir [Création de lignes de base et association à des objets d'inventaire](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-baselines).

##	Mise à niveau du format de disque vSAN
{: #vum-updating-vsan-upgrade-vsan}

La console RVC (Ruby vSphere Console) est une interface de ligne de commande Ruby pour vSphere. Elle peut être utilisée pour gérer VMware vSphere ESXi et vCenter. L'inventaire vSphere est présenté sous forme d'arborescence, ce qui vous permet de naviguer et d'exécuter des commandes sur les objets vCenter.

De nombreuses tâches administratives de base peuvent s'effectuer avec plus d'efficacité qu'en cliquant dans le client vSphere. La console RVC est entièrement implémentée dans le dispositif VCSA et reliée au dispositif par une connexion SSH.
1. Utilisez SSH pour vous connecter à VCSA et ouvrez une session avec l'utilisateur racine et le mot de passe fournis sur la console ICVS.
2. A l'invite, entrez :
  `rvc Administrator@vsphere.local@localhost` et appuyez sur **Entrée**.
3. Entrez le mot de passe de l'administrateur fourni sur la console ICVS. Vous êtes maintenant à la racine du système de fichiers virtuel, entrez ls et appuyez sur **Entrée**, vous voyez ceci :
  `0 /
  1 localhost/``

5. Entrez `cd 1`, appuyez sur Entrée puis entrez `ls` et appuyez sur **Entrée**. Vous voyez ceci :
  `0 / datacenter1 (datacenter)`

6. Tapez `cd 0`, puis appuyez sur Entrée et entrez `ls` et appuyez sur **Entrée**. Vous obtenez :

  `0 storage/
  1 computers [host]/
  2 networks [network]/
  3 datastores [datastore]/
  4 vms [vm]/`

7. Entrez `cd 1`, appuyez sur **Entrée**, puis entrez `ls` et appuyez sur **Entrée**. Vous voyez votre cluster :
  `0 cluster1 (cluster)``

8. Utilisez les commandes VSAN sur ce cluster. Pour vérifier le statut du disque, entrez `vsan.disks_stats 0` et appuyez sur **Entrée**.

9. Vérifiez que l'état de santé (Health Status) de tous les disques est OK. Lancez ensuite la mise à niveau en entrant `vsan.ondisk_upgrade 0`, puis en appuyant sur **Entrée**.

10. Selon la taille de votre vSAN, cette tâche peut prendre beaucoup de temps. Lorsqu'elle est terminée, entrez `vsan.objstatusreport 0`, puis appuyez sur **Entrée** pour vérifier que les versions des objets sont mises à niveau avec le nouveau format sur disque.

11. La mise à niveau du cluster VSAN est à présent terminée. Entrez `exit` et appuyez sur **Entrée** pour quitter la console RVC.

## Liens connexes
{: #vum-updating-vsan-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (démonstrations)

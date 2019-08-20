---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Transformation de la charge de travail Stock Trader issue de WebSphere Application Server en charge de travail Stock Trader dans des conteneurs
{: #vcscontent-stocktrmod}

La prochaine étape du parcours de modernisation de Stock Trader consiste à transformer la charge de travail, qui s'exécute dans des machines virtuelles, afin qu'elle s'exécute dans des conteneurs.

Pour continuer, Todd et Jane exécutent Transformation Advisor afin d'analyser la charge de travail Stock Trader, identifier une éventuelle complexité de migration et recommander des modifications. Lorsqu'ils sont prêts, ils utilisent Transformation Advisor pour déployer Stock Trader dans des conteneurs Liberty qui s'exécutent dans {{site.data.keyword.icpfull_notm}}.

## Préparation d'IBM Cloud Private
{: #vcscontent-stocktrmod-prep-icp}

Todd doit commencer par installer {{site.data.keyword.icpfull_notm}}. Puisqu'il dispose de son environnement VMware on {{site.data.keyword.cloud_notm}}, il décide d'utiliser l'offre {{site.data.keyword.cloud_notm}} Private Hosted qui lui fournit une instance {{site.data.keyword.icpfull_notm}} complète s'exécutant sur des machines virtuelles VMware dans {{site.data.keyword.cloud_notm}}.

Le tableau de bord par défaut fournit une interface utilisateur complète permettant de gérer le cluster, la sécurité et le stockage Kubernetes et d'effectuer un déploiement à partir du catalogue.

### Préparation du stockage
{: #vcscontent-stocktrmod-prep-storage}

{{site.data.keyword.cloud_notm}} Private Hosted est configuré de manière à être prêt à l'emploi avec GlusterFS et fournit le stockage de fichiers sur des machines virtuelles en tant que noeuds GlusterFS dédiés. L'intérêt de GlusterFS est qu'il active la mise à disposition dynamique. Si Todd le souhaite, il peut configurer des machines virtuelles supplémentaires en tant que serveurs NFS.

Puisque Todd voulait avoir un serveur NFS à sa disposition, il a identifié une machine virtuelle nommée ‘toddnfs’ et exécuté ces [étapes](https://help.ubuntu.com/community/SettingUpNFSHowTo).

Todd exécute les commandes suivantes pour créer un nouveau serveur NFS :

`ssh root@toodnfs.acme.com`

`apt-get install nfs-kernel-server`

`mkdir -p /shared`

`chown nobody:nogroup /shared`

`vi /etc/exports`

Ensuite, Todd ajoute la ligne suivante :

`/shared \*(rw,no_subtree_check,async,insecure,no_root_squash)`

`systemctl restart nfs-kernel-server`

Todd exécute ensuite la commande suivante sur chaque machine virtuelle afin d'installer NFS sur chaque machine virtuelle worker {{site.data.keyword.icpfull_notm}} :

`sudo apt-get update`

`sudo apt-get install nfs-common`

Todd exécute la commande suivante pour vérifier la version installée :

`apt-cache policy nfs-common`

A chaque fois qu'un nouveau volume NFS est nécessaire, Todd exécute la commande suivante pour en créer un :

`cd /shared`

`mkdir -p <foldername>`

`chmod 777 <foldername>`

### Préparation de la sécurité d'image
{: #vcscontent-stocktrmod-prep-img-sec}

Dans {{site.data.keyword.icpfull_notm}} V3.1, la sécurité est améliorée en exigeant qu'une politique d'image soit mise en place avant qu'une image soit extraite dans une instance {{site.data.keyword.icpfull_notm}}. Cette amélioration nécessite que vous ajoutiez une politique d'image là où les images IBM résident, *dockerhub/ibmcom*, et dans le magasin Docker.

La politique ibmcloud-default-cluster-image-policy est fournie par défaut et s'applique aux images IBM présentes dans docker.io/ibmcom/\*, mais, dans la mesure où Db2 et d'autres contenus IBM se trouvent dans le magasin Docker, ce dernier requiert une autre politique d'image, *docker.io/store/ibmcorp/*.

En outre, certains contenus nécessitent qu'une politique de sécurité de pod soit définie afin de permettre un accès spécifique pour un pod. Par exemple, Db2 requiert une politique pour les clients qui exécutent Db2 dans un espace de nom autre que l'espace de nom par défaut ('default’).

Pour en savoir plus, voir l'[IBM Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.1.0/manage_cluster/enable_pod_security.html).

## Déploiement de Transformation Advisor et de Microclimate
{: #vcscontent-stocktrmod-deploy-tam}

Une fois que {{site.data.keyword.icpfull_notm}} est opérationnel, Todd installe Transformation Advisor, en même temps que Microclimate. Il ouvre le [catalogue](https://www.ibm.com/cloud/private/architecture) et affiche tout le contenu disponible.

Todd recherche Transformation Advisor et Microclimate et les installe à l'aide des instructions de fichier Readme fournies lorsqu'il clique sur la charte Helm.

### Exécution de Transformation Advisor
{: #vcscontent-stocktrmod-run-trans-advisor}

Pour exécuter Transformation Advisor, Jane ajoute le collecteur de données dans la machine virtuelle qui exécute Stock Trader dans WebSphere et ouvre l'interface utilisateur [Transformation
Advisor](https://developer.ibm.com/recipes/tutorials/using-the-transformation-advisor-on-ibm-cloud-private/) pour afficher les résultats.

Jane clique sur Stock Trader et voit la recommandation invitant à exécuter chaque fichier War dans Liberty et à exécuter la majeure partie de la migration de façon modérée. Jane clique sur les détails de la migration et voit que Transformation Advisor fournit des fichiers de déploiement qu'elle peut utiliser pour terminer la migration. Après avoir téléchargé les fichiers binaires dans Transformation Advisor, Jane utilise les API fournies par Microclimate pour déployer les conteneurs Liberty.

Au final, les options de présentation de Stock Trader sont les suivantes :
* Conteneur Liberty unique - Si Jane déploie un environnement d'exécution Liberty et ajoute son application Stock Trader dans ce conteneur.
* Plusieurs conteneurs Liberty - Un pour chaque fichier .war conformément aux recommandations de Transformation Advisor pour Stock Trader.

Todd n'a pas modifié la source de données durant l'étape de transformation. Transformation Advisor prend la configuration de source de données WebSphere Application Server Network Deployment et l'ajoute au fichier server.xml du conteneur Liberty.
{:important}

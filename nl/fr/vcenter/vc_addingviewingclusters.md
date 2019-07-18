---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server add cluster, view cluster vCenter Server, delete cluster vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Ajout, affichage et suppression de clusters pour des instances vCenter Server
{: #vc_addingviewingclusters}

Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés sous **cluster1**.

Vous pouvez ajouter vos propres clusters à vos instances VMware vCenter Server afin d'étendre la capacité de calcul et de stockage. Au sein d'un cluster, vous pouvez gérer des serveurs ESXi afin d'optimiser l'allocation des ressources et la haute disponibilité. Lorsque vous n'en avez plus besoin, supprimez les clusters que vous avez ajoutés à vos instances.

La fonction de suppression de cluster est disponible uniquement pour les instances qui ont été déployées dans (ou mises à niveau vers) la version 2.3 et les versions ultérieures.
{:note}

## Ajout de clusters à des instances vCenter Server
{: #vc_addingviewingclusters-adding}

### Avant d'ajouter des clusters
{: #vc_addingviewingclusters-before-add}

* Dans la mesure du possible, vous devez ajouter les clusters à l'aide de la console {{site.data.keyword.vmwaresolutions_full}} car les modifications apportées au client VMware vSphere Web Client ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. Par conséquent, ajoutez des clusters à vCenter Server uniquement pour les clusters sur site ou les clusters que vous ne pouvez ou ne voulez pas gérer dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Pour les instances déployées dans (ou mises à niveau vers) la version 2.5 et des versions ultérieures, le nombre de clusters, d'hôtes et de machines virtuelles détermine la limite maximum relative au nombre de clusters que vous pouvez ajouter. Vous devez respecter les règles et limites de dimensionnement VMware pour votre déploiement. Pour plus d'informations sur les limites maximum, voir [VMware Configuration Maximums](https://configmax.vmware.com/home){:external}.
* Pour les instances déployées dans (ou mises à niveau vers) la version 2.0, 2.3, ou 2.4, vous pouvez ajouter jusqu'à 10 clusters.
* Pour les instances déployées dans la version 2.1 ou dans des versions antérieures, vous pouvez ajouter jusqu'à cinq clusters.

### Paramètres système
{: #vc_addingviewingclusters-adding-sys-settings}

Lorsque vous ajoutez un cluster pour une instance vCenter Server, vous devez spécifier les paramètres suivants :

#### Nom de cluster
{: #vc_addingviewingclusters-adding-cluster-name}

Le nom du cluster qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom de cluster doit commencer et se terminer par un caractère alphanumérique.
* Le nombre maximal de caractères autorisés est 30.
* Le nom de cluster doit être unique au sein de l'instance vCenter Server.

#### Emplacement de centre de données
{: #vc_addingviewingclusters-adding-dc-location}

L'emplacement de l'{{site.data.keyword.CloudDataCent}} du cluster est, par défaut, l'{{site.data.keyword.CloudDataCent_notm}} de l'instance vCenter Server. Vous pouvez déployer le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui de l'instance déployée, sous réserve que la latence du réseau entre les deux {{site.data.keyword.CloudDataCents_notm}} soit inférieure à 150 ms. Pour vérifier la latence du réseau, vous pouvez utiliser un outil tel que [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass).

Si vous déployez le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} ou pod d'infrastructure {{site.data.keyword.cloud_notm}}, trois VLAN supplémentaires sont commandés pour être utilisés avec les serveurs {{site.data.keyword.baremetal_short}} commandés.

### Paramètres de serveur bare metal
{: #vc_addingviewingclusters-bare-metal-settings}

Vous pouvez choisir l'option **Skylake**, **Certifiés SAP** ou **Broadwell**. Les options peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

#### Skylake
{: #vc_addingviewingclusters-adding-skylake}

Avec l'option **Skylake**, un certain nombre d'options est disponible pour les paramètres **Modèle UC** et **Mémoire RAM**. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
{: caption="Tableau 1. Options pour les serveurs Skylake {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Certifiés SAP
{: #vc_addingviewingclusters-adding-sap}

Lorsque vous sélectionnez **Certifiés SAP**, vous ne pouvez pas modifier les paramètres d'UC ou de mémoire RAM.

En fonction de vos besoins, sélectionnez une configuration de serveur bare metal :
* Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/192 Go de mémoire RAM
* Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/384 Go de mémoire RAM
* Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/768 Go de mémoire RAM
* Processeur Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz/512 Go de mémoire RAM
* Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,2 GHz/1024 Go de mémoire RAM
* Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,2 GHz/2048 Go de mémoire RAM
* Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,2 GHz/4096 Go de mémoire RAM

#### Broadwell
{: #vc_addingviewingclusters-adding-broadwell}

Avec l'option **Broadwell**, un certain nombre d'options est disponible pour les paramètres **Modèle UC** et **Mémoire RAM**. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/40 coeurs au total, 1,9 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
| Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,2 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
{: caption="Tableau 2. Options pour les serveurs Broadwell {{site.data.keyword.baremetal_short}}" caption-side="top"}

#### Nombre de serveurs bare metal
{: #vc_addingviewingclusters-adding-bare-metal-number}

* Tous les serveurs que vous commandez ont la même configuration.
* Pour le stockage vSAN, vous pouvez commander entre 4 et 59 serveurs.
* Pour le stockage NFS, vous pouvez commander entre 2 et 59 serveurs. Cependant, pour les charges de travail de production, un minimum de 3 serveurs est recommandé. Pour plus d'informations, voir [Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-).

### Paramètres de stockage
{: #vc_addingviewingclusters-adding-storage-settings}

Les paramètres de stockage varient en fonction de la configuration de serveur bare metal et du type de stockage que vous sélectionnez.

#### Stockage vSAN
{: #vc_addingviewingclusters-adding-vsan-storage}

Spécifiez les options vSAN suivantes :
* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Si vous souhaitez augmenter la capacité au-delà de la limite de 10 disques, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de 12 disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée.

  L'option **Hautes performances avec Intel Optane** n'est disponible que pour les modèles d'unités centrales Skylake.
  {:note}

* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.
* **Licence vSAN** : utilisez la licence VMware fournie par IBM pour le composant vSAN en sélectionnant **Inclure avec achat** ou fournissez votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant votre propre clé de licence

Si votre cluster initial était de type vSAN, tous les clusters vSAN supplémentaires utilisent la même licence vSAN et ont la même configuration que le cluster vSAN initial. C'est également le cas si vSAN est sélectionné pour être déployé dans un cluster de l'instance (initial ou supplémentaire). La première fois, un message vous demande la licence vSAN (licence achetée ou la vôtre) et l'édition. Ensuite, la prochaine fois que vous sélectionnerez vSAN pour un nouveau cluster, la licence que vous avez choisie initialement sera réutilisée.

#### Stockage NFS
{: #vc_addingviewingclusters-adding-nfs-storage}

Lorsque vous sélectionnez **Stockage NFS**, vous pouvez ajouter un stockage partagé de niveau fichier pour votre instance dans lequel tous les partages utilisent les mêmes paramètres ou vous pouvez spécifier des paramètres de configuration différents pour chaque partage de fichiers. Spécifiez les options NFS suivantes :

Le nombre de partages de fichiers doit être compris entre 1 et 32.
{:note}

* **Configurer les partages individuellement** : permet de spécifier des paramètres de configuration différents pour chaque partage de fichiers.
* **Nombre de partages** : lorsque vous souhaitez utiliser le même paramètre de configuration pour chaque partage de fichiers, spécifiez le nombre de partages de fichiers pour le stockage partagé NFS que vous souhaitez ajouter.
* **Taille** : sélectionnez la capacité qui répond à vos besoins de stockage partagé.
* **Performances** : sélectionnez la valeur IOPS (opérations d'entrée/sortie par seconde) par Go adaptée à vos besoins en matière de charge de travail.
* **Ajouter NFS** : permet d'ajouter des partages de fichiers individuels avec des paramètres de configuration différents.

Détails relatifs au niveau de performance :

| Option        | Détails       |
|:------------- |:------------- |
| 0,25 IOPS/Go | Cette option est conçue pour les charges de travail qui ne sont pas souvent utilisées. Exemples d'applications : données de coffre, hébergement de bases de données de grande taille avec des données existantes ou images de disque virtuel de système de mémoire virtuelle en tant que sauvegarde. |
| 2 IOPS/Go | Cette option est adaptée à la plupart des charges de travail d'usage général. Entre autres exemples d'application, citons l'hébergement de petites bases de données, la sauvegarde d'applications Web ou les images de disque de machine virtuelle pour un hyperviseur. |
| 4 IOPS/Go | Cette option est adaptée aux charges de travail de grande intensité qui ont un pourcentage élevé de données actives simultanément. Les bases de données transactionnelles en sont un exemple. |
| 10 IOPS/Go | Cette option est adaptée aux types de charge de travail les plus exigeants, tels que les analyses. Les bases de données à transactions élevées et autres bases de données sensibles aux performances en sont des exemples. Ce niveau de performance est limité à une capacité maximale de 4 To par partage de fichiers. |
{: caption="Tableau 3. Options de niveau de performance NFS" caption-side="top"}

### Disques locaux
{: #vc_addingviewingclusters-adding-local-disks}

L'option Disques locaux est disponible uniquement pour la configuration de processeur Quad Intel Xeon E7-8890 v4 Bare Metal **certifié SAP**. Indiquez les options suivantes :
* **Nombre de disques **: sélectionnez le nombre de disques que vous voulez ajouter.
* **Type de disque **: sélectionnez une option pour le type de disque dont vous avez besoin.

### Paramètres d'octroi de licence
{: #vc_addingviewingclusters-adding-licensing-settings}

Spécifiez l'option d'octroi de licence pour le composant VMware vSphere dans le cluster :
* Si vous êtes un partenaire commercial, la licence vCenter (édition Enterprise Plus) est incluse et achetée en votre nom.
* Si vous n'êtes pas un partenaire commercial, vous pouvez utiliser les licences VMware fournies par IBM pour ce composant en sélectionnant **Inclure avec achat** ou vous pouvez fournir votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant votre propre clé de licence.

### Paramètres d'interface réseau
{: #vc_addingviewingclusters-adding-network-interface-settings}

Les paramètres d'activation de carte d'interface réseau varient selon que vous sélectionnez **Réseau public et réseau privé** ou **Réseau privé uniquement**. Les services complémentaires suivants nécessitent des cartes d'interface réseau publiques et ne sont pas disponibles si vous sélectionnez l'option privée :

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Récapitulatif de la commande
{: #vc_addingviewingclusters-adding-order-summary}

Selon la configuration que vous avez sélectionnée pour le cluster, le coût estimé est généré et affiché instantanément dans la section **Récapitulatif de la commande** sur le panneau de droite. Cliquez sur **Détails concernant la tarification** pour générer un document PDF contenant le récapitulatif des coûts pour les ressources {{site.data.keyword.vmwaresolutions_short}}.

Vous pouvez également ajouter les ressources mises à disposition à l’outil d’estimation {{site.data.keyword.cloud_notm}} en cliquant sur **Ajouter à l'estimation**. Cela est utile si vous souhaitez estimer le coût des ressources {{site.data.keyword.vmwaresolutions_short}} sélectionnées avec d'autres ressources {{site.data.keyword.cloud_notm}} que vous pourriez envisager d'acheter.

## Procédure d'ajout de clusters à des instances vCenter Server
{: #vc_addingviewingclusters-adding-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à laquelle vous souhaitez ajouter des clusters.

   Assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas ajouter de clusters à l'instance.
   {:note}
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche et cliquez sur **Ajouter** dans l'angle supérieur droit du tableau **CLUSTERS**.
4. Sur la page **Ajouter un cluster**, entrez le nom du cluster.
5. Si vous souhaitez héberger le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui dans lequel l'instance est hébergée, sous **Serveur bare metal**, cochez la case **Sélectionner un autre emplacement** et choisissez l'{{site.data.keyword.CloudDataCent_notm}} dans lequel héberger l'instance.
6. Procédez à la configuration du serveur bare metal.
   * Si vous avez sélectionné **Skylake** ou **Broadwell**, renseignez les zones **Modèle d'UC**, **Mémoire RAM** et **Nombre de serveurs {{site.data.keyword.baremetal_short}}**.
   * Si vous avez sélectionné **Certifiés SAP**, spécifiez le modèle d'UC.
7. Procédez à la configuration du stockage.
  * Si vous sélectionnez **Stockage vSAN**, spécifiez les types de disque pour les disques de cache et de capacité, le nombre de disques et l'édition de licence vSAN. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
  * Si vous sélectionnez **Stockage NFS** et que vous souhaitez ajouter et configurer les mêmes paramètres pour tous les partages de fichiers, renseignez les zones **Nombre de partages**, **Performances** et **Taille (Go)**.
  * Si vous sélectionnez **Stockage NFS** et que vous souhaitez ajouter et configurer des partages de fichiers individuellement, sélectionnez **Configurer les partages individuellement**. Ensuite, cliquez sur l'icône **+** en regard du libellé **Ajout de stockage partagé** et sélectionnez une valeur pour les zones **Performances** et **Taille (Go)** pour chaque partage de fichiers. Vous devez sélectionner au moins un partage de fichiers.
  * Si vous sélectionnez **Disques locaux**, indiquez le nombre et le type de disque.
8. Spécifiez les paramètres d'interface réseau.
8. Spécifiez de quelle manière la clé de licence vSphere est fournie :
  * Si vous êtes un partenaire commercial, la licence vCenter (édition Enterprise Plus) est incluse et achetée en votre nom.
  * Si vous n'êtes pas un partenaire commercial, vous pouvez sélectionnez l'une des options suivantes :
      * Si vous voulez que de nouvelles licences soient achetées en votre nom, sélectionnez **Inclure avec achat** pour le composant.
      * Si vous voulez utiliser votre propre licence VMware pour le composant, sélectionnez **Je fournirai** et entrez votre clé de licence.
9. Sélectionnez le paramètre réseau **Réseau public et réseau privé** ou **réseau privé uniquement**.
10. Sur la page **Récapitulatif de la commande**, vérifiez la configuration du cluster avant d'ajouter celui-ci.
   1. Passez en revue les paramètres du cluster.
   2. Passez en revue le coût estimé du cluster. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
   3. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant d'ajouter le cluster.
   4. Cliquez sur **Mettre à disposition**.

### Que se passe-t-il après l'ajout de clusters à des instances vCenter Server ?
{: #vc_addingviewingclusters-adding-results}

1. Le déploiement du cluster démarre automatiquement et celui-ci prend le statut **Initialisation en cours**. Vous pouvez vérifier le statut du déploiement en affichant l'historique de déploiement sur la page **Récapitulatif** de l'instance.
2. Lorsque le cluster est prêt pour utilisation, il prend le statut **Prêt à l'emploi**. Le cluster qui vient d'être ajouté est activé avec vSphere haute disponibilité et vSphere Distributed Resource Scheduler (DRS).

Vous ne pouvez pas modifier le nom du cluster. La modification du nom du cluster peut entraîner l'échec d'opérations d'ajout ou de suppression de serveurs ESXi dans le cluster.
{:important}

## Procédure d'affichage des clusters dans les instances vCenter Server
{: #vc_addingviewingclusters-viewing-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous voulez afficher les clusters.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, consultez le récapitulatif concernant les clusters :
  * **Nom** : nom du cluster.
  * **Serveurs ESXi** : nombre de serveurs ESXi dans le cluster.
  * **Stockage** : type de stockage utilisé par le cluster.
  * **Emplacement de centre de données** : centre de données IBM Cloud où est hébergé le cluster.
  * **Pod** : pod où est déployé le cluster.
  * **Statut** : statut du cluster. Ce statut peut prendre l'une des valeurs suivantes :
    <dl class="dl">
        <dt class="dt dlterm">Initialisation en cours</dt>
        <dd class="dd">Le cluster est en cours de création et de configuration.</dd>
        <dt class="dt dlterm">Modification en cours</dt>
        <dd class="dd">Le cluster est en cours de modification.</dd>
        <dt class="dt dlterm">Prêt à l'emploi</dt>
        <dd class="dd">Le cluster est prêt pour utilisation.</dd>
        <dt class="dt dlterm">Suppression en cours</dt>
        <dd class="dd">Le cluster est en cours de suppression.</dd>
        <dt class="dt dlterm">Supprimé</dt>
        <dd class="dd">Le cluster est supprimé.</dd>
    </dl>
  * **Actions** : cliquez sur l'icône **Supprimer** pour supprimer le cluster.
4. Cliquez sur un nom de cluster pour afficher les détails relatifs au serveur ESXi, au stockage et à l'interface réseau. 

Détails relatifs au serveur ESXi :

| Elément        | Description       |  
|:------------- |:------------- |
| Nom | Le nom du serveur ESXi a le format suivant :<br> `<host_prefix><n>.<subdomain_label>.<root_domain>` <br> où :<br> `host_prefix` est le préfixe du nom d'hôte<br> `n` est la séquence du serveur<br> `subdomain_label` est le libellé de sous-domaine<br> `root_domain` est le nom du domaine racine |
| Version | Version du serveur ESXi. |
| Données d'identification | Nom d'utilisateur et mot de passe d'accès au serveur ESXi. |
| Adresse IP privée | Adresse IP privée du serveur ESXi. |
| Statut | Statut du serveur ESXi, qui peut avoir l'une des valeurs suivantes :<br> **Ajouté** : le serveur ESXi est ajouté et prêt à être utilisé.<br> **Ajout en cours** : le serveur ESXi est en cours d'ajout.<br> **Suppression en cours** : le serveur ESXi est en cours de suppression. |
{: caption="Tableau 4. Informations relatives au serveur ESXi" caption-side="top"}

Développez le serveur ESXi pour plus de détails : 

| Elément        | Description       |  
|:------------- |:------------- |
| UC | Spécification d'UC des serveurs ESXi du cluster. |
| Mémoire | Taille de mémoire totale des serveurs ESXi du cluster. |
| Disques vSAN personnalisés | Nombre de disques vSAN dans le cluster, ainsi que le type et la capacité des disques. |
| Disques de cache vSAN | Type et nombre de disques de cache vSAN. |
| Utilisation en réseau |Paramètres d'activation de la carte d'interface réseau (NIC) des Réseaux public et privé ou du Réseau privé uniquement. |
{: caption="Tableau 5. Informations supplémentaires relatives au serveur ESXi" caption-side="top"}

Détails relatifs au stockage :

| Elément        | Description       |  
|:------------- |:------------- |
| Nom | Nom du magasin de données. |
| Taille | Capacité du stockage. |
| IOPS/Go | Niveau de performance du stockage. |
| Protocole NFS | Version NFS du stockage. |
{: caption="Tableau 6. Informations relatives au stockage" caption-side="top"}

Détails relatifs à l'interface réseau :

| Elément        | Description       |  
|:------------- |:------------- |
| Numéro de VLAN | Numéro unique de VLAN.  |
| Description | Description du réseau local virtuel.  |
| Emplacement | Emplacement du centre de données. |
| Route principale | Route principale du VLAN. |
{: caption="Tableau 7. Interface réseau - Détails VLAN" caption-side="top"}

Cliquez sur **Afficher la ressource** pour accéder aux détails du réseau local virtuel.

Détails relatifs au sous-réseau :

| Elément        | Description       |  
|:------------- |:------------- |
| Nom | Nom du sous-réseau. Cliquez sur le nom pour accéder aux détails du sous-réseau. |
| Type | Type de sous-réseau : principal ou portable. |
| Description | Description du sous-réseau. |
{: caption="Tableau 8. Interface réseau - Détails de sous-réseau" caption-side="top"}

Détails relatifs à l'adresse IP :

| Elément        | Description       |  
|:------------- |:------------- |
| IP | Adresse IP. |
| Statut | Statut de l'adresse IP. |
| Description |Description de l'adresse IP.  |
{: caption="Tableau 9. Interface réseau - Détails d'adresse IP" caption-side="top"}

## Suppression de clusters des instances vCenter Server
{: #vc_addingviewingclusters-deleting}

Vous souhaiterez peut-être supprimer un cluster d'une instance si vous n'en avez plus besoin.

### Avant de supprimer des clusters
{: #vc_addingviewingclusters-deleting-prereq}

* Utilisez cette procédure pour supprimer des clusters des instances qui sont déployées dans la version 2.3 ou dans des versions ultérieures.
* Pour les clusters déployés dans des instances V2.2 ou antérieures, vous devez mettre à niveau l'instance vers la version 2.3 si vous souhaitez supprimer les clusters que vous lui avez ajoutés.
* Dans la mesure du possible, vous devez supprimer les clusters à l'aide de la console {{site.data.keyword.vmwaresolutions_full}} car les modifications apportées au client VMware vSphere Web Client ne sont pas synchronisées avec la console {{site.data.keyword.vmwaresolutions_short}}. Par conséquent, supprimez des clusters de vCenter Server uniquement en cas de clusters sur site ou de clusters que vous ne pouvez ou ne voulez pas gérer dans la console {{site.data.keyword.vmwaresolutions_short}}.
* Vous ne pouvez supprimer qu'un seul cluster à la fois. Pour supprimer plusieurs clusters, vous devez le faire de manière séquentielle. Attendez que le cluster précédent soit supprimé avant de supprimer le cluster suivant.
* Assurez-vous que tous les noeuds présents dans un cluster sont sous tension et opérationnels avant de supprimer le cluster.
* Lorsque vous supprimez un cluster, toutes les machines virtuelles présentes sur le cluster sont également supprimées et ne peuvent pas être récupérées. Si vous souhaitez conserver les machines virtuelles, faites-les migrer vers d'autres clusters.
* Le cluster par défaut ne peut pas être supprimé.

### Procédure de suppression de clusters des instances vCenter Server
{: #vc_addingviewingclusters-deleting-procedure}

1. Dans la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Ressources** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez supprimer les clusters.

   Assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas supprimer de clusters de l'instance.
   {:note}

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, localisez le cluster que vous souhaitez supprimer et cliquez sur l'icône **Supprimer** dans la colonne **Actions**.
4. Confirmez que vous avez terminé la migration de machines virtuelles vers d'autres clusters, le cas échéant, et que vous souhaitez supprimer le cluster.

## Liens connexes
{: #vc_addingviewingclusters-related}

* [Affichage des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)

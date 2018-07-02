---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# Ajout, affichage et suppression de clusters pour des instances VMware Federal

Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés sous **cluster1**.

Vous pouvez ajouter des clusters à vos instances VMware Federal Server afin d'étendre la capacité de calcul et de stockage. Au sein d'un cluster, vous pouvez gérer des serveurs ESXi afin d'optimiser l'allocation des ressources et la haute disponibilité. Lorsque vous n'en avez plus besoin, vous pouvez supprimer les clusters que vous avez ajoutés à vos instances.

**Disponibilité** : le dispositif d'ajout et de suppression de clusters est disponible uniquement pour les instances qui ont été déployées dans (ou mises à niveau vers) la version 2.3 et des éditions ultérieures.

## Ajout de clusters à des instances VMware Federal

Vous pouvez ajouter jusqu'à 10 clusters à une instance. Lorsque vous ajoutez un cluster pour une instance VMware Federal, vous devez spécifier les paramètres suivants :

### Paramètres système

Lorsque vous ajoutez un cluster pour une instance VMware Federal, vous devez spécifier les paramètres suivants :

#### Nom de cluster

Le nom du cluster qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom de cluster doit commencer et se terminer par un caractère alphanumérique.
* Le nom de cluster ne doit pas dépasser 30 caractères.
* Le nom de cluster doit être unique au sein de l'instance VMware Federal.

#### Emplacement de centre de données

Le centre de données du cluster est, par défaut, le centre de données de l'instance VMware Federal.

### Paramètres de serveur bare metal

#### Personnalisée

Indiquez le modèle d'UC et la mémoire RAM du serveur bare metal. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée. 

Tableau 1. Options pour les serveurs {{site.data.keyword.baremetal_short}} personnalisés

| Options d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

#### Nombre de serveurs bare metal

Un minimum de 2 serveurs {{site.data.keyword.baremetal_short}} est requis pour un cluster.

Pour les instances VMware Federal déployées dans la version 2.1 ou des éditions ultérieures, vous pouvez ajouter jusqu'à 59 serveurs {{site.data.keyword.baremetal_short}} pour un cluster et entre 1 et 59 serveurs ESXi à la fois.

Après le déploiement, vous pouvez créer jusqu'à quatre clusters supplémentaires. Pour les paramètres de stockage vSAN, 4 serveurs sont nécessaires pour le cluster initial et pour les clusters d'après déploiement.

<!--When there are more than 51 ESXi servers in the initial cluster of an instance, the HCX on {{site.data.keyword.cloud_notm}} service cannot be installed into the instance. Because the HCX service requires 8 IPs in the vMotion subnet from the initial cluster, if the number of ESXi servers exceeds 51, no IPs in the vMotion subnet can be available for HCX service.-->

### Paramètres de stockage

Les paramètres de stockage varient selon que vous sélectionnez l'option vSAN, NFS ou Stockage NFS personnalisé.

#### Stockage vSAN

Pour vSAN, spécifiez les options de stockage suivantes :

* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez la capacité qui répond à vos besoins de stockage partagé.
* **Nombre de disques de capacité vSAN** : sélectionnez le nombre de disques que vous voulez ajouter pour le stockage partagé vSAN. Le nombre de disques doit être de 2, 4, 6 ou 8.
* Sélectionnez l'édition de licence VMware vSAN 6.6 (Advanced ou Enterprise).

Si votre cluster initial était de type vSAN, tous les clusters vSAN supplémentaires utilisent la même licence vSAN et ont la même configuration que le cluster vSAN initial. C'est également le cas si vSAN est sélectionné pour être déployé dans un cluster de l'instance (initial ou supplémentaire). La première fois, un message s'affiche pour vous demander d'entrer la licence vSAN et l'édition. Ensuite, chaque fois que vous sélectionnez vSAN pour un cluster supplémentaire, vos choix initiaux sont réutilisés.

#### Stockage NFS

Lorsque vous sélectionnez **Stockage NFS**, vous pouvez ajouter un stockage partagé de niveau fichier pour votre instance dans lequel tous les partages utilisent les mêmes paramètres ou vous pouvez spécifier des paramètres de configuration différents pour chaque partage de fichiers. Spécifiez les options NFS suivantes :

**Remarque :** le nombre de partages de fichiers doit être compris entre 1 et 32. 

* **Configurer les partages individuellement** : permet de spécifier des paramètres de configuration différents pour chaque partage de fichiers. 
* **Nombre de partages** : lorsque vous utilisez le même paramètre de configuration pour chaque partage de fichiers, spécifiez le nombre de partages de fichiers pour le stockage partagé NFS que vous souhaitez ajouter. 
* **Taille** : sélectionnez la capacité qui répond à vos besoins de stockage partagé.
* **Performances** : permet de sélectionner la valeur IOPS (Input/output Operations Per Second) par Go adaptée à vos besoins en matière de charge de travail. 
* **Ajouter NFS** : permet d'ajouter des partages de fichiers individuels qui utiliseront des paramètres de configuration différents. 

Tableau 2. Options de niveau de performance NFS

| Option        | Détails       |
  |:------------- |:------------- |
  | 2 IOPS/Go | Cette option est adaptée à la plupart des charges de travail d'usage général. Entre autres exemples d'application, citons l'hébergement de petites bases de données, la sauvegarde d'applications Web ou les images de disque de machine virtuelle pour un hyperviseur. |
  | 4 IOPS/Go | Cette option est adaptée aux charges de travail de grande intensité qui ont un pourcentage élevé de données actives simultanément. Les bases de données transactionnelles en sont un exemple. |
  | 10 IOPS/Go | Cette option est adaptée aux types de charge de travail les plus exigeants, tels que les analyses. Les bases de données à transactions élevées et autres bases de données sensibles aux performances en sont des exemples. Ce niveau de performance est limité à une capacité maximale de 4 To par partage de fichiers.|

### Paramètres d'octroi de licence

Licences VMware fournies par IBM pour les produits suivants :
  * VMware vSphere Enterprise Plus 6.5u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.3
  * (Pour les clusters vSAN) VMware vSAN Advanced ou Enterprise 6.6

### Récapitulatif de la commande

Selon la configuration que vous avez sélectionnée pour le cluster, le coût estimé est généré et affiché instantanément dans la section **Récapitulatif de la commande** sur le panneau de droite. 

## Procédure d'ajout de clusters à des instances VMware Federal

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à laquelle vous souhaitez ajouter des clusters.

   **Remarque** : assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas ajouter de clusters à l'instance.

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche et cliquez sur **Ajouter** dans l'angle supérieur droit du tableau **CLUSTERS**. 
4. Sur la page **Ajouter un cluster**, entrez le nom du cluster. 
5. Renseignez les zones **Modèle UC**, **Mémoire RAM** et **Nombre de serveurs bare metal** pour la configuration de serveur bare metal.
6. Procédez à la configuration du stockage.
  * Si vous sélectionnez **Stockage vSAN**, renseignez les zones **Type et taille de disque pour disques de capacité vSAN** et **Nombre de disques de capacité vSAN**, ainsi que Edition de licence VMware vSAN.
  * Si vous sélectionnez **Stockage NFS**, renseignez les zones **Nombre de partages**, **Taille** et **Performances**.
  * Pour ajouter et configurer individuellement des partages de fichiers, sélectionnez l'onglet **Stockage NFS personnalisé**, puis cliquez sur l'icône **+** située en regard de l'intitulé **Ajouter NFS** et renseignez les zones **Taille** et **Performances** pour chaque partage de fichiers. Vous devez sélectionner au moins un partage de fichiers. 
7. Sélectionnez l'édition de licence pour VMware vSAN pour la configuration de licence.
8. Sur la page **Récapitulatif de la commande**, vérifiez la configuration du cluster avant d'ajouter celui-ci. 
   1. Passez en revue les paramètres du cluster. 
   2. Passez en revue le coût estimé du cluster. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
   3. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant d'ajouter le cluster. 
   4. Cliquez sur **Mettre à disposition**.

## Résultats après l'ajout de clusters à des instances VMware Federal

1. Le déploiement du cluster démarre automatiquement et celui-ci prend le statut **Initialisation en cours**. Vous pouvez vérifier le statut du déploiement en affichant l'historique de déploiement sur la page récapitulative de l'instance. 
2. Lorsque le cluster est prêt pour utilisation, il prend le statut **Prêt à l'emploi**. Le cluster qui vient d'être ajouté est activé avec vSphere haute disponibilité et vSphere Distributed Resource Scheduler (DRS).

**Important** : vous ne pouvez pas modifier le nom du cluster. La modification du nom du cluster peut entraîner l'échec d'opérations d'ajout ou de suppression de serveurs ESXi dans le cluster.

## Affichage des clusters dans les instances VMware Federal

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous voulez afficher les clusters.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, consultez le récapitulatif concernant les clusters :
   * **Nom** : nom du cluster.
   * **Serveur ESXi** : nombre de serveurs ESXi dans le cluster.
   * **UC** : spécification d'UC des serveurs ESXi du cluster.
   * **Disques vSAN personnalisés** : nombre de disques vSAN dans le cluster, ainsi que le type et la capacité des disques.
   * **Mémoire** : taille de mémoire totale des serveurs ESXi du cluster.
   * **Emplacement de centre de données** : centre de données où est hébergé le cluster.
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
4. Cliquez sur un nom de cluster pour afficher les détails relatifs aux serveurs ESXi, au stockage et aux licences. 

### Serveurs ESXi

   * **Nom** : nom du serveur ESXi au format `<host_prefix><n>.<subdomain_label>.<root_domain>`, où :

      `host_prefix` est le préfixe de nom d'hôte,
      `n` est la séquence du serveur ESXi,
      `subdomain_label` est le libellé de sous-domaine et
      `root_domain` est le nom de domaine racine.

   * **Version** : version du serveur ESXi.
   * **Données d'identification** : nom d'utilisateur et mot de passe d'accès au serveur ESXi.
   * **Adresse IP privée** : adresse IP privée du serveur ESXi.
   * **Status** :  statut du serveur ESXi, qui peut avoir l'une des valeurs suivantes :
        <dl class="dl">
        <dt class="dt dlterm">Ajouté</dt>
        <dd class="dd">Le serveur ESXi a été ajouté et est prêt pour utilisation. </dd>
        <dt class="dt dlterm">Ajout en cours</dt>
        <dd class="dd">L'ajout du serveur ESXi est en cours. </dd>
        <dt class="dt dlterm">Suppression en cours</dt>
        <dd class="dd">La suppression du serveur ESXi est en cours.</dd>
        </dl>

### Stockage

   * **Nom** : nom du magasin de données.
   * **Taille** : capacité du stockage.
   * **IOPS/Go** : niveau de performance du stockage.
   * **NFS/Portail** : version NFS du stockage.
   * **Statut** : statut du stockage, qui peut prendre l'une des valeurs suivantes :
        <dl class="dl">
        <dt class="dt dlterm">Ajouté</dt>
        <dd class="dd">Le serveur ESXi a été ajouté et est prêt pour utilisation. </dd>
        <dt class="dt dlterm">Ajout en cours</dt>
        <dd class="dd">L'ajout du serveur ESXi est en cours. </dd>
        <dt class="dt dlterm">Suppression en cours</dt>
        <dd class="dd">La suppression du serveur ESXi est en cours.</dd>
        </dl>

### Licences

   * **Licence** : type de licence.
   * **Type de commande** : la licence a été fournie par IBM ou par l'utilisateur.
   * **Edition de licence** : version et édition de la licence.
   * **Clé de licence** : clé de la licence.
   * **Capacité totale (UC)** : quantité totale de capacité d'UC pour la licence.
   * **Capacité disponible (UC)** : quantité de capacité d'UC disponible pour la licence.

## Suppression de clusters des instances VMware Federal

Vous pouvez être amené à vouloir supprimer un cluster d'une instance si vous n'en avez plus besoin.

**Remarque** : utilisez cette procédure pour retirer des clusters des instances qui sont déployées dans (ou mis à niveau vers) la version 2.3 et des éditions ultérieures.

### Avant de supprimer

* Cette procédure permet de supprimer des clusters des instances qui sont déployées dans la version 2.3 ou des éditions ultérieures.
* Pour les clusters déployés dans des instances V2.2 ou antérieures, vous devez mettre à niveau l'instance vers la version 2.3 pour pouvoir supprimer les clusters que vous lui avez ajoutés.
* Vous ne pouvez supprimer qu'un seul cluster à la fois. Pour supprimer plusieurs clusters, vous devez attendre que le cluster précédent soit supprimé avant de tenter de supprimer le cluster suivant.
* Assurez-vous que tous les noeuds présents dans un cluster sont sous tension et opérationnels avant de supprimer le cluster.
* Lorsque vous supprimez un cluster, toutes les machines virtuelles présentes sur le cluster sont également supprimées et ne peuvent pas être récupérées. Si vous souhaitez conserver les machines virtuelles, faites-les migrer vers d'autres clusters.
* Le cluster par défaut ne peut pas être supprimé.

## Procédure de suppression de clusters des instances VMware Federal

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez supprimer les clusters.

   **Remarque** : assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas supprimer de clusters de l'instance.

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, localisez le cluster que vous souhaitez supprimer et cliquez sur l'icône **Supprimer** dans la colonne **Actions**. 

## Liens connexes

* [Affichage des instances VMware Federal](vc_fed_viewinginstance.html)
* [Extension et réduction de capacité pour des instances VMware Federal](vc_fed_addingremovingservers.html)

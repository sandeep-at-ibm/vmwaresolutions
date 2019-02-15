---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ajout, affichage et suppression de clusters pour des instances vCenter Server

Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés sous **cluster1**.

Vous pouvez ajouter vos propres clusters à vos instances VMware vCenter Server afin d'étendre la capacité de calcul et de stockage. Au sein d'un cluster, vous pouvez gérer des serveurs ESXi afin d'optimiser l'allocation des ressources et la haute disponibilité. Lorsque vous n'en avez plus besoin, supprimez les clusters que vous avez ajoutés à vos instances.

La fonction de suppression de cluster est disponible uniquement pour les instances qui ont été déployées dans (ou mises à niveau vers) la version 2.3 et les versions ultérieures.
{:note}

## Ajout de clusters à des instances vCenter Server

Le nombre de clusters pouvant être ajoutés à une instance varie en fonction de la version de l'instance :
* Pour les instances déployées dans (ou mises à niveau vers) la version 2.5 et des versions ultérieures, le nombre de clusters, d'hôtes et de machines virtuelles détermine la limite maximum relative au nombre de clusters que vous pouvez ajouter. Vous devez respecter les règles et limites de dimensionnement VMware pour votre déploiement.
* Pour les instances déployées dans (ou mises à niveau vers) la version 2.0 et des versions ultérieures, vous pouvez ajouter jusqu'à 10 clusters.
* Pour les instances déployées dans la version 2.1 ou dans des versions antérieures, vous pouvez ajouter jusqu'à cinq clusters.

Pour plus d'informations sur les limites maximum, voir [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.

### Paramètres système

Lorsque vous ajoutez un cluster pour une instance vCenter Server, vous devez spécifier les paramètres suivants :

#### Nom de cluster

Le nom du cluster qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom de cluster doit commencer et se terminer par un caractère alphanumérique.
* Le nombre maximal de caractères autorisés est 30.
* Le nom de cluster doit être unique au sein de l'instance vCenter Server.

#### Emplacement de centre de données

L'emplacement de l'{{site.data.keyword.CloudDataCent}} du cluster est, par défaut, l'{{site.data.keyword.CloudDataCent_notm}} de l'instance vCenter Server. Vous pouvez déployer le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui de l'instance déployée, sous réserve que la latence du réseau entre les deux {{site.data.keyword.CloudDataCents_notm}} soit inférieure à 150 ms. Pour vérifier la latence du réseau, utilisez un outil tel que [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/).

Si vous déployez le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} ou pod d'infrastructure {{site.data.keyword.cloud_notm}}, trois VLAN supplémentaires sont commandés pour être utilisés avec les serveurs {{site.data.keyword.baremetal_short}} commandés.

### Paramètres de serveur bare metal

Vous pouvez choisir l'option **Skylake**, **Certifiés SAP** ou **Broadwell**.

#### Skylake

Avec l'option **Skylake**, un certain nombre d'options est disponible pour les paramètres **Modèle UC** et **Mémoire RAM**. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

Tableau 1. Options pour les serveurs Skylake {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

#### Certifiés SAP

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

Avec l'option **Broadwell**, un certain nombre d'options est disponible pour les paramètres **Modèle UC** et **Mémoire RAM**. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

Tableau 2. Options pour les serveurs Broadwell {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Quad Intel Xeon E7-4820 v4/40 coeurs au total, 1,9 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
| Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,2 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |

#### Nombre de serveurs bare metal

Les clusters requièrent au moins deux serveurs {{site.data.keyword.baremetal_short}}.

Pour les instances vCenter Server déployées dans la version 2.1 ou des versions antérieures, vous pouvez ajouter jusqu'à 59 serveurs {{site.data.keyword.baremetal_short}} pour un cluster. Vous pouvez ajouter de 1 à 59 serveurs ESXi à la fois.

Pour les instances vCenter Server déployées dans la version 2.0 ou des versions antérieures, vous pouvez ajouter jusqu'à 32 serveurs {{site.data.keyword.baremetal_short}} pour un cluster. Vous pouvez ajouter 1 à 20 serveurs ESXi à la fois pour la configuration de serveur bare metal **Skylake**, **Certifiés SAP** ou **Broadwell**.

Après le déploiement, vous pouvez créer jusqu'à quatre clusters supplémentaires. Si vous sélectionnez la configuration de serveur bare metal **Skylake** ou**Broadwell** avec un stockage VMware vSAN, quatre serveurs sont nécessaires pour le cluster initial et pour les clusters post-déploiement.

### Paramètres de stockage

Les paramètres de stockage varient en fonction de la configuration de serveur bare metal et du type de stockage que vous sélectionnez.

#### Stockage vSAN

Spécifiez les options vSAN suivantes :
* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Pour ajouter des disques de capacité au-delà de la limite fixée à huit, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de dix disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée.

  L'option **Hautes performances Intel Optane** est disponible uniquement pour les modèles d'UC Skylake Dual Intel Xeon Gold 5120 et Dual Intel Xeon Gold 6140.
  {:note}

* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.
* **Licence vSAN** : utilisez la licence VMware fournie par IBM pour le composant vSAN en sélectionnant **Inclure avec achat** ou fournissez votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant votre propre clé de licence

Si votre cluster initial était de type vSAN, tous les clusters vSAN supplémentaires utilisent la même licence vSAN et ont la même configuration que le cluster vSAN initial. C'est également le cas si vSAN est sélectionné pour être déployé dans un cluster de l'instance (initial ou supplémentaire). La première fois, un message vous demande la licence vSAN (licence achetée ou la vôtre) et l'édition. Ensuite, la prochaine fois que vous sélectionnerez vSAN pour un nouveau cluster, la licence que vous avez choisie initialement sera réutilisée.

#### Stockage NFS

Lorsque vous sélectionnez **Stockage NFS**, vous pouvez ajouter un stockage partagé de niveau fichier pour votre instance dans lequel tous les partages utilisent les mêmes paramètres ou vous pouvez spécifier des paramètres de configuration différents pour chaque partage de fichiers. Spécifiez les options NFS suivantes :

Le nombre de partages de fichiers doit être compris entre 1 et 32.
{:note}

* **Configurer les partages individuellement** : permet de spécifier des paramètres de configuration différents pour chaque partage de fichiers.
* **Nombre de partages** : lorsque vous souhaitez utiliser le même paramètre de configuration pour chaque partage de fichiers, spécifiez le nombre de partages de fichiers pour le stockage partagé NFS que vous souhaitez ajouter.
* **Taille** : sélectionnez la capacité qui répond à vos besoins de stockage partagé.
* **Performances** : sélectionnez la valeur IOPS (opérations d'entrée/sortie par seconde) par Go adaptée à vos besoins en matière de charge de travail.
* **Ajouter NFS** : permet d'ajouter des partages de fichiers individuels avec des paramètres de configuration différents.

Tableau 3. Options de niveau de performance NFS

| Option        | Détails       |
  |:------------- |:------------- |
  | 0,25 IOPS/Go | Cette option est conçue pour les charges de travail qui ne sont pas souvent utilisées. Exemples d'applications : données de coffre, hébergement de bases de données de grande taille avec des données existantes ou images de disque virtuel de système de mémoire virtuelle en tant que sauvegarde. |
  | 2 IOPS/Go | Cette option est adaptée à la plupart des charges de travail d'usage général. Entre autres exemples d'application, citons l'hébergement de petites bases de données, la sauvegarde d'applications Web ou les images de disque de machine virtuelle pour un hyperviseur. |
  | 4 IOPS/Go | Cette option est adaptée aux charges de travail de grande intensité qui ont un pourcentage élevé de données actives simultanément. Les bases de données transactionnelles en sont un exemple. |
  | 10 IOPS/Go | Cette option est adaptée aux types de charge de travail les plus exigeants, tels que les analyses. Les bases de données à transactions élevées et autres bases de données sensibles aux performances en sont des exemples. Ce niveau de performance est limité à une capacité maximale de 4 To par partage de fichiers. |

### Disques locaux

L'option Disques locaux est disponible uniquement pour la configuration de processeur Quad Intel Xeon E7-8890 v4 Bare Metal **certifié SAP**. Indiquez les options suivantes :
* **Nombre de disques **: sélectionnez le nombre de disques que vous voulez ajouter.
* **Type de disque **: sélectionnez une option pour le type de disque dont vous avez besoin.

### Paramètres d'octroi de licence

Spécifiez l'option d'octroi de licence pour le composant VMware vSphere dans le cluster :
* Si vous êtes un partenaire commercial, la licence vCenter (édition Enterprise Plus) est incluse et achetée en votre nom.
* Si vous n'êtes pas un partenaire commercial, vous pouvez utiliser les licences VMware fournies par IBM pour ce composant en sélectionnant **Inclure avec achat** ou vous pouvez fournir votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant votre propre clé de licence.

### Paramètres d'interface réseau

Les paramètres d'activation de carte d'interface réseau varient selon que vous sélectionnez **Réseau public et réseau privé** ou **Réseau privé uniquement**. Les services complémentaires suivants requièrent des cartes d'interface réseau public et ne sont pas disponibles si vous sélectionnez l'option de réseau privé :

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Récapitulatif de la commande

Selon la configuration que vous avez sélectionnée pour le cluster, le coût estimé est généré et affiché instantanément dans la section **Récapitulatif de la commande** sur le panneau de droite.

## Procédure d'ajout de clusters à des instances vCenter Server

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
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

### Résultats après l'ajout de clusters à des instances vCenter Server

1. Le déploiement du cluster démarre automatiquement et celui-ci prend le statut **Initialisation en cours**. Vous pouvez vérifier le statut du déploiement en affichant l'historique de déploiement sur la page **Récapitulatif** de l'instance.
2. Lorsque le cluster est prêt pour utilisation, il prend le statut **Prêt à l'emploi**. Le cluster qui vient d'être ajouté est activé avec vSphere haute disponibilité et vSphere Distributed Resource Scheduler (DRS).

Vous ne pouvez pas modifier le nom du cluster. La modification du nom du cluster peut entraîner l'échec d'opérations d'ajout ou de suppression de serveurs ESXi dans le cluster.
{:important}

## Procédure d'affichage des clusters dans les instances vCenter Server

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous voulez afficher les clusters.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, consultez le récapitulatif concernant les clusters :
  * **Nom** : nom du cluster.
  * **Serveurs ESXi** : nombre de serveurs ESXi dans le cluster.
  * **UC** : spécification d'UC des serveurs ESXi du cluster.
  * **Disques vSAN personnalisés** : nombre de disques vSAN dans le cluster, ainsi que le type et la capacité des disques.
  * **Mémoire** : taille de mémoire totale des serveurs ESXi du cluster.
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
4. Cliquez sur un nom de cluster pour afficher les détails relatifs aux serveurs ESXi et au stockage :

  * Détails relatifs aux serveurs ESXi :
     * **Nom** : nom du serveur ESXi au format `<host_prefix><n>.<subdomain_label>.<root_domain>`, où :

       `host_prefix` est le préfixe du nom d'hôte,

       `n` est la séquence du serveur,

       `subdomain_label` est le libellé de sous-domaine, et

       `root_domain` est le nom de domaine racine.

     * **Version** : version du serveur ESXi.
     * **Données d'identification** : nom d'utilisateur et mot de passe d'accès au serveur ESXi.
     * **Adresse IP privée** : adresse IP privée du serveur ESXi.
     * **Statut** : statut du serveur ESXi, qui peut avoir l'une des valeurs suivantes :
        <dl class="dl">
        <dt class="dt dlterm">Ajouté</dt>
        <dd class="dd">Le serveur ESXi a été ajouté et est prêt pour utilisation. </dd>
        <dt class="dt dlterm">Ajout en cours</dt>
        <dd class="dd">L'ajout du serveur ESXi est en cours. </dd>
        <dt class="dt dlterm">Suppression en cours</dt>
        <dd class="dd">La suppression du serveur ESXi est en cours.</dd>
        </dl>
  * Détails relatifs au stockage :
    * **Nom** : nom du magasin de données.
    * **Taille** : capacité du stockage.
    * **IOPS/Go** : niveau de performance du stockage.
    * **Protocole NFS** : version NFS du stockage.

## Suppression de clusters des instances vCenter Server

Vous souhaiterez peut-être supprimer un cluster d'une instance si vous n'en avez plus besoin.

### Avant de supprimer

* Utilisez cette procédure pour supprimer des clusters des instances qui sont déployées dans la version 2.3 ou dans des versions ultérieures.
* Pour les clusters déployés dans des instances V2.2 ou antérieures, vous devez mettre à niveau l'instance vers la version 2.3 si vous souhaitez supprimer les clusters que vous lui avez ajoutés.
* Vous ne pouvez supprimer qu'un seul cluster à la fois. Pour supprimer plusieurs clusters, vous devez le faire de manière séquentielle. Attendez que le cluster précédent soit supprimé avant de supprimer le cluster suivant.
* Assurez-vous que tous les noeuds présents dans un cluster sont sous tension et opérationnels avant de supprimer le cluster.
* Lorsque vous supprimez un cluster, toutes les machines virtuelles présentes sur le cluster sont également supprimées et ne peuvent pas être récupérées. Si vous souhaitez conserver les machines virtuelles, faites-les migrer vers d'autres clusters.
* Le cluster par défaut ne peut pas être supprimé.

### Procédure de suppression de clusters des instances vCenter Server

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez supprimer les clusters.

   Assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas supprimer de clusters de l'instance.
   {:note}

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, localisez le cluster que vous souhaitez supprimer et cliquez sur l'icône **Supprimer** dans la colonne **Actions**.
4. Confirmez que vous avez terminé la migration de machines virtuelles vers d'autres clusters, le cas échéant, et que vous souhaitez supprimer le cluster.

### Liens connexes

* [Affichage des instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_viewinginstances.html)
* [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html)

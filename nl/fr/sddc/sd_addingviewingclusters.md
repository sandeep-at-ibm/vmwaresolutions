---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-28"

---

# Ajout, affichage et suppression de clusters pour des instances Cloud Foundation

Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont regroupés dans un cluster par défaut. Le nom du cluster par défaut est le suivant :
* Pour les instances déployées dans la version 2.1 ou des éditions ultérieures : **MGMT-Cluster-`<subdomain_label>`**
* Pour les instances déployées dans la 2.0 ou des éditions antérieures : **SDDC-Cluster**

Vous pouvez ajouter vos propres clusters à vos instances VMware Cloud Foundation afin d'étendre la capacité de calcul et de stockage. Au sein d'un cluster, vous pouvez gérer des serveurs ESXi afin d'optimiser l'allocation des ressources et la haute disponibilité. Lorsque vous n'en avez plus besoin, vous pouvez supprimer les clusters que vous avez ajoutés à vos instances.

**Disponibilité :**
* La fonction d'ajout de cluster est disponible uniquement pour les instances qui ont été déployées dans (ou mises à niveau vers) la version 2.0 et des éditions ultérieures.
* La fonction de suppression de cluster est disponible uniquement pour les instances qui ont été déployées dans (ou mises à niveau vers) la version 2.3 et des éditions ultérieures.  

## Ajout de clusters à des instances Cloud Foundation

Vous pouvez ajouter jusqu'à cinq clusters à une instance Cloud Foundation.

### Paramètres système

Lorsque vous ajoutez un cluster à une instance Cloud Foundation, vous devez spécifier les paramètres énumérés ci-après.

#### Nom de cluster

Le nom du cluster qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom de cluster doit commencer et se terminer par un caractère alphanumérique.
* Le nom de cluster ne doit pas dépasser 30 caractères.
* Le nom de cluster doit être unique au sein de l'instance Cloud Foundation.

#### Emplacement de centre de données

L'{{site.data.keyword.CloudDataCent}} du cluster est, par défaut, l'{{site.data.keyword.CloudDataCent_notm}} de l'instance Cloud Foundation. Vous pouvez déployer le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui de l'instance déployée, sous réserve que la latence du réseau entre les deux {{site.data.keyword.CloudDataCents_notm}} soit inférieure à 150 ms. Pour vérifier la latence du réseau, utilisez un outil tel que [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Les centres de données dont vous disposez dépendent de la configuration de serveur bare metal qui est sélectionnée pour le déploiement. Si vous sélectionnez la configuration **Personnalisée**, vous pouvez également déployer le cluster dans un autre pod de l'infrastructure {{site.data.keyword.cloud_notm}} si le centre de données sélectionné contient des pods supplémentaires. Cette configuration se révèle utile lorsque le pod de l'infrastructure {{site.data.keyword.cloud_notm}} par défaut où est déployée l'instance initiale a atteint sa capacité maximale.

**Remarque** : les configurations de serveur bare metal **Petite** et **Grande** normalisées utilisent un pod par défaut non modifiable.

Si vous déployez le cluster dans un autre centre de données ou pod, au moins trois VLAN supplémentaires sont commandés pour une utilisation avec les serveurs {{site.data.keyword.baremetal_short}} commandés.

### Paramètres de serveur bare metal

Vous pouvez choisir l'option **Personnalisée** ou **Préconfigurée**.

#### Personnalisée

Avec l'option **Personnalisée**, un certain nombre d'options est disponible pour les paramètres **Modèle UC** et **Mémoire RAM**. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

Tableau 1. Options pour les serveurs {{site.data.keyword.baremetal_short}} personnalisés

| Options de modèle d'UC   | Options de RAM   |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |

#### Préconfigurée

Pour l'option **Préconfigurée**, vous pouvez choisir une **configuration de serveur bare metal** adaptée à vos besoins :
* Petite (Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz/128 Go de RAM/12 disques)
* Grande (Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz/512 Go de RAM/12 disques)

### Paramètres de stockage vSAN

Pour les configurations de serveur bare metal **préconfigurées**, vous ne pouvez pas modifier les paramètres de stockage vSAN :
* Pour la configuration de serveur bare metal **Petite**, deux unités de disque SED SSD de 1,9 To sont commandées.
* Pour la configuration de serveur bare metal **Grande**, quatre unités de disque SED SSD de 3,8 To sont commandées.

Pour la configuration de serveur bare metal **Personnalisée** vous pouvez personnaliser le stockage vSAN en spécifiant les paramètres suivants :

* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Pour ajouter des disques de capacité au-delà de la limite fixée à huit, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de dix disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée. L'option **Hautes performances avec Intel Optane** est disponible pour les processeurs Dual Intel Xeon Gold 5120 et 6140.
* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.

### Paramètres d'octroi de licence

Vous pouvez spécifier les options d'octroi de licence pour les composants VMware du cluster, y compris VMware vSphere et VMware vSAN :
* Si vous êtes un partenaire commercial IBM, la licence vSphere (Enterprise Plus edition) et la licence vSAN sont incluses et achetées en votre nom. Vous devez néanmoins spécifier l'édition pour la licence vSAN.
* Si vous n'êtes pas un partenaire commercial IBM, vous pouvez utiliser les licences VMware fournies par IBM pour les composants en sélectionnant **Inclure avec achat** ou vous pouvez fournir votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant vos propres clés de licence.

## Procédure d'ajout de clusters à des instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance à laquelle vous souhaitez ajouter des clusters.

   **Remarque** : assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas ajouter de clusters à l'instance.

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche et cliquez sur **Ajouter** en haut à droite du tableau **CLUSTERS**.
4. Sur la page **Ajouter un cluster**, entrez le nom du cluster.
5. Si vous souhaitez héberger le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui dans lequel l'instance est hébergée, sous **Serveur bare metal**, cochez la case **Sélectionner un autre emplacement** et choisissez l'{{site.data.keyword.CloudDataCent_notm}} dans lequel héberger l'instance.
6. Procédez à la configuration du serveur bare metal :
   * Si vous avez sélectionné **Personnalisée**, renseignez les zones **Modèle UC** et **Mémoire RAM**.
   * Si vous avez sélectionné **Préconfigurée**, renseignez la zone **Configuration de serveur bare metal**.
7. Procédez à la configuration du stockage :
   * Si vous avez sélectionné l'option **Préconfigurée** pour la configuration de serveur bare metal, les paramètres de stockage des configurations de serveur bare metal normalisées **Petite** et **Grande** ne sont pas modifiables.
   * Si vous avez sélectionné le type **Personnalisée** pour la configuration de serveur bare metal, spécifiez les types de disque pour les disques de cache et de capacité VSAN, ainsi que le nombre de disques. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
8. Spécifiez de quelle manière les clés de licence sont fournies :
   * Si vous êtes un partenaire commercial IBM, la licence vSphere (Enterprise Plus edition) et la licence vSAN sont incluses et achetées en votre nom. Vous devez néanmoins spécifier l'édition pour la licence vSAN.
   * Si vous n'êtes pas un partenaire commercial IBM, vous pouvez sélectionnez l'une des options suivantes :
       * Si vous voulez que de nouvelles licences soient achetées en votre nom, sélectionnez **Inclure avec l'achat** pour les composants. Pour VMware vSAN, sélectionnez également l'édition de licence.
       * Si vous voulez utiliser votre propre licence VMware pour un composant, sélectionnez **Je fournirai** et entrez la clé de licence pour le composant.
9. Sur la page **Récapitulatif de la commande**, vérifiez la configuration du cluster avant d'ajouter celui-ci.
   1. Passez en revue les paramètres du cluster.
   2. Passez en revue le coût estimé du cluster. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
   3. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant d'ajouter le cluster.
   4. Cliquez sur **Mettre à disposition**.

### Résultats après l'ajout de clusters à des instances Cloud Foundation

1. Le déploiement du cluster démarre automatiquement et le cluster prend le statut **Initialisation en cours**. Vous pouvez vérifier le statut du déploiement en affichant l'historique de déploiement sur la page récapitulative de l'instance.
2. Lorsque le cluster est prêt pour utilisation, il prend le statut **Prêt à l'emploi**. Le cluster qui vient d'être ajouté est activé avec vSphere à haute disponibilité et vSphere Distributed Resource Scheduler (DRS).

**Important :** vous ne pouvez pas modifier le nom du cluster. La modification du nom du cluster peut entraîner l'échec d'opérations d'ajout ou de suppression de serveurs ESXi dans le cluster.

## Procédure d'affichage des clusters dans les instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur une instance dont vous voulez afficher les clusters.
3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, consultez le récapitulatif concernant les clusters :
   * **Nom** : nom du cluster.
   * **Serveurs ESXi** : nombre de serveurs ESXi dans le cluster.
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
4. Cliquez sur un nom de cluster pour afficher la liste des serveurs ESXi et les informations les concernant :

   * **Nom** : nom du serveur ESXi au format `<host_prefix><n>.<subdomain_label>.<root_domain>`, où :

      `host_prefix` est le préfixe de nom d'hôte,
      `n` est la séquence du serveur ESXi,
      `subdomain_label` est le libellé de sous-domaine et
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
   * Le détails de la licence vSAN et de la licence vSphere. Les détails de licence vSphere sont disponibles uniquement lorsque vous avez choisi d'utiliser votre propre licence VMware (mode BYOL) lorsque vous avez commandé le cluster :
       * **Type de licence** : licence vSAN ou licence vSphere.
       * **Type de commande** : la licence est fournie par l'utilisateur (mode BYOL) ou achetée au nom de l'utilisateur.
       * **Edition de licence** : édition de la licence.
       * **Clé de licence** : clé de licence.
       * **Capacité totale (UC)** : capacité totale ou nombre d'UC fournies par la licence.
       * **Capacité disponible (UC)** : capacité actuellement disponible pour la licence.

## Suppression de clusters des instances Cloud Foundation

Vous pouvez être amené à vouloir supprimer un cluster d'une instance si vous n'en avez plus besoin.

### Avant de supprimer

* Cette procédure permet de supprimer des clusters des instances qui sont déployées dans la version 2.3 ou des éditions ultérieures.
* Pour les clusters déployés dans des instances V2.2 ou antérieures, vous devez mettre à niveau l'instance vers la version 2.3 pour pouvoir supprimer les clusters que vous lui avez ajoutés.
* Vous ne pouvez supprimer qu'un seul cluster à la fois. Pour supprimer plusieurs clusters, vous devez attendre que le cluster précédent soit supprimé avant de tenter de supprimer le cluster suivant.
* Assurez-vous que tous les noeuds présents dans un cluster sont sous tension et opérationnels avant de supprimer le cluster.
* Lorsque vous supprimez un cluster, toutes les machines virtuelles présentes sur le cluster sont également supprimées et ne peuvent pas être récupérées. Si vous souhaitez conserver les machines virtuelles, faites-les migrer vers d'autres clusters.
* Le cluster par défaut ne peut pas être supprimé.

## Procédure de suppression de clusters des instances Cloud Foundation

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances Cloud Foundation**, cliquez sur l'instance dont vous souhaitez supprimer des clusters.

   **Remarque** : assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas supprimer de clusters de l'instance.

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, localisez le cluster que vous souhaitez supprimer et cliquez sur l'icône **Supprimer**.
4. Confirmez que vous avez terminé la migration de machines virtuelles vers d'autres clusters, le cas échéant, et que vous souhaitez supprimer le cluster.

### Liens connexes

* [Affichage d'instances Cloud Foundation](sd_viewinginstances.html)
* [Extension et réduction de capacité pour des instances Cloud Foundation](sd_addingremovingservers.html)

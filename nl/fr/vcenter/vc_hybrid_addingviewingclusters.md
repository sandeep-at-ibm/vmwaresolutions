---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ajout, affichage et suppression de clusters pour des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters}

Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés sous **cluster1**.

Vous pouvez ajouter des clusters à votre instance VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle afin d'étendre la capacité de calcul et de stockage. Au sein d'un cluster, gérez les serveurs ESXi afin d'optimiser l'allocation des ressources et la haute disponibilité. Lorsque vous n'en avez plus besoin, supprimez les clusters que vous avez ajoutés à votre instance.

## Ajout de clusters à des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding}

Le nombre de clusters pouvant être ajoutés à une instance varie en fonction de la version de l'instance :
* Pour les instances déployées dans (ou mises à niveau vers) la version 2.5 et des versions ultérieures, le nombre de clusters, d'hôtes et de machines virtuelles détermine la limite maximum relative au nombre de clusters que vous pouvez ajouter. Vous devez respecter les règles et limites de dimensionnement VMware pour votre déploiement.
* Pour les instances déployées dans (ou mises à niveau vers) la version 2.3 et des versions ultérieures, vous pouvez ajouter jusqu'à 10 clusters.

Pour plus d'informations sur les limites maximum, voir [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}.

### Paramètres système
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

Lorsque vous ajoutez un cluster pour une instance vCenter Server with Hybridity Bundle, vous devez spécifier les paramètres suivants :

#### Nom de cluster
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

Le nom du cluster qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom de cluster doit commencer et se terminer par un caractère alphanumérique.
* Le nom de cluster ne doit pas dépasser 30 caractères.
* Le nom de cluster doit être unique au sein de l'instance vCenter Server with Hybridity Bundle.

#### Emplacement de centre de données
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

L'emplacement de l'{{site.data.keyword.CloudDataCent_notm}} du cluster est, par défaut, l'{{site.data.keyword.CloudDataCent_notm}} de l'instance vCenter Server. Vous pouvez déployer le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui de l'instance déployée, sous réserve que la latence du réseau entre les deux {{site.data.keyword.CloudDataCents_notm}} soit inférieure à 150 ms. Pour vérifier la latence du réseau, utilisez un outil tel que [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window}.

Si vous déployez le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} ou pod d'infrastructure {{site.data.keyword.cloud_notm}}, trois VLAN supplémentaires sont commandés pour être utilisés avec les serveurs {{site.data.keyword.baremetal_short}} commandés.

### Paramètres de serveur bare metal
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

Indiquez le modèle d'UC et la mémoire RAM du serveur bare metal. Les options disponibles peuvent varier en fonction de la version dans laquelle votre instance a été initialement déployée.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

Lorsque vous sélectionnez **Skylake**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM adaptée à vos besoins.

Tableau 1. Options pour les serveurs Skylake bare metal

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

Lorsque vous sélectionnez **Broadwell**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM adaptée à vos besoins.

Tableau 2. Options pour les serveurs Broadwell bare metal

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Quad Intel Xeon E7-4820 v4/40 coeurs au total, 1,9 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
| Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,2 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |

#### Nombre de serveurs bare metal
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

Au moins deux serveurs {{site.data.keyword.baremetal_short}} sont requis pour un cluster.

Vous pouvez ajouter jusqu'à 59 serveurs {{site.data.keyword.baremetal_short}} pour un cluster et entre 1 et 59 serveurs ESXi à la fois.

Après le déploiement, vous pouvez créer jusqu'à quatre clusters supplémentaires. Pour le stockage VMware vSAN, quatre serveurs sont requis pour le cluster initial et pour les clusters post-déploiement.

### Paramètres de stockage vSAN
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

VMware vSAN 6.6 est inclus avec votre commande d'instance vCenter Server with Hybridity Bundle. Spécifiez les options vSAN suivantes :
* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Pour ajouter des disques de capacité au-delà de la limite fixée à huit, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de dix disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée.

  L'option **Hautes performances Intel Optane** est disponible uniquement pour les modèles d'UC Skylake Dual Intel Xeon Gold 5120 et Dual Intel Xeon Gold 6140.
  {:note}

* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.
* **Licence vSAN** : sélectionnez l'édition de licence VMware vSAN 6.6 (Advanced ou Enterprise).

### Paramètres d'octroi de licence
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

Licences fournies par IBM pour les composants VMware suivants :
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4 (édition Advanced ou Enterprise)

### Paramètres d'interface réseau
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

Les paramètres de carte d'interface réseau varient selon que vous sélectionnez **Réseau public et réseau privé** ou **Réseau privé uniquement**. Les services complémentaires suivants requièrent des cartes d'interface réseau public et ne sont pas disponibles avec l'option de réseau privé :

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}
* Zerto on {{site.data.keyword.cloud_notm}}

### Récapitulatif de la commande
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

Selon la configuration que vous avez sélectionnée pour le cluster, le coût estimé est généré et affiché instantanément dans la section **Récapitulatif de la commande** sur le panneau de droite.

## Procédure d'ajout de clusters à des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous voulez afficher les clusters.

   Assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Si tel n'est pas le cas, vous ne pourrez pas ajouter de clusters à l'instance.
   {:note}

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche et cliquez sur **Ajouter** dans l'angle supérieur droit du tableau **CLUSTERS**.
4. Sur la page **Ajouter un cluster**, entrez le nom du cluster.
5. Vous pouvez héberger le cluster dans un autre {{site.data.keyword.CloudDataCent_notm}} que celui dans lequel l'instance est hébergée. Pour ce faire, sous **Serveur bare metal**, cochez la case **Sélectionner un autre emplacement** et choisissez l'{{site.data.keyword.CloudDataCent_notm}} dans lequel héberger l'instance.
6. Renseignez les zones **Modèle UC**, **Mémoire RAM** et **Nombre de serveurs bare metal** pour la configuration de serveur bare metal.
7.  Sélectionnez **Stockage vSAN** et spécifiez les types de disque pour les disques de cache et de capacité, ainsi que le nombre de disques. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
8. Sélectionnez l'édition de licence pour VMware vSAN pour la configuration de licence.
9. Sélectionnez le paramètre réseau **Réseau public et réseau privé** ou **réseau privé uniquement**.
10. Sur la page **Récapitulatif de la commande**, vérifiez la configuration du cluster avant d'ajouter celui-ci.
   1. Passez en revue les paramètres du cluster.
   2. Passez en revue le coût estimé du cluster. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
   3. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant d'ajouter le cluster.
   4. Cliquez sur **Mettre à disposition**.

### Résultats après l'ajout de clusters à des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-adding-results}

1. Le déploiement du cluster démarre automatiquement et celui-ci prend le statut **Initialisation en cours**. Vous pouvez vérifier le statut du déploiement en affichant l'historique de déploiement sur la page **Récapitulatif** de l'instance.
2. Lorsque le cluster est prêt pour utilisation, il prend le statut **Prêt à l'emploi**. Le cluster qui vient d'être ajouté est activé avec vSphere haute disponibilité et vSphere Distributed Resource Scheduler (DRS).

Vous ne pouvez pas modifier le nom du cluster. La modification du nom du cluster peut entraîner l'échec d'opérations d'ajout ou de suppression de serveurs ESXi dans le cluster.
{:important}

## Procédure d'affichage des clusters dans les instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

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

## Suppression de clusters des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-deleting}

Vous souhaiterez peut-être supprimer un cluster d'une instance si vous n'en avez plus besoin.

### Avant de supprimer
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* Vous ne pouvez supprimer qu'un seul cluster à la fois. Pour supprimer plusieurs clusters, vous devez le faire de manière séquentielle et attendre que le cluster précédent soit supprimé avant de supprimer le cluster suivant.
* Assurez-vous que tous les noeuds présents dans un cluster sont sous tension et opérationnels avant de supprimer le cluster.
* Lorsque vous supprimez un cluster, toutes les machines virtuelles présentes sur le cluster sont également supprimées et ne peuvent pas être récupérées. Si vous souhaitez conserver les machines virtuelles, faites-les migrer vers d'autres clusters.
* Le cluster par défaut ne peut pas être supprimé.

## Procédure de suppression de clusters des instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance dont vous souhaitez supprimer les clusters.

   Assurez-vous que le statut de l'instance est **Prêt à l'emploi**. Sinon, vous ne pouvez pas retirer de clusters de l'instance.
   {:note}

3. Cliquez sur **Infrastructure** dans le panneau de navigation de gauche. Dans le tableau **CLUSTERS**, localisez le cluster que vous souhaitez supprimer et cliquez sur l'icône **Supprimer** dans la colonne **Actions**.

## Liens connexes
{: #vc_hybrid_addingviewingclusters-related}

* [Affichage des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)

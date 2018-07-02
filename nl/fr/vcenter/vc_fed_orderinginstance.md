---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# Commande d'instances VMware Federal

Afin de déployer une plateforme virtuelle VMware personnalisable et flexible totalement adaptée à vos besoins en charge de travail, commandez une instance VMware Federal qui vous permet de déconnecter la connexion de gestion ouverte et de sécuriser votre instance déployée. 

**Remarque :** actuellement, seules les instances vCenter Server prennent en charge VMware Federal on {{site.data.keyword.cloud}}.

## Conditions requises

Assurez-vous que :
* Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](../vmonic/useraccount.html).
* Vous avez passé en revue les informations décrites dans la rubrique [Exigences et planification pour les instances VMware Federal](vc_fed_planning.html).
* Vous avez passé en revue le format des noms d'instance et de domaine. Le nom de domaine et le libellé de sous-domaine sont utilisés pour générer le nom d'utilisateur et les noms de serveur de l'instance.

Tableau 1. Format de la valeur des noms d'instance et de domaine

| Nom        | Format de la valeur      |
  |:------------- |:------------- |
  | Nom de domaine | `<root_domain>` |  
  | Nom d'utilisateur de connexion vCenter Server | `<user_id>@<root_domain>` (utilisateur Microsoft Active Directory) ou `administrator@vsphere.local` |
  | Nom de domaine complet vCenter Server | `vcenter.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |
  | Nom du site de connexion unique | `<subdomain_label>` |
  | Nom de serveur ESXi qualifié complet | `<host_prefix><n>.<subdomain_label>.<root_domain>`, où `<n>` est la séquence du serveur ESXi. La longueur maximale admise est de 50 caractères. |  
  | Nom de domaine complet PSC | `psc-<subdomain_label>.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |

**Important** : ne modifiez aucune des valeurs définies lors de la commande et du déploiement de l'instance. Toute modification risquerait de rendre votre instance inutilisable. Par exemple, le réseau public pourrait s'arrêter, les serveurs et les instances de serveur virtuel pourraient passer derrière une passerelle Vyatta durant la mise à disposition ou l'instance de serveur virtuel IBM CloudBuilder pourrait s'arrêter ou être supprimée.

## Paramètres système

Vous devez spécifier les paramètres système répertoriés ci-après lorsque vous commandez une instance VMware Federal.

### Nom d'instance

Le nom de l'instance qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom d'instance doit commencer et se terminer par un caractère alphanumérique.
* Le nom d'instance ne doit pas dépasser 10 caractères.
* Le nom d'instance doit être unique au sein de votre compte.

### Principale ou secondaire

Commandez une nouvelle instance principale. Le déploiement d'une instance secondaire pour la haute disponibilité n'est pas pris en charge actuellement.

## Paramètres d'octroi de licence

Licences VMware fournies par IBM pour les produits suivants :

* VMware vCenter Server 6.5
* VMware vSphere Enterprise Plus 6.5u1
* VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.3
* (Pour les clusters vSAN) VMware vSAN Advanced ou Enterprise 6.6

**Attention :**

* Les éditions de licence minimum sont indiquées sur l'interface utilisateur. Si différentes éditions de composant sont prises en charge, vous pouvez sélectionner celle qui vous convient. Il est de votre responsabilité de vous assurer que la clé de licence fournie est correcte pour chaque composant VMware sélectionné.
* Pour vSphere, des frais de licence seront imputés au moment de la commande, mais ces frais seront ultérieurement crédités à votre compte.

## Paramètres de serveur bare metal

Les paramètres de serveur bare metal sont basés sur votre configuration personnalisée. L'option de sélection d'une configuration préconfigurée n'est pas prise en charge actuellement.

### Emplacement de centre de données

Sélectionnez l'IBM Cloud Data Center où l'instance doit être hébergée. 

### Personnalisée

Indiquez le modèle d'UC et la mémoire RAM du serveur bare metal.

Tableau 2. Options pour les serveurs {{site.data.keyword.baremetal_short}} personnalisés

| Options d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 64 Go, 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

### Nombre de serveurs bare metal

Vous pouvez configurer de 2 à 20 serveurs ESXi.

Tous les serveurs ESXi se partagent la même configuration. Après le déploiement, vous pouvez ajouter quatre clusters supplémentaires. Pour les paramètres de stockage vSAN, 4 serveurs ESXi sont nécessaires pour le cluster initial et pour les clusters d'après déploiement. Pour plus d'informations sur le nombre minimum de serveurs ESXi, voir [Une instance vCenter Server à deux noeuds est-elle à haute disponibilité ?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)

## Paramètres de stockage

Les paramètres de stockage varient selon que vous sélectionnez l'option vSAN, NFS ou Stockage NFS personnalisé.

### Stockage vSAN

Pour vSAN, spécifiez les options de stockage suivantes :

* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez la capacité qui répond à vos besoins de stockage partagé.
* **Nombre de disques de capacité vSAN** : sélectionnez le nombre de disques que vous voulez ajouter pour le stockage partagé vSAN. Le nombre de disques doit être de 2, 4, 6 ou 8.
* Sélectionnez l'édition de licence VMware vSAN 6.6 (Advanced ou Enterprise).

### Stockage NFS

Lorsque vous sélectionnez **Stockage NFS**, vous pouvez ajouter un stockage partagé de niveau fichier pour votre instance dans lequel tous les partages utilisent les mêmes paramètres ou vous pouvez spécifier des paramètres de configuration différents pour chaque partage de fichiers. Spécifiez les options NFS suivantes :

**Remarque :** le nombre de partages de fichiers doit être compris entre 1 et 32. 

* **Configurer les partages individuellement** : permet de spécifier des paramètres de configuration différents pour chaque partage de fichiers. 
* **Nombre de partages** : lorsque vous utilisez le même paramètre de configuration pour chaque partage de fichiers, spécifiez le nombre de partages de fichiers pour le stockage partagé NFS que vous souhaitez ajouter. 
* **Taille** : permet de sélectionner la capacité qui répond à vos besoins en matière de stockage partagé.
* **Performances** : permet de sélectionner la valeur IOPS (Input/output Operations Per Second) par Go adaptée à vos besoins en matière de charge de travail. 
* **Ajouter NFS** : permet d'ajouter des partages de fichiers individuels qui utilisent des paramètres de configuration différents. 

Tableau 3. Options de niveau de performance NFS

| Option        | Détails       |
  |:------------- |:------------- |
  | 2 IOPS/Go | Cette option est adaptée à la plupart des charges de travail d'usage général. Entre autres exemples d'application, citons l'hébergement de petites bases de données, la sauvegarde d'applications Web ou les images de disque de machine virtuelle pour un hyperviseur. |
  | 4 IOPS/Go | Cette option est adaptée aux charges de travail de grande intensité qui ont un pourcentage élevé de données actives simultanément. Les bases de données transactionnelles en sont un exemple. |
  | 10 IOPS/Go | Cette option est adaptée aux types de charge de travail les plus exigeants, tels que les analyses. Les bases de données à transactions élevées et autres bases de données sensibles aux performances en sont des exemples. Ce niveau de performance est limité à une capacité maximale de 4 To par partage de fichiers. |

## Paramètres d'interface réseau

### Préfixe de nom d'hôte

Le préfixe du nom d'hôte qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le préfixe de nom d'hôte doit commencer et se terminer par un caractère alphanumérique.
*  Le préfixe de nom d'hôte ne doit pas dépasser 10 caractères.

### Libellé de sous-domaine

Le libellé du sous-domaine qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le libellé de sous-domaine doit commencer et se terminer par un caractère alphanumérique.
*  Le libellé de sous-domaine ne doit pas dépasser 10 caractères.
*  Le libellé de sous-domaine doit être unique au sein de votre compte.

### Nom de domaine

Le nom du domaine racine qui doit respecter les règles suivantes :
* Le nom de domaine doit être composé d'au moins deux chaînes séparées par un point (.)
* La première chaîne doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Toutes les chaînes, à l'exception de la dernière, ne peuvent contenir que des caractères alphanumériques et des tirets (-).
* La dernière chaîne ne peut contenir que des caractères alphabétiques.
* La dernière chaîne doit comporter entre 2 et 24 caractères.

**Remarque :** la longueur maximale du nom de domaine complet des hôtes et des machines virtuelles est de 50 caractères. Les noms de domaine doivent respecter cette longueur maximale.

### Configuration DNS

Sélectionnez la configuration de système de noms de domaine (DNS, Domain Name System) de votre instance :

* **Une instance de serveur virtuel Windows publique pour Active Directory/DNS** : une unique instance de serveur virtuel Windows Microsoft pour Microsoft Active Directory (AD), qui fonctionne en tant que serveur de noms de domaine pour l'instance où sont enregistrés les hôtes et les machines virtuelles, est déployée et peut être interrogée.
* **Deux machines virtuelles Windows Server dédiées à haute disponibilité sur le cluster de gestion** : à compter de l'édition V2.3, deux machines virtuelles Microsoft Windows virtual sont déployées, pour plus de sécurité et de robustesse. 

**Important :** vous devez fournir deux licences Microsoft Windows Server 2012 R2 si vous configurez votre instance de manière à utiliser deux machines virtuelles Microsoft Windows. Utilisez la licence d'édition Microsoft Windows Server 2012 R2 Standard et/ou la licence d'édition Microsoft Windows Server 2012 R2 Datacenter.

Actuellement, chaque licence ne peut être affectée qu'à un seul serveur physique et couvre jusqu'à deux processeurs physiques. Une licence d'édition Standard est à même d'exécuter deux machines virtuelles Microsoft Windows virtualisées par serveur à 2 processeurs. Par conséquent, deux licences sont nécessaires puisque deux machines virtuelles Microsoft Windows sont déployées sur deux hôtes différents.

Vous disposez de 30 jours pour activer les machines virtuelles.

Pour plus d'informations sur la commande de licence Windows, voir la [documentation Windows Server 2012 R2](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2).

## Récapitulatif de la commande

Selon la configuration que vous avez sélectionnée pour l'instance, le coût estimé est généré et affiché instantanément dans la section **Récapitulatif de la commande** sur le panneau de droite. Cliquez sur **Détails concernant la tarification** en bas à droite du panneau pour générer un document PDF contenant les détails relatifs à l'estimation.

## Procédure

1. Dans le catalogue IBM Cloud, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **vCenter Server** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vCenter Server on IBM Cloud**, cliquez sur la carte **vCenter Server**, puis sur **Créer**.
3. Sur la page **vCenter Server**, entrez le nom de l'instance.
4. Cliquez sur **Instance principale** pour déployer une seule instance dans l'environnement.
5. Spécifiez l'édition de licence VMware NSX.
6. Procédez à la configuration du serveur bare metal :
  1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger l'instance.
  2. Sélectionnez le modèle d'UC **Personnalisé** et la quantité de mémoire **RAM**.
7. Procédez à la configuration du stockage.
      * Si vous avez sélectionné **Stockage vSAN**, renseignez les zones **Type et taille de disque pour disques de capacité vSAN** et **Nombre de disques de capacité vSAN**, ainsi que Edition de licence VMware vSAN.
      * Si vous avez sélectionné **Stockage NFS**, renseignez les zones **Nombre de partages**, **Taille** et **Performances**.
      * Pour ajouter et configurer individuellement des partages de fichiers, sélectionnez l'onglet **Stockage NFS personnalisé**, puis cliquez sur l'icône **+** située en regard de l'intitulé **Ajouter NFS** et renseignez les zones **Taille** et **Performances** pour chaque partage de fichiers. Vous devez sélectionner au moins un partage de fichiers. 
8. Procédez à la configuration de l'interface réseau.
   1. Renseignez les zones Préfixe de nom d'hôte, Libelle de sous-domaine et Nom de domaine racine.
   2. Sélectionnez la configuration DNS.
9. Sur la page **Récapitulatif de la commande**, vérifiez la configuration de l'instance avant de passer la commande.
   1. Passez en revue les paramètres de l'instance.
   2. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant de commander l'instance.
   3. Passez en revue le coût estimé de l'instance en cliquant sur le lien correspondant au prix sous **Calculer le coût**. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
   4. Cliquez sur **Mettre à disposition**.

## Résultats

Le déploiement de l'instance commence automatiquement. Vous recevez une confirmation que la commande est en cours de traitement et vous pouvez vérifier l'état du déploiement en affichant les détails de l'instance.

Une fois l'instance correctement déployée, les composants décrits dans la rubrique [Composants de l'instance VMware Federal](../vcenter/vc_fed_overview.html#vcenter-server-instance-components-for-vmware-federal-on-ibm-cloud) sont installés sur votre plateforme virtuelle VMware. Les serveurs ESXi que vous avez commandés sont, par défaut, regroupés en **cluster1**.

Lorsque l'instance est prête pour utilisation, elle prend le statut **Prêt à l'emploi** et vous recevez une notification par courrier électronique.

<!--When you order a secondary instance, the VMware vSphere Web Client for the primary instance (linked to the secondary one) might be restarted after your secondary instance order is completed.-->

## Etape suivante

Affichez, gérez ou sécurisez l'instance VMware Federal que vous avez commandée.

**Important** : vous devez gérer les composants {{site.data.keyword.vmwaresolutions_full}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou autre élément extérieur à la console.
Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.

**ATTENTION :** gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lorsque vous avez commandé l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque de rendre votre environnement instable. Ces activités de gestion incluent :
*  L'ajout, la modification, le retour ou la suppression de composants
*  Le développement ou la réduction de la capacité de l'instance via le retrait de serveurs ESXi
*  La mise hors tension de composants

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

## Liens connexes

* [Inscription à un compte {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Affichage des instances VMware Federal](vc_fed_viewinginstance.html)
* [Extension et réduction de capacité pour des instances VMware Federal](vc_fed_addingremovingservers.html)
* [Ajout, affichage et suppression de clusters pour des instances VMware Federal](fed_addviewdeleteclusters.html)
* [Sécurisation des instances VMware Federal](vc_fed_securinginstance.html)
* [Suppression d'instances VMware Federal](vc_fed_deletinginstance.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)

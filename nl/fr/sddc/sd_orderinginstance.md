---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Commande d'instances Cloud Foundation

Pour déployer une plateforme de centre de données définie par logiciels (SDDC, Software-Defined Data Center) unifiée avec une configuration de calcul, de stockage et de réseau standard, commandez une instance VMware Cloud Foundation. Lors de la commande initiale, vous pouvez également ajouter des services, tels que [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html) pour la reprise après incident.

## Conditions requises

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](../vmonic/useraccount.html).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les instances Cloud Foundation](sd_planning.html).

**Important :** ne modifiez aucune des valeurs définies lors de la commande et du déploiement de l'instance. Toute modification risquerait de rendre votre instance inutilisable. De plus, ne modifiez pas le nom d'instance, le nom de domaine racine, le libellé de sous-domaine ou le préfixe de nom d'hôte une fois l'instance déployée.

## Paramètres système

Vous devez spécifier les paramètres système répertoriés ci-après lorsque vous commandez une instance Cloud Foundation.

### Nom d'instance

Le nom de l'instance qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom d'instance doit commencer et se terminer par un caractère alphanumérique.
* Le nom d'instance ne doit pas dépasser 10 caractères.
* Le nom d'instance doit être unique au sein de votre compte.

### Principale ou secondaire

Indiquez si vous souhaitez commander une nouvelle instance principale ou une instance secondaire pour une instance principale existante.

## Paramètres d'octroi de licence

Spécifiez les options d'octroi de licence pour les composants VMware suivants dans l'instance :  
* Licence vCenter Server - Standard
* Licence vSphere - Enterprise Plus
* Licence NSX - Enterprise
* Licence vSAN : sélectionnez l'édition Advanced ou Enterprise

Si vous êtes un partenaire commercial, la licence vCenter Server (édition Standard), la licence vSphere (édition Enterprise Plus), la licence NSX et la licence vSAN sont incluses et achetées en votre nom. Vous devez néanmoins spécifier l'édition pour la licence vSAN.

Si vous n'êtes pas un partenaire commercial, vous pouvez utiliser les licences VMware fournies par IBM pour ces composants en sélectionnant **Inclure avec achat** ou vous pouvez fournir votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant vos propres clés de licence.

## Paramètres de serveur bare metal

### Emplacement de centre de données

Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} où l'instance doit être hébergée.

### Préconfigurée

Lorsque vous sélectionnez **Préconfigurée**, vous ne pouvez pas modifier les paramètres d'UC ou de mémoire RAM.

En fonction de vos besoins, sélectionnez une configuration de serveur bare metal :
  * Petite (Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz/128 Go de RAM/12 unités)
  * Grande (Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz/512 Go de RAM/12 unités)

### Personnalisée

Lorsque vous sélectionnez **Personnalisée**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM adaptée à vos besoins.

Sélectionnez le modèle d'UC et la mémoire RAM du serveur bare metal.

Tableau 1. Options pour les serveurs {{site.data.keyword.baremetal_short}} personnalisés

| Options d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |

### Nombre de serveurs bare metal

Une instance Cloud Foundation comprend quatre serveurs bare metal lors du déploiement initial. Vous ne pouvez pas modifier le nombre de serveurs bare metal lorsque vous passez la commande.

## Paramètres de stockage

Les instances Cloud Foundation ne prennent en charge que le stockage vSAN.
* Lorsque vous sélectionnez la configuration de serveur bare metal **Préconfigurée**, les paramètres de stockage sont normalisés et ne peuvent pas être modifiés :
  * Pour la configuration de serveur bare metal **Petite**, deux unités de disque SED SSD de 1,9 To sont commandées.
  * Pour la configuration de serveur bare metal **Grande**, quatre unités de disque SED SSD de 3,8 To sont commandées.
* Lorsque vous sélectionnez la configuration de serveur bare metal **Personnalisée** vous pouvez personnaliser le stockage VMware vSAN pour votre instance en spécifiant les paramètres suivants sous **Stockage vSAN** :
  * **Type et taille de disque pour disques de capacité vSAN** : sélectionnez la capacité qui répond à vos besoins de stockage partagé.
  * **Nombre de disques de capacité vSAN** : indiquez le nombre de disques que vous voulez ajouter pour le stockage partagé vSAN. Le nombre de disques doit être de 2, 4, 6 ou 8.

## Paramètres d'interface réseau

Vous devez spécifier les paramètres d'interface réseau répertoriés ci-après lorsque vous commandez une instance Cloud Foundation.

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

### Format de valeur pour les paramètres réseau

Le nom de domaine et le libellé de sous-domaine sont utilisés pour générer le nom d'utilisateur et les noms de serveur de l'instance, comme illustré dans le tableau ci-après.

Tableau 2. Format de valeur pour les noms d'utilisateur, les noms de domaine et les noms de serveur

| Nom        | Format de la valeur      |
  |:------------- |:------------- |
  | Nom de domaine | `<root_domain>` |  
  | Nom de serveur ESXi qualifié complet | `<host_prefix><n>.<subdomain_label>.<root_domain>`, où `<n>` est la séquence du serveur ESXi. La longueur maximale admise est de 50 caractères. |   
  | Nom d'utilisateur de connexion vCenter Server | `<user_id>@<root_domain>` (utilisateur Microsoft Active Directory) ou `administrator@vsphere.local` |
  | Nom de domaine complet vCenter Server | `vcenter-1.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |  
  | Nom de domaine complet du gestionnaire SDDC | `sddcmanager.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |
  | Nom du site de connexion unique | `<subdomain_label>`
  | Nom de domaine complet PSC | `PSC-<subdomain_label>.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |  

  Le nom de domaine complet du gestionnaire SDDC doit être impossible à résoudre publiquement. Sinon, la configuration d'instance Cloud Foundation risque d'échouer et n'est pas récupérable. Avant de spécifier le nom de domaine, passez en revue la rubrique [Remarques relatives au choix d'un nom de domaine racine](../vmonic/trbl_limitations.html#considerations-when-choosing-a-root-domain-name-for-cloud-foundation-instances).

### Réseaux locaux virtuels

Les paramètres de réseau varient selon que vous sélectionnez **Commander de nouveaux VLAN** ou **Sélectionner des VLAN existants**.

Un VLAN public et deux VLAN privés sont nécessaires pour votre commande d'instance. Les deux VLAN privés sont liés respectivement à chaque serveur bare metal.

**Commander de nouveaux VLAN**  
Sélectionnez cette option pour commander un nouveau VLAN public et deux nouveaux VLAN privés.

**Sélectionner des VLAN existants**  
En fonction de l'{{site.data.keyword.CloudDataCent_notm}} que vous avez sélectionné, des VLAN publics et privés existants peuvent être disponibles.

Lorsque vous sélectionnez cette option pour réutiliser des VLAN publics et privés existants, spécifiez les VLAN et les sous-réseaux :
  * **VLAN public**, pour l'accès au réseau public.
  * **VLAN privé**, pour la connectivité entre les centres de données et les services dans {{site.data.keyword.cloud_notm}}.
  * **VLAN privé secondaire**, pour les dispositifs VMware, tels que vSAN.
  * **Sous-réseau principal**, affecté aux hôtes physiques pour l'accès au réseau public.
  * **Sous-réseau principal privé**, affecté aux hôtes physiques pour le trafic de gestion.

**Important :**
* Vérifiez que la configuration de pare-feu sur les VLAN sélectionnés ne bloque pas le trafic des données de gestion.
* Vérifiez que tous les VLAN sélectionnés se trouvent dans le même pod, car les serveurs ESXi ne peuvent pas être mis à disposition sur des VLAN multi-pods.

## Services

Lorsque vous commandez une instance Cloud Foundation, vous pouvez également commander des services supplémentaires. Pour plus d'informations sur les services disponibles, voir [Services pour les instances Cloud Foundation](sd_planning.html#services-for-cloud-foundation-instances).

## Récapitulatif de la commande

Selon la configuration que vous avez sélectionnée pour l'instance et les services complémentaires, le coût estimé est généré et affiché instantanément dans le panneau de droite. Cliquez sur **Détails concernant la tarification** en bas à droite du panneau pour générer un document PDF contenant les détails relatifs à l'estimation.

## Procédure

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **Cloud Foundation** dans la section **Centres de données virtuels**.
2. Sur la page **VMware Cloud Foundation on IBM Cloud**, cliquez sur **Créer**.
3. Sur la page **Cloud Foundation**, entrez le nom de l'instance.
4. Sélectionnez le type d'instance :
   * Cliquez sur **Instance principale** pour déployer une seule instance dans l'environnement ou pour déployer la première instance dans une topologie multisite.
   * Cliquez sur **Instance secondaire** pour connecter l'instance à une instance (principale) existante dans l'environnement à des fins de haute disponibilité et procédez comme suit :
     1. Sélectionnez l'instance principale à laquelle vous voulez que l'instance secondaire soit connectée.
     2. Entrez le mot de passe de l'administrateur PSC pour l'instance principale.
5. Spécifiez les paramètres de licence pour les composants d'instance:
   *  Pour utiliser des licences fournies par IBM, sélectionnez **Inclure avec achat**.
   *  Pour utiliser votre propre licence, sélectionnez **Je fournirai** et entrez la clé de licence.  
6. Spécifiez les paramètres de serveur bare metal :
   1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger l'instance.
   2. Sélectionnez la configuration de serveur bare metal.
      * Lorsque vous sélectionnez **Préconfigurée**, choisissez une configuration **Petite**, Moyenne ou **Grande**.
      * Lorsque vous sélectionnez **Personnalisée**, spécifiez le modèle d'UC et la taille de mémoire RAM.
7. Spécifiez les paramètres de stockage :
   * Si vous avez sélectionné le type **Préconfigurée** pour la configuration de serveur bare metal, sachez que les paramètres de stockage des configurations de serveur bare metal normalisées de type **Petite** et **Grande** ne sont pas modifiables.
   * Si vous avez sélectionné le type **Personnalisée** pour la configuration de serveur bare metal, renseignez les zones **Type et taille de disque pour disques de capacité vSAN** et **Nombre de disques de capacité vSAN**.
8. Spécifiez les paramètres d'interface réseau :
   1. Renseignez les zones Préfixe de nom d'hôte, Libelle de sous-domaine et Nom de domaine racine. Pour une instance secondaire, le nom de domaine est automatiquement renseigné.
   2. Sélectionnez les paramètres VLAN :
      * Si vous voulez commander de nouveaux VLAN publics et privés, cliquez sur **Commander de nouveaux VLAN**.
      * Si vous voulez réutiliser les VLAN publics et privés existants lorsqu'ils sont disponibles, cliquez sur **Sélectionner des VLAN existants** et spécifiez les VLAN et les sous-réseaux.

9. Sélectionnez les services complémentaires à déployer dans l'instance en cliquant sur la carte de service correspondante. Si un service nécessite de la configuration, spécifiez les paramètres qui lui sont propres et cliquez sur **Ajouter un service** dans la fenêtre de configuration contextuelle. Pour savoir comment indiquer les paramètres d'un service, voir la rubrique de commande de service correspondante.

10. Sur la page **Récapitulatif de la commande**, vérifiez la configuration de l'instance avant de passer la commande.
    1. Passez en revue les paramètres de l'instance.
    2. Passez en revue le coût estimé de l'instance. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
    3. Assurez-vous que le compte qui sera facturé est correct et cochez la case **Je comprends que le compte répertorié ci-dessous sera facturé**.
    4. Cliquez sur le ou les liens des conditions applicables à votre commande. Prenez soin d'accepter ces conditions, puis cochez la case **J'ai lu et j'accepte les accords de services tiers ci-dessous**.
    5. Cliquez sur **Mettre à disposition**.

## Résultats

Le déploiement de l'instance commence automatiquement. Vous recevez une confirmation que la commande est en cours de traitement et vous pouvez vérifier l'état du déploiement en affichant les détails de l'instance.

Une fois l'instance correctement déployée, les composants décrits dans [Spécifications techniques relatives aux instances Cloud Foundation](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances) sont installés sur votre plateforme virtuelle VMware. Les serveurs ESXi que vous avez commandés sont, par défaut, regroupés en **SDDC-Cluster**. Si vous avez commandé des services supplémentaires, le déploiement des services commence une fois votre commande honorée.

Lorsque l'instance est prête pour utilisation, elle prend le statut **Prêt à l'emploi** et vous recevez une notification par courrier électronique.

Lorsque vous commandez une instance secondaire, le client Web VMware vSphere de l'instance principale (liée à l'instance secondaire) devra peut-être être redémarré une fois la commande d'instance secondaire honorée.

## Etape suivante

Affichez et gérez l'instance Cloud Foundation que vous avez commandée.

**Important** : vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou autre élément extérieur à la console. Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.

**ATTENTION** : gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lorsque vous avez commandé l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque de rendre votre environnement instable. Ces activités de gestion incluent :

*  L'ajout, la modification, le retour ou la suppression de composants
*  L'extension ou la réduction de la capacité de l'instance via l'ajout ou la suppression de serveurs ESXi
*  La mise hors tension de composants
*  Le redémarrage de services

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

### Liens connexes

* [Inscription à un compte {{site.data.keyword.cloud_notm}}](../vmonic/signing_softlayer_account.html)
* [Affichage d'instances Cloud Foundation](sd_viewinginstances.html)
* [Ajout, affichage et suppression de clusters pour des instances Cloud Foundation](sd_addingviewingclusters.html)
* [Extension et réduction de capacité pour des instances Cloud Foundation](sd_addingremovingservers.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](sd_addingremovingservices.html)
* [Suppression d'instances Cloud Foundation](sd_deletinginstance.html)
* [Foire aux questions sur le mode BYOL](../vmonic/faq_byol.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande d'instances Cloud Foundation
{: #sd_orderinginstance}

Pour déployer une plateforme de centre de données définie par logiciels (SDDC, Software-Defined Data Center) unifiée avec une configuration de calcul, de stockage et de réseau standard, commandez une instance VMware Cloud Foundation. Lors de la commande initiale, vous pouvez également ajouter des services, tels que [Zerto on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) pour la reprise après incident.

## Conditions requises
{: #sd_orderinginstance-req}

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_planning).

Ne modifiez aucune des valeurs définies lors de la commande ou du déploiement de l'instance. Cela rendrait votre instance inutilisable. Par exemple, si le réseau public s'arrête, si les serveurs et les instances de serveur virtuel passent derrière un mi-parcours Vyatta ou si l'instance de serveur virtuel IBM CloudBuilder s'arrête ou est supprimée. De plus, ne modifiez pas le nom d'instance, le nom de domaine racine, le libellé de sous-domaine ou le préfixe de nom d'hôte une fois l'instance déployée.
{:important}

## Paramètres système
{: #sd_orderinginstance-sys-settings}

Vous devez spécifier les paramètres système répertoriés ci-après lorsque vous commandez une instance Cloud Foundation.

### Nom d'instance
{: #sd_orderinginstance-inst-name}

Le nom de l'instance qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom d'instance doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Le nom d'instance ne doit pas dépasser 10 caractères.
* Le nom d'instance doit être unique au sein de votre compte.

### Principale ou secondaire
{: #sd_orderinginstance-primary-secondary}

Indiquez si vous souhaitez commander une nouvelle instance principale ou une instance secondaire pour une instance principale existante.

## Paramètres d'octroi de licence
{: #sd_orderinginstance-licensing-settings}

Spécifiez les options d'octroi de licence pour les composants VMware suivants dans l'instance :  
* Licence vCenter Server - Standard
* Licence vSphere - Enterprise Plus
* Licence NSX - Enterprise
* Licence vSAN : sélectionnez l'édition Advanced ou Enterprise

Si vous êtes un partenaire commercial, la licence vCenter Server (édition Standard), la licence vSphere (édition Enterprise Plus), la licence NSX et la licence vSAN sont incluses et achetées en votre nom. Vous devez néanmoins spécifier l'édition pour la licence vSAN.

Si vous n'êtes pas un partenaire commercial, vous pouvez utiliser les licences VMware fournies par IBM pour ces composants en sélectionnant **Inclure avec achat** ou vous pouvez fournir votre propre licence (mode BYOL) en sélectionnant **Je fournirai** et en entrant vos propres clés de licence.

## Paramètres de serveur bare metal
{: #sd_orderinginstance-bare-metal}

### Emplacement de centre de données
{: #sd_orderinginstance-dc-location}

Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} où l'instance doit être hébergée.

### Skylake
{: #sd_orderinginstance-skylake}

Lorsque vous sélectionnez **Skylake**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM de serveur bare metal adaptée à vos besoins.

Tableau 1. Options pour les serveurs Skylake {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC  | Options de RAM       |
|:------------- |:------------- |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 128 GB, 192 GB, 384 GB, 768 GB, 1.5 To |

### Broadwell
{: #sd_orderinginstance-broadwell}

Lorsque vous sélectionnez **Broadwell**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM de serveur bare metal adaptée à vos besoins.

Tableau 2. Options pour les serveurs Broadwell {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 128 Go, 256 Go, 512 Go, 768 Go, 1,5 To |
| Quad Intel Xeon E7-4820 v4/40 coeurs au total, 2,0 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
| Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,1 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |

### Nombre de serveurs bare metal
{: #sd_orderinginstance-bare-metal-number}

Une instance Cloud Foundation comprend quatre serveurs bare metal lors du déploiement initial. Vous ne pouvez pas modifier le nombre de serveurs bare metal lorsque vous passez la commande.

## Paramètres de stockage
{: #sd_orderinginstance-storage}

Pour les instances Cloud Foundation, vous pouvez commander un stockage VMware vSAN uniquement.

Lorsque vous sélectionnez la configuration de serveur bare metal **Skylake** ou **Broadwell**, vous pouvez personnaliser le stockage vSAN pour votre instance. Spécifiez les paramètres vSAN suivants :
* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Pour ajouter des disques de capacité au-delà de la limite fixée à huit, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de dix disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée.

  L'option **Hautes performances Intel Optane** est disponible uniquement pour les modèles d'UC Skylake Dual Intel Xeon Gold 5120 et Dual Intel Xeon Gold 6140.
  {:note}

* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.

## Paramètres d'interface réseau
{: #sd_orderinginstance-network-interface}

Vous devez spécifier les paramètres d'interface réseau répertoriés ci-après lorsque vous commandez une instance Cloud Foundation.

### Préfixe de nom d'hôte
{: #sd_orderinginstance-hostname-prefix}

Le préfixe du nom d'hôte qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le préfixe de nom d'hôte doit commencer et se terminer par un caractère alphanumérique.
*  Le préfixe de nom d'hôte ne doit pas dépasser 10 caractères.

### Libellé de sous-domaine
{: #sd_orderinginstance-subdomain-label}

Le libellé du sous-domaine qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le libellé de sous-domaine doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
*  Le libellé de sous-domaine ne doit pas dépasser 10 caractères.
*  Le libellé de sous-domaine doit être unique au sein de votre compte.

### Nom de domaine
{: #sd_orderinginstance-domain-name}

Le nom du domaine racine qui doit respecter les règles suivantes :
* Le nom de domaine doit être composé d'au moins deux chaînes séparées par un point (.)
* La première chaîne doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Toutes les chaînes, à l'exception de la dernière, ne peuvent contenir que des caractères alphanumériques et des tirets (-).
* La dernière chaîne ne peut contenir que des caractères alphabétiques.
* La dernière chaîne doit comporter entre 2 et 24 caractères.

La longueur maximale du nom de domaine complet des hôtes et des machines virtuelles est de 50 caractères. Les noms de domaine doivent respecter cette longueur maximale.
{:note}

### Format de valeur pour les paramètres réseau
{: #sd_orderinginstance-network-settings-value-format}

Le nom de domaine et le libellé de sous-domaine sont utilisés pour générer le nom d'utilisateur et les noms de serveur de l'instance, comme illustré dans le tableau ci-après.

Tableau 3. Format de valeur pour les noms d'utilisateur, les noms de domaine et les noms de serveur

| Nom        | Format de la valeur      |
  |:------------- |:------------- |
  | Nom de domaine | `<root_domain>` |  
  | Nom de serveur ESXi qualifié complet | `<host_prefix><n>.<subdomain_label>.<root_domain>`, où `<n>` est la séquence du serveur ESXi. La longueur maximale admise est de 50 caractères. |   
  | Nom d'utilisateur de connexion vCenter Server | `<user_id>@<root_domain>` (utilisateur Microsoft Active Directory) ou `administrator@vsphere.local` |
  | Nom de domaine complet vCenter Server | `vcenter-1.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |  
  | Nom de domaine complet du gestionnaire SDDC | `sddcmanager.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |
  | Nom du site de connexion unique | `<subdomain_label>`
  | PSC FQDN | `PSC-<subdomain_label>.<subdomain_label>.<root_domain>`. La longueur maximale admise est de 50 caractères. |  

  Le nom de domaine complet du gestionnaire SDDC doit être impossible à résoudre publiquement. Sinon, la configuration d'instance Cloud Foundation risque d'échouer et n'est pas récupérable. Avant de spécifier le nom de domaine, passez en revue la rubrique [Remarques relatives au choix d'un nom de domaine racine](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_limitations#considerations-when-choosing-a-root-domain-name-for-cloud-foundation-instances).

### Réseaux locaux virtuels
{: #sd_orderinginstance-vlans}

Les paramètres de réseau varient selon que vous sélectionnez **Commander de nouveaux VLAN** ou **Sélectionner des VLAN existants**.

Un VLAN public et deux VLAN privés sont nécessaires pour votre commande d'instance. Les deux VLAN privés sont liés respectivement à chaque serveur bare metal.

#### Commander de nouveaux VLAN
{: #sd_orderinginstance-new-vlans}

Sélectionnez cette option pour commander un nouveau VLAN public et deux nouveaux VLAN privés.

#### Sélectionner des VLAN existants
{: #sd_orderinginstance-existing-vlans}

En fonction de l'{{site.data.keyword.CloudDataCent_notm}} que vous avez sélectionné, des VLAN publics et privés existants peuvent être disponibles.

Lorsque vous sélectionnez cette option pour réutiliser des VLAN publics et privés existants, spécifiez les VLAN et les sous-réseaux :
  * **VLAN public**, pour l'accès au réseau public.
  * **VLAN privé**, pour la connectivité entre les centres de données et les services dans {{site.data.keyword.cloud_notm}}.
  * **VLAN privé secondaire**, pour les dispositifs VMware, tels que vSAN.
  * **Sous-réseau principal**, affecté aux hôtes physiques pour l'accès au réseau public.
  * **Sous-réseau principal privé**, affecté aux hôtes physiques pour le trafic de gestion.

Vérifiez que la configuration de pare-feu sur les VLAN sélectionnés ne bloque pas le trafic des données de gestion. Vérifiez que tous les VLAN sélectionnés se trouvent dans le même pod, car les serveurs ESXi ne peuvent pas être mis à disposition sur des VLAN multi-pods.
{:important}

## Services
{: #sd_orderinginstance-addon-services}

Lorsque vous commandez une instance Cloud Foundation, vous pouvez également commander des services complémentaires. Pour plus d'informations sur les services disponibles, voir [Services pour les instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_planning#services-for-cloud-foundation-instances).

## Récapitulatif de la commande
{: #sd_orderinginstance-order-summary}

Selon la configuration que vous avez sélectionnée pour l'instance et les services complémentaires, le coût estimé est généré et affiché instantanément dans le panneau de droite. Cliquez sur **Détails concernant la tarification** dans le panneau de droite pour générer un document PDF contenant les détails relatifs à l'estimation.

## Procédure à utiliser pour commander des instances Cloud Foundation
{: #sd_orderinginstance-procedure}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **Cloud Foundation** dans la section **Centres de données virtuels**.
2. Sur la page **VMware Cloud Foundation on IBM Cloud**, cliquez sur **Créer**.
3. Sur la page **Cloud Foundation**, entrez le nom de l'instance.
4. Sélectionnez le type d'instance :
   * Cliquez sur **Instance principale** pour déployer une seule instance dans l'environnement ou pour déployer la première instance dans une topologie multisite.
   * Cliquez sur **Instance secondaire** pour connecter l'instance à une instance (principale) existante dans l'environnement à des fins de haute disponibilité. Effectuez les opérations suivantes :
     1. Sélectionnez l'instance principale à laquelle vous voulez que l'instance secondaire soit connectée.
     2. Pour les instances principales V2.5 ou ultérieures, entrez une valeur dans la zone **Mot de passe de l'administrateur PSC pour l'instance principale**.
     3. Pour les instances principales V2.4 ou antérieures, assurez-vous que la valeur préremplie dans la zone **Mot de passe de l'administrateur PSC pour l'instance principale** est correcte.
5. Spécifiez les paramètres de licence pour les composants d'instance:
   *  Pour utiliser des licences fournies par IBM, sélectionnez **Inclure avec achat**.
   *  Pour utiliser votre propre licence, sélectionnez **Je fournirai** et entrez la clé de licence.  
6. Spécifiez les paramètres de serveur bare metal :
   1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger l'instance.
   2. Sélectionnez la configuration de serveur bare metal, puis spécifiez le modèle d'UC et la taille de mémoire RAM.
7. Procédez à la configuration du stockage.
   1. Spécifiez les types de disque pour les disques de cache et de capacité vSAN, ainsi que le nombre de disques.
   2. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
8. Spécifiez les paramètres d'interface réseau :
   1. Renseignez les zones Préfixe de nom d'hôte, Libelle de sous-domaine et Nom de domaine racine. Pour une instance secondaire, le nom de domaine est automatiquement renseigné.
   2. Sélectionnez les paramètres VLAN :
      * Si vous voulez commander de nouveaux VLAN publics et privés, cliquez sur **Commander de nouveaux VLAN**.
      * Si vous voulez réutiliser les VLAN publics et privés existants lorsqu'ils sont disponibles, cliquez sur **Sélectionner des VLAN existants** et spécifiez les VLAN et les sous-réseaux.

9. Sélectionnez les services complémentaires à déployer dans l'instance en cliquant sur la carte de service correspondante. Si un service nécessite de la configuration, spécifiez les paramètres qui lui sont propres et cliquez sur **Ajouter un service** dans la fenêtre de configuration contextuelle. Pour savoir comment indiquer les paramètres d'un service, voir la rubrique de commande de services correspondante.

10. Sur la page **Récapitulatif de la commande**, vérifiez la configuration de l'instance avant de passer la commande.
    1. Passez en revue les paramètres de l'instance.
    2. Passez en revue le coût estimé de l'instance. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
    3. Assurez-vous que le compte qui sera facturé est correct et cochez la case **Je comprends que le compte répertorié ci-dessous sera facturé**.
    4. Cliquez sur le ou les liens des conditions applicables à votre commande. Prenez soin d'accepter ces conditions, puis cochez la case **J'ai lu et j'accepte les accords de services tiers ci-dessous**.
    5. Cliquez sur **Mettre à disposition**.

## Résultats
{: #sd_orderinginstance-results}

Le déploiement de l'instance commence automatiquement. Vous recevez une confirmation que la commande est en cours de traitement et vous pouvez vérifier l'état du déploiement en affichant les détails de l'instance.

Une fois l'instance correctement déployée, les composants décrits dans [Spécifications techniques relatives aux instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances) sont installés sur votre plateforme virtuelle VMware. Les serveurs ESXi que vous avez commandés sont, par défaut, regroupés en **SDDC-Cluster**. Si vous avez commandé des services complémentaires, le déploiement des services commence une fois votre commande honorée.

Lorsque l'instance est prête pour utilisation, elle prend le statut **Prêt à l'emploi** et vous recevez une notification par courrier électronique.

Lorsque vous commandez une instance secondaire, le client Web VMware vSphere de l'instance principale (liée à l'instance secondaire) devra peut-être être redémarré une fois la commande d'instance secondaire honorée.

## Etape suivante
{: #sd_orderinginstance-next}

Affichez et gérez l'instance Cloud Foundation que vous avez commandée.

Vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou tout autre élément extérieur à la console. Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.
{:important}

**ATTENTION :** gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lorsque vous avez commandé l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque de rendre votre environnement instable. Ces activités de gestion incluent :

*  L'ajout, la modification, le retour ou la suppression de composants
*  L'extension ou la réduction de la capacité de l'instance via l'ajout ou la suppression de serveurs ESXi
*  La mise hors tension de composants
*  Le redémarrage de services

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

## Liens connexes
{: #sd_orderinginstance-related}

* [Inscription à un compte {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [Affichage d'instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Ajout, affichage et suppression de clusters pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-and-viewing-clusters-for-cloud-foundation-instances)
* [Extension et réduction de capacité pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
* [Suppression d'instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance)
* [Foire aux questions sur le mode BYOL](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_byol)

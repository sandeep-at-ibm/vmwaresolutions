---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-19"

keywords: vCenter Server Hybridity order instance, order vCenter Server Hybridity, order Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande d'instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance}

Afin de déployer une plateforme virtuelle VMware personnalisable et flexible totalement adaptée à vos besoins en charge de travail, commandez une instance VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. L'instance vCenter Server with Hybridity Bundle inclut la licence VMware Hybrid Cloud Extension (HCX) qui vous autorise à utiliser le service VMware HCX on {{site.data.keyword.cloud_notm}}. Vous pouvez également ajouter des services, tels que [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) pour la reprise après incident.

## Exigences relatives à la commande d'instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-req}

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Vous avez passé en revue les informations décrites dans la rubrique [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning).
* Vous avez passé en revue le format des noms d'instance et de domaine. Le nom de domaine et le libellé de sous-domaine sont utilisés pour générer le nom d'utilisateur et les noms de serveur de l'instance.

Tableau 1. Format de la valeur des noms d'instance et de domaine

| Nom        | Format de la valeur      |
  |:------------- |:------------- |
  | Nom de domaine | `<root_domain>` |  
  | Nom d'utilisateur de connexion vCenter Server | `<user_id>@<root_domain>` (utilisateur Microsoft Active Directory) ou `administrator@vsphere.local` |
  | vCenter Server (avec PSC intégré) FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. La longueur maximale est de 50 caractères. |
  | Nom du site de connexion unique | `<subdomain_label>` |
  | Nom de serveur ESXi qualifié complet | `<host_prefix><n>.<subdomain_label>.<root_domain>`, où `<n>` est la séquence du serveur ESXi. La longueur maximale admise est de 50 caractères. |

Ne modifiez aucune des valeurs définies lors de la commande ou du déploiement de l'instance. Cela rendrait votre instance inutilisable. Par exemple, si le réseau public s'arrête, si les serveurs et les instances de serveur virtuel passent derrière un mi-parcours Vyatta ou si l'instance de serveur virtuel IBM CloudBuilder s'arrête ou est supprimée.
{:important}

## Paramètres système
{: #vc_hybrid_orderinginstance-sys-settings}

Vous devez spécifier les paramètres système répertoriés ci-après lorsque vous commandez une instance vCenter Server with Hybridity Bundle.

### Nom d'instance
{: #vc_hybrid_orderinginstance-inst-name}

Le nom de l'instance qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le nom d'instance doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Le nom d'instance ne doit pas dépasser 10 caractères.
* Le nom d'instance doit être unique au sein de votre compte.

### Licences VMware vSphere
{: #vc_hybrid_orderinginstance-vsphere-license}

Indiquez si vous souhaitez commander vSphere Enterprise Plus 6.7u1 ou vSphere Enterprise Plus 6.5u2.

vSphere Enterprise Plus 6.7u1 est disponible uniquement pour les serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} Broadwell et Skylake.
{:note}

### Principale ou secondaire
{: #vc_hybrid_orderinginstance-primary-secondary}

Indiquez si vous souhaitez commander une nouvelle instance principale ou une instance secondaire pour une instance principale existante.

## Paramètres d'octroi de licence
{: #vc_hybrid_orderinginstance-licensing-settings}

Les licences VMware suivantes sont incluses avec votre commande d'instance vCenter Server with Hybridity Bundle. Vous devez spécifier l'édition pour les licences NSX et vSAN.

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 ou 6.7
* NSX Service Providers 6.4 (édition Advanced ou Enterprise)
* vSAN 6.6 (édition Advanced ou Enterprise)

### Attention
{: #vc_hybrid_orderinginstance-attention}

* Les instances vCenter Server with Hybridity Bundle ne prennent pas en charge le mode BYOL (Bring Your Own License).
* Les éditions de licence minimum sont indiquées sur l'interface utilisateur. Si différentes éditions de composant sont prises en charge, vous pouvez sélectionner celle qui vous convient.

## Paramètres de serveur bare metal
{: #vc_hybrid_orderinginstance-bare-metal-settings}

Les paramètres bare metal dépendent de l'{{site.data.keyword.CloudDataCent_notm}} que vous sélectionnez et de la configuration de serveur bare metal.

Quatre serveurs ESXi sont nécessaires pour le cluster initial et pour les clusters post-déploiement dans le cadre des configurations vSAN. Tous les serveurs ESXi se partagent la même configuration. Après le déploiement, vous pouvez ajouter quatre clusters supplémentaires.

### Emplacement de centre de données
{: #vc_hybrid_orderinginstance-dc-location}

Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} où l'instance doit être hébergée.

### Skylake
{: #vc_hybrid_orderinginstance-skylake}

Lorsque vous sélectionnez **Skylake**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM de serveur bare metal adaptée à vos besoins.

Tableau 2. Options pour les serveurs Skylake {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

### Broadwell
{: #vc_hybrid_orderinginstance-broadwell}

Lorsque vous sélectionnez **Broadwell**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM de serveur bare metal adaptée à vos besoins.

Tableau 3. Options pour les serveurs Broadwell {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/40 coeurs au total, 2,0 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
| Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,1 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |

### Nombre de serveurs bare metal
{: #vc_hybrid_orderinginstance-bare-metal-number}

* Tous les serveurs que vous commandez ont la même configuration.
* Vous pouvez commander entre 4 et 20 serveurs.

## Paramètres de stockage
{: #vc_hybrid_orderinginstance-storage-settings}

VMware vSAN 6.6 est inclus avec votre commande d'instance vCenter Server with Hybridity Bundle. Spécifiez les options vSAN suivantes :
* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Si vous souhaitez augmenter la capacité au-delà de la limite de 10 disques, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de 12 disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée.

  L'option **Hautes performances avec Intel Optane** n'est disponible que pour les modèles d'unités centrales Skylake.
  {:note}

* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.

## Paramètres d'interface réseau
{: #vc_hybrid_orderinginstance-network-interface-settings}

Vous devez spécifier les paramètres d'interface réseau répertoriés ci-après lorsque vous commandez une instance vCenter Server with Hybridity Bundle.

### Préfixe de nom d'hôte
{: #vc_hybrid_orderinginstance-host-name-prefix}

  Le préfixe du nom d'hôte qui doit respecter les règles suivantes :
  *  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
  *  Le préfixe de nom d'hôte doit commencer et se terminer par un caractère alphanumérique.
  *  Le préfixe de nom d'hôte ne doit pas dépasser 10 caractères.

### Libellé de sous-domaine
{: #vc_hybrid_orderinginstance-subdomain-label}

Le libellé du sous-domaine qui doit respecter les règles suivantes :
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Le libellé de sous-domaine doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Le libellé de sous-domaine ne doit pas dépasser 10 caractères.
* Le libellé de sous-domaine doit être unique dans toutes les instances de votre configuration multisite.

### Nom de domaine
{: #vc_hybrid_orderinginstance-domain-name}

Le nom du domaine racine qui doit respecter les règles suivantes :
* Le nom de domaine doit être composé d'au moins deux chaînes séparées par un point (.)
* La première chaîne doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique.
* Toutes les chaînes, à l'exception de la dernière, ne peuvent contenir que des caractères alphanumériques et des tirets (-).
* La dernière chaîne ne peut contenir que des caractères alphabétiques.
* La dernière chaîne doit comporter entre 2 et 24 caractères.

La longueur maximale du nom de domaine complet des hôtes et des machines virtuelles est de 50 caractères. Les noms de domaine doivent respecter cette longueur maximale.
{:note}

### Réseau public ou privé
{: #vc_hybrid_orderinginstance-public-private-network}

Les paramètres d'activation de carte d'interface réseau varient selon que vous sélectionnez **Réseau public et réseau privé** ou **Réseau privé uniquement**.

Si vous sélectionnez l'option **Réseau privé uniquement** :
* Les passerelles ESG VMware NSX ne sont pas mises à disposition (ni la passerelle ESG des services de gestion ni la passerelle ESG gérée par le client).
* Les services complémentaires suivants, qui nécessitent des cartes d'interface réseau publiques, ne sont pas disponibles :
  * F5 on {{site.data.keyword.cloud_notm}}
  * Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
  * Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### Commander de nouveaux VLAN
{: #vc_hybrid_orderinginstance-new-vlans}

Sélectionnez **Commander de nouveaux VLAN** pour commander un nouveau VLAN public et deux nouveaux VLAN privés.

Un VLAN public et deux VLAN privés sont nécessaires pour votre commande d'instance. Les deux VLAN privés sont liés respectivement à chaque serveur bare metal.

### Sélectionner des VLAN existants
{: #vc_hybrid_orderinginstance-existing-vlans}

En fonction de l'{{site.data.keyword.CloudDataCent_notm}} que vous avez sélectionné, des VLAN publics et privés existants peuvent être disponibles.

Un VLAN public et deux VLAN privés sont nécessaires pour votre commande d'instance. Les deux VLAN privés sont liés respectivement à chaque serveur bare metal.

Choisissez **Sélectionner des VLAN existants** pour réutiliser des VLAN publics et privés existants et faites votre choix parmi les VLAN et les sous-réseaux disponibles.

* Vérifiez que la configuration de pare-feu sur les VLAN sélectionnés ne bloque pas le trafic des données de gestion.
* Vérifiez que tous les VLAN sélectionnés se trouvent dans le même pod, car les serveurs ESXi ne peuvent pas être mis à disposition sur des VLAN multi-pods.
{:important}

### Configuration DNS
{: #vc_hybrid_orderinginstance-dns-config}

Sélectionnez la configuration de système de noms de domaine (DNS, Domain Name System) de votre instance :

* **Une instance de serveur virtuel Windows publique pour Active Directory/DNS** : une unique instance de serveur virtuel Windows Microsoft pour Microsoft Active Directory (AD), qui fonctionne en tant que serveur de noms de domaine pour l'instance où sont enregistrés les hôtes et les machines virtuelles, est déployée et peut être interrogée.
* **Deux machines virtuelles Windows Server dédiées à haute disponibilité sur le cluster de gestion** : deux machines virtuelles Microsoft Windows sont déployées, pour plus de sécurité et de robustesse.

Vous devez fournir deux licences Standard Edition de Microsoft Windows Server 2016 si vous configurez votre instance de manière à utiliser les deux machines virtuelles Microsoft Windows.
{:important}

Chaque licence ne peut être affectée qu'à un seul serveur physique et couvre jusqu'à deux processeurs physiques. Une licence d'édition Standard est à même d'exécuter deux machines virtuelles Microsoft Windows virtualisées par serveur à 2 processeurs. Par conséquent, deux licences sont nécessaires puisque deux machines virtuelles Microsoft Windows sont déployées sur deux hôtes différents.

Vous disposez de 30 jours pour activer les machines virtuelles.

Pour en savoir plus sur la commande des licences Windows Server 2016, voir [Prise en main de Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:new_window}.

## Paramètres de services
{: #vc_hybrid_orderinginstance-addon-services}

Lorsque vous commandez une instance vCenter Server with Hybridity Bundle, vous pouvez également commander des services supplémentaires. Pour plus d'informations sur les services, voir [Services disponibles pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances).

## Récapitulatif de la commande
{: #vc_hybrid_orderinginstance-order-summary}

Selon la configuration que vous avez sélectionnée pour l'instance et les services complémentaires, le coût estimé est généré et affiché instantanément dans la section **Récapitulatif de la commande** sur le panneau de droite. Cliquez sur **Détails concernant la tarification** pour générer un document PDF contenant le récapitulatif des coûts pour les ressources {{site.data.keyword.vmwaresolutions_short}}. 

Vous pouvez également ajouter les ressources mises à disposition à l’outil d’estimation {{site.data.keyword.cloud_notm}} en cliquant sur **Ajouter à l'estimation**. Cela est utile si vous souhaitez estimer le coût des ressources {{site.data.keyword.vmwaresolutions_short}} sélectionnées avec d'autres ressources {{site.data.keyword.cloud_notm}} que vous pourriez envisager d'acheter.

## Procédure de commande d'instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_orderinginstance-procedure}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **vCenter Server** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vCenter Server on IBM Cloud**, cliquez sur la carte **vCenter Server with Hybridity Bundle**, puis sur **Créer**.
3. Sur la page **vCenter Server**, entrez le nom de l'instance.
5. Sélectionnez la version vSphere.
4. Sélectionnez le type d'instance :
   * Cliquez sur **Instance principale** pour déployer une seule instance dans l'environnement ou pour déployer la première instance dans une topologie multisite.
   * Cliquez sur **Instance secondaire** pour connecter l'instance à une instance (principale) existante dans l'environnement à des fins de haute disponibilité et procédez comme suit :
     1. Sélectionnez l'instance principale à laquelle vous voulez que l'instance secondaire soit connectée.
     2. Pour les instances principales V2.8 ou ultérieures, entrez le mot de passe administrateur vCenter Server pour l'instance principale.
     3. Pour les instances principales V2.7 ou antérieures, entrez le mot de passe administrateur PSC pour l'instance principale.
6. Sélectionnez l'édition de licence NSX et l'édition de licence vSAN.
7. Spécifiez les paramètres de serveur bare metal.
  1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger l'instance.
  2. Sélectionnez le modèle d'UC **Skylake** ou **Broadwell** et la quantité de mémoire **RAM**.
8. Procédez à la configuration du stockage. Spécifiez les types de disque pour les disques de cache et de capacité, ainsi que le nombre de disques. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
9. Procédez à la configuration de l'interface réseau.
  1. Entrez le préfixe du nom d'hôte de l'instance mise à disposition, le libellé de sous-domaine et le nom du domaine racine.
  2. Sélectionnez le paramètre réseau **Réseau public et réseau privé** ou **réseau privé uniquement**.
  3. Sélectionnez la configuration VLAN.
     *  Si vous voulez commander de nouveaux VLAN publics et privés, cliquez sur **Commander de nouveaux VLAN**.
     *  Si vous voulez réutiliser les VLAN publics et privés existants lorsqu'ils sont disponibles, cliquez sur **Sélectionner des VLAN existants**, puis sélectionnez le VLAN public, le sous-réseau principal, le VLAN privé, le sous-réseau principal privé et le VLAN privé secondaire.
  4. Sélectionnez la configuration DNS.
10. Effectuez la configuration du service HCX on {{site.data.keyword.cloud_notm}} inclus. Pour savoir comment indiquer les paramètres d'un service, voir la section _Configuration de VMware HCX on IBM Cloud_ dans [Commande de VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering#vmware-hcx-on-ibm-cloud-configuration).
11. Sélectionnez les services complémentaires à déployer dans l'instance en cliquant sur la carte de service correspondante. Si un service nécessite de la configuration, spécifiez les paramètres qui lui sont propres et cliquez sur **Ajouter un service** sur la carte.  
Pour savoir comment indiquer les paramètres d'un service, voir la rubrique de commande de service correspondante.

12. Sur la page **Récapitulatif de la commande**, vérifiez la configuration de l'instance avant de passer la commande.
   1. Passez en revue les paramètres de l'instance.
   2. Passez en revue le coût estimé de l'instance. Cliquez sur **Détails concernant la tarification** pour générer un récapitulatif au format PDF. Pour sauvegarder ou imprimer votre récapitulatif de commande, cliquez sur l'icône d'**impression** ou de **téléchargement** dans l'angle supérieur droit de la fenêtre du PDF.
   3. Cliquez sur le ou les liens des conditions applicables à votre commande et prenez soin d'accepter ces conditions avant de commander l'instance.
   4. Cliquez sur **Mettre à disposition**.

## Que se passe-t-il après la commande d'instances vCenter Server with Hybridity Bundle ?
{: #vc_hybrid_orderinginstance-results}

* Le déploiement de l'instance démarre automatiquement et vous recevez la confirmation que la commande est en cours de traitement. Vous pouvez vérifier l'état du déploiement, y compris tout problème pouvant nécessiter votre attention, en consultant la section **Historique de déploiement** des détails de l'instance. 
* Une fois l'instance correctement déployée, les composants décrits dans [Spécifications techniques relatives aux instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs) sont installés sur votre plateforme virtuelle VMware. Les serveurs ESXi que vous avez commandés sont, par défaut, regroupés en **cluster1**. Si vous avez commandé des services complémentaires, le déploiement des services commence une fois votre commande honorée.
* Lorsque l'instance est prête pour utilisation, elle prend le statut **Prêt à l'emploi** et vous recevez une notification par courrier électronique.
* Lorsque vous commandez une instance secondaire, le client Web VMware vSphere de l'instance principale (liée à l'instance secondaire) devra peut-être être redémarré une fois la commande d'instance secondaire honorée.

## Etape suivante
{: #vc_hybrid_orderinginstance-next}

Affichez et gérez l'instance vCenter Server with Hybridity Bundle que vous avez commandée.

Vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou tout autre élément extérieur à la console.
Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.
{:important}

**ATTENTION :** gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lorsque vous avez commandé l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque de rendre votre environnement instable. Ces activités de gestion incluent :
*  L'ajout, la modification, le retour ou la suppression de composants
*  L'extension ou la réduction de la capacité de l'instance via l'ajout ou la suppression de serveurs ESXi
*  La mise hors tension de composants
*  Le redémarrage de services

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

## Liens connexes
{: #vc_hybrid_orderinginstance-related}

* [Inscription à un compte {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts)
* [Affichage des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [Configuration multisite pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_multisite)
* [Ajout et affichage de clusters pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Suppression des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)

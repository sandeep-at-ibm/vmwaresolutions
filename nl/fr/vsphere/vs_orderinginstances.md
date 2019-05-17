---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-26"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Commande de nouveaux clusters vSphere
{: #vs_orderinginstances}

Pour déployer une plateforme virtuelle VMware hautement personnalisable, commandez un cluster VMware vSphere on {{site.data.keyword.cloud}}. Cette procédure permet de définir un nouveau cluster vSphere.

Cette procédure vous guide lors de la sélection des composants VMware, des paramètres de serveur Bare Metal {{site.data.keyword.cloud_notm}}, des paramètres de stockage, des options de mise en réseau, pour créer un nouveau cluster. Une fois la commande passée, la configuration de cluster est capturée de sorte que vous pouvez y revenir et continuer, au besoin, à augmenter le cluster. Lorsque la commande est terminée, vous pouvez configurer manuellement le cluster VMware selon vos besoins.

## Conditions requises
{: #vs_orderinginstances-req}

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Gestion des paramètres et comptes utilisateur](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).

## Paramètres système
{: #vs_orderinginstances-sys-settings}

Vous devez spécifier les paramètres système suivants lorsque vous commandez un nouveau cluster vSphere :

### Nom de cluster
{: #vs_orderinginstances-cluster-name}

Le nom de cluster doit être unique au sein de votre compte.

## Paramètres d'octroi de licence
{: #vs_orderinginstances-licensing-settings}

Sélectionnez les composants VMware à commander avec votre cluster et spécifiez l'option d'octroi de licence pour les composants.

### Offres groupées de composants pour des partenaires commerciaux IBM
{: #vs_orderinginstances-component-bundles-for-bp-users}

Si vous êtes un partenaire commercial IBM, vous pouvez sélectionner une offre groupée de licences de composant lorsque vous commandez un nouveau cluster vSphere. Les offres groupées suivantes sont disponibles :

Tableau 1. Offres groupées de composants pour les clusters vSphere réservées aux partenaires commerciaux IBM

| Offre groupée | Composants                   |
|:------------------------- |:----------------------- |
| Standard with Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

Vous pouvez également inclure dans votre commande les composants VMware suivants :
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

L'option BYOL n'est pas disponible pour les partenaires commerciaux IBM.
{:note}

### Composants individuels pour des partenaires non commerciaux
{: #vs_orderinginstances-individual-components-for-non-bp-users}

Si vous n'êtes pas un partenaire commercial, vous pouvez sélectionner les composants suivants pour votre cluster vSphere :
* VMware vSphere Enterprise Plus 6.7 U1 ou 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

Le composant VMware vSAN n'est pas disponible lorsque vous commandez VMware vSphere Enterprise Plus 6.0. Si vous prévoyez d'utiliser votre propre licence pour VMware vSphere Enterprise Plus 6.0, un ticket d'infrastructure {{site.data.keyword.cloud_notm}} sera ouvert en votre nom. Ce ticket demande que les licences vSphere des serveurs {{site.data.keyword.baremetal_short}} commandés soient remplacées par vos propres licences.
{:note}

### Options d'octroi de licence
{: #vs_orderinginstances-licensing-options}

Vous disposez des options d'octroi de licence suivantes pour les composants VMware sélectionnés :
* **Inclure une licence avec achat** : avec cette option, une nouvelle licence est achetée en votre nom pour le composant VMware. Une licence VMware combinée est générée afin de correspondre à la taille du cluster de la commande.
* **Je fournirai la licence** : avec cette option, vous utilisez votre propre licence pour le composant VMware.

Si vous choisissez d'acheter toutes les licences, sauf pour vSphere Enterprise Plus et vCenter Server, et que vous commandez plusieurs serveurs ESXi, un ticket {{site.data.keyword.cloud_notm}} est automatiquement ouvert en votre nom afin de combiner les clés de licence. Vous êtes chargé du suivi du ticket afin de vous assurer que vous n'utilisez que les clés de licence générées par l'équipe DevOps.

L'utilisation de clés de licence individuelles avec les clés de licence combinées ne répond pas aux exigences de paiement des licences dont vous aurez besoin.
{:important}

## Paramètres de serveur bare metal
{: #vs_orderinginstances-bare-metal-settings}

### Emplacement de centre de données
{: #vs_orderinginstances-dc-location}

Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} dans lequel le cluster doit être hébergé.

**Remarques :**
* Si vous sélectionnez un composant vSAN, la liste des emplacements est filtrée par disponibilité SSD.
* Les serveurs bare metal Broadwell ne sont pas disponible dans le centre de données **FRA05 de Francfort**.
* Les serveurs bare metal Broadwell certifiés SAP ne sont pas disponible dans le centre de données **LON05 de Londres**.

### Skylake
{: #vs_orderinginstances-skylake}

Lorsque vous sélectionnez **Skylake**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM de serveur bare metal adaptée à vos besoins. Les options disponibles varient selon que vous avez ou non sélectionné le composant VMware vSAN.

Tableau 2. Options pour les serveurs Skylake {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

### Certifiés SAP
{: #vs_orderinginstances-sap}

L'onglet **Certifiés SAP** n'est pas disponible si vous avez précédemment sélectionné VMware vSAN. Lorsque vous sélectionnez **Certifiés SAP**, vous ne pouvez pas modifier les paramètres d'UC ou de mémoire RAM.

En fonction de vos besoins, sélectionnez une configuration de serveur bare metal :
  * Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/192 Go de mémoire RAM
  * Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/384 Go de mémoire RAM
  * Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz/768 Go de mémoire RAM
  * Processeur Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz/512 Go de mémoire RAM
  * Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,2 GHz/1024 Go de mémoire RAM
  * Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,2 GHz/2048 Go de mémoire RAM
  * Processeur Quad Intel Xeon E7-8890 v4/96 coeurs au total, 2,2 GHz/4096 Go de mémoire RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

Lorsque vous sélectionnez **Broadwell**, vous pouvez choisir la combinaison de modèle d'UC et de mémoire RAM de serveur bare metal adaptée à vos besoins. Les options disponibles varient selon que vous avez ou non sélectionné le composant VMware vSAN.

Tableau 3. Options pour les serveurs Broadwell {{site.data.keyword.baremetal_short}}

| Options de modèle d'UC        | Options de RAM       |
|:------------- |:------------- |
| Quad Intel Xeon E7-4820 v4/40 coeurs au total, 2,0 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |
| Quad Intel Xeon E7-4850 v4/64 coeurs au total, 2,1 GHz | 128 Go, 256 Go, 512 Go, 1 To, 2 To, 3 To |

### Nombre de serveurs bare metal
{: #vs_orderinginstances-bare-metal-number}

Nombre de serveurs ESXi que vous voulez ajouter au cluster vSphere. Tous les serveurs ESXi ont la même configuration.
* Si vous avez sélectionné le composant VMware NSX, un minimum de trois serveurs est requis.
* Si vous avez sélectionné le composant VMware vSAN, un minimum de quatre serveurs est requis.

## Paramètres de stockage
{: #vs_orderinginstances-storage-settings}

Pour les commandes sans vSAN, les serveurs ESXi sont commandés avec un châssis de 12 disques, avec deux disques pour le système d'exploitation ESXi.

Pour les commandes avec vSAN, les serveurs ESXi sont commandés avec un châssis de 12 disques et quatre disques commandés : deux pour le système d'exploitation ESXi et deux réservés à la mise en cache. Ces paramètres sont configurés par défaut et ne sont pas modifiables. Vous pouvez commander davantage de capacité sur disques en renseignant la zone **Type et taille de disque pour disques de capacité vSAN** et **Nombre de disques de capacité vSAN**.

Si vous sélectionnez le composant VMware vSAN pour le cluster, spécifiez les paramètres suivants :
* **Type et taille de disque pour disques de capacité vSAN** : sélectionnez une option correspond aux disques de capacité dont vous avez besoin.
* **Nombre de disques de capacité vSAN** : indiquez le nombre de disques de capacité que vous souhaitez ajouter.
* Si vous souhaitez augmenter la capacité au-delà de la limite de huit disques, cochez la case **Hautes performances avec Intel Optane**. Cette option fournit deux baies de disques de capacité supplémentaires pour un total de dix disques de capacité. Elle s'avère utile pour les charges de travail qui nécessitent un temps d'attente plus court et une capacité de traitement d'IOPS plus élevée.

  L'option **Hautes performances avec Intel Optane** n'est disponible que pour les modèles d'unités centrales Skylake.
  {:note}

* Passez en revue les valeurs de **type de disque pour les disques de cache vSAN** et de **nombre de disques de cache vSAN**. Ces valeurs dépendent de la sélection de la case **Hautes performances avec Intel Optane**.

## Paramètres d'interface réseau
{: #vs_orderinginstances-network-interface-settings}

Vous devez spécifier les paramètres d'interface réseau suivants lorsque vous commandez un nouveau cluster vSphere :

### Préfixe de nom d'hôte
{: #vs_orderinginstances-host-name-prefix}

Le nom d'hôte est utilisé pour toutes les commandes de serveur bare metal. Il est recommandé d'utiliser le nom d'hôte pour toutes les machines virtuelles de gestion, telles que vCenter Server et NSX.

Le préfixe du nom d'hôte qui doit respecter les règles suivantes :
* Le nom doit commencer et se terminer par un caractère alphanumérique.
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* La longueur maximale admise est de 10 caractères.

### Libellé de sous-domaine
{: #vs_orderinginstances-subdomain-label}

Le libellé du sous-domaine qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le libellé de sous-domaine doit commencer et se terminer par un caractère alphanumérique.
*  Le libellé de sous-domaine ne doit pas dépasser 10 caractères.
*  Le libellé de sous-domaine doit être unique au sein de votre compte.

### Nom de domaine
{: #vs_orderinginstances-domain-name}

Le nom de domaine utilisé pour tous les serveurs {{site.data.keyword.baremetal_short}} et qui doit respecter les règles suivantes :
* Le nom doit être composé d'au moins deux chaînes séparées par un point (.)
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Chaque chaîne doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique et la dernière chaîne ne doit contenir que des caractères alphabétiques.
* La dernière chaîne doit comporter entre 2 et 24 caractères.
* Les autres chaînes doivent comporter entre 1 et 63 caractères.
* Le nom de domaine ne doit pas dépasser 189 caractères.

### Réseau public ou privé
{: #vs_orderinginstances-public-private-network}

Les paramètres d'activation de carte d'interface réseau varient selon que vous sélectionnez **Réseau public et réseau privé** ou **Réseau privé uniquement**.

### Réseaux locaux virtuels
{: #vs_orderinginstances-vlans}

Les paramètres de réseau varient selon que vous sélectionnez **Commander de nouveaux VLAN** ou **Sélectionner des VLAN existants**.

Un VLAN public et deux VLAN privés sont nécessaires pour votre commande de cluster. Les deux VLAN privés sont liés respectivement à chaque serveur bare metal.

#### Commander de nouveaux VLAN
{: #vs_orderinginstances-new-vlans}

Sélectionnez cette option pour commander un nouveau VLAN public et deux nouveaux VLAN privés.

#### Sélectionner des VLAN existants
{: #vs_orderinginstances-existing-vlans}

En fonction de l'{{site.data.keyword.CloudDataCent_notm}} que vous avez sélectionné, des VLAN publics et privés existants peuvent être disponibles.

  Lorsque vous sélectionnez cette option pour réutiliser des VLAN publics et privés existants, spécifiez les VLAN et les sous-réseaux :
  * **VLAN public**, pour l'accès au réseau public.
  * **VLAN privé**, pour la connectivité entre les centres de données et les services dans {{site.data.keyword.cloud_notm}}.
  * **VLAN privé secondaire**, pour les dispositifs VMware, tels que vSAN.
  * **Sous-réseau principal**, affecté aux hôtes physiques pour l'accès au réseau public.
  * **Sous-réseau privé principal**, affecté aux hôtes physiques pour le trafic de gestion.

**Important :**
* Vérifiez que la configuration de pare-feu sur les VLAN sélectionnés ne bloque pas le trafic des données de gestion.
* Vérifiez que tous les VLAN sélectionnés se trouvent dans le même pod. Les serveurs ESXi ne peuvent pas être mis à disposition sur des VLAN multi-pods.

#### Paire à haute disponibilité de dispositifs FortiGate Physical Appliance série 300
{: #vs_orderinginstances-fortigate-physical-appliance}

Vous pouvez également choisir d'inclure la paire à haute disponibilité de dispositifs FortiGate Physical Appliance série 300 pour sécuriser votre environnement de cloud. Pour plus d'informations, voir [Présentation de FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations).

## Récapitulatif de la commande
{: #vs_orderinginstances-order-summary}

Selon vos configurations, le coût estimé est généré et affiché instantanément dans le panneau **Récapitulatif de la commande** sur la droite. Cliquez sur **Détails concernant la tarification** pour générer un document PDF contenant les détails de l'estimation.

## Procédure de commande de clusters vSphere
{: #vs_orderinginstances-procedure}

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
   Vérifiez que vous vous trouvez sur l'onglet **Créer** et que **Nouveau cluster** est affiché dans la liste **Configurations de cluster**.
3. Entrez le nom du cluster.
4. Sélectionnez les composants VMware :
  * Si vous êtes un partenaire commercial IBM, sélectionnez une offre groupée de licences et d'éventuels composants VMware disponibles supplémentaires.
  * Si vous n'êtes pas un partenaire commercial, sélectionnez le composant, l'édition, le cas échéant, et spécifiez l'option de licence.
  Lorsque vous choisissez de fournir votre propre licence (mode BYOL) pour VMware vSphere Enterprise Plus, un ticket {{site.data.keyword.cloud_notm}} est ouvert automatiquement en votre nom pour demander que les licences vSphere par défaut sur vos serveurs {{site.data.keyword.baremetal_short}} commandés soient remplacées par vos propres licences.   

    **Important :** vous êtes responsable du suivi du ticket afin de remplacer la licence vSphere sur les nouveaux serveurs ESXi commandés. De la sorte, {{site.data.keyword.cloud_notm}} accorde l'annulation des frais de licence vSphere de l'infrastructure {{site.data.keyword.cloud_notm}} initialement fournie. Pour remplacer votre licence ESXi vSphere, voir [Configuration des paramètres de licence pour un hôte ESXi](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.
5. Spécifiez les paramètres de serveur bare metal :
   1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger le cluster.
   2. Sélectionnez la configuration de serveur bare metal.
      * Lorsque vous sélectionnez **Skylake** ou **Broadwell**, spécifiez le modèle d'UC et la taille de mémoire RAM.
      * Lorsque vous sélectionnez **Certifiés SAP**, choisissez l'une des configurations prédéfinies.
   3. Spécifiez le nombre de serveurs bare metal.
6. Si vous avez sélectionné le composant **VMware vSAN**, procédez à la configuration de stockage vSAN. Spécifiez les types de disque pour les disques de cache et de capacité, ainsi que le nombre de disques. Si vous souhaitez obtenir davantage de stockage, cochez la zone **Hautes performances avec Intel Optane**.
7. Spécifiez les paramètres d'interface réseau :
   1. Renseignez les zones Préfixe de nom d'hôte, Libelle de sous-domaine et Nom de domaine.
   2. Sélectionnez le paramètre réseau **Réseau public et réseau privé** ou **réseau privé uniquement**.
   3. Sélectionnez l'interface réseau que vous désirez utiliser .
    * Si vous voulez commander de nouveaux VLAN publics et privés, cliquez sur **Commander de nouveaux VLAN**.
    * Si vous voulez réutiliser les VLAN publics et privés existants lorsqu'ils sont disponibles, cliquez sur **Sélectionner des VLAN existants** et spécifiez les VLAN et éventuellement les sous-réseaux.
    4. Spécifiez si vous souhaitez inclure la paire de dispositifs FortiGate Physical Appliance série 300 à haute disponibilité pour sécuriser votre environnement de cloud.  
8. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration du cluster et le coût estimé.
   * Pour sauvegarder la configuration en tant que modèle sans passer de commande, cliquez sur **Sauvegarde de la configuration**.
   * Pour passer la commande, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

   Seuls les serveurs {{site.data.keyword.baremetal_short}} sont installés. Vous êtes responsable de l'installation et de la configuration des divers composants après déploiement du cluster, tels que VMware vCenter, VMware NSX, VMware vSAN.
   {:note}

### Résultats
{: #vs_orderinginstances-results}

Si vous avez sauvegardé la configuration en tant que modèle, vous obtenez une notification sur la console qui confirme la réussite de la sauvegarde de la configuration et le modèle figure dans la liste **Configurations de cluster**.

Si vous avez passé la commande, le déploiement du cluster démarre automatiquement et vous recevez par courrier électronique la confirmation que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, un courrier électronique vous en avertit.

Les clusters vSphere, contrairement aux instances vCenter Server, ne s'affichent pas sur la page **Ressources**.
{:note}

## Liens connexes
{: #vs_orderinginstances-related}

* [Commande de clusters vSphere on la base de configurations existantes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Mise à l'échelle de clusters existants](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Mise à l'échelle de clusters créés en dehors de la console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

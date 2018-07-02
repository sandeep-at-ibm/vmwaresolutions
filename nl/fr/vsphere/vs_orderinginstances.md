---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

{:tip: .tip}

# Commande de nouveaux clusters vSphere

Pour déployer une plateforme virtuelle VMware hautement personnalisable, commandez un cluster VMware vSphere on {{site.data.keyword.cloud}}. Cette procédure permet de définir un nouveau cluster VMware vSphere.

Cette procédure vous guide lors de la sélection des composants VMware, la définition des paramètres de serveur bare metal {{site.data.keyword.cloud_notm}} et des paramètres de stockage et la sélection des options de mise en réseau, pour créer un nouveau cluster. Une fois la commande passée, la configuration de cluster est capturée de sorte que vous pouvez y revenir et continuer, au besoin, à augmenter le cluster. Lorsque la commande est terminée, vous pouvez configurer manuellement le cluster VMware selon vos besoins.

## Conditions requises

Assurez-vous que :
*  Vous avez configuré les données d'identification de l'infrastructure {{site.data.keyword.cloud_notm}} sur la page **Paramètres**. Pour plus d'informations, voir [Paramètres et comptes utilisateur](../vmonic/useraccount.html).
*  Vous avez passé en revue les exigences et les remarques énoncées dans [Exigences et planification pour les clusters vSphere](vs_planning.html).

## Paramètres système

<!--**Important: Do not modify any values that are set during ordering and cluster deployment. Doing so can result in your cluster becoming unusable.**-->
Vous devez spécifier les paramètres système suivants lorsque vous commandez un nouveau cluster vSphere :

### Nom de cluster

Le nom de cluster doit être unique au sein de votre compte.

## Paramètres d'octroi de licence

Sélectionnez les composants VMware à commander avec votre cluster et spécifiez l'option d'octroi de licence pour les composants.

### (Réservé aux partenaires commerciaux) Offres groupées de composants

Si vous êtes un partenaire commercial, vous pouvez sélectionner une offre groupée de licences de composant lorsque vous commandez un nouveau cluster vSphere. Les offres groupées disponibles sont les suivantes :

Tableau 1. Offres groupées de composants pour les clusters vSphere réservées aux partenaires commerciaux

| Offre groupée | Composants                   |
|:-------------------------|:-----------------------|
| Standard with Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
| Advanced                 | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
| Advanced with Networking | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
| Advanced with Networking and Management | vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

Vous pouvez également inclure dans votre commande les composants VMware supplémentaires suivants :
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

**Remarque :** le mode BYOL n'est pas disponible pour les partenaires commerciaux. L'option **Je fournirai la licence** n'est pas disponible lorsqu'ils passent leur commande.

### (Réservé aux utilisateurs qui ne sont pas des partenaires commerciaux) Composants individuels

Si vous n'êtes pas un partenaire commercial, vous pouvez sélectionner les composants VMware suivants pour votre cluster vSphere:
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

**Remarque :** le composant VMware vSAN n'est pas disponible lorsque vous commandez VMware vSphere Enterprise Plus 6.0. Si vous prévoyez d'utiliser votre propre licence pour VMware vSphere Enterprise Plus 6.0, un ticket d'infrastructure {{site.data.keyword.cloud_notm}} sera ouvert en votre nom pour demander que les licences vSphere des serveurs {{site.data.keyword.baremetal_short}} commandés soient remplacées par vos propres licences.

### Options d'octroi de licence

Vous disposez des options d'octroi de licence suivantes pour les composants VMware sélectionnés :
* **Inclure une licence avec achat** : avec cette option, une nouvelle licence est achetée en votre nom pour le composant VMware. Une licence VMware combinée est générée afin de correspondre à la taille du cluster de la commande.
* **Je fournirai la licence** : avec cette option, vous utilisez votre propre licence pour le composant VMware.

Si vous choisissez d'acheter toutes les licences, sauf pour vSphere Enterprise Plus et vCenter Server, et que vous commandez plusieurs serveurs ESXi, un ticket {{site.data.keyword.cloud_notm}} est automatiquement ouvert en votre nom afin de combiner les clés de licence. Vous êtes chargé du suivi du ticket afin de vous assurer que vous n'utilisez que les clés de licence générées par l'équipe DevOps.

**Important** : l'utilisation de clés de licence individuelles avec les clés de licence combinées ne répond pas aux exigences de paiement des licences dont vous aurez besoin.

## Paramètres de serveur bare metal

### Emplacement de centre de données

Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} dans lequel le cluster doit être hébergé.

**Remarque :** si vous sélectionnez un composant vSAN, la liste des emplacements est filtrée par disponibilité SSD.

### Modèle d'UC et mémoire RAM

Indiquez le modèle d'UC et la mémoire RAM du serveur bare metal.

Tableau 2. Options pour les serveurs {{site.data.keyword.baremetal_short}} personnalisés

| Options d'UC        | Options de RAM       |
|:------------- |:------------- |
| Dual Intel Xeon E5-2620 v4/16 coeurs au total, 2,1 GHz | 64 Go, 128 Go, 256 Go, 384 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz | 64 Go, 128 Go, 256 Go, 384 Go, 512 Go, 768 Go, 1,5 To |
| Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz | 64 Go, 128 Go, 256 Go, 384 Go, 512 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Silver 4110/16 coeurs au total, 2,1 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 5120/28 coeurs au total, 2,2 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |
| Processeur Dual Intel Xeon Gold 6140/36 coeurs au total, 2,3 GHz | 64 Go, 96 Go, 128 Go, 192 Go, 384 Go, 768 Go, 1,5 To |

Les options disponibles varient selon que vous avez ou non sélectionné le composant VMware vSAN.

### Nombre de serveurs bare metal

Nombre de serveurs ESXi que vous voulez ajouter au cluster vSphere. Tous les serveurs ESXi se partagent la même configuration.
* Si vous avez sélectionné le composant VMware NSX, un minimum de 3 serveurs est requis.
* Si vous avez sélectionné le composant VMware vSAN, un minimum de 4 serveurs est requis.

## Paramètres de stockage

Pour les commandes sans vSAN, les serveurs ESXi sont commandés avec un châssis de 12 disques, avec deux disques pour le système d'exploitation ESXi.

Pour les commandes avec vSAN, les serveurs ESXi sont commandés avec un châssis de 12 disques et quatre disques commandés : deux pour le système d'exploitation ESXi et deux réservés à la mise en cache. Ces paramètres sont configurés par défaut et ne sont pas modifiables. Vous pouvez commander davantage de capacité sur disques en renseignant la zone **Type et taille de disque pour disques de capacité vSAN** et **Nombre de disques de capacité vSAN**.

Si vous avez sélectionné le composant VMware vSAN pour le cluster, spécifiez les paramètres suivants :

### Type et taille de disque pour disques de capacité vSAN

Cette option est disponible uniquement si vous avez sélectionné le composant VMware vSAN.

Les types de disque suivants sont disponibles :
* SSD SED 960 Go
* SSD SED 1,9 To
* SSD SED 3,8 To (les unités SSD SED 3,8 To sont prises en charge lorsqu'elles sont officiellement disponibles dans un centre de données)

### Nombre de disques de capacité vSAN

Cette option est disponible uniquement si vous avez sélectionné le composant VMware vSAN. Les options de nombre de disques sont 2, 4, 6 et 8.

## Paramètres d'interface réseau

Vous devez spécifier les paramètres d'interface réseau suivants lorsque vous commandez un nouveau cluster vSphere :

### Préfixe de nom d'hôte

Le nom d'hôte est utilisé pour toutes les commandes de serveur bare metal. Il est recommandé d'utiliser le nom d'hôte pour toutes les machines virtuelles de gestion, telles que vCenter Server, NSX, etc.

Le préfixe du nom d'hôte qui doit respecter les règles suivantes :
* Le nom doit commencer et se terminer par un caractère alphanumérique.
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* La longueur maximale admise est de 10 caractères.

### Libellé de sous-domaine

Le libellé du sous-domaine qui doit respecter les règles suivantes :
*  Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
*  Le libellé de sous-domaine doit commencer et se terminer par un caractère alphanumérique.
*  Le libellé de sous-domaine ne doit pas dépasser 10 caractères.
*  Le libellé de sous-domaine doit être unique au sein de votre compte.

### Nom de domaine

Le nom de domaine utilisé pour tous les serveurs {{site.data.keyword.baremetal_short}} et qui doit respecter les règles suivantes :
* Le nom doit être composé d'au moins deux chaînes séparées par un point (.)
* Seuls les caractères alphanumériques et le tiret (-) sont autorisés.
* Chaque chaîne doit commencer par un caractère alphabétique et se terminer par un caractère alphanumérique et la dernière chaîne ne doit contenir que des caractères alphabétiques.
* La dernière chaîne doit comporter entre 2 et 24 caractères.
* Les autres chaînes doivent comporter entre 1 et 63 caractères.
* Le nom de domaine ne doit pas dépasser 189 caractères.

### Réseaux locaux virtuels

Les paramètres de réseau varient selon que vous sélectionnez **Commander de nouveaux VLAN** ou **Sélectionner des VLAN existants**.

Un VLAN public et deux VLAN privés sont nécessaires pour votre commande de cluster. Les deux VLAN privés sont liés respectivement à chaque serveur bare metal.

#### Commander de nouveaux VLAN
Sélectionnez cette option pour commander un nouveau VLAN public et deux nouveaux VLAN privés.

#### Sélectionner des VLAN existants  
En fonction de l'{{site.data.keyword.CloudDataCent_notm}} que vous avez sélectionné, des VLAN publics et privés existants peuvent être disponibles.

  Lorsque vous sélectionnez cette option pour réutiliser des VLAN publics et privés existants, spécifiez les VLAN et les sous-réseaux :
  * **VLAN public**, pour l'accès au réseau public.
  * **VLAN privé**, pour la connectivité entre les centres de données et les services dans {{site.data.keyword.cloud_notm}}.
  * **VLAN privé secondaire**, pour les dispositifs VMware, tels que vSAN.
  * **Sous-réseau principal**, affecté aux hôtes physiques pour l'accès au réseau public.
  * **Sous-réseau privé principal**, affecté aux hôtes physiques pour le trafic de gestion.

**Important :**
* Vérifiez que la configuration de pare-feu sur les VLAN sélectionnés ne bloque pas le trafic des données de gestion.
* Vérifiez que tous les VLAN sélectionnés se trouvent dans le même pod, car les serveurs ESXi ne peuvent pas être mis à disposition sur des VLAN multi-pods.

#### Paire à haute disponibilité de dispositifs FortiGate Physical Appliance série 300

Vous pouvez également choisir d'inclure la paire à haute disponibilité de dispositifs FortiGate Physical Appliance série 300 pour sécuriser votre environnement de cloud. Pour plus d'informations, voir [Présentation de FortiGate Security Appliance on IBM Cloud](../services/fsa_considerations.html).

## Récapitulatif de la commande

Selon vos configurations, le coût estimé est généré et affiché instantanément dans le panneau **Récapitulatif de la commande** sur la droite. Cliquez sur **Détails concernant la tarification** au bas du panneau pour générer un document PDF contenant les détails relatifs à l'estimation.

## Procédure

1. Dans le catalogue {{site.data.keyword.cloud_notm}}, cliquez sur **VMware** dans le panneau de navigation de gauche, puis cliquez sur **VMware vSphere** dans la section **Centres de données virtuels**.
2. Sur la page **VMware vSphere on IBM Cloud**, cliquez sur **Créer**.  
   Vérifiez que vous vous trouvez sur l'onglet **Créer** et que **Nouveau cluster** est affiché dans la liste **Configurations de cluster**.
3. Entrez le nom du cluster.
4. Sélectionnez les composants VMware :
  * Si vous êtes un partenaire commercial, sélectionnez une offre groupée de licences et des composants VMware disponibles supplémentaires.
  * Si vous n'êtes pas un partenaire commercial, sélectionnez le composant, l'édition, le cas échéant, et spécifiez l'option d'octroi de licence.
  Lorsque vous choisissez de fournir votre propre licence (mode BYOL) pour VMware vSphere Enterprise Plus, un ticket {{site.data.keyword.cloud_notm}} est ouvert automatiquement en votre nom pour demander que les licences vSphere par défaut sur vos serveurs {{site.data.keyword.baremetal_short}} commandés soient remplacées par vos propres licences.   

    **Important** : vous êtes chargé du suivi du ticket afin de garantir le remplacement de la licence vSphere sur les serveurs ESXi que vous venez de commander et faire en sorte que l'infrastructure {{site.data.keyword.cloud_notm}} accorde l'annulation des frais de la licence vSphere d'infrastructure {{site.data.keyword.cloud_notm}} initialement fournie. Pour remplacer votre licence ESXi vSphere, voir [Configuration des paramètres de licence pour un hôte ESXi](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}.

5. Spécifiez les paramètres de serveur bare metal :
   1. Sélectionnez l'{{site.data.keyword.CloudDataCent_notm}} qui doit héberger le cluster.
   2. Sélectionnez le modèle d'UC et la taille de mémoire RAM.
   3. Spécifiez le nombre de serveurs bare metal.
6. Si vous avez sélectionné **Stockage vSAN**, spécifiez les paramètres de stockage vSAN en renseignant les zones **Type et taille de disque pour disques de capacité vSAN** et **Nombre de disques de capacité vSAN**.
7. Spécifiez les paramètres d'interface réseau :
   1. Renseignez les zones Préfixe de nom d'hôte, Libelle de sous-domaine et Nom de domaine.
   2. Sélectionnez l'interface réseau à utiliser :
    * Si vous voulez commander de nouveaux VLAN publics et privés, cliquez sur **Commander de nouveaux VLAN**.
    * Si vous voulez réutiliser les VLAN publics et privés existants lorsqu'ils sont disponibles, cliquez sur **Sélectionner des VLAN existants** et spécifiez les VLAN et éventuellement les sous-réseaux.
    3. Spécifiez si vous souhaitez inclure la paire de dispositifs FortiGate Physical Appliance série 300 à haute disponibilité pour sécuriser votre environnement de cloud.  
8. Sur le panneau **Récapitulatif de la commande**, vérifiez la configuration du cluster et le coût estimé.
   * Pour sauvegarder la configuration en tant que modèle sans passer de commande, cliquez sur **Sauvegarde de la configuration**.
   * Pour passer la commande, assurez-vous que le compte qui devra être facturé est correct, passez en revue et acceptez les conditions, puis cliquez sur **Mettre à disposition**.

   **Remarque** : seuls les serveurs {{site.data.keyword.baremetal_short}} sont installés. Vous êtes responsable de l'installation et de la configuration des divers composants après déploiement du cluster, tels que VMware vCenter, VMware NSX, VMware vSAN.

## Résultats

Si vous avez sauvegardé la configuration en tant que modèle, vous obtenez une notification sur la console qui confirme la réussite de la sauvegarde de la configuration et le modèle figure dans la liste **Configurations de cluster**.

Si vous avez passé la commande, le déploiement du cluster démarre automatiquement et vous recevez par courrier électronique la confirmation que la commande est en cours de traitement. Lorsque le cluster est prêt pour utilisation, un courrier électronique vous en avertit.

**Remarque :** contrairement aux instances vCenter Server et Cloud Foundation, les clusters vSphere ne s'affichent pas sur la page **Instances déployées**.

## Liens connexes

* [Commande de clusters vSphere sur la base de configurations existantes](vs_orderingbasedonexistingconfig.html)
* [Mise à l'échelle de clusters existants](vs_scalingexistingclusters.html)
* [Mise à l'échelle de clusters créés en dehors de la console](vs_orderingforclustersoutside.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de vCenter Server
{: #vc_vcenterserveroverview}

VMware vCenter Server on {{site.data.keyword.cloud}} est un cloud privé hébergé qui offre la pile VMware vSphere en tant que service. L'environnement VMware est construit sur {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, offre un stockage sur réseau partagé et des options de stockage à définition logicielle dédié. Il inclut également la configuration et le déploiement automatique d'un pare-feu périphérique logique simple à gérer optimisé pour VMware NSX.

Dans de nombreux cas, l'ensemble de l'environnement peut être mis à disposition en moins d'une journée et l'infrastructure bare metal peut rapidement et de manière élastique augmenter ou diminuer en fonction des besoins de la capacité de calcul.

Après le déploiement, vous pouvez augmenter le stockage partagé en commandant davantage de partages de fichiers NFS (Network File System) à partir du portail {{site.data.keyword.slportal}} et en les connectant manuellement à tous les serveurs ESXi d'un cluster.Si vous avez besoin d'un stockage dédié, [NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview) est offert en configuration hautes performances (entièrement SSD) et en configuration haute capacité (entièrement SATA).

VMware vSAN est également disponible en tant qu'option de stockage dédié. Pour augmenter la capacité d'un stockage basé sur vSAN d'un cluster vSAN, vous pouvez ajouter d'autres serveurs ESXi après le déploiement.

Si vous avez acheté une licence VMware fournie par IBM, vous pouvez mettre l'édition de base VMware NSX au niveau Advanced ou Enterprise et vous pouvez acheter davantage de composants VMware, tels que VMware vRealize Operations.

Vous pouvez ajouter des services gérés par IBM si vous voulez décharger les opérations quotidiennes et la maintenance de la virtualisation, du système d'exploitation invité ou des couches application. L'équipe {{site.data.keyword.cloud_notm}} Professional Services est également disponible pour vous aider à accélérer votre transition vers le cloud en vous offrant des services de migration, d'implémentation, de planification et d'intégration.

## Architecture vCenter Server
{: #vc_vcenterserveroverview-archi}

Le graphique suivant décrit l'architecture de haut niveau et les composants d'un déploiement vCenter Server à trois noeuds.

Figure 1. Architecture vCenter Server de haut niveau pour un cluster à trois noeuds ![Architecture vCenter Server](vc_architecture.svg "Architecture vCenter Server de haut niveau pour un cluster à trois noeuds")

### Infrastructure physique
{: #vc_vcenterserveroverview-physical-infras}

Cette couche fournit l'infrastructure physique (ressources de calcul, de stockage et réseau) qu'utilise l'infrastructure virtuelle.

### Infrastructure de virtualisation (calcul et réseau)
{: #vc_vcenterserveroverview-virtualization-infras}

Cette couche virtualise l'infrastructure physique par le biais de différents produits VMware :
* VMware vSphere virtualise les ressources de calcul physiques.
* VMware NSX est la plateforme de virtualisation réseau qui fournit les composants de mise en réseau logique et les réseaux virtuels.

### Gestion de la virtualisation
{: #vc_vcenterserveroverview-virtualization-mgmt}

Cette couche se compose du dispositif vCenter Server Appliance (vCSA) avec Platform Services Controller (PSC) intégré, NSX Manager, deux NSX ESG, trois NSX Controllers et l'instance de serveur virtuel (VSI) IBM CloudDriver. L'instance de serveur virtuel CloudDriver est déployée à la demande en fonction des besoins de certaines opérations, telles que l'ajout d'hôtes à l'environnement.

L'offre de base est déployée avec un dispositif vCenter Server dimensionné de manière à prendre en charge un environnement comportant jusqu'à 400 hôtes et jusqu'à 4000 machines virtuelles. Les mêmes outils et scripts compatibles API vSphere peuvent être utilisés pour gérer l'environnement VMware hébergé par IBM.

Au total, l'offre de base nécessite 38 UC virtuelles et 67 Go de vRAM réservés pour la couche de gestion de la virtualisation. La capacité hôte restante pour vos machines virtuelles dépend de plusieurs facteurs, tels que le taux de surabonnement, le dimensionnement des machines virtuelles et les besoins de performances de la charge de travail.

Pour plus d'informations sur l'architecture, voir [Référence de l'architecture {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Spécifications techniques relatives aux instances vCenter Server
{: #vc_vcenterserveroverview-specs}

Les composants suivants sont inclus dans votre instance vCenter Server.

La disponibilité et la tarification des configurations matérielles normalisées peuvent varier en fonction de l'{{site.data.keyword.CloudDataCent_notm}} sélectionné pour le déploiement.
{:note}

### Serveur bare metal
{: #vc_vcenterserveroverview-bare-metal}

Vous pouvez commander trois serveurs {{site.data.keyword.baremetal_short}} ou plus dans l'une des configurations suivantes :
* **Skylake** : Génération Intel Skylake 2 UC (série Intel Xeon 4100/5100/6100) avec le modèle d'UC et la taille de mémoire RAM que vous avez sélectionnés.
* **Certifiés SAP** : serveurs des générations Intel Skylake ou Intel Broadwell (Intel série Xeon 6140/E5-2690/E7-8890) avec votre modèle d'UC sélectionné.
* **Broadwell** : serveurs des générations Intel Broadwell à 4 UC (Intel série Xeon E7-4800) avec vos modèle d'UC et taille de RAM sélectionnés.

Si vous prévoyez d'utiliser un stockage vSAN, la configuration requiert un minimum de quatre serveurs {{site.data.keyword.baremetal_short}}.
{:note}

### Utilisation en réseau
{: #vc_vcenterserveroverview-networking}

Les composants réseau suivants sont commandés :
*  Liaisons montantes réseau public et privé double de 10 Gbps
*  Trois VLAN (réseaux locaux virtuels) : un VLAN public et deux VLAN privés
*  Un VXLAN (réseau local virtuel extensible) avec routeur logique distribué (DLR) pour éventuelle communication d'est en ouest entre des charges de travail locales connectées à des réseaux de la couche 2 (L2). Le VXLAN est déployé en tant qu'exemple de topologie de routage, que vous pouvez modifier, à partir duquel vous pouvez construire et que vous pouvez supprimer. Vous pouvez également ajouter des zones de sécurité en connectant des VXLAN supplémentaires aux nouvelles interfaces logiques sur le DLR.
*  Deux passerelles de services périphériques VMware NSX :
  * Une passerelle de gestion sécurisée VMware NSX Edge Services Gateway (ESG) pour le trafic de gestion HTTPS sortant, déployée par IBM dans le cadre de la topologie de réseau de gestion. Les machines virtuelles de gestion IBM utilisent cette passerelle ESG pour communiquer avec des composants de gestion IBM externes spécifiques liés à l'automatisation. Pour plus d'informations, voir [Configuration du réseau en vue d'utiliser la passerelle ESG gérée par le client](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Cette passerelle ESG se nomme **mgmt-nsx-edge**. Vous n'avez pas accès à cette passerelle ESG et vous ne pouvez pas l'utiliser. Si vous la modifiez, vous ne pourrez plus gérer l'instance vCenter Server depuis la console {{site.data.keyword.vmwaresolutions_short}}. De plus, si vous utilisez un pare-feu ou désactivez les communications ESG vers des composants de gestion IBM externes, {{site.data.keyword.vmwaresolutions_short}} sera inutilisable.
    {:important}
  * Une passerelle VMware NSX Edge Services Gateway sécurisée gérée par le client pour le trafic de charge de travail HTTPS sortant et entrant. Cette passerelle est déployée par IBM en tant que modèle que vous pouvez modifier pour fournir un accès au réseau privé virtuel ou un accès public. Pour plus d'informations, voir [La passerelle NSX Edge gérée par le client présente-t-elle un risque pour la sécurité ?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#faq-customer-nsx)

### Instance de serveur virtuel
{: #vc_vcenterserveroverview-vsi}

Les instances de serveur virtuel suivantes sont commandées :
* Une instance de serveur virtuel pour IBM CloudBuilder, fermée une fois le déploiement de l'instance terminé.
* (Pour les instances V2.2 et ultérieures) Vous pouvez choisir de déployer une seule instance de serveur virtuel Microsoft Windows Server pour Microsoft Active Directory (AD) ou deux machines virtuelles à haute disponibilité Microsoft Windows dans le cluster de gestion pour plus de sécurité et de robustesse.
* (Pour les instances V1.9 à V2.1) Une instance de serveur virtuel Microsoft Windows Server pour Microsoft Active Directory (AD) est déployée et peut être interrogée. L'instance de serveur virtuel fonctionne en tant que serveur de noms de domaine pour l'instance où sont enregistrés les hôtes et les machines virtuelles.
* (Pour les instances V1.8 et antérieures) Une instance de serveur virtuel pour la sauvegarde basée sur des instantanés des composants de gestion, qui continue à s'exécuter une fois le déploiement de l'instance terminé.

### Stockage
{: #vc_vcenterserveroverview-storage}

Lors du déploiement initial, vous avez le choix entre les options de stockage vSAN et NFS.

Pour les instances en version 2.8 et versions ultérieure, vous pouvez ajouter des partages de stockage NFS à un cluster NFS ou vSAN existant. Pour plus d'informations, voir la section *Ajout de stockage NFS à des instances vCenter Server* dans [Extension et réduction de capacité pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances).
{:note}

#### Stockage vSAN
{: #vc_vcenterserveroverview-vsan-storage}

L'option vSAN offre des configurations personnalisées, avec différentes options en matière de quantité de disques et de taille et de type de disque :
* Quantité de disques : 2, 4, 6 ou 8
* Disque de stockage : SSD SED de 960 Go, SSD SED de 1,9 To ou SSD SED de 3,8 To.

  De plus, deux disques cache de 960 Go par hôte sont également commandés.

  Les unités SSD (Solid State Disk) de 3,8 To sont prises en charge une fois qu'elles sont officiellement disponibles dans un centre de données.
  {:note}
* L'option Hautes performances avec Intel Optane, qui fournit deux baies de disques de capacité supplémentaires pour un total de 12 disques de capacité. Cette option dépend du modèle d'UC.

#### Stockage NFS
{: #vc_vcenterserveroverview-nfs-storage}

L'option NFS offre un stockage de niveau fichier partagé personnalisé pour les charges de travail avec diverses options de taille et de performance :
* Taille : 20 Go à 24 To
* Performances : 0.25, 2, 4 ou 10 IOPS/Go.
* Configuration individuelle des partages de fichiers.

  Le niveau de performance 10 IOPS/Go est limité à une capacité maximale de 4 To par partage de fichiers.
  {:note}

Si vous sélectionnez l'option NFS, un partage de fichiers de 2 To et 4 IOPS/Go pour les composants de gestion est commandé.

#### Stockage sur disque local
{: #vc_vcenterserveroverview-local-disk-storage}

L'option Disques locaux, disponible uniquement pour la configuration de processeur Quad Intel Xeon E7-8890 v4 Bare Metal **certifié SAP**, offre des configurations personnalisées avec différentes options relatives au nombre et au type de disque.

### Licences (fournies par IBM ou BYOL) et frais
{: #vc_vcenterserveroverview-license-and-fee}

* VMware vSphere Enterprise Plus 6.5u2 ou 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
* (Pour les clusters vSAN) VMware vSAN Advanced ou Enterprise 6.6
* Frais de prise en charge et de services (une licence par noeud)

## Spécifications techniques relatives aux noeuds d'extension vCenter Server
{: #vc_vcenterserveroverview-expansion-node-specs}

Chaque noeud d'extension vCenter Server déploie et génère des frais, imputés à votre compte {{site.data.keyword.cloud_notm}}, pour les composants suivants.

### Matériel pour les noeuds d'extension
{: #vc_vcenterserveroverview-expansion-node-hardware}

Un serveur bare metal doté de la configuration présentée dans [Spécifications techniques relatives aux instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vc_vcenterserveroverview-specs).

### Licences et frais pour les noeuds d'extension
{: #vc_vcenterserveroverview-expansion-node-license-and-fee}

* One VMware vSphere Enterprise Plus 6.5u2 ou 6.7u1
* Une pour VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
* Frais de support et de services
* (Pour les clusters vSAN) VMware vSAN Advanced ou Enterprise 6.6

Vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou tout autre élément extérieur à la console. Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.
Gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lors de la commande de l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque d'entraîner une instabilité de votre environnement. Ces activités de gestion incluent :
*  L'ajout, la modification, le retour ou la suppression de composants
*  L'extension ou la réduction de la capacité de l'instance via l'ajout ou la suppression de serveurs ESXi
*  La mise hors tension de composants
*  Redémarrage des services
   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.
   {:important}

## Liens connexes
{: #vc_vcenterserveroverview-related}

* [Nomenclature du logiciel vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Planification des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Stockage connecté pour vCenter Server](/docs/services/vmwaresolutions/services?topic=vmware-solutions-storage-benefits#storage-benefits)
* [Extension de la capacité de partage de fichiers](/docs/infrastructure/FileStorage?topic=FileStorage-expandCapacity#expandCapacity)

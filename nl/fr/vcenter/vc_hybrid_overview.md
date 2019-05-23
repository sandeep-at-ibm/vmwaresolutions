---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de vCenter Server with Hybridity Bundle
{: #vc_hybrid_overview}

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle est une instance disponible en V2.3 et dans les éditions ultérieures. A compter de V2.6, l'instance vCenter Server with Hybridity Bundle est disponible pour les partenaires commerciaux.

Le service vCenter Server with Hybridity Bundle est un cloud privé hébergé qui fournit la pile VMware vSphere en tant que service. L'environnement VMware, qui est construit sur un minimum de quatre serveurs {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}}, inclut VMware vSAN comme stockage dédié, fournit un déploiement et une configuration automatiques d'un pare-feu périphérique logique simple à gérer optimisé pour VMware NSX et comprend le service VMware HCX on {{site.data.keyword.cloud_notm}}.

Dans de nombreux cas, l'ensemble de l'environnement peut être mis à disposition en moins d'une journée et l'infrastructure bare metal peut rapidement et de manière élastique augmenter ou diminuer en fonction des besoins de la capacité de calcul.

Pour augmenter la capacité d'un stockage basé sur vSAN d'un cluster vSAN, vous pouvez ajouter d'autres serveurs ESXi après le déploiement.

Vous pouvez mettre à niveau l'édition VMware NSX Advanced vers l'édition Enterprise et vous pouvez acheter davantage de composants VMware, tels que VMware vRealize Operations.

Vous pouvez ajouter des services gérés par IBM si vous voulez décharger les opérations quotidiennes et la maintenance de la virtualisation, du système d'exploitation invité ou des couches application. L'équipe {{site.data.keyword.cloud_notm}} Professional Services est également disponible pour vous aider à accélérer votre transition vers le cloud en vous offrant des services de migration, d'implémentation, de planification et d'intégration.

## Architecture vCenter Server with Hybridity Bundle
{: #vc_hybrid_overview-archi}

Le graphique suivant décrit l'architecture de haut niveau et les composants d'un déploiement vCenter Server with Hybridity Bundle à trois noeuds.

![Architecture vCenter Server with Hybridity Bundle](../images/hybrid_architecture.svg "Architecture vCenter Server with Hybridity Bundle")

### Infrastructure physique
{: #vc_hybrid_overview-physical-infras}

Cette couche fournit l'infrastructure physique (ressources de calcul, de stockage et réseau) qu'utilise l'infrastructure virtuelle.

### Infrastructure de virtualisation (calcul, stockage et réseau)
{: #vc_hybrid_overview-virtualization-infras}

Cette couche virtualise l'infrastructure physique par le biais de différents produits VMware :
* VMware vSphere virtualise les ressources de calcul physiques.
* VMware Virtual SAN (vSAN) fournit un stockage partagé défini par les logiciels basé sur le stockage des serveurs physiques.
* VMware NSX est la plateforme de virtualisation réseau qui fournit les composants de mise en réseau logique et les réseaux virtuels.

### Gestion de la virtualisation
{: #vc_hybrid_overview-virtualization-mgmt}

Cette couche se compose du dispositif vCenter Server Appliance (vCSA) avec Platform Services Controller (PSC) intégré, NSX Manager, deux NSX ESG, trois NSX Controllers et l'instance de serveur virtuel (VSI) IBM CloudDriver. L'instance de serveur virtuel CloudDriver est déployée à la demande en fonction des besoins de certaines opérations, telles que l'ajout d'hôtes à l'environnement.

L'offre de base est déployée avec un dispositif vCenter Server dimensionné de manière à prendre en charge un environnement comportant jusqu'à 400 hôtes et jusqu'à 4000 machines virtuelles. Les mêmes outils et scripts compatibles API vSphere peuvent être utilisés pour gérer l'environnement VMware hébergé par IBM.

Au total, l'offre de base nécessite 38 UC virtuelles et 67 Go de vRAM réservés pour la couche de gestion de la virtualisation. La capacité hôte restante pour vos machines virtuelles dépend de plusieurs facteurs, tels que le taux de dépassement de capacité, le dimensionnement des machines virtuelles et les besoins de performances de la charge de travail.

Si vous avez besoin de ressources de gestion supplémentaires lors du déploiement du service HCX on {{site.data.keyword.cloud_notm}}, voir [Présentation de VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations).

### Hybridité de l'infrastructure
{: #vc_hybrid_overview-infras-hybrid}

Cette couche fournit une abstraction de ressources entre les sites locaux et les sites {{site.data.keyword.cloud_notm}} de sorte que vous pouvez déplacer les charges de travail vers l'arrière et vers l'avant facilement et en toute sécurité sans avoir à modifier les caractéristiques des machines virtuelles, par exemple, leurs adresses IP.

Sur la base de VMware Hybrid Cloud Extension (HCX), vous pouvez créer des interconnexions à couplage lâche entre les sites locaux et les sites {{site.data.keyword.cloud_notm}} afin d'activer la migration en bloc de machines virtuelles ou le déplacement opérationnel de machines virtuelles via vMotion, sans temps d'indisponibilité.

## Spécifications techniques relatives aux instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_overview-specs}

Les composants suivants sont inclus dans votre instance vCenter Server with Hybridity Bundle :

La disponibilité et la tarification des configurations matérielles normalisées peuvent varier en fonction de l'{{site.data.keyword.CloudDataCent_notm}} sélectionné pour le déploiement.
{:note}

### Serveur bare metal
{: #vc_hybrid_overview-bare-metal}

Vous pouvez commander quatre ou plusieurs serveurs {{site.data.keyword.baremetal_short}} dans l'une des configurations suivantes :
  * **Skylake** : Génération Intel Skylake 2 UC (série Intel Xeon 4100/5100/6100) avec le modèle d'UC et la taille de mémoire RAM que vous avez sélectionnés.
  * **Broadwell** : serveurs des générations Intel Broadwell à 4 UC (Intel série Xeon E7-4800) avec vos modèle d'UC et taille de RAM sélectionnés.

### Utilisation en réseau
{: #vc_hybrid_overview-networking}

Les composants réseau suivants sont commandés :
*  Liaisons montantes réseau public et privé double de 10 Gbps
*  Trois VLAN (réseaux locaux virtuels) : un VLAN public et deux VLAN privés
*  Un VXLAN (réseau local virtuel extensible) avec routeur logique distribué (DLR) pour éventuelle communication d'est en ouest entre des charges de travail locales connectées à des réseaux de la couche 2 (L2). Le VXLAN est déployé en tant qu'exemple de topologie de routage, que vous pouvez modifier, à partir duquel vous pouvez construire et que vous pouvez supprimer. Vous pouvez également ajouter des zones de sécurité en connectant d'autres VXLAN aux nouvelles interfaces logiques sur le DLR.
*  Deux passerelles VMware NSX Edge Services Gateway :
  * Une passerelle de gestion sécurisée VMware NSX Edge Services Gateway (ESG) pour le trafic de gestion HTTPS sortant, déployée par IBM dans le cadre de la topologie de réseau de gestion. Les machines virtuelles de gestion IBM utilisent cette passerelle ESG pour communiquer avec des composants de gestion IBM externes spécifiques liés à l'automatisation. Pour plus d'informations, voir [Configuration du réseau en vue d'utiliser la passerelle ESG gérée par le client](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    Vous n'avez pas accès à cette passerelle ESG et vous ne pouvez pas l'utiliser. Si vous la modifiez, vous ne pourrez peut-être plus gérer l'instance vCenter Server with Hybridity Bundle depuis la console {{site.data.keyword.vmwaresolutions_short}}. De plus, sachez que si vous utilisez un pare-feu ou désactivez les communications ESG vers des composants de gestion IBM externes, {{site.data.keyword.vmwaresolutions_short}} sera inutilisable.
    {:important}
  * Une passerelle VMware NSX Edge Services Gateway sécurisée gérée par le client pour le trafic de charge de travail HTTPS sortant et entrant, déployée par IBM en tant que modèle que vous pouvez modifier pour fournir un accès au réseau privé virtuel ou un accès public. Pour plus d'informations, voir [La passerelle NSX Edge gérée par le client présente-t-elle un risque pour la sécurité ?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#faq-customer-nsx)

Pour plus d'informations sur les composants de mise en réseau commandés lors du déploiement du service HCX on {{site.data.keyword.cloud_notm}}, voir [Présentation de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations).

### Instance de serveur virtuel
{: #vc_hybrid_overview-vsi}

Les instances de serveur virtuel suivantes sont commandées :
* Une instance de serveur virtuel pour IBM CloudBuilder, annulée une fois le déploiement de l'instance terminé.
* Vous pouvez choisir de déployer une seule instance de serveur virtuel Microsoft Windows Server pour Microsoft Active Directory (AD) ou deux machines virtuelles à haute disponibilité Microsoft Windows dans le cluster de gestion pour plus de sécurité et de robustesse.

### Stockage vSAN
{: #vc_hybrid_overview-vsan-storage}

Le stockage vSAN offre des configurations personnalisées, avec différentes options en matière de quantité de disques et de type de disque :
* Quantité de disques : 2, 4, 6 ou 8.
* Disque de stockage : SSD SED de 960 Go, SSD SED de 1,9 To ou SSD SED de 3,8 To.

  De plus, deux disques cache de 960 Go par hôte sont commandés.
* L'option Hautes performances avec Intel Optane, qui fournit deux baies de disques de capacité supplémentaires pour un total de 12 disques de capacité. Cette option dépend du modèle d'UC.

### Licences fournies par IBM et frais
{: #vc_hybrid_overview-license-and-fee}

Les licences suivantes sont incluses avec votre commande d'instance vCenter Server with Hybridity Bundle.

* VMware vSphere Enterprise Plus 6.5u2 ou 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Advanced ou Enterprise) 6.4
* VMware vSAN (Advanced ou Enterprise) 6.6

Des frais supplémentaires de support et de services peuvent s'appliquer.

## Spécifications techniques relatives aux noeuds d'extension vCenter Server with Hybridity Bundle
{: #vc_hybrid_overview-expansion-node-specs}

Chaque noeud d'extension vCenter Server with Hybridity Bundle déployé génère des frais, imputés à votre compte {{site.data.keyword.cloud_notm}}, pour les composants suivants.

### Matériel pour les noeuds d'extension
{: #vc_hybrid_overview-expansion-node-hardware}

Un serveur bare metal doté de la configuration présentée dans [Spécifications techniques relatives aux instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#vc_hybrid_overview-specs).

### Licences et frais pour les noeuds d'extension
{: #vc_hybrid_overview-expansion-node-license-and-fee}

* One VMware vSphere Enterprise Plus 6.5u2 ou 6.7u1
* Une pour VMware NSX Service Providers Edition (Advanced ou Enterprise) 6.4
* Frais de support et de services
* VMware vSAN (Advanced ou Enterprise) 6.6

Vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou tout autre élément extérieur à la console. Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.
{:important}

**ATTENTION :** gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lors de la commande de l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque d'entraîner une instabilité de votre environnement. Ces activités de gestion incluent :
*  L'ajout, la modification, le retour ou la suppression de composants
*  L'extension ou la réduction de la capacité de l'instance via l'ajout ou la suppression de serveurs ESXi
*  La mise hors tension de composants
*  Le redémarrage de services

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

## Liens connexes
{: #vc_hybrid_overview-related}

* [Nomenclature du logiciel vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [Exigences et planification pour les instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Présentation de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

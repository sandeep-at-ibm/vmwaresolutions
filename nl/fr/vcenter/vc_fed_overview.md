---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Présentation de VMware Federal on IBM Cloud

VMware Federal on {{site.data.keyword.cloud}} fournit une prise en charge pour la commande d'une instance vCenter Server de base et fournit aux agences gouvernementales fédérales américaines la possibilité de sécuriser les instances vCenter Server déployées. Sélectionner l'option de sécurisation des instances déployées entraîne la suppression des informations sensibles concernant les instances et supprime la connexion de gestion ouverte pour l'accès entrant à l'instance des fonctions de gestion, telles que l'ajout et la suppression d'hôtes et de clusters. Une fois l'option de sécurisation sélectionnée, toutes les fonctions de gestion sont désactivées sauf celle de suppression complète d'une instance.

Pour plus d'informations sur vCenter Server on {{site.data.keyword.cloud_notm}} et sur l'architecture vCenter Server, voir [Présentation de vCenter Server](vc_vcenterserveroverview.html).

**Attention :** VMware Federal on {{site.data.keyword.cloud_notm}} ne fournit qu'un sous-ensemble des offres vCenter Server. La configuration multisite, les serveurs bare metal {{site.data.keyword.cloud_notm}} préconfigurés, la fonction BYOL (apport de sa propre licence) et l'option permettant de commander des services supplémentaires ne sont pas pris en charge.

## Spécifications techniques relatives aux instances VMware Federal on IBM Cloud

Les composants réseau suivants sont inclus :

### Serveur bare metal

Vous pouvez commander au moins deux serveurs {{site.data.keyword.baremetal_short}} personnalisés avec l'une des configurations suivantes :

* Génération Intel Broadwell 2 UC (série Intel Xeon E5-2600 v4)
* Génération Intel Skylake 2 UC (série Intel Xeon 4100/5100/6100)

Pour une configuration de stockage NFS, le nombre de serveurs {{site.data.keyword.baremetal_short}} recommandé est de trois par défaut.

**Remarque :** si vous sélectionnez un stockage vSAN, la configuration requiert quatre serveurs {{site.data.keyword.baremetal_short}}.

### Utilisation en réseau

Les composants réseau suivants sont commandés :
*  Trois VLAN (réseaux locaux virtuels) : un VLAN public et deux VLAN privés
*  Un VXLAN (réseau local virtuel extensible) avec routeur logique distribué (DLR) pour éventuelle communication d'est en ouest entre des charges de travail locales connectées à des réseaux de la couche 2 (L2). Le VXLAN est déployé en tant qu'exemple de topologie de routage, que vous pouvez modifier, à partir duquel vous pouvez construire et que vous pouvez supprimer. Vous pouvez également ajouter des zones de sécurité en connectant d'autres VXLAN aux nouvelles interfaces logiques sur le DLR.
*  Deux passerelles de services périphériques VMware NSX :
  * Une passerelle de gestion sécurisée VMware NSX Edge Services Gateway (ESG) pour le trafic de gestion HTTPS sortant, déployée par IBM dans le cadre de la topologie de réseau de gestion. Les machines virtuelles de gestion IBM utilisent cette passerelle ESG pour communiquer avec des composants de gestion IBM externes spécifiques liés à l'automatisation. Pour plus d'informations, voir [Configuration du réseau en vue d'utiliser la passerelle ESG gérée par le client](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms).

    **Important** : vous n'avez pas accès à cette passerelle ESG et vous ne pouvez pas l'utiliser. Si vous la modifiez, vous ne pourrez plus gérer l'instance vCenter Server depuis la console {{site.data.keyword.vmwaresolutions_short}}. De plus, sachez que si vous utilisez un pare-feu ou désactivez les communications ESG vers des composants de gestion IBM externes, {{site.data.keyword.vmwaresolutions_short}} sera inutilisable.
  * Une passerelle VMware NSX Edge Services Gateway sécurisée gérée par le client pour le trafic de charge de travail HTTPS sortant et entrant, déployée par IBM en tant que modèle que vous pouvez modifier pour fournir un accès au réseau privé virtuel ou un accès public. Pour plus d'informations, voir [La passerelle NSX Edge gérée par le client présente-t-elle un risque pour la sécurité ?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-).

  **Remarque** : la passerelle VMware NSX Edge Services (ESG) pour le trafic de gestion HTTPS sortant est retirée dans le cadre de l'action de sécurisation de votre instance VMware Federal déployée. Pour plus d'informations, voir [Sécurisation des instances VMware Federal](vc_fed_securinginstance.html).

### Instance de serveur virtuel

Les instances de serveur virtuel suivantes sont commandées :
* Une instance de serveur virtuel pour IBM CloudBuilder, fermée une fois le déploiement de l'instance terminé.
* (Pour les instances V2.3 et ultérieures) Vous pouvez choisir de déployer une seule instance de serveur virtuel Microsoft Windows Server pour Microsoft Active Directory (AD) ou deux machines virtuelles à haute disponibilité Microsoft Windows dans le cluster de gestion pour plus de sécurité et de robustesse.
* (Pour les instances V2.2) Une instance de serveur virtuel Microsoft Windows Server pour Microsoft Active Directory (AD), qui fonctionne en tant que serveur de noms de domaine pour l'instance où sont enregistrés les hôtes et les machines virtuelles, est déployée et peut être interrogée.

### Stockage

Lors du déploiement initial, vous avez le choix entre les options de stockage vSAN et NFS.

L'option vSAN offre des configurations personnalisées, avec différentes options en matière de quantité de disques et de type de disque :
* Quantité de disques : 2, 4, 6 ou 8.
* Disque de stockage : SSD SED de 960 Go, SSD SED de 1,9 To ou SSD SED de 3,8 To.

  De plus, 2 disques cache de 960 Go par hôte sont également commandés.

L'option NFS offre un stockage de niveau fichier partagé personnalisé pour les charges de travail avec diverses options de taille et de performance :
* Taille : 1, 2, 4, 8 ou 12 To.
* Performance : 2, 4 ou 10 IOPS/Go.
* Partages de fichiers configurés individuellement.

Si vous sélectionnez l'option NFS, un partage de fichiers de 2 To, 4 IOPS/Go pour les composants de gestion est commandé.

### Licences fournies par IBM et frais

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
* (Pour les clusters vSAN) VMware vSAN Advanced ou Enterprise 6.6

## Spécifications techniques relatives aux noeuds d'extension VMware Federal on IBM Cloud

Chaque noeud d'extension vCenter Server déployé génère des frais, imputés à votre compte {{site.data.keyword.cloud_notm}}, pour les composants suivants.

### Matériel pour les noeuds d'extension

Un serveur bare metal doté de la configuration présentée dans [Spécifications techniques relatives aux instances VMware Federal sur {{site.data.keyword.cloud_notm}}](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances).

### Licences et frais pour les noeuds d'extension

* Une pour VMware vSphere Enterprise Plus 6.5u1
* Une pour VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
* (Pour les clusters vSAN) VMware vSAN Advanced ou Enterprise 6.6

**Important** : vous devez gérer les composants {{site.data.keyword.vmwaresolutions_short}} créés dans votre compte {{site.data.keyword.cloud_notm}} uniquement depuis la console {{site.data.keyword.vmwaresolutions_short}}, et non depuis le portail	{{site.data.keyword.slportal}} ou autre élément extérieur à la console. Si vous modifiez ces composants en dehors de la console {{site.data.keyword.vmwaresolutions_short}}, les modifications ne sont pas synchronisées avec la console.

**ATTENTION** : gérer des composants {{site.data.keyword.vmwaresolutions_short}} (installés dans votre compte {{site.data.keyword.cloud_notm}} lors de la commande de l'instance) en dehors de la console {{site.data.keyword.vmwaresolutions_short}} risque d'entraîner une instabilité de votre environnement. Ces activités de gestion incluent :
*  L'ajout, la modification, le retour ou la suppression de composants
*  L'extension ou la réduction de la capacité de l'instance via l'ajout ou la suppression de serveurs ESXi
*  La mise hors tension de composants

   Seules les activités de gestion des partages de fichiers du stockage partagé depuis le portail {{site.data.keyword.slportal}} font exception. Il s'agit des activités suivantes : commande, suppression (pouvant avoir un impact sur des magasins de données éventuellement montés), accord d'autorisation et montage de partages de fichiers de stockage partagé.

### Liens connexes

* [Nomenclature du logiciel vCenter Server](vc_bom.html)
* [Exigences et planification pour les instances VMware Federal](vc_fed_planning.html)
* [Commande d'instances VMware Federal](vc_fed_orderinginstance.html)
* [Sécurisation des instances VMware Federal](vc_fed_securinginstance.html)
* [Contacter le support IBM](../vmonic/trbl_support.html)
* [Stockage de fichiers et de blocs d'{{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}

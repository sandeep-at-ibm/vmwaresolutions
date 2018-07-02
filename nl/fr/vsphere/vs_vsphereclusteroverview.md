---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-29"

---

# Présentation de VMware vSphere on IBM Cloud

VMware vSphere on {{site.data.keyword.cloud}} est une plateforme de commande rationalisée et optimisée pour VMware, qui vous permet de construire votre propre environnement VMware hébergé par IBM en personnalisant et en commandant le matériel compatible VMware sur la base des composants VMware sélectionnés.

La console {{site.data.keyword.vmwaresolutions_short}} filtre automatiquement le matériel en fonction des composants VMware que vous avez sélectionnés. Par exemple, lors de la création d'un nouveau cluster VMware vSAN intégralement Flash, seul le matériel validé par le [guide de compatibilité VMware](https://www.vmware.com/resources/compatibility/search.php) est présenté et un minimum de quatre serveurs ESXi requis.

VMware vSphere on {{site.data.keyword.cloud_notm}} n'automatise pas l'installation, la configuration et l'apport des composants VMware optionnels, ce qui vous laisse une grande souplesse dans la conception et l'élaboration de votre environnement VMware hébergé tandis que vous incorporez le matériel compatible VMware.

Utilisez cette offre pour créer un cluster de serveurs ESXi ou en augmenter un existant dans un {{site.data.keyword.CloudDataCent_notm}}. Selon les composants VMware que vous sélectionnez, vous pouvez démarrer avec un seul serveur ESXi dans le cluster puis en ajouter en fonction de vos besoins.

## Composants VMware vSphere on IBM Cloud

Passez en revue les composants VMware vSphere on {{site.data.keyword.cloud_notm}}.

**Remarque** : la disponibilité et la tarification des configurations matérielles normalisées varient en fonction de l'{{site.data.keyword.CloudDataCent_notm}} sélectionné pour le déploiement.

### Composants VMware

Licences (fournies par IBM ou BYOL) pour les composants VMware suivants :
* VMware vSphere Enterprise Plus 6.0u2 ou 6.5u1
* Composants VMware optionnels :
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced ou Enterprise)
   * VMware vSAN (Advanced ou Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Serveur bare metal

Un ou plusieurs serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} avec le modèle d'UC et la taille de mémoire RAM que vous avez sélectionnés :
* Génération Intel Broadwell 2 UC (série Intel Xeon E5-2600 v4)
* Génération Intel Skylake 2 UC (série Intel Xeon 4100/5100/6100)

Les options disponibles varient selon que vous avez ou non sélectionné le composant VMware vSAN.

Les spécifications de disque et de réseau suivantes s'ajoutent :
* Liaisons montantes réseau public et privé double de 10 Gbps
* Un contrôleur de disque RAID

### Utilisation en réseau

* Trois VLAN (réseaux locaux virtuels) : un VLAN public et deux VLAN privés
* (En option) Une paire à haute disponibilité de dispositifs FortiGate Security Appliance

### Stockage

Stockage personnalisé par l'utilisateur pour la configuration vSAN lorsque le composant VMware vSAN est sélectionné :
* Options de disque de stockage :  SSD SED de 960 Go, SSD SED de 1.9 To ou SSD SED de 3.8 To
* Options de nombre de disques : 2, 4, 6 ou 8

**Remarque :** les unités SSD (Solid State Disk) de 3,8 To seront prises en charge une fois officiellement disponibles dans un centre de données.

## Composants des noeuds d'extension de cluster vSphere

Chaque noeud d'extension de cluster vSphere déployé génère des frais, imputés à votre compte de portail {{site.data.keyword.slportal}}, pour les composants suivants.

### Matériel pour les noeuds d'extension

Un serveur bare metal IBM Cloud avec la configuration matérielle présentée dans [Composants VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

### Mise en réseau des noeuds d'extension

Un serveur bare metal IBM Cloud avec la configuration réseau présentée dans [Composants VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

### Composants VMware pour les noeuds d'extension

* Un serveur bare metal IBM Cloud avec VMware vSphere Enterprise Plus 6.0u2 ou 6.5u1  
* Composants VMware facultatifs présentés dans [Composants VMware vSphere on IBM Cloud](../vsphere/vs_vsphereclusteroverview.html#components-of-vmware-vsphere-on-ibm-cloud).

**Important** : vous devez gérer les serveurs ESXi, les composants VMware facultatifs et le matériel supplémentaire commandés et livrés sur votre compte {{site.data.keyword.cloud_notm}} uniquement à partir du portail {{site.data.keyword.slportal}}. Après la création d'un nouveau cluster sur la console {{site.data.keyword.vmwaresolutions_short}}, vous pouvez revenir sur la console pour mettre à l'échelle le nouveau cluster à l'aide de la configuration enregistrée. Pour plus d'informations, voir [Mise à l'échelle de clusters existants](vs_scalingexistingclusters.html).

## Liens connexes

* [Nomenclature du logiciel VMware vSphere](vs_bom.html)
* [Planification des clusters vSphere](vs_planning.html)
* [Commande de clusters vSphere](vs_orderinginstances.html)
* [Mise à l'échelle de clusters vSphere existants](vs_scalingexistingclusters.html)

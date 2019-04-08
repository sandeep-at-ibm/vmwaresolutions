---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de VMware vSphere on IBM Cloud
{: #vs_vsphereclusteroverview}

VMware vSphere on {{site.data.keyword.cloud}} est une plateforme de commande rationalisée et optimisée pour VMware. Cette plateforme vous permet de construire votre propre environnement VMware hébergé par IBM en personnalisant et en commandant le matériel compatible VMware sur la base des composants VMware sélectionnés.

La console {{site.data.keyword.vmwaresolutions_short}} filtre automatiquement le matériel en fonction des composants VMware que vous avez sélectionnés. Par exemple, lors de la création d'un nouveau cluster VMware vSAN exclusivement Flash, seul le matériel validé par le [Guide de compatibilité VMware](https://www.vmware.com/resources/compatibility/search.php) est présenté. Par ailleurs, un minimum de quatre serveurs est requis.

VMware vSphere on {{site.data.keyword.cloud_notm}} n'automatise pas l'installation, la configuration et l'activation des composants VMware facultatifs. Cette plateforme permet une souplesse maximale pour la conception et la construction de votre environnement VMware hébergé tout en intégrant du matériel compatible avec VMware.

Utilisez cette offre pour créer un cluster de serveurs ESXi ou en augmenter un existant dans un {{site.data.keyword.CloudDataCent_notm}}. Selon les composants VMware que vous sélectionnez, vous pouvez démarrer avec un seul serveur ESXi dans le cluster puis en ajouter en fonction de vos besoins.

## Spécifications techniques relatives aux clusters VMware vSphere on IBM Cloud
{: #vs_vsphereclusteroverview-specs}

Passez en revue les composants VMware vSphere on {{site.data.keyword.cloud_notm}}.

La disponibilité et la tarification des configurations matérielles normalisées peuvent varier en fonction de l'{{site.data.keyword.CloudDataCent_notm}} sélectionné pour le déploiement.
{:note}

### Composants VMware
{: #vs_vsphereclusteroverview-specs-vmware-components}

Sélectionnez des licences (fournies par IBM ou BYOL) pour les composants VMware suivants :
* VMware vSphere Enterprise Plus 6.7 U1 ou 6.5 U2
* Les composants VMware suivants sont facultatifs :
   * VMware vCenter Server Standard
   * VMware NSX (Base, Advanced ou Enterprise)
   * VMware vSAN (Advanced ou Enterprise)
   * VMware Site Recovery Manager
   * VMware vRealize Automation Enterprise
   * VMware vRealize Operations Enterprise
   * VMware vRealize Log Insight

### Serveur bare metal
{: #vs_vsphereclusteroverview-specs-bare-metal}

Vous pouvez commander un ou plusieurs serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} dans l'une des configurations suivantes :
* **Skylake** : Génération Intel Skylake 2 UC (série Intel Xeon 4100/5100/6100) avec le modèle d'UC et la taille de mémoire RAM que vous avez sélectionnés.
* **Certifiés SAP** : Génération Intel Skylake ou Intel Broadwell (série Intel Xeon 6140/E5-2690/E7-8890) avec votre modèle d'UC sélectionné.
* **Broadwell** : Génération Intel Broadwell 2 UC (série Intel Xeon E5-2600/E7-4800) avec le modèle d'UC et la taille de mémoire RAM que vous avez sélectionnés.

Les options disponibles varient selon que vous avez ou non sélectionné le composant VMware vSAN.

Les spécifications de disque et de réseau suivantes s'ajoutent :
* Liaisons montantes réseau public et privé double de 10 Gbps
* Un contrôleur de disque RAID

### Utilisation en réseau
{: #vs_vsphereclusteroverview-specs-network}

* Un VLAN public et deux VLAN privés
* (En option) Une paire à haute disponibilité de dispositifs FortiGate Security Appliance

### Stockage
{: #vs_vsphereclusteroverview-specs-storage}

Stockage personnalisé par l'utilisateur pour la configuration vSAN lorsque le composant VMware vSAN est sélectionné :
* Options de disque de stockage : SSD SED de 960 Go, SSD SED de 1,9 To ou SSD SED de 3,8 To
* Options de quantité de disques : 2, 4, 6 ou 8

  De plus, deux disques cache de 960 Go par hôte sont également commandés.

  Les unités SSD (Solid Disk) de 3,8 To sont prises en charge une fois qu'elles sont officiellement disponibles dans un centre de données.
  {:note}
* L'option Hautes performances avec Intel Optane, qui fournit deux baies de disques de capacité supplémentaires pour un total de dix disques de capacité. Cette option dépend du modèle d'UC.

## Spécifications techniques relatives aux noeuds d'extension de cluster vSphere
{: #vs_vsphereclusteroverview-expansion-node-specs}

Chaque noeud d'extension de cluster vSphere déploie et génère des frais, imputés à votre compte {{site.data.keyword.slportal}}, pour les composants suivants.

### Matériel pour les noeuds d'extension
{: #vs_vsphereclusteroverview-expansion-node-specs-hardware}

Un serveur {{site.data.keyword.cloud_notm}} Bare Metal Server doté de la configuration matérielle présentée dans [Spécifications techniques relatives aux clusters VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

### Mise en réseau des noeuds d'extension
{: #vs_vsphereclusteroverview-expansion-node-specs-network}

Un serveur {{site.data.keyword.cloud_notm}} Bare Metal Server doté de la configuration de mise en réseau présentée dans [Spécifications techniques relatives aux clusters VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

### Composants VMware pour les noeuds d'extension
{: #vs_vsphereclusteroverview-expansion-node-specs-vmware-components}

* Un serveur {{site.data.keyword.cloud_notm}} Bare Metal Server doté de VMware vSphere Enterprise Plus 6.7u1 ou 6.5u2.  
* Des composants VMware facultatifs présentés dans [Spécifications techniques relatives aux clusters VMware vSphere on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview#specs).

Vous devez gérer les serveurs ESXi, les composants VMware facultatifs et le matériel supplémentaire commandés et livrés sur votre compte {{site.data.keyword.cloud_notm}} uniquement à partir du portail {{site.data.keyword.slportal}}. Après avoir créé un nouveau cluster sur la console {{site.data.keyword.vmwaresolutions_short}}, vous pouvez revenir sur la console pour mettre à l'échelle le nouveau cluster à l'aide de la configuration enregistrée. Pour plus d'informations, voir [Mise à l'échelle de clusters existants](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters).
{:important}

## Liens connexes
{: #vs_vsphereclusteroverview-related}

* [Nomenclature du logiciel VMware vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)
* [Planification des clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)
* [Commande de clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Mise à l'échelle de clusters vSphere existants](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)

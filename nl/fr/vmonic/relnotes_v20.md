---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notes sur l'édition pour la version 2.0
{: #relnotes_v20}

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour obtenir la liste des erreurs rectifiées dans les différentes éditions, des problèmes connus concernant le produit et des astuces relatives à l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v20-fva}

Le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation instances et VMware vCenter Server en version 2.0 et ultérieure. Ce service déploie dans votre environnement une paire à haute disponibilité de dispositifs FortiGate Virtual Appliance qui vous permettent de réduire les risques en implémentant des contrôles de sécurité critiques au sein de votre infrastructure virtuelle.

Commandez des instances avec le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} déjà inclus ou ajoutez ultérieurement ce service à vos instances existantes à partir de l'onglet **Services** de la page des détails d'instance. En fonction de vos besoins, sélectionnez pour ce service l'une des trois tailles de déploiement et options d'octroi de licence. Une fois le service correctement installé, gérez et configurez des règles de pare-feu pour les dispositifs FortiGate Virtual Appliance depuis la console FortiGate.

Pour plus d'informations, voir les rubriques suivantes :
* [Composants et remarques pour FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [Gestion de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)

## Installation de plusieurs services pour F5 on IBM Cloud et le service FortiGate Virtual Appliance on IBM Cloud
{: #relnotes_v20-multiple-services}

Vous pouvez désormais installer plusieurs instances du service F5 on {{site.data.keyword.cloud_notm}} et le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} pour une instance Cloud Foundation ou vCenter Server. Lorsque vous sélectionnez le service F5 ou le service FortiGate lorsque vous commandez une instance, vous devez indiquer un nom pour l'instance de service de manière à la différentier des instances de service supplémentaires que vous installerez ultérieurement.

Une fois le déploiement de l'instance achevé, vous pouvez ajouter d'autres instances du service F5 ou FortiGate en installant le service à partir de l'onglet **Ajouter des services** de la page des détails de l'instance. Vous ne pouvez ajouter qu'une seule instance de service à la fois et répéter le processus pour toutes les instances que vous voulez ajouter pour un service.

Pour plus d'informations, voir[Commande, affichage et retrait de services pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Mises à jour pour le service FortiGate Security Appliance on IBM Cloud
{: #relnotes_v20-fsa}

Dans cette édition, le service Fortinet on {{site.data.keyword.cloud_notm}} a été renommé FortiGate Security Appliance (FSA) on {{site.data.keyword.cloud_notm}}. Les deux dispositifs FortiGate Security Appliance (FSA) du service sont configurés de manière à être sécurisés par défaut lorsqu'ils sont déployés dans votre instance.
* Si vous déployez une paire de dispositifs FSA dans le cadre d'une nouvelle instance Cloud Foundation ou vCenter Server, ces dispositifs sont configurés de manière à n'autoriser que les communications sortantes requises depuis votre instance vers le réseau public et à refuser toutes les autres communications.
* Si vous déployez une paire de dispositifs FSA dans le cadre d'une instance Cloud Foundation ou vCenter Server existante, ces dispositifs sont configurés avec une règle explicite de manière à autoriser toutes les communications de gestion sortantes requises depuis votre instance vers le réseau public, et les dispositifs FSA sont également configurés avec une règle permettant toutes les autres communications afin de garantir que le trafic d'application existant n'est pas interrompu.

Dans tous les cas, vous devez gérer la configuration des dispositifs FSA avec la plus grande attention de manière à n'autoriser que les communications nécessaires et à refuser toutes les autres communications.

## Cohérence du format du nom de domaine complet
{: #relnotes_v20-fqdn}

Le nom de domaine complet est désormais représenté de manière cohérente pour toutes les instances. Lorsque vous passez une commande, vous pouvez entrer vos propres préfixe de sous-domaine et préfixe de nom d'hôte pour faire en sorte que la convention sur le format de nom de domaine complet (industrie) soit appliquée. Par exemple, `préfixe-nom-hôte<n>.préfixe-sousdomaine.nom-domaine`.

Pour plus d'informations, voir les rubriques suivantes :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Estimation de la charge de travail et du stockage en cours de commande d'une instance
{: #relnotes_v20-estimates-order}

* Lors d'une commande d'une instance VMware vSphere on {{site.data.keyword.cloud_notm}}, une estimation du nombre de machines virtuelles qui peuvent s'exécuter sur l'instance commandée vous est fournie.
* Lors d'une commande d'une instance Cloud Foundation et vCenter Server, une estimation de la capacité de stockage utilisable pour l'instance commandée vous est fournie.

Pour plus d'informations, voir les rubriques suivantes :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Mises à jour des instances VMware Cloud Foundation
{: #relnotes_v20-vcf}

L'édition actuelle applique les améliorations et mises à jour de composant suivantes au nouveaux déploiements :

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* Gestionnaire VMware SDDC 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Patch Release ESXi650-201710401-BG. Mises à jour esx-base, esx-tboot, vsan et vsanhealth VIBs (2151061). Pour plus d'informations sur les modules de correction, voir [Modules de correction de sécurité du système d'exploitation de VMware vCenter Server Appliance Photon](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}.

Les instances existantes (à partir des éditions V1.9 et de niveau antérieur) ne peuvent pas être mises à niveau vers les versions de composant figurant dans cette liste.
{:note}

### Prise en charge des clusters pour les instances Cloud Foundation
{: #relnotes_v20-vcf-cluster}

Vous pouvez désormais utiliser des clusters pour gérer des serveurs ESXi dans les instances Cloud Foundation déployées en version 2.0 et éditions ultérieures de manière à bénéficier d'une meilleure gestion des ressources et de la haute disponibilité. Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés en **SDDC-Cluster**.

Vous pouvez afficher les détails du cluster et ajouter jusqu'à cinq clusters à une instance à partir de l'onglet **Infrastructure** de la page des détails de l'instance. Lorsque vous augmentez ou réduisez la capacité d'une instance, vous pouvez sélectionner le cluster dans lequel ajouter ou retirer des serveurs ESXi.

### Prise en charge du stockage vSAN personnalisé pour des instances Cloud Foundation
{: #relnotes_v20-custom-vsan-vcf}

Vous pouvez désormais personnaliser la configuration du stockage vSAN en sélectionnant le nombre d'unités de stockage vSAN et leur taille dans votre commande d'instance.

### Choix de l'édition de licence VMware vSAN pour des instances Cloud Foundation : Advanced ou Enterprise
{: #relnotes_v20-vsan-license}

Vous pouvez désormais sélectionner l'édition de licence vSAN qui vous convient lors de la commande d'une instance Cloud Foundation. Vous pouvez acheter la licence dans le cadre de votre commande ou fournir votre propre licence (BYOL, Bring Your Own License).

### Nouvelles configurations normalisées de serveur IBM bare metal pour les instances Cloud Foundation
{: #relnotes_v20-vcf-bare-metal}

Les paramètres de configuration de serveur bare metal suivants sont désormais disponibles :
* Petite (Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz/128 Go de RAM/12 disques)
* Grande (Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz/512 Go de RAM/12 disques)

Le châssis dispose de suffisamment d'espace pour 12 disques. Tous les emplacements ne sont pas remplis. La **Petite** configuration fournit deux unités Micron 5100 MAX de 1,9 To et la **Grande** configuration fournit quatre unités Micron 5100 PRO de 3,8 To.
{:note}

## Mises à jour des instances VMware vCenter Server
{: #relnotes_v20-vcs}

L'édition actuelle applique les mises à jour de composant suivantes au nouveaux déploiements :

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

Les commandes personnalisées de vCenter Server avec ou sans le composant VMware vSAN incluent toujours un serveur de châssis de 12 disques. Ce serveur laisse apparaître un coût légèrement supérieur pour les serveurs {{site.data.keyword.baremetal_short}} de la commande sans vSAN dans le PDF du coût estimé.
{:note}

Pour plus d'informations sur les composants, voir [Présentation de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview).

### Prise en charge de configuration multisite pour des instances vCenter Server
{: #relnotes_v20-vcs-multisite}

Vous pouvez désormais déployer une instance vCenter Server en plus des instances secondaires associées à l'instance principale. Le modèle de configuration multisite utilise un concentrateur et une topologie en étoile (hub and spoke) avec un site principal et un maximum de sept sites secondaires.

Pour plus d'informations, voir [Configuration multisite pour des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite).

### Prise en charge du stockage vSAN personnalisé pour des instances vCenter Server
{: #relnotes_v20-custom-vsan-vcs}

Le stockage vSAN est désormais disponible sur les instances vCenter Server pour les instances principales comme secondaires. Il n'est disponible que lorsque vous sélectionnez une configuration personnalisée par l'utilisateur. Vous pouvez désormais sélectionner l'édition de licence vSAN (Advanced ou Enterprise) qui vous convient lors de la commande d'une instance vCenter Server. Vous pouvez acheter la licence dans le cadre de votre commande ou fournir votre propre licence (BYOL, Bring Your Own License).

Pour plus d'informations, voir [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Apport de votre propre licence (BYOL, Bring Your Own License) pour les instances VMware vCenter Server
{: #relnotes_v20-byol}

BYOL est désormais disponible pour les instances vCenter Server. utilisez une ou plusieurs de vos propres licences vCenter Server, vSphere, vSAN et NSX VMware lorsque vous commandez des instances vCenter Server.

Pour plus d'informations, voir les rubriques suivantes :
* [Commande d'instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Mises à jour pour VMware vSphere on IBM Cloud
{: #relnotes_v20-vss}

### Nouveaux types de disque pour les serveurs bare metal
{: #relnotes_v20-disk-type}

Pour le composant VMware vSAN, les types de disque suivants sont désormais disponibles pour les serveurs {{site.data.keyword.baremetal_short}} :
* 960 Go SSD SED
* 1,9 To SSD SED
* 3,8 To SSD SED

**Remarques** :
* Les unités SSD SED de 3,8 To sont prises en charge une fois qu'elles sont officiellement disponibles dans un {{site.data.keyword.CloudDataCent_notm}}.
* Les commandes avec ou sans le composant VMware vSAN incluent toujours un serveur de châssis de 12 disques. Ce serveur laisse apparaître un coût légèrement supérieur pour les serveurs {{site.data.keyword.baremetal_short}} de la commande sans vSAN dans le PDF du coût estimé.

Pour plus d'informations, voir [Commande de nouveaux clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Mises à jour pour NetApp ONTAP Select on IBM Cloud
{: #relnotes_v20-netapp}

### Nouvelles options de serveur bare metal
{: #relnotes_v20-netapp-bare-metal}

Les options de configuration de serveur bare metal suivantes sont désormais disponibles :
* **Hautes performances (Moyenne)** – Licence Premium/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/128 Go de RAM/capacité de 22 unités SSD de 1,9 To par noeud/capacité effective d'un cluster de 4 noeuds – 59 To
* **Hautes performances (Grande)** – Licence Premium/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/128 Go de RAM/capacité de 22 unités SSD de 3,8 To par noeud/capacité effective d'un cluster de 4 noeuds – 118 To
* **Haute capacité** – Licence Standard/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/64 Go de RAM/capacité de dix unités SATA de 4 To par noeud/capacité effective d'un cluster de 4 noeuds – 60 To

Les unités SSD de 3,8 To sont prises en charge une fois qu'elles sont officiellement disponibles dans un {{site.data.keyword.CloudDataCent_notm}}.
{:note}

Pour plus d'informations, voir les rubriques suivantes :
* [Présentation de NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [Commande d'instances NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Documentation nouvelle et mise à jour
{: #relnotes_v20-new-docs}

Les utilisateurs de VMware Cloud Foundation peuvent utiliser les instructions détaillées et la plateforme NSX de VMware sur {{site.data.keyword.cloud_notm}} pour permettre à des machines virtuelles de communiquer entre elles et avec internet. Pour plus d'informations, voir[Configuration de NSX pour des machines virtuelles de charge de travail sur VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Améliorations et mises à jour apportées à l'interface utilisateur
{: #relnotes_v20-ui}

* Le nombre maximum de serveurs ESXi pouvant être ajoutés à un cluster a été mis à jour pour atteindre 32 serveurs. Le nombre maximum de clusters est toujours de cinq.
* Sur la page **Ressources**, la colonne **Serveurs ESXi** des tableaux récapitulatifs des instances a été remplacée par la colonne **Version**, qui indique la version d'édition dans laquelle les instances ont été déployées ou mises à jour.
* La version du gestionnaire SDDC pour les instances Cloud Foundation est désormais disponible sur la page des détails de l'instance.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

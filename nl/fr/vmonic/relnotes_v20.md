---

copyright:

  years:  2016, 2018

lastupdated: "2017-11-20"

---

# Notes sur l'édition pour la version 2.0

Cette édition inclut de nouvelles fonctionnalités, des mises à jour de composant, des améliorations d'utilisation et des corrections d'erreur. Pour la liste des erreurs rectifiées dans les différentes éditions, les problèmes connus concernant le produit et des conseils supplémentaires pour l'utilisation d'{{site.data.keyword.vmwaresolutions_full}}, voir [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud

Le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} est désormais disponible pour les instances VMware Cloud Foundation instances et VMware vCenter Server en version 2.0 et ultérieure. Ce service déploie dans votre environnement une paire à haute disponibilité de dispositifs FortiGate Virtual Appliance qui vous permettent de réduire les risques en implémentant des contrôles de sécurité critiques au sein de votre infrastructure virtuelle.

Vous pouvez commander des instances avec le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} déjà inclus ou vous pouvez ajouter ultérieurement ce service à vos instances existantes à partir de l'onglet **Services** de la page des détails d'instance. En fonction de vos besoins, sélectionnez pour ce service l'une des trois tailles de déploiement et les options d'octroi de licence. Une fois le service correctement installé, vous pouvez gérer et configurer des règles de pare-feu pour les dispositifs FortiGate Virtual Appliance depuis la console FortiGate.

Pour plus d'informations, voir :
* [Composants et remarques pour FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/fortinetvm_considerations.html)
* [Gestion de FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](../services/managingfortinetvm.html)

## Installation de plusieurs services pour F5 on IBM Cloud et le service FortiGate Virtual Appliance on IBM Cloud

Vous pouvez désormais installer plusieurs instances du service F5 on {{site.data.keyword.cloud_notm}} et le service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} pour une instance Cloud Foundation ou vCenter Server. Lorsque vous sélectionnez le service F5 ou le service FortiGate lors d'une commande d'instance, vous devez indiquer un nom pour l'instance de service de manière à la différentier des instances de service supplémentaires que vous installerez ultérieurement.

Une fois le déploiement de l'instance achevé, vous pouvez ajouter d'autres instances du service F5 ou FortiGate en installant le service à partir de l'onglet **Ajouter des services** de la page des détails de l'instance. Vous ne pouvez ajouter qu'une seule instance de service à la fois et répéter le processus pour toutes les instances que vous voulez ajouter pour un service.

Pour plus d'informations, voir :
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](../vcenter/vc_addingremovingservices.html)

## Mises à jour pour le service FortiGate Security Appliance on IBM Cloud

Dans cette édition, le service Fortinet on {{site.data.keyword.cloud_notm}} a été renommé FortiGate Security Appliance (FSA) on {{site.data.keyword.cloud_notm}} et les deux dispositifs FortiGate Security Appliance du service sont configurés de manière à être sécurisés par défaut lorsqu'ils sont déployés dans votre instance :
* Si vous déployez une paire de dispositifs FSA  dans le cadre d'une nouvelle instance Cloud Foundation ou vCenter Server, ces dispositifs sont configurés de manière à n'autoriser que les communications sortantes requises depuis votre instance vers le réseau public et à refuser toutes les autres communications.
* Si vous déployez une paire de dispositifs FSA dans le cadre d'une instance Cloud Foundation ou vCenter Server existante, ces dispositifs sont configurés avec une règle explicite de manière à autoriser toutes les communications de gestion sortantes requises depuis votre instance vers le réseau public, et les dispositifs FSA sont également configurés avec une règle supplémentaire permettant toutes les autres communications afin de garantir que le trafic d'application existant n'est pas interrompu.

Dans tous les cas, vous devez gérer la configuration des dispositifs FSA avec la plus grande attention de manière à n'autoriser que les communications nécessaires et à refuser toutes les autres communications.

## Cohérence du format du nom de domaine complet

Le nom de domaine complet est désormais représenté de manière cohérente pour toutes les instances. Lorsque vous passez une commande, vous pouvez entrer vos propres préfixe de sous-domaine et préfixe de nom d'hôte. Ceci garantit que la convention de l'industrie en matière de format de nom de domaine complet est respectée, soit : `préfixe-nom-hôte<n>.préfixe-sousdomaine.nom-domaine`.

Pour plus d'informations, voir :
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Commande de nouveaux clusters vSphere](../vsphere/vs_orderinginstances.html)

## Estimation de la charge de travail et du stockage en cours de commande d'une instance

* Lors d'une commande d'une instance VMware vSphere on {{site.data.keyword.cloud_notm}}, une estimation du nombre de machines virtuelles qui peuvent s'exécuter sur l'instance commandée vous est fournie.
* Lors d'une commande d'une instance Cloud Foundation et vCenter Server, une estimation de la capacité de stockage utilisable pour l'instance commandée vous est fournie.

Pour plus d'informations, voir :
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Commande de nouveaux clusters vSphere](../vsphere/vs_orderinginstances.html)

## Mises à jour des instances VMware Cloud Foundation

L'édition actuelle applique les améliorations et mises à jour de composant suivantes au nouveaux déploiements :

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* Gestionnaire VMware SDDC 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Patch Release ESXi650-201710401-BG : mises à jour esx-base, esx-tboot, vsan et vsanhealth VIBs (2151061). Pour des détails concernant les correctifs, voir [Correctifs de sécurité du système d'exploitation de VMware vCenter Server Appliance Photon](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}.

**Remarque** : les instances existantes (à partir des éditions V1.9 et de niveau antérieur) ne peuvent pas être mises à niveau vers les versions de composant figurant dans cette liste.

Pour plus d'informations sur les composants, voir [Présentation de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

### Prise en charge des clusters pour les instances Cloud Foundation

Vous pouvez désormais utiliser des clusters pour gérer des serveurs ESXi dans les instances Cloud Foundation déployées en version 2.0 et éditions ultérieures de manière à bénéficier d'une meilleure gestion des ressources et de la haute disponibilité. Les serveurs ESXi que vous avez configurés lors de la commande d'une instance sont, par défaut, regroupés en **SDDC-Cluster**.

Vous pouvez afficher les détails du cluster et ajouter jusqu'à cinq clusters à une instance à partir de l'onglet **Infrastructure** de la page des détails de l'instance. Lorsque vous augmentez ou réduisez la capacité d'une instance, vous pouvez sélectionner le cluster dans lequel ajouter ou retirer des serveurs ESXi. Pour plus d'informations, voir [Ajout et affichage des clusters des instances Cloud Foundation](../sddc/sd_addingviewingclusters.html).

### Prise en charge du stockage vSAN personnalisé pour des instances Cloud Foundation

Vous pouvez désormais personnaliser la configuration du stockage vSAN en sélectionnant le nombre d'unités de stockage vSAN et leur taille dans votre commande d'instance.

Pour plus d'informations, voir :
* [Présentation de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)

### Choix de l'édition de licence VMware vSAN pour des instances Cloud Foundation : Advanced ou Enterprise

Vous pouvez désormais sélectionner l'édition de licence vSAN qui vous convient lors de la commande d'une instance Cloud Foundation. Vous pouvez acheter la licence dans le cadre de votre commande ou fournir votre propre licence (BYOL, Bring Your Own License). Pour plus d'informations, voir [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html).

### Nouvelles configurations normalisées de serveur IBM bare metal pour les instances Cloud Foundation

Les paramètres de configuration de serveur bare metal suivants sont désormais disponibles :
* Petite (Dual Intel Xeon E5-2650 v4/24 coeurs au total, 2,2 GHz/128 Go de RAM/12 disques)
* Grande (Dual Intel Xeon E5-2690 v4/28 coeurs au total, 2,6 GHz/512 Go de RAM/12 disques)

**Remarque** : le châssis dispose d'espace pour 12 disques, mais tous les emplacements ne sont pas remplis. La **Petite** configuration fournit deux unités Micron 5100 MAX de 1,9 To et la **Grande** configuration fournit quatre unités Micron 5100 PRO de 3,8 To.

Pour plus d'informations, voir :
* [Présentation de Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)

## Mises à jour des instances VMware vCenter Server

L'édition actuelle applique les mises à jour de composant suivantes au nouveaux déploiements :

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

**Remarque :** les commandes personnalisées de vCenter Server avec ou sans le composant VMware vSAN incluent toujours un châssis de 12 disques qui laisse apparaître un coût légèrement supérieur pour les serveurs {{site.data.keyword.baremetal_short}} de la commande sans vSAN dans le PDF du coût estimé.

Pour plus d'informations sur les composants, voir [Présentation de vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Prise en charge de configuration multisite pour des instances vCenter Server

Vous pouvez désormais déployer une instance vCenter Server en plus des instances secondaires associées à l'instance principale. Le modèle de configuration multisite utilise un concentrateur et une topologie en étoile (hub and spoke) avec un site principal et un maximum de 7 sites secondaires.

Pour plus d'informations, voir [Configuration multisite pour des instances vCenter Server](../vcenter/vc_multisite.html).

### Prise en charge du stockage vSAN personnalisé pour des instances vCenter Server

Le stockage vSAN est désormais disponible sur les instances vCenter Server pour les instances principales comme secondaires. Il n'est disponible que si vous sélectionnez une configuration personnalisée par l'utilisateur. Vous pouvez désormais sélectionner l'édition de licence vSAN (Advanced ou Enterprise) qui vous convient lors de la commande d'une instance vCenter Server. Vous pouvez acheter la licence dans le cadre de votre commande ou fournir votre propre licence (BYOL, Bring Your Own License).

Pour plus d'informations, voir [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html).

### Apport de votre propre licence (BYOL, Bring Your Own License) pour les instances VMware vCenter Server

BYOL est désormais disponible pour les instances vCenter Server. BYOL vous permet d'utiliser une ou plusieurs de vos propres licences vCenter Server, vSphere, vSAN et NSX VMware lors de la commande d'instances vCenter Server.

Pour plus d'informations, voir :
* [Commande d'instances Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Commande d'instances vCenter Server](../vcenter/vc_orderinginstance.html)
* [Commande de nouveaux clusters vSphere](../vsphere/vs_orderinginstances.html)

## Mises à jour pour VMware vSphere on IBM Cloud

### Nouveaux types de disque pour les serveurs bare metal

Pour le composant VMware vSAN, les types de disque suivants sont désormais disponibles pour les serveurs {{site.data.keyword.baremetal_short}} :
* 960 Go SSD SED
* 1,9 To SSD SED
* 3,8 To SSD SED

**Remarques :**
* Les unités SSD SED de 3,8 To seront prises en charge une fois officiellement disponibles dans un {{site.data.keyword.CloudDataCent_notm}}.
* Les commandes avec ou sans le composant VMware vSAN incluent toujours un châssis de 12 disques qui laisse apparaître un coût légèrement supérieur pour les serveurs {{site.data.keyword.baremetal_short}} de la commande sans vSAN dans le PDF du coût estimé.

Pour plus d'informations, voir [Commande de nouveaux clusters vSphere](../vsphere/vs_orderinginstances.html).

## Mises à jour pour NetApp ONTAP Select on IBM Cloud

### Nouvelles options de serveur bare metal

Les options de configuration de serveur bare metal suivantes sont désormais disponibles :
* **Hautes performances (Moyenne)** – Licence Premium/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/128 Go de RAM/capacité de vingt-deux unités SSD de 1,9 To par noeud/capacité effective d'un cluster de 4 noeuds – 59 To
* **Hautes performances (Grande)** – Licence Premium/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/128 Go de RAM/capacité de vingt-deux unités SSD de 3,8 To par noeud/capacité effective d'un cluster de 4 noeuds – 118 To
* **Haute capacité** – Licence Standard/Dual Intel Xeon E5-2650 v4 (24 coeurs au total, 2,2 GHz)/64 Go de RAM/capacité de dix unités SATA de 4 To par noeud/capacité effective d'un cluster de 4 noeuds – 60 To

**Remarque :** les unités SSD de 3,8 To seront prises en charge une fois officiellement disponibles dans un {{site.data.keyword.CloudDataCent_notm}}. 

Pour plus d'informations, voir :
* [Présentation de NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Commande d'instances NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Documentation nouvelle et mise à jour

Les utilisateurs de VMware Cloud Foundation peuvent utiliser les instructions détaillées et la plateforme NSX de VMware sur {{site.data.keyword.cloud_notm}} pour permettre à des machines virtuelles de communiquer entre elles sur Internet. Pour plus d'informations, voir[Configuration de NSX pour des machines virtuelles de charge de travail sur VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Améliorations et mises à jour apportées à l'interface utilisateur

* Le nombre maximum de serveurs ESXi pouvant être ajoutés à un cluster a été mis à jour pour atteindre 32 serveurs. Le nombre maximum de clusters est toujours de cinq.
* Sur la page **Instances déployées**, la colonne **Serveurs ESXi** des tableaux récapitulatifs des instances a été remplacée par la colonne **Version**, qui indique la version d'édition dans laquelle les instances ont été déployées ou mises à jour.
* La version du gestionnaire SDDC pour les instances Cloud Foundation est désormais disponible sur la page des détails de l'instance.
* Diverses améliorations ont été apportées au niveau des messages d'erreur et des infobulles pour vous aider à sélectionner le paramétrage approprié sur l'interface utilisateur.

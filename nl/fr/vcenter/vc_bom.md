---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Nomenclature de vCenter Server
{: #vc_bom}

Passez en revue les informations de nomenclature des instances VMware vCenter Server.

## Nomenclature des réseaux locaux virtuels (VLAN) pour les instances vCenter Server
{: #vc_bom-vlans}

Le tableau suivant fournit des informations de nomenclature détaillées concernant les réseaux locaux virtuels de vCenter Server.

Tableau 1. Nomenclature des réseaux locaux virtuels des instances vCenter Server

| VLAN       | Type       | Détails       |
|:---------- |:---------- |:------------- |
| VLAN1     | Public, Principal | Affectés à des serveurs ESXi physiques pour accès au réseau public. Inutilisés après le déploiement initial. Disponibles pour l'accès Internet. |
| VLAN2     | Privé A, Principal | Affectés par {{site.data.keyword.cloud}} à des serveurs ESXi physiques. Utilisés par l'interface de gestion pour le trafic de gestion VMware vSphere.<br><br>Affectés à des machines virtuelles qui fonctionnent en tant que composants de gestion.<br><br>Affectés à VMware NSX VTEP (point d'extrémité du tunnel VXLAN) |
| VLAN3     | Privé B, Portable | Affectés à VMware vSAN, si utilisés.<br><br>Affectés à VMware NFS, si utilisés.<br><br>Affectés à VMware vSphere vMotion. |

## Nomenclature logicielle pour les instances vCenter Server
{: #vc_bom-software}

Le tableau suivant fournit des informations de nomenclature détaillées concernant les composants logiciels vCenter Server.

Tableau 2. Nomenclature des composants logiciels des instances vCenter Server

| Fabricant  | Composant                      | Version    |
|:------------- |:------------------------------ |:------------- |
| VMware       | vSphere ESXi                    | 6.7 Update 1 (build 6.7.0-11675023) ou <br/>6.5 Update 2 (build 6.5.0-11925212) |
| VMware       | vCenter Server Appliance        | 6.7 Update 1 (build 6.7.0-10244745) ou <br/>6.5 Update 2d (build 6.5.0-10964411) |
| VMware       | Contrôleur PSC (Platform Services Controller)    | 6.7 Update 1 (build 6.7.0-10244745) ou <br/>6.5 Update 2d (build 6.5.0-10964411) |
| VMware       | vSAN                            | 6.7 Update 1 ou <br/>6.6.1       |
| VMware       | NSX for vSphere                 | 6.4.4 (build 11197766)    |
| Microsoft    | Windows Server édition Standard | 2012R2       |

VMware vSAN est un composant optionnel.
{:note}

## Paramètres de configuration avancée pour les serveurs ESXi
{: #vc_bom-esxi-server-advance-config}

Consultez le tableau suivant pour obtenir une présentation des paramètres de configuration avancée appliqués aux serveurs ESXi. Ces paramètres varient selon que l'instance vCenter Server est déployée dans la version V2.2 ou dans une version ultérieure, ou mise à niveau vers la version 2.2 ou une version ultérieure à partir de la version 2.1 ou d'une version antérieure.

Les paramètres s'appliquent aux nouvelles instances et aux nouveaux clusters des instances de version 2.2 ou ultérieure. Ils ne s'appliquent pas aux nouveaux clusters d'instances existantes de la version 2.1 ou d'une version antérieure ou d'instances existantes qui sont mises au niveau vers la version 2.2 ou une version ultérieure.

Tableau 3. Paramètres de configuration avancée des serveurs ESXi pour les instances et clusters vCenter Server

| Paramètre de configuration | Nouveau déploiement en version 2.2 ou ultérieure  | Mise à niveau depuis la version 2.1 ou antérieure |
|:------------- |:------------- |:------------- |
| Maximum of Volumes | **MaxVolumes** = 256 | **/NFS/MaxVolumes** et **/NFS41/MaxVolumes** = 256 |
| Heartbeat Maximum Failures | **HeartbeatMaxFailures** = 10 | Non défini |
| Heartbeat Frequency | **HeartbeatFrequency** = 12 | Non défini |
| Heartbeat Timeout | **HeartbeatTimeout** = 5 | Non défini |
| Maximum Queue Depth | **MaxQueueDepth** = 64 | Non défini |
| Queue Full Sample Size | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Queue Full Threshold | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |
| TCP/IP Heap Size | **TcpipHeapSize** = 32 | Non défini |
| TCP/IP Heap Maximum | **TcpipHeapMax** = 1536 | Non défini |

**Remarques :**
* Le paramètre **MaxVolumes** est obligatoire pour le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} car ce service risque d'utiliser plus que le nombre de montages NFS par défaut sur le serveur ESXi.
* La valeur **Non défini** d'un paramètre de configuration indique que le nouveau paramètre n'est pas automatiquement appliqué car il nécessite un réamorçage des serveurs ESXi, ce qui risque de provoquer une interruption.

  Il est recommandé de remplacer les paramètres de configuration **Non défini** par les nouvelles valeurs afin de garantir la cohérence entre toutes les instances et de permettre la prise en charge appropriée d'une extension de stockage. IBM prévoit de n'effectuer ses tests qu'avec ces nouvelles valeurs pour toutes les {{site.data.keyword.vmwaresolutions_short}} de version 2.2 et éditions ultérieures.

  Pour plus d'informations, voir [Augmentation de la valeur par défaut qui définit le nombre maximum de montages NFS sur un hôte ESXi](https://kb.vmware.com/s/article/2239).

## Paramètres de configuration de NSX et des groupes de ports
{: #vc_bom-nsx-port-group-config}

Consultez le tableau suivant pour une présentation des paramètres de configuration de VMware NSX et des groupes de ports pour des instances vCenter Server, et pour les différences entre les éditions.

Les paramètres s'appliquent aux nouvelles instances et aux nouveaux clusters des instances de version 2.2 ou ultérieure. Ils ne s'appliquent pas aux nouveaux clusters d'instances existantes de la version 2.1 ou d'une version antérieure ou d'instances existantes qui sont mises au niveau vers la version 2.2 ou une version ultérieure.

Tableau 4. Paramètres de configuration de NSX et des groupes de ports pour des instances vCenter Server

| Paramètre de configuration | Version 2.1 ou antérieure  | Version 2.2 ou ultérieure |   
|:------------- |:------------- |:------------- |
| NSX VXLAN cluster teaming policy | Basculement | Equilibrage de charge - SRCID |
| NSX VXLAN cluster VTEP | 1 | 2 |
| Segment ID pool for primary instance | 6000 à 8000 | 6000 à 7999 |  
| Segment ID pool for subsequent secondary instance or instances | 6000 à 8000 | Précédente plage de fin de la configuration multisite + 1 à la précédente plage de fin de la configuration multisite + 2000 |  
| Port group SDDC-DPortGroup-VSAN (si applicable) | **Active uplinks** défini sur **uplink1** et **Standby uplinks** défini sur **uplink2** | **Active uplinks** défini sur **uplink2** et **Standby uplinks** défini sur **uplink1** |  
| Port group SDDC-DPortGroup-Mgmt | **Port binding** défini sur **Ephemeral - no binding** et **Load balancing** défini sur **Route based on originating virtual port** | **Port binding** défini sur **Static binding** et **Load balancing** défini sur **Route based on physical NIC load** |  
| Port group SDDC-DPortGroup-External | **Port binding** défini sur **Ephemeral - no binding** | **Port binding** défini sur **Static binding** |

## Paramètres de configuration de MTU réseau
{: #vc_bom-network-mtu-config}

Le cluster vSphere utilise deux commutateurs VdS (vSphere Distributed Switches) vSphere, un pour la connectivité de réseau public et l'autre pour la connectivité de réseau privé.

Les connexions de réseau privé sont configurées pour utiliser 9000 comme taille MTU de trame Jumbo, ce qui permet d'améliorer les performances des transferts d'importantes quantités de données, comme le stockage et VMware vMotion. Il s'agit de la taille MTU maximale autorisée au sein de VMware et par {{site.data.keyword.cloud_notm}}.

A partir de la version 2.1, les connexions de réseau public utilisent 1500 comme taille MTU Ethernet standard. La valeur 1500 doit être conservée ; tout changement peut provoquer une fragmentation des paquets sur Internet.

Consultez le tableau suivant pour obtenir une présentation des paramètres de configuration de MTU réseau appliqués au commutateur Distributed Virtual Switch (DVS) public et privé selon que l'instance vCenter Server est déployée en V2.1 ou dans une édition ultérieure.

Tableau 5. Paramètres de configuration de MTU pour les instances et clusters vCenter Server en fonction de la version d'instance

| vDS | V2.1 ou édition ultérieure  | V2.0 ou édition antérieure (ou mise à niveau depuis V2.0 ou une édition antérieure) |
|:-------------- |:-------------- |:------------- |
| Commutateur public  | 1500 (valeur par défaut) | 9000 (trames Jumbo) |
| Commutateur privé | 9000 (trames Jumbo) | 9000 (trames Jumbo) |

Les paramètres s'appliquent aux nouvelles instances et aux nouveaux clusters des instances déployées en V2.1 ou dans une édition ultérieure. Les paramètres s'appliquent également aux nouveaux clusters présents dans des {{site.data.keyword.CloudDataCents_notm}} à partir d'instances qui ont été mises à niveau vers V2.1 ou une édition ultérieure.

Ils ne s'appliquent pas aux nouveaux clusters présents dans le même {{site.data.keyword.CloudDataCent_notm}}, pour des instances existantes depuis V2.0 ou une édition antérieure ou des instances existantes mises au niveau vers V2.1 ou une édition ultérieure.

Pour les instances déployées en V2.0 ou dans une édition antérieure, nous vous conseillons de mettre à niveau le paramètre de MTU de commutateur public vers 1500.

### Mise à jour du paramètre de MTU de commutateur public
{: #vc_bom-procedure-update-public-switch-mtu-setting}

Afin de mettre à jour le paramètre de MTU pour le commutateur public, procédez comme suit dans le client Web VMware vSphere :
1. Cliquez avec le bouton droit de la souris sur le commutateur vDS, puis cliquez sur **Editer les paramètres**.
2. Sur l'onglet **Propriétés**, sélectionnez l'option **Avancé**.
3. Assurez-vous que la valeur maximale indiquée pour **MTU** est 1500.

   Lorsque la taille de MTU dans un commutateur vDS est modifiée, les liaisons montantes connectées (NIC physiques) sont désactivées, puis réactivées. Il en résulte une brève indisponibilité pour les machines virtuelles qui utilisent la liaison montante. Par conséquent, il est recommandé de planifier la mise à jour du paramètre de MTU durant le temps d'indisponibilité planifié.
   {:note}

## Liens connexes
{: #vc_bom-related}

* [Numéros et versions de génération de VMware ESXi et ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Numéros et versions de génération de VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Activation de trames Jumbo sur des commutateurs distribués virtuels](https://kb.vmware.com/s/article/1038827)
* [{{site.data.keyword.vmwaresolutions_short}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:new_window}
* [Présentation de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Planification des instances vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)

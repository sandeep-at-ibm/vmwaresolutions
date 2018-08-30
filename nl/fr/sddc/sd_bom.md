---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Nomenclature de Cloud Foundation

Passez en revue les informations liées à la nomenclature des instances VMware Cloud Foundation.

## Nomenclature des réseaux locaux virtuels des instances Cloud Foundation

Le tableau suivant fournit des informations de nomenclature détaillées concernant les réseaux locaux virtuels de Cloud Foundation.

Tableau 1. Nomenclature des réseaux locaux virtuels des instances Cloud Foundation

| VLAN      | Type      | Détails      |
|:----------|:----------|:-------------|
| VLAN1     | Public, Principal | Affectés à des serveurs ESXi physiques pour accès au réseau public. Inutilisés après le déploiement initial. Disponibles pour l'accès Internet. |
| VLAN2     | Privé A, Principal | Affectés par {{site.data.keyword.cloud}} à des serveurs ESXi physiques. Utilisés par l'interface de gestion pour le trafic de gestion VMware vSphere.<br><br>Affectés à des machines virtuelles qui fonctionnent en tant que composants de gestion.<br><br>Affectés à VMware NSX VTEP (point d'extrémité du tunnel VXLAN) |
| VLAN3     | Privé B, Portable | Affectés à VMware vSAN, si utilisés.<br><br>Affectés à VMware NFS, si utilisés.<br><br>Affectés à VMware vSphere vMotion. |

## Nomenclature logicielle des instances Cloud Foundation

Le tableau suivant fournit des informations de nomenclature détaillées concernant les composants logiciels de Cloud Foundation.

Tableau 2. Nomenclature des composants logiciels des instances Cloud Foundation

| Fabricant | Composant                                | Version      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 U1g (ESXi 6.5u1 avec le niveau de module de correction ESXi650-201803001 appliqué) |
| VMware       | vCenter Server Appliance                 | 6.5 Update 1g |
| VMware       | Contrôleur PSC (Platform Services Controller)             | 6.5 Update 1g |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.3.5        |
| VMware       | Gestionnaire SDDC                             | 2.4          |
| IBM          | CloudDriver                              | 2.5          |
| Microsoft    | Windows Server édition Standard (64 bits) | 2012R2       |

## Paramètres de configuration avancée pour les serveurs ESXi

Consultez le tableau suivant pour une présentation des paramètres de configuration avancée applicables aux serveurs ESXi selon que l'instance Cloud Server est déployée dans la version 2.2 ou ultérieure ou mise au niveau vers la version 2.2 ou ultérieure à partir d'une version 2.1 ou d'une édition antérieure.

Tableau 3. Paramètres de configuration avancée des serveurs ESXi pour les instances et clusters Cloud Foundation

| Paramètre de configuration | Nouveau déploiement en version 2.2 ou ultérieure  | Mise à niveau depuis la version 2.1 ou antérieure |   
|:------------- |:------------- |:------------- |
| TCP/IP Heap Size | **TcpipHeapSize** = 32 | Non défini |
| TCP/IP Heap Maximum | **TcpipHeapMax** = 1536 | Non défini |  
| Maximum of Volumes | **MaxVolumes** = 256 | **/NFS/MaxVolumes** et **/NFS41/MaxVolumes** = 256 |  
| Heartbeat Maximum Failures | **HeartbeatMaxFailures** = 10 | Non défini |  
| Heartbeat Frequency | **HeartbeatFrequency** = 12 | Non défini |  
| Heartbeat Timeout | **HeartbeatTimeout** = 5 | Non défini |
| Maximum Queue Depth | **MaxQueueDepth** = 64 | Non défini |
| Queue Full Sample Size | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| Queue Full Threshold | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

**Remarques** :
* Le paramètre **MaxVolumes** est obligatoire pour le service IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} car ce service risque d'utiliser plus que le nombre de montages NFS par défaut sur le serveur ESXi.
* La valeur **Non défini** d'un paramètre de configuration indique que le nouveau paramètre n'est pas automatiquement appliqué car il nécessite un réamorçage des serveurs ESXi, ce qui risque de provoquer une interruption.

  Il est recommandé de remplacer les paramètres de configuration **Non défini** par les nouvelles valeurs afin de garantir la cohérence entre toutes les instances et de permettre la prise en charge appropriée d'une extension de stockage. IBM prévoit de n'effectuer ses tests qu'avec ces nouvelles valeurs pour toutes les {{site.data.keyword.vmwaresolutions_short}} de version 2.2 et éditions ultérieures.

  Pour plus d'informations, voir [Augmentation de la valeur par défaut qui définit le nombre maximum de montages NFS sur un hôte ESXi/ESX](https://kb.vmware.com/s/article/2239).

### Liens connexes

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [Feuille de données de protection de VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=C87A0EC07E7311E6BA51E79BE9476040)
* [Présentation de Cloud Foundation](sd_cloudfoundationoverview.html)
* [Planification des instances Cloud Foundation](sd_planning.html)

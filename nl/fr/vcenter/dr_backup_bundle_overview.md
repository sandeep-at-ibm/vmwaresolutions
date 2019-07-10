---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Présentation de Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview}

Single-node Trial for Data Protection and Disaster Recovery vous permet de tester le lecteur {{site.data.keyword.cloud}} pour migrer et récupérer les charges de travail VMware dans {{site.data.keyword.cloud_notm}}. En outre, Single-node Trial for Data Protection and Disaster Recovery inclut les services Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX sur {{site.data.keyword.cloud_notm}} et Zerto on {{site.data.keyword.cloud_notm}}.

Single-node Trial est une version d'évaluation de VMware vCenter Server sur {{site.data.keyword.cloud_notm}} qui fournit la plateforme VMware à service exclusif pouvant être gérée à l'aide des mêmes outils que dans les environnements sur site. Vous pouvez ainsi bénéficier de la vitesse et de l'échelle du cloud tout en conservant le même niveau de contrôle et de visibilité que dans un environnement local.

La version d'essai permet de migrer jusqu'à 20 charges de travail simples de développement ou de test à l'aide de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle. L'automatisation installe et configure VMware HCX dans {{site.data.keyword.cloud_notm}}, fournit une clé d'activation HCX locale, puis installe Veeam on {{site.data.keyword.cloud_notm}} et Zerto on {{site.data.keyword.cloud_notm}} en quelques heures. Vous pouvez sauvegarder et répliquer 20 machines virtuelles (VM) avec Veeam on {{site.data.keyword.cloud_notm}} et Zerto on {{site.data.keyword.cloud_notm}}. 

Single-node Trial for Data Protection and Disaster Recovery est destiné à une démonstration de faisabilité uniquement. N'exécutez pas de charges de travail de production dans cet environnement. Les fonctions de gestions, telles que l'ajout et le retrait d'hôtes et de clusters, la commande de services complémentaires supplémentaires et l'application de mises à jour ne sont pas prises en charge.
{:important}

Une fois que votre instance Single-node Trial est déployée, vous pouvez utiliser [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:new_window} à partir d'[IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:new_window} pour obtenir de l'assistance sur votre instance. En outre, [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:new_window} peut vous aider à accélérer la modernisation des applications grâce aux dernières recommandations pour le cloud natif.

Cette version d'essai peut être utilisée pendant un maximum de 90 jours. Les frais récurrents mensuels sont facturés en fonction de votre calendrier de facturation, et non du moment où l'instance est commandée. Si l'instance n'est pas annulée le dernier jour de votre cycle de facturation ou avant, vous êtes facturé pour le mois suivant. Il est fort probable qu'un essai de 90 jours entraîne quatre mois de frais, à moins que l'annulation ne soit effectuée avant le quatrième mois.
{:note}

Une fois qu'elle a expiré, vous pouvez supprimer cet environnement, puis mettre à disposition un nouvel environnement répondant à vos besoins en matière de capacité.

## Spécifications techniques relatives aux instances Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview-tech-specs}

Les composants suivants sont inclus dans votre instance Single-node Trial for Data Protection and Disaster Recovery.

La disponibilité et la tarification des configurations matérielles normalisées peuvent varier en fonction de l'{{site.data.keyword.CloudDataCent_notm}} sélectionné pour le déploiement.
{:note}

### Serveur bare metal
{: #dr_backup_bundle_overview-bare-metal}

Processeur Skylake Dual Intel Xeon Gold 5120 / 28 coeurs au total, 2,2 GHz avec 384 Go de RAM pour environ 20 VM 

#### Surallocations d'UC
{: #dr_backup_bundle_overview-cpu}

Surallocation d'UC 16:1 pour la gestion vCenter Server, HCX et 20 MV de charge de travail client

#### Surallocations de mémoire RAM
{: #dr_backup_bundle_overview-ram}

* Surallocation de mémoire RAM 1.22:1 pour un déploiement client de 20 MV de charge de travail avec 8 Go chacune
* 1:1 (pas de surallocation) pour un déploiement client de neuf MV de charge de travail avec 8 Go chacune

### Stockage NFS
{: #dr_backup_bundle_overview-nfs-storage}

* 2 To pour la gestion
* 1 To pour la charge de travail client (pour 20 MV client)

### Spécifications de mise en réseau relatives aux instances Single-node Trial for Data Protection and Disaster Recovery
{: #dr_backup_bundle_overview-networking-specs}

Les composants réseau suivants sont commandés :
*  Liaisons montantes réseau public et privé double de 10 Gbps
*  Trois VLAN (réseaux locaux virtuels) : un VLAN public et deux VLAN privés
*  Un VXLAN (réseau local virtuel extensible) avec routeur logique distribué (DLR) pour éventuelle communication d'est en ouest entre des charges de travail locales connectées à des réseaux de la couche 2 (L2). Le VXLAN est déployé en tant qu'exemple de topologie de routage, que vous pouvez modifier, à partir duquel vous pouvez construire et que vous pouvez supprimer. Vous pouvez également ajouter des zones de sécurité en connectant des VXLAN supplémentaires aux nouvelles interfaces logiques sur le DLR.
*  Deux passerelles VMware NSX Edge Services Gateway :
  * Une passerelle de gestion sécurisée VMware NSX Edge Services Gateway (ESG) pour le trafic de gestion HTTPS sortant, déployée par IBM dans le cadre de la topologie de réseau de gestion. Les machines virtuelles de gestion IBM utilisent cette passerelle ESG pour communiquer avec des composants de gestion IBM externes spécifiques liés à l'automatisation.

    Vous n'avez pas accès à cette passerelle ESG et vous ne pouvez pas l'utiliser. Si vous la modifiez, vous ne pourrez peut-être plus gérer l'instance Single-node Trial for Data Protection and Disaster Recovery à partir de la console {{site.data.keyword.vmwaresolutions_short}}. De plus, sachez que si vous utilisez un pare-feu ou désactivez les communications ESG vers des composants de gestion IBM externes, {{site.data.keyword.vmwaresolutions_short}} sera inutilisable.
    {:important}
  * Une passerelle VMware NSX Edge Services Gateway sécurisée gérée par le client pour le trafic de charge de travail HTTPS sortant et entrant, déployée par IBM en tant que modèle que vous pouvez modifier pour fournir un accès au réseau privé virtuel ou un accès public.

### Instance de serveur virtuel
{: #dr_backup_bundle_overview-vsi}

Les instances de serveur virtuel suivantes sont commandées :

* Une instance de serveur virtuel pour IBM CloudBuilder, annulée une fois le déploiement de l'instance terminé.
* Une instance de serveur virtuel Microsoft Windows Server pour Microsoft Active Directory (AD) est déployée et peut être interrogée. L'instance de serveur virtuel fonctionne en tant que serveur de noms de domaine pour l'instance où sont enregistrés les hôtes et les machines virtuelles.
* Une instance de serveur virtuel pour Zerto on {{site.data.keyword.cloud_notm}} - Zerto Virtual Manager.
* Une instance de serveur virtuel avec Veeam Backup and Replication 9.5 OS Add-on et Veeam Availability Suite 9.5.

### Licences fournies par IBM et frais
{: #dr_backup_bundle_overview-license-and-fee}

Les licences suivantes sont incluses dans votre commande d'instance Single-node Trial for Data Protection and Disaster Recovery.

* Licences vCenter Server avec Hybridity Bundle :
  * VMware vSphere Enterprise Plus 6.7u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

Les instances Single-node Trial for Data Protection and Disaster Recovery ne prennent pas en charge le mode BYOL (Bring Your Own License).
{:note}

## Spécifications techniques relatives à VMware HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery inclut HCS on {{site.data.keyword.cloud_notm}}. Les composants suivants sont commandés et inclus dans le service HCX on {{site.data.keyword.cloud_notm}} :

Les instances HCX locales incluent uniquement l'octroi de licence et l'activation.
{:note}

### Paire active/passive de passerelles VMware NSX Edge Services Gateway pour HCX Management
{: #dr_backup_bundle_overview-esg}

* UC : 6 vCPU
* Mémoire RAM : 8 Go
* Disque : VMDK 3 Go

### HCX Management Appliance - Machine virtuelle
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* UC : 4 vCPU
* Mémoire RAM : 12 Go
* Disque : VMDK 60 Go

Des dispositifs HCX supplémentaires sont déployés durant la configuration s'il y a lieu pour la connectivité L2, l'optimisation WAN et les connexions de passerelle.

### Spécifications de réseau pour HCX on IBM Cloud
{: #dr_backup_bundle_overview-hcx-networking-specs}

* Un sous-réseau portable public avec 16 adresses IP
* Deux sous-réseaux portables privés avec 64 adresses IP
* Huit adresses IP issues du sous-réseau vMotion portable privé

## Spécifications techniques relatives à Veeam on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-veeam-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery inclut Veeam on {{site.data.keyword.cloud_notm}}. Les composants suivants sont commandés et inclus dans le service Veeam on {{site.data.keyword.cloud_notm}}.

* Licence de 25 packs de Veeam Availability Suite 
* 4000 Go de stockage 
* 0,25 IOPS/Go de performances de stockage 
* Windows Server 2016 Standard Edition (64 bits)
* 4 coeurs de 2 GHz
* 8 Go de mémoire RAM
* Liaison montante de réseau privé 1 Gbps
* Disque 100 Go (SAN)

## Spécifications techniques relatives à Zerto on {{site.data.keyword.cloud_notm}}
{: #dr_backup_bundle_overview-zerto-tech-specs}

Single-node Trial for Data Protection and Disaster Recovery inclut Zerto on {{site.data.keyword.cloud_notm}}. Les composants suivants sont commandés et inclus dans le service Zerto on {{site.data.keyword.cloud_notm}} :

* Licence Zerto Virtual Replication V6.5u3 
* Une instance de serveur virtuel - Zerto Virtual Manager
* 2 coeurs de 2 GHz
* 4 Go de mémoire RAM
* Windows Server 2016 Standard Edition (64 bits)
* Disque (SAN) 100 Go

## Spécifications techniques pour IBM Cloud Automation Manager
{: #dr_backup_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2 est installé à l'aide de la topologie Développement/Test sur toutes les instances Single-node Trial for Data Protection and Disaster Recovery. Pour plus d'informations sur {{site.data.keyword.cloud_notm}} Automation Manager, voir [Documentation d'{{site.data.keyword.cloud_notm}} Automation Manager](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: new_window}.

## Liens connexes
{: #dr_backup_bundle_overview-related}

* [Ressources VMware HCX](https://hcx.vmware.com/#/docs){:new_window}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:new_window}
* [Gestion de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam)
* [Gestion de Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr)

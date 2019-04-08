---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-22"

subcollection: vmwaresolutions


---

# Mise en réseau et infrastructure IBM Cloud
{: #vcscar-arch-overview-infrastructure}

## Virtual Routing and Forwarding (VRF)
{: #vcscar-arch-overview-infrastructure-vrf}

Les comptes {{site.data.keyword.cloud}} peuvent être configurés en tant que comptes VRF (Virtual Routing and Forwarding). Un compte VRF active le routage global automatique entre des blocs IP de sous-réseau. Tous les comptes dotés de connexions Direct Link doivent être convertis en ou créés en tant que compte VRF.

## Direct Link
{: #vcscar-arch-overview-infrastructure-direct-link}

{{site.data.keyword.cloud_notm}} Direct Link Connect offre un accès privé à votre infrastructure {{site.data.keyword.cloud_notm}}, ainsi qu'à d'autres clouds liés à votre fournisseur de services réseau, via votre centre de données {{site.data.keyword.CloudDataCent_notm}} local. Cette option est idéale pour la création d'une connectivité multi-cloud dans un environnement individuel.

Nous connectons des clients au réseau privé {{site.data.keyword.cloud_notm}} Private grâce à une topologie de bande passante partagée. A l'instar de tous les produits Direct Link, vous pouvez ajouter le routage mondial, qui active le trafic de réseau privé vers tous les emplacements {{site.data.keyword.cloud_notm}}.

## Réseaux privés virtuels
{: #vcscar-arch-overview-infrastructure-virt-private-net}

### VPN strongSwan
{: #vcscar-arch-overview-infrastructure-strongswan}

Le service VPN IPSec strongSwan fournit un canal de communication de bout en bout sécurisé sur Internet, basé sur l'ensemble de protocoles IPSec (Internet Protocol Security) aux normes de l'industrie.

### Hybridité (HCX)
{: #vcscar-arch-overview-infrastructure-hcx}

Le service VMware vCenter Server on {{site.data.keyword.cloud_notm}} Hybridity Bundle peut en toute transparence étendre les réseaux des centres de données locaux dans {{site.data.keyword.cloud_notm}}, ce qui permet de faire migrer les machines virtuelles vers et depuis {{site.data.keyword.cloud_notm}} sans aucune conversion ni modification.

## Structure physique
{: #vcscar-arch-overview-infrastructure-phys-structure}

L'infrastructure physique nécessaire pour déployer une instance de production {{site.data.keyword.icpfull_notm}} sur un cluster VMware vCenter Server on {{site.data.keyword.cloud_notm}}, requiert la spécification minimale suivante.

Tableau 1. Spécification vCenter Server for {{site.data.keyword.icpfull_notm}}

| | Déploiement NFS | Déploiement vSAN |
|:---------- |:---------- |:---------- |
| Nombre de serveurs | 3 | 4 |
| UC | 28 coeurs 2,2 GHz | 28 coeurs 2,2 GHz |
| Mémoire | 384 Go | 384 Go |
| Stockage | 2000 GoB 2IOPS/Go de gestion, 2000 Go 4IOPS/Go de charge de travail, 4000 Go 4IOPS/Go {{site.data.keyword.icpfull_notm}} | Au moins 2 unités SSD de 960Go |

En plus de la configuration matérielle {{site.data.keyword.cloud_notm}} requise, vous devez créer des volumes persistants dans l'environnement {{site.data.keyword.icpfull_notm}} pour stocker les données de journal et la base de données Cloud Automation Manager (CAM). CAM prend en charge tous les types de volume persistant pris en charge par {{site.data.keyword.icpfull_notm}}, mais les deux configurations de stockage recommandées pour CAM sont NFS et GlusterFS.

## Structure virtuelle
{: #vcscar-arch-overview-infrastructure-virt-structure}

Figure 1. Structure du déploiement vCenter Server et {{site.data.keyword.icpfull_notm}}
![Structure du déploiement vCenter Server et {{site.data.keyword.icpfull_notm}}](vcscar-icp.svg)

Dans l'instance vCenter Server, l'instance {{site.data.keyword.icpfull_notm}} est déployée avec une passerelle NSX Edge Services Gateway (ESG) dédiée et un routeur logique distribué (DLR).
L'installation {{site.data.keyword.icpfull_notm}} est chargée dans le sous-réseau VXLAN qui est défini dans les composants ci-dessus.

La passerelle ESG est configurée avec une règle SNAT pour autoriser le trafic sortant, activant ainsi la connectivité pour télécharger les prérequis {{site.data.keyword.icpfull_notm}} et la connectivité à GitHub et Docker. Vous pouvez aussi utiliser un proxy Web pour la connectivité Internet. La passerelle ESG est également configurée pour fournir l'accès aux services DNS et NTP.

La passerelle ESG est également configurée avec une règle NAT de destination (DNAT) vers les adresses IP virtuelles maître/proxy {{site.data.keyword.icpfull_notm}} à partir du réseau {{site.data.keyword.cloud_notm}} 10.x jusqu'à l'environnement VXLAN.

## Liens connexes
{: #vcscar-arch-overview-infrastructure-related}

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

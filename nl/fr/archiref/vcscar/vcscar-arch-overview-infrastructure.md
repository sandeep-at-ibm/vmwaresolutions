---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Mise en réseau et infrastructure IBM Cloud

## Virtual Routing and Forwarding (VRF)

Les comptes {{site.data.keyword.cloud}} peuvent également être configurés en tant que comptes VRF (Virtual Routing and Forwarding). Un compte VRF permet de fournir des fonctionnalités similaires au spanning VLAN et ainsi d'activer le routage automatique entre les blocs d'adresses IP de sous-réseau. Tous les comptes dotés de connexions Direct Link doivent être convertis en ou créés en tant que compte VRF.

## Direct Link

{{site.data.keyword.cloud_notm}} Direct Link Connect offre un accès privé à votre infrastructure {{site.data.keyword.cloud_notm}}, ainsi qu'à d'autres clouds liés à votre fournisseur de services réseau, via votre centre de données {{site.data.keyword.CloudDataCent_notm}} local. Cette option est idéale pour la création d'une connectivité multi-cloud dans un environnement individuel.

Nous connectons des clients au réseau privé {{site.data.keyword.cloud_notm}} Private grâce à une topologie de bande passante partagée. A l'instar de tous les produits Direct Link, vous pouvez ajouter le routage mondial, qui active le trafic de réseau privé vers tous les emplacements {{site.data.keyword.cloud_notm}}.

## Réseaux privés virtuels

### VPN strongSwan

Le service VPN IPSec strongSwan fournit un canal de communication de bout en bout sécurisé sur Internet, basé sur l'ensemble de protocoles IPSec (Internet Protocol Security) aux normes de l'industrie.

### Hybridité (HCX)

Le service VMware vCenter Server on {{site.data.keyword.cloud_notm}} Hybridity Bundle peut en toute transparence étendre les réseaux des centres de données locaux dans {{site.data.keyword.cloud_notm}}, ce qui permet de faire migrer les machines virtuelles vers et depuis {{site.data.keyword.cloud_notm}} sans aucune conversion ni modification.

## Structure physique

L'infrastructure physique nécessaire pour déployer une instance de production {{site.data.keyword.icpfull_notm}} sur un cluster VMware vCenter Server on {{site.data.keyword.cloud_notm}}, requiert la spécification minimale suivante.

Tableau 1. Spécification vCenter Server for {{site.data.keyword.icpfull_notm}}

| Déploiement NFS | Déploiement vSAN |
:--|:----:|:----:
Nombre de serveurs | 3 | 4
UC | 28 coeurs 2,2 GHz | 28 coeurs 2,2 GHz
Mémoire | 384 Go | 384 Go
Stockage | 2000 GB 2IOPS/GB Management, Charge de travail 2000 GB 4IOPS/GB, 4000 GB 4IOPS/GB {{site.data.keyword.icpfull_notm}} | Min 960-GB SSD x 2

En plus de la configuration matérielle {{site.data.keyword.cloud_notm}} requise, vous devez créer des volumes persistants dans l'environnement {{site.data.keyword.icpfull_notm}} pour stocker les données de journal et la base de données Cloud Automation Manager (CAM). CAM prend en charge tous les types de volume persistant pris en charge par {{site.data.keyword.icpfull_notm}}, mais les deux configurations de stockage recommandées pour CAM sont NFS et GlusterFS.

## Structure virtuelle

Figure 1. Structure du déploiement vCenter Server et {{site.data.keyword.icpfull_notm}}
![Structure du déploiement vCenter Server et {{site.data.keyword.icpfull_notm}}](vcscar-icp.svg)

Dans l'instance vCenter Server, l'instance {{site.data.keyword.icpfull_notm}} est déployée avec une passerelle NSX Edge Services Gateway (ESG) dédiée et un routeur logique distribué (DLR).
L'installation {{site.data.keyword.icpfull_notm}} est chargée dans le sous-réseau VXLAN qui est défini dans les composants ci-dessus.

La passerelle ESG est configurée avec une règle SNAT pour autoriser le trafic sortant, activant ainsi la connectivité pour télécharger les prérequis {{site.data.keyword.icpfull_notm}} et la connectivité à GitHub et Docker. Vous pouvez aussi utiliser un proxy Web pour la connectivité Internet. La passerelle ESG est également configurée pour fournir l'accès aux services DNS et NTP.

La passerelle ESG est également configurée avec une règle NAT de destination (DNAT) vers les adresses IP virtuelles maître/proxy {{site.data.keyword.icpfull_notm}} à partir du réseau {{site.data.keyword.cloud_notm}} 10.x jusqu'à l'environnement VXLAN.

### Liens connexes

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)

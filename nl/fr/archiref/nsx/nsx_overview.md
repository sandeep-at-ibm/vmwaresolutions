---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# A propos de NSX Edge Services Gateway (ESG)
{: #nsx_overview}

La solution VMWare NSX Edge Services Gateway (ESG) est une extension des offres VMware Cloud Foundation on {{site.data.keyword.cloud}} et vCenter Server on {{site.data.keyword.cloud_notm}} actuellement disponibles sur {{site.data.keyword.cloud_notm}}. L'architecture de la solution pour Cloud Foundation et vCenter Server décrit en détails les composants de la solution et la configuration à haut niveau de chaque composant de la conception.

Pour plus d'informations sur la conception de Cloud Foundation et vCenter Server, voir [Présentation de la solution](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview).

## Présentation de NSX Edge Services Gateway (ESG)
{: #nsx_overview-nsx-esg}

NSX Edge Services Gateway connecte des réseaux stub isolés à des réseaux (de liaison montante) partagés en fournissant des services de passerelle courants, tels que DHCP (Dynamic Host Configuration Protocol), réseau privé virtuel (VPN), conversion d'adresses réseau (NAT), routage dynamique et équilibrage de charge. Les déploiements courants de NSX Edge comprennent une zone démilitarisée (DMZ), des extranets VPN, des environnements cloud à plusieurs locataires dans lesquels NSX Edge crée des frontières virtuelles pour chaque locataire, charge de travail ou composant de gestion. Les fonctions suivantes sont disponibles dans NSX Edge Service Gateway.

Tableau 1. Fonctions disponibles avec NSX Edge Service Gateway

| Fonction | Description |
|:------- |:----------- |
| Routage de services NSX Edge | Fournit les informations de transfert nécessaires entre deux domaines de diffusion L2, vous permettant ainsi de réduire les domaines de diffusion L2 et d'améliorer l'évolutivité et l'efficacité du réseau. NSX étend cette fonction à l'emplacement des charges de travail pour effectuer le routage est-ouest. Cela permet une communication plus directe de machine virtuelle à machine virtuelle sans avoir à étendre les tronçons ce qui prendrait du temps et de l'argent. En même temps, NSX fournit également la connectivité nord-sud, permettant ainsi aux locataires d'accéder aux réseaux publics. |
| Pare-feu | Les règles de pare-feu prises en charge comprennent une configuration à 5 tuples pour les adresses IP avec des plages d'adresses IP et de port pour l'inspection avec état de tous les protocoles. |
| NAT | Fournit des contrôles distincts pour les adresses IP source et de destination et la conversion de port. |
| DHCP | Fournit la configuration des pools d'adresses IP, des passerelles, des serveurs DNS et des domaines de recherche. |
| VPN de site à site | Utilise les paramètres du protocole IPSec normalisés pour interopérer avec tous les fournisseurs principaux de VPN. |
| L2VPN | Etend les réseaux L2 sur les topologies L3. |
| SSL VPN-Plus |  SSL VPN-Plus permet aux utilisateurs distants de se connecter de manière sécurisée à des réseaux privés derrière une passerelle NSX Edge. |
| Equilibrage de charge | Fournit des groupes de serveurs et des adresses IP virtuelles configurables de manière simple et dynamique. |
| Haute disponibilité | Assure la présence d'une machine virtuelle NSX Edge active sur le réseau en cas d'indisponibilité de la machine virtuelle NSX Edge principale. |

## Liens connexes
{: #nsx_overview-related}

* [Présentation de la solution](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: Mission Critical VMware, Mission Critical, tech specs Mission Critical

subcollection: vmware-solutions


---

# Présentation de Mission Critical VMware on IBM Cloud
{: #mcv_overview}

Mission Critical VMware on {{site.data.keyword.cloud}} fournit une architecture de cloud multi-zone qui permet aux entreprises d'empêcher les temps d'indisponibilité pour les applications en cloud et qui permet d'automatiser les basculements dans une région de cloud.

Grâce à cette architecture de cloud, les clients peuvent atteindre un taux de réussite de disponibilité et de basculement plus élevé que celui obtenu par la plupart des clients VMware avec des environnements sur site ou des plateformes cloud concurrentes.

Cette architecture prend en charge des charges de travail existantes indispensables à la mission, y compris des applications natives non-cloud, à un taux de disponibilité en agrégat ciblée de 99,99 %. Les régions IBM Cloud multi-zone sont conçues pour maintenir les charges de travail indispensables à la mission en ligne en cas de panne sur le site. Les charges de travail sur un site en échec sont automatiquement redémarrées en temps quasi réel, tandis que les charges de travail sur les sites voisins restent en ligne et disponibles.

L'architecture couvre divers services d'entreprise, y compris les réseaux, le stockage, la résilience et d'autres outils créés pour la surveillance et le traitement des incidents liés aux applications cloud. De plus, cette architecture peut être intégrée à IBM Services Platform with Watson, créé sur {{site.data.keyword.cloud_notm}}, afin de permettre une plus grande consommation de services. Grâce aux fonctions cognitives de la plateforme, les clients peuvent exploiter des données de manière plus efficace et obtenir de nouvelles connaissances métier permettant la continuité des opérations.

## Spécifications techniques relatives à Mission Critical VMware on IBM Cloud
{: #mcv_overview-specs}

L'architecture Mission Critical VMware on {{site.data.keyword.cloud_notm}} est une architecture de référence de bout en bout qui fournit un basculement automatique pour les charges de travail client. Elle utilise une région {{site.data.keyword.cloud_notm}} multi-zone avec un service géré par IBM qui couvre les composants suivants :

* Architecture de calcul (VMware vSphere)
* Architecture de réseau (actuellement, NSX-V)
* Architecture de stockage (VMware vSAN)
* Intégration à IBM Services Platform with Watson pour activer la consommation de services
* Outils de surveillance, de traitement des incidents et de gestion des performances et de la capacité :
  * Modèle vRealize Suite (Operations, Log Insight et Network Insight)
  * Modèle Active Directory
  * Intégration à Netcool/Bluecare pour la génération automatique de demandes de service, la génération d'alertes et l'enrichissement d'événement
  * Modèles de résilience (sauvegarde et reprise)

Mission Critical VMware on {{site.data.keyword.cloud_notm}} est disponible dans les régions suivantes :
* Amérique : Sud de l'Amérique du Nord - tous les centres de données IBM Cloud situés à Dallas et Est de l'Amérique du Nord - tous les centres de données IBM Cloud situés à Washington, DC
* Europe : tous les centres de données IBM Cloud situés à Francfort et à Londres
* Asie-Pacifique : tous les centres de données IBM Cloud situés à Sydney et à Tokyo

### Spécifications d'architecture de l'infrastructure de base :
{: #mcv_overview-base-specs}

Les spécifications de l'infrastructure de base sont les suivantes :
* Chaque site possède son propre cluster de gestion et Edge dédié
* Le cluster de ressources est un cluster vSphere + vSAN étendu
* Le site témoin contient un hôte ESXi témoin
* Architecture vCenter et NSX Manager unique
* vCenter Server Appliance avec un contrôleur PSC (Platform Services Controller) intégré qui utilise vCenter High Availability (HA) sur une architecture de réseau L3
* La reprise NSX Manager utilise une méthodologie de secours automatique qui synchronise les fichiers de sauvegarde

### Spécifications de l'architecture des outils et des technologies
{: #mcv_overview-tooling-specs}

Les spécifications de l'architecture des outils et des technologies sont les suivantes :
* vRealize Operations, vRealize Log Insight et vRealize Network Insight fournissent des opérations et des fonctions de gestion propres aux produits VMware utilisés, par exemple, NSX, vSAN et vSphere
* IBM Software Defined Environment Automation Tool Health Check (SAT HC) est utilisé pour valider les déploiements en termes de meilleures pratiques et de règles de sécurité
* Fonction de reprise après incident facultative sur un site {{site.data.keyword.cloud_notm}} hors région
* Fortigate Security Appliance ou un dispositif similaire est utilisé pour sécuriser les accès Internet et faciliter l'intégration de réseau active-active au réseau sur site

### Spécifications de l'architecture de cluster vSphere + vSAN étendu
{: #mcv_overview-stretched-cluster-specs}

Les spécifications de l'architecture de cluster vSphere + vSAN étendu sont les suivantes :
* Le cluster fournit des fonctions de stockage et de calcul sur deux sites pour assurer une plus grande disponibilité
* Les demandes d'écriture provenant des machines virtuelles sont écrites de façon synchronisée vers les deux sites, occasionnant un temps d'attente des réseaux de site à site
* Les demandes de lecture provenant des machines virtuelles sont satisfaites localement sur l'emplacement physique de ces dernières, évitant ainsi des temps d'attente supplémentaires
* Le site témoin et l'hôte témoin agissent comme déconnexion cérébrale/quorum
* Le chiffrement natif vSAN (pour le chiffrement des données au repos) peut être utilisé conjointement avec cette architecture

### Spécifications de l'architecture de réseau
{: #mcv_overview-network-specs}

Les spécifications de l'architecture de réseau sont les suivantes :
* L'ensemble Edge/DLR/VXLAN est utilisé conjointement au routage basé sur les métriques BGP pour faciliter une conception de site active-active avec basculement automatisé
* Chaque site possède son propre ensemble Edge/DLR/VXLAN
* Dans des conditions de fonctionnement normales, toutes les machines virtuelles connectées à DLR-A, par exemple, VM-A, figureront dans la zone de disponibilité {{site.data.keyword.cloud_notm}} numéro 1 et le trafic sera à la fois entrant et sortant localement
* Durant une activité vMotion pour VM-A, le trafic sera toujours entrant et sortant via la zone de disponibilité {{site.data.keyword.cloud_notm}} numéro 1
* Durant une panne de site ou de cluster Edge, le trafic sera acheminé vers le site disponible restant

## Liens connexes
{: #mcv_overview-related}

* [Demande de Mission Critical VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_mcv)

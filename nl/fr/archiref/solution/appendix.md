---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

# Graphique de comparaison des éditions de composant VMware
{: #solution-appendix}

## Comparaison des éditions VMware NSX
{: #solution-appendix-nsx-editions}

Dans cette conception, plusieurs composants nécessitent des licences. Ces informations indiquent les licences minimales nécessaires pour que l'environnement fonctionne correctement.

Tableau 1. Exigence en matière de licence

Composant | Objectif | Licence
----------|---------|-------------
**vSphere** | Virtualisation du calcul | vSphere 6.7 Enterprise Plus
**vCenter Server** | Gestion d'infrastructure | vCenter Server 6.7 Standard
**NSX** | Virtualisation du réseau | NSX Base for Service Providers 6.4
**vSAN** | Virtualisation du stockage | vSAN 6.6 Advanced  

L'édition NSX Base for Service Providers est disponible uniquement pour les fournisseurs de services via VMware vCloud Air Network (vCAN). Les fonctionnalités de cette édition sont récapitulées dans le tableau suivant.
{:note}

Tableau 2. Graphique de comparaison des éditions dVMware NSX

| Fonction NSX                                   | Base | Advanced | Enterprise |
|-----------------------------------------------|------|----------|------------|
| Commutation et routage distribués             | •    | •        | •          |
| Pare-feu NSX Edge                             | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| Equilibrage de charge NSX Edge                       | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| Automatisation pilotée par API                         | •    | •        | •          |
| Intégration avec vRealize et OpenStack\*     | •    | •        | •          |
| Automatisation des politiques de sécurité avec vRealize |      | •        | •          |
| Pontage SW L2 vers un environnement physique        |      | •        | •          |
| Routage dynamique avec ECMP (actif-actif)     |      | •        | •          |
| Protection pare-feu distribuée                       |      | •        | •          |
| Intégration à Active Directory             |      | •        | •          |
| Surveillance des activités de serveur                    |      | •        | •          |
| Insertion de service (intégration tierce)     |      | •        | •          |
| Equilibrage de charge distribué                    |      |          | •          |
| Passerelle NSX vCenter transversale                             |      |          | •          |
| Optimisations NSX multisite                  |      |          | •          |
| Passerelle éloignée                                |      |          | •          |
| Intégration à HW VTEP                     |      |          | •          |
\*Intégration L2, L3 & NSX Edge uniquement. Pas de consommation de groupes de sécurité.

## Comparaison des éditions VMware vSAN
{: #solution-appendix-vsan-editions}

Le tableau suivant répertorie les fonctions disponibles pour les éditions **Advanced** et **Enterprise** de VMware vSAN qui sont prises en charge par la solution.

Tableau 3. Graphique de comparaison des éditions VMware vSAN

| Fonction vSAN                                    | Advanced | Enterprise |
|-------------------------------------------------|----------|------------|
| Gestion basée sur des règles de stockage                 | •        | •          |
| Cache en lecture/écriture flash                        | •        | •          |
| RAID distribué                                | •        | •          |
| Commutateur distribué virtuel                      | •        | •          |
| Détection d'armoire                                  | •        | •          |
| Réplication vSphere                             | •        | •          |
| Total de contrôle de logiciel                               | •        | •          |
| Matériel all-flash                              | •        | •          |
| Unité cible iSCSI                            | •        | •          |
| Limite IOPS                                      | •        | •          |
| Dédoublonnage et compression                   | •        | •          |
| Codage d'effacement RAID-5/6                         | •        | •          |
| Chiffrement des données au repos                         |          | •          |
| Cluster étendu avec protection locale contre les pannes |          | •          |

## Liens connexes
{: #solution-appendix-related}

* [Présentation de la solution](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [Présentation de la conception](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Sauvegarde des composants](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)

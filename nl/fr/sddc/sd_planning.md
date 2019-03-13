---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Exigences et planification pour les instances Cloud Foundation
{: #sd_planning}

Passez en revue les exigences suivantes avant de commander vos instances VMware Cloud Foundation. Planifiez votre instance en fonction de l'emplacement de l'{{site.data.keyword.CloudDataCent}}, de vos besoins en capacité de charge de travail et de vos besoins en services.

## Exigences liées au compte IBM Cloud
{: #sd_planning-account-req}

Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-slaccountrequirement).

## Disponibilité du centre de données IBM Cloud
{: #sd_planning-dc-availability}

Des exigences très strictes sont liées au déploiement Cloud Foundation sur l'infrastructure physique. Par conséquent, vous ne pouvez déployer des instances que dans des {{site.data.keyword.CloudDataCents_notm}} qui répondent à ces exigences. Les {{site.data.keyword.CloudDataCents_notm}} suivants sont disponibles pour un déploiement Cloud Foundation :

Tableau 1. {{site.data.keyword.CloudDataCents_notm}} et configurations de serveur bare metal {{site.data.keyword.cloud_notm}} disponibles pour des instances Cloud Foundation

| {{site.data.keyword.CloudDataCent_notm}} | Emplacement | Région | Configurations de serveur |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europe | Skylake, Broadwell |
| CHE01 | Chennai | Asie-Pacifique | Skylake, Broadwell |
| DAL09 | Dallas | Sud des Etats-Unis | Skylake, Broadwell |
| DAL10 | Dallas | Sud des Etats-Unis | Skylake, Broadwell |
| DAL12 | Dallas | Sud des Etats-Unis | Skylake, Broadwell |
| DAL13 | Dallas | Sud des Etats-Unis | Skylake, Broadwell |
| FRA02 | Francfort | Europe | Skylake, Broadwell |
| FRA04 | Francfort | Europe | Skylake, Broadwell |
| HKG02 | Hong Kong | Asie-Pacifique | Skylake, Broadwell |
| LON02 | Londres | Europe | Skylake, Broadwell |
| LON04 | Londres | Europe | Skylake, Broadwell |
| LON06 | Londres | Europe | Skylake, Broadwell |
| MEL01 | Melbourne | Asie-Pacifique | Skylake, Broadwell |
| MEX01 | Querétaro | Sud des Etats-Unis | Skylake, Broadwell |
| MIL01 | Milan | Europe | Skylake, Broadwell |
| MON01 | Montréal | Est des Etats-Unis | Skylake, Broadwell |
| OSL01 | Oslo | Europe | Skylake, Broadwell |
| PAR01 | Paris | Europe | Skylake, Broadwell |
| SAO01 | São Paulo | Amérique du Sud | Skylake, Broadwell |
| SEO01 | Séoul | Asie-Pacifique | Skylake, Broadwell |
| SJC03 | San José | Ouest des Etats-Unis | Skylake, Broadwell |
| SJC04 | San José | Ouest des Etats-Unis | Skylake, Broadwell |
| SNG01 | Singapour | Asie-Pacifique | Skylake, Broadwell |
| SYD01 | Sydney | Asie-Pacifique | Skylake, Broadwell |
| SYD04 | Sydney | Asie-Pacifique | Skylake, Broadwell |
| TOK02 | Tokyo | Asie-Pacifique | Skylake, Broadwell |
| TOR01 | Toronto | Est des Etats-Unis | Skylake, Broadwell |
| WDC04 | Washington, DC | Est des Etats-Unis | Skylake, Broadwell |
| WDC06 | Washington, DC | Est des Etats-Unis | Skylake, Broadwell |
| WDC07 | Washington, DC | Est des Etats-Unis | Skylake, Broadwell |

Selon la disponibilité et l'approvisionnement du stock, les {{site.data.keyword.CloudDataCents_notm}} peuvent afficher un indicateur de statut sur la console {{site.data.keyword.vmwaresolutions_short}} pour vous aider à planifier vos déploiements.

Tableau 2. Indicateurs de statut pour les {{site.data.keyword.CloudDataCents_notm}} lors de la commande d'instances Cloud Foundation

| Statut | Détails du statut |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Temporarily Out of Inventory  | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Limited Inventory             | L'{{site.data.keyword.CloudDataCent_notm}} a une disponibilité limitée et la commande risque de ne pas être honorée. |

## Sauvegarde des composants de gestion
{: #sd_planning-backup-mgmt-components}

Vous êtes chargé de gérer et d'assurer la disponibilité de tous les composants d'instance. Il est recommandé de planifier la sauvegarde ou la haute disponibilité de tous les composants de gestion. Pour plus d'informations, voir [Sauvegarde des composants](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services pour les instances Cloud Foundation
{: #sd_planning-addon-services}

Vous pouvez commander des services complémentaires pour votre instance en fonction de vos besoins, par exemple, la reprise après incident. Pour plus d'informations, voir [Commande, affichage et retrait de services pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices).

## Remarques sur la capacité
{: #sd_planning-capacity-considerations}

Pour plus d'informations sur la capacité, voir [Mise à l'échelle de la capacité](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Liens connexes
{: #sd_planning-related}

* [Présentation de Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Commande d'instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Extension et réduction de capacité pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# Exigences et planification pour les instances Cloud Foundation

Passez en revue les exigences suivantes avant de commander vos instances VMware Cloud Foundation. Planifiez votre instance en fonction de l'emplacement de l'{{site.data.keyword.CloudDataCent}}, de vos besoins en capacité de charge de travail et de vos besoins en services.

## Exigences liées au compte IBM Cloud

Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilité du centre de données IBM Cloud

Des exigences très strictes sont liées au déploiement Cloud Foundation sur l'infrastructure physique. Par conséquent, vous ne pouvez déployer des instances que dans des {{site.data.keyword.CloudDataCents_notm}} qui répondent à ces exigences. Les {{site.data.keyword.CloudDataCents_notm}} suivants sont disponibles pour un déploiement Cloud Foundation :

Tableau 1. {{site.data.keyword.CloudDataCents_notm}} et configurations de serveur bare metal {{site.data.keyword.cloud_notm}} disponibles pour des instances Cloud Foundation

| {{site.data.keyword.CloudDataCent_notm}} | Emplacement | Région | Configurations de serveur |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdam | Europe | Personnalisée |
| CHE01 | Chennai | Asie-Pacifique | Personnalisée |
| DAL09 | Dallas | Sud des Etats-Unis | Personnalisée |
| DAL10 | Dallas | Sud des Etats-Unis | Personnalisée, Petite, Grande |
| DAL12 | Dallas | Sud des Etats-Unis | Personnalisée |
| DAL13 | Dallas | Sud des Etats-Unis | Personnalisée |
| FRA02 | Francfort | Europe | Personnalisée, Grande |
| FRA04 | Francfort | Europe | Personnalisée |
| HKG02 | Hong Kong | Asie-Pacifique | Personnalisée |
| LON02 | Londres | Europe | Personnalisée |
| LON04 | Londres | Europe | Personnalisée |
| LON06 | Londres | Europe | Personnalisée, Petite, Grande |
| MEL01 | Melbourne | Asie-Pacifique | Personnalisée |
| MEX01 | Querétaro | Sud des Etats-Unis | Personnalisée |
| MIL01 | Milan | Europe | Personnalisée |
| MON01 | Montréal | Est des Etats-Unis | Personnalisée |
| OSL01 | Oslo | Europe | Personnalisée |
| PAR01 | Paris | Europe | Personnalisée |
| SAO01 | São Paulo | Amérique du Sud | Personnalisée |
| SEO01 | Séoul | Asie-Pacifique | Personnalisée |
| SJC03 | San José | Ouest des Etats-Unis | Personnalisée |
| SJC04 | San José | Ouest des Etats-Unis | Personnalisée |
| SNG01 | Singapour | Asie-Pacifique | Personnalisée |
| SYD01 | Sydney | Asie-Pacifique | Personnalisée |
| SYD04 | Sydney | Asie-Pacifique | Personnalisée |
| TOK02 | Tokyo | Asie-Pacifique | Personnalisée |
| TOR01 | Toronto | Est des Etats-Unis | Personnalisée, Petite, Grande |
| WDC04 | Washington, DC | Est des Etats-Unis | Personnalisée, Petite, Grande |
| WDC06 | Washington, DC | Est des Etats-Unis | Personnalisée |
| WDC07 | Washington, DC | Est des Etats-Unis | Personnalisée |

Selon la disponibilité et l'approvisionnement du stock, les {{site.data.keyword.CloudDataCents_notm}} peuvent afficher un indicateur de statut sur la console {{site.data.keyword.vmwaresolutions_short}} pour vous aider à planifier vos déploiements.

Tableau 2. Indicateurs de statut pour les {{site.data.keyword.CloudDataCents_notm}} lors de la commande d'instances Cloud Foundation

| Statut | Détails du statut |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Temporarily Out of Inventory  | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Limited Inventory             | L'{{site.data.keyword.CloudDataCent_notm}} a une disponibilité limitée et la commande risque de ne pas être honorée. |

## Sauvegarde des composants de gestion

Vous êtes chargé de gérer et d'assurer la disponibilité de tous les composants d'instance. Il est recommandé de planifier la sauvegarde ou la haute disponibilité de tous les composants de gestion. Pour plus d'informations, voir [Sauvegarde des composants](../archiref/solution/solution_backingup.html).

## Services pour les instances Cloud Foundation

Vous pouvez commander des services complémentaires pour votre instance en fonction de vos besoins, par exemple, la reprise après incident. Pour plus d'informations, voir [Commande, affichage et retrait de services pour des instances Cloud Foundation](sd_addingremovingservices.html).

## Remarques sur la capacité

Pour plus d'informations sur la capacité, voir [Mise à l'échelle de la capacité](../archiref/solution/solution_scaling.html).

### Liens connexes

* [Présentation de Cloud Foundation](sd_cloudfoundationoverview.html)
* [Commande d'instances Cloud Foundation](sd_orderinginstance.html)
* [Extension et réduction de capacité pour des instances Cloud Foundation](sd_addingremovingservers.html)
* [Commande, affichage et retrait de services pour des instances Cloud Foundation](sd_addingremovingservices.html)

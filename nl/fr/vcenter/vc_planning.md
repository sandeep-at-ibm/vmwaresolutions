---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Exigences et planification pour les instances vCenter Server

Passez en revue les exigences suivantes avant de commander vos instances VMware vCenter Server. Planifiez votre instance en fonction de l'emplacement de l'{{site.data.keyword.CloudDataCent}}, de vos besoins en capacité de charge de travail et de vos besoins en services complémentaires.

## Exigences liées au compte IBM Cloud

Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilité du centre de données IBM Cloud

Les déploiements unifiés vCenter Server ont des exigences strictes quant à l'infrastructure physique. Par conséquent, vous ne pouvez déployer des instances que dans des {{site.data.keyword.CloudDataCents_notm}} qui répondent à ces exigences. Les {{site.data.keyword.CloudDataCents_notm}} suivants sont disponibles pour un déploiement vCenter Server :

Tableau 1. {{site.data.keyword.CloudDataCents_notm}} disponibles pour les instances vCenter Server

| {{site.data.keyword.CloudDataCent_notm}} | Emplacement | Région | Options de serveur |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdam | Europe | Personnalisée |
| CHE01 | Chennai | Asie-Pacifique | Personnalisée |
| DAL09 | Dallas | Sud des Etats-Unis | Personnalisée |
| DAL10 | Dallas | Sud des Etats-Unis | Personnalisée, Petite, Moyenne, Grande |
| DAL12 | Dallas | Sud des Etats-Unis | Personnalisée |
| DAL13 | Dallas | Sud des Etats-Unis | Personnalisée |
| FRA02 | Francfort | Europe | Personnalisée, Petite, Moyenne, Grande |
| FRA04 | Francfort | Europe | Personnalisée |
| HKG02 | Hong Kong | Asie-Pacifique | Personnalisée |
| LON02 | Londres | Europe | Personnalisée |
| LON04 | Londres | Europe | Personnalisée |
| LON06 | Londres | Europe | Personnalisée, Petite, Moyenne, Grande |
| MEL01 | Melbourne | Asie-Pacifique | Personnalisée |
| MEX01 | Querétaro | Sud des Etats-Unis | Personnalisée |
| MIL01 | Milan | Europe | Personnalisée |
| MON01 | Montréal | Est des Etats-Unis | Personnalisée |
| OSL01 | Oslo | Europe | Personnalisée |
| PAR01 | Paris | Europe | Personnalisée |
| SAO01 | São Paulo | Amérique du Sud | Personnalisée |
| SEO01 | Séoul | Asie-Pacifique | Personnalisée |
| SJC03 | San José | Ouest des Etats-Unis | Personnalisée, Petite, Moyenne, Grande |
| SJC04 | San José | Ouest des Etats-Unis | Personnalisée |
| SNG01 | Singapour | Asie-Pacifique | Personnalisée |
| SYD01 | Sydney | Asie-Pacifique | Personnalisée |
| SYD04 | Sydney | Asie-Pacifique | Personnalisée |
| TOK02 | Tokyo | Asie-Pacifique | Personnalisée |
| TOR01 | Toronto | Est des Etats-Unis | Personnalisée, Petite, Moyenne, Grande |
| WDC04 | Washington, DC | Est des Etats-Unis | Personnalisée, Petite, Moyenne, Grande |
| WDC06 | Washington, DC | Est des Etats-Unis | Personnalisée |
| WDC07 | Washington, DC | Est des Etats-Unis | Personnalisée |

Un petit sous-ensemble d'{{site.data.keyword.CloudDataCents_notm}} offre des options de serveur bare metal **Petite**, **Moyenne** et **Grande** préconfigurées. Selon la disponibilité et l'approvisionnement du stock, les {{site.data.keyword.CloudDataCents_notm}} peuvent afficher un indicateur de statut sur la console {{site.data.keyword.vmwaresolutions_short}} pour vous aider à planifier vos déploiements.

Tableau 2. Indicateurs de statut pour les {{site.data.keyword.CloudDataCents_notm}} lors de la commande d'instances vCenter Server

| Statut | Détails du statut |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Temporarily Out of Inventory  | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Limited Inventory             | L'{{site.data.keyword.CloudDataCent_notm}} a une disponibilité limitée et la commande risque de ne pas être honorée. |

## Sauvegarde des composants de gestion

Vous êtes chargé de gérer et d'assurer la disponibilité de tous les composants d'instance. Il est fortement recommandé de planifier la sauvegarde ou la haute disponibilité de tous les composants de gestion. Pour plus d'informations, voir [Sauvegarde des composants](../archiref/solution/solution_backingup.html).

## Services pour les instances vCenter Server

Vous pouvez commander des services complémentaires pour votre instance en fonction de vos besoins, par exemple, la reprise après incident. Pour plus d'informations, voir[Commande, affichage et retrait de services pour des instances vCenter Server](vc_addingremovingservices.html).

## Remarques sur la capacité

Pour plus d'informations sur la capacité, voir [Mise à l'échelle de la capacité](../archiref/solution/solution_scaling.html).

### Liens connexes

* [Présentation de vCenter Server](vc_vcenterserveroverview.html)
* [Commande d'instances vCenter Server](vc_orderinginstance.html)
* [Extension et réduction de capacité pour des instances vCenter Server](vc_addingremovingservers.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server](vc_addingremovingservices.html)

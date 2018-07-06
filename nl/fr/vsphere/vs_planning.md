---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Exigences et planification pour VMware vSphere on IBM Cloud

Passez en revue les exigences suivantes avant de commander VMware vSphere on {{site.data.keyword.cloud}}. Planifiez vos clusters VMware vSphere en fonction de l'emplacement de l'{{site.data.keyword.CloudDataCent_notm}} et de vos besoins en matière de capacité de charge de travail.

**Remarque** : vous êtes responsable de la configuration de l'environnement, de l'installation et de la configuration des divers composants VMware après le déploiement des serveurs ESXi. Ces composants sont notamment : VMware vCenter Server, VMware NSX et VMware vSAN.

## Exigences liées au compte IBM Cloud

Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilité du centre de données IBM Cloud

Un déploiement vSphere a des exigences strictes quant à l'infrastructure physique. Par conséquent, vous ne pouvez déployer des clusters que dans les {{site.data.keyword.CloudDataCents_notm}} qui répondent à ces exigences. Les {{site.data.keyword.CloudDataCent_notm}} suivants sont disponibles pour un déploiement vSphere.

**Remarque :** si vous sélectionnez un composant vSAN, la liste des emplacements est filtrée par disponibilité SSD (Solid State Disk).

Tableau 1. {{site.data.keyword.CloudDataCents_notm}} disponibles pour les clusters vSphere

| {{site.data.keyword.CloudDataCent_notm}} | Emplacement | Région |
|:----------------------|:---------|:-------|
| AMS03 | Amsterdam | Europe |
| CHE01 | Chennai | Asie-Pacifique |
| DAL09 | Dallas | Sud des Etats-Unis |
| DAL10 | Dallas | Sud des Etats-Unis |
| DAL12 | Dallas | Sud des Etats-Unis |
| DAL13 | Dallas | Sud des Etats-Unis |
| FRA02 | Francfort | Europe |
| FRA04 | Francfort | Europe |
| HKG02 | Hong Kong | Asie-Pacifique |
| LON02 | Londres | Europe |
| LON04 | Londres | Europe |
| LON06 | Londres | Europe |
| MEL01 | Melbourne | Asie-Pacifique |
| MEX01 | Querétaro | Sud des Etats-Unis |
| MIL01 | Milan | Europe |
| MON01 | Montréal | Est des Etats-Unis |
| OSL01 | Oslo | Europe |
| PAR01 | Paris | Europe |
| SAO01 | São Paulo | Amérique du Sud |
| SEO01 | Séoul | Asie-Pacifique |
| SJC03 | San José | Ouest des Etats-Unis |
| SJC04 | San José | Ouest des Etats-Unis |
| SNG01 | Singapour | Asie-Pacifique |
| SYD01 | Sydney | Asie-Pacifique |
| SYD04 | Sydney | Asie-Pacifique |
| TOK02 | Tokyo | Asie-Pacifique |
| TOR01 | Toronto | Est des Etats-Unis |
| WDC04 | Washington, DC | Est des Etats-Unis |
| WDC06 | Washington, DC | Est des Etats-Unis |
| WDC07 | Washington, DC | Est des Etats-Unis |

## Liens connexes

* [Commande de nouveaux clusters vSphere](vs_orderinginstances.html)
* [Mise à l'échelle de clusters existants](vs_scalingexistingclusters.html)
* [Mise à l'échelle de clusters existants créés en dehors de la console](vs_orderingforclustersoutside.html)

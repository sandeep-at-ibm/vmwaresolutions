---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# Exigences et planification pour les instances vCenter Server with Hybridity Bundle

Passez en revue les exigences suivantes avant de commander votre instance VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Planifiez votre instance en fonction de l'emplacement de l'{{site.data.keyword.CloudDataCent_notm}}, de vos besoins en capacité de charge de travail et de vos besoins en services supplémentaires.

## Exigences liées au compte IBM Cloud

Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilité du centre de données IBM Cloud

Le déploiement vCenter Server with Hybridity Bundle a des exigences strictes quant à l'infrastructure physique. Par conséquent, vous ne pouvez déployer des instances que dans des {{site.data.keyword.CloudDataCents_notm}} qui répondent à ces exigences. Les {{site.data.keyword.CloudDataCents_notm}} suivants sont disponibles pour le déploiement vCenter Server with Hybridity Bundle :

Tableau 1. {{site.data.keyword.CloudDataCents_notm}} disponibles pour les instances vCenter Server with Hybridity Bundle

| {{site.data.keyword.CloudDataCent_notm}} | Emplacement | Région |
|:-----|:----------------|
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

Selon la disponibilité et l'approvisionnement du stock, les {{site.data.keyword.CloudDataCents_notm}} peuvent afficher un indicateur de statut sur la console {{site.data.keyword.vmwaresolutions_short}} pour vous aider à planifier vos déploiements.

Tableau 2. Indicateurs de statut pour les {{site.data.keyword.CloudDataCents_notm}} lors de la commande d'instances Center Server with Hybridity Bundle

| Statut | Détails du statut |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Temporarily Out of Inventory  | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Limited Inventory             | L'{{site.data.keyword.CloudDataCent_notm}} a une disponibilité limitée et la commande risque de ne pas être honorée. |

## Sauvegarde des composants de gestion

Vous êtes chargé de gérer et d'assurer la disponibilité de tous les composants d'instance. Il est fortement recommandé de planifier la sauvegarde ou la haute disponibilité de tous les composants de gestion. Pour plus d'informations, voir [Sauvegarde des composants](../archiref/solution/solution_backingup.html).

## Services pour les instances vCenter Server with Hybridity Bundle

L'instance vCenter Server with Hybridity Bundle inclut la licence VMware Hybrid Cloud Extension (HCX) qui vous autorise à utiliser le service VMware HCX on {{site.data.keyword.cloud_notm}}. Ce service peut en toute transparence étendre les réseaux des centres de données locaux dans {{site.data.keyword.cloud_notm}}, ce qui permet de migrer les machines virtuelles vers et depuis {{site.data.keyword.cloud_notm}} sans aucune conversion ni modification.

Lorsque vous déployez ce service, définissez les paramètres suivants :
* Renseignez la zone **Type d'interconnexion HCX** en sélectionnant l'une des options suivantes :
  * **Réseau public** : HCX crée une connexion chiffrée entre des sites sur le réseau public.
  * **Réseau privé** : HCX crée une connexion chiffrée entre des sites sur le réseau privé.
* Renseignez la zone **Type de certificat de noeud final public**. Si vous sélectionnez **Certificat de l'autorité de certification**, configurez les paramètres suivants :
  * **Contenu de certificat** : entrez le contenu du certificat de l'autorité de certification.
  * **Clé privée** : entrez la clé privée du certificat de l'autorité de certification.
  * (Facultatif) **Mot de passe** : entrez le mot de passe de la clé privée si elle est chiffrée.
  * (Facultatif) **Confirmer le mot de passe** : entrez de nouveau le mot de passe de la clé privée.
  * (Facultatif) **Nom d'hôte** : entrez le nom d'hôte à mapper au nom usuel du certificat de l'autorité de certification. HCX on {{site.data.keyword.cloud_notm}} exige que le certificat de l'autorité de certification soit dans un format accepté par NSX Edge. Pour plus d'informations sur les formats de certificat NSX Edge, voir [Importation de certificats SSL](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

Vous pouvez commander d'autres services complémentaires pour votre instance en fonction de vos besoins, par exemple, la reprise après incident. Pour plus d'informations, voir [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html).

## Remarques sur la capacité

Pour plus d'informations sur la capacité, voir [Mise à l'échelle de la capacité](../archiref/solution/solution_scaling.html).

### Liens connexes

* [Présentation de vCenter Server with Hybridity Bundle](vc_hybrid_overview.html)
* [Commande d'instances vCenter Server with Hybridity Bundle](vc_hybrid_orderinginstance.html)
* [Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservers.html)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](vc_hybrid_addingremovingservices.html)

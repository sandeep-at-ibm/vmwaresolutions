---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: planning vCenter Server Hybridity, data center hybridity, vCenter Server Hybridity

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# Exigences et planification pour les instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_planning}

Passez en revue les exigences suivantes avant de commander votre instance VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle. Planifiez votre instance en fonction de l'emplacement de l'{{site.data.keyword.CloudDataCent_notm}}, de vos besoins en capacité de charge de travail et de vos besoins en services supplémentaires.

## Exigences liées au compte IBM Cloud
{: #vc_hybrid_planning-account-req}

Le compte {{site.data.keyword.cloud_notm}} que vous utilisez doit répondre à certaines exigences. Pour plus d'informations, voir [Exigences liées au compte {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## Disponibilité du centre de données IBM Cloud
{: #vc_hybrid_planning-dc-availability}

Le déploiement vCenter Server with Hybridity Bundle a des exigences strictes quant à l'infrastructure physique. Par conséquent, vous ne pouvez déployer des instances que dans des {{site.data.keyword.CloudDataCents_notm}} qui répondent à ces exigences. Les {{site.data.keyword.CloudDataCents_notm}} suivants sont disponibles pour le déploiement vCenter Server with Hybridity Bundle :

| {{site.data.keyword.CloudDataCent_notm}} | Emplacement | Région |
|:----------------------|:---------|:---------------|
| AMS03 | Amsterdam | Europe |
| CHE01 | Chennai | Asie-Pacifique |
| DAL09 | Dallas | Sud des Etats-Unis |
| DAL10 | Dallas | Sud des Etats-Unis |
| DAL12 | Dallas | Sud des Etats-Unis |
| DAL13 | Dallas | Sud des Etats-Unis |
| FRA02 | Francfort | Europe |
| FRA04 | Francfort | Europe |
| FRA05 | Francfort | Europe |
| HKG02 | Hong Kong | Asie-Pacifique |
| LON02 | Londres | Europe |
| LON04 | Londres | Europe |
| LON05 | Londres | Europe |
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
| TOK04 | Tokyo | Asie-Pacifique |
| TOR01 | Toronto | Est des Etats-Unis |
| WDC04 | Washington, DC | Est des Etats-Unis |
| WDC06 | Washington, DC | Est des Etats-Unis |
| WDC07 | Washington, DC | Est des Etats-Unis |
{: caption="Tableau 1. {{site.data.keyword.CloudDataCents_notm}} disponibles pour les instances vCenter Server with Hybridity Bundle" caption-side="top"}

Selon la disponibilité et l'approvisionnement du stock, les {{site.data.keyword.CloudDataCents_notm}} peuvent afficher un indicateur de statut sur la console {{site.data.keyword.vmwaresolutions_short}} pour vous aider à planifier vos déploiements.

| Statut | Détails du statut |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Temporarily Out of Inventory  | L'{{site.data.keyword.CloudDataCent_notm}} n'est pas disponible actuellement. |
| Limited Inventory             | L'{{site.data.keyword.CloudDataCent_notm}} a une disponibilité limitée et la commande risque de ne pas être honorée. |
{: caption="Tableau 2. Indicateurs de statut pour les {{site.data.keyword.CloudDataCents_notm}} lors de la commande d'instances Center Server with Hybridity Bundle" caption-side="top"}

## Sauvegarde des composants de gestion
{: #vc_hybrid_planning-backup-mgmt-components}

Vous êtes chargé de gérer et d'assurer la disponibilité de tous les composants d'instance. Il est fortement recommandé de planifier la sauvegarde ou la haute disponibilité de tous les composants de gestion. Pour plus d'informations, voir [Sauvegarde des composants](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Services pour les instances vCenter Server with Hybridity Bundle
{: #vc_hybrid_planning-addon-services}

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
  * (Facultatif) **Nom d'hôte** : entrez le nom d'hôte à mapper au nom usuel du certificat de l'autorité de certification. HCX on {{site.data.keyword.cloud_notm}} exige que le certificat de l'autorité de certification soit dans un format accepté par NSX Edge. Pour plus d'informations sur les formats de certificat NSX Edge, voir [Importation de certificats SSL](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}.

Vous pouvez commander d'autres services complémentaires pour votre instance en fonction de vos besoins, par exemple, la reprise après incident. Pour plus d'informations, voir [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices).

## Remarques sur la capacité
{: #vc_hybrid_planning-capacity-considerations}

Pour plus d'informations sur la capacité, voir [Mise à l'échelle de la capacité](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Liens connexes
{: #vc_hybrid_planning-related}

* [Présentation de vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Commande d'instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [Extension et réduction de capacité pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [Commande, affichage et retrait de services pour des instances vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)

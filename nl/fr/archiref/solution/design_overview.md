---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Présentation de la conception
{: #design_overview}

{{site.data.keyword.vmwaresolutions_full}} fournit l'automatisation du déploiement des composants de technologie VMware dans les {{site.data.keyword.CloudDataCents_notm}} situés dans le monde entier.

## Offres de la solution
{: #design_overview-offerings}

Les offres de la solution incluent les produits VMware vSphere suivants dans un cluster automatiquement déployé et configuré :
* VMware Cloud Foundation : vSphere ESXi, Platform Services Controller (PSC), VMware vCenter Server Appliance, SDDC Manager, VMware NSX et VMware vSAN.
* VMware vCenter Server : vSphere ESXi, Platform Services Controller (PSC), vCenter Server Appliance, NSX et éventuellement vSAN.

Dans cette conception, une instance est déployée dans un pod d'un {{site.data.keyword.CloudDataCent_notm}} lors de la commande initiale. Après le déploiement initial, vous pouvez étendre votre environnement virtuel dans d'autres pods au sein du même centre de données ou dans d'autres centres de données.

La conception permet l'extension et la contraction automatisées de la capacité virtuelle dans une instance Cloud Foundation ou vCenter Server.

## Composants de VMware on IBM Cloud
{: #design_overview-comp}

Figure 1. Composants de VMware on {{site.data.keyword.cloud_notm}}
![Composants de VMware on {{site.data.keyword.cloud_notm}}](design_overview.svg "La solution est constituée d'une infrastructure physique, d'une infrastructure virtuelle, d'une gestion d'infrastructure et de services communs.")

## Liens connexes
{: #design_overview-related}

* [Conception d'infrastructure physique](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [Conception d'infrastructure virtuelle](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [Conception des services communs](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)
* [Conception de gestion d'infrastructure](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)

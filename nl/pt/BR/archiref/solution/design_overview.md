---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# Visão geral do design
{: #design_overview}

O {{site.data.keyword.vmwaresolutions_full}} fornece automação para implementar componentes de tecnologia VMware no {{site.data.keyword.CloudDataCents_notm}} em todo o mundo.

## Ofertas de solução
{: #design_overview-offerings}

As ofertas de solução incluem os produtos do VMware vSphere a seguir dentro de um cluster implementado e configurado automaticamente:
* VMware Cloud Foundation: vSphere ESXi, Platform Services Controller (PSC), VMware vCenter Server Appliance, SDDC Manager, VMware NSX e VMware vSAN.
* VMware vCenter Server: vSphere ESXi, Platform Services Controller (PSC), vCenter Server Appliance, NSX e opcionalmente vSAN.

Nesse design, uma instância é implementada em um único pod de um {{site.data.keyword.CloudDataCent_notm}} na ordem inicial. Após a implementação inicial, é possível ampliar seu ambiente virtual em outros pods dentro do mesmo data center ou em outros data centers.

O design também permite expansão e contração automatizadas de capacidade virtual em uma instância do Cloud Foundation ou do vCenter Server.

## VMware em componentes do IBM Cloud
{: #design_overview-comp}

Figura 1. Componentes do VMware no {{site.data.keyword.cloud_notm}}
![Componentes do VMware no {{site.data.keyword.cloud_notm}}](design_overview.svg "A solução inclui infraestrutura física, infraestrutura virtual, gerenciamento de infraestrutura e serviços comuns.")

## Links relacionados
{: #design_overview-related}

* [ Design da infraestrutura física ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [ Design de infraestrutura virtual ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [ Design de serviços comuns ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)
* [ Design de gerenciamento de infraestrutura ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_infrastructuremgmt)

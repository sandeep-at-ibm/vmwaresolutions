---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: planning vSphere, data center, vSphere data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisitos e planejamento para o VMware vSphere on IBM Cloud
{: #vs_planning}

Revise os requisitos a seguir antes de pedir o VMware vSphere on {{site.data.keyword.cloud}}. Planeje seus clusters do VMware vSphere com base no local do {{site.data.keyword.CloudDataCent_notm}} e nos requisitos de capacidade da carga de trabalho.

Você é responsável por configurar o ambiente, instalar e configurar vários componentes do VMware depois que os servidores ESXi são implementados. Os exemplos a seguir são componentes do VMware: VMware vCenter Server, VMware NSX e VMware vSAN.
{:note}

## Requisitos da conta do IBM Cloud
{: #vs_planning-account-req}

A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, consulte [Requisitos da conta do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## Disponibilidade do data center do IBM Cloud
{: #vs_planning-dc-availability}

A implementação do vSphere tem requisitos rigorosos na infraestrutura física. Portanto, é possível implementar clusters apenas no {{site.data.keyword.CloudDataCents_notm}} que atende aos requisitos. Os seguintes {{site.data.keyword.CloudDataCent_notm}} estão disponíveis para implementação do vSphere.

Os {{site.data.keyword.baremetal_short}} Cascade Lake estão disponíveis nos
{{site.data.keyword.CloudDataCents_notm}} de região de multizona. Para obter mais informações, consulte [Visão geral da região de multizona (MZR)
](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview).

Se você selecionar um componente vSAN, a lista de locais será filtrada pela disponibilidade de SSD (Disco de Estado Sólido).
{:note}

| {{site.data.keyword.CloudDataCent_notm}} | Localização | Região |
|:----------------------|:---------|:---------------|
| AMS03 | Amsterdã | Europa |
| CHE01 | Chennai | Ásia-Pacífico |
| DAL09 | Dallas | NA Sul |
| DAL10 | Dallas | NA Sul |
| DAL12 | Dallas | NA Sul |
| DAL13 | Dallas | NA Sul |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| FRA05 | Frankfurt | Europa |
| HKG02 | Hong Kong | Ásia-Pacífico |
| LON02 | Londres | Europa |
| LON04 | Londres | Europa |
| LON05 | Londres | Europa |
| LON06 | Londres | Europa |
| MEL01 | Melbourne | Ásia-Pacífico |
| MEX01 | Querétaro | NA Sul |
| MIL01 | Milão | Europa |
| MON01 | Montreal | NA Leste |
| OSL01 | Oslo | Europa |
| PAR01 | Paris | Europa |
| SAO01 | São Paulo | América do Sul |
| SEO01 | Seul | Ásia-Pacífico |
| SJC03 | São José | Oeste ND |
| SJC04 | São José | Oeste ND |
| SNG01 | Cingapura | Ásia-Pacífico |
| SYD01 | Sydney | Ásia-Pacífico |
| SYD04 | Sydney | Ásia-Pacífico |
| TOK02 | Tóquio | Ásia-Pacífico |
| TOK04 | Tóquio | Ásia-Pacífico |
| TOR01 | Toronto | NA Leste |
| WDC04 | Washington, DC | NA Leste |
| WDC06 | Washington, DC | NA Leste |
| WDC07 | Washington, DC | NA Leste |
{: caption="Tabela 1. Disponível {{site.data.keyword.CloudDataCents_notm}} para clusters do vSphere" caption-side="top"}

## Links relacionados
{: #vs_planning-related}

* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Ajustando a escala de clusters existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [Ajustando a escala dos clusters existentes criados fora do console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

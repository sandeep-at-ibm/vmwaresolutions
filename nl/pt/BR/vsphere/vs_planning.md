---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Requisitos e planejamento para o VMware vSphere on IBM Cloud

Revise os requisitos a seguir antes de pedir o VMware vSphere on {{site.data.keyword.cloud}}. Planeje seus clusters do VMware vSphere com base no local do {{site.data.keyword.CloudDataCent_notm}} e nos requisitos de capacidade da carga de trabalho.

**Nota**: você é responsável por configurar o ambiente, instalar e configurar vários componentes do VMware depois que os servidores ESXi forem implementados. Esses componentes são: VMware vCenter Server, VMware NSX e VMware vSAN.

## Requisitos da conta do IBM Cloud

A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos para a conta do {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidade do data center do IBM Cloud

A implementação do vSphere tem requisitos rigorosos na infraestrutura física. Portanto, é possível implementar clusters apenas no {{site.data.keyword.CloudDataCents_notm}} que atende aos requisitos. Os seguintes {{site.data.keyword.CloudDataCent_notm}} estão disponíveis para implementação do vSphere.

**Nota:** se você selecionar um componente vSAN, a lista de local será filtrada por disponibilidade de SSD (Solid State Disk).

Tabela 1. Disponível {{site.data.keyword.CloudDataCents_notm}} para clusters do vSphere

| {{site.data.keyword.CloudDataCent_notm}} | Localização | Região |
|:----------------------|:---------|:-------|
| AMS03 | Amsterdã | Europa |
| CHE01 | Chennai | Ásia Pacífico |
| DAL09 | Dallas | NA Sul |
| DAL10 | Dallas | NA Sul |
| DAL12 | Dallas | NA Sul |
| DAL13 | Dallas | NA Sul |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| HKG02 | Hong Kong | Ásia Pacífico |
| LON02 | Londres | Europa |
| LON04 | Londres | Europa |
| LON06 | Londres | Europa |
| MEL01 | Melbourne | Ásia Pacífico |
| MEX01 | Querétaro | NA Sul |
| MIL01 | Milão | Europa |
| MON01 | Montreal | NA Leste |
| OSL01 | Oslo | Europa |
| PAR01 | Paris | Europa |
| SAO01 | São Paulo | América do Sul |
| SEO01 | Seul | Ásia Pacífico |
| SJC03 | São José | Oeste ND |
| SJC04 | São José | Oeste ND |
| SNG01 | Cingapura | Ásia Pacífico |
| SYD01 | Sydney | Ásia Pacífico |
| SYD04 | Sydney | Ásia Pacífico |
| TOK02 | Tóquio | Ásia Pacífico |
| TOR01 | Toronto | NA Leste |
| WDC04 | Washington, DC | NA Leste |
| WDC06 | Washington, DC | NA Leste |
| WDC07 | Washington, DC | NA Leste |

## Links relacionados

* [Pedindo novos clusters do vSphere](vs_orderinginstances.html)
* [Ajustando a escala de clusters existentes](vs_scalingexistingclusters.html)
* [Ajustando a escala dos clusters existentes criados fora do console](vs_orderingforclustersoutside.html)

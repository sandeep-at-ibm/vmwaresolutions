---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-28"

---

# Requisitos e planejamento para instâncias do Cloud Foundation

Revise os requisitos a seguir antes de pedir suas instâncias do VMware Cloud Foundation. Planeje sua instância com base no local do {{site.data.keyword.CloudDataCent}}, nos requisitos de capacidade de carga de trabalho e nos requisitos de serviço.

## Requisitos da conta do IBM Cloud

A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos para a conta do {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidade do data center do IBM Cloud

A implementação do Cloud Foundation tem requisitos rigorosos na infraestrutura física. Portanto, é possível implementar instâncias apenas em {{site.data.keyword.CloudDataCents_notm}} que atendam aos requisitos. Os seguintes {{site.data.keyword.CloudDataCents_notm}} estão disponíveis para implementação do Cloud Foundation:

Tabela 1. Configurações do Bare Metal Server do {{site.data.keyword.CloudDataCents_notm}} e do {{site.data.keyword.cloud_notm}} disponíveis para instâncias do Cloud Foundation

| {{site.data.keyword.CloudDataCent_notm}} | Localização | Região | Configurações do servidor |
|:----------------------|:---------|:-------|:----------------------|
| AMS03 | Amsterdã | Europa | Customizado |
| CHE01 | Chennai | Ásia Pacífico | Customizado |
| DAL09 | Dallas | NA Sul | Customizado |
| DAL10 | Dallas | NA Sul | Customizado, Pequeno, Grande |
| DAL12 | Dallas | NA Sul | Customizado |
| DAL13 | Dallas | NA Sul | Customizado |
| FRA02 | Frankfurt | Europa | Customizado, Grande |
| FRA04 | Frankfurt | Europa | Customizado |
| HKG02 | Hong Kong | Ásia Pacífico | Customizado |
| LON02 | Londres | Europa | Customizado |
| LON04 | Londres | Europa | Customizado |
| LON06 | Londres | Europa | Customizado, Pequeno, Grande |
| MEL01 | Melbourne | Ásia Pacífico | Customizado |
| MEX01 | Querétaro | NA Sul | Customizado |
| MIL01 | Milão | Europa | Customizado |
| MON01 | Montreal | NA Leste | Customizado |
| OSL01 | Oslo | Europa | Customizado |
| PAR01 | Paris | Europa | Customizado |
| SAO01 | São Paulo | América do Sul | Customizado |
| SEO01 | Seul | Ásia Pacífico | Customizado |
| SJC03 | São José | Oeste ND | Customizado |
| SJC04 | São José | Oeste ND | Customizado |
| SNG01 | Cingapura | Ásia Pacífico | Customizado |
| SYD01 | Sydney | Ásia Pacífico | Customizado |
| SYD04 | Sydney | Ásia Pacífico | Customizado |
| TOK02 | Tóquio | Ásia Pacífico | Customizado |
| TOR01 | Toronto | NA Leste | Customizado, Pequeno, Grande |
| WDC04 | Washington, DC | NA Leste | Customizado, Pequeno, Grande |
| WDC06 | Washington, DC | NA Leste | Customizado |
| WDC07 | Washington, DC | NA Leste | Customizado |

Dependendo da disponibilidade e do fornecimento do inventário, o {{site.data.keyword.CloudDataCents_notm}} pode exibir um indicador de status no console do {{site.data.keyword.vmwaresolutions_short}} para ajudá-lo a planejar suas implementações.

Tabela 2. Indicadores de status para o {{site.data.keyword.CloudDataCents_notm}} ao pedir instâncias do Cloud Foundation

| Barra de Status | Detalhes do status |
|:------------------------------|:--------------------------------------------------|
| Em breve                   | O {{site.data.keyword.CloudDataCent_notm}} não está disponível atualmente. |
| Provisoriamente fora do inventário  | O  {{site.data.keyword.CloudDataCent_notm}}  não tem nenhuma disponibilidade atualmente. |
| Inventário limitado             | O {{site.data.keyword.CloudDataCent_notm}} limitou a disponibilidade e o pedido pode não estar concluído. |

## Backup de componentes de gerenciamento

Você é responsável por manter e assegurar a disponibilidade de todos os componentes da instância. Recomenda-se planejar o backup ou a alta disponibilidade de todos os componentes de gerenciamento. Para obter mais informações, consulte [Fazendo backup de componentes](../archiref/solution/solution_backingup.html).

## Serviços para instâncias do Cloud Foundation

É possível pedir serviços complementares para a sua instância com base em suas necessidades, por exemplo, recuperação de desastre. Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](sd_addingremovingservices.html).

## Considerações sobre capacidade

Para obter mais informações sobre capacidade, consulte [Ajustando a escala da capacidade](../archiref/solution/solution_scaling.html).

### Links relacionados

* [Visão geral do Cloud Foundation](sd_cloudfoundationoverview.html)
* [Pedindo instâncias do Cloud Foundation](sd_orderinginstance.html)
* [Expandindo e contraindo capacidade para instâncias do Cloud Foundation](sd_addingremovingservers.html)
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](sd_addingremovingservices.html)

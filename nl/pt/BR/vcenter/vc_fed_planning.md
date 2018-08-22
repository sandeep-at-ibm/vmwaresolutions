---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Requisitos e planejamento para as instâncias do VMware Federal

Revise os seguintes requisitos antes de pedir uma instância do VMware Federal. Planeje sua instância com base em seus requisitos de capacidade da carga de trabalho.

## Requisitos da conta do IBM Cloud

A conta do {{site.data.keyword.cloud}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos para a conta do {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidade do data center do IBM Cloud

A implementação do VMware Federal on {{site.data.keyword.cloud_notm}} tem requisitos rigorosos na infraestrutura física. É possível implementar instâncias do VMware Federal somente nos {{site.data.keyword.CloudDataCents_notm}} a seguir:
- WDC03-Washington, DC, POD2
- DAL08-Dallas, TX, POD2

## Backup de componentes de gerenciamento

Você é responsável por manter e assegurar a disponibilidade de todos os componentes da instância usando sua solução de backup preferencial. É altamente recomendável planejar o backup ou a alta disponibilidade de todos os componentes de gerenciamento. Para obter mais informações, consulte [Fazendo backup de componentes](../archiref/solution/solution_backingup.html).

## Serviços para instâncias do VMware Federal

O VMware Federal on {{site.data.keyword.cloud_notm}} não oferece a opção para pedir serviços adicionais.

## Considerações de capacidade

Para obter informações e considerações de capacidade, consulte [Capacidade de ajuste de escala](../archiref/solution/solution_scaling.html).

### Links relacionados

* [Lista de materiais do software vCenter Server](vc_bom.html)
* [ Federal do VMware em  {{site.data.keyword.cloud_notm}}  visão geral ](vc_fed_overview.html)
* [Pedindo instâncias do VMware Federal](vc_fed_orderinginstance.html)
* [Protegendo instâncias do VMware Federal](vc_fed_securinginstance.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)

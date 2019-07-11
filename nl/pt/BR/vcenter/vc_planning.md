---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

# Requisitos e planejamento para instâncias do vCenter Server
{: #vc_planning}

Revise os seguintes requisitos antes de pedir suas instâncias do VMware vCenter Server. Planeje sua instância com base no local do {{site.data.keyword.CloudDataCent}}, nos requisitos de capacidade de carga de trabalho e nos requisitos de serviço complementares.

## Requisitos da conta do IBM Cloud
{: #vc_planning-account-req}

A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, consulte [Requisitos da conta do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).

## Disponibilidade do data center do IBM Cloud
{: #vc_planning-dc-availability}

A implementação do vCenter Server tem requisitos rigorosos na infraestrutura física. Portanto, é possível implementar instâncias apenas em {{site.data.keyword.CloudDataCents_notm}} que atendam aos requisitos. Os {{site.data.keyword.CloudDataCents_notm}} a seguir estão disponíveis para implementação do vCenter Server:

Tabela 1. {{site.data.keyword.CloudDataCents_notm}} disponível para instâncias do vCenter Server

| {{site.data.keyword.CloudDataCent_notm}} | Localização | Região | Opções do servidor |
|:----------------------|:---------|:-------|:---------------|
| AMS03 | Amsterdã | Europa | Skylake, Broadwell |
| CHE01 | Chennai | Ásia-Pacífico | Skylake, certificado pelo SAP, Broadwell |
| DAL09 | Dallas | NA Sul | Skylake, certificado pelo SAP, Broadwell |
| DAL10 | Dallas | NA Sul | Skylake, certificado pelo SAP, Broadwell |
| DAL12 | Dallas | NA Sul | Skylake, certificado pelo SAP, Broadwell |
| DAL13 | Dallas | NA Sul | Skylake, certificado pelo SAP, Broadwell |
| FRA02 | Frankfurt | Europa | Skylake, certificado pelo SAP, Broadwell |
| FRA04 | Frankfurt | Europa | Skylake, certificado pelo SAP, Broadwell |
| FRA05 | Frankfurt | Europa | Skylake, Broadwell |
| HKG02 | Hong Kong | Ásia-Pacífico | Skylake, Broadwell |
| LON02 | Londres | Europa | Skylake, Broadwell |
| LON04 | Londres | Europa | Skylake, certificado pelo SAP, Broadwell |
| LON05 | Londres | Europa | Skylake, Broadwell |
| LON06 | Londres | Europa | Skylake, certificado pelo SAP, Broadwell |
| MEL01 | Melbourne | Ásia-Pacífico | Skylake, certificado pelo SAP, Broadwell |
| MEX01 | Querétaro | NA Sul | Skylake, certificado pelo SAP, Broadwell |
| MIL01 | Milão | Europa | Skylake, certificado pelo SAP, Broadwell |
| MON01 | Montreal | NA Leste | Skylake, certificado pelo SAP, Broadwell |
| OSL01 | Oslo | Europa | Skylake, Broadwell |
| PAR01 | Paris | Europa | Skylake, Broadwell |
| SAO01 | São Paulo | América do Sul | Skylake, certificado pelo SAP, Broadwell |
| SEO01 | Seul | Ásia-Pacífico | Skylake, certificado pelo SAP, Broadwell |
| SJC03 | São José | Oeste ND | Skylake, Broadwell |
| SJC04 | São José | Oeste ND | Skylake, Broadwell |
| SNG01 | Cingapura | Ásia-Pacífico | Skylake, Broadwell |
| SYD01 | Sydney | Ásia-Pacífico | Skylake, Broadwell |
| SYD04 | Sydney | Ásia-Pacífico | Skylake, certificado pelo SAP, Broadwell |
| TOK02 | Tóquio | Ásia-Pacífico | Skylake, certificado pelo SAP, Broadwell |
| TOR01 | Toronto | NA Leste | Skylake, certificado pelo SAP, Broadwell |
| WDC04 | Washington, DC | NA Leste | Skylake, certificado pelo SAP, Broadwell |
| WDC06 | Washington, DC | NA Leste | Skylake, certificado pelo SAP, Broadwell |
| WDC07 | Washington, DC | NA Leste | Skylake, certificado pelo SAP, Broadwell |

Dependendo da disponibilidade e do fornecimento do inventário, o {{site.data.keyword.CloudDataCents_notm}} pode exibir um indicador de status no console do {{site.data.keyword.vmwaresolutions_short}} para ajudá-lo a planejar suas implementações.

Tabela 2. Indicadores de status para {{site.data.keyword.CloudDataCents_notm}} ao pedir instâncias do vCenter Server

| Barra de Status | Detalhes do status |
|:------------------------------|:--------------------------------------------------|
| Em breve                   | O {{site.data.keyword.CloudDataCent_notm}} não está disponível atualmente. |
| Provisoriamente fora do inventário  | O  {{site.data.keyword.CloudDataCent_notm}}  não tem nenhuma disponibilidade atualmente. |
| Inventário limitado             | O {{site.data.keyword.CloudDataCent_notm}} limitou a disponibilidade e o pedido pode não estar concluído. |

## Backup de componentes de gerenciamento
{: #vc_planning-backup-mgmt-components}

Você é responsável por manter e assegurar a disponibilidade de todos os componentes da instância. É altamente recomendável planejar o backup ou a alta disponibilidade de todos os componentes de gerenciamento. Para obter mais informações, consulte [Fazendo backup de componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

## Serviços para instâncias do vCenter Server
{: #vc_planning-addon-services}

É possível pedir serviços complementares para a sua instância com base em suas necessidades, por exemplo, recuperação de desastre. Para obter mais informações, veja [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

Os serviços são suportados para instâncias do vCenter Server com NSX-T.
{:note}

## Considerações sobre capacidade
{: #vc_planning-capacity-considerations}

Para obter mais informações sobre considerações de capacidade, consulte [Capacidade de ajuste de escala](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling).

## Links relacionados
{: #vc_planning-related}

* [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)

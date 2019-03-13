---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a liberação para V2.0
{: #relnotes_v20}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud

O serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} está agora disponível para instâncias V2.0 e mais recente do VMware Cloud Foundation V2.0 e do VMware vCenter Server. Este serviço implementa um par de alta disponibilidade (HA) do FortiGate Virtual Appliances para o seu ambiente, que pode ajudá-lo a reduzir o risco implementando controles de segurança críticos em sua infraestrutura virtual.

Peça instâncias com o serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} incluído ao pedir sua instância ou inclua esse serviço em suas instâncias existentes posteriormente por meio da guia **Serviços** na página de detalhes da instância. Dependendo de seus requisitos, selecione um dos três tamanhos de implementação e as opções de licenciamento para esse serviço. Depois que o serviço for instalado com êxito, gerencie e configure regras de firewall para os FortiGate Virtual Appliances por meio do console do FortiGate.

Para obter mais informações, veja os tópicos a seguir:
* [ Componentes e considerações para o FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [Gerenciando o FortiGate Virtual Appliance no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)

## Instalação de vários serviços para o F5 on IBM Cloud e o FortiGate Virtual Appliance on IBM Cloud

Agora é possível instalar múltiplas instâncias do serviço F5 on {{site.data.keyword.cloud_notm}} e do serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} para uma instância do Cloud Foundation ou uma instância do vCenter Server. Quando você seleciona o serviço F5 ou o serviço FortiGate durante o pedido de instância, deve-se especificar um nome para a instância de serviço para distingui-lo das instâncias de serviço adicionais que forem instaladas posteriormente.

Depois que a implementação da instância for concluída, será possível incluir mais instâncias do serviço F5 ou FortiGate instalando o serviço na guia **Incluir Serviços** da página de detalhes da instância. É possível incluir apenas uma instância de serviço de cada vez e deve-se repetir o processo para todas as instâncias que desejar incluir para um serviço.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservices)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)

## Atualizações para o FortiGate Security Appliance on IBM Cloud

Nesta liberação, o serviço Fortinet on {{site.data.keyword.cloud_notm}} foi renomeado para FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}. O par de FortiGate Security Appliances (FSAs) do serviço foi configurado para ser seguro por padrão ao ser implementado em sua instância.
* Se você implementar um par de FSAs como parte de uma nova instância do Cloud Foundation ou do vCenter Server, os FSAs serão configurados para permitir apenas as comunicações de saída necessárias de sua instância para a rede pública e negar todas as outras comunicações.
* Se você implementar um par de FSAs como parte de uma instância existente do Cloud Foundation ou do vCenter Server, os FSAs serão configurados com uma regra explícita para permitir todas as comunicações de gerenciamento de saída necessárias de sua instância para a rede pública e os FSAs também serão configurados com uma regra para permitir que todas as outras comunicações assegurem que o tráfego de aplicativo existente não seja interrompido.

Em todos os casos, deve-se gerenciar a configuração dos FSAs cuidadosamente para permitir apenas as comunicações necessárias e negar todas as outras comunicações.

## Consistência do formato do nome completo do domínio

O nome completo do domínio (FQDN) agora é representado de maneira consistente para todas as instâncias. Ao fazer um pedido, é possível inserir seu próprio prefixo de subdomínio e prefixo de nome de host para assegurar que a convenção da indústria para o formato FQDN seja seguida. Por exemplo, `host-name-prefix<n>.subdomain-prefix.domain-name`.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Estimativas de carga de trabalho e armazenamento durante um pedido de instância

* Durante uma ordem do VMware vSphere on {{site.data.keyword.cloud_notm}}, é fornecida uma estimativa de quantas máquinas virtuais podem ser executadas na instância pedida.
* Durante um pedido do Cloud Foundation e do vCenter Server, é fornecida a você uma estimativa da capacidade de armazenamento utilizável para a instância pedida.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Atualizações para instâncias do VMware Cloud Foundation

A liberação atual se aplica às seguintes atualizações de componentes e melhorias para novas implementações:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Liberação de correção ESXi650-201710401-BG. As atualizações esx-base, esx-tboot, vsan e vsanhealth VIBs (2151061). Para obter mais informações sobre detalhes das correções, consulte [Correções de segurança do S.O. Photon do VMware vCenter Server Appliance](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}.

As instâncias existentes (das liberações V1.9 e anteriores) não podem ser atualizadas para as versões do componente nessa lista.
{:note}

Para obter mais informações sobre os componentes, consulte [Visão geral do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview).

### Suporte de cluster para instâncias do Cloud Foundation

Agora, é possível usar clusters para gerenciar servidores ESXi em instâncias do Cloud Foundation que são implementadas na V2.0 e liberações mais recentes para um melhor gerenciamento de recursos e alta disponibilidade. Os servidores ESXi que você configurou quando pediu uma instância são agrupados como **SDDC-Cluster** por padrão.

É possível visualizar os detalhes do cluster ou incluir até um total de cinco clusters em uma instância na guia **Infraestrutura** da página de detalhes da instância. Quando você estiver expandindo ou contraindo a capacidade de uma instância, será possível selecionar em qual cluster incluir ou de qual cluster remover servidores ESXi. Para obter mais informações, veja [Incluindo e visualizando clusters para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-adding-and-viewing-clusters-for-cloud-foundation-instances).

### Suporte para armazenamento vSAN customizado para instâncias do Cloud Foundation

Agora, é possível customizar a configuração de armazenamento vSAN selecionando o número e o tamanho das unidades de armazenamento vSAN como parte do seu pedido de instância.

Para obter mais informações, veja os tópicos a seguir:

* [Visão geral do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)

### Opção de edição de licença vSAN do VMware para instâncias do Cloud Foundation: Advanced ou Enterprise

Agora, é possível selecionar a edição de licença vSAN que você deseja durante o pedido da instância do Cloud Foundation. É possível comprar a licença como parte de seu pedido ou Bring Your Own License (BYOL). Para obter mais informações, veja [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance).

### Novas configurações padronizadas do IBM Bare Metal Server para instâncias do Cloud Foundation

As seguintes definições de configuração do Bare Metal Server estão disponíveis:
* Pequeno (Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz/128 GB de RAM/12 discos)
* Grande (Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM/12 discos)

O chassi tem espaço para 12 discos. Nem todos os slots estão preenchidos. A configuração **Pequeno** fornece duas unidades 5100 MAX Micron de 1,9 TB e a configuração **Grande** fornece quatro unidades 5100 PRO Micron de 3,8 TB.
{:note}

Para obter mais informações, veja os tópicos a seguir:
* [Visão geral do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)

## Atualizações para instâncias do VMware vCenter Server

A liberação atual se aplica às seguintes atualizações de componentes para novas implementações:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

As ordens customizadas do vCenter Server com ou sem o componente VMware vSAN sempre incluem um servidor de chassi de 12 discos. Esse servidor resulta em um custo um pouco maior para o {{site.data.keyword.baremetal_short}} para o caso de pedido não vSAN no PDF de estimativa de preço.
{:note}

Para obter mais informações sobre os componentes, consulte [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview).

### Suporte de configuração de vários sites para instâncias do vCenter Server

Agora, é possível implementar uma única instância do vCenter Server além das instâncias secundárias que estão conectadas a uma instância primária. O modelo de configuração multisite usa uma topologia hub-and-spoke com um site primário e um máximo de sete sites secundários.

Para obter mais informações, veja [Configuração de vários sites para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_multisite).

### Suporte para armazenamento vSAN customizado para instâncias do vCenter Server

Agora, o armazenamento vSAN está disponível em instâncias do vCenter Server para as instâncias primária e secundária. Fica disponível apenas durante a seleção de uma configuração customizada pelo usuário. É possível selecionar a edição de licença vSAN (Advanced ou Enterprise) que você deseja durante o pedido da instância do vCenter Server. É possível comprar a licença como parte de seu pedido ou Bring Your Own License (BYOL).

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

### Bring Your Own License (BYOL) para instâncias do VMware vCenter Server

O BYOL está disponível para instâncias do vCenter Server. Use uma ou mais de suas próprias licenças do vCenter Server, do vSphere, do vSAN e do NSX VMware ao pedir instâncias do vCenter Server.

Para obter mais informações, veja os tópicos a seguir:
* [Pedindo instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_orderinginstance)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)

## Atualizações para o VMware vSphere on IBM Cloud

### Novos tipos de discos para Bare Metal Servers

Para o componente vSAN do VMware, os seguintes tipos de discos estão disponíveis para o {{site.data.keyword.baremetal_short}}:
* SSD SED de 960 GB
* SSD SED de 1,9 TB
* SSD SED de 3,8 TB

**Notas**:
* As unidades SSD SED de 3,8 TB serão suportadas quando forem disponibilizadas geralmente em um {{site.data.keyword.CloudDataCent_notm}}.
* Os pedidos com ou sem o componente VMware vSAN sempre incluem um servidor de chassi de 12 discos. Esse servidor resulta em um custo um pouco maior para o {{site.data.keyword.baremetal_short}} para o caso de pedido não vSAN no PDF de estimativa de preço.

Para obter mais informações, veja [Pedindo novos clusters vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances).

## Atualizações para o NetApp ONTAP Select on IBM Cloud

### Novas opções do servidor bare metal

As seguintes opções de configuração do servidor bare metal estão disponíveis:
* **Alto desempenho (Médio)** – Licença Premium/Dual Intel Xeon E5-2650 v4 (total de 24 núcleos, 2.2 GHz)/128 GB de RAM/Capacidade de 22 unidades SSD de 1,9 TB por nó/Capacidade efetiva de um cluster de 4 nós – 59 TB
* **Alto desempenho (Grande)** – Licença Premium/Dual Intel Xeon E5-2650 v4 (total de 24 núcleos, 2.2 GHz)/128 GB de RAM/Capacidade de 22 unidades SSD de 3,8 TB por nó/Capacidade efetiva de um cluster de 4 nós – 118 TB
* **Alta capacidade** - Licença padrão/Dual Intel Xeon E5-2650 v4 (total de 24 núcleos, 2.2 GHz)/64 GB de RAM/Capacidade de dez unidades SATA de 4 TB por nó/Capacidade efetiva de um cluster de 4 nós - 60 TB

As unidades SSD de 3,8 TB são suportadas quando elas são geralmente disponibilizadas em um {{site.data.keyword.CloudDataCent_notm}}.
{:note}

Para obter mais informações, veja os tópicos a seguir:
* [Visão geral do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)
* [Pedindo instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## Documentação nova e atualizada

Os usuários do VMware Cloud Foundation podem usar instruções passo a passo, junto à plataforma NSX do VMware, no {{site.data.keyword.cloud_notm}} para permitir que as máquinas virtuais se comuniquem entre si e com a Internet. Para obter mais informações, veja [Configurando o NSX para MVs de carga de trabalho no VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Atualizações e aprimoramentos da interface com o usuário

* O número máximo de servidores ESXi que podem ser incluídos em um cluster é atualizado para 32 servidores. O número máximo de clusters continua a ser cinco.
* Na página **Instâncias implementadas**, a coluna **Servidores ESXi** nas tabelas de resumo da instância é substituída pela coluna **Versão**, na qual é possível localizar a versão de liberação na qual as instâncias foram implementadas ou atualizadas.
* A versão do SDDC Manager para instâncias do Cloud Foundation está, agora, disponível na página de detalhes da instância.
* Várias mensagens de erro e aprimoramentos de dicas de ferramenta estão disponíveis para ajudá-lo na seleção da configuração apropriada na interface com o usuário.

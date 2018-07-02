---

copyright:

  years:  2016, 2018

lastupdated: "2017-11-20"

---

# Notas sobre a liberação para V2.0

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em liberações diferentes, problemas conhecidos com o produto e dicas adicionais para usar o {{site.data.keyword.vmwaresolutions_full}}, veja o [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## FortiGate Virtual Appliance on IBM Cloud

O serviço FortiGate Virtual Appliance on IBM Cloud está, agora, disponível para instâncias do VMware Cloud Foundation e do VMware vCenter Server V2.0 e mais recente. Este serviço implementa um par de alta disponibilidade (HA) do FortiGate Virtual Appliances para o seu ambiente, que pode ajudá-lo a reduzir o risco implementando controles de segurança críticos em sua infraestrutura virtual.

É possível pedir instâncias com o serviço FortiGate Virtual Appliance on IBM Cloud incluído quando você pede suas instâncias ou incluir esse serviço em suas instâncias existentes posteriormente na guia **Serviços** na página de detalhes da instância. Dependendo de seus requisitos, é possível selecionar um dos três tamanhos de implementação e opções de licenciamento para este serviço. Depois que o serviço for instalado com êxito, será possível gerenciar e configurar regras de firewall para o FortiGate Virtual Appliances do console do FortiGate.

Para obter mais informações, veja:
* [Componentes e considerações para o FortiGate Virtual Appliance on IBM Cloud](../services/fortinetvm_considerations.html)
* [Gerenciando o FortiGate Virtual Appliance on IBM Cloud](../services/managingfortinetvm.html)

## Instalação de vários serviços para o F5 on IBM Cloud e o FortiGate Virtual Appliance on IBM Cloud

Agora, é possível instalar várias instâncias do serviço F5 on IBM Cloud e do serviço FortiGate Virtual Appliance on IBM Cloud para uma instância do Cloud Foundation ou do vCenter Server. Ao selecionar o serviço F5 ou o serviço FortiGate durante o pedido da instância, deve-se especificar um nome para a instância do serviço para distingui-la das instâncias de serviço adicionais que você instalar mais tarde.

Depois que a implementação da instância for concluída, será possível incluir mais instâncias do serviço F5 ou FortiGate instalando o serviço na guia **Incluir Serviços** da página de detalhes da instância. É possível incluir apenas uma instância de serviço de cada vez e deve-se repetir o processo para todas as instâncias que desejar incluir para um serviço.

Para obter mais informações, veja:
* [Pedindo, visualizando e removendo serviços para instâncias do Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Pedindo, visualizando e removendo serviços para instâncias do vCenter Server](../vcenter/vc_addingremovingservices.html)

## Atualizações para o FortiGate Security Appliance on IBM Cloud

Nesta liberação, o serviço Fortinet on IBM Cloud é renomeado para FortiGate Security Appliance on IBM Cloud e o par do FortiGate Security Appliances (FSAs) do serviço é configurado para ser seguro por padrão quando eles são implementados em sua instância:
* Se você implementar um par de FSAs como parte de uma nova instância do Cloud Foundation ou do vCenter Server, os FSAs serão configurados para permitir apenas as comunicações de saída necessárias de sua instância para a rede pública e negar todas as outras comunicações.
* Se você implementar um par de FSAs como parte de uma instância existente do Cloud Foundation ou do vCenter Server, os FSAs serão configurados com uma regra explícita para permitir que todas as comunicações necessárias de gerenciamento de saída de sua instância para a rede pública e os FSAs também serão configurados com uma regra adicionais para permitir todas as outras comunicações para assegurar que o tráfego de aplicativo existente não seja interrompido.

Em todos os casos, deve-se gerenciar a configuração dos FSAs cuidadosamente para permitir apenas as comunicações necessárias e negar todas as outras comunicações.

## Consistência do formato do nome completo do domínio

Agora, o nome completo do domínio (FQDN) é representado de maneira consistente para todas as instâncias. Ao fazer um pedido, é possível inserir o seu próprio prefixo de subdomínio e o prefixo de nome do host. Isso assegura que a convenção da indústria para o formato FQDN seja seguido, como `host-name-prefix<n>.subdomain-prefix.domain-name`.

Para obter mais informações, veja:
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html)

## Estimativas de carga de trabalho e de armazenamento durante o pedido da instância

* Durante um pedido do VMware vSphere on IBM Cloud, é fornecida a você uma estimativa de quantas máquinas virtuais podem ser executadas na instância pedida.
* Durante um pedido do Cloud Foundation e do vCenter Server, é fornecida a você uma estimativa da capacidade de armazenamento utilizável para a instância pedida.

Para obter mais informações, veja:
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html)

## Atualizações para instâncias do VMware Cloud Foundation

A liberação atual se aplica às seguintes atualizações de componentes e melhorias para novas implementações:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware SDDC Manager 2.4
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4
* VMware ESXi 6.5, Liberação de Correção ESXi650-201710401-BG: Atualizações esx-base, esx-tboot, vsan e vsanhealth VIBs (2151061). Para obter detalhes da correção, veja [VMware vCenter Server Appliance Photon OS Security Patches](https://docs.vmware.com/en/VMware-vSphere/6.5/rn/vcenter-server-appliance-photonos-security-patches.html){:new_window}.

**Nota**: as instâncias existentes (das liberações V1.9 e anterior) não podem ser submetidas a upgrade para as versões de componentes nessa lista.

Para obter mais informações sobre componentes, veja [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html).

### Suporte de cluster para instâncias do Cloud Foundation

Agora, é possível usar clusters para gerenciar servidores ESXi em instâncias do Cloud Foundation que são implementadas na V2.0 e liberações mais recentes para um melhor gerenciamento de recursos e alta disponibilidade. Os servidores ESXi que você configurou quando pediu uma instância são agrupados como **SDDC-Cluster** por padrão.

É possível visualizar os detalhes do cluster ou incluir até um total de cinco clusters em uma instância na guia **Infraestrutura** da página de detalhes da instância. Quando você estiver expandindo ou contraindo a capacidade de uma instância, será possível selecionar em qual cluster incluir ou de qual cluster remover servidores ESXi. Para obter mais informações, veja [Incluindo e visualizando clusters para instâncias do Cloud Foundation](../sddc/sd_addingviewingclusters.html).

### Suporte para armazenamento vSAN customizado para instâncias do Cloud Foundation

Agora, é possível customizar a configuração de armazenamento vSAN selecionando o número e o tamanho das unidades de armazenamento vSAN como parte do seu pedido de instância.

Para obter mais informações, veja:
* [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)

### Opção de edição de licença vSAN do VMware para instâncias do Cloud Foundation: Advanced ou Enterprise

Agora, é possível selecionar a edição de licença vSAN que você deseja durante o pedido da instância do Cloud Foundation. É possível comprar a licença como parte de seu pedido ou Bring Your Own License (BYOL). Para obter mais informações, veja [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html).

### Novas configurações padronizadas do IBM Bare Metal Server para instâncias do Cloud Foundation

As seguintes definições de configuração do Bare Metal Server estão disponíveis:
* Pequeno (Dual Intel Xeon E5-2650 v4/total de 24 núcleos, 2.2 GHz/128 GB de RAM/12 discos)
* Grande (Dual Intel Xeon E5-2690 v4/total de 28 núcleos, 2.6 GHz/512 GB de RAM/12 discos)

**Nota**: o chassi tem espaço para 12 discos, no entanto, nem todos os slots são preenchidos. A configuração **Pequeno** fornece duas unidades 5100 MAX Micron de 1,9 TB e a configuração **Grande** fornece quatro unidades 5100 PRO Micron de 3,8 TB.

Para obter mais informações, veja:
* [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)

## Atualizações para instâncias do VMware vCenter Server

A liberação atual se aplica às seguintes atualizações de componentes para novas implementações:

* VMware vSphere Enterprise Plus 6.5u1 (5969303)
* VMware vCenter Server 6.5U1a
* VMware vSAN 6.6.1
* VMware NSX for vSphere 6.3.4

**Nota:** pedidos customizados do vCenter Server com ou sem o componente vSAN do VMware sempre incluem um servidor do chassi de 12 discos que reflete um custo um pouco maior para o {{site.data.keyword.baremetal_short}} para o caso de pedido não vSAN no PDF de estimativa de preço.

Para obter mais informações sobre componentes, veja [Visão geral do vCenter Server](../vcenter/vc_vcenterserveroverview.html).

### Suporte de configuração de vários sites para instâncias do vCenter Server

Agora, é possível implementar uma única instância do vCenter Server além das instâncias secundárias que estão conectadas a uma instância primária. O modelo de configuração de vários sites usa uma topologia de hub e spoke com um site primário e um máximo de 7 sites secundários.

Para obter mais informações, veja [Configuração de vários sites para instâncias do vCenter Server](../vcenter/vc_multisite.html).

### Suporte para armazenamento vSAN customizado para instâncias do vCenter Server

Agora, o armazenamento vSAN está disponível em instâncias do vCenter Server para as instâncias primária e secundária. Ele está disponível apenas ao selecionar uma configuração customizada pelo usuário. É possível selecionar a edição de licença vSAN (Advanced ou Enterprise) que você deseja durante o pedido da instância do vCenter Server. É possível comprar a licença como parte de seu pedido ou Bring Your Own License (BYOL).

Para obter mais informações, veja [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html).

### Bring Your Own License (BYOL) para instâncias do VMware vCenter Server

O BYOL está disponível para instâncias do vCenter Server. O BYOL permite usar uma ou mais de suas próprias licenças do vCenter Server, vSphere, vSAN e NSX VMware ao pedir instâncias do vCenter Server.

Para obter mais informações, veja:
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Pedindo novos clusters do vSphere](../vsphere/vs_orderinginstances.html)

## Atualizações para o VMware vSphere on IBM Cloud

### Novos tipos de discos para Bare Metal Servers

Para o componente vSAN do VMware, os seguintes tipos de discos estão disponíveis para o {{site.data.keyword.baremetal_short}}:
* SSD SED de 960 GB
* SSD SED de 1,9 TB
* SSD SED de 3,8 TB

**Notas:**
* Unidades SSD SED de 3,8 TB serão suportadas quando forem disponibilizadas geralmente em um data center.
* Pedidos com ou sem o componente vSAN do VMware sempre incluem um servidor de chassi de 12 discos que reflete um custo um pouco maior para o {{site.data.keyword.baremetal_short}} para o caso de um pedido não vSAN no PDF de estimativa de preço.

Para obter mais informações, veja [Pedindo novos clusters vSphere](../vsphere/vs_orderinginstances.html).

## Atualizações para o NetApp ONTAP Select on IBM Cloud

### Novas opções do servidor bare metal

As seguintes opções de configuração do servidor bare metal estão disponíveis:
* **Alto desempenho (Médio)** – Licença completa/Dual Intel Xeon E5-2650 v4 (Total de 24 núcleos, 2,2 GHz)/128 GB de RAM/Capacidade de vinte e duas unidades SSD de 1,9 TB por nó/Capacidade efetiva de um cluster de 4 nós – 59 TB
* **Alto desempenho (Grande)** – Licença completa/Dual Intel Xeon E5-2650 v4 (Total de 24 núcleos, 2,2 GHz)/128 GB de RAM/Capacidade de vinte e duas unidades SSD de 3,8 TB por nó/Capacidade efetiva de um cluster de 4 nós – 118 TB
* **Alta capacidade** - Licença padrão/Dual Intel Xeon E5-2650 v4 (total de 24 núcleos, 2.2 GHz)/64 GB de RAM/Capacidade de dez unidades SATA de 4 TB por nó/Capacidade efetiva de um cluster de 4 nós - 60 TB

**Nota:** unidades SSD de 3,8 TB serão suportadas quando elas forem geralmente disponibilizadas em um data center.

Para obter mais informações, veja:
* [Visão geral do NetApp ONTAP Select](../netapp/np_netappoverview.html)
* [Pedindo instâncias do NetApp ONTAP Select](../netapp/np_orderinginstances.html)

## Documentação nova e atualizada

Os usuários do VMware Cloud Foundation podem usar instruções passo a passo junto com a plataforma NSX do VMware no IBM Cloud para permitir que máquinas virtuais se comuniquem umas com as outras e a Internet. Para obter mais informações, veja [Configurando o NSX para VMs de carga de trabalho no VMware Cloud Foundation on IBM Cloud (VCF)](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/){:new_window}.

## Atualizações e aprimoramentos da interface com o usuário

* O número máximo de servidores ESXi que podem ser incluídos em um cluster é atualizado para 32 servidores. O número máximo de clusters continua a ser cinco.
* Na página **Instâncias implementadas**, a coluna **Servidores ESXi** nas tabelas de resumo da instância é substituída pela coluna **Versão**, na qual é possível localizar a versão de liberação na qual as instâncias foram implementadas ou atualizadas.
* A versão do SDDC Manager para instâncias do Cloud Foundation está, agora, disponível na página de detalhes da instância.
* Várias mensagens de erro e aprimoramentos de dica de ferramenta foram feitos para ajudá-lo na seleção da configuração apropriada na interface com o usuário.

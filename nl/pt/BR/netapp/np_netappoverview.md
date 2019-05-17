---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visão geral do NetApp ONTAP Select
{: #np_netappoverview}

Revise a arquitetura e os componentes do NetApp ONTAP Select na implementação do {{site.data.keyword.cloud}}.

## Arquitetura do NetApp ONTAP Select
{: #np_netappoverview-archi}

O NetApp ONTAP Select na oferta do {{site.data.keyword.cloud_notm}} complementa a implementação do vCenter Server fornecendo serviços de virtualização de armazenamento.

O gráfico a seguir ilustra a arquitetura geral do NetApp ONTAP Select na implementação do vCenter Server.

Figura 1. Arquitetura de alto nível do NetApp ONTAP Select no {{site.data.keyword.cloud_notm}}

![Arquitetura do NetApp ONTAP Select](np_architecture.svg "Arquitetura de alto nível do NetApp ONTAP Select no IBM Cloud")

### Infraestrutura física
{: #np_netappoverview-physical-infras}

Essa camada fornece a infraestrutura física (recursos de cálculo, rede e armazenamento) a ser usada pela infraestrutura virtual.

### Infraestrutura de virtualização (Cálculo, Rede e NetApp ONTAP Select)
{: #np_netappoverview-virtual-infras}

Essa camada virtualiza a infraestrutura física por meio dos produtos VMware a seguir e do produto NetApp ONTAP Select:
* O VMware vSphere virtualizará os recursos de cálculo físico
* VMware NSX é a plataforma de virtualização de rede que fornece componentes de rede lógica e redes virtuais.
* O NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} implementa um cluster do ONTAP Select, que consiste em quatro MVs para os quatro hosts.

O gráfico a seguir ilustra os componentes da implementação do NetApp ONTAP Select.

Figura 2. Componentes do NetApp ONTAP Select

![Componentes do NetApp ONTAP Select](np_netappcomponents.svg "Componentes do NetApp ONTAP Select")

### Gerenciamento de virtualização
{: #np_netappoverview-virtualization-mgmt}

A camada de gerenciamento de virtualização consiste nos seguintes componentes:

* vCenter Server Appliance (vCSA) com o Platform Services Controller (PSC) integrado
* Gerenciador NSX
* Dois NSX Edge Services Gateways (ESGs)
* Três NSX Controllers
* Instância do servidor virtual do IBM CloudDriver (VSI)

O NetApp ONTAP Select é executado em um cluster VMware e virtualiza o armazenamento local nos hosts. O NetApp ONTAP Select é implementado no modelo dedicado, em que outras cargas de trabalho não são esperadas compartilhar o cluster com ele. Como resultado, a configuração de hardware do NetApp ONTAP Select na oferta do {{site.data.keyword.cloud_notm}} é dimensionada apenas com base nos requisitos do NetApp ONTAP Select.

## Especificações técnicas para instâncias do NetApp ONTAP Select
{: #np_netappoverview-specs}

Os componentes a seguir estão incluídos em sua instância do NetApp ONTAP Select.

A disponibilidade e a precificação de configurações padronizadas podem variar com base no {{site.data.keyword.CloudDataCent_notm}} selecionado para implementação.
{:note}

### Armazenamento
{: #np_netappoverview-storage}

* Escolha entre **Alto desempenho (Médio)**, **Alto desempenho (Grande)** e **Alta capacidade**
* RAID 5 com hot spare
* Duas unidades SATA 1 TB ESXi OS – RAID 1
* Armazenamento de dados de gerenciamento – 500 GB para MVs de gerenciamento

### Configurações predefinidas
{: #np_netappoverview-preset-config}

Quatro {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} com as opções de configuração a seguir são fornecidos:
* **Alto desempenho (Médio)** – Licença Premium/Dual Intel Xeon E5-2650 v4 (total de 24 núcleos, 2.2 GHz)/128 GB de RAM/Capacidade de 22 unidades SSD de 1,9 TB por nó/Capacidade efetiva de um cluster de 4 nós – 59 TB
* **Alto desempenho (Grande)** – Licença Premium/Dual Intel Xeon E5-2650 v4 (total de 24 núcleos, 2.2 GHz)/128 GB de RAM/Capacidade de 22 unidades SSD de 3,8 TB por nó/Capacidade efetiva de um cluster de 4 nós – 118 TB
* **Alta capacidade** - Licença padrão/Dual Intel Xeon E5-2650 v4 (Total de 24 núcleos, 2,2 GHz)/64 GB de RAM/Capacidade de trinta e quatro unidades SATA de 4 TB por nó/Capacidade efetiva de um cluster de 4 nós – 190 TB

As unidades SSD de 3,8 TB (Disco de estado sólido) são suportadas quando são disponibilizadas geralmente em um data center.
{:note}

### Hardware
{: #np_netappoverview-hardware}

* Três opções de RAM e disco: **Alto desempenho (médio)**, **Alto desempenho (grande)** e **Alta capacidade**
* Duas unidades SATA 1 TB ESXi OS
* Um controlador de disco RAID
* VMware Server Virtualization 6.5

### Rede
{: #np_netappoverview-network}

* Uplinks duais de rede pública e privada de 10 Gbps
* Três VLANs (Virtual LANs): uma VLAN pública e duas VLANs privadas
* Um gateway de serviços do VMware NSX Edge seguro

### Virtual Server Instances
{: #np_netappoverview-vsi}

Duas VSIs (Virtual Server Instances):
* Um VSI para o Active Directory (AD) da Microsoft e serviços do Sistema de Nomes de Domínio (DNS).
* Um VSI for IBM CloudBuilder, que será encerrado depois que a implementação da instância for concluída.

### Licenças e taxas
{: #np_netappoverview-license-and-fee}

*  Quatro licenças Premium ou Standard Edition do NetApp ONTAP Select (fornecidas pelo usuário)
*  VMware vSphere 6.5 Enterprise Plus Edition
*  VMware vCenter Server 6.5
*  VMware NSX Service Providers Edition (Base, Advanced ou Enterprise) 6.4
*  Taxa de suporte e serviços (uma licença por nó)

Deve-se gerenciar os componentes do {{site.data.keyword.vmwaresolutions_short}} que são criados em sua conta do {{site.data.keyword.cloud_notm}} somente por meio do console do
{{site.data.keyword.vmwaresolutions_short}}, não do {{site.data.keyword.slportal}} ou de qualquer outro meio fora do console. Se você mudar esses componentes fora do console do {{site.data.keyword.vmwaresolutions_short}}, as mudanças não serão sincronizadas com o console.
{:important}

**CUIDADO:** Gerenciar quaisquer componentes do {{site.data.keyword.vmwaresolutions_short}} (que foram instalados em sua conta do {{site.data.keyword.cloud_notm}} quando você pediu a instância) de fora do console do {{site.data.keyword.vmwaresolutions_short}} pode desestabilizar seu ambiente. Estas atividades de gerenciamento incluem:
*  Inclusão, modificação, retorno, remoção ou desligamento de componentes
*  Expandindo ou contraindo a capacidade da instância por meio da inclusão ou remoção de servidores ESXi
*  Reiniciando os serviços

   As exceções a essas atividades incluem o gerenciamento de compartilhamentos de arquivos de armazenamento compartilhado por meio do {{site.data.keyword.slportal}}. Essas atividades incluem: pedido, exclusão (que poderá afetar armazenamentos de dados, se montado), autorização e montagem de compartilhamentos de arquivos de armazenamento compartilhado.

## Considerações de firewall
{: #np_netappoverview-firewall-considerations}

Caso esteja usando firewalls, deve-se configurar regras para todas as comunicações por meio da instância de servidor virtual (VSI) do {{site.data.keyword.IBM}} CloudDriver e das máquinas virtuais (MVs) do SDDC Manager. Essas regras devem permitir que todos os protocolos se comuniquem nos endereços IP `10.0.0.0/8` e `161.26.0.0/16`. Exemplos desses firewalls são os NSX Distributed Firewalls (DFW) ou os firewalls Vyatta.

## Links relacionados
{: #np_netappoverview-related}

* [Planejando instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_planning#requirements-and-planning-for-netapp-ontap-select-instances)
* [Pedindo instâncias do NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [Visão geral do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [Centro de Documentação do NetApp ONTAP](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){:new_window}

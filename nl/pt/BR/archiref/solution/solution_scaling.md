---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Escalando a capacidade
{: #solution_scaling}

Após a implementação inicial, é possível ampliar a capacidade de cálculo por meio do console do {{site.data.keyword.vmwaresolutions_full}}. O design suporta os caminhos de ampliação a seguir:
* Adição de novos sites gerenciados por servidores vCenter separados
* Inclusão de novos clusters
* Adição de novos hosts a um cluster existente

## Incluindo mais sites
{: #solution_scaling-sites}

O {{site.data.keyword.vmwaresolutions_short}} pode alavancar a presença mundial do data center {{site.data.keyword.cloud_notm}} e o backbone de rede integrada para permitir que vários casos de uso de geografia cruzada sejam implementados e funcionem dentro de uma fração do tempo que levaria para construir tal infraestrutura do zero.

Nesse design, a definição de uma implementação multissite é composta do seguinte:
* Uma implementação inicial ou primária do VMware contendo um novo domínio-raiz do DNS/AD, subdomínio, domínio de SSO e nome do site de SSO a serem fornecidos.
* Sites secundários únicos ou múltiplos que são provisionados para o domínio SSO de sites primários que requerem a configuração a seguir:
   * Novo nome do site SSO
   * Novo site/subdomínio DNS vinculado à raiz do domínio primário
   * Configuração de replicação do DNS e AD entre as MVs do AD do site secundário e primário
   * Configuração do vCenter com o Enhanced Linked Mode para o vCenter do site primário

Além disso, o NSX Manager em sites secundários pode ser configurado como NSX Managers secundários para o NSX Manager no site primário. Este é um processo manual que você precisa concluir.

## Incluindo novos clusters
{: #solution_scaling-clusters}

Também é possível ampliar a capacidade de cálculo criando um novo cluster por meio do console do {{site.data.keyword.vmwaresolutions_short}} e pedindo novos hosts que são incluídos automaticamente no novo cluster.

Esse método permite que você realize as coisas a seguir:
* Criando um cluster adicional separado no ambiente.
* Segregando cargas de trabalho de gerenciamento de cargas de trabalho do aplicativo física e logicamente.
* Segregando cargas de trabalho com base em outras características, por exemplo, cluster do banco de dados Microsoft SQL.
* Implementando aplicativos em topologias altamente disponíveis.

Quando o cluster inicial for convertido em um cluster somente de gerenciamento, a migração de cargas de trabalho existentes envolverá etapas manuais a serem executadas pelo usuário. Isso pode envolver a reconexão de armazenamentos de dados ao novo cluster ou, alternadamente, a migração de armazenamento. Os endereços IP das cargas de trabalho poderão precisar ser mudados se o novo cluster residir em um pod do {{site.data.keyword.cloud_notm}} diferente ou se o cluster estiver designado a um ID de VLAN diferente.
{:note}

## Incluindo hosts ESXi em clusters existentes
{: #solution_scaling-hosts}

É possível ampliar um cluster existente pedindo hosts por meio do console do {{site.data.keyword.vmwaresolutions_short}}.  Os novos hosts são incluídos automaticamente no cluster. Observe que você pode precisar ajustar a política de reserva de HA para o cluster com base em seus requisitos de reserva.

## Links relacionados
{: #solution_scaling-related}

* [Visão geral da solução](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [ Visão geral do design ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [Fazendo backup de componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-10"

---

# Escalando a capacidade

Após a implementação inicial, é possível ampliar a capacidade de cálculo por meio do console do {{site.data.keyword.vmwaresolutions_full}}. O design suporta os caminhos de ampliação a seguir:
* Adição de novos sites gerenciados por servidores vCenter separados
* Inclusão de novos clusters
* Adição de novos hosts a um cluster existente

## Incluindo mais sites

O {{site.data.keyword.vmwaresolutions_short}} pode alavancar a presença de data centers do {{site.data.keyword.cloud_notm}} no mundo todo e o backbone de rede integrada para permitir que uma variedade de casos de uso de geografia cruzada seja implementada e esteja em funcionamento dentro de uma fração do tempo que levaria para construir tal infraestrutura do zero.

Nesse design, a definição de uma implementação multissite é composta do seguinte:
* Uma implementação inicial ou primária do VMware contendo um novo domínio-raiz do DNS/AD, subdomínio, domínio de SSO e nome do site de SSO a serem fornecidos.
* Sites secundários únicos ou múltiplos que são provisionados para o domínio de SSO de sites primários que requerem a configuração a seguir:
   * Novo nome do site SSO
   * Novo site/subdomínio do DNS ligado à raiz do domínio primário
   * Configuração de replicação do DNS e AD entre as VMs do AD do site secundário e primário
   * PSC implementado e configurado para sincronizar com o PSC do site primário
   * Configuração do vCenter com o Enhanced Linked Mode para o vCenter do site primário

Além disso, o NSX Manager em sites secundários pode ser configurado como NSX Managers secundários para o NSX Manager no site primário.

## Incluindo novos clusters

Também é possível ampliar a capacidade de cálculo criando um novo cluster por meio do console do {{site.data.keyword.vmwaresolutions_short}} e pedindo novos hosts que são incluídos automaticamente no novo cluster.

Esse método permite que você realize as coisas a seguir:
* Criando um cluster adicional separado no ambiente.
* Segregando cargas de trabalho de gerenciamento de cargas de trabalho do aplicativo física e logicamente.
* Segregando cargas de trabalho com base em outras características, por exemplo, cluster do banco de dados Microsoft SQL.
* Implementando aplicativos em topologias altamente disponíveis.

**Nota**: quando o cluster inicial for convertido em um cluster somente de gerenciamento, a migração de cargas de trabalho existentes envolverá etapas manuais a serem seguidas pelo usuário. Isso pode envolver a reconexão de armazenamentos de dados ao novo cluster ou, alternadamente, a migração de armazenamento. Os endereços IP das cargas de trabalho poderão precisar ser mudados se o novo cluster residir em um pod do {{site.data.keyword.cloud_notm}} diferente ou se for designado para um ID de VLAN diferente.

## Incluindo hosts ESXi em clusters existentes

É possível ampliar um cluster existente pedindo hosts por meio do console do {{site.data.keyword.vmwaresolutions_short}}.  Os novos hosts são incluídos automaticamente no cluster. Observe que você pode precisar ajustar a política de reserva de HA para o cluster com base em seus requisitos de reserva.

### Links relacionados

* [ Visão geral da solução ](solution_overview.html)
* [ Visão geral do design ](design_overview.html)
* [ Fazendo backup de componentes ](solution_backingup.html)

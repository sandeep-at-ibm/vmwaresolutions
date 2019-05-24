---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Mensagens do histórico da instância
{: #audit_messages}

Todas as operações que o {{site.data.keyword.cloud_notm}} executa para a instância do VMware são registradas no histórico da instância. É possível usar o histórico da instância como uma referência para revisar essas operações. Para obter mais informações sobre como revisar o histórico da instância, consulte [Procedimento para visualizar o histórico de implementação para instâncias do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history).

As seções a seguir fornecem todas as mensagens possíveis que podem ser emitidas para o histórico da instância.

## Mensagens gerais do histórico da instância
{: #audit_messages-general}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para ações gerais:

* ``Iniciando a criação do usuário da instância e dos serviços necessários...``
* ``A criação do usuário da instância e dos serviços necessários está concluída.``
* ``Pedindo a licença do vCenter Server...``
* ``Pedindo licenças do VMware...``
* ``Concluída a ordem para licenças do VMware.``
* ``Pedindo <quantity> encargos...``
* ``Iniciando a instalação e configuração do <environment>...``
* ``A instalação e a configuração do <environment> estão concluídas.``
* ``Iniciando componentes do VMware...``
* ``Iniciando a implementação da instância...``
* ``A instância do <instance_name> está pronta para uso.``
* ``Iniciando o upgrade para <version>...``
* ``O upgrade para a <version> está concluído.``
* ``O upgrade do componente do VMware está concluído.``
* ``Iniciando a exclusão da instância do <instance_name>...``
* ``A instância do <instance_name> foi excluída com êxito.``
* ``A limpeza segura da instância está concluída.``
* ``Cancelando a licença do vCenter...``
* ``Cancelando o usuário da instância e os serviços necessários...``
* ``Cancelando encargos do <environment>...``
* ``Cancelamento da licença do VMware em andamento...``
* ``O cancelamento da licença do VMware está concluído.``
* ``A ordem do SoftLayer falhou ou atingiu o tempo limite.``

## Mensagens de erro da instância
{: #audit_messages-error}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens de erro do histórico da instância a seguir:

* ``Erro ao pedir licenças do VMware. Abra um chamado de serviço para obter assistência.``
* ``Erro ao pedir sub-redes. Abra um chamado de serviço para obter assistência.``
* ``Erro: a chave de API do SoftLayer não é válida. Abra um chamado de serviço para obter assistência.``
* ``Erro: o data center do SoftLayer não é válido. Abra um chamado de serviço para obter assistência.``
* ``Erro ao usar uma imagem compartilhada na conta do SoftLayer fornecida. Abra um chamado de serviço para obter assistência.``
* ``Erro ao pedir entradas de serviço. Abra um chamado de serviço para obter assistência.``
* ``Erro ao pedir sub-redes. Abra um chamado de serviço para obter assistência.``
* ``Erro ao pedir licenças. Abra um chamado de serviço para obter assistência.``
* ``Erro ao pedir serviços. Abra um chamado de serviço para obter assistência.``

## Mensagens do histórico do cluster
{: #audit_messages-cluster}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para os clusters do vCenter Server:

* ``Iniciando a configuração de cluster...``
* ``Iniciando a configuração de cluster para o <cluster_name>...``
* ``A configuração de cluster está concluída.``
* ``O cluster <cluster_name> está pronto para uso.``
* ``Incluindo o novo cluster no vCenter...``
* ``O novo cluster foi incluído no vCenter.``
* ``Iniciando a exclusão de cluster para <cluster_name>...``
* ``Excluindo o cluster do <cluster_name> do vCenter...``
* ``O cluster do <cluster_name> foi excluído do vCenter.``
* ``O cluster do <cluster_name> foi excluído.``

## Mensagens do histórico do servidor ESXi
{: #audit_messages-esxi}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para servidores ESXi:

* ``Iniciando a ordem para <quantity> servidores ESXi...``
* ``Verificando a ordem do servidor ESXi...``
* ``Os servidores ESXi com o endereço IP Privado <ip_addresses> estão prontos.``
* ``Todos os servidores ESXi são recuperados.``
* ``Incluindo servidores ESXi na instância do vCenter Server...``
* ``Os servidores ESXi foram atualizados com êxito.``
* ``Começando a pedir servidores ESXi para o cluster...``
* ``Começando a pedir <quantity> servidores ESXi para o cluster <Cluster Name>...``
* ``Os servidores ESXi para o cluster estão prontos.``
* ``Os servidores ESXi com o endereço IP Privado <ip_addresses> estão prontos para o cluster.``
* ``O servidor ESXi está pronto.``
* ``A configuração do servidor ESXi está concluída.``
* ``O servidor ESXi foi incluído com êxito com a propriedade.``
* ``Todas as solicitações para incluir servidores ESXi foram concluídas com êxito.``
* ``Incluindo o servidor ESXi...``
* ``Pedindo um Bare Metal Server para o servidor ESXi...``
* ``Novos servidores ESXi foram incluídos no vCenter.``
* ``Iniciando a inclusão de serviços nos novos servidores ESXi...``
* ``Os servidores ESXi selecionados foram cancelados com êxito.``
* ``Novos servidores ESXi foram provisionados.``
* ``Novos servidores ESXi foram verificados e estão prontos.``
* ``Começando a pedir <quantity> novos servidores ESXi para o cluster <cluster_name>...``
* ``Os servidores ESXi selecionados foram removidos do vCenter Server.``
* ``Iniciando a remoção de serviços para remover servidores ESXi...``
* ``Verificando servidores ESXi para o cluster <cluster_name>...``
* ``Os novos servidores ESXi de cluster passaram com êxito na verificação.``
* ``Verificando nova ordem do servidor ESXi...``
* ``A verificação da ordem de servidores ESXi falhou.``
* ``Dividindo a solicitação de servidores ESXi de inclusão de lote.``
* ``Todas as solicitações para remover servidores ESXi foram concluídas com êxito.``
* ``O host foi incluído com êxito.``
* ``Os hosts foram removidos com êxito.``
* ``Cancelamento do Bare Metal Server em andamento...``
* ``O cancelamento do Bare Metal Server está concluído.``
* ``Removendo servidores ESXi da instância do vCenter Server...``
* ``Removendo o servidor ESXi.``
* ``Removendo o servidor ESXi <server_id>.``
* ``Removendo servidores ESXi selecionados do vCenter Server...``
* ``Cancelando os servidores ESXi...``
* ``Cancelando os servidores ESXi selecionados...``

## Mensagens do histórico de rede
{: #audit_messages-network}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para configurações de rede:

* ``Iniciando a ordem da VLAN pública...``
* ``A configuração da VLAN foi concluída com êxito.``
* ``Pedindo a VLAN privada adicional...``
* ``A VLAN privada adicional foi provisionada.``
* ``Uma Instância de Servidor Virtual da VLAN privada adicional foi provisionada.``
* ``Truncando a VLAN privada adicional para Bare Metal Servers...``
* ``A VLAN privada adicional para Bare Metal Servers foi truncada com êxito.``
* ``Cancelando a Instância de Servidor Virtual da VLAN privada adicional...``
* ``Cancelando VLANs...``
* ``Cancelamento de VLAN em andamento...``
* ``O cancelamento da VLAN está concluído.``
* ``Pedindo uma licença NXS <type> de dois soquetes...``
* ``A configuração do NSX para o novo cluster está concluída.``
* ``Cancelando a licença do NSX e dois soquetes...``
* ``A licença do NSX foi cancelada com êxito.``
* ``Iniciando a ordem para sub-rede...``
* ``A sub-rede está pronta.``
* ``A sub-rede privada móvel está pronta.``
* ``Concedendo novo acesso de sub-rede ao armazenamento NFS...``
* ``Cancelando sub-redes...``
* ``Cancelamento de sub-rede em andamento...``
* ``Cancelando a sub-rede privada móvel do cliente...``
* ``Cancelando a sub-rede pública móvel do cliente...``
* ``Cancelando a sub-rede privada do Armazenamento do Endurance...``
* ``Cancelando a sub-rede pública móvel...``
* ``A sub-rede pública móvel está pronta.``
* ``Iniciando a ordem da sub-rede pública móvel...``
* ``O cancelamento da sub-rede está concluído.``
* ``Cancelando o armazenamento de rede...``

## Mensagens do histórico da Instância de servidor virtual
{: #audit_messages-vsi}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para as Instâncias de Virtual Server (VSIs):

* ``Pedindo uma nova instância de servidor virtual para o IBM CloudDriver...``
* ``A instância de servidor virtual do IBM CloudDriver <ip_address> foi provisionada.``
* ``Cancelando a instância de servidor virtual do IBM CloudDriver <ip_address>...``
* ``Iniciando a ordem para a instância de servidor virtual do Microsoft Windows para o Microsoft Active Directory/DNS...``
* ``Verificando a ordem da instância de servidor virtual do Microsoft Windows para o Active Directory/DNS...``
* ``A instância de servidor virtual do Microsoft Windows para o Active Directory/DNS está pronta.``
* ``Cancelamento da instância de servidor virtual em andamento...``
* ``Cancelando instâncias de servidor virtual associadas...``
* ``O cancelamento da instância de servidor virtual está concluído.``

## Mensagens do histórico do IBM CloudBuilder
{: #audit_messages-cloudbuilder}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para o IBM CloudBuilder:

* ``Verificando a ordem da Instância de Servidor Virtual do IBM CloudBuilder...``
* ``Iniciando a ordem para a Instância de Servidor Virtual do IBM CloudBuilder...``
* ``A Instância de Servidor Virtual do IBM CloudBuilder está pronta.``
* ``O IBM CloudBuilder está pronto para o serviço.``
* ``Descartando a Instância de Servidor Virtual do IBM CloudBuilder...``

## Mensagens do histórico do IBM CloudDriver
{: #audit_messages-clouddriver}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para o IBM CloudDriver:

* ``Preparando o IBM CloudDriver...``
* ``O IBM CloudDriver está pronto.``
* ``O IBM CloudDriver <ip_address> está pronto para uso.``
* ``Verificando o status do IBM CloudDriver...``
* ``Reutilizando o IBM CloudDriver <ip_address> existente...``
* ``Reutilizando o IBM CloudDriver existente (em fornecimento)...``
* ``Liberando o IBM CloudDriver...``
* ``Liberando o IBM CloudDriver <ip_address>...``
* ``Iniciando a exclusão do IBM CloudDriver...``
* ``Concluída a exclusão do IBM CloudDriver.``

## Mensagens do histórico de armazenamento
{: #audit_messages-storage}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para configurações de armazenamento:

* ``Pedindo a licença do vSAN...``
* ``Cancelando a licença do vSAN...``
* ``O cancelamento da licença do VSAN está concluído.``
* ``Pedindo <quantity> armazenamentos NFS para o cluster <cluster_name>.``
* ``O novo armazenamento NFS foi incluído e está pronto para uso.``
* ``Cancelando o armazenamento de compartilhamento NFS de gerenciamento...``
* ``O armazenamento NFS selecionado foi excluído.``
* ``Iniciando a ordem para o Armazenamento do Endurance...``
* ``Cancelando o Armazenamento do Endurance...``

## Mensagens do histórico de serviço
{: #audit_messages-services}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para os serviços:

* ``Iniciando a configuração de serviços gerenciamento...``
* ``Pedindo entradas de serviço...``
* ``Concluída a ordem para entradas de serviço.``
* ``Os serviços de operação da IBM estão em execução.``
* ``Ativando os serviços padrão...``
* ``Os serviços padrão foram ativados com êxito.``
* ``Cancelamento da entrada de serviço em andamento...``
* ``O cancelamento da entrada de serviço está concluído.``

## Mensagens do histórico do vCenter Server with Hybridity Bundle
{: #audit_messages-hybridity}

O {{site.data.keyword.vmwaresolutions_short}} emite as mensagens a seguir para as instâncias do vCenter Server with Hybridity Bundle:

* ``Pedindo licenças do vCenter Server with Hybridity Bundle...``
* ``Iniciando a conversão do vCenter Server with Hybridity Bundle...``
* ``A conversão do vCenter Server with Hybridity Bundle está concluída.``
* ``Removendo o vCenter Server with Hybridity Bundle...``
* ``O vCenter Server with Hybridity Bundle foi removido com êxito.``
* ``Cancelando a conversão do vCenter Server with Hybridity Bundle...``

## Links relacionados
{: #audit_messages-related}

* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Eventos de rastreador de atividade](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

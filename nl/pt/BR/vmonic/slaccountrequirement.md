---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisitos para a conta de infraestrutura do IBM Cloud

Para usar {{site.data.keyword.vmwaresolutions_full}} para pedir instâncias, deve-se ter uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer). O custo dos componentes que são pedidos em suas instâncias é faturado para aquela conta {{site.data.keyword.cloud_notm}}.

A conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) era conhecida anteriormente como a conta do IBM SoftLayer.
{:note}

## Permissões para a conta de infraestrutura do IBM Cloud

A conta de infraestrutura do {{site.data.keyword.cloud_notm}} que você está usando deve ter determinadas permissões para poder pedir os componentes em suas instâncias e executar operações em seu nome. Os requisitos de permissão são aplicáveis a todos os tipos de instâncias e serviços que você está pedindo do console do {{site.data.keyword.vmwaresolutions_short}}.

Os usuários autorizados podem verificar e atualizar as permissões para uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} no {{site.data.keyword.slportal}}. Para obter mais informações, consulte [Editando permissões do portal do cliente de um usuário](/docs/customer-portal/cpmanuserprof.html#cp_editusercpperm){:new_window}.

Tabela 1. Permissões necessárias para a conta de infraestrutura do {{site.data.keyword.cloud_notm}}

| Permissão         | Detalhes                                 |
|:------------------ |:--------------------------------------- |
| Incluir servidor | Essa permissão é necessária para as seguintes operações: para pedir o {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} no qual o VMware ESXi é executado e para fornecer, a cada hora, servidores virtuais que são usados para operações de configuração, manutenção e suporte de instâncias. |
| Cancelar servidor | Essa permissão é necessária para liberar e recuperar o {{site.data.keyword.baremetal_short}} no qual o VMware ESXi é executado. Se você excluir sua instância, os componentes pedidos serão automaticamente liberados na sequência de dependência correta. |
| Visualizar detalhes do Virtual Server | Essa permissão é necessária para recuperar os detalhes de fornecimento do servidor, que são necessários para a validação do pedido e a configuração automatizada. |
| Incluir armazenamento | Essa permissão é necessária para pedir armazenamento de backup e armazenamento compartilhado para a instância. |
| Gerenciar armazenamento | Essa permissão é necessária para gerenciar o armazenamento de backup e o armazenamento compartilhado para a instância. |
| Hardware Firewall | Essa permissão é necessária para editar ou visualizar arquivos de log de firewall e configurações para o serviço Fortinet on {{site.data.keyword.cloud_notm}}, se ele estiver instalado em sua instância. |
| Incluir Compute com Porta de Rede Pública | Essa permissão é necessária para pedir hardware e VSIs (Virtual Server Instances) com portas de rede pública. |
| Incluir endereços IP | Essa permissão é necessária para pedir intervalos de sub-rede privada móvel em seu nome, o que é necessário para gerenciar as máquinas virtuais que são executadas em um cluster vSphere. Quando mais serviços são incluídos em sua instância, os endereços IP privados móveis são designados a servidores VMware ESXi para isolar e alocar a largura da banda. |
| Incluir chamados | Essa permissão é necessária para abrir chamados de serviços em seu nome. Os chamados podem ser criados para as seguintes operações: para iniciar operações de restauração e para iniciar processos de resolução de problemas automaticamente quando forem encontrados problemas. |
| Editar chamados | Essa permissão é necessária para editar os tickets de serviço que são criados em seu nome. |
| Visualizar chamados | Essa permissão é necessária para monitorar os tickets de serviço que estão relacionados aos componentes em sua instância para atrasos e problemas de fornecimento de infraestrutura do {{site.data.keyword.cloud_notm}}. |
| Visualizar detalhes do hardware | Essa permissão é necessária para recuperar os detalhes do hardware, que são necessários para a validação do pedido e a configuração automatizada. |
| Visualizar licenças | Essa permissão é necessária para recuperar e validar as licenças que são usadas pela sua instância. |
| Visualizar senhas | Essa permissão é necessária para poder administrar os VSIs pedidos. |
| Gerenciar Monitoramento do Servidor | Essa permissão não é necessária para fazer um pedido, mas é necessária para recuperar e validar o status de monitoramento do {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} no qual os servidores VMware ESXi estão em execução em sua instância. |

## Requisito de roteamento e encaminhamento virtual (VRF)

A conta de infraestrutura do {{site.data.keyword.cloud_notm}} deve ser uma conta VRF ou, caso seja uma conta não VRF, deve ter a ampliação de VLAN ativada. Para obter mais informações sobre como converter sua conta de não VRF para VRF,
consulte [Visão geral do VRF on IBM Cloud](/docs/infrastructure/direct-link/vrf-on-ibm-cloud.html).

## Ampliação de VLAN para contas não VRF

Se você estiver usando uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} não VRF, a
ampliação de VLAN deve ser ativada. Se a ampliação de VLAN não estiver ativada para contas não VRF, os vários
componentes do ambiente de virtualização do VMware podem não ser capazes de se comunicar uns com os outros.

Para ativar a ampliação de VLAN em sua conta, consulte
[Ampliação de VLAN](/docs/infrastructure/vlans/vlan-spanning.html){:new_window}.

### Links relacionados

* [Requisitos para instâncias do Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_planning.html)
* [Requisitos para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
* [Conta do usuário e configurações](/docs/services/vmwaresolutions/vmonic/useraccount.html)
* [ Visão geral do VRF no IBM Cloud ](/docs/infrastructure/direct-link/vrf-on-ibm-cloud.html)

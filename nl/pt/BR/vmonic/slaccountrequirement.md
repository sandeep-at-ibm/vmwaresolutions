---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Requisitos para a conta de infraestrutura do IBM Cloud
{: #slaccountrequirement}

Para usar {{site.data.keyword.vmwaresolutions_full}} para pedir instâncias, deve-se ter uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer). O custo dos componentes que são pedidos em suas instâncias é faturado para aquela conta {{site.data.keyword.cloud_notm}}.

A conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) era conhecida anteriormente como a conta do IBM SoftLayer.
{:note}

## Permissões para a conta de infraestrutura do IBM Cloud
{: #slaccountrequirement-permissions}

A conta de infraestrutura do {{site.data.keyword.cloud_notm}} que você está usando deve ter determinadas permissões para poder pedir os componentes em suas instâncias e executar operações em seu nome. Os requisitos de permissão são aplicáveis a todos os tipos de instâncias e serviços que você está pedindo do console do {{site.data.keyword.vmwaresolutions_short}}.

Os usuários autorizados podem verificar e atualizar as permissões para uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} no {{site.data.keyword.slportal}}. Para obter mais informações, consulte [Editando permissões do portal do cliente de um usuário](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}.

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

## VRF com terminais em serviço ativados
{: #slaccountrequirement-vrf-se}

A sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} deve ser uma conta Virtual Routing and Forwarding (VRF) com os terminais em serviço ativados. Se a sua conta for não VRF, você deverá convertê-la para uma conta VRF. Além disso, deve-se ativar a conta VRF para usar os terminais em serviço.

Para obter mais informações, veja:
* [ Visão geral do VRF no IBM Cloud ](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [Ativar sua conta para usar terminais em serviço](/docs/services/service-endpoint?topic=services/service-endpoint-cs_cli_install_steps#cs_cli_install_steps)

## VLAN Spanning end of support
{: #slaccountrequirement-vlan-eos}

A partir de agosto de 2019, a ampliação de VLAN não será mais suportada. Até o final de julho de 2019, deve-se converter sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} para VRF e ativar os terminais em serviço.
{:important}

## Links relacionados
{: #slaccountrequirement-related}

* [Requisitos para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [Conta do usuário e configurações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [ Visão geral do VRF no IBM Cloud ](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)

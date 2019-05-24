---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IDs de usuário da IBM
{: #audit_user_ids}

O {{site.data.keyword.vmwaresolutions_short}} mantém um conjunto de usuários em sua conta para uso pela automação do {{site.data.keyword.cloud_notm}} ao executar operações, como incluir hosts, clusters ou armazenamento em sua instância do VMware. Revise as seções a seguir para os IDs de usuário de automação do {{site.data.keyword.cloud_notm}}.

As operações de instância do VMware falharão se os IDs de usuário da IBM forem excluídos, desativados ou se suas senhas forem mudadas.
{:important}

## IDs de usuário do vCenter e do Platform Services Controller
{: #audit_user_ids-vcenter-psc}

Iniciando com a V2.5, o {{site.data.keyword.vmwaresolutions_short}} usa os IDs de usuário a seguir para incluir uma origem da identidade, integrada por padrão, no vCenter.

Tabela 1. IDs de usuário do vCenter e do Platform Services Controller

| Usuário     | ID do usuário      | Método | Descrição |
|:---------|:-------------|:-------|:------------|
| IBM      | raiz         | SSH    | Usada para configuração do VMware, como configurar o VMware High Availability e criar comutadores distribuídos. Usado pós-implementação para emparelhar as instâncias primária e secundária do vCenter Server. |
| Cliente | customerroot | SSH    | Criado somente para uso do cliente. |
| IBM      | automation@``root_domain``<br/>(usuário do Active Directory) | HTTP | Usado pós-implementação para incluir e remover hosts e clusters e para implementar e configurar máquinas virtuais para serviços complementares. |
| Cliente | Administrator@vsphere.local | HTTP | Criado somente para uso do cliente. |

O HTTP é usado para instalação e configuração do vCenter, bem como operações do VMware, como incluir hosts, clusters ou armazenamento para gerenciamento de recursos do vCenter.
{:note}

## IDs de usuário do NSX Manager
{: #audit_user_ids-nsx-mgr}

Tabela 2. IDs de usuário do NSX Manager

| Usuário     | ID do usuário      | Descrição |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(usuário do Active Directory) | Usado pós-implementação para gerenciar os endereços IP do NSX VTEP, gerenciar a configuração do host e do cluster ao incluir e remover hosts e clusters e gerenciar a configuração do ESG para serviços complementares que requerem acesso à rede pública para licenciamento, ativação ou relatório de uso. |
| Cliente | Admin        | Criado somente para uso do cliente. |

## IDs de usuário do host ESXi
{: #audit_user_ids-esxi}

Tabela 3. IDs de usuário do host ESXi

| Usuário     | ID do usuário      | Descrição |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | Usada a pós-implementação para incluir armazenamento NFS adicional, configurar rotas para esse armazenamento e executar todo o código de validação do servidor. |
| Cliente | raiz         | Criado somente para uso do cliente. |

## IDs de usuário do Microsoft Active Directory
{: #audit_user_ids-ad}

Tabela 4. IDs de usuário do Active Directory

| Usuário     | ID do usuário       | Descrição |
|:---------|:------------- |:------------|
| IBM      | automação    | Usado para incluir um host, para incluir uma máquina virtual para serviço e para configurar entradas do Active Directory e do DNS. |
| Cliente | Administrador | Criado somente para uso do cliente. |

## Links relacionados
{: #audit_user_ids-related}

* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Eventos de rastreador de atividade](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

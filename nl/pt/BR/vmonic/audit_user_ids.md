---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IDs de usuário da IBM
{: #audit_user_ids}

O {{site.data.keyword.vmwaresolutions_short}} mantém um conjunto de usuários em sua conta para uso pela automação do {{site.data.keyword.cloud_notm}} ao executar operações, como incluir hosts, clusters ou armazenamento em sua instância do VMware. Os usuários em sua conta também podem ser usados para instalação e configuração de serviços pela automação de serviços do {{site.data.keyword.cloud_notm}}. Revise as seções a seguir para os IDs de usuário de automação do {{site.data.keyword.cloud_notm}}.

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

## IDs de usuário do serviço
{: #audit_user_ids-services}

Tabela 5. IDs de usuário do serviço

| ID do usuário                                    | Descrição |
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço F5 on {{site.data.keyword.cloud_notm}}. |
| prod-Caveonix-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}. |
| prod-Fortigate-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}. |
| prod-FortigateVM-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustCC-``5_letter_ID``-@``domain name`` | Usado para instalação e configuração do serviço HyTrust CloudControl on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustDC-``5_letter_ID``-@``domain name`` | Usado para instalação e configuração do serviço HyTrust DataControl on {{site.data.keyword.cloud_notm}}. |
| prod-HyTrustKC-``5_letter_ID``-@``domain name`` | Usado para instalação e configuração do serviço HyTrust KeyControl on {{site.data.keyword.cloud_notm}}. |
| prod-KMIPAdapter-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}. |
| prod-ICP-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço {{site.data.keyword.cloud_notm}} Private Hosted. |
| prod-SPPlus-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}. |
| prod-Veeam-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço Veeam on {{site.data.keyword.cloud_notm}}. |
| prod-HCX-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço VMware HCX on {{site.data.keyword.cloud_notm}}. |
| prod-Zerto-``dynamic_ID``-@``domain name`` | Usado para instalação e configuração do serviço Zerto on {{site.data.keyword.cloud_notm}}. |

Os IDs dinâmicos têm de oito a dez letras de comprimento.
{:note}

## Links relacionados
{: #audit_user_ids-related}

* [Considerações sobre como alterar os artefatos do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Eventos de rastreador de atividade](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

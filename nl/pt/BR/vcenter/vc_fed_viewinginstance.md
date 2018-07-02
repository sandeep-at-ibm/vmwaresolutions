---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Visualizando instâncias do VMware Federal

Use este procedimento para visualizar as instâncias do VMware Federal que você pediu e informações detalhadas sobre elas.

## Visualizando o resumo de instâncias do VMware Federal

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **vCenter Server**, visualize a lista de suas instâncias.

Tabela 1. Itens de instâncias do VMware Federal

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome da instância. |
| Versão | A versão de liberação na qual a instância foi implementada ou para a qual teve upgrade feito. |  
| Localização | O {{site.data.keyword.CloudDataCent}} no qual a instância é hospedada. |  
| Horário de criação | A data e hora em que a instância foi criada. |  

A instância pode ter um intervalo de status.

Tabela 2. Descrições de status de instâncias do data center do VMware Federal

| Status        | Descrição       |
|:------------- |:------------- |
| Criando | A instância está sendo criada. |
| Construindo | A instância está sendo configurada. |
| Pronto para usar | A instância está pronta para uso. |
| Modificando | A instância está sendo modificada. |
| Protegida | A instância implementada é desconectada de uma conexão de gerenciamento aberta e automação.
| Com falha | O processo de criação, configuração ou modificação falhou. |
| Excluindo | A instância está sendo excluída. |
| Erro de exclusão | Ocorreu um erro quando a instância estava sendo excluída. |
| Excluído | A instância foi excluída. |

## Visualizando detalhes da propriedade da instância do VMware Federal

Para visualizar os detalhes da propriedade de uma instância:

1. Na tabela **Instâncias do vCenter Server**, clique em um nome da instância.
2. Em **Propriedades**, visualize os detalhes da instância.

Tabela 3. Propriedades de instância do VMware Federal

| Propriedade        | Descrição       |
|:------------- |:------------- |
| Nome | O nome da instância. |
| ID | O ID da instância. |
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada. |
| Versão atual |  A versão atual do {{site.data.keyword.vmwaresolutions_short}}. |
| Versão do vCenter | A versão do VMware vCenter Server.<br><br>**Nota:** há uma ligeira variação entre a versão do vCenter Server exibida no console do {{site.data.keyword.vmwaresolutions_short}} e o VMware vSphere Web Client. Ambos estão corretos. |
| NSX for vSphere | A versão do produto VMware NSX for vSphere. |
| Edição de licença NSX | A versão e a edição da licença do VMware NSX. |
| Domínio-raiz DNS | O nome do domínio-raiz é o nome de domínio do DNS (Sistema de Nomes de Domínio) e o nome raiz da floresta do Microsoft Active Directory (AD). |
| Domínio SSO DNC | O domínio SSO é o domínio de Conexão única do vSphere. O nome de domínio SSO é corrigido para todas as instâncias implementadas do vCenter Server com um valor de <samp class="ph codeph">vsphere.local</samp>. |
| Subdomínio DNS | O subdomínio é o nome do subdomínio do DNS no nome de domínio-raiz no qual os nomes de host da instância local do vCenter Server residem. O nome do subdomínio está no formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Status | O status da instância. |

## Visualizando informações de acesso para instâncias do VMware Federal

Em **Informações de acesso**, visualize as informações de acesso dos componentes relacionados à instância. As senhas exibidas são senhas iniciais geradas pelo sistema. Se você as mudar fora do console do {{site.data.keyword.vmwaresolutions_short}}, elas não serão atualizadas na página de resumo da instância.

Tabela 4. Informações de acesso para componentes relacionados à instância

| Componente        | Descrição       |
|:------------- |:------------- |
| IPs do AD/DNS | Os endereços IP dos dois servidores AD. |
| FQDNs do AD/DNS | Os nomes completos de domínio do servidor AD/DNS.<br><br>**Nota**: a mesma senha do administrador pode ser usada para se conectar a todos os servidores AD/DNS usando uma conexão de área de trabalho remota. |
| ADMINISTRADOR DO AD/DNS (Área de trabalho remota)  | Para instâncias primárias, ele exibe o nome do usuário e a senha para acessar o servidor AD por meio de uma conexão de área de trabalho remota.
| IP do NSX Manager  | O endereço IP do NSX Manager.  |
| FQDN do NSX Manager  | O nome completo do domínio (FQDN) do NSX Manager.  |
| HTTP do NSX Manager  | O nome do usuário e a senha usados para acessar o console da web do NSX Manager. |
| IP do PSC  | O endereço IP do Platform Services Controller (PSC).  |
| FQDN do PSC  | O nome completo do domínio (FQDN) do PSC.  |    
| ADMINISTRADOR do PSC  | O nome do usuário e a senha do VMware vCenter Single Sign-On que podem ser usados para acessar o console da web do PSC.  |
| SSH do PSC  | O nome do usuário e a senha que podem ser usados para acessar a VM do PSC por meio da conexão SSH.  |
| IP do vCenter  | O endereço IP do vCenter Server.  |
| FQDN do vCenter  | O nome completo do domínio (FQDN) do vCenter Server.  |
| ADMINISTRADOR do vCenter  | O nome do usuário e a senha do VMware vCenter Single Sign-On que podem ser usados para efetuar login no vCenter Server usando o vSphere Web Client.  |
| SSH do vCenter  | O nome do usuário e a senha que podem ser usados para acessar a VM do vCenter Server por meio da conexão SSH.  |

## Visualizando o histórico de implementação para instâncias do VMware Federal

Em **Histórico de implementação**, visualize o histórico de implementação da instância.

Tabela 5. Histórico de implementação da instância do VMware Federal

| Item        | Descrição       |  
|:------------- |:------------- |
| Data | A data e hora em que o status da instância é mudado. |
| Resumo | Os detalhes da mudança. |

## O que fazer se ocorrerem erros

Se ocorrerem erros durante a implementação ou exclusão da instância, a equipe de Suporte do {{site.data.keyword.cloud_notm}} será notificada automaticamente. Para consultar o status de seu chamado, é possível [entrar em contato com o Suporte IBM](../vmonic/trbl_support.html).

## O que fazer a seguir

Gerencie suas instâncias do console do {{site.data.keyword.vmwaresolutions_short}} ou do VMware vSphere Web Client.

**Importante**: antes de clicar em **Console do vCenter** na página de resumo da instância para acessar o vSphere Web Client e começar a gerenciar os seus servidores do ESXi, deve-se efetuar login no portal da VPN do {{site.data.keyword.CloudDataCent_notm}}. Passe o mouse sobre o botão **console do vCenter** e siga as instruções para assegurar-se de que atenda a todos os requisitos e que tenha concluído as etapas necessárias antes de acessar o vSphere Web Client.

Revise os tópicos a seguir para obter informações que ajudarão a concluir as instruções de login:
*  Para obter os requisitos e as etapas necessárias antes de acessar o vSphere Web Client, veja [Tempo limite atingido ao se conectar ao vSphere Web Client](../vmonic/trbl_timeout_vc_console.html).
*  Para obter uma lista de pontos de acesso para efetuar login na Rede Privada da infraestrutura do {{site.data.keyword.cloud_notm}} usando a VPN, veja [Acesso à VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Se tiver problemas ao implementar um arquivo OVF (Open Virtualization Format) usando o vSphere Web Client, veja [Implementando um arquivo OVF usando o vSphere Web Client](../vmonic/trbl_deploy_ovf.html).

## Links relacionados

* [Visão geral do VMware Federal on IBM Cloud](vc_fed_overview.html)
* [Pedindo instâncias do VMware Federal](vc_fed_orderinginstance.html)
* [Excluindo instâncias do VMware Federal](vc_fed_deletinginstance.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)

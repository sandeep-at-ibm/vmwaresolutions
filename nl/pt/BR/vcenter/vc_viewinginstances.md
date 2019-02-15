---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visualizando instâncias do vCenter Server

Visualize o resumo e as informações detalhadas das instâncias do VMware vCenter Server que são provisionadas para diferentes contas do usuário.

## Procedimento para visualizar o resumo de instâncias do vCenter Server

Para visualizar um resumo de todas as instâncias do vCenter Server que são provisionadas para uma conta do usuário, conclua as etapas a seguir:

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. No banner do console, clique em seu ícone de conta do usuário e, em seguida, clique no campo **Conta** para selecionar a conta do usuário da qual você deseja verificar as instâncias.  
3. Na tabela **Instâncias do vCenter Server**, visualize a lista de instâncias que são provisionadas na conta do usuário selecionada.

Tabela 1. Itens de instância do vCenter Server

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome da instância |
| Tipo | O tipo de instância do vCenter Server |
| Versão | A versão de liberação na qual a instância foi implementada ou submetida a upgrade |  
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada |  
| Horário de criação | A data e hora em que a instância foi criada |
| Status | O status da instância |   

A instância pode ter um intervalo de status.

Tabela 2. Descrições do status de instâncias do vCenter Server

| Status | Descrição       |
|:------------- |:------------- |
| Criando | A instância está sendo criada. |
| Construindo | A instância está sendo configurada. |
| Pronto para usar | A instância está pronta para uso. |
| Modificando | A instância está sendo modificada. |
| Com falha | O processo de criação, configuração ou modificação falhou. |
| Excluindo | A instância está sendo excluída. |
| Erro de exclusão | Ocorreu um erro quando a instância estava sendo excluída. |
| Excluído | A instância foi excluída. |

## Procedimento para visualizar os detalhes da propriedade de instância do vCenter Server

Para visualizar os detalhes da propriedade de uma instância:

1. Na tabela **Instâncias do vCenter Server**, clique em um nome de instância.
2. Em **Propriedades**, visualize os detalhes da instância.

Tabela 3. Propriedades da instância do vCenter Server

| Propriedade        | Descrição       |
|:------------- |:------------- |
| Nome | O nome da instância. |
| ID | O ID da instância. |
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada. |
| Versão atual | A versão atual do {{site.data.keyword.vmwaresolutions_short}}. |
| Versão do vCenter | A versão do VMware vCenter Server.<br><br>**Nota:** há uma ligeira variação entre a versão do vCenter Server exibida no console do {{site.data.keyword.vmwaresolutions_short}} e o VMware vSphere Web Client. Ambos estão corretos. |
| NSX for vSphere | A versão do produto VMware NSX for vSphere. |
| Licença do _componente do VMware_ | Se tiver selecionado para usar sua própria licença do VMware para qualquer um dos componentes do VMware na página **Licenciamento** quando pediu a instância, o nome do componente do VMware e a chave de licença inseridos para o componente serão exibidos.<br><br>Exemplos de licenças do componente do VMware podem incluir: **Licença do NSX**, **Licença do vCenter Server** e **Licença do vSAN**. |
| Edição de licença NSX | A versão e a edição da licença do VMware NSX. |
| DNS, domínio-raiz | O nome do domínio-raiz é o nome de domínio do DNS (Sistema de Nomes de Domínio) e o nome raiz da floresta do Microsoft Active Directory (AD). |
| DNS, domínio SSO | O domínio SSO é o domínio de Conexão única do vSphere. O nome de domínio SSO é corrigido para todas as instâncias implementadas do vCenter Server com um valor de <samp class="ph codeph">vsphere.local</samp>. |
| DNS, subdomínio | O subdomínio é o nome do subdomínio do DNS no nome de domínio-raiz no qual os nomes de host da instância local do vCenter Server residem. O nome do subdomínio está no formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Hybridity Bundle | Indica se o Pacote configurável vCenter Server with Hybridity está instalado. |
| Status | O status da instância.<br><br>As informações exibidas fornecem uma atualização sobre o progresso da implementação ou a ação que é executada na instância. Se houver problemas, uma mensagem poderá ser exibida para ajudá-lo a investigar e resolver o problema. |

## Procedimento para visualizar as informações de acesso para instâncias do vCenter Server

Em **Informações de acesso**, visualize as informações de acesso dos componentes relacionados à instância. As senhas exibidas são senhas iniciais geradas pelo sistema. Se você as mudar fora do console do {{site.data.keyword.vmwaresolutions_short}}, elas não serão atualizadas na página de resumo da instância.

Tabela 4. Informações de acesso do vCenter Server para componentes relacionados à instância

| Componente        | Descrição       |
|:------------- |:------------- |
| IPs do AD/DNS | Os endereços IP dos dois servidores AD. |
| FQDNs do AD/DNS | Os nomes completos de domínio do servidor AD/DNS.<br><br>**Nota:** a mesma senha do administrador pode ser usada para conectar-se a todos os servidores AD/DNS usando uma conexão de área de trabalho remota. |
| ADMINISTRADOR DO AD/DNS (Área de trabalho remota)  | Para instâncias primárias, ele exibe o nome do usuário e a senha para acessar o servidor AD por meio de uma conexão de área de trabalho remota.<br><br>Para instâncias secundárias, clique no link **Visualizar na instância primária** para ser direcionado para as informações de nome de usuário e senha na instância primária.<br><br>**Nota:** após a instância secundária ser incluída no domínio DNS primário e ocorrer a replicação, a senha do administrador local na instância principal poderá substituir a senha do administrador local na instância secundária. Ao clicar no link **Visualizar na instância primária**, você obterá acesso à senha correta do administrador.  
| IP do NSX Manager  | O endereço IP do NSX Manager.  |
| FQDN do NSX Manager  | O nome completo do domínio (FQDN) do NSX Manager.  |
| HTTP do NSX Manager  | O nome do usuário e a senha usados para acessar o console da web do NSX Manager. |
| IP do vCenter  | O endereço IP do vCenter Server.  |
| FQDN do vCenter  | O nome completo do domínio (FQDN) do vCenter Server.  |
| ADMINISTRADOR do vCenter  | O nome do usuário e a senha do VMware vCenter Single Sign-On que podem ser usados para efetuar login no vCenter Server usando o vSphere Web Client.  |
| SSH do vCenter  | O nome do usuário e a senha que podem ser usados para acessar a MV do vCenter Server por meio da conexão SSH.  |

## Procedimento para visualizar o histórico de implementação para instâncias do vCenter Server

Clique em **Histórico de implementação** na área de janela de navegação esquerda para visualizar o histórico de implementação da instância.

Tabela 5. Histórico de implementação da instância do vCenter Server

| Item        | Descrição       |  
|:------------- |:------------- |
| Data | A data e hora em que o status da instância muda |
| Resumo | Os detalhes da mudança |

## O que fazer se ocorrerem erros

Se ocorrerem erros durante a implementação ou exclusão da instância, a equipe de Suporte do {{site.data.keyword.cloud_notm}} será notificada automaticamente. Para consultar o status de seu chamado, é possível [entrar em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html).

## O que fazer a seguir

Gerencie suas instâncias do console do {{site.data.keyword.vmwaresolutions_short}} ou do VMware vSphere Web Client.

Antes de clicar no **Console do vCenter** na página de resumo da instância para acessar o Web client do vSphere e começar a gerenciar seus servidores ESXi, deve-se efetuar login no portal VPN do {{site.data.keyword.CloudDataCent_notm}}. Passe o mouse sobre o botão **console do vCenter** e siga as instruções para assegurar-se de que atenda a todos os requisitos e que tenha concluído as etapas necessárias antes de acessar o vSphere Web Client.
{:important}

Revise os tópicos a seguir para obter informações que ajudarão a concluir as instruções de login:
*  Para obter os requisitos e as etapas necessárias antes de acessar o vSphere Web Client, veja [Tempo limite atingido ao se conectar ao vSphere Web Client](/docs/services/vmwaresolutions/vmonic/trbl_timeout_vc_console.html).
*  Para obter uma lista de pontos de acesso para efetuar login na Rede Privada da infraestrutura do {{site.data.keyword.cloud_notm}} usando a VPN, veja [Acesso à VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Se tiver problemas ao implementar um arquivo OVF (Open Virtualization Format) usando o vSphere Web Client, veja [Implementando um arquivo OVF usando o vSphere Web Client](/docs/services/vmwaresolutions/vmonic/trbl_deploy_ovf.html).

### Links relacionados

* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)
* [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingviewingclusters.html)
* [Expandindo e contraindo a capacidade para instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html)
* [Excluindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_deletinginstance.html)

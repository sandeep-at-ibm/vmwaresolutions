---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Visualizando instâncias do Cloud Foundation

Visualize o resumo e as informações detalhadas das instâncias do VMware Cloud Foundation que são provisionadas para diferentes contas do usuário.

## Procedimento para visualizar o resumo de instâncias do Cloud Foundation

Para visualizar um resumo de todas as instâncias do Cloud Foundation que são provisionadas para uma conta do usuário, conclua as etapas a seguir:

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. No banner do console, clique em seu ícone de conta do usuário e, em seguida, clique no campo **Conta** para selecionar a conta do usuário da qual você deseja verificar as instâncias.
3. Na tabela **Instâncias do Cloud Foundation**, visualize a lista de suas instâncias:

Tabela 1. Cloud Foundation instância itens

| Item        | Descrição       |  
|:------------- |:------------- |
| Nome | O nome da instância |
| Versão | A versão de liberação na qual a instância foi implementada ou submetida a upgrade |
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada |
| Horário de criação | A data e hora em que a instância foi criada |
| Barra de Status | O status da instância |

A instância pode ter um intervalo de status.

Tabela 2. Descrições do status de instâncias do Cloud Foundation

| Barra de Status        | Descrição       |
|:------------- |:------------- |
| Criando | A instância está sendo criada. |
| Construindo | A instância está sendo configurada. |
| Pronto para usar | A instância está pronta para uso. |
| Modificando | A instância está sendo modificada. |
| Com falha | O processo de criação, configuração ou modificação falhou. |
| Excluindo | A instância está sendo excluída. |
| Erro de exclusão | Ocorreu um erro quando a instância estava sendo excluída. |
| Excluído | A instância foi excluída. |

## Procedimento para visualizar detalhes da propriedade de instâncias do Cloud Foundation

Para visualizar os detalhes da propriedade de uma instância:

1. Na tabela **Instâncias do Cloud Foundation**, clique em um nome da instância.
2. Em **Propriedades**, visualize os detalhes da instância.

Tabela 3. Cloud Foundation propriedades da instância

| Propriedade        | Descrição       |
|:------------- |:------------- |
| Nome | O nome da instância |
| ID | O ID da instância |
| Localização | O {{site.data.keyword.CloudDataCent_notm}} no qual a instância é hospedada |
| Versão atual | A versão atual do {{site.data.keyword.vmwaresolutions_short}} |
| Versão do vCenter | A versão do VMware vCenter Server<br><br>**Nota:** há uma pequena variação entre a versão do vCenter Server que é exibida no console do {{site.data.keyword.vmwaresolutions_short}} e no VMware vSphere Web Client. Ambos estão corretos. |
| NSX for vSphere | O VMware NSX para a versão do produto vSphere |
| Licença do _componente do VMware_ | Se tiver selecionado para usar sua própria licença do VMware para qualquer um dos componentes do VMware na página **Licenciamento** quando pediu a instância, o nome do componente do VMware e a chave de licença inseridos para o componente serão exibidos.<br><br>Exemplos de licenças de componentes do VMware são **Licença do vCenter Server** e **Licença do NSX**. |
| Edição de licença NSX | A versão e edição da licença do VMware NSX |
| DNS, domínio-raiz | O nome do domínio-raiz é o nome de domínio do DNS (Sistema de Nomes de Domínio) e o nome raiz da floresta do Microsoft Active Directory (AD). |
| DNS, domínio SSO | O domínio SSO é o domínio de Conexão única do vSphere. O nome de domínio SSO é fixo para todas as instâncias implementadas do Cloud Foundation com um valor de <samp class="ph codeph">vsphere.local</samp>. |
| DNS, subdomínio | O subdomínio é o nome do subdomínio DNS do nome do domínio-raiz em que residem os nomes de host da instância do Cloud Foundation local. O nome do subdomínio está no formato <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>. |
| Versão do SDDC Manager  |  A versão do SDDC Manager da instância |
| Barra de Status  | O status da instância<br><br>As informações exibidas fornecem uma atualização sobre o progresso da implementação ou a ação que é executada na instância. Quando ocorrem problemas, uma mensagem pode ser exibida para ajudar a investigar e resolver o problema. |

## Procedimento para visualizar informações de acesso para instâncias do Cloud Foundation

Em **Informações de acesso**, visualize as informações de acesso dos componentes relacionados à instância. As senhas exibidas são senhas iniciais geradas pelo sistema. Se você as mudar fora do console do {{site.data.keyword.vmwaresolutions_short}}, elas não serão atualizadas na página de resumo da instância.

Tabela 4. Informações de acesso do Cloud Foundation para componentes relacionados à instância

| Componente        | Descrição       |
|:------------- |:------------- |
| AD/DNS IP | O endereço IP dos dois servidores AD |
| AD/DNS FQDN | O nome completo do domínio do servidor AD/DNS<br><br>**Nota:** a mesma senha do administrador pode ser usada para conectar-se a todos os servidores AD/DNS usando uma conexão de área de trabalho remota. |
| ADMINISTRADOR DO AD/DNS (Área de trabalho remota)  | Para instâncias primárias, ele exibe o nome do usuário e a senha para acessar o servidor AD por meio de uma conexão de área de trabalho remota.<br><br>Para instâncias secundárias, clique no link **Visualizar na instância primária** para ser direcionado para as informações de nome de usuário e senha na instância primária.<br><br>**Nota:** após a instância secundária ser incluída no domínio DNS primário e ocorrer a replicação, a senha do administrador local na instância principal poderá substituir a senha do administrador local na instância secundária. Ao clicar no link **Visualizar na instância primária**, você obtém acesso à senha correta do administrador.  |
| IP do NSX Manager  | O endereço IP do NSX Manager  |
| FQDN do NSX Manager  | O nome completo do domínio do NSX Manager  |
| HTTP do NSX Manager  | O nome do usuário e a senha usados para acessar o console da web do NSX Manager |
| SSH do NSX Manager | O nome do usuário e a senha que podem ser usados para acessar o NSX Manager por meio da conexão SSH |
| IP do PSC  | O endereço IP do Platform Services Controller  |
| FQDN do PSC  | O nome completo do domínio do PSC  |    
| SSH do PSC  | O nome do usuário e a senha que você pode usar para acessar a VM do PSC por meio de uma conexão SSH  |
| ADMINISTRADOR do PSC  | O nome do usuário e a senha de Conexão Única do VMware vCenter que você pode usar para acessar o console da web do PSC  |
| IP do vCenter  | O endereço IP do vCenter Server  |
| FQDN do vCenter  | O nome completo do domínio do vCenter Server  |
| SSH do vCenter  | O nome do usuário e a senha que você pode usar para acessar a VM do vCenter Server por meio de uma conexão SSH |
| ADMINISTRADOR do vCenter  | O nome do usuário e a senha de Conexão Única do VMware vCenter que você pode usar para efetuar login no vCenter Server usando o vSphere Web Client  |

## Procedimento para visualizar o histórico de implementação para instâncias do Cloud Foundation

Clique em **Histórico de implementação** na área de janela de navegação esquerda para visualizar o histórico de implementação da instância.

Tabela 5. Histórico de implementação da instância do Cloud Foundation

| Item        | Descrição       |  
|:------------- |:------------- |
| Data | A data e hora em que o status da instância muda |
| Resumo | Os detalhes da mudança |

## O que fazer se ocorrerem erros

Se ocorrerem erros durante a implementação ou exclusão da instância, a equipe de Suporte do {{site.data.keyword.cloud_notm}} será notificada automaticamente. Para consultar o status de seu chamado, é possível [entrar em contato com o Suporte IBM](../vmonic/trbl_support.html).

## O que fazer a seguir

Gerencie suas instâncias do console do {{site.data.keyword.vmwaresolutions_short}} ou do vSphere Web Client.

Antes de clicar no **Console do vCenter** na página de resumo da instância para acessar o Web client do vSphere e começar a gerenciar seus servidores ESXi, deve-se efetuar login no portal VPN do {{site.data.keyword.CloudDataCent_notm}}. Passe o mouse sobre o botão do console do vCenter e siga as instruções para assegurar que você atenda a todos os requisitos e que tenha concluído as etapas necessárias antes de acessar o vSphere Web Client.
{:important}

Revise os tópicos a seguir para obter informações que ajudarão a concluir as instruções de login:

* Para obter os requisitos e as etapas necessárias antes de acessar o vSphere Web Client, veja [Tempo limite atingido ao se conectar ao vSphere Web Client](../vmonic/trbl_timeout_vc_console.html).
* Para obter uma lista de pontos de acesso para efetuar login na Rede privada do {{site.data.keyword.cloud_notm}} usando a VPN, consulte [Acesso à VPN](http://www.softlayer.com/vpn-access){:new_window}.
* Se tiver problemas ao implementar um arquivo OVF (Open Virtualization Format) usando o vSphere Web Client, consulte [Implementando um arquivo OVF usando o vSphere Web Client](../vmonic/trbl_deploy_ovf.html).

### Links relacionados

* [Pedindo instâncias do Cloud Foundation](sd_orderinginstance.html)
* [Expandindo e contraindo capacidade para instâncias do Cloud Foundation](sd_addingremovingservers.html)
* [Excluindo instâncias do Cloud Foundation](sd_deletinginstance.html)

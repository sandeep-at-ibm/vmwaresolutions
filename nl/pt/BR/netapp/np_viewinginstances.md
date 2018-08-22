---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# Visualizando instâncias do NetApp ONTAP Select

Visualize o resumo e as informações detalhadas das instâncias do NetApp ONTAP Select que são provisionadas para diferentes contas do usuário.

## Visualizando instâncias do NetApp ONTAP Select resumo

Para visualizar um resumo de todas as instâncias do NetApp ONTAP Select que são provisionadas para uma conta do usuário, conclua as etapas a seguir:

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. No canto superior direito do console, clique em seu avatar e, em seguida, clique no campo **Conta** para selecionar a conta do usuário da qual você deseja verificar instâncias.
3. Na tabela **Instâncias do NetApp ONTAP Select**, visualize a lista de instâncias que são provisionadas na conta do usuário selecionada.

Tabela 1. Itens de instâncias do NetApp ONTAP Select

| Item        | Descrição       |  
|:------------- |:--------------- |
| Nome | O nome da instância. |
| Versão | A versão da instância. |  
| Localização | O data center no qual a instância está hospedada. |
| Horário de criação | A data e hora em que a instância foi criada. |   
| Status | O status da instância. O status pode ter um dos valores a seguir:<ul><li>Criando: A instância está sendo criada.</li><li>Prédio: A instância está sendo configurada.</li><li>Pronta para uso: A instância está pronta para uso.</li><li>Modificando: A instância está sendo modificada.</li><li>Com falha: o processo de criação, configuração ou modificação falhou.</li><li>Excluindo: A instância está sendo excluída.</li><li>Erro de exclusão: ocorreu um erro quando a instância estava sendo excluída.</li><li>Excluído: A instância foi excluída.</li></ul>|

## Visualizando detalhes da propriedade de instâncias do NetApp ONTAP Select

Para visualizar os detalhes da propriedade de uma instância:

1. Na tabela **Instâncias do NetApp ONTAP Select**, clique em um nome da instância.
2. Em **Propriedades**, visualize os detalhes da instância.

Tabela 2. Propriedades de instância do NetApp ONTAP Select

| Propriedade        | Descrição       |
|:--------------- |:----------------- |
| Nome | O nome da instância. |
| ID | O ID da instância. |
| Localização | O data center no qual a instância está hospedada. |
| Versão implementada | A versão implementada do  {{site.data.keyword.vmwaresolutions_short}}. |
| Versão do vCenter | A versão do VMware vCenter Server.<br><br>**Nota**: há uma pequena variação entre a versão do vCenter Server exibida no console do {{site.data.keyword.vmwaresolutions_short}} e do VMware vSphere Web Client. Ambos estão corretos. |
| NSX for vSphere | A versão do produto VMware NSX for vSphere. |
| Edição de licença NSX | A versão e a edição da licença do VMware NSX. |
| Versão do NetApp | A versão do NetApp ONTAP Select. |
| Tipo de licença do NetApp | O tipo da licença do NetApp ONTAP Select. |
| DNS, domínio-raiz | O nome de domínio-raiz é o nome de domínio DNS (Sistema de Nomes de Domínio) e o nome raiz da floresta do Microsoft Active Directory (AD) para a instância. |
| DNS, domínio SSO | O domínio SSO é o domínio de Conexão única do vSphere. O nome de domínio SSO é configurado para todas as instâncias implementadas do NetApp ONTAP Select com um valor de `vsphere.local`. |
| DNS, subdomínio | O subdomínio é o nome de subdomínio DNS do nome de domínio-raiz no qual os nomes de host da instância do NetApp ONTAP Select local residem. O nome de subdomínio está no formato `<subdomain_label>.<root_domain>`. |
| Status | O status da instância. |

## Visualizando informações de acesso para instâncias do NetApp ONTAP Select

Em **Informações de acesso**, visualize as informações de acesso dos componentes relacionados à instância. Essas senhas são senhas iniciais que são geradas pelo sistema. Se você as mudar fora do console do {{site.data.keyword.vmwaresolutions_short}}, elas não serão atualizadas na página de resumo da instância.

Tabela 3. Informações de acesso para componentes relacionados à instância do NetApp ONTAP Select

| Componente        | Descrição       |
|:---------------- |:----------------- |
| IPs do AD/DNS | Os endereços IP dos dois servidores AD. |
| AD/DNS FQDN | O nome completo do domínio do servidor AD/DNS. |
| ADMINISTRADOR DO AD/DNS (Área de trabalho remota) | O nome do usuário e a senha que podem ser usados para acessar o servidor AD por meio de uma conexão de área de trabalho remota. |
| IP do NSX Manager | O endereço IP do NSX Manager. |
| FQDN do NSX Manager | O nome completo do domínio do NSX Manager. |
| HTTP do NSX Manager | O nome do usuário e a senha que podem ser usados para acessar o console da web do NSX Manager. |
| NetApp Cluster IP | O endereço IP do cluster do NetApp ONTAP Select. |
| NetApp Cluster FQDN | O nome completo do domínio do cluster do NetApp ONTAP. |
| NetApp Cluster HTTPS | O nome do usuário e a senha que podem ser usados para acessar o cluster do NetApp ONTAP Select. |
| NetApp Deploy Tool IP | O endereço IP da máquina virtual do NetApp ONTAP Select Deploy. |
| NetApp Deploy Tool FQDN | O nome completo do domínio do NetApp ONTAP Select Deploy. |
| NetApp Deploy Tool HTTPS | O nome do usuário e a senha que podem ser usados para acessar a máquina virtual do NetApp ONTAP Select Deploy. |
| IP do PSC | O endereço IP do Platform Services Controller. |
| FQDN do PSC | O nome completo do domínio do PSC. |
| ADMINISTRADOR do PSC | O nome do usuário e a senha do VMware vCenter Single Sign-On que podem ser usados para acessar o console da web do PSC. |
| SSH do PSC | O nome do usuário e a senha que podem ser usados para acessar a VM do PSC por meio da conexão SSH. |
| IP do vCenter | O endereço IP do vCenter Server. |
| FQDN do vCenter | O nome completo do domínio do vCenter Server. |
| ADMINISTRADOR do vCenter | O nome do usuário e a senha do VMware vCenter Single Sign-On que podem ser usados para efetuar login no vCenter Server usando o vSphere Web Client. |
| SSH do vCenter | O nome do usuário e a senha que podem ser usados para acessar a VM do vCenter Server por meio da conexão SSH. |

## Visualizando o histórico de implementação para instâncias do NetApp ONTAP Select

Clique em **Histórico de implementação** na área de janela de navegação esquerda para visualizar o histórico de implementação da instância.

Tabela 4. Histórico de implementação de instância do NetApp ONTAP Select

| Item        | Descrição       |  
|:------------|:------------- |
| Data | A data e hora em que o status da instância muda |
| Resumo | Os detalhes da mudança |

Se ocorrerem erros durante a implementação ou exclusão da instância, a equipe de Suporte do {{site.data.keyword.cloud_notm}} será notificada automaticamente. Para consultar o status de seu chamado, é possível [entrar em contato com o Suporte IBM](../vmonic/trbl_support.html).

## Visualizando clusters do NetApp ONTAP Select

1. Clique em **Infraestrutura** na área de janela de navegação esquerda.
2. Em **CLUSTERS**, visualize o resumo sobre os clusters do NetApp ONTAP Select.

	Tabela 5: Itens de clusters do NetApp ONTAP Select

	 <table>
	   <tr>
	     <th>Item</th>
	     <th>Descrição</th>
	   </tr>
	   <tr>
	     <td>Nome</td>
	     <td>O nome do cluster.</td>
	   </tr>
	   <tr>
	     <td>Servidores ESXi</td>
	     <td>O número de servidores ESXi no cluster.</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>A especificação de CPU dos servidores ESXi no cluster.</td>
	   </tr>
	   <tr>
	      <td>Efetivo de armazenamento</td>
	      <td>A capacidade do disco total dos servidores ESXi no cluster.</td>
	   </tr>
	   <tr>
	      <td>Memória</td>
	      <td>O tamanho da memória total dos servidores ESXi no cluster.</td>
	   </tr>
	   <tr>
	      <td>Local do datacenter</td>
	      <td>O data center no qual o cluster está hospedado. É o mesmo com o local do data center da instância.</td>
	   </tr>
		 <tr>
		   <td>Pod</td>
			 <td>O pod no qual o cluster é criado.</td>
		 </tr>
		 <tr>
		  <td>Barra de Status</td>
			<td>O status do cluster. O status pode ter um dos valores a seguir:<ul><li>Inicializando: o cluster está sendo criado e configurado.</li><li>Modificando: O cluster está sendo modificado.</li><li>Pronto para uso: o cluster está pronto para uso.</li></ul></td>
		 </tr>
		 <tr>
		  <td>Ações</td>
			<td>Clique no ícone **Excluir** para excluir o cluster.</td>
		 </tr>
	 </table>

3. Clique no nome do cluster para visualizar os detalhes do servidor ESXi.

Tabela 6. Detalhes do servidor ESXi de um cluster do NetApp ONTAP Select

| Item        | Descrição       |  
|:------------|:----------------- |
| Nome | O nome do servidor ESXi está no formato `<host_prefix><n>.<subdomain_label>.<root_domain>`, em que:<br><br>`host_prefix` é o prefixo de nome do host, `n` é a sequência do servidor, `subdomain_label` é o rótulo do subdomínio e `root_domain` é o nome de domínio raiz. |
| Versão | A versão do servidor ESXi. |
| Credenciais | O nome de usuário e a senha para acessar o servidor ESXi. |
| IP privado | O endereço IP privado do servidor ESXi. |
| Status | O status do servidor ESXi, que pode ser um dos valores a seguir:<ul><li>Ativo: o servidor ESXi está pronto para uso.</li><li>Excluindo: o servidor ESXi está sendo excluído.</li></ul> |

## O que fazer a seguir

Gerencie suas instâncias do console do {{site.data.keyword.vmwaresolutions_short}}, do VMware vSphere Web Client ou do console do NetApp.

**Importante**: antes de clicar em **Console do vCenter** na página de resumo da instância para acessar o vSphere Web Client e começar a gerenciar os seus servidores do ESXi, deve-se efetuar login no portal da VPN do {{site.data.keyword.CloudDataCent_notm}}. Passe o mouse sobre o botão **console do vCenter** e siga as instruções para assegurar-se de que atenda a todos os requisitos e que tenha concluído as etapas necessárias antes de acessar o vSphere Web Client.

Revise os tópicos a seguir para obter informações que ajudarão a concluir as instruções de login:

*  Para obter os requisitos e as etapas necessárias antes de acessar o vSphere Web Client, veja [Tempo limite atingido ao se conectar ao vSphere Web Client](../vmonic/trbl_timeout_vc_console.html).
*  Para obter uma lista de pontos de acesso para efetuar login na Rede Privada da infraestrutura do {{site.data.keyword.cloud_notm}} usando a VPN, veja [Acesso à VPN](http://www.softlayer.com/vpn-access){:new_window}.
*  Se tiver problemas ao implementar um arquivo OVF (Open Virtualization Format) usando o vSphere Web Client, veja [Implementando um arquivo OVF usando o vSphere Web Client](../vmonic/trbl_deploy_ovf.html).

### Links relacionados

* [Pedindo instâncias do NetApp ONTAP Select](np_orderinginstances.html)
* [Excluindo instâncias do NetApp ONTAP Select](np_deletinginstance.html)
* [Anexar armazenamento dedicado a implementações do NetApp ONTAP Select](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)

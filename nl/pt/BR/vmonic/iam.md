---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# Gerenciando o acesso de usuário com o IAM

O acesso às instâncias de serviço do {{site.data.keyword.vmwaresolutions_full}} para os usuários em sua conta é controlado pelo {{site.data.keyword.cloud}} Identity and Access Management (IAM). Cada usuário que acessa os serviços do {{site.data.keyword.vmwaresolutions_short}} em sua conta deve ser designado a uma política de acesso com uma função de usuário do IAM definida.

A política de acesso determina as ações que o usuário pode executar dentro do contexto do serviço ou da instância que você seleciona. As ações permitidas são customizadas e definidas pelo serviço {{site.data.keyword.cloud_notm}} como operações que têm permissão para serem executadas no serviço. As ações são, então, mapeadas para funções de usuário do IAM.

As políticas permitem que o acesso seja concedido em diferentes níveis. Algumas das opções incluem os acessos a seguir:

* Acesso em todas as instâncias de serviço em sua conta
* Acesso a uma instância de serviço individual em sua conta
* Acesso a um recurso específico dentro de uma instância
* Acesso a todos os serviços ativados pelo IAM em sua conta

Depois de definir o escopo da política de acesso, você designa uma função.

Revise as informações a seguir, que descreve as ações que cada função permite dentro do serviço {{site.data.keyword.vmwaresolutions_short}}.

## Funções e permissões de gerenciamento de plataforma

As funções de gerenciamento de plataforma permitem que os usuários executem tarefas em recursos de serviço no nível de plataforma. Por exemplo, designe o acesso de usuário ao serviço, crie ou exclua IDs de serviço, crie instâncias e ligue instâncias a aplicativos.

A tabela a seguir fornece informações sobre as ações que são mapeadas para funções de gerenciamento de plataforma.

Tabela 1. Funções de gerenciamento de plataforma e ações permitidas

| Função de gerenciamento de plataforma | Ações | Exemplo de ações |
|:----------------- |:----------------- |:----------------- |
| Visualizador | Ações somente leitura | <ul><li>Visualizar o resumo de instâncias</li><li>Visualizar os detalhes de uma instância</li></ul>|
| Editor | Atualizar uma instância específica |<ul><li>Incluir ou remover servidores ESXi</li><li>Incluir ou remover clusters</li><li>Incluir ou remover serviços</li><li>Fazer upgrade de uma instância para uma versão superior</li></ul> |
| Operador | Ações somente leitura | <ul><li>Listar instâncias</li><li>Visualizar os detalhes de uma instância</li></ul> |
| Administrador | Acesso total ao gerenciamento |<ul><li>Criar novas instâncias</li><li>Excluir instâncias</li><li>Conceda acesso à plataforma a outros usuários</li></ul>|

Para  {{site.data.keyword.vmwaresolutions_short}}, existem as seguintes ações:

Tabela 2. Descrições de ação e funções necessárias

| Ação | Operação em serviço | Atribuição |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Criar novas instâncias | Administrador |
| vmware-solutions.instances.delete | Excluir instâncias | Administrador |
| vmware-solutions.instances.view | <ul><li>Listar instâncias</li><li>Visualizar os detalhes de uma instância</li></ul> | Visualizador, Operador, Editor e Administrador |
| vmware-solutions.instances.update | <ul><li>Incluir ou remover servidores ESXi</li><li>Incluir ou remover clusters</li><li>Incluir ou remover serviços</li><li>Fazer upgrade de uma instância para uma versão superior</li></ul> | Editor e Administrador |
| vmware-solutions.account.update | Atualizar configurações da conta | Administrador |

## Gerenciando o acesso para usuários

É possível incluir novos usuários na conta do {{site.data.keyword.cloud_notm}} para que esses usuários possam compartilhar os serviços e os recursos que são provisionados para a conta. Para obter mais informações, veja [Convidando usuários para acessar serviços e recursos](../vmonic/iamuserinvite.html).

Também é possível gerenciar o acesso para usuários existentes, incluindo a modificação de acesso existente, a designação de novo acesso e a revisão de acesso designado. Para gerenciar o acesso para usuários, deve-se ser o proprietário da conta ou ter a função de gerenciamento de plataforma **Administrador**. Para obter mais informações, veja [Gerenciando acesso ao IAM](../../../iam/mngiam.html).

## Migrando instâncias existentes para contas do IBM Cloud

Devido à integração do {{site.data.keyword.vmwaresolutions_short}} ao IAM, as instâncias que são implementadas na V2.5 e liberações mais recentes em sua conta do {{site.data.keyword.cloud}} são incluídas automaticamente em sua conta e são gerenciadas pelo IAM.

Para as suas instâncias existentes que foram implementadas na V2.4 e liberações anteriores, é possível migrá-las para as contas do {{site.data.keyword.cloud_notm}} especificadas para gerenciamento ativado pelo IAM. Para obter mais informações, veja os tópicos a seguir:
* [Migrando instâncias do vCenter Server anteriores à V2.5 para contas do IBM Cloud](../vcenter/vc_addinstancetousraccount.html)
* [Migrando instâncias do vCenter Server with Hybridity Bundle anteriores à V2.5 para contas do IBM Cloud](../vcenter/vc_hybrid_addinstancetousraccount.html)
* [Migrando instâncias do Cloud Foundation anteriores à V2.5 para contas do IBM Cloud](../sddc/sd_addinstancetousraccount.html)
* [Migrando instâncias do NetApp ONTAP Select anteriores à V2.5 para contas do IBM Cloud](../netapp/np_addinstancetousraccount.html)
* [Migrando instâncias do VMware Federal anteriores à V2.5 para contas do IBM Cloud](../vcenter/vc_fed_addinstancetousraccount.html)

### Links relacionados

* [ Gerenciando a identidade e o acesso ](../../../iam/quickstart.html)
* [ Gerenciando usuários e o acesso ](../../../iam/iamusermanage.html)
* [ O que é IAM ](../../../iam/index.html)

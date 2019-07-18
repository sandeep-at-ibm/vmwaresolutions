---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: IAM user, user role, user permission

subcollection: vmware-solutions


---

# Gerenciando o acesso de usuário com o IAM
{: #iam}

O acesso às instâncias de serviço do {{site.data.keyword.vmwaresolutions_full}} para os usuários em sua conta é controlado pelo {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Cada usuário que acessa os serviços do {{site.data.keyword.vmwaresolutions_short}} em sua conta deve ser designado a uma política de acesso com uma função de usuário do IAM definida.

A política de acesso determina as ações que o usuário pode executar dentro do contexto do serviço ou da instância que você seleciona. As ações permitidas são customizadas e definidas pelo serviço {{site.data.keyword.cloud_notm}} como operações que têm permissão para serem executadas no serviço. As ações são, então, mapeadas para funções de usuário do IAM.

As políticas permitem que o acesso seja concedido em diferentes níveis. Algumas das opções incluem os acessos a seguir:

* Acesso em todas as instâncias de serviço em sua conta
* Acesso a uma instância de serviço individual em sua conta
* Acesso a um recurso específico dentro de uma instância
* Acesso a todos os serviços ativados pelo IAM em sua conta

Depois de definir o escopo da política de acesso, você designa uma função.

Revise as informações a seguir, que descreve as ações que cada função permite dentro do serviço {{site.data.keyword.vmwaresolutions_short}}.

## Funções e permissões de gerenciamento de plataforma
{: #iam-roles}

As funções de gerenciamento de plataforma permitem que os usuários executem tarefas em recursos de serviço no nível de plataforma. Por exemplo, designe o acesso de usuário ao serviço, crie ou exclua IDs de serviço, crie instâncias e ligue instâncias a aplicativos.

A tabela a seguir fornece informações sobre as ações que são mapeadas para funções de gerenciamento de plataforma.

| Função de gerenciamento de plataforma | Ações | Exemplo de ações |
|:----------------- |:----------------- |:----------------- |
| Visualizador | Ações somente leitura | Visualizar o resumo de instâncias<br>Visualizar os detalhes de uma instância |
| Editor | Atualizar uma instância específica | Incluir ou remover servidores ESXi<br>Incluir ou remover clusters<br>Incluir ou remover serviços<br>Fazer upgrade de uma instância para uma versão superior |
| Operador | Ações somente leitura | Listar instâncias<br>Visualizar os detalhes de uma instância |
| Administrador | Acesso total ao gerenciamento | Criar novas instâncias<br>Excluir instâncias<br>Conceda acesso à plataforma a outros usuários|
{: caption="Tabela 1. Funções de gerenciamento de plataforma e ações permitidas" caption-side="top"}

Para  {{site.data.keyword.vmwaresolutions_short}}, existem as seguintes ações:

| Ação | Operação em serviço | Atribuição |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | Criar novas instâncias | Administrador |
| vmware-solutions.instances.delete | Excluir instâncias | Administrador |
| vmware-solutions.instances.view | Listar instâncias<br>Visualizar os detalhes de uma instância | Visualizador, Operador, Editor e Administrador |
| vmware-solutions.instances.update | Incluir ou remover servidores ESXi<br>Incluir ou remover clusters<br>Incluir ou remover serviços<br>Fazer upgrade de uma instância para uma versão superior | Editor e Administrador |
| vmware-solutions.account.update | Atualizar configurações da conta | Administrador |
{: caption="Tabela 2. Descrições de ação e funções necessárias" caption-side="top"}

## Gerenciando o acesso para usuários
{: #iam-users}

É possível incluir novos usuários na conta do {{site.data.keyword.cloud_notm}} para que esses usuários possam compartilhar os serviços e os recursos que são provisionados para a conta. Para obter mais informações, veja [Convidando usuários para acessar serviços e recursos](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite).

Também é possível gerenciar o acesso para usuários existentes, incluindo a modificação de acesso existente, a designação de novo acesso e a revisão de acesso designado. Para gerenciar o acesso para usuários, deve-se ser o proprietário da conta ou ter a função de gerenciamento de plataforma **Administrador**. Para obter mais informações, consulte [Gerenciando o acesso a recursos](/docs/iam?topic=iam-iammanidaccser).

## Migrando instâncias existentes para contas do IBM Cloud
{: #iam-migrate}

Devido à integração do {{site.data.keyword.vmwaresolutions_short}} ao IAM, as instâncias que são implementadas na V2.5 e liberações mais recentes em sua conta do {{site.data.keyword.cloud_notm}} são incluídas automaticamente em sua conta e são gerenciadas pelo IAM.

Para as suas instâncias existentes que foram implementadas na V2.4 e liberações anteriores, é possível migrá-las para as contas do {{site.data.keyword.cloud_notm}} especificadas para gerenciamento ativado pelo IAM. Para obter mais informações, veja os tópicos a seguir:
* [Migrando instâncias do vCenter Server pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [Migrando instâncias do vCenter Server with Hybridity Bundle pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [Migrando instâncias do NetApp ONTAP Select pré-V2.5 para contas do IBM Cloud](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## Links relacionados
{: #iam-related}

* [ Gerenciando a identidade e o acesso ](/docs/iam?topic=iam-getstarted)
* [Convidando usuários](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [ O que é IAM ](/docs/iam?topic=iam-iamoverview)

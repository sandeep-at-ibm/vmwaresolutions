---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-14"

keywords: set credentials, user credentials, set notifications

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Gerenciando contas de usuário e configurações
{: #useraccount}

O {{site.data.keyword.vmwaresolutions_full}} se comunica com a infraestrutura do {{site.data.keyword.cloud_notm}} por meio de chamadas do {{site.data.keyword.slapi_short}}. Para acessar o {{site.data.keyword.slapi_short}} com segurança, deve-se vincular as credenciais de sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} à sua conta do {{site.data.keyword.cloud_notm}}.

Também é possível especificar se você deseja receber notificações por e-mail e do console para vários eventos.

## Antes de iniciar
{: #useraccount-reqs}

* É possível vincular somente uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} a uma conta do usuário do {{site.data.keyword.cloud_notm}}.
* A conta de infraestrutura do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, consulte [Requisitos da conta de infraestrutura do {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req).
* Se a chave API para sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} muda, deve-se atualizar a chave na página **Configurações** no console do {{site.data.keyword.vmwaresolutions_short}}.

   É sua responsabilidade assegurar que a chave de API salva na página **Configurações** esteja correta e atualizada. Caso contrário, as operações que requerem validação da chave API podem falhar.
   {:important}

## Procedimento para configurar notificações
{: #useraccount-set-notif}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Configurações** na área de janela de navegação esquerda.
2. Se você desejar ser notificado por e-mail quando eventos ocorrerem, clique em **Ativar notificações por e-mail**.
3. Se você desejar ser notificado no console quando eventos ocorrerem, clique em **Ativar notificações do console**.

## Procedimento para configurar as credenciais de conta do usuário
{: #useraccount-set-cred}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Configurações** na área de janela de navegação esquerda.
2. Na área **Credenciais de infraestrutura do IBM Cloud**, revise as informações para as etapas que precisam ser executadas.
3. Se você tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} e uma conta do {{site.data.keyword.cloud_notm}} vinculadas, clique em **Recuperar** para concluir as credenciais automaticamente.
4. Caso você tenha uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} e uma conta do {{site.data.keyword.cloud_notm}} não vinculadas, deve-se vinculá-las. Siga as instruções em [Vinculando contas do IBMid](/docs/account?topic=account-unifyingaccounts#link_accounts) e, em seguida, clique em **Recuperar** para concluir as credenciais automaticamente.
5. Se você não tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} e não tiver uma conta faturável do {{site.data.keyword.cloud_notm}}, primeiro [faça upgrade de sua conta](/docs/account?topic=account-upgrading-account) e, em seguida, [crie uma chave de API de infraestrutura clássica](/docs/iam?topic=iam-classic_keys).
6. Caso você não tenha uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} e tenha uma conta faturável do {{site.data.keyword.cloud_notm}}, deve-se [criar uma chave de API de infraestrutura clássica](/docs/iam?topic=iam-classic_keys).
7. Clique em **Salvar Credenciais**.

## Resultados
{: #useraccount-results}

Depois que a conta do {{site.data.keyword.cloud_notm}} e a conta de infraestrutura do {{site.data.keyword.cloud_notm}} são vinculadas, o console recupera automaticamente as credenciais de conta de infraestrutura do {{site.data.keyword.cloud_notm}} para se comunicar com o ambiente do VMware no {{site.data.keyword.cloud_notm}}.

As credenciais de conta de infraestrutura armazenadas do {{site.data.keyword.cloud_notm}} são usadas em operações futuras que requerem interação com a infraestrutura do {{site.data.keyword.cloud_notm}}.

Se as notificações por e-mail ou de console estiverem ativadas para determinados eventos de instância, você será notificado por e-mail ou mensagens do console quando esses eventos ocorrerem.

## Links relacionados
{: #useraccount-related}

* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Pedindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Notificações](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)
* [SoftLayer API](/docs/customer-portal?topic=customer-portal-customerportal_api)

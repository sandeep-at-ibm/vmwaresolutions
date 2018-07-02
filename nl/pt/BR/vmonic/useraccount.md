---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-03"

---

# Gerenciando contas de usuário e configurações

O {{site.data.keyword.vmwaresolutions_full}} se comunica com a infraestrutura do {{site.data.keyword.cloud_notm}} por meio de chamadas do {{site.data.keyword.slapi_short}}. Para acessar o {{site.data.keyword.slapi_short}} com segurança, deve-se associar as credenciais de sua conta {{site.data.keyword.cloud_notm}} à sua conta de usuário {{site.data.keyword.vmwaresolutions_short}}.

**Nota**: a conta {{site.data.keyword.cloud_notm}} era conhecida anteriormente como a conta IBM SoftLayer.

No console do {{site.data.keyword.vmwaresolutions_short}}, é possível também especificar se você deseja receber notificações por e-mail para vários eventos.

## Antes de iniciar

* É possível associar apenas uma conta {{site.data.keyword.cloud_notm}} à sua conta de usuário {{site.data.keyword.vmwaresolutions_short}}.
* A conta do {{site.data.keyword.cloud_notm}} que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos da conta {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).
* Se a chave API de sua conta {{site.data.keyword.cloud_notm}} mudar, deve-se atualizar a chave em sua conta de usuário {{site.data.keyword.vmwaresolutions_short}}.

   **Importante**: é sua responsabilidade assegurar que a chave API que é salva na página **Configurações** esteja correta e atualizada.
   Caso contrário, as operações que requerem validação da chave API podem falhar.

Para associar a conta {{site.data.keyword.vmwaresolutions_short}} à conta {{site.data.keyword.cloud_notm}}, insira as credenciais de conta {{site.data.keyword.cloud_notm}} na página **Configurações** no console do {{site.data.keyword.vmwaresolutions_short}}.

Depois de associar a conta {{site.data.keyword.cloud_notm}}, o console recupera automaticamente as credenciais de conta {{site.data.keyword.cloud_notm}} para se comunicar com seu ambiente VMware no {{site.data.keyword.cloud_notm}}.

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Configurações** na área de janela de navegação esquerda.
2. Se desejar ser notificado por e-mail quando novos eventos ocorrem, marque a caixa de seleção **Ativar notificações por e-mail**.
3. Se desejar ser notificado no console quando novos eventos ocorrem, marque a caixa de seleção **Ativar notificações do console**.
4. Na área **Credenciais de infraestrutura do IBM Cloud**, insira o nome de usuário de sua conta {{site.data.keyword.cloud_notm}} e, em seguida, siga as instruções no console para inserir a chave de {{site.data.keyword.slapi_short}}.
5. Clique em **Salvar Credenciais**.

## Resultados

As credenciais de conta {{site.data.keyword.cloud_notm}} armazenadas são usadas em operações futuras que requerem interação com a infraestrutura do {{site.data.keyword.cloud_notm}}. Se as notificações por e-mail ou por console forem ativadas para certos eventos de instância, você será notificado por mensagens de e-mail ou mensagens de console quando ocorrerem esses eventos.

## Links relacionados

* [Perguntas mais frequentes](faq.html)
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Notificações](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}

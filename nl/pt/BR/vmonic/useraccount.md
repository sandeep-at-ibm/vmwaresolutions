---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-16"

---

# Gerenciando contas de usuário e configurações

O {{site.data.keyword.vmwaresolutions_full}} se comunica com a infraestrutura do {{site.data.keyword.cloud_notm}} por meio de chamadas do {{site.data.keyword.slapi_short}}. Para acessar o {{site.data.keyword.slapi_short}} com segurança, deve-se vincular as credenciais de sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) à sua conta do {{site.data.keyword.cloud_notm}}.

**Nota**: a conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) era conhecida anteriormente como a conta do IBM SoftLayer.

Também é possível especificar se você deseja receber notificações por e-mail e do console para vários eventos.

## Antes de iniciar

* É possível vincular somente uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) a uma conta do usuário do {{site.data.keyword.cloud_notm}}.
* A conta e infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) que você está usando deve atender a determinados requisitos. Para obter mais informações, veja [Requisitos de conta de infraestrutura do {{site.data.keyword.cloud_notm}}](slaccountrequirement.html).
* Caso a chave API para sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) mude, deve-se atualizar a chave na página **Configurações** no console do {{site.data.keyword.vmwaresolutions_short}}.

   **Importante**: é sua responsabilidade assegurar que a chave API que é salva na página **Configurações** esteja correta e atualizada. Caso contrário, as operações que requerem validação da chave API podem falhar.

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Configurações** na área de janela de navegação esquerda.
2. Na área **Notificações**, especifique suas configurações de notificação.
   * Se você desejar ser notificado por e-mail quando eventos ocorrerem, clique em **Ativar notificações por e-mail**.
   * Se você desejar ser notificado no console quando eventos ocorrerem, clique em **Ativar notificações do console**.
3. Na área **Credenciais de infraestrutura do IBM Cloud**, insira o nome do usuário e a chave API de sua conta de infraestrutura do
{{site.data.keyword.cloud_notm}} (SoftLayer):
   * Se sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) e sua conta do {{site.data.keyword.cloud_notm}} estiverem vinculadas, clique em **Recuperar** para inserir as credenciais automaticamente.
   * Se sua conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) e sua conta do {{site.data.keyword.cloud_notm}} não estão vinculadas, deve-se vinculá-las. Efetue login no [Portal do cliente de infraestrutura do{{site.data.keyword.cloud_notm}}](https://control.softlayer.com/) e siga as instruções no console para obter as credenciais e, em seguida, insira-as.
   * Se você não tiver uma conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer), [se inscreva para obter uma](../vmonic/signing_softlayer_account.html), siga as instruções no console para obter as credenciais e, em seguida, insira-as.
4. Clique em **Salvar Credenciais**.

## Resultados

Depois que a conta do {{site.data.keyword.cloud_notm}} e a conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) estiverem vinculadas, o console recuperará automaticamente as credenciais de conta da infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) para se comunicar com seu ambiente do VMware no {{site.data.keyword.cloud_notm}}.

As credenciais de conta de infraestrutura do {{site.data.keyword.cloud_notm}} (SoftLayer) armazenadas são usadas em operações futuras que requerem interação com a infraestrutura do {{site.data.keyword.cloud_notm}}.

Se as notificações por e-mail ou de console estiverem ativadas para determinados eventos de instância, você será notificado por e-mail ou mensagens do console quando esses eventos ocorrerem.

### Links relacionados

* [Perguntas mais frequentes](faq.html)
* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Pedindo instâncias do vCenter Server](../vcenter/vc_orderinginstance.html)
* [Notificações](notifications.html)
* [SoftLayer API](../../../customer-portal/cpapi.html){:new_window}

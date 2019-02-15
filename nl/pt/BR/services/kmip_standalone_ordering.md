---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# Pedindo instâncias do KMIP for VMware on IBM Cloud

É possível pedir uma instância do KMIP for VMware on {{site.data.keyword.cloud}} sem associá-la a nenhuma instância do VMware para gerenciamento flexível do serviço e das instâncias.

## Antes de iniciar

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Contas e configurações do usuário](/docs/services/vmwaresolutions/vmonic/useraccount.html).
*  Você revisou todas as considerações em
[Considerações ao instalar
instâncias do KMIP for VMware on {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html).

## Pedindo instâncias do KMIP for VMware on IBM Cloud

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Introdução** na área de janela de navegação esquerda.
2. Na área **Pedir serviços adicionais**, clique em **KMIP for VMware on IBM Cloud**.
3. Na página **KMIP for VMware on IBM Cloud**, defina as configurações de serviço conforme necessário.
4. Clique em **Provisão**.

## Configuração do serviço KMIP for VMware on IBM Cloud

Quando você pedir esse serviço, forneça as configurações a seguir:

### Nome da instância

Especifique um nome para a instância do KMIP for VMware {{site.data.keyword.cloud_notm}}.

### Região do serviço

Selecione a região do {{site.data.keyword.cloud_notm}} na qual a instância do KMIP for VMware {{site.data.keyword.cloud_notm}} deve ser hospedada.

O {{site.data.keyword.cloud_notm}} mantém um terminal de serviço KMIP para VMware no {{site.data.keyword.cloud_notm}} altamente disponível em cada região em que o serviço está disponível.

Tabela 1. Regiões do terminal do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Região         | Terminais               |
|:---------------|:-----------------------|
| Alemanha        |  <ul><li><code> kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696 </code></li><li><code> kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696 </code></li></ul> |
| Tóquio          | <ul><li><code> kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696 </code></li><li><code> kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696 </code></li></ul> |
| Sul dos EUA       |  <ul><li><code> kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696 </code></li><li><code> kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696 </code></li></ul> |

### Chave API para o ID do serviço

Insira a chave API para o ID do serviço do {{site.data.keyword.cloud_notm}} que é usado para acessar a instância do IBM Key Protect Service.

### Instância do Key Protect

Clique em **Recuperar** para obter a lista de instâncias disponíveis do IBM Key Protect Service e selecione aquela a ser usada para o gerenciamento de chave.

### Chave raiz do cliente

Clique em **Recuperar** para obter a chave raiz do cliente que está armazenada em sua instância selecionada do IBM Key Protect.

## Resultados

O pedido da instância é iniciado automaticamente. Você recebe a confirmação de que o pedido está sendo processado e pode verificar o status do pedido visualizando os detalhes da instância.

Quando a instância estiver pronta para uso, o status da instância será mudado para **Instalado** e você receberá uma notificação por e-mail.

## O que fazer a seguir

Inclua certificados de cliente para a instância do KMIP for VMware on {{site.data.keyword.cloud_notm}} que você pediu. Para obter mais informações, consulte [Incluindo, visualizando e excluindo certificados para instâncias do KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html).

### Links relacionados

* [Visualizando as instâncias do KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [Excluindo o KMIP for VMware em {{site.data.keyword.cloud_notm}} instâncias](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [Eventos do Activity Tracker](/docs/services/vmwaresolutions/vmonic/at-events.html)

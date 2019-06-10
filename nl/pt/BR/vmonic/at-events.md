---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-03"

subcollection: vmware-solutions


---

# Eventos do Activity Tracker
{: #at-events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para rastrear como os usuários e aplicativos interagem com o {{site.data.keyword.vmwaresolutions_short}} no {{site.data.keyword.Bluemix_notm}}.

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.Bluemix_notm}}. Para obter mais informações, consulte o [Sobre o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

## Tabela de eventos do Activity Tracker
{: #at-events-table}

Verifique a tabela a seguir para obter a descrição das colunas na tabela de eventos do Activity Tracker.

Tabela 1. Descrição da tabela de eventos do Activity Tracker

| Coluna                | Tipo de valor | Descrição |
|:----------------------|:-----------|:------------|
| Horário                  | N/A        | A data e hora em que o evento é criado. |
| initiator.name        | Cadeia     | O IBMid do usuário que inicia a ação. |
| target_name           | Cadeia     | O recurso no qual a ação é executada. |
| target.typeURI        | Cadeia     | O Identificador Exclusivo Universal (UUID) do destino no qual a ação é executada. |
| action                | Cadeia     | A ação que aciona o evento. Os valores válidos são `create`, `update` e `delete`. |
| resultado               | Cadeia     | O resultado da ação. O valor é `success`, `failure` ou `pending`. |
| código_de_razão     | Inteiro    | O código de razão do resultado. |
| initiator_host_address| Cadeia     | O endereço IP do qual a solicitação vem. |

Para obter mais informações, veja [Campos de eventos do Activity Tracker](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event).

## Rastreando eventos de gerenciamento de instância
{: #at-events-instance-mgmt}

Quando você gerencia contas do usuário, instâncias, clusters e serviços no {{site.data.keyword.vmwaresolutions_short}}, um evento é gerado e enviado para o **domínio de contas** no Activity Tracker.

Verifique a tabela a seguir para obter as ações que geram e enviam eventos de gerenciamento para o Activity Tracker.

Tabela 2. Descrição de ações que geram eventos de gerenciamento

| Ação                                   | Descrição | Resultado |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.user_account.update`    | <ul><li>A solicitação para atualizar a conta do usuário é recebida.</li><li>A solicitação para atualizar a conta do usuário é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.notification.update` | <ul><li>A solicitação para atualizar notificações é recebida.</li><li>A solicitação para atualizar notificações é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.secure_data.wipe`       | <ul><li>A solicitação para apagar os dados seguros é recebida.</li><li>A solicitação para apagar os dados seguros é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.bss_account.migrate` | <ul><li>A solicitação para migrar para a conta bss é recebida.</li><li>A solicitação para migrar para a conta bss é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.order`                 | <ul><li>A solicitação para pedir uma instância do vCenter Server é recebida.</li><li>A solicitação para pedir uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.delete`                | <ul><li>A solicitação para excluir uma instância do vCenter Server é recebida.</li><li>A solicitação para excluir uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.add_host`              | <ul><li>A solicitação para incluir servidores ESXi em uma instância do vCenter Server é recebida.</li><li>A solicitação para incluir servidores ESXi em uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.remove_hosts`          | <ul><li>A solicitação para excluir servidores ESXi de uma instância do vCenter Server é recebida.</li><li>A solicitação para excluir servidores ESXi de uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.schedule_update`       | <ul><li>A solicitação para planejar uma atualização para uma instância do vCenter Server é recebida.</li><li>A solicitação para planejar uma atualização para uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.create_cluster`        | <ul><li>A solicitação para criar um cluster para uma instância do vCenter Server é recebida.</li><li>A solicitação para criar um cluster para uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.delete_cluster`        | <ul><li>A solicitação para excluir o cluster de uma instância do vCenter Server é recebida.</li> <li>A solicitação para excluir o cluster de uma instância do vCenter Server é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.update_nsx_license`        | <ul><li>A solicitação para atualizar a licença do VMware NSX é recebida.</li><li>A solicitação para atualizar a licença do VMware NSX é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vcs.upgrade_to_hybridity`   | <ul><li>A solicitação para fazer upgrade de uma instância do vCenter Server para uma instância do vCenter Server with Hybridity Bundle é recebida.</li><li>A solicitação para fazer upgrade de uma instância do vCenter Server para uma instância do vCenter Server with Hybridity Bundle é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vsphere.order`              | <ul><li>A solicitação para pedir um cluster do vSphere é recebida.</li><li>A solicitação para pedir um cluster do vSphere é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vsphere.update`             | <ul><li>A solicitação para atualizar um cluster do vSphere é recebida.</li><li>A solicitação para atualizar um cluster do vSphere é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.vsphere.save_template`      | <ul><li>A solicitação para salvar a configuração de um cluster do vSphere é recebida.</li><li>A solicitação para salvar a configuração de um cluster do vSphere é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.netapp.order`               | <ul><li>A solicitação para pedir uma instância do NetApp ONTAP Select é recebida.</li><li>A solicitação para pedir uma instância do NetApp ONTAP Select é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.netapp.delete`              | <ul><li>A solicitação para excluir uma instância do NetApp ONTAP Select é recebida.</li><li>A solicitação para excluir uma instância do NetApp ONTAP Select é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.service_variable.update`    | <ul><li>A solicitação para atualizar a configuração de um serviço é recebida.</li><li>A solicitação para atualizar a configuração de um serviço é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.service.order`              | <ul><li>A solicitação para pedir um serviço para uma instância é recebida.</li><li>A solicitação para pedir um serviço para uma instância é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.service.delete_by_id`       | <ul><li>A solicitação para excluir um serviço de uma instância é recebida.</li><li>A solicitação para excluir um serviço de uma instância é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.service.upgrade_to_hybridity` | <ul><li>A solicitação para fazer upgrade de uma instância existente do vCenter Server para uma instância do vCenter Server with Hybridity Bundle é recebida.</li><li>A solicitação para fazer upgrade de uma instância existente do vCenter Server para uma instância do vCenter Server with Hybridity Bundle é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.service.deploy` | A ação para implementar um serviço em uma instância é executada. | `success` |
| `vmware-solutions.service.undeploy` | A ação para remover um serviço de uma instância é executada. | `success` |

## Rastreando eventos para o serviço KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Ao gerenciar chaves para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}, um evento é gerado e enviado para o **domínio de contas** no Activity Tracker.

Verifique a tabela a seguir para obter as ações que geram e enviam eventos para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Tabela 3. Descrição de ações que geram eventos para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Ação                                      | Descrição                               | Resultado |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.key.create`               | <ul><li>A solicitação para criar uma chave é recebida.</li><li>A solicitação para criar uma chave é respondida.</li></ul> | <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.key.get`                  | <ul><li>A solicitação para obter o conteúdo de uma chave é recebida.</li><li>A solicitação para obter o conteúdo de uma chave é respondida.</li></ul> |  <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.key.get_attributes`       | <ul><li>A solicitação para obter os atributos de uma chave é recebida.</li><li>A solicitação para obter os atributos de uma chave é respondida.</li></ul> |  <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.key.activate`             | <ul><li>A solicitação para ativar uma chave é recebida.</li><li>A solicitação para ativar uma chave é respondida.</li></ul> |  <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.key.revoke`               | <ul><li>A solicitação para revogar uma chave é recebida.</li><li>A solicitação para revogar uma chave é respondida.</li></ul> |  <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.key.destroy`              | <ul><li>A solicitação para destruir uma chave é recebida.</li><li>A solicitação para destruir uma chave é respondida.</li></ul> |  <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |
| `vmware-solutions.key.discover_versions`    | <ul><li>A solicitação para localizar a versão do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} é recebida.</li><li>A solicitação para localizar a versão do serviço KMIP for VMware on {{site.data.keyword.cloud_notm}} é respondida.</li></ul> |  <ul><li>` pendente `</li><li>` success `  ou  ` failure `</li></ul> |

## Onde visualizar os eventos
{: #at-events-viewing}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no
{{site.data.keyword.cloudaccesstrailshort}} **domínio de contas** disponível na região do
{{site.data.keyword.Bluemix_notm}} na qual eles são gerados.

## Links relacionados
{: #at-events-related}

* [ Rastreador de Atividades de Fornecimento ](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [Navegando até o painel do Activity Tracker no Console do {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [ Visão geral do KMIP for VMware on  {{site.data.keyword.cloud_notm}}  overview ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

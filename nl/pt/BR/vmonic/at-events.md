---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-17"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Eventos de rastreador de atividade
{: #at-events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para rastrear como os usuários e aplicativos interagem com o {{site.data.keyword.vmwaresolutions_short}} no {{site.data.keyword.cloud_notm}}.

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte o [Sobre o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

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
| `vmware-solutions.account-apikey.update` |	A chave de API da infraestrutura de uma conta é atualizada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.account-notification.update` | A configuração de notificação de uma conta é atualizada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | Os dados protegidos da instância são limpos. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	Uma instância é migrada para uma conta BSS. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs.create` |	Uma instância do vCenter Server é criada. |` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs.delete` |	Uma instância do vCenter Server é excluída. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-host.add` |	Um host é incluído em uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |	Um host é removido de uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs.update`	| Uma instância do vCenter Server é atualizada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	| Um cluster é criado para uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	| Um cluster é excluído de uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	| A licença do NSX é atualizada para uma instância do servidor vCenter. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	| O Hybridity Bundle é submetido a upgrade para uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	| O Hybridity Bundle é removido de uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	| O armazenamento NFS é incluído em uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	| O armazenamento NFS é removido de uma instância do vCenter Server. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	| O plano de uma instância do vCenter Server é atualizado. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vss.create`	| Uma instância do vSphere é criada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vss.update`	| Uma instância do vSphere é atualizada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.vss-template.remove` |	Um modelo do vSphere é removido. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.service.create`	| Um serviço é criado. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.service.delete`	| Um serviço é excluído. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` | Um Hybridity Bundle é submetido a upgrade para `version`. | ` pendente `<br>`sucesso`<br>`failure` |

## Rastreando eventos para o serviço KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Ao gerenciar chaves para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}, um evento é gerado e enviado para o **domínio de contas** no Activity Tracker.

Verifique a tabela a seguir para obter as ações que geram e enviam eventos para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}.

Tabela 3. Descrição de ações que geram eventos para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Ação                                      | Descrição                               | Resultado |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |	Uma chave KMIP é criada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |	Uma chave KMIP é recuperada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |	Os atributos de uma chave KMIP são recuperados. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |	Uma chave KMIP é ativada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |	Uma chave KMIP é revogada. | ` pendente `<br>`sucesso`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |	Uma chave KMIP é destruída. | ` pendente `<br>`sucesso`<br>`failure` |

## Onde visualizar os eventos
{: #at-events-viewing}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no
{{site.data.keyword.cloudaccesstrailshort}} **domínio de contas** disponível na região do
{{site.data.keyword.cloud_notm}} na qual eles são gerados.

## Links relacionados
{: #at-events-related}

* [ Rastreador de Atividades de Fornecimento ](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-provision)
* [Navegando para o painel do Activity Tracker no Console do {{site.data.keyword.cloud_notm}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui)
* [ Visão geral do KMIP for VMware on  {{site.data.keyword.cloud_notm}}  overview ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

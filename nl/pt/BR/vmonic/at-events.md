---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-23"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Eventos de rastreador de atividade
{: #at-events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para rastrear como os usuários e aplicativos interagem com o {{site.data.keyword.vmwaresolutions_short}} no {{site.data.keyword.cloud_notm}}.

O {{site.data.keyword.at_full_notm}} registra as atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. É possível usar esse serviço para investigar atividades anormais e ações críticas e preencher os requisitos de auditoria regulamentares. Além disso, é possível receber alertas sobre as ações conforme elas acontecem. Os eventos que são coletados obedecem ao padrão Cloud Auditing Data Federation (CADF). Para obter mais informações, consulte [{{site.data.keyword.cloud_notm}} Activity Tracker com LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Rastreando eventos de gerenciamento de instância
{: #at-events-instance-mgmt}

Quando você gerencia contas do usuário, instâncias, clusters e serviços no {{site.data.keyword.vmwaresolutions_short}}, um evento é gerado e enviado para um domínio global ou para uma instância do serviço no local em que o serviço é provisionado. Para obter mais informações, consulte [Monitorando eventos globais e baseados em local](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

A tabela a seguir fornece as ações que geram e enviam eventos de gerenciamento para o Activity Tracker.

| Ação                                   | Descrição |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | A chave de API da infraestrutura de uma conta é atualizada. |
| `vmware-solutions.account-notification.update` | A configuração de notificação de uma conta é atualizada. |
| `vmware-solutions.instance-secure-data.wipe` | Os dados protegidos da instância são limpos. |
| `vmware-solutions.instance-bss-account.migrate` |	Uma instância é migrada para uma conta BSS. |
| `vmware-solutions.vcs.create` | Uma instância do vCenter Server é criada. |
| `vmware-solutions.vcs.delete` | Uma instância do vCenter Server é excluída. |
| `vmware-solutions.vcs-host.add` | Um host é incluído em uma instância do vCenter Server. |
| `vmware-solutions.vcs-host.remove` | Um host é removido de uma instância do vCenter Server. |
| `vmware-solutions.vcs.update` | Uma instância do vCenter Server é atualizada. |
| `vmware-solutions.vcs-cluster.create` | Um cluster é criado para uma instância do vCenter Server. |
| `vmware-solutions.vcs-cluster.delete` | Um cluster é excluído de uma instância do vCenter Server. |
| `vmware-solutions.vcs-nsx-license.update` | A licença do NSX é atualizada para uma instância do servidor vCenter. |
| `vmware-solutions.vcs-nfs-storage.add` | O armazenamento NFS é incluído em uma instância do vCenter Server. |
| `vmware-solutions.vcs-nfs-storage.remove` | O armazenamento NFS é removido de uma instância do vCenter Server. |
| `vmware-solutions.vcs-plan.update` | O plano de uma instância do vCenter Server é atualizado. |
| `vmware-solutions.vss.create` | Uma instância do vSphere é criada. |
| `vmware-solutions.vss.update` | Uma instância do vSphere é atualizada. |
| `vmware-solutions.vss-template.remove` | Um modelo do vSphere é removido. |
| `vmware-solutions.service.create` | Um serviço é criado. |
| `vmware-solutions.service.delete` | Um serviço é excluído. |
{: caption="Tabela 1. Descrição de ações que geram eventos de gerenciamento" caption-side="top"}

## Rastreando eventos para o serviço KMIP for VMware on IBM Cloud
{: #at-events-kmip}

Ao gerenciar chaves para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}, um evento é gerado e enviado para um domínio global ou para uma instância do serviço no local em que o serviço é provisionado. Para obter mais informações, consulte [Monitorando eventos globais e baseados em local](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

A tabela a seguir fornece as ações que geram e enviam eventos para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}.

| Ação                                      | Descrição                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | Uma chave KMIP é criada. |
| `vmware-solutions.kmip-key.retrieve` | Uma chave KMIP é recuperada. |
| `vmware-solutions.kmip-key-attributes.retrieve` | Os atributos de uma chave KMIP são recuperados. |
| `vmware-solutions.kmip-key.activate` | Uma chave KMIP é ativada. |
| `vmware-solutions.kmip-key.revoke` | Uma chave KMIP é revogada. |
| `vmware-solutions.kmip-key.destroy` | Uma chave KMIP é destruída. |
{: caption="Tabela 2. Descrição de ações que geram eventos para o serviço KMIP for VMware on {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Onde visualizar os eventos
{: #at-events-viewing}

Os eventos estão disponíveis no local **Frankfurt**.

Há somente 1 instância do {{site.data.keyword.at_full_notm}} por local. Para visualizar eventos, deve-se acessar a IU da web do serviço {{site.data.keyword.at_full_notm}} no local **EU-DE**. Para obter mais informações, consulte [Ativando a IU da web por meio da IU do IBM Cloud](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## Links relacionados
{: #at-events-related}

* [Provisionando uma instância](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Navegando para a UI da web](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [ Visão geral do KMIP for VMware on  {{site.data.keyword.cloud_notm}}  overview ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

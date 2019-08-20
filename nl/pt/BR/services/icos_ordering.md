---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-11"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo e configurando o IBM Cloud Object Storage com o Veeam
{: #icos_ordering}

Com a liberação do Veeam Availability Suite 9.5 Atualização 4, o Veeam é compatível com o IBM Cloud Object Storage (ICOS). O pedido do IBM Cloud Object Storage não é automatizado quando você pede o Veeam on IBM Cloud, mas pode ser incluído após a implementação.

Para pedir o IBM Cloud Object Storage, conclua as tarefas a seguir no pedido especificado.

## Criando uma instância do Object Storage
{: #icos_ordering-obj}

Para criar uma instância do Object Storage, consulte [Criando uma nova instância de serviço](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance). Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Criando um depósito
{: #icos_ordering-bucket}

Para criar um bucket, consulte [Criar alguns buckets para armazenar seus dados](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets). Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Criando credenciais de serviço
{: #icos_ordering-service-cred}

Para criar credenciais de serviço, incluindo credenciais do HMAC, consulte [Credenciais de serviço](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Incluindo um repositório de dimensionamento
{: #icos_ordering-scale-repo}

* Como parte da instalação e configuração do serviço Veeam, um repositório de backup de ampliação com o nome `IC4V Scale-Out Repository` é criado. O `IC4V Default VM Backup Repository` é incluído no repositório de ampliação como uma extensão.
* Ao criar a tarefa de backup, deve-se selecionar `IC4V Scale-Out Repository` como o repositório de backup e não `IC4V Default Config Backup Repository`. O último repositório deve ser usado para os backups de configuração do Veeam.
* É possível incluir mais repositórios nesse repositório padrão, como um repositório de backup do tipo Object Storage. Para obter mais informações, consulte [Incluindo repositórios de ampliação](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:external}. Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Mantendo e gerenciando a sua camada de nuvem
{: #icos_ordering-manage-cloud}

Para obter mais informações, consulte [Gerenciando dados da camada de capacidade](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:external}.

## Links relacionados
{: #icos_ordering-related}

* [Veeam no {{site.data.keyword.cloud_notm}} visão geral](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Pedindo o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Gerenciando o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Serviços gerenciados para o Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Veeam on {{site.data.keyword.cloud_notm}} - Demos](https://www.ibm.com/demos/collection/Veeam-on-IBM-Cloud/){:external}

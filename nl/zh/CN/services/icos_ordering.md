---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 通过 Veeam 订购和配置 IBM Cloud Object Storage
{: #icos_ordering}

Veeam Availability Suite 9.5 Update 4 发布后，现在 Veeam 与 IBM Cloud Object Storage (ICOS) 兼容。订购 Veeam on IBM Cloud 时，不会自动订购 IBM Cloud Object Storage，但可以在部署后添加 IBM Cloud Object Storage。

要订购 IBM Cloud Object Storage，请按指定的顺序完成以下任务。

## 创建 Object Storage 实例
{: #icos_ordering-obj}

要创建 Object Storage 实例，请参阅[创建新服务实例](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-order-storage#creating-a-new-service-instance)。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 创建存储区
{: #icos_ordering-bucket}

要创建存储区，请参阅[创建一些存储区来存储数据](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-getting-started-tutorial#gs-create-buckets)。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 创建服务凭证
{: #icos_ordering-service-cred}

要创建服务凭证（包括 HMAC 凭证），请参阅[服务凭证](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 添加横向扩展存储库
{: #icos_ordering-scale-repo}

要在 Veeam 中添加横向扩展存储库，请参阅[添加横向扩展存储库](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 维护和管理云层
{: #icos_ordering-manage-cloud}

有关维护和管理云层的信息，请参阅[管理容量层数据](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}。

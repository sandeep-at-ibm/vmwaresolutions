---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: IBM Cloud Object Storage, ICOS configuration, order Cloud Object Storage

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 通过 Veeam 订购和配置 IBM Cloud Object Storage
{: #icos_ordering}

Veeam Availability Suite 9.5 Update 4 发布后，现在 Veeam 与 IBM Cloud Object Storage (ICOS) 兼容。订购 Veeam on IBM Cloud 时，不会自动订购 IBM Cloud Object Storage，但可以在部署后添加 IBM Cloud Object Storage。

要订购 IBM Cloud Object Storage，请按指定的顺序完成以下任务。

## 创建 Object Storage 实例
{: #icos_ordering-obj}

要创建 Object Storage 实例，请参阅[创建新服务实例](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance)。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 创建存储区
{: #icos_ordering-bucket}

要创建存储区，请参阅[创建一些存储区来存储数据](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets)。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 创建服务凭证
{: #icos_ordering-service-cred}

要创建服务凭证（包括 HMAC 凭证），请参阅[服务凭证](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials)。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 添加横向扩展存储库
{: #icos_ordering-scale-repo}

* 作为 Veeam 服务安装和配置的一部分，将创建一个名为 `IC4V 横向扩展存储库`的横向扩展备份存储库。`IC4V 缺省 VM 备份存储库`将作为扩展数据块添加到横向扩展存储库。
* 创建备份作业时，必须选择 `IC4V 横向扩展存储库`作为备份存储库，而不是选择 `IC4V 缺省配置备份存储库`。后一个存储库用于 Veeam 配置备份。
* 您可以将更多存储库添加到此缺省存储库，例如，类型为 Object Storage 的备份存储库。有关更多信息，请参阅 [Adding Scale-Out Repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:external}。执行其中的步骤，然后返回到此部分以继续执行以下任务。

## 维护和管理云层
{: #icos_ordering-manage-cloud}

有关更多信息，请参阅 [Managing Capacity Tier Data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:external}。

## 相关链接
{: #icos_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [订购 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Veeam on {{site.data.keyword.cloud_notm}} 的受管服务](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

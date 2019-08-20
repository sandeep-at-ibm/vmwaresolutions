---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: IAM user, invite user, service access

subcollection: vmware-solutions


---

# 邀请用户访问服务和资源
{: #iamuserinvite}

{{site.data.keyword.vmwaresolutions_full}} 与 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 集成，用于在多个用户之间进行协作。注册 {{site.data.keyword.cloud_notm}} 帐户并登录到 {{site.data.keyword.vmwaresolutions_short}} 控制台后，可以将用户添加到 {{site.data.keyword.cloud_notm}} 帐户。这些添加的用户可以共享为帐户供应的服务和资源。

## 开始之前
{: #iamuserinvite-reqs}

* 确保您是帐户所有者，或者确保您的 **VMware Solutions** 服务的平台管理角色是**管理员**。
* 确保查看了[使用 Identity and Access Management 管理用户访问权](/docs/services/vmwaresolutions?topic=vmware-solutions-iam#iam)中的用户角色和许可权。

## 邀请用户访问服务和资源的过程
{: #iamuserinvite-procedure}

1. 单击条幅左侧的**管理 > 安全性 > 身份和访问权**。
2. 在**用户**页面上，单击**邀请用户**。
3. 在**邀请用户**页面上**用户**部分中的**电子邮件地址**字段中，输入要邀请的用户的电子邮件地址。
4. 在**访问权**部分中，展开**服务**，然后完成以下任务：
   1. 从**将访问权分配给**列表中，选择**资源**。
   2. 从**服务**列表中，选择 **VMware Solutions**。
   3. 选择要分配给用户的平台访问角色。可以是**管理员**、**编辑者**、**操作员**或**查看者**。
5. 单击**邀请用户**。

## 结果
{: #iamuserinvite-results}

添加的用户在接受邀请后，可以登录到 {{site.data.keyword.vmwaresolutions_short}} 控制台并切换到您的帐户。要执行此操作，用户可以单击 {{site.data.keyword.vmwaresolutions_short}} 控制台条幅中自己的用户帐户图标。然后，添加的用户可以进行协作，并共享指定帐户中可用的服务和资源。

## 相关链接
{: #iamuserinvite-related}

* [邀请用户和分配访问权](/docs/iam?topic=iam-iamuserinv)
* [管理身份和访问权](/docs/iam?topic=iam-getstarted)
* [邀请用户](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [什么是 IAM](/docs/iam?topic=iam-iamoverview)
* [将 V2.5 之前的 vCenter Server 实例迁移到 {{site.data.keyword.cloud_notm}} 帐户](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [将 V2.5 之前的 NetApp ONTAP Select 实例迁移到 {{site.data.keyword.cloud_notm}} 帐户](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

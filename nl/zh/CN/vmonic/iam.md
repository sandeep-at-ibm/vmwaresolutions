---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmware-solutions


---

# 使用 IAM 管理用户访问权
{: #iam}

帐户中用户对 {{site.data.keyword.vmwaresolutions_full}} 服务实例的访问权通过 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 进行控制。对于访问帐户中 {{site.data.keyword.vmwaresolutions_short}} 服务的每个用户，必须为其分配定义了 IAM 用户角色的访问策略。

访问策略确定用户可在所选服务或实例的上下文中执行的操作。允许的操作由 {{site.data.keyword.cloud_notm}} 服务作为允许在该服务上执行的操作进行定制和定义。然后，这些操作将映射到 IAM 用户角色。

策略允许在不同级别授予访问权。其中一些选项包括以下访问权：

* 对帐户中所有服务实例的访问权
* 对帐户中单个服务实例的访问权
* 对实例中特定资源的访问权
* 对帐户中所有支持 IAM 的服务的访问权

定义访问策略的作用域后，可以分配角色。

查看以下信息，其中概述了在 {{site.data.keyword.vmwaresolutions_short}} 服务中每个角色允许的操作。

## 平台管理角色和许可权
{: #iam-roles}

平台管理角色支持用户在平台级别对服务资源执行任务。例如，分配对服务的用户访问权，创建或删除服务标识，创建实例以及将实例绑定到应用程序。

下表提供了有关映射到平台管理角色的操作的信息。

表 1. 平台管理角色和允许的操作

|平台管理角色|操作|示例操作|
|:----------------- |:----------------- |:----------------- |
|查看者|只读操作| <ul><li>查看实例摘要</li><li>查看实例的详细信息</li></ul>|
|编辑者|更新特定实例|<ul><li>添加或除去 ESXi 服务器</li><li>添加或除去集群</li><li>添加或除去服务</li><li>将实例升级到更高版本</li></ul> |
|操作员|只读操作| <ul><li>列出实例</li><li>查看实例的详细信息</li></ul> |
|管理员|完全管理访问权|<ul><li>创建新实例</li><li>删除实例</li><li>向其他用户授予平台访问权</li></ul>|

对于 {{site.data.keyword.vmwaresolutions_short}}，存在以下操作：

表 2. 操作的描述和必需的角色

|操作|服务上的操作|角色|
|:------ |:-------------------- |:---- |
|vmware-solutions.instances.create|创建新实例|管理员|
|vmware-solutions.instances.delete|删除实例|管理员|
|vmware-solutions.instances.view| <ul><li>列出实例</li><li>查看实例的详细信息</li></ul> |查看者、操作员、编辑者和管理员|
|vmware-solutions.instances.update| <ul><li>添加或除去 ESXi 服务器</li><li>添加或除去集群</li><li>添加或除去服务</li><li>将实例升级到更高版本</li></ul> |编辑者和管理员|
|vmware-solutions.account.update|更新帐户设置|管理员|

## 管理用户的访问权
{: #iam-users}

可以将新用户添加到 {{site.data.keyword.cloud_notm}} 帐户，以便这些用户可以共享为帐户供应的服务和资源。有关更多信息，请参阅[邀请用户访问服务和资源](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)。

您还可以管理现有用户的访问权，包括修改现有访问权、分配新访问权以及复查分配的访问权。要管理用户的访问权，您必须是帐户所有者，或者必须具有**管理员**平台管理角色。有关更多信息，请参阅[管理对资源的访问权](/docs/iam?topic=iam-iammanidaccser)。

## 将现有实例迁移到 IBM Cloud 帐户
{: #iam-migrate}

由于 {{site.data.keyword.vmwaresolutions_short}} 与 IAM 集成，在 {{site.data.keyword.cloud_notm}} 帐户中 V2.5 和更高发行版中部署的实例会自动添加到帐户，并由 IAM 进行管理。

对于部署在 V2.4 和更低发行版中的现有实例，可以将其迁移到指定的 {{site.data.keyword.cloud_notm}} 帐户，以进行支持 IAM 的管理。有关更多信息，请参阅以下主题：
* [将 V2.5 之前的 vCenter Server 实例迁移到 IBM Cloud 帐户](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [将 V2.5 之前的 vCenter Server with Hybridity Bundle 实例迁移到 IBM Cloud 帐户](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [将 V2.5 之前的 NetApp ONTAP Select 实例迁移到 IBM Cloud 帐户](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## 相关链接
{: #iam-related}

* [管理身份和访问权](/docs/iam?topic=iam-getstarted)
* [邀请用户](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [什么是 IAM](/docs/iam?topic=iam-iamoverview)

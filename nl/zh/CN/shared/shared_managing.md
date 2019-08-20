---

copyright:

  years:  2019

lastupdated: "2019-08-06"

keywords: manage shared resources, shared resources, shared resource tasks

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Shared 资源
{: #shared_managing}

{{site.data.keyword.vmwaresolutions_full}} Shared 作为试验性产品提供。
{:note}

客户可使用 {{site.data.keyword.vmwaresolutions_short}} 产品来管理虚拟数据中心的生命周期。

无论使用 Web UI 还是公共 API，都支持以下功能：
- 查看虚拟数据中心实例
- 访问 vCloud 管理控制台
- 调整虚拟数据中心实例大小
- 删除虚拟数据中心实例
- 在虚拟数据中心实例中添加和除去 VMware 服务（**未来**）

## 查看虚拟数据中心实例
{: #shared_managing-viewing}

要查看针对用户帐户供应的所有虚拟数据中心实例的摘要，请完成以下步骤：

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在控制台条幅中，单击您的用户帐户图标，然后单击**帐户**字段以选择要检查其实例的用户帐户。  
3. 在 **IBM Cloud VMware Solutions Shared** 表中，查看所选用户帐户中供应的实例的列表。

|项|描述|  
|:------------- |:------------- |
|名称|实例的名称|
|类型|虚拟数据中心的类型|
|位置|托管实例的 {{site.data.keyword.CloudDataCent_notm}}|  
|创建时间|创建实例的日期和时间|
|状态|实例的状态|

{: caption="表 1. 虚拟数据中心实例项" caption-side="top"}

实例可以有一系列状态。

|状态|描述|
|:------------- |:------------- |
|正在创建|正在创建实例。|
|可供使用|实例准备就绪，可供使用。|
|正在修改|正在修改实例。|
|正在删除|正在删除实例。|
|已删除|实例已删除。|

{: caption="表 2. 虚拟数据中心实例的状态描述" caption-side="top"}

## 查看虚拟数据中心属性详细信息的过程
{: #vc_viewinginstances-procedure-view-vdc-details}

要查看实例的属性详细信息，请执行以下操作：

1. 在 **IBM Cloud VMware Solutions Shared** 表中，单击实例名称。
2. 在**属性**下，查看实例的详细信息。

|属性|描述|
|:------------- |:------------- |
|名称|实例的名称。|
|类型|虚拟数据中心类型。|
|位置|托管实例的 {{site.data.keyword.CloudDataCent_notm}}。|
|标识|实例的标识。|
|创建时间|创建实例的日期和时间，这也是计费开始时的日期和时间。|
|vCPU|虚拟数据中心可以随时使用的 CPU 限制或保留量。|
|RAM|虚拟数据中心可以随时使用的内存限制或保留量。|
|公共 IP|每个虚拟数据中心都随附 5 个公共 IP 地址，可用于将 vApp 和 VM 连接到因特网。|

{: caption="表 3. 虚拟数据中心属性" caption-side="top"}

## 访问 vCloud Director 管理控制台
{: #shared_managing-accessing}

通过 vCloud Director 管理控制台来管理虚拟数据中心。

对 vCloud Director 管理控制台的首次访问是使用**管理员**凭证完成的。使用虚拟数据中心详细信息页面中的**重置位置密码**链接生成密码。此操作会生成初始复杂随机密码，该密码可随时重置。

{{site.data.keyword.vmwaresolutions_short}} 产品不会存储**管理员**密码。生成密码后，必须将其捕获。如果密码丢失，那么应该生成新密码。

同一位置的所有虚拟数据中心都具有相同的**管理员**密码。重置虚拟数据中心实例上的密码会重置**管理员**密码，此密码供同一位置中的所有虚拟数据中心实例访问 vCloud Director 管理控制台。

生成第一个**管理员**密码后，详细信息页面右上角的 **vCloud Director 门户网站**按钮会变为可用。单击 **vCloud Director 门户网站**可访问 vCloud Director 管理控制台。要进行登录，请使用用户名 **admin** 以及通过**重置位置密码**链接获取的密码。

## 调整虚拟数据中心实例大小
{: #shared_managing-resizing}

虚拟数据中心实例处于**可供使用**状态时，可以随时更改分配给虚拟数据中心的资源量。 

在虚拟数据中心详细信息页面中，调整虚拟数据中心实例的 vCPU 或 RAM 资源的大小。单击详细信息页面上**资源**旁边的“画笔”图标，然后更改 vCPU 或 RAM 属性的值。

最后，在下订单之前验证配置和估算成本。

  如果在正在使用 vCPU 和 RAM 资源时下调其大小，那么配置更改会失败，因为无法将虚拟数据中心资源量下调到低于当前活动资源使用量的水平。
  {:note}

进行更改时，虚拟数据中心实例会进入**正在修改**状态。资源准备就绪可供使用后，其状态会更改为**可供使用**。

## 删除虚拟数据中心实例
{: #shared_managing-deleting}

虚拟数据中心实例处于**可供使用**状态时，可以将其删除。在虚拟数据中心详细信息页面或“IBM Cloud VMware Solutions Shared 资源”表中执行删除操作。

在详细信息页面中，单击详细信息页面右上角的溢出菜单选项中的**删除**图标。然后，确认要删除该实例。

在“IBM Cloud VMware Solutions Shared 资源”表中，找到要删除的实例，然后单击**操作**列中的**删除**图标。然后，确认要删除该实例。

## 相关链接
{: #shared_managing-related}

* [{{site.data.keyword.cloud_notm}} for VMware Solutions Shared 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_overview)
* [订购 Shared - 随需应变](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_ondemand)
* [订购 Shared - 保留](/docs/services/vmwaresolutions/services?topic=vmware-solutions-shared_ordering_reserved)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){:external}

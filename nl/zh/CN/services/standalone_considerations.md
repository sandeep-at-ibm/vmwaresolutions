---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-23"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 内部部署 VMware HCX on IBM Cloud 实例的注意事项
{: #standalone_considerations}

安装或删除针对内部部署使用而订购的 HCX on {{site.data.keyword.cloud}} 实例之前，请查看以下注意事项。

具有 HCX on {{site.data.keyword.cloud_notm}} 的 vCenter Server 实例限制为可同时从内部部署站点建立三个连接。
{:note}

## 安装内部部署 HCX on IBM Cloud 实例之前的注意事项
{: #standalone_considerations-install}

HCX on {{site.data.keyword.cloud_notm}} 组件必须同时安装在 {{site.data.keyword.cloud_notm}} 和内部部署 vSphere 环境中。在安装内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例之前，建议您将 HCX on {{site.data.keyword.cloud_notm}} 服务安装到 {{site.data.keyword.cloud_notm}} 上的 vCenter Server with Hybridity Bundle 实例中。有关更多信息，请参阅[安装 HCX on {{site.data.keyword.cloud_notm}} 时的注意事项](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-hcx_considerations#hcx_considerations-install)。

### IP 地址需求
{: #standalone_considerations-ip}

要获取完整的 HCX 功能，至少需要五个具有因特网访问权的专用 IP 地址。

### 内部部署 HCX on IBM Cloud 实例的部署过程
{: #standalone_considerations-deploy}

必须完成以下任务才能成功安装内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例：
1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例。有关更多信息，请参阅[订购内部部署 HCX 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances)。
2. 在 **HCX 云控制台**中，完成以下步骤：
    1. 单击**管理**选项卡。
    2. 在**系统更新**选项卡上，单击**请求下载链接**。
    3. 单击**复制链接**，然后使用此链接将 HCX Enterprise Client 下载到有权访问内部部署 vSphere 环境的内部部署环境中。
3. 在 VMware vSphere Web Client 中，将 HCX Enterprise Client 作为 HCX Manager 虚拟设备 (HCX Manager) 部署到内部部署环境中。

   必须在专用网络上部署此内部部署 HCX Manager，并允许它访问公用网络。可以使用 NSX Edge、Vyatta 或类似网关，以允许通过因特网访问内部部署 HCX Manager。如果用于专用网络访问和公用网络访问的网关不同，那么建议您使用缺省网关来允许公用网络访问，并通过内部部署的 **HCX Manager 管理控制台**创建静态路由以用于专用网络访问。
   {:note}
4. 在 HCX Manager 部署完成后，使用 **HCX Manager 管理控制台**来激活内部部署 HCX Manager。要获取内部部署 HCX Manager 的激活密钥，请在 {{site.data.keyword.vmwaresolutions_short}} 控制台中订购内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例。有关更多信息，请参阅[订购内部部署 HCX 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_orderingserviceinstances)。
5. 如果订购 HCX on {{site.data.keyword.cloud_notm}} 服务时使用的是自签名 SSL 证书，那么必须通过完成以下步骤将证书导入到内部部署 HCX Manager：
    1. 在内部部署 **HCX Manager 管理控制台**中，单击**管理**选项卡。
    2. 在左侧导航窗格中，单击**可信 CA 证书**，然后单击右侧的**导入**。
    3. 单击 **URL**，然后输入要应用的证书的 URL，即 **HCX 云 IP** (``https://<cloud-side public IP>``)，您可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中的 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到该 URL。
    4. 单击**应用**。

现在，您已完成内部部署 HCX Manager 的基本设置。可以继续将内部部署 HCX on {{site.data.keyword.cloud_notm}} 站点与云端 HCX 站点进行配对。

有关更多信息，请参阅 [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)。

## 删除内部部署 HCX on IBM Cloud 实例之前的注意事项
{: #standalone_considerations-delete}

删除针对内部部署使用而订购的 HCX on {{site.data.keyword.cloud_notm}} 实例之前，请查看以下注意事项：
1. 在 VMware vSphere Web Client 中，转至 HCX 用户界面，然后检查以下各项：
    1. 确保没有任何 HCX 迁移或灾难恢复操作正在运行。
    2. 确保除去了所有扩展网络。
    3. 确保除去了所有具有成对云站点的互连组件。

   在继续下一步之前，必须完成所有先前步骤。否则，将取消内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例的许可证。如果取消了许可证，那么无法执行迁移，并且 HCX 组件可能会发生错误。  
   {:important}
2. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，删除订购用于获取内部部署 HCX Manager 的激活密钥的内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例。确保删除的实例在控制台中不再可用，然后再继续执行下一步。

   有关更多信息，请参阅[删除内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_deletingserviceinstances)。
3. 在 VMware vSphere Web Client 中，删除内部部署 HCX Manager。

## 相关链接
{: #standalone_considerations-related}

* [查看内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_viewingserviceinstances)
* [HCX 术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [VMware Hybrid Cloud Extension 文档](https://cloud.vmware.com/vmware-hcx/resources)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

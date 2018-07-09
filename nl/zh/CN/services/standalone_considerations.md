---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# 内部部署 VMware HCX on IBM Cloud 实例的注意事项

安装或删除针对内部部署使用而订购的 HCX on {{site.data.keyword.cloud}} 实例之前，请查看以下注意事项。

**注**：具有 HCX on {{site.data.keyword.cloud_notm}} 的 vCenter Server 实例限制为可同时从内部部署站点建立三个连接。

## 安装内部部署 HCX on IBM Cloud 实例时的注意事项

HCX on {{site.data.keyword.cloud_notm}} 组件必须同时安装在 {{site.data.keyword.cloud_notm}} 和内部部署 vSphere 环境中。在安装内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例之前，建议您将 HCX on {{site.data.keyword.cloud_notm}} 服务安装到 {{site.data.keyword.cloud_notm}} 上的 vCenter Server with Hybridity Bundle 实例中。有关更多信息，请参阅 [HCX on {{site.data.keyword.cloud_notm}} 的注意事项](../services/hcx_considerations.html)。

### 有关 IP 地址的需求

要获取完整的 HCX 功能，至少需要五个专用 IP 地址，并且必须允许这些地址访问因特网。

### 内部部署 HCX on IBM Cloud 实例的部署过程

必须完成以下任务才能成功安装内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例：
1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，完成以下步骤：
    1. 在左侧导航窗格中，单击**部署的实例**。
    2. 单击安装了 HCX on {{site.data.keyword.cloud_notm}} 服务的 vCenter Server with Hybridity Bundle 实例。这是要从内部部署 vSphere 环境连接到的云端。
    3. 在**服务**选项卡上，单击**安装的服务**。
    4. 单击 **HCX on {{site.data.keyword.cloud_notm}}** 卡。
    5. 单击**查看 HCX 云控制台**，然后使用 vCenter Server 凭证登录到控制台以查看云端 HCX on {{site.data.keyword.cloud_notm}} 服务的详细信息。
2. 在 **HCX 云控制台**中，完成以下步骤：
    1. 单击**管理**选项卡。
    2. 在**系统更新**选项卡上，单击**请求下载链接**。
    3. 单击**复制链接**，然后使用此链接将 HCX Enterprise Client 下载到有权访问内部部署 vSphere 环境的内部部署环境中。
3. 在 VMware vSphere Web Client 中，将 HCX Enterprise Client 作为 HCX Manager 虚拟设备 (HCX Manager) 部署到内部部署环境中。

   **注**：必须在专用网络上内部部署 HCX Manager，并允许它访问公用网络。可以使用 NSX Edge、Vyatta 或类似网关，以允许通过因特网访问内部部署 HCX Manager。如果用于专用网络访问和公用网络访问的网关不同，那么建议您使用缺省网关来允许公用网络访问，并通过内部部署的 **HCX Manager 管理控制台**创建静态路由以用于专用网络访问。
4. 在 HCX Manager 部署完成后，使用 **HCX Manager 管理控制台**来激活内部部署 HCX Manager。要获取内部部署 HCX Manager 的激活密钥，请在 {{site.data.keyword.vmwaresolutions_short}} 控制台中订购内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例。有关更多信息，请参阅[订购内部部署 HCX 实例](../services/standalone_orderingserviceinstances.html)。
5. 如果订购 HCX on {{site.data.keyword.cloud_notm}} 服务时使用的是自签名 SSL 证书，那么必须通过完成以下步骤将证书导入到内部部署 HCX Manager：
    1. 在内部部署 **HCX Manager 管理控制台**中，单击**管理**选项卡。
    2. 在左侧导航窗格中，单击**可信 CA 证书**，然后单击右侧的**导入**。
    3. 单击 **URL**，然后输入要应用的证书的 URL，即 **HCX 云 IP** (``https://<cloud-side public IP>``)，可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台的 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到该 IP 地址。
    4. 单击**应用**。

现在，您已完成内部部署 HCX Manager 的基本设置。可以继续将内部部署 HCX on {{site.data.keyword.cloud_notm}} 站点与云端 HCX 站点进行配对。

有关更多信息，请参阅 [VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)。

## 删除内部部署 HCX on IBM Cloud 实例时的注意事项

删除针对内部部署使用而订购的 HCX on {{site.data.keyword.cloud_notm}} 实例之前，请查看以下注意事项：
1. 在 VMware vSphere Web Client 中，转至 HCX 用户界面，然后检查以下各项：
    1. 确保没有任何 HCX 迁移或灾难恢复操作正在运行。
    2. 确保除去了所有扩展网络。
    3. 确保除去了所有具有成对云站点的互连组件。

   **重要信息**：在继续下一步之前，必须完成所有注意事项。否则，将取消内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例的许可证，这样一来，将无法执行迁移，并且 HCX 组件上可能会发生错误。  
2. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，删除订购用于获取内部部署 HCX Manager 的激活密钥的内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例。确保删除的实例在控制台中不再可用，然后再继续执行下一步。

   有关更多信息，请参阅[删除内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例](../services/standalone_deletingserviceinstances.html)。
3. 在 VMware vSphere Web Client 中，删除内部部署 HCX Manager。

## 相关链接

* [查看内部部署 HCX on {{site.data.keyword.cloud_notm}} 实例](../services/standalone_viewingserviceinstances.html)
* [HCX 术语的词汇表](hcx_glossary.html)
* [VMware Hybrid Cloud Extension 文档](https://hcx.vmware.com/#vm-documentation)
* [VMware HCX Enterprise 安装与用户指南](https://hcx.vmware.com/content/docs/vmware-hcx-enterprise-install-guide.pdf){:new_window}
* [联系 IBM 支持](../vmonic/trbl_support.html)

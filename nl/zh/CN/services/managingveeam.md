---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# 管理 Veeam on IBM Cloud

此服务部署到实例后，可以使用 RDP 来访问 Veeam 控制台，以管理环境中所有虚拟机的备份和复原，包括管理组件的备份和复原。您还可以通过从 Veeam Web 站点下载并安装 Veeam 更新来升级此服务。

对于在低于 V1.8 的发行版中部署的实例，如果要使用 Veeam on {{site.data.keyword.cloud}} 服务，必须替换这些实例中的现有 Veeam VSI。有关更多信息，请参阅_使用 Veeam on IBM Cloud 替换 V1.8 之前版本的实例的 Veeam VSI_ 部分。

## 使用 RDP 访问 Veeam 控制台

要管理 Veeam on {{site.data.keyword.cloud_notm}} 服务，请通过完成以下步骤来访问 Veeam 控制台：
1. 使用远程桌面协议 (RDP) 连接到 Windows IP 地址。
2. 使用管理员凭证，登录到 Windows 控制台。
3. 使用管理员凭证，从 Windows 控制台访问 Veeam 控制台。

您可以在 Veeam on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到 Windows IP 地址和管理员凭证。

有关更多信息，请参阅以下主题：
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)

## 备份和复原安装了 Veeam on IBM Cloud 的实例的管理组件

Veeam on {{site.data.keyword.cloud_notm}} 服务可以配置为使用 Veeam 控制台来备份管理组件。有关更多信息，请参阅[备份组件](../archiref/solution/solution_backingup.html)。

对于部署在（或升级到）V1.8 或更高发行版的实例，不会自动备份对环境的配置更改。因此，在更改环境配置之前，建议通过在 Veeam 控制台中运行管理备份作业，手动备份管理组件。有关手动备份的更多信息，请参阅 [Veeam 技术指示信息](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}。

管理组件发生故障时，可以使用 Veeam 控制台将管理组件复原到先前的备份。有关手动复原的更多信息，请参阅 [Veeam 技术指示信息]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}。

## 对 Veeam on IBM Cloud 应用更新

您应负责维护 Veeam 软件，以使其保持为最新版本。

### 对于使用公用和专用网络部署的实例

如果 Veeam 服务安装在使用公用和专用网络的实例上，那么可以使用 Veeam 软件本身来检查并下载更新。

### 对于仅使用专用网络部署的实例

如果 Veeam 服务安装在仅使用专用网络的实例上，那么由于 Veeam 虚拟机 (VM) 配置为不具有公用网络访问权，因此无法使用 Veeam 软件本身来检查或下载更新。您必须改为从 Veeam Web 站点下载更新，将其传输到 Veeam VM，然后安装这些更新。

## 更新 Veeam 许可证

### 对于使用公用和专用网络部署的实例

如果 Veeam 服务安装在使用公用和专用网络的实例上，那么可以通过遵循[更新许可证]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html)中的 Veeam 指示信息来自动或手动更新 Veeam 许可证。

### 对于仅使用专用网络部署的实例

如果 Veeam 服务安装在仅使用专用网络的实例上，那么需要续订时，您必须记下许可证的到期日期，并与 [IBM 支持人员](../vmonic/trbl_support.html)联系，以获取有关更新许可证密钥的帮助。

## 使用 Veeam on IBM Cloud 替换 V1.8 之前版本的实例的 Veeam VSI

Veeam on {{site.data.keyword.cloud_notm}} 服务可以同时备份管理组件和工作负载，它将取代仅备份管理组件且集成在 V1.8 之前发行版的 VMware Cloud Foundation 和 VMware vCenter Server 中的先前 Veeam VSI。

由于此更改，除去了实例详细信息页面上的先前**备份和复原**选项卡，并且实例的备份点在 {{site.data.keyword.vmwaresolutions_short}} 控制台中不再可用，尽管 V1.8 之前版本的实例中的 Veeam VSI 仍保持运行。

您必须创建 {{site.data.keyword.cloud_notm}} 支持凭单来获取有关复原的帮助。此外，V1.8 之前版本的实例中的 Veeam VSI 许可证已于 2017 年 10 月 14 日到期。因此，必须将先前的 Veeam VSI 替换为新的 Veeam on {{site.data.keyword.cloud_notm}} 服务。

完成以下步骤：
1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**已部署的实例**，然后单击目标实例。
2. 在实例详细信息页面上，单击**更新和补丁**选项卡。确保已将实例升级到 V1.8 发行版。
3. 单击**服务**选项卡。
4. 在**添加服务**选项卡上，安装 Veeam on {{site.data.keyword.cloud_notm}} 服务。

部署了新的 Veeam on {{site.data.keyword.cloud_notm}} 服务并且成功完成管理组件备份后，可以通过创建 {{site.data.keyword.cloud_notm}} 支持凭单，从帐户除去现有 Veeam VSI。IBM 支持人员将确定并删除现有 Veeam VSI 和存储器。

### 相关链接

* [Veeam on {{site.data.keyword.cloud_notm}} 概述](veeam_considerations.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Veeam.com Web 站点](https://www.veeam.com/)
* [Veeam 技术文档](https://www.veeam.com/documentation-guides-datasheets.html)

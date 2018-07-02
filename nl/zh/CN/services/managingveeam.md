---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# 管理 Veeam on IBM Cloud

对于在低于 V1.8 的发行版中部署的实例，如果要使用 Veeam on {{site.data.keyword.cloud}} 服务，必须替换这些实例中的现有 Veeam VSI。此服务部署到实例后，可以使用 RDP 来访问 Veeam 控制台，以管理环境中所有虚拟机的备份和复原，包括管理组件的备份和复原。您还可以通过从 Veeam Web 站点下载并安装 Veeam 更新来升级此服务。

## 使用 Veeam on IBM Cloud 替换 V1.8 之前版本的实例的 Veeam VSI

Veeam on {{site.data.keyword.cloud_notm}} 服务可以备份管理组件和工作负载，将取代集成到低于 V1.8 的发行版中 VMware Cloud Foundation 和 VMware vCenter Server 以用于仅备份管理组件的先前 Veeam VSI。由于此更改，除去了实例详细信息页面上的先前**备份和复原**选项卡，并且实例的备份点在 {{site.data.keyword.vmwaresolutions_short}} 控制台中不再可用，尽管 V1.8 之前版本的实例中的 Veeam VSI 仍保持运行。您必须创建 {{site.data.keyword.cloud_notm}} 支持凭单来获取有关复原的帮助。此外，V1.8 之前版本的实例中的 Veeam VSI 许可证已于 2017 年 10 月 14 日到期。因此，必须将先前的 Veeam VSI 替换为新的 Veeam on {{site.data.keyword.cloud_notm}} 服务。

完成以下步骤：
1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**部署的实例**，然后单击目标实例。
2. 在实例详细信息页面上，单击**更新和补丁**选项卡。确保已将实例升级到 V1.8 发行版。
3. 单击**服务**选项卡。
4. 在**添加服务**选项卡上，安装 Veeam on {{site.data.keyword.cloud_notm}} 服务。

部署了新的 Veeam on {{site.data.keyword.cloud_notm}} 服务并且成功完成管理组件备份后，可以通过创建 {{site.data.keyword.cloud_notm}} 支持凭单，从帐户除去现有 Veeam VSI。然后，IBM 支持人员将确定并删除现有 Veeam VSI 和存储器。

## 使用 RDP 访问 Veeam 控制台

要管理 Veeam on {{site.data.keyword.cloud_notm}} 服务，必须通过完成以下步骤来访问 Veeam 控制台：
1. 使用远程桌面协议 (RDP) 连接到 Windows IP 地址，此地址可以在 Veeam on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到。
2. 使用可在 Veeam on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的管理员凭证，登录到 Windows 控制台。
3. 使用可在 Veeam on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的管理员凭证，通过 Windows 控制台访问 Veeam 控制台。

有关更多信息，请参阅以下主题：
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)

## 备份和复原安装了 Veeam on IBM Cloud 的实例的管理组件

Veeam on {{site.data.keyword.cloud_notm}} 服务已预配置一个管理备份作业，该作业会自动运行以每天备份管理组件，最多可有 14 个复原点。

您还可以使用 Veeam 控制台来手动备份管理组件。从 V1.8 发行版开始，不会自动备份对环境的配置更改。因此，建议您在更改环境配置之前，通过在 Veeam 控制台中运行预配置的管理备份作业，执行管理组件的手动备份。有关如何执行手动备份作业的更多信息，请参阅 [Veeam 技术指示信息](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}。

管理组件发生故障时，可以使用 Veeam 控制台将管理组件复原到先前的备份。有关如何执行手动复原作业的更多信息，请参阅 [Veeam 技术指示信息]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}。

## 升级 Veeam on IBM Cloud

要升级 Veeam on {{site.data.keyword.cloud_notm}} 服务，请从 Veeam Web 站点下载 Veeam 更新，将更新复制到 Veeam VSI，然后安装这些更新。

## 相关链接

* [Veeam on {{site.data.keyword.cloud_notm}} 概述](veeam_considerations.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Veeam.com Web 站点](https://www.veeam.com/)
* [Veeam 技术文档](https://www.veeam.com/documentation-guides-datasheets.html)

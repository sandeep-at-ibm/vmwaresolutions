---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud 概述

Veeam on {{site.data.keyword.cloud}} 服务可与 VMware 系统管理程序无缝集成，以帮助企业实现高可用性。此服务可为应用程序和数据提供恢复点和时间目标。在完成配置后的 15 分钟内就会提供恢复点和时间目标。通过使用此服务，您可以在 Veeam 控制台中直接控制基础架构的所有虚拟机的备份和复原。

**可用性**：此服务仅可用于在 V1.8 或更高发行版中部署的实例。

## Veeam on IBM Cloud 的组件

Veeam on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：
* 一个 Windows Server 2016 VSI，使用主专用 IP 地址和 1 GbE 接口
* {{site.data.keyword.cloud_notm}} 耐久性块存储器，其大小和性能在订购此服务时选择

## 安装 Veeam on IBM Cloud 时的注意事项

* 此服务会备份以下管理组件：
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **仅限 Cloud Foundation 实例**：VMware SDDC Manager
  - **仅限具有 HA AD/DNS 的 vCenter Server 实例**：AD/DNS 服务器的高可用性对

* Veeam on {{site.data.keyword.cloud_notm}} 服务不会备份 ESXi 服务器的配置。

* 缺省情况下，NSX Controller 和 NSX Edge 的配置将使用 NSX Manager 每天备份，最多可有 14 个复原点。要完全复原 NSX 配置，必须创建 {{site.data.keyword.cloud_notm}} 支持凭单，因为 NSX 配置的备份是保存在 {{site.data.keyword.vmwaresolutions_full}} 内部的存储器上的。有关使用 NSX Manager 来管理 NSX 配置备份的更多信息，请参阅 [VMware 技术指示信息](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html)。
* 用于存储的存储库和 Veeam 服务器位于原始 pod 和数据中心内。因此，远程集群的备份操作性能可能会下降。

## 除去 Veeam on IBM Cloud 时的注意事项

在除去 Veeam on {{site.data.keyword.cloud_notm}} 服务之前，请注意，除去此服务将停止所有备份（包括管理 VM 的备份），并且将删除所有先前的备份（此删除操作不可撤销）。如果管理 VM 后续损坏，将无法对其进行复原。

## 相关链接

* [订购 Veeam on {{site.data.keyword.cloud_notm}}](veeam_ordering.html)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](managingveeam.html)
* [请求 Veeam on {{site.data.keyword.cloud_notm}} 的受管服务](managing_veeam_services.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Veeam Web 站点](https://www.veeam.com/){:new_window}
* [Veeam 帮助中心](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

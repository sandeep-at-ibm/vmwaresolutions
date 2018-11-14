---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

#	收集元数据

VUM 通过预定义的自动过程来下载有关升级、补丁或扩展的元数据，您可以对自动过程进行修改。根据可配置的定期时间间隔，VUM 会与 VMware 或第三方来源联系，以收集有关可用升级、补丁或扩展的最新元数据。但是，将 VMware 中的缺省设置用于 VCS 实例是可接受的，因此您可以根据需要针对您的企业需求更改这些设置。

VUM 显示由 vSAN 生成的系统管理的基线。系统管理的基线会自动定期更新其内容，这需要 VUM 有权持续访问因特网。vSAN 系统基线通常每 24 小时刷新一次。

您可以使用系统管理的基线将 vSAN 集群升级到建议的针对 vSAN 的关键补丁、驱动程序、更新或最新支持的 ESXi 主机版本。

对于大多数企业，VUM 的 VMware 缺省设置被视为适合使用。如果您的企业希望使用不同的设置，那么下面提供了有关如何更改这些设置的信息。

##	下载安排
更新是指虚拟设备升级、主机补丁和扩展，缺省情况下，VUM 会每天下载一次更新。这可以通过访问 vSphere Web Client，浏览至**主页** > **Update Manager** > **管理** > **设置**，选择**下载安排**，然后单击**编辑**进行更改。

##	通知检查安排
通知是指有关补丁召回、新修订和警报的信息，缺省情况下，VUM 会每小时下载一次通知。这可以通过访问 vSphere Web Client，浏览至**主页** > **Update Manager** > **管理** > **设置**，选择**通知检查安排**，然后单击**编辑**进行更改。

##	VM 设置
要更改 VM 设置，请访问 vSphere Web Client，浏览至**主页** > **Update Manager** > **管理** > **设置**和 **VM 设置**，然后单击**编辑**。

##	主机/集群设置
要更改主机/集群设置，请访问 vSphere Web Client，浏览至**主页** > **Update Manager** > **管理** > **设置**和**主机/集群设置**，然后单击**编辑**。

### 相关链接

* [VMware HCX on IBM Cloud 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）

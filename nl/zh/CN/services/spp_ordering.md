---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 订购 IBM Spectrum Protect Plus on IBM Cloud

订购 {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

## 为新实例订购 IBM Spectrum Protect Plus on IBM Cloud

可以使用下列其中一种方法订购包含 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **IBM Spectrum Protect Plus on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **IBM Spectrum Protect Plus on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 IBM Spectrum Protect Plus on IBM Cloud

可以使用下列其中一种方法将 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **IBM Spectrum Protect Plus on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

## IBM Spectrum Protect Plus on IBM Cloud 服务配置

订购此服务时，请提供以下设置。

### 存储卷数

满足存储需求的卷数。

### 每个卷的存储大小

每个卷的存储容量。

### 存储性能

基于工作负载需求的 IOPS（每秒输入/输出操作数）/GB。
* 如果要订购 IBM Spectrum Protect Plus 的许可证，请在**订购许可证**选项卡上指定**要许可的 VM 数**。
* 如果要自带许可证 (BYOL)，请单击 **IBM Spectrum Protect Plus 许可证**选项卡，然后单击**添加许可证文件**以上传您拥有的 IBM Spectrum Protect Plus 许可证文件。

## IBM Spectrum Protect Plus on IBM Cloud 的部署过程

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的部署会自动执行。无论是订购实例时包含此服务，还是稍后再将此服务部署到实例中，都会通过 {{site.data.keyword.vmwaresolutions_short}} 自动过程来完成以下步骤：

1. 根据指定的设置，针对 IBM Spectrum Protect Plus 备份存储库从 {{site.data.keyword.cloud_notm}} 基础架构订购耐久性 NFS 存储器。
2. 根据指定的设置，从 {{site.data.keyword.cloud_notm}} 基础架构订购若干 IBM Spectrum Protect Plus 许可证。订购的许可证以 10 个虚拟机 (VM) 许可证包为单位递增，并基于在订购 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务时指定要许可的 VM 数。如果想要自带现有 IBM Spectrum Protect Plus 许可证，那么不会向 {{site.data.keyword.cloud_notm}} 基础架构订购任何许可证。
3. 将为此服务订购的 NFS 存储器安装到实例的缺省集群中的所有 ESXi 服务器，包括将每个 ESXi 服务器上的正确静态路由添加到存储器专用子网。
4. 在 vCenter Server 中为安装到 ESXi 服务器的所有 NFS 存储卷创建 NFS 数据存储。
5. 在实例的缺省集群中部署、激活和配置 IBM Spectrum Protect Plus VM。
6. 将为此服务订购的 NFS 存储器连接到 IBM Spectrum Protect Plus VM，并配置备份存储库。
7. 向实例的 DNS 服务器注册 IBM Spectrum Protect Plus VM 的主机名和 IP 地址。

### 相关链接

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 概述](spp_considerations.html)
* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 预防性服务规划](http://www.ibm.com/support/docview.wss?uid=swg22012650)
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](managingspp.html)
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](../vcenter/vc_hybrid_addingremovingservices.html)
* [IBM Spectrum Protect Plus 文档](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)

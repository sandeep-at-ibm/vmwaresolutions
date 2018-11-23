---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# 请求 IBM Cloud Private Hosted

{{site.data.keyword.cloud}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} 会自动在 VMware vCenter Server 实例上部署 {{site.data.keyword.cloud_notm}} Private Hosted。

{{site.data.keyword.cloud_notm}} Private Hosted 会将微服务和容器的强大功能引入到 {{site.data.keyword.cloud_notm}} 上的 VMware 环境中。使用此服务，可以将内部部署中您熟悉的 VMware 和 {{site.data.keyword.cloud_notm}} Private 操作模型和工具扩展到 {{site.data.keyword.cloud_notm}} 中。

## IBM Cloud Private Hosted 的技术规范

以下是请求 {{site.data.keyword.cloud_notm}} Private Hosted 服务的最低需求：

* VMware vCenter Server on {{site.data.keyword.cloud_notm}}。**注**：不支持 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle。
* VMware NSX Advanced Edition 或 Enterprise Edition
* 三个 {{site.data.keyword.baremetal_long}}
* 双 Intel Xeon Gold 5120 处理器 / 共 28 个核心，2.2 GHz
* 每个服务器 384 GB RAM
* 一个共享 NFS 存储器文件共享（8,000 GB，4 IOPS/GB）
* 33 个 IBM Cloud Private 虚拟处理器核心许可证
* 对于数据备份，建议使用 Veeam on IBM Cloud 服务。

## 请求 IBM Cloud Private Hosted 的过程

1. 按照[订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)中的步骤订购新的 vCenter Server 实例。您还可以为现有实例请求 IBM Cloud Private Hosted。**重要信息**：请确保您的环境满足前面列出的最低需求。
2. 确保您具有 IBM Cloud Private 授权。
3. 在收到 vCenter Server 实例已准备就绪的确认信息后，继续以下步骤来请求 IBM Cloud Private Hosted。
4. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**开始**。
5. 向下滚动页面，然后在**订购其他服务**下，单击 **IBM Cloud Private Hosted** 卡。
6. 在 **IBM Cloud Private Hosted on vCenter Server on IBM Cloud** 页面上的**联系 IBM Cloud Private Hosted DevOps 团队**框中，输入您的需求描述，然后单击**请求咨询**。

{{site.data.keyword.cloud_notm}} Private Hosted DevOps 代表会通过您的 {{site.data.keyword.cloud_notm}} 联系信息与您联系，以帮助您快速入门。

### 相关链接

* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)（PDF 下载）
* [开具有关 IBM Cloud Private 的凭单](https://www.ibm.com/mysupport/s/?language=en_US)

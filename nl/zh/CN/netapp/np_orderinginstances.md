---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# 订购 NetApp ONTAP Select 实例

要部署具有专用、高度可用的软件定义存储设备的 VMware 虚拟化平台，请订购 NetApp ONTAP Select 实例。

## 需求

确保已完成以下任务：
*  已在**设置**页面上配置 {{site.data.keyword.cloud}} 基础架构凭证。有关更多信息，请参阅[管理用户帐户和设置](../vmonic/useraccount.html)。
*  已查看[针对 NetApp ONTAP Select 实例的需求和规划](np_planning.html)中的需求和注意事项。

**重要信息：不要修改在订购和实例部署期间设置的任何值。这样做可能会使您的实例不可用。**

## 系统设置

订购 NetApp ONTAP Select 实例时，必须指定其基本设置。

### 实例名称

实例名称必须满足以下需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 实例名称必须以字母数字字符开头和结尾。
* 实例名称的最大长度为 10 个字符。
* 实例名称在您的帐户中必须唯一。

## 网络接口设置

订购 NetApp ONTAP Select 实例时，必须指定以下网络接口设置。

### 主机名前缀

主机名前缀必须满足以下需求：
*  只允许使用字母数字字符和短划线 (-) 字符。
*  主机名前缀必须以字母数字字符开头和结尾。
*  主机名前缀的最大长度为 10 个字符。

### 子域标签

子域标签必须满足以下需求：
*  只允许使用字母数字字符和短划线 (-) 字符。
*  子域标签必须以字母数字字符开头和结尾。
*  子域标签的最大长度为 10 个字符。
*  子域标签在您的帐户中必须唯一。

### 域名

根域名必须满足以下需求：
* 域名必须包含两个或更多用句点 (.) 分隔的字符串。
* 第一个字符串必须以字母字符开头并以字母数字字符结尾。
* 除了最后一个字符串外，其他所有字符串都只能包含字母数字和短划线 (-) 字符。
* 最后一个字符串只能包含字母字符。
* 最后一个字符串的长度必须在 2 到 24 个字符范围内。

**注**：主机和 VM（虚拟机）的 FQDN（标准域名）的最大长度为 50 个字符。域名必须符合此最大长度。

## 许可证设置

必须上传四个 NetApp 许可文件，因为四个 {{site.data.keyword.baremetal_short}} 各自需要一个许可证。请联系 NetApp 销售团队，以购买针对高性能或高容量部署的相应许可。

## 裸机服务器设置

### 数据中心位置

必须选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。

### 裸机服务器配置

可以根据需求选择裸机服务器配置：
* **高性能（中型）**- 高级许可证 / 双 Intel Xeon E5-2650 V4（共 24 个核心，2.2 GHz）/ 128 GB RAM / 每节点 22 个 1.9 TB SSD 驱动器容量 / 4 节点集群的有效容量 - 59 TB
* **高性能（大型）**- 高级许可证 / 双 Intel Xeon E5-2650 V4（共 24 个核心，2.2 GHz）/ 128 GB RAM / 每节点 22 个 3.8 TB SSD 驱动器容量 / 4 节点集群的有效容量 - 118 TB
* **高容量** - 标准许可证 / 双 Intel Xeon E5-2650 V4（共 24 个核心，2.2 GHz）/ 64 GB RAM / 每节点 34 个 4 TB SATA 驱动器容量 / 4 节点集群的有效容量 - 190 TB

**注**：3.8 TB SSD（固态磁盘）驱动器在 {{site.data.keyword.CloudDataCent_notm}} 内一般可用后就会受到支持。

### 裸机服务器的数量

缺省情况下，NetApp ONTAP Select 实例的 ESXi 服务器数为 4 个。您不能对其进行更改。所有 ESXi 服务器都共享配置。

## 过程

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格中的 **VMware**，然后单击**虚拟数据中心**部分中的 **NetApp ONTAP Select**。
2. 在 **NetApp ONTAP Select** 页面上，单击**创建**。
3. 在 **NetApp ONTAP** 页面上，输入实例名称。
4. 通过输入**主机名前缀**、**子域标签**和**域名**，完成网络接口设置。
5. 通过单击**添加许可证文件**以上传四个 {{site.data.keyword.baremetal_short}} 所需的四个 NetApp 许可证文件，完成许可设置。
6. 完成裸机服务器设置：
   1. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。
   2. 选择裸机服务器配置。
7. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
    1. 复查实例的设置。
    2. 复查实例的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
    3. 确保要向其收费的帐户正确，然后选中**我了解将向下面列出的帐户收费**复选框。
    4. 单击订单适用条款的链接。确保您同意这些条款，然后选中**我已阅读并同意下面列出的第三方服务协议**复选框。
    5. 单击**供应**。

## 结果

实例部署会自动启动。您将收到说明订单正在处理的确认，并且您可以通过查看实例详细信息来检查部署的状态。

成功部署实例后，[NetApp ONTAP Select 实例的技术规范](../netapp/np_netappoverview.html#technical-specifications-for-netapp-ontap-select-instances)中描述的组件已安装在 VMware 虚拟平台上。

实例准备就绪可供使用后，该实例的状态会更改为**可供使用**，并且您将收到通过电子邮件发送的通知。

## 后续步骤

查看和管理订购的 NetApp ONTAP Select 实例。

**重要信息**：您只能通过 {{site.data.keyword.vmwaresolutions_short}} 控制台管理 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 组件，而不能通过 {{site.data.keyword.slportal}} 或在该控制台外部通过其他任何方法进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步。

**注意**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部管理任何 {{site.data.keyword.vmwaresolutions_short}} 组件（在订购实例时安装到 {{site.data.keyword.cloud_notm}} 帐户中）可能会使环境变得不稳定。这些管理活动包括：
*  添加、修改、返回或除去组件
*  关闭组件电源

   这些活动的例外情况包括在 {{site.data.keyword.slportal}} 中管理共享存储器文件共享。此类活动包括：订购、删除（如果已安装，可能会影响数据存储）、授权和安装共享存储器文件共享。

### 相关链接

* [查看 NetApp ONTAP Select 实例](np_viewinginstances.html)
* [删除 NetApp ONTAP Select 实例](np_deletinginstance.html)
* [NetApp ONTAP 文档中心](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html)
* [将专用存储器连接到 NetApp ONTAP Select 部署](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)

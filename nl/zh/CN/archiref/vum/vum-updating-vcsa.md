---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# VCSA 更新和 SSO 链接的 vCenter

## PSC 和 VCSA 更新

本部分说明与 vCentre Server Appliance (VCSA) 和 Platform Services Controller (PSC) 相关的内容。这两种设备都是 VCSA 设备，但具有不同的角色。升级具有外部 PSC 的 vSphere 时，请首先升级 PSC，接着升级 VCSA，再升级 ESXi 主机，最后升级虚拟机中的硬件版本和 VMware Tools。

VUM 不会更新 PSC/VCSA。以下信息描述了更新这些设备的过程。VMware vCenter Server on {{site.data.keyword.cloud}} 实例中部署的 PSC/VCSA 没有因特网访问权，因此必须首先将更新捆绑软件下载到跳板机。

PSC/VCSA 是通过设备管理控制台（而不是 vSphere Web Client）进行更新的。使用浏览器以及 PSC/VCSA IP 地址和端口 5480 来访问 PSC/VCSA 设备管理控制台。

更新之前，您必须启动设备的快照或 PSC/VCSA 的备份。确保一切运行正常，然后在几天内除去快照，以避免性能下降。此外，在尝试任何升级之前，请先查看 VMware 发行说明，以了解针对指定发行版的任何特定指示信息。

要更新 PSC/VCSA，请执行以下步骤：
1. 可以通过转至 VMware 补丁[下载中心](https://my.vmware.com/group/vmware/patch#search)，登录并从**按产品搜索**菜单中选择 VC 来下载更新。选择相应的补丁，然后单击**下载**。
2. 使用 vSphere Web Client 将 ISO 文件上传到 vCenter 数据存储库。
3. 将更新 ISO 文件安装到 vCenter Server。
4. 生成 vCenter Server 的快照。
5. 登录到 vCenter 设备管理控制台：`https://vcenterip:5480`（对于 PSC）或 `https://vcenterip:5480`（对于 VCSA）
6. 转至**更新**部分，选择**检查更新**，然后选择**检查 CDROM**。这将列出更新。
7. 选择**安装更新**，然后选择**接受** EULA。这将安装更新。
8. 更新完成后，必须返回到设备管理控制台，然后选择重新启动控制台。
9. 重新登录到 vSphere Web Client 并检查是否有任何错误。通过选择**主页** > **主机和集群**，选择数据中心或集群，选择 **Update Manager** 选项卡，然后单击**扫描更新**，从而完成对 VUM 的手动扫描。如果手动扫描生成错误，请参阅[在 vCenter Server Appliance 6.5 上重置 VMware Update Manager 数据库 (2147284)](https://kb.vmware.com/s/article/2147284)。
10. 测试后，如果需要回退，请还原为快照或使用先前的备份复原 vCenter。

## SSO 链接的 vCenter

如果您具有主 vCenter Server 实例和辅助 vCenter Server 实例，说明 VCSA 已配置为位于单个 vCenter Single Sign-On (SSO) 域中。每个 VCSA 都拥有一个已部署的 VUM 实例。您修改的配置属性仅应用于指定的 VUM 实例，而不会传播到组中的其他实例。

可以通过从导航栏中选择 VUM 实例注册到的 VCSA 的名称，从而指定 VUM 实例。还可以管理基线和基线组，以及仅扫描和修复 VUM 实例注册到的 VCSA 所管理的库存对象。

### 相关链接

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）

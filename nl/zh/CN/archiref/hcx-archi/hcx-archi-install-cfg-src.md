---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---
# 在源上安装和配置 HCX
{: #hcx-archi-install-cfg-src}

内部部署安装需要部署 HCX 管理设备，并向 vCenter 以及一个或多个支持 VCF/VCS HCX 的云端点注册该设备。

## 安装 HCX Manager 设备
{: #hcx-archi-install-cfg-src-install-hma}

在内部部署 vCenter 中安装 HCX Manager 设备。

1. 登录到**我的 VMware**，然后从产品下载页面中下载 Hybrid Cloud Services OVA 文件。
2. 打开浏览器并登录到 vSphere Web Client。此任务无法在 vSphere Client 中执行。查看**主页**选项卡。
3. 在**清单树**列表中，单击**主机和集群**。
4. 展开层次结构以显示数据中心。
5. 右键单击目标数据中心，并从菜单中选择**部署 OVF 模板**。**部署 OVF 模板**菜单项可能需要几秒钟才会显示。
6. 选择**部署 OVF 模板**。
  1. 选择**本地文件**，然后单击**浏览**以查找下载到计算机的 OVA 文件。单击**下一步**。
  2. 在**查看详细信息**页面上，选中**接受额外配置选项**框，然后单击**下一步**。
  3. 在**接受 EULA** 页面上，向下滚动以查看 VMware 用户许可协议。单击**接受**，然后单击**下一步**。
  4. 在**选择名称和文件夹**页面上，根据需要编辑名称，然后选择 Hybrid Cloud Services 的位置。单击**下一步**。
  5. 在**选择资源**页面上，选择安装位置。
  6. 在**选择存储器**页面上，为 Hybrid Cloud Services 选择存储器，然后单击**下一步**。从**选择虚拟盘格式**列表中，可以选择**精简配置**或**密集配置**。
  7. 在**设置网络**页面上，将 Hybrid Cloud Services 适配器映射到从**目标**列表中选择的主机网络。
7. 在**定制模板**页面上，输入特定于环境的值：
  * 对于密码，命令行界面 (CLI) 和 Web 用户界面的缺省用户名都是 **admin**。需要用于登录到 Web 用户界面的 **admin** 用户和密码，此外还需要可以设置其密码的 **root** 用户帐户。
  * 输入并再次输入 CLI **admin** 用户密码。
  * 输入并再次输入 CLI **root** 用户密码。未来，如果需要 VMware 全球支持服务 (GSS) 提供帮助，可能必须共享此密码，GSS 才能对系统进行故障诊断。
  * 对于网络属性，输入 HCX Manager VM 的主机名。输入网络 IPv4 地址、IPv4 前缀 (CIDR) 和缺省网关。下表显示了样本值：

表 1. 网络属性的样本值

|字段|值|
|--------------------------|-----------------|
|主机名|HCM_1|
|网络 1 IPv4 地址|192.168.200.101|
|网络 1 IPv4 前缀|24|
|缺省 IPv4 网关|192.168.200.1|
|网络 1 IPv6 地址|                 |
|网络 1 IPv6 前缀|                 |

8. 复查 vService 绑定页面。单击**下一步**以继续。
9. 在**即将完成**页面上，执行以下步骤：
  * 选中**部署后打开电源**框。
  * 复查 Hybrid Cloud Services 设置，然后单击**完成**。Hybrid Cloud Services 设备可能需要几分钟才能打开电源。
  * 要检查状态，请转至 vSphere Web Client 主页，然后在**主页**选项卡上，转至**清单**，然后单击**主机和集群**。展开数据中心层次结构，然后单击 Hybrid Cloud Services 虚拟机以在中央窗格中显示摘要。
  * 查看**摘要**选项卡，控制台会显示**已打开电源**，并且**启动**按钮为绿色。
10. HCX Manager 已打开电源并准备好向 vCenter 注册。

## 相关链接
{: #hcx-archi-install-cfg-src-related}

* [准备安装环境](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-prep-install)

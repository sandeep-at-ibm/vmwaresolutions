---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 客户机部署
{: #hcxclient-vcs-client-deployment}

最小的 HCX 安装包含单个云和客户机端部署。

HCX 客户机端可以安装在 HCX 支持的任何版本的 vSphere 上，前提是客户机端与云端之间存在网络连接。

## 需求
{: #hcxclient-vcs-client-deployment-req}

|组件|CPU 计数|内存 (GB)| 磁盘 (GB) |
|--------|--------|---------|-------|
|HCX Manager|4| 12G |  60G |
| HCX Interconnect (HCX-IX) |4| 3G |  2G |
| HCX Network Extension (HCX-NE) |4| 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) |8| 14G |  100G |

## 客户机许可
{: #hcxclient-vcs-client-deployment-licensing}

HCX 是一项服务。HCX 按站点和虚拟机 (VM) 获得许可，这通过 VMware 维护的许可服务器进行管理。HCX 云和客户机端实例需要在其整个生命周期内与 VMware 注册站点进行通信。
- 必须允许 80 和 443 上的流量流至 `https://connect.hybridity.vmware.com`
- 针对 {{site.data.keyword.vmwaresolutions_full}} 控制台提供的客户机端安装，提供了一次性使用的注册密钥。每个客户机端 HCX 安装都需要一个密钥。

### 订购内部部署 HCX 许可证的过程
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 滚动到**内部部署 HCX 许可证**表，然后单击**供应新项**。
3. 指定许可证名称。
4. 单击订单适用条款的链接，并确保在订购许可证之前同意这些条款。
5. 单击**供应**。

## IP 地址需求
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

要部署 HCX，必须在内部部署和目标 IBM Cloud 中提供适当数量的 IP 地址。

* vMotion 地址
  保留单独的网络用于 vMotion 是内部部署数据中心的常见做法。云网关必须有权访问 vMotion 网络。如果无权访问，那么需要额外的 IP 地址与 vMotion 网络进行通信。

* 内部部署
  * 一个 IP 地址用于 HCX Manager 设备。
  * 每个互联设备对应一个 IP 地址，如果有单独的 vMotion 网络，请添加一个 IP 地址。
  * 每个标准网络扩展对应一个 IP 地址

* IBM Cloud
  * 每个连接到 IBM Cloud 的 HCX Manager 设备两个 IP 地址。这些地址可用于连接到因特网或者一个或多个 Direct Connect 线路。
  * 如果有单独的 vMotion 网络连接，请添加一个 IP 地址。

## 客户机端 OVA 下载
{: #hcxclient-vcs-client-deployment-client-ova}

客户机端 HCX 是用户部署的，需要具有对源 vCenter 的管理员级别许可权。本文撰写之时，HCX 客户机端管理器 OVA 大约为 1.7 GB。使用 {{site.data.keyword.vmwaresolutions_short}} 控制台订购 HCX 时，会提供一个 URL，其中包含用于下载客户机端 HCX 版本的链接，该版本与部署在云端的 HCX 版本相匹配。此链接在云端 HCX Manager 用户界面 (UI) 中提供。

此外，还提供一次性使用注册密钥。使用以下步骤来配置使用注册。

1. 从云端 HCX UI 中提供的链接下载 HCX 客户机（企业）OVA。
    1. 使用 IBM 提供的 HCX 注册 UI 登录到云端 HCX UI。
    2. 使用云 vCenter 标识和密码登录到 UI。
    3. 在**管理**选项卡上，选择**请求下载链接**以下载客户机端 OVA。使用部署了 OVA 的源 vCenter 的本地“跳转框”来完成此步骤。

## 在源上安装和配置 HCX
{: #hcxclient-vcs-client-deployment-install-cfg-src}

内部部署安装需要部署 HCX 管理设备，并向 vCenter 环境注册该设备。

### 安装 HCX Manager 设备
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

在内部部署 vCenter 中安装 HCX Manager 设备。
1. 登录到**我的 VMware**，然后从产品下载页面中下载 Hybrid Cloud Services OVA 文件。
2. 打开浏览器并登录到 vSphere Web Client。查看**主页**选项卡。
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
10. HCX Manager 已打开电源并准备好向内部部署 vCenter 注册。

## HX Manager Appliance 的初始配置
{: #hcxclient-vcs-client-deployment-inital-config}

1. 确保混合云服务虚拟设备具有对 `https://connect.hcx.vmware.com` 的出站访问权
2. 使用 **admin** 登录到混合云服务虚拟设备管理界面 `https://<IP>:9443`
3. 提供客户机端必备软件中收集的许可证密钥。
4. HCX 云数据中心位置
    - 输入离 HCX 云实例所在的数据中心最近的城市。如果该城市不存在，请选择最近的主要城市。
5. 提供系统名称

## 导入 vSphere 服务器证书
{: #hcxclient-vcs-client-deployment-import-cert}

1. 登录到 HCX Manager 管理界面 `https://<IP>:9443`
2. 选择**管理**选项卡，在**证书** -> **可信 CA 证书**下
3. 导入 vSphere 服务器 Web 站点
   1. 选择从 URL 导入证书，并键入 HCX 云端注册 URL。
     * 圣保罗：`https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## 向 vCenter/SSO/NSX 注册 HCX Manager 的过程
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. 登录到 Hybrid Cloud Services 服务虚拟设备。
2. 单击**管理设置**磁贴。
  1. 在左侧窗格中的**配置系统**下，选择 vCenter。
  2. 单击右上方的**添加 vCenter**。
  3. 输入格式为 `https://vCenter` 或 `https://vCenter` 的 vCenter Server 的 IP 地址。
    * 例如，`https://My-vCenter` 或 `https://10.108.26.211`。
  4. 输入 vCenter Server 用户名和密码。使用的帐户必须具有 vCenter 管理员角色。
  5. 单击**确定**。显示_您需要重新启动应用程序_消息时，不要重新启动。
3. 配置 SSO/查找服务。
  6. 单击**管理**选项卡。
  7. 单击**查找服务 URL** 文本框旁边的**编辑**。
  8. 输入以下格式的查找网络服务端点：
    * 对于 vCenter Server 6.5 `https://psc/`
  9.  根据需要提供 NSX 详细信息。
  10. 单击**确定**。显示重新启动 Web 引擎的消息时，不要重新启动。
4. 单击**摘要**选项卡，并找到**混合管理组件**部分。停止并启动应用程序引擎和 Web 引擎。
5. 要最终完成注册，请从 vSphere Web Client 注销。重新登录到 vSphere Web Client，验证 HCX 选项卡是否存在。

## 结果
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

请注意现有**混合云**图标和左侧的 **Hybrid Cloud Services** 菜单项。Hybrid Cloud Services 注册会更新这些标签。在清单中，图标标签会变为 **Hybrid Cloud Services**。

## 相关链接
{: #hcxclient-vcs-client-deployment-related}

* [HCX 组件和术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [准备安装环境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 内部部署服务网](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合云迁移](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [监视参数和组件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

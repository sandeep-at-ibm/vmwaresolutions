---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购和删除 VMware vCenter Server on IBM Cloud 单节点试用版实例
{: #vc_trial_hybrid_orderinginstance}

VMware vCenter Server on {{site.data.keyword.cloud}} 单节点试用版是一种托管的单租户专用云，可将 VMware vSphere 堆栈作为服务交付。虽然客户机管理的环境通常至少部署有 3 个节点，但通过此单节点试用版，能以低成本来体验混合云实施的优点。

此试用版是概念验证的理想选择，可展示 IBM 初始部署高级自动化的速度，以及将简单的非生产工作负载转入云中的简便性。通过使用 VMware Hybrid Cloud Extension (HCX)，可以将内部部署数据中心网络安全地扩展到 {{site.data.keyword.CloudDataCent_notm}}，同时降低互连配置的网络复杂性。HCX 将底层联网资源抽象到公用因特网上的隧道，以便您可以无缝地双向移动工作负载，而无需重新设置虚拟机 (VM) 的 IP。通过使用 HCX，不必以内部部署方式安装 VMware NSX，HCX 会向后兼容旧版本的 vSphere。  

单节点试用版仅适用于概念验证。不要在此环境中运行生产工作负载。不支持添加和除去主机和集群、订购其他附加组件服务以及应用更新等管理功能。
{:important}

此试用版最长可使用 90 天。试用版使用时间到期后，可以删除此环境，然后供应满足您的容量需求的高可用性环境。

有关体系结构设计的信息，请参阅[针对 vCenter Server on IBM Cloud 单节点试用版的 HCX on IBM Cloud 体系结构设计](/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)。

## vCenter Server 单节点试用版实例的技术规范
{: #vc_trial_hybrid_orderinginstance-specs}

vCenter Server 单节点试用版实例中包含以下组件：

标准化硬件配置的可用性和定价可能会因选择用于部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### 裸机服务器
{: #vc_trial_hybrid_orderinginstance-bare-metal}

双 Intel Xeon Gold 5120（28 个核心，2.20 GHz）处理器，384 GB RAM。

### vCenter Server 单节点试用版实例的联网规范
{: #vc_trial_hybrid_orderinginstance-networking-specs}

订购了以下联网组件：
*  10 Gbps 双公用和专用网络上行链路
*  三个 VLAN（虚拟 LAN）：一个公用 VLAN 和两个专用 VLAN
*  一个 VXLAN（虚拟可扩展 LAN），带 DLR（分布式逻辑路由器），用于处理连接到第 2 层 (L2) 网络的本地工作负载之间的潜在东-西通信。VXLAN 部署为样本路由拓扑，可以基于该拓扑进行构建，或者进行修改或将其除去。还可以通过将其他 VXLAN 连接到 DLR 上的新逻辑接口来添加安全区域。
*  两个 VMware NSX Edge 服务网关：
  * 用于出站 HTTPS 管理流量的安全管理服务 VMware NSX Edge 服务网关 (ESG)，由 IBM 部署为管理联网拓扑的一部分。IBM 管理 VM 使用此 ESG 来与自动化相关的特定外部 IBM 管理组件进行通信。

    您无法访问此 ESG，也无法使用此 ESG。如果对其进行修改，那么可能无法在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理 vCenter Server 单节点试用版实例。此外，请注意，使用防火墙或禁用与外部 IBM 管理组件的 ESG 通信将导致 {{site.data.keyword.vmwaresolutions_short}} 无法使用。
{:important}
  * 用于出站和入站 HTTPS 工作负载流量的客户管理的安全 VMware NSX Edge 服务网关，由 IBM 部署为模板，您可修改此模板来提供 VPN 访问或公共访问。

### 虚拟服务器实例
{: #vc_trial_hybrid_orderinginstance-vsi}

订购了以下虚拟服务器实例 (VSI)：
* 用于 IBM CloudBuilder 的 VSI，在完成实例部署后取消。
* 用于 Microsoft Active Directory (AD) 的 Microsoft Windows Server VSI 已部署并且可进行查找。此 VSI 充当在其中注册主机和 VM 的实例的 DNS。

### IBM 提供的许可证和费用
{: #vc_trial_hybrid_orderinginstance-license-and-fee}

vCenter Server 单节点试用版实例订单中包含以下许可证：
* VMware vSphere Enterprise Plus 6.5
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

vCenter Server 单节点试用版实例不支持自带许可证。
{:note}

## VMware HCX on IBM Cloud 的技术规范
{: #vc_trial_hybrid_orderinginstance-hcx-tech-specs}

vCenter Server 单节点试用版包含 HCX on {{site.data.keyword.cloud_notm}}。HCX on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

内部部署 HCX 实例仅包括许可和激活。
{:note}

### VMware NSX Edge 服务网关 (ESG) 的主动/被动对，以用于 HCX 管理
{: #vc_trial_hybrid_orderinginstance-esg}

* CPU：6 个 vCPU
* RAM：8 GB
* 磁盘：3 GB VMDK

### HCX Management Appliance - 虚拟机
{: #vc_trial_hybrid_orderinginstance-hcs-mgmt-appliance}

* CPU：4 个 vCPU
* RAM：12 GB
* 磁盘：60 GB VMDK

配置期间根据需要部署了更多 HCX 设备，以用于 L2 连接、WAN 优化和网关连接。

### HCX on IBM Cloud 服务的联网规范
{: #vc_trial_hybrid_orderinginstance-hcx-networking-specs}

* 一个具有 16 个 IP 地址的公用可移植子网
* 两个具有 64 个 IP 地址的专用可移植子网
* 专用可移植 vMotion 子网中的 8 个 IP 地址

## 订购 vCenter Server 单节点试用版实例的需求和规划
{: #vc_trial_hybrid_orderinginstance-req}

确保确认以下需求并完成以下任务：
* 内部部署 HCX 实例的先决条件：
 * 需要 VMware vSphere 和 vCenter 5.5 或更高版本。
 * vSphere 环境必须具有用于将迁移到 {{site.data.keyword.cloud_notm}} 的 VMx 的分布式交换机。
 * HCX Manager 虚拟设备必须能够部署在内部部署环境中的专用网络上，并且必须允许它访问公用因特网。
 * 要使用 {{site.data.keyword.vmwaresolutions_short}} 订购实例，您必须具有 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户。在实例中订购的组件的成本将计入到该 {{site.data.keyword.cloud_notm}} 帐户。
 *  在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**设置**。
 * 复查实例名称需求：
    * 只允许使用字母数字字符和短划线 (-) 字符。
    * 实例名称必须以字母数字字符开头和结尾。
    * 实例名称的最大长度为 10 个字符。
    * 实例名称在您的帐户中必须唯一。

## 订购 vCenter Server 单节点试用版实例的过程
{: #vc_trial_hybrid_orderinginstance-procedure}

1. 在 **VMware vCenter Server on {{site.data.keyword.cloud_notm}} 单节点试用版**页面上，单击**继续**。
2. 在 **VMware vCenter Server 单节点试用版**页面上，完成请求 {{site.data.keyword.cloud_notm}} 基础架构帐户或提供现有**用户名**和 **API 密钥**的步骤，然后单击**检索**。

 如果 API 密钥已存在，那么将隐藏此部分。
 {:note}
3. 输入实例名称。
4. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。  

 缺省情况下，DAL09 {{site.data.keyword.CloudDataCent_notm}} 已预先选择。如果需要，请选择其他 {{site.data.keyword.CloudDataCent_notm}} 位置。
{:note}
5. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
   1. 复查实例的设置。
   2. 复查实例的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在订购实例之前确认您同意这些条款。
   4. 单击**供应**。

### 结果
{: #vc_trial_hybrid_orderinginstance-results}

实例的部署会自动启动，并会订购内部部署 HCX on {{site.data.keyword.cloud_notm}} 服务激活密钥。

#### HCX on IBM Cloud 的部署过程
{: #vc_trial_hybrid_orderinginstance-hcs-deploy-process}

部署 HCX on {{site.data.keyword.cloud_notm}} 会自动执行。以下步骤由 {{site.data.keyword.vmwaresolutions_short}} 自动化过程完成：
1. 为 {{site.data.keyword.cloud_notm}} 基础架构中的 HCX 订购三个子网：
   * 两个专有可移植子网，用于 HCX 管理。
   * 一个用于 VMware 激活和维护的公共可移植子网。此子网还用于 HCX 互连。

   为 HCX 订购的子网中的 IP 地址旨在由 VMware on {{site.data.keyword.cloud_notm}} 自动化进行管理。这些 IP 地址无法分配给您所创建的 VMware 资源，例如 VM 和 NSX Edge。如果需要更多 IP 地址用于 VMware 工件，那么必须向 {{site.data.keyword.cloud_notm}} 订购您自己的子网。
   {:important}
3. 为 HCX 创建三个资源池和 VM 文件夹，以用于 HCX 互连、本地 HCX 组件和远程 HCX 组件。
4. 部署并配置 VMware NSX Edge 服务网关 (ESG) 对，以用于 HCX 管理流量：
   * 使用订购的子网配置公用和专用上行链路接口。
   * 将 ESG 配置为启用了高可用性 (HA) 的超大型 Edge 设备对。
   * 将防火墙规则和网络地址转换 (NAT) 规则配置为允许进出 HCX Manager 的入站和出站 HTTPS 流量。
   * 配置负载均衡器规则和资源池。这些规则和资源池用于将与 HCX 相关的入站流量转发到 HCX Manager 和 vCenter Server（具有嵌入式 Platform Services Controller）的相应虚拟设备。
   * 应用 SSL 证书以对通过 ESG 流入的与 HCX 相关的入站 HTTPS 流量进行加密。

   HCX 管理 Edge 专用于处理内部部署 HCX 组件和云端 HCX 组件之间的 HCX 管理流量。不要修改 HCX 管理 Edge 或将其用于 HCX 网络扩展。请改为创建单独的 Edge 用于网络扩展。此外，使用防火墙或者禁用与专用 IBM 管理组件或公用因特网的 HCX 管理 Edge 通信，可能会对 HCX 功能产生负面影响。
   {:important}

5. 部署、激活和配置 HCX Manager on {{site.data.keyword.cloud_notm}}：
   * 向 vCenter Server 注册 HCX Manager。
   * 配置 HCX Manager、vCenter Server（具有嵌入式 Platform Services Controller）和 NSX Manager。
   * 配置 HCX Fleet。
   * 配置本地和远程 HCX 部署容器。
6. 向 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 DNS 服务器注册 HCX Manager 的主机名和 IP 地址。

#### 查看实例详细信息
{: #vc_trial_hybrid_orderinginstance-view-inst-details}

您可以通过查看实例详细信息来检查部署的状态。在左侧导航窗格中，单击**资源**，然后找到 **vCenter Server 实例**或**内部部署 HCX 实例**表，以查看有关所订购实例的信息。

成功部署实例后，本主题的*技术规范*部分中所述的组件已安装在 VMware 虚拟平台上，并且内部部署 HCX on {{site.data.keyword.cloud_notm}} 服务激活密钥在**内部部署 HCX 实例**表中列出。

实例的状态会更改为**可供使用**，并且您收到相关电子邮件通知。

### 后续步骤
{: #vc_trial_hybrid_orderinginstance-next}

安装内部部署 HCX Enterprise Manager，并配置与 HCX on {{site.data.keyword.cloud_notm}} 实例的连接。

1. 在**资源**页面上找到内部部署激活密钥。
  1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
  2. 在 **vCenter Server 实例**表中，查看**类型**列以找到 vCenter Server 单节点试用版实例，并记下该实例的名称。
  3. 滚动到**内部部署 HCX 实例**表并查看**名称**列，以找到与订购的单节点实例同名但后缀为 *-OnPrem* 的实例。
  4. 记下**激活密钥**字段中的密钥。
2. 在 HCX on {{site.data.keyword.cloud_notm}} HCX Manager 控制台中获取内部部署 HCX Enterprise Manager Open Virtual Appliance (OVA)。
  1. 连接到 HCX 云控制台。
    1. 在 **vCenter Server 实例**表中，单击单节点试用版实例以查看实例详细信息。
    2. 在**访问信息**下，找到并记下 vCenter 凭证。
    3. 在左侧导航窗格中，单击**服务**。
    4. 在**服务**页面上，单击 **HCX on IBM Cloud**。
    5. 在 **HCX on IBM Cloud** 详细信息页面上，找到并记下 **HCX 云 IP**。
    6. 确保已连接到 VPN 来访问 {{site.data.keyword.cloud_notm}} 专用网络。
    7. 单击**查看 HCX 云控制台**。
  2. 在 **HCX 云控制台**中，完成以下步骤：
      1. 单击**管理**选项卡。
      2. 在**系统更新**选项卡上，单击**请求下载链接**。
      3. 单击**复制链接**，然后使用此链接将 HCX Enterprise Client 下载到有权访问内部部署 vSphere 环境的内部部署环境中。
3. 在 VMware vSphere Web Client 中，将 HCX Enterprise Client 作为 HCX Manager 虚拟设备 (HCX Manager) 部署到内部部署环境中。有关更多信息，请参阅[安装 HCX Enterprise Manager OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-C61E107C-1F5F-4615-9BA9-351900CDB69E.html)。

    必须在专用网络上部署此内部部署 HCX Manager，并允许它访问公用网络。可以使用 NSX Edge、Vyatta 或类似网关，以允许通过因特网访问内部部署 HCX Manager。如果用于专用网络访问和公用网络访问的网关不同，那么建议您使用缺省网关来允许公用网络访问，并通过内部部署的 **HCX Manager 管理控制台**创建静态路由以用于专用网络访问。  
    {:note}
4. 使用步骤 1 中记录的内部部署激活密钥来激活内部部署 HCX Enterprise Manager VM。
  1. 使用部署 OVA 时指定的凭证登录到内部部署 HCX Enterprise Manager VM。
  2. 在提示时输入激活密钥。

  有关更多信息，请参阅 [HCX 激活和初始配置](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-6A4740C1-2225-444C-8ADC-CBE54F181536.html)。
  {:note}
5. 自签名 SSL 证书已在 HCX on {{site.data.keyword.cloud_notm}} 服务上生成。您必须通过完成以下步骤将该证书导入到内部部署 HCX Manager：
    1. 在内部部署 **HCX Manager 管理控制台**中，单击**管理**选项卡。
    2. 在左侧导航窗格中，单击**可信 CA 证书**，然后单击右侧的**导入**。
    3. 单击 **URL**，然后输入要应用的证书的 URL，即 **HCX 云 IP** (``https://<cloud-side public IP>``)，可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台的 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到该 IP 地址。
    4. 单击**应用**。
6. 继续执行初始配置并构建互连。有关更多信息，请参阅[安装和配置 VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html)。
7. 将 VMware HCX 中的网络从内部部署扩展到 {{site.data.keyword.cloud_notm}}。有关更多信息，请参阅[通过 VMware HCX 扩展网络](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g)。
8. 在内部部署和 {{site.data.keyword.cloud_notm}} 之间迁移 VM。有关更多信息，请参阅[通过 VMware HCX 迁移虚拟机](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA)。

您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理在 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 基础架构组件，而不能在 {{site.data.keyword.slportal}} 中或在该控制台外部通过其他任何方法对这些组件进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步，并且会使环境变得不稳定。
{:important}

## 删除 vCenter Server 单节点试用版实例的过程
{: #vc_trial_hybrid_orderinginstance-deleting-procedure}

删除 vCenter Server 单节点试用版实例时，会按顺序释放以下组件：

1. 所有部署的服务
3. VMware 产品许可证
4. ESXi 服务器
5. 子网
6. VLAN

由于资源依赖关系，删除实例后，不会立即释放该实例中的组件。例如，在 {{site.data.keyword.cloud_notm}} 基础架构完全回收 ESXi 服务器（在 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束时发生）后，才能删除子网和 VLAN。在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时，将删除子网和 VLAN，此时实例删除操作完成。

在所删除实例的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
   {:note}

要删除 vCenter Server 单节点试用版实例，请完成以下步骤：

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，找到要删除的实例。
3. 在**操作**列中，单击“删除”图标。
   实例的状态会更改为**正在删除**。成功删除实例后，会释放该实例的组件，并且实例的状态会更改为**已删除**。
4. 如果要在 {{site.data.keyword.vmwaresolutions_short}} 控制台中除去实例记录，请完成以下步骤：
   1. 在**操作**列中，再次单击“删除”图标。
   2. 在**删除实例**窗口中，单击**确定**。

## 相关链接
{: #vc_trial_hybrid_orderinginstance-related}

* [针对 vCenter Server on IBM Cloud 单节点试用版的 HCX on IBM Cloud 体系结构设计](https://console.bluemix.net/docs/services/vmwaresolutions/archiref/trial/vc_trial_hcx_arch.html)
* [VMware Hybrid Cloud Extension 文档](https://hcx.vmware.com/#/vm-documentation)
* [获取 HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购、查看和删除 Migration and App Modernization 单节点试用版实例
{: #cloud_modern_bundle_orderinginstance}

订购 Migration and App Modernization 单节点试用版实例之前，请复查规划需求。

## 订购 Migration and App Modernization 单节点试用版实例的需求和规划
{: #cloud_modern_bundle_orderinginstance-req}

确保确认以下需求并完成以下任务。

### 内部部署 HCX 实例的先决条件
{: #cloud_modern_bundle_orderinginstance-hcx-req}

* 需要 VMware vSphere 和 vCenter 5.5 或更高版本。
* vSphere 环境必须具有用于将迁移到 {{site.data.keyword.cloud_notm}} 的 VM 的分布式交换机。
* HCX Manager 虚拟设备必须能够部署在内部部署环境中的专用网络上，并且必须允许它访问公用因特网。

### IBM Cloud 基础架构帐户
{: #cloud_modern_bundle_orderinginstance-account-req}

* 要使用 {{site.data.keyword.vmwaresolutions_short}} 订购实例，您必须具有 {{site.data.keyword.cloud_notm}} Infrastructure (SoftLayer) 帐户。在实例中订购的组件的成本将计入到该 {{site.data.keyword.cloud_notm}} 帐户。
*  在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**设置**。

### 实例名称需求
{: #cloud_modern_bundle_orderinginstance-inst-name-req}

复查实例名称需求：
* 只允许使用字母数字字符和短划线 (-) 字符。
* 实例名称必须以字母字符开头并以字母数字字符结尾。
* 实例名称的最大长度为 10 个字符。
* 实例名称在您的帐户中必须唯一。

## 订购 Migration and App Modernization 单节点试用版实例的过程
{: #cloud_modern_bundle_orderinginstance-procedure}

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格上的 **VMware**，然后单击**虚拟数据中心**部分中的 **Migration and App Modernization 单节点试用版**。
2. 在 **Migration and App Modernization 单节点试用版**页面上，单击**继续**。
3. 完成请求 {{site.data.keyword.cloud_notm}} 基础架构帐户的步骤，或提供现有**用户名**和 **API 密钥**，然后单击**检索**。

 如果 API 密钥已存在，那么将隐藏此部分。
 {:note}
4. 输入实例名称。
5. 选择要托管实例的 {{site.data.keyword.CloudDataCent_notm}}。  

 缺省情况下，DAL09 {{site.data.keyword.CloudDataCent_notm}} 已预先选择。如果需要，请选择其他 {{site.data.keyword.CloudDataCent_notm}} 位置。
{:note}
6. 在**订单摘要**窗格上，验证实例配置，然后再下订单。
   1. 复查实例的设置。
   2. 复查实例的估算成本。单击**定价详细信息**以生成 PDF 摘要。要保存或打印订单摘要，请单击 PDF 窗口右上角的**打印**或**下载**图标。
   3. 单击订单适用条款的链接，并在订购实例之前确认您同意这些条款。
   4. 单击**供应**。

### 结果
{: #cloud_modern_bundle_orderinginstance-results}

实例的部署会自动启动，并会订购内部部署 HCX on {{site.data.keyword.cloud_notm}} 服务激活密钥。

#### HCX on IBM Cloud 的部署过程
{: #cloud_modern_bundle_orderinginstance-hcx-deploy-process}

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
{: #cloud_modern_bundle_orderinginstance-view-inst-details}

您可以通过查看实例详细信息来检查部署的状态。在左侧导航窗格中，单击**资源**，然后找到 **vCenter Server 实例**或**内部部署 HCX 实例**表，以查看有关所订购实例的信息。

成功部署实例后，本主题的*技术规范*部分中所述的组件已安装在 VMware 虚拟平台上，并且内部部署 HCX on {{site.data.keyword.cloud_notm}} 服务激活密钥在**内部部署 HCX 实例**表中列出。

实例的状态会更改为**可供使用**，并且您收到相关电子邮件通知。

### 后续步骤
{: #cloud_modern_bundle_orderinginstance-next}

安装内部部署 HCX Enterprise Manager，并配置与 HCX on {{site.data.keyword.cloud_notm}} 实例的连接。

1. 在**资源**页面上找到内部部署激活密钥。
  1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
  2. 在 **vCenter Server 实例**表中，查看**类型**列以找到 Migration and App Modernization 单节点试用版实例，并记下该实例的名称。
  3. 滚动到**内部部署 HCX 实例**表并查看**名称**列，以找到与订购的单节点实例同名但后缀为 *-OnPrem* 的实例。
  4. 记下**激活密钥**字段中的密钥。
2. 在 HCX on {{site.data.keyword.cloud_notm}} HCX Manager 控制台中获取内部部署 HCX Enterprise Manager Open Virtual Appliance (OVA)。
  1. 连接到 HCX 云控制台。
    1. 在 **vCenter Server 实例**表中，单击 Migration and App Modernization 单节点试用版实例以查看实例详细信息。
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
    3. 单击 **URL**，然后输入要应用的证书的 URL。这是 **HCX 云 IP** (``https://<cloud-side public IP>``)，可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台的 HCX on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到该 IP。
    4. 单击**应用**。
6. 继续执行初始配置并构建互连。有关更多信息，请参阅[安装和配置 VMware HCX Enterprise](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-A26BFB16-FA94-426F-8E18-15BAD4BF840E.html)。
7. 将 VMware HCX 中的网络从内部部署扩展到 {{site.data.keyword.cloud_notm}}。有关更多信息，请参阅[通过 VMware HCX 扩展网络](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-DD9C3316-D01C-4088-B3EA-84ADB9FED573.html?hWord=N4IghgNiBcIKIA8AuBTAdgEwJZoOYAI0UkB3AewCcBrAZxAF8g)。
8. 在内部部署和 {{site.data.keyword.cloud_notm}} 之间迁移 VM。有关更多信息，请参阅[通过 VMware HCX 迁移虚拟机](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-D0CD0CC6-3802-42C9-9718-6DA5FEC246C6.html?hWord=N4IghgNiBcILIEsDmAnMAXBA7JACAagiugK6S5xgDGAFtgKYDOuA7gujQXC2CvbgAkAwgA0QAXyA)。

您只能在 {{site.data.keyword.vmwaresolutions_short}} 控制台中管理在 {{site.data.keyword.cloud_notm}} 帐户中创建的 {{site.data.keyword.vmwaresolutions_short}} 基础架构组件，而不能在 {{site.data.keyword.slportal}} 中或在该控制台外部通过其他任何方法对这些组件进行管理。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部更改这些组件，那么这些更改与控制台不同步，并且会使环境变得不稳定。
{:important}

## 删除 Migration and App Modernization 单节点试用版实例的过程
{: #cloud_modern_bundle_orderinginstance-deleting-procedure}

删除 Migration and App Modernization 单节点试用版实例时，会按顺序释放以下组件：

1. 所有部署的服务
3. VMware 产品许可证
4. ESXi 服务器
5. 子网
6. VLAN

由于资源依赖关系，删除实例后，不会立即释放该实例中的组件。例如，在 {{site.data.keyword.cloud_notm}} 基础架构完全回收 ESXi 服务器（在 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束时发生）后，才能删除子网和 VLAN。在 {{site.data.keyword.cloud_notm}} 基础架构计费周期（通常为 30 天）结束时，将删除子网和 VLAN，此时实例删除操作完成。

在所删除实例的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
   {:note}

要删除 Migration and App Modernization 单节点试用版实例，请完成以下步骤：

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，找到要删除的实例。
3. 在**操作**列中，单击“删除”图标。
   实例的状态会更改为**正在删除**。成功删除实例后，会释放该实例的组件，并且实例的状态会更改为**已删除**。
4. 如果要在 {{site.data.keyword.vmwaresolutions_short}} 控制台中除去实例记录，请完成以下步骤：
   1. 在**操作**列中，再次单击“删除”图标。
   2. 在**删除实例**窗口中，单击**确定**。

## 相关链接
{: #cloud_modern_bundle_orderinginstance-related}

* [vCenter Server 和 IBM Cloud Private 指南](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [开具有关 IBM Cloud Private 的凭单](https://www.ibm.com/mysupport/s/?language=en_US)
* [VMware Hybrid Cloud Extension 文档](https://hcx.vmware.com/#/vm-documentation)
* [获取 HCX OVA](https://docs.vmware.com/en/VMware-NSX-Hybrid-Connect/3.5.1/user-guide/GUID-B0471D10-6EB0-4587-9205-11BF0C78EC1C.html)

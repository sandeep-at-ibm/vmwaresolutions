---

copyright:

  years:  2019

lastupdated: "2019-06-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions：底层概览
{: #under_the_hood}

## 部署和管理 VMware 虚拟环境
{: #under_the_hood-deploy}

深入了解 {{site.data.keyword.vmwaresolutions_full}} 的体系结构，它是一个 {{site.data.keyword.cloud_notm}} 产品，用于部署和管理 VMware 虚拟环境。在本教程中，我们将说明该产品的组件，以便您可以了解各组件如何协同工作在公共云中供应和维护环境。

## 两家公司合作，推出一个简化解决方案
{: #under_the_hood-two-companies}

用户已自行或在专业服务人员的帮助下，将 VMware 虚拟环境部署到 IBM 公共云一段时间了。2016 年 2 月，[IBM 和 VMware 宣布建立合作伙伴关系](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external}，支持在 {{site.data.keyword.cloud_notm}} 中自动执行部署 VMware 软件和 VMware 环境的过程。这一合作伙伴关系取得的其中一项早期成果是能够通过 {{site.data.keyword.vmwaresolutions_short}} 控制台订购各种 VMware 产品部署和许可证，后来又支持在 {{site.data.keyword.cloud_notm}} 中提供 [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external}。此外，IBM 和 VMware 密切合作，联手制定了 IBM 公共云的 [VMware 标准参考体系结构和部署方案](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external}。

2016 年秋，IBM 和 VMware 联合发布了 {{site.data.keyword.vmwaresolutions_short}}。这组产品基于 VMware 的虚拟化技术，包括虚拟化计算 (VMware vSphere)、联网 (VMware NSX) 和可选的虚拟存储器 (VMware vSAN)。这些环境被相应地称为软件定义的数据中心。

{{site.data.keyword.vmwaresolutions_short}} 基于 VMware 技术而构建，显著简化了 IBM 公共云中这些软件定义的数据中心的部署和管理。现在，使用 {{site.data.keyword.vmwaresolutions_short}} 可自动（而不是手动）将标准参考体系结构的各个部分部署到 {{site.data.keyword.cloud_notm}}。先前需要数周时间进行部署和配置的环境，现在可以在几小时内就供应完毕。

通过此轻松部署，您可以专注于在 VMware 的基础之上实现解决方案，而不用关注如何构建环境。在随时可供您支配的环境中，可以构建跨私有云和 IBM 公共云的混合云解决方案，还可以在 IBM 公共云中构建云本机解决方案。通过组合多个部署，可以轻松地将灾难恢复或高可用性功能添加到解决方案中。

现在，我们来看看 {{site.data.keyword.vmwaresolutions_short}} 体系结构的底层。您将了解构成解决方案的不同组件，以及这些组件如何协同工作在 {{site.data.keyword.cloud_notm}} 中供应和管理软件定义的数据中心。您还将了解有关网络拓扑以及用于连接到环境的多个选项的信息。

## IBM Cloud for VMware Solutions 基础知识

软件定义的数据中心使用 [{{site.data.keyword.vmwaresolutions_short}} 控制台](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}进行供应和管理。您可以使用 IBM 标识帐户登录到控制台。

在 VMware Solutions 目录中，可以供应多种虚拟环境中的一种环境。特色虚拟化解决方案是 *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*，这种解决方案提供 VMware 的 vSphere Hypervisor、VMware vCenter Server、VMware NSX 以及可选的 VMware vSAN。此外，还可为此环境供应更多附加组件服务，用于提供备份、灾难恢复、迁移、安全性、合规性和联网服务。

订购 vCenter Server 实例之前，必须在 VMware Solutions 目录中配置 {{site.data.keyword.cloud_notm}} 基础架构 API 密钥。要执行此操作，请单击控制台左侧菜单中的[设置](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external}链接，然后在系统提示输入 {{site.data.keyword.cloud_notm}} 基础架构凭证的位置输入用户名和 API 密钥。系统会验证 API 密钥和帐户是否具有部署实例的相应许可权和设置。

订购 vCenter Server 实例时，请首先选择实例名称和 VMware vSphere 版本。所有 VMware 实例都与 Microsoft Active Directory 域控制器一起部署，并且为了实现单点登录，必须将实例指定为主站点或辅助站点。主实例是单点登录域中的第一个实例或唯一实例。可以部署更多辅助实例，并将这些实例与现有主实例的相同单点登录域相关联。接下来，选择是否使用自带 VMware 许可证，或者要向 {{site.data.keyword.cloud_notm}} 租用哪个许可证版本。最后，为实例选择 {{site.data.keyword.cloud_notm}} 区域和数据中心，以及集群中主机的 CPU 和内存特征。

在订单页面的下一部分中，输入实例的存储器和联网特征。可以为集群选择 vSAN 或 NFS 存储器；对于 vSAN，能够选择 vSAN 闪存磁盘的大小和数量以及 vSAN 许可证版本，或者对于 NFS，可选择 NFS 存储卷的大小和计数以及性能。对于联网，可选择主机的主机名前缀以及集群的子域和域。可以选择将 Active Directory 控制器部署为单个 {{site.data.keyword.cloud_notm}} 虚拟服务器实例 (VSI)，或部署为集群中的两个虚拟机（需要为其提供许可和激活）。

在 vCenter Server 订购页面的底部，可以从可为 VMware 实例部署的各种附加组件服务中进行选择，使用这些服务的费用将计入您的 {{site.data.keyword.cloud_notm}} 帐户。某些服务需要额外的配置，可在订购表单中进行指定。

订购表单会根据您的选择来计算并显示价格估算。在下订单之前，您有机会复查此估算并查看各种条款和条件。

### 部署选项
{: #under_the_hood-deploy-options}

vCenter Server 订购表单为实例提供了各种 CPU、内存和存储选项。新的选项会定期推出，因此请查看 {{site.data.keyword.cloud_notm}}“目录”以获取最新的可用性信息。

{{site.data.keyword.cloud_notm}} 使用三个 VLAN 来部署 vCenter Server 实例：一个公用 VLAN 和两个专用 VLAN。公用 VLAN 连接到双 10 GbE 接口，并且大部分保留供您使用，您可自行决定将其用于您自己工作负载部署的公共连接或隧道。但是，在部署时，将在公用 VLAN 上部署 NSX Edge 服务网关对，以允许某些附加组件服务连接到公用网络进行许可和计费。专用 VLAN 连接到单独的双 10 GbE 接口：第一个专用 VLAN 用于管理通信和 NSX VTEP，第二个专用 VLAN 用于 vMotion 并处理 NFS 存储器流量。

VMware 实例可以在 35 个不同的 {{site.data.keyword.CloudDataCents_notm}} 中进行供应。{{site.data.keyword.cloud_notm}} 不定期供应新的数据中心。请查看 {{site.data.keyword.cloud_notm}}“目录”以获取可用位置的最新列表。

### 实例部署
{: #under_the_hood-inst-deploy}

订购新的 VMware vCenter 实例时，可选择实例位置和规范。然后，{{site.data.keyword.vmwaresolutions_short}} 会使用您先前选择的 {{site.data.keyword.cloud_notm}} 用户名和 API 密钥来编排订购、安装和配置虚拟化环境的整个过程。这包括：

1. 订购 VLAN 和子网以进行联网。
2. 订购安装了 vSphere Hypervisor 的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。
3. 使用嵌入式 Platform Services Controller、VMware NSX Manager、NSX Controller 和 Edge 服务网关来部署和配置 VMware vCenter Server。
4. 订购和配置集群存储器，包括 VMware vSAN 或 {{site.data.keyword.cloud_notm}} 耐久性存储器。
5. 部署名为 IBM CloudDriver 的 IBM 管理组件。
6. 部署和配置为实例选择的任何附加组件服务。
7. 验证环境的安装和配置。

选择要在其中供应实例的 {{site.data.keyword.CloudDataCent_notm}}。提供的硬件在所选 {{site.data.keyword.CloudDataCent_notm}} 中可用，实例供应过程通常在 24 小时内完成。

供应了实例后，如果已通过 VPN 连接到 {{site.data.keyword.cloud_notm}} 帐户，那么可以直接通过工作站 Web 浏览器连接到 vCenter 服务器。

实例组件通常按其主机名（而不是其 IP 地址）进行访问。为了连接到 vCenter 并向其进行认证，应该通过将 vCenter 和 Platform Services Controller (PSC) 主机名添加到工作站的 hosts 文件（如“列表 1”中所示），确保工作站可以解析该主机名。您可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中您实例的**摘要**选项卡上找到主机名和 IP 地址。您还可能希望将 vSphere 主机的主机名和 IP 地址添加到 hosts 文件中。

*列表 1. hosts 文件*

<pre># Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# Dallas site hosts
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

部署实例后，可以通过控制台对实例进行管理。管理功能包括执行以下每个操作的能力：

* 在集群中部署和除去节点
* 在同一数据中心和 pod 中或者在备用数据中心和 pod 中，部署和除去其他集群
* 为实例部署和除去附加组件服务
* 升级实例的特定许可证版本

{{site.data.keyword.vmwaresolutions_short}} 控制台提供每个 vCenter Server 实例的详细视图。对于每个实例，**摘要**选项卡包含指向 vCenter 控制台的链接以及有关实例和管理组件的其他详细信息。**基础架构**选项卡显示有关实例的集群、主机、存储器和联网的详细信息，并允许您添加或除去集群、主机和存储器。在**更新和补丁**选项卡上，可以升级某些许可证版本。在**服务**选项卡上，可以查看和管理为实例部署的附加组件服务。**部署历史记录**选项卡显示对实例执行的所有操作的历史记录。

## IBM Cloud for VMware Solutions 组件
{: #under_the_hood-comp}

若干不同的组件协同工作来供应和管理环境。其中大部分组件会部署到 {{site.data.keyword.cloud_notm}} 帐户中。由于解决方案依赖于所有这些组件协同工作，因此不应在 {{site.data.keyword.cloud_notm}} 帐户中修改或取消其中任何组件。除去运行中实例的正确方法是使用控制台，而不是取消单个组件。

虽然这是一个集成的虚拟化环境，但各种虚拟化组件（例如，VMware 许可证）、基础架构组件（裸机服务器、VLAN、子网和存储器）和管理组件的成本会在 {{site.data.keyword.cloud_notm}} 发送给您的帐单中逐项列出。

### IBM Cloud for VMware Solutions 控制台
{: #under_the_hood-console}

您可登录到 [{{site.data.keyword.vmwaresolutions_short}} 控制台](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}来创建和管理实例。此部分解决方案负责环境的初始订购和供应以及环境的持续管理。已部署的实例使用 {{site.data.keyword.cloud_notm}} Private 网络与控制台进行通信。

### IBM CloudBuilder 组件
{: #under_the_hood-ibm-cb}

供应新实例时，控制台会将临时虚拟服务器实例 (VSI) 部署到 {{site.data.keyword.cloud_notm}} 帐户。此虚拟服务器称为 IBM CloudBuilder，用于执行所有实例组件的安装和配置以及对环境的验证。供应完成后，将删除 CloudBuilder。

### IBM CloudDriver 组件
{: #under_the_hood-ibm-cd}

与 CloudBuilder 十分类似，IBM CloudDriver 也是部署到 {{site.data.keyword.cloud_notm}} 帐户中的临时虚拟服务器实例 (VSI)，用于对实例执行后续操作。此组件根据需要进行部署，可配置或除去实例中的主机、集群、存储器或服务。

### VMware 组件
{: #under_the_hood-vmware-comp}

对于所有实例，vSphere Hypervisor 都会安装在裸机服务器上。然后，{{site.data.keyword.cloud_notm}} 会将集成了 Platform Services Controller (PSC)、NSX Manager、三个 NSX Controller 和两个 NSX Edge 服务网关对的 vCenter Server Appliance 部署到 VMware 管理集群。

### 其他组件
{: #under_the_hood-add-comp}

根据您的选择，会在集群中部署一个 Microsoft Windows VSI 或同时部署两个 Microsoft Windows 虚拟机作为管理组件的 Active Directory 服务器。您可以选择将自己的 Active Directory 服务器添加为其他身份源以用于管理访问。

无论您选择如何为自己的工作负载提供业务连续性，{{site.data.keyword.cloud_notm}} 都强烈建议您备份实例的管理组件。通过 {{site.data.keyword.vmwaresolutions_short}} 控制台，可以将集成的 IBM Spectrum Protect Plus 备份服务器或 Veeam Backup & Replication 备份服务器与实例一起部署。这些备份服务可以用作实例的[完整备份解决方案](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup)的一部分。

### 许可证
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}} 提供了若干 VMware 许可证（如 vCenter Server 和 NSX），这些许可证可安装到实例中，并且相关费用将计入您的 {{site.data.keyword.cloud_notm}} 帐户。

## IBM Cloud for VMware Solutions 网络体系结构
{: #under_the_hood-network}

vCenter Server 实例连接到公用 VLAN，供您用于部署的工作负载。公用 VLAN 大部分保留供您酌情使用，但一个 NSX Edge 服务网关对会连接到公用 VLAN，允许特定附加组件服务进行出站通信，以进行许可和计费。可以在不使用公用网络的情况下部署实例，对于这种情况，不一定支持所有附加组件服务，并且您可能需要提供 Web 代理才能支持使用特定附加组件服务。

vCenter Server 实例有两个专用 VLAN，可在系统管理程序的专用网络接口上一起中继。第一个专用 VLAN 用于管理连接（例如，vCenter 与系统管理程序的通信），并由 NSX 用于为已部署工作负载的所有 VXLAN 流量进行隧道传输。第二个专用 VLAN 用于 vMotion 并处理存储流量。存储流量可以是 NFS 或 vSAN 协议。

{{site.data.keyword.cloud_notm}} 在这些专用 VLAN 上提供了某些额外的服务。Active Directory 服务器通过专用管理 VLAN 与 {{site.data.keyword.cloud_notm}} DNS 服务器通信。主机和其他组件通过专用管理 VLAN 与 {{site.data.keyword.cloud_notm}} NTP 服务器进行通信。IBM CloudBuilder 和 CloudDriver 也通过此 VLAN 与 {{site.data.keyword.vmwaresolutions_short}} 控制台进行通信。主机通过专用存储器 VLAN 连接到 {{site.data.keyword.cloud_notm}} 耐久性存储器。

### 连接到实例
{: #under_the_hood-connect-inst}

您有若干选项可用于连接到实例。可以使用 [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/VPN-Access){:external} 直接连接到实例（例如，vCenter）中的专用 IP 地址。还可以为帐户订购 [{{site.data.keyword.cloud_notm}} 网络设备](https://www.ibm.com/cloud/network-appliances){:external}和 [{{site.data.keyword.cloud_notm}} 硬件或虚拟防火墙](https://www.ibm.com/cloud/network-security)，例如 FortiGate 和 vSRX。{{site.data.keyword.cloud_notm}} 还在网络和 {{site.data.keyword.cloud_notm}} 帐户中的 VLAN 之间提供[直接链路](https://www.ibm.com/cloud/direct-link){:external}。

要访问部署的 VM，可以将公共 IP 地址直接应用于 VM。但是，还可以使用 {{site.data.keyword.cloud_notm}} 网络设备和防火墙功能，通过 NAT 和防火墙来设置对 VM 的更安全公共访问。您还可以部署 NSX Edge 服务器，并使用这些服务器为 VM 设置 VPN 或 NAT 连接。

## 总结
{: #under_the_hood-conclusion}

在本教程中，您了解了 {{site.data.keyword.vmwaresolutions_short}} 的基本功能，用于在公共云中部署和管理标准化 VMware 虚拟化环境。您能够以前所未有的速度供应这些环境，因此可以将精力专注于在这些环境的基础之上部署应用程序和解决方案，以及将云连接在一起以实现灾难恢复或高可用性。

我们探索了部署到 {{site.data.keyword.cloud_notm}} 帐户中的各种组件，这些组件会显示在 {{site.data.keyword.cloud_notm}} 计费结算表上，并协同工作使环境保持正常运行。最后，我们探讨了解决方案的网络体系结构，以及用于与环境建立连接的一些选项：使用各种安全连接选项使通信保持专用，或者使用各种选项建立公用因特网连接。

既然您已了解了入门所需掌握的全部内容，接下来可立即着手在 {{site.data.keyword.cloud_notm}} 上部署下一个 VMware 虚拟化环境！

## 相关链接
{: #under_the_hood-related}

* [入门](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [VMware Solutions 体系结构](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)

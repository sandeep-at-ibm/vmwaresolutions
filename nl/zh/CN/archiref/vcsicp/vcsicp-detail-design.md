---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# 详细设计

## 公共服务组件
公共服务提供由云管理平台中其他服务使用的服务。这包括身份和访问权服务、域名服务和 NTP 服务。

图 1. ICP 公共服务

![ICP 公共服务](vcsicp-icp-commonservices.svg)

### 身份和访问权服务
作为 VCS 自动化的一部分，Microsoft Active Directory (AD) 用于身份管理。部署了单个 AD 虚拟服务器实例 (VSI)。vCenter 配置为利用 MS AD 认证，并且 ICP 也可以配置为进行 LDAP 认证。

###	域名服务
VCS 部署利用部署的 Microsoft Active Directory (AD) VSI 作为实例的 DNS 服务器。所有部署的组件（vCenter、PSC、NSX 和 ESXi 主机）都配置为指向作为其缺省 DNS 的 MS AD。

###	NTP 服务
VCS 部署利用 {{site.data.keyword.cloud}} 基础架构 NTP 服务器。所有部署的组件都将配置为利用这些 NTP 服务器。使设计中的所有组件都利用相同的 NTP 服务器对于证书和 MS AD 认证正常运行至关重要。

## 联网

### NSX-V 联网

NSX-V 的架构是使一个 NSX-V Manager 平台与一个 vCenter Server 实例相关联。NSX-V 可为 vSphere 环境中运行的应用程序提供联网服务。

通过利用 VCS 部署中包含的 NSX-V 联网，我们可以将 ICP 部署到 VXLAN 覆盖网络中。

ICP 部署有 Kubernetes 的缺省 Calico 网络堆栈，用于提供集群内的网络隔离。

图 2. 使用 NSX-V 联网的 ICP

![使用 NSX-V 联网的 ICP](vcsicp-nsxv-networking.svg)

有关更多信息，请参阅 [vCenter Server 联网指南](../vcsnsxt/vcsnsxt-intro.html)。

### NSX-T 联网

NSX-T 的架构是一个可以连接到任何类型应用程序（基于虚拟机或基于容器）的联网平台，在 vSphere 环境内部或外部运行。

ICP 提供了一个选项，用于将 Calico 联网替换为 NSX-T 实例，从而提供单个位置来管理网络和安全性。

图 3. 使用 NSX-T 联网的 ICP

![使用 NSX-T 联网的 ICP](vcsicp-icp-nsxt-networking.svg)

### 相关链接

* [VCS Hybridity Bundle 概述](../vcs/vcs-hybridity-intro.html)

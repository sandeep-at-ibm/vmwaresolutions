---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-13"

---

# 订购 VMware HCX on IBM Cloud

订购 VMware HCX on {{site.data.keyword.cloud_notm}} 服务时，可订购包含此服务的新 VMware vCenter Server with Hybridity Bundle 实例，也可通过向现有实例添加此服务来进行订购。

## 为新实例订购 VMware HCX on IBM Cloud

要订购包含 VMware HCX on {{site.data.keyword.cloud_notm}} 的新 VMware vCenter Server on IBM Cloud with Hybridity Bundle 实例，请在 {{site.data.keyword.vmwaresolutions_full}} 控制台订购该实例时在**服务**部分中选择 **VMware HCX on IBM Cloud**。


## 为现有实例订购 VMware HCX on IBM Cloud

要将 VMware HCX on {{site.data.keyword.cloud_notm}} 服务添加到现有 VMware vCenter Server on IBM Cloud with Hybridity Bundle 实例，请查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加服务**。

## VMware HCX on IBM Cloud 配置

要安装 HCX on {{site.data.keyword.cloud_notm}}，请完成以下设置：
1. 通过选择下列其中一个选项来指定 **HCX 互连类型**：
  * **公用网络**：HCX 通过公用网络在站点之间创建加密连接。
  * **专用网络**：HCX 通过专用网络在站点之间创建加密连接。
2. 指定**公共端点证书类型**。如果选择 **CA 证书**，请配置以下设置：
  * **证书内容**：输入 CA 证书的内容。
  * **专用密钥**：输入 CA 证书的专用密钥。
  * （可选）**密码**：输入专用密钥的密码（如果对专用密钥进行了加密）。
  * （可选）**重新输入密码**：重新输入专用密钥的密码。
  * （可选）**主机名**：要映射到 CA 证书的公共名称 (CN) 的主机名。HCX on {{site.data.keyword.cloud_notm}} 要求 CA 证书的格式必须是 NSX Edge 接受的格式。有关 NSX Edge 证书格式的更多信息，请参阅[导入 SSL 证书](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html)。
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## HCX on IBM Cloud 的部署过程

部署 HCX on {{site.data.keyword.cloud_notm}} 会自动执行。无论是订购 vCenter Server with Hybridity Bundle 实例时包含此服务，还是稍后再将此服务部署到实例中，都会通过 {{site.data.keyword.vmwaresolutions_short}} 自动过程来完成以下步骤：
1. 为 {{site.data.keyword.cloud_notm}} 基础架构中的 HCX 订购三个子网：
   * 一个专有可移植子网，用于 HCX 管理。
   * 一个专有可移植子网，用于 HCX 互联（如果为 **HCX 互连类型**选择了**专用网络**）。
   * 一个公有可移植子网，用于 HCX 互联（如果为 **HCX 互连类型**选择了**公用网络**）。此子网还用于激活和维护 VMware。

   **重要信息**：为 HCX 订购的子网中的 IP 地址旨在由 VMware on {{site.data.keyword.cloud_notm}} 自动化进行管理。这些 IP 地址无法分配给您所创建的 VMware 资源，例如 VM 和 NSX Edge。如果需要更多 IP 地址用于 VMware 工件，那么必须向 {{site.data.keyword.cloud_notm}} 订购您自己的子网。
2. 向 VMware 订购 HCX 激活密钥。
3. 为 HCX 创建三个资源池和 VM 文件夹，以用于 HCX 互连、本地 HCX 组件和远程 HCX 组件。
4. 部署并配置 VMware NSX Edge 服务网关 (ESG) 对，以用于 HCX 管理流量：
   * 使用订购的子网配置公用和专用上行链路接口。
   * 将 ESG 配置为启用了高可用性 (HA) 的超大型 Edge 设备对。
   * 将防火墙规则和网络地址转换 (NAT) 规则配置为允许进出 HCX Manager 的入站和出站 HTTPS 流量。
   * 配置负载均衡器规则和资源池。这些规则和资源池用于将与 HCX 相关的入站流量转发到 HCX Manager、vCenter Server 和 Platform Services Controller (PSC) 的相应虚拟设备。
   * 应用 SSL 证书以对通过 ESG 流入的与 HCX 相关的入站 HTTPS 流量进行加密。

   **重要信息**：HCX 管理 Edge 专用于处理内部部署 HCX 组件和云端 HCX 组件之间的 HCX 管理流量。不要修改 HCX 管理 Edge 或将其用于 HCX 网络扩展。请改为创建单独的 Edge 用于网络扩展。此外，请注意，使用防火墙或者禁用与专用 IBM 管理组件或公用因特网的 HCX 管理 Edge 通信，可能会对 HCX 功能产生负面影响。

5. 部署、激活和配置 HCX Manager on {{site.data.keyword.cloud_notm}}：
   * 向 vCenter Server 注册 HCX Manager。
   * 配置 HCX Manager、vCenter Server、PSC 和 NSX Manager。
   * 配置 HCX Fleet。
   * 配置本地和远程 HCX 部署容器。
6. 向 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 DNS 服务器注册 HCX Manager 的主机名和 IP 地址。

## 相关链接

* [HCX on {{site.data.keyword.cloud_notm}} 概述](hcx_considerations.html)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](../vcenter/vc_hybrid_addingremovingservices.html)
* [HCX 术语的词汇表](hcx_glossary.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension 概述](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 文档](https://hcx.vmware.com/#vm-documentation)

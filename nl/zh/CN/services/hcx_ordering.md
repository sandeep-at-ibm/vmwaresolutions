---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX deployment, HCX configuration, order HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 VMware HCX on IBM Cloud
{: #hcx_ordering}

订购 VMware HCX on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新 VMware vCenter Server 实例，也可通过向现有实例添加此服务来进行订购。

订购 VMware HCX on {{site.data.keyword.cloud_notm}} 服务时，需要承诺使用 12 个月。如果在 12 个月的承诺期结束之前删除主机或集群，那么将继续向您的帐户收取 HCX 组件的费用。
{:important}

要订购包含 VMware HCX on {{site.data.keyword.cloud_notm}} 的新 VMware vCenter Server 实例，请在 {{site.data.keyword.vmwaresolutions_short}} 控制台中订购该实例时在**服务**部分中选择 **HCX on IBM Cloud 3.5**。


## 为现有实例订购 VMware HCX on IBM Cloud
{: #hcx_ordering-existing}

要将 VMware HCX on {{site.data.keyword.cloud_notm}} 服务添加到现有 VMware vCenter Server 实例，请查看要为其添加该服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。

## VMware HCX on IBM Cloud 配置
{: #hcx_ordering-config}

要安装 HCX on {{site.data.keyword.cloud_notm}}，请完成以下设置：
1. 选中相应复选框以确认您同意与订购 HCX on {{site.data.keyword.cloud_notm}} 服务关联的条款。

   在 12 个月的承诺期到期日期之后，这些复选框即不会再显示。
   {:note}

2. 通过选择下列其中一个选项来指定 **HCX 网络连接**：
  * **公用网络**：HCX 通过公用网络在站点之间创建加密连接。许可证注册和计量通过公用网络执行。
  * **专用互联**：HCX 通过专用网络在站点之间创建加密连接。许可证注册和计量通过公用网络执行。
  * **专用网络**：HCX 通过专用网络在站点之间创建加密连接。许可证注册和计量通过专用网络经由 HTTP 代理执行。
3. 如果选择**专用网络**，请填写以下字段：
  * **代理地址**：代理服务器的 IPv4 地址。
  * **代理端口**：代理服务器端口。端口号通常为 8080 或 3128。
  * **用户名**：用户名（如果需要代理认证）。
  * **密码**：密码（如果需要代理认证）。
  * **重新输入密码**：重新输入用于验证代理认证的密码。
2. 指定**公共端点证书类型**。如果选择 **CA 证书**，请配置以下设置：
  * **证书内容**：输入 CA 证书的内容。
  * **专用密钥**：输入 CA 证书的专用密钥。
  * （可选）**密码**：输入专用密钥的密码（如果对专用密钥进行了加密）。
  * （可选）**重新输入密码**：重新输入专用密钥的密码。
  * （可选）**主机名**：要映射到 CA 证书的公共名称 (CN) 的主机名。HCX on {{site.data.keyword.cloud_notm}} 要求 CA 证书的格式必须是 NSX Edge 接受的格式。有关 NSX Edge 证书格式的更多信息，请参阅[导入 SSL 证书](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}。
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## HCX on IBM Cloud 的部署过程
{: #hcx_ordering-deploy}

部署 HCX on {{site.data.keyword.cloud_notm}} 会自动执行。无论是订购 vCenter Server 实例时包含此服务，还是稍后再将此服务部署到实例中，都会通过 {{site.data.keyword.vmwaresolutions_short}} 自动过程来完成以下步骤：
1. 为 {{site.data.keyword.cloud_notm}} 基础架构中的 HCX 订购三个子网：
   * 一个专有可移植子网，用于 HCX 管理。
   * 一个用于 HCX 互联的专用可移植子网。在为 **HCX 互联类型**选择了**专用网络**选项的情况下，会使用此子网。
   * 一个用于 VMware 激活和维护的公共可移植子网。如果为 **HCX 互联类型**选择了**公用网络**选项，那么还会将此子网用于 HCX 互联。

   为 HCX 订购的子网中的 IP 地址旨在由 VMware on {{site.data.keyword.cloud_notm}} 自动化进行管理。这些 IP 地址无法分配给您所创建的 VMware 资源，例如 VM 和 NSX Edge。如果需要更多 IP 地址用于 VMware 工件，那么必须向 {{site.data.keyword.cloud_notm}} 订购您自己的子网。
   {:important}
2. 如果针对 **HCX 网络连接**选择了**专用网络**，那么将在专用分布式虚拟交换机 (DVS) 上创建名为 **SDDC-DPortGroup-HCX-Private** 的端口组。
3. 向 VMware 订购 HCX 激活密钥。
4. 为 HCX 创建三个资源池和 VM 文件夹，以用于 HCX 互连、本地 HCX 组件和远程 HCX 组件。
5. 部署并配置 VMware NSX Edge 服务网关 (ESG) 对，以用于 HCX 管理流量：
   * 使用订购的子网配置公用和专用上行链路接口。
   * 将 ESG 配置为启用了高可用性 (HA) 的超大型 Edge 设备对。
   * 将防火墙规则和网络地址转换 (NAT) 规则配置为允许进出 HCX Manager 的入站和出站 HTTPS 流量。
   * 配置负载均衡器规则和资源池。这些规则和资源池用于将与 HCX 相关的入站流量转发到 HCX Manager 和 vCenter Server（具有嵌入式 Platform Services Controller）的相应虚拟设备。
   * 应用 SSL 证书以对通过 ESG 流入的与 HCX 相关的入站 HTTPS 流量进行加密。

   HCX 管理 Edge 专用于处理内部部署 HCX 组件和云端 HCX 组件之间的 HCX 管理流量。不要修改 HCX 管理 Edge 或将其用于 HCX 网络扩展。请改为创建单独的 Edge 用于网络扩展。此外，使用防火墙或者禁用与专用 IBM 管理组件或公用因特网的 HCX 管理 Edge 通信，可能会对 HCX 功能产生负面影响。
   {:important}

6. 部署、激活和配置 HCX Manager on {{site.data.keyword.cloud_notm}}：
   * 向 vCenter Server 注册 HCX Manager。
   * 配置 HCX Manager、vCenter Server（具有嵌入式 Platform Services Controller）和 NSX Manager。
   * 配置 HCX Fleet。
   * 配置本地和远程 HCX 部署容器。
7. 向 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 DNS 服务器注册 HCX Manager 的主机名和 IP 地址。

## 相关链接
{: #hcx_ordering-related}

* [HCX on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [HCX 术语的词汇表](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension 概述](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension 文档](https://cloud.vmware.com/vmware-hcx/resources){:external}

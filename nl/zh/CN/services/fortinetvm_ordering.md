---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering}

订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

## 为新实例订购 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-new}

可以使用下列其中一种方法订购包含 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **FortiGate Virtual Appliance on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **FortiGate Virtual Appliance on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-existing}

可以使用下列其中一种方法将 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **FortiGate Virtual Appliance on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

## 为专用实例订购 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-private}

为未配置公共接口的实例订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 时，必须提供代理服务器以完成安装。HTTP 代理服务器必须已配置并通过虚拟路由和转发 (VRF) 可用，才能开始安装 Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}。

要确保持续运行，FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 必须可通过因特网持久访问 Fortigate 许可证服务器。

## FortiGate Virtual Appliance on IBM Cloud 服务配置
{: #fortinetvm_ordering-config}

订购此服务时，请提供以下设置。

### FortiGuard 网络连接
{: #fortinetvm_ordering-config-network-connect}

为 FortiGuard 选择**公用网络**或**专用网络**。如果目标集群配置为仅使用专用网络接口，那么仅**专用网络**选项可用。此选项会确定 FortiGuard 将如何联系 Fortinet 许可证服务器以激活许可证并下载安全补丁，并且此选项不会影响工作负载数据平面。

如果选择**专用网络**，请指定以下设置：
* **代理 IP 地址**：代理服务器的 IPv4 地址。
* **代理端口号**：代理服务器的端口号，通常为 8080 或 3128。
* **代理用户名**：如果您需要代理认证，请输入代理服务器的用户名。
* **代理密码**：如果您需要代理认证，请输入代理服务器的密码。

### 名称
{: #fortinetvm_ordering-config-name}

输入服务名称。

### 部署大小
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}} 提供以下部署大小选项：
* 小型（2 个 vCPU/ 4 GB RAM）
* 中型（4 个 vCPU/ 6 GB RAM）
* 大型（8 个 vCPU/ 12 GB RAM）

### 许可模型
{: #fortinetvm_ordering-config-license}

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的许可模型提供了以下选项：
<dl class="dl">
        <dt class="dt dlterm">标准 FW</dt>
        <dd class="dd">此捆绑软件包含有状态包检查、VLAN 保护和高级日志记录、流入和流出防火墙规则、SSL/IPSec VPN 终止以及全天候支持。</dd>
        <dt class="dt dlterm">标准 FW + UTM</dt>
        <dd class="dd">此捆绑软件除了包含高级恶意软件防护 (AMP) 服务外，还包含所有标准防火墙服务。它包含 Antivirus、Botnet IP/Domain Service、Mobile Malware Security、FortiSandbox Cloud、Virus Outbreak Protection Service 和 Content Disarm & Reconstruct。此外，还包含 Web Filtering、IPS、Antispam、Application Control 和 FortiCare 服务。</dd>
        <dt class="dt dlterm">标准 FW + Enterprise</dt>
        <dd class="dd">此捆绑软件包含所有标准防火墙和 UTM 服务，以及以下服务：<ul><li>Cloud Access Security Broker (CASB) - 此服务为基于云的服务提供可视性、合规性、数据安全性和威胁保护。</li><li>Industrial Security - 此服务提供通用 ICS/SCADA 协议的签名。</li><li>Security Rating - 此服务提供审计功能，用于识别关键漏洞和配置弱点，并实施最佳实践建议。</li></ul></dd>
</dl>

在 2018 年第 3 季度，Fortinet 向其企业捆绑软件添加了三个新服务（CASB、Industrial Security 和 Security Rating）。这些服务仅在 FortiGate 6.0 上可用。
{:note}

无法在安装服务后更改许可模型。要更改许可模型，必须除去现有服务，然后通过选择其他许可选项来重新安装该服务。
{:important}

## 相关链接
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet Web 站点](https://www.fortinet.com/){:new_window}
* [Fortinet 文档库](https://docs.fortinet.com/product/fortigate/6.2){:new_window}

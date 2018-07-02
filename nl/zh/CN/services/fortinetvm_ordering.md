---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 订购 FortiGate Virtual Appliance on IBM Cloud

订购 FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

## 为新实例订购 FortiGate Virtual Appliance on IBM Cloud

可以使用下列其中一种方法订购包含 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_full}} 控制台中，订购新实例时，请在**服务**部分中选择 **FortiGate Virtual Appliance on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **FortiGate Virtual Appliance on IBM Cloud 服务**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 FortiGate Virtual Appliance on IBM Cloud

可以使用下列其中一种方法将 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加服务**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **FortiGate Virtual Appliance on IBM Cloud 服务**，指定服务设置，然后选择**添加到现有实例**。

## FortiGate Virtual Appliance on IBM Cloud 服务配置

订购此服务时，请提供以下设置。

### 名称

输入服务名称。

### 部署大小

IBM Cloud 提供以下部署大小选项：
- **小型（2 个 vCPU/ 4 GB RAM）**
- **中型（4 个 vCPU/ 6 GB RAM）**
- **大型（8 个 vCPU/ 12 GB RAM）**

### 许可模型

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的许可模型提供了以下选项：
<dl class="dl">
        <dt class="dt dlterm">标准 FW</dt>
        <dd class="dd">此捆绑软件包含有状态包检查、VLAN 保护和高级日志记录、流入/流出防火墙规则、SSL/IPSec VPN 终止以及全天候支持。</dd>
        <dt class="dt dlterm">标准 FW + UTM</dt>
        <dd class="dd">此捆绑软件除了包含 NGFW IPS 和 Web 过滤、AntiVirus 和 AntiSpam、IP & Domain Reputation 和核心 FortiCare 安全服务之外，还包含所有标准防火墙服务。</dd>
        <dt class="dt dlterm">标准 FW + Enterprise</dt>
        <dd class="dd">此捆绑软件除了包含 FortiSandbox Cloud 和 Mobile Security 外，还包含所有标准防火墙和 UTM 服务。</dd>
</dl>

**重要信息**：无法在安装服务后更改许可模型。要更改许可模型，必须除去现有服务，然后通过选择其他许可选项来重新安装该服务。

## 相关链接

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 概述](fortinetvm_considerations.html)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](managingfortinetvm.html)
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](../vcenter/vc_hybrid_addingremovingservices.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Fortinet Web 站点](https://www.fortinet.com/){:new_window}
* [Fortinet 文档库](http://docs.fortinet.com/fortigate/admin-guides){:new_window}

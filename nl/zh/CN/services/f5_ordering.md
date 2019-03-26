---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购 F5 on IBM Cloud
{: #f5_ordering}

订购 F5 on {{site.data.keyword.cloud}} 服务时，可订购包含此服务的新实例，也可通过向现有实例添加此服务来进行订购。

## 为新实例订购 F5 on IBM Cloud
{: #f5_ordering-new}

可以使用下列其中一种方法订购包含 F5 on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **F5 on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **F5 on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 F5 on IBM Cloud
{: #f5_ordering-existing}

可以使用下列其中一种方法将 F5 on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **F5 on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

## F5 on IBM Cloud 服务配置
{: #f5_ordering-config}

订购此服务时，请提供以下设置。

### F5 许可证激活连接
{: #f5_ordering-config-license}

选择**公用网络**或**专用网络**以激活许可证。如果目标集群配置为仅使用专用网络接口，那么仅**专用网络**选项可用。此选项会确定 F5 虚拟服务器将如何联系 F5 许可证服务器，并且此选项不会影响工作负载数据平面。

如果选择**专用网络**，请指定以下设置：
* **代理 IP 地址**：代理服务器的 IPv4 地址。
* **代理端口号**：代理服务器的端口号，通常为 8080 或 3128。

不支持认证代理。
{:note}

### 名称
{: #f5_ordering-config-name}

输入服务名称。

### 最大带宽
{: #f5_ordering-config-bandwidth}

指定 F5 BIG-IP 设备的最大吞吐量。

### 许可模型
{: #f5_ordering-config-license-model}

F5 on {{site.data.keyword.cloud_notm}} 服务的许可模型提供了以下选项：
<dl class="dl">
        <dt class="dt dlterm">良好</dt>
        <dd class="dd">此选项使用作为完整代理体系结构运行的 BIG-IP Local Traffic Manager™ (LTM) VE，提供智能本地流量管理、完整的 SSL 流量可视性以及分析和运行状况监视，以确保应用程序服务器始终可供用户使用。</dd>
        <dt class="dt dlterm">更佳</dt>
        <dd class="dd">此选项基于**良好**选项的优点而构建，增加了 BIG-IP DNS™、BIG-IP Advanced Firewall Manager™ (AFM) 和 BIG-IP Application Acceleration Manager™ (AAM) 模块。此项提供全球流量管理服务、应用程序性能优化以及高级网络防火墙和分布式拒绝服务 (DDoS) 缓解功能。</dd>
        <dt class="dt dlterm">最佳</dt>
        <dd class="dd">除了具备**良好**和**更佳**选项的优点外，BIG-IP Application Security Manager™ (ASM) 还提供针对 L7 DDoS、Open Web Application Security Project (OWASP) 十大威胁及常见应用程序漏洞的综合应用程序保护。BIG-IP Access Policy Manager™ (APM) 为用户提供对多云环境中任何位置内应用程序的简化的安全访问，包括 SSO (Single Sign-On) 和 MFA（多因子认证）等功能。</dd>
</dl>

无法在安装服务后更改许可模型。要更改许可模型，必须除去现有服务，然后通过选择其他许可模型重新安装该服务。
{:important}

## 相关链接
{: #f5_ordering-releated}

* [F5 on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [管理 F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [F5 部署指南](https://f5.com/solutions/deployment-guides){:new_window}

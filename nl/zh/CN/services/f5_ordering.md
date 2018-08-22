---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 订购 F5 on IBM Cloud

订购 F5 on {{site.data.keyword.cloud}} 服务时，可订购包含 BIG-IP Virtual Edition (VE) 的新实例，也可通过向现有实例添加 BIG-IP VE 来进行订购。

## 为新实例订购 F5 on IBM Cloud

可以使用下列其中一种方法订购包含 F5 on {{site.data.keyword.cloud_notm}} 的新实例：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，订购新实例时，请在**服务**部分中选择 **F5 on IBM Cloud**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **F5 on IBM Cloud**，指定服务设置，然后选择**添加到新实例**。

## 为现有实例订购 F5 on IBM Cloud

可以使用下列其中一种方法将 F5 on {{site.data.keyword.cloud_notm}} 服务添加到现有实例中：
* 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，查看要为其添加服务的实例，单击左侧导航窗格上的**服务**，然后单击**添加**。
* 在 {{site.data.keyword.cloud_notm}}“目录”中，选择 **F5 on IBM Cloud**，指定服务设置，然后选择**添加到现有实例**。

## F5 on IBM Cloud 服务配置

订购此服务时，请提供以下设置。

### 名称

输入服务名称。

### 许可模型

F5 on {{site.data.keyword.cloud_notm}} 服务的许可模型提供了以下选项：
<dl class="dl">
        <dt class="dt dlterm">良好</dt>
        <dd class="dd">此选项利用 BIG-IP Local Traffic Manager™ (LTM) VE 作为完整代理体系结构运行，提供智能本地流量管理、完整的 SSL 流量可视性以及分析和运行状况监视，以确保应用程序服务器始终可供用户使用。</dd>
        <dt class="dt dlterm">更佳</dt>
        <dd class="dd">此选项基于**良好**选项的优点而构建，增加了 BIG-IP DNS™、BIG-IP Advanced Firewall Manager™ (AFM) 和 BIG-IP Application Acceleration Manager™ (AAM) 模块。此项提供全球流量管理服务、应用程序性能优化以及高级网络防火墙和分布式拒绝服务 (DDoS) 缓解功能。</dd>
        <dt class="dt dlterm">最佳</dt>
        <dd class="dd">除了具备**良好**和**更佳**选项的优点外，BIG-IP Application Security Manager™ (ASM) 还提供针对 L7 DDoS、Open Web Application Security Project (OWASP) 十大威胁及常见应用程序漏洞的综合应用程序保护。BIG-IP Access Policy Manager™ (APM) 为用户提供对多云环境中任何位置内应用程序的简化的安全访问，包括 SSO (Single Sign-On) 和 MFA（多因子认证）等功能。</dd>
</dl>

**重要信息**：无法在安装服务后更改许可模型。要更改许可模型，必须除去现有服务，然后使用其他许可模型重新安装该服务。

### 最大带宽

指定 F5 BIG-IP 设备的最大吞吐量。

### 相关链接

* [F5 on {{site.data.keyword.cloud_notm}} 概述](f5_considerations.html)
* [管理 F5 on {{site.data.keyword.cloud_notm}}](managing_f5.html)
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)
* [订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务](../vcenter/vc_hybrid_addingremovingservices.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [F5 部署指南](https://f5.com/solutions/deployment-guides){:new_window}

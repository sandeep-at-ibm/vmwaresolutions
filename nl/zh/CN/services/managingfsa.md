---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# 管理 FortiGate Security Appliance on IBM Cloud

成功安装 FortiGate Security Appliance on {{site.data.keyword.cloud}} 服务后，可以在 FortiGate 控制台中管理和配置 FSA 的防火墙规则。

**重要信息**：必须确保将 FSA 防火墙规则定义为允许通过管理组件（例如，IBM CloudDriver 虚拟机或 Zerto Virtual Manager）启动的出站 HTTPS（TCP 端口 443）通信，以便通过因特网与 {{site.data.keyword.cloud_notm}} 基础架构上的外部管理数据库进行通信。出站 HTTPS（TCP 端口 443）通信从实例中的管理服务 VMware NSX Edge 服务网关 (ESG) 的公共 IP 地址发起。

## 访问 FortiGate 300 系列控制台

要管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务，必须通过下列其中一种方式来访问 FortiGate® 300 系列控制台：
* 使用可在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的凭证，登录到 FortiOS Web Client。
* 使用可在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的凭证，通过 SSH 连接访问该控制台。

有关更多信息，请参阅以下主题：
* [订购、查看和除去 Cloud Foundation 实例的服务](../sddc/sd_addingremovingservices.html)
* [订购、查看和除去 vCenter Server 实例的服务](../vcenter/vc_addingremovingservices.html)

### 相关链接

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 概述](fsa_considerations.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [fortinet.com Web 站点](https://www.fortinet.com/)
* [Fortinet 技术文档](http://docs.fortinet.com/fortigate/admin-guides)

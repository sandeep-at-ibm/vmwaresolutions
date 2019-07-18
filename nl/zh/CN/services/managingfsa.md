---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: FortiGate Security console, FortiGate 300 console, login FortiGate console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 FortiGate Security Appliance on IBM Cloud
{: #managingfsa}

成功安装 FortiGate Security Appliance on {{site.data.keyword.cloud}} 服务后，可以在 FortiGate 控制台中管理和配置 FSA 的防火墙规则。

必须确保将 FSA 防火墙规则定义为允许通过管理组件（例如，Zerto Virtual Manager）启动的出站 HTTPS（TCP 端口 443）通信，以便通过因特网与 {{site.data.keyword.cloud_notm}} 基础架构上的外部管理数据库进行通信。出站 HTTPS（TCP 端口 443）通信从实例中的管理服务 VMware NSX Edge 服务网关 (ESG) 的公共 IP 地址发起。
{:important}

## 访问 FortiGate 300 系列控制台
{: #managingfsa-access-console}

要管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务，必须通过下列其中一种方式来访问 FortiGate® 300 系列控制台：
* 使用可在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的凭证，登录到 FortiOS Web Client。
* 使用可在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务详细信息页面上找到的凭证，通过 SSH 连接访问该控制台。

有关更多信息，请参阅[订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 相关链接
{: #managingfsa-related}

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [fortinet.com Web 站点](https://www.fortinet.com/){:external}
* [Fortinet 文档库](https://docs.fortinet.com/product/fortigate/6.2){:external}

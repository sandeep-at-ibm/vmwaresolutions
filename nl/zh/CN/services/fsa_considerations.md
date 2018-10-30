---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-26"

---

# FortiGate Security Appliance on IBM Cloud 概述

FortiGate Security Appliance on {{site.data.keyword.cloud}} 服务用于以高可用性方式部署 FortiGate Security Appliance (FSA) 300 系列设备对，以提供防火墙、路由、NAT 和 VPN 服务来保护实例公用 VLAN 上的所有服务器和虚拟机。

可以使用 FortiOS Web Client 或通过 SSH 连接的命令行界面来管理此服务。

**可用性**：此服务仅可用于在 V1.8 或更高发行版中部署的实例。

## FortiGate Security Appliance on IBM Cloud 的技术规范

FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务中订购并包含了以下组件：

### 硬件

FortiGate 300 系列 Security Appliance。

### 高可用性

两个设备以主动/被动配置方式进行部署。

### 联网

* 上游和下游网络上均绑定了双 1 GbE
* 一个新的上游 {{site.data.keyword.cloud_notm}} 公用 VLAN
* 一个现有下游 {{site.data.keyword.cloud_notm}} 公用 VLAN

## 安装 FortiGate Security Appliance on IBM Cloud 时的注意事项

安装 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* 确保要使用的 {{site.data.keyword.cloud_notm}} 帐户具有**硬件防火墙**许可权。要编辑或查看实例的 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务的防火墙日志和设置，需要此许可权。
* 如果要将 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务添加到已部署的实例，请确保该实例的公用 VLAN 上尚未部署 {{site.data.keyword.cloud_notm}} 基础架构中的其他任何防火墙。
* 安装 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务将添加新的公用 VLAN。
* 在服务部署期间，实例可能暂时无法访问因特网。
* 成功安装 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务后，可以在 FortiGate 控制台中管理和配置 FSA 的防火墙规则。必须确保将 FSA 防火墙规则定义为允许通过管理组件（例如，Zerto Virtual Manager）启动的出站 HTTPS（TCP 端口 443）通信，以便通过因特网与 {{site.data.keyword.cloud_notm}} 上的外部管理数据库进行通信。出站 HTTPS（TCP 端口 443）通信从实例中的管理服务 VMware NSX Edge 服务网关 (ESG) 的公共 IP 地址发起。
* 您必须谨慎管理 FortiGate Security Appliance 配置，以仅允许必要的通信，而拒绝其他所有通信。
* 如果订购更多集群，那么这些新添加集群的公用 VLAN 不会有 Security Appliance 的 HA 对。

## 除去 FortiGate Security Appliance on IBM Cloud 时的注意事项

除去 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务之前，请查看以下注意事项：
* 除去 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务将除去添加的公用 VLAN。
* 在服务除去期间，实例可能暂时无法访问因特网。
* 将除去允许、检查、阻塞和路由 NAT 流量的所有 FortiGate 规则以及 Fortinet 服务。如果有任何 NAT 规则，那么必须对其进行重新配置。

### 相关链接

* [订购 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [联系 IBM 支持人员](../vmonic/trbl_support.html)
* [常见问题](../vmonic/faq.html)
* [Fortinet Web 站点](https://www.fortinet.com/){:new_window}
* [Fortinet 文档库](http://docs.fortinet.com/fortigate/admin-guides){:new_window}

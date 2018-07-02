---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# 协助故障诊断

## 问题

在某些情况下，可能会发生更复杂的问题，并且日志文件不足以完成根本原因分析并提供解决方案。

## 解决方法

要对此类型问题进行故障诊断并予以解决，{{site.data.keyword.vmwaresolutions_full}} 支持团队需要访问 {{site.data.keyword.cloud_notm}} 管理虚拟机 (VM)。此管理 VM（称为 IBM CloudDriver）是主界面，用于管理部署的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。

出于安全原因，对 IBM CloudDriver 的访问受到限制。{{site.data.keyword.vmwaresolutions_short}} 支持团队将请求客户核准，在获得客户核准后，该团队可以使用 {{site.data.keyword.cloud_notm}} 基础架构虚拟服务器来访问 CloudDriver 组件。此服务器通过 {{site.data.keyword.cloud_notm}} 基础架构前端客户路由器 (FCR) 公用网络桥接到环境中。

接下来，{{site.data.keyword.vmwaresolutions_short}} 支持团队使用为订购和配置实例而提供的 {{site.data.keyword.cloud_notm}} 基础架构 {{site.data.keyword.slapi_short}} 密钥（或者，如果需要，使用客户提供的更新密钥）来部署每小时 {{site.data.keyword.cloud_notm}} 基础架构虚拟服务器。

将根据 IBM CloudBuilder 工具用于故障诊断的使用量来对客户帐户收费。调试和修复完成后，会释放 IBM CloudBuilder 组件。

将使用以下规范来部署用于故障诊断的 {{site.data.keyword.cloud_notm}} 基础架构虚拟服务器：

* CentOS 7 公共节点 VSI（虚拟服务实例）与 1 个 CPU 和 1 GB RAM 配合使用。
* VSI 部署在实例所在的相同主公用和专用 VLAN 上的相同数据中心内。
* 安装后脚本与 VSI 部署配合使用来设置防火墙规则，以仅允许来自 {{site.data.keyword.vmwaresolutions_short}} 支持团队所拥有并使用的特定 IP 地址组的入局 SSH 连接。
* 使用这些 IP 地址的支持启动系统在 {{site.data.keyword.cloud_notm}} 基础架构 VM 上运行，此 VM 只能通过专用 {{site.data.keyword.cloud_notm}} 基础架构网络访问，并且通过 HA（高可用性）{{site.data.keyword.cloud_notm}} 基础架构 Vyatta 系统对确保安全。
* IBM 安全工具（例如，QRadar®、Nessus 和 IBM BigFix®）用于监视支持启动系统中是否有任何安全威胁。

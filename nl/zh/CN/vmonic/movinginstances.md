---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# 从 V1.4 之前的发行版升级实例

## 问题

V1.4 和更高发行版中的实例网络拓扑与低于 V1.4 的发行版中的不同。由于此更改，在 V1.4 之前的发行版中部署的实例不能以其状态在当前发行版中使用。

## 解决方法

在 V1.4 和更高发行版中，有多个网络拓扑增强功能可用于您的实例：
* （应用于所有实例）：优化了联网配置。由于您使用的 {{site.data.keyword.cloud}} 帐户必须是 VRF（虚拟路由和转发）帐户，或者如果是经典（非 VRF）帐户，那么必须启用 VLAN 生成，因此不需要第二个可移植 IP 地址。部署只需要主 {{site.data.keyword.cloud_notm}} 基础架构可移植 IP 地址。
* （仅应用于 Cloud Foundation 实例）：具有 Microsoft Windows AD SSO (Active Directory Single Sign-On) 和域名系统 (DNS) 服务器的多站点部署功能。

如果尚未从 1.4 之前的发行版中迁移或删除实例，那么这些实例可能仍然会以“仅查看”方式在 {{site.data.keyword.vmwaresolutions_short}} 控制台上显示。这些实例在用户界面上标记为**不推荐**，并带有警告符号图标。

**注**：实例属性中显示的信息反映的是截至 V1.4 发行日期的数据，这些数据不会再刷新。

在 V1.4 之前的实例上，以下操作可用：
*  在实例详细信息页面上查看信息。
*  查看实例备份信息。
*  打开 vSphere Web Client 并使用 vCenter 中的实例。
*  通过开具 {{site.data.keyword.cloud_notm}} 支持凭单来请求实例复原。
*  删除实例。

对于 V1.4 之前的实例，其他所有操作都不再可用。

如果您有 V1.4 之前的实例并且计划继续使用这些实例，那么可以通过创建新实例，然后将现有配置移至这些新实例来对其进行升级。

要将 V1.4 之前的实例移至新实例，请在 VMware vSphere Web Client 中完成以下步骤：
1. 从 V1.4 之前的实例，导出所有 VM（虚拟机）。
2. 在当前发行版中创建新实例。
3. 导入从**步骤 1** 中导出的所有 VM。
4. 开始使用新实例。

有关导出和导入 VM 的信息，请参阅 VMware vSphere 文档。

如果您需要有关 {{site.data.keyword.vmwaresolutions_short}} 的帮助，请通过下列其中一种支持渠道[联系 IBM 支持](trbl_support.html)。

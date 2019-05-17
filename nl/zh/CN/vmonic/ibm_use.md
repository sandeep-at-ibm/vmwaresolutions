---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 实例的 IBM 用户标识和部署历史记录消息
{: #ibm_use}

{{site.data.keyword.cloud}} 需要访问您的帐户来实现自动化和操作日志记录。

## 用户标识
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}} 在您的帐户中维护有一组用户，在您执行操作（例如，向 VMware 实例添加主机、集群或存储器）时，{{site.data.keyword.cloud_notm}} 自动化会使用这些用户。请查看有关 {{site.data.keyword.cloud_notm}} 自动化用户标识的以下各部分。

如果删除或禁用了 IBM 用户标识，或者更改了其密码，那么 VMware 实例操作会失败。
{:important}

### vCenter 和 Platform Services Controller 用户标识
{: #ibm_use-user-ids-vcenter-psc}

从 V2.5 开始，{{site.data.keyword.vmwaresolutions_short}} 使用以下用户标识将缺省情况下嵌入的身份源添加到 vCenter 中。

表 1. vCenter 和 Platform Services Controller 用户标识

| User |用户标识|方法|描述|
|:---------|:-------------|:-------|:------------|
|IBM|root|SSH|用于 VMware 配置，例如设置 VMware 高可用性和创建分布式交换机。在部署后用于对主和辅助 vCenter Server 实例进行配对。|
|客户|customerroot|SSH|创建仅供客户使用。|
|IBM|automation@``root_domain``<br/>（Active Directory 用户）|HTTP|在部署后用于添加和除去主机和集群，以及为附加组件服务部署和配置虚拟机。|
|客户|Administrator@vsphere.local|HTTP|创建仅供客户使用。|

HTTP 用于 vCenter 设置和配置以及 VMware 操作（例如，添加主机、集群或存储器以供 vCenter 管理资源）。
{:note}

### NSX Manager 用户标识
{: #ibm_use-user-ids-nsx-mgr}

NSX Manager 用户标识用于为服务添加 ESG 规则。

表 2. NSX Manager 用户标识

| User |用户标识|描述|
|:---------|:-------------|:------------|
|IBM|automation@``root_domain``<br/>（Active Directory 用户）|在部署后用于管理 NSX VTEP IP 地址，在添加和除去主机和集群时管理主机和集群配置，以及管理需要公共网络访问权以进行许可、激活或使用情况报告的附加组件服务的 ESG 配置。|
|客户|管理员|创建仅供客户使用。|

### ESXi 主机用户标识
{: #ibm_use-user-ids-esxi}

ESXi 主机用户标识用于添加存储器，执行修补，配置 vSAN 集群以及运行所有服务器验证代码。

表 3. ESXi 主机用户标识

| User |用户标识|描述|
|:---------|:-------------|:------------|
|IBM|ic4vroot|在部署后用于添加其他 NFS 存储器，并为该存储器配置路径。|
|客户|root|创建仅供客户使用。|

### Microsoft Active Directory 用户标识
{: #ibm_use-user-ids-ad}

Active Directory 用户标识用于设置 DNS 条目。

表 4. Active Directory 用户标识

| User |用户标识|描述|
|:---------|:------------- |:------------|
|IBM|automation|用于添加主机，为服务添加虚拟机以及设置 Active Directory 和 DNS 条目。|
|客户|管理员|创建仅供客户使用。|

## 实例历史记录消息
{: #ibm_use-msgs}

{{site.data.keyword.cloud_notm}} 对 VMware 实例执行的所有操作都会记录在实例历史记录中。可以使用实例历史记录作为参考来复查这些操作。有关查看实例历史记录的更多信息，请参阅[查看 vCenter Server 实例的部署历史记录的过程](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history)。

以下各部分提供了可以发布到实例历史记录的所有可能的消息。

### 常规实例历史记录消息
{: #ibm_use-msgs-general}

{{site.data.keyword.vmwaresolutions_short}} 会对常规操作发出以下消息：

* ``开始创建实例用户和必需的服务...``
* ``实例用户和必需的服务创建完成。``
* ``正在订购 vCenter Server 许可证...``
* ``正在订购 VMware 许可证...``
* ``完成订购 VMware 许可证。``
* ``正在订购 <quantity> 附加费用...``
* ``正在启动 <environment> 安装和配置...``
* ``<environment> 安装和配置完成。``
* ``正在启动 VMware 组件...``
* ``开始部署实例...``
* ``<instance_name> 实例准备就绪，可供使用。``
* ``开始升级到 <version>...``
* ``升级到 <version> 完成。``
* ``VMware 组件升级完成。``
* ``正在启动 <instance_name> 实例删除...``
* ``<instance_name> 实例已成功删除。``
* ``安全擦除实例完成。``
* ``正在取消 vCenter 许可证...``
* ``正在取消实例用户和必需的服务...``
* ``正在取消 <environment> 附加费用...``
* ``正在取消 VMware 许可证...``
* ``VMware 许可证取消完成。``
* ``SoftLayer 订购失败或超时。``

### 集群历史记录消息
{: #ibm_use-msgs-cluster}

{{site.data.keyword.vmwaresolutions_short}} 会对 vCenter Server 集群发出以下消息：

* ``正在启动集群配置...``
* ``正在启动 <cluster_name> 的集群配置...``
* ``集群配置完成。``
* ``<cluster_name> 集群准备就绪，可供使用。``
* ``正在将新集群添加到 vCenter...``
* ``新集群已添加到 vCenter。``
* ``正在对 <cluster_name> 启动集群删除...``
* ``正在从 vCenter 中删除 <cluster_name> 集群...``
* ``<cluster_name> 集群已从 vCenter 中删除。``
* ``<cluster_name> 集群已删除。``

### 虚拟服务器实例历史记录消息
{: #ibm_use-msgs-vsi}

{{site.data.keyword.vmwaresolutions_short}} 会对虚拟服务器实例 (VSI) 发出以下消息：

* ``正在订购 IBM CloudDriver 的新虚拟服务器实例...``
* ``<ip_address> IBM CloudDriver 虚拟服务器实例已供应。``
* ``正在取消 <ip_address> IBM CloudDriver 虚拟服务器实例...``
* ``开始订购用于 Microsoft Active Directory/DNS 的 Microsoft Windows 虚拟服务器实例...``
* ``正在验证用于 Active Directory/DNS 的 Microsoft Windows 虚拟服务器实例订单...``
* ``用于 Active Directory/DNS 的 Microsoft Windows 虚拟服务器实例准备就绪。``
* ``正在取消虚拟服务器实例...``
* ``正在取消关联的虚拟服务器实例...``
* ``虚拟服务器实例取消完成。``

### IBM CloudDriver 历史记录消息
{: #ibm_use-msgs-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} 会对 IBM CloudDriver 发出以下消息：

* ``正在准备 IBM CloudDriver...``
* ``IBM CloudDriver 准备就绪。``
* ``<ip_address> IBM CloudDriver 准备就绪，可供使用。``
* ``正在检查 IBM CloudDriver 状态...``
* ``正在复用现有 <ip_address> IBM CloudDriver...``
* ``正在复用现有 IBM CloudDriver（正在供应）...``
* ``正在发布 IBM CloudDriver...``
* ``正在发布 <ip_address> IBM CloudDriver...``
* ``正在启动 IBM CloudDriver 删除...``
* ``完成 IBM CloudDriver 删除。``

### ESXi 服务器历史记录消息
{: #ibm_use-msgs-esxi}

{{site.data.keyword.vmwaresolutions_short}} 会对 ESXi 服务器发出以下消息：

* ``开始订购 <quantity> 个 ESXi 服务器...``
* ``正在验证 ESXi 服务器订单...``
* ``具有 <ip_addresses> 专用 IP 地址的 ESXi 服务器准备就绪。``
* ``所有 ESXi 服务器均已回收。``
* ``正在将 ESXi 服务器添加到 vCenter Server 实例...``
* ``ESXi 服务器已成功更新。``
* ``开始订购集群的 ESXi 服务器...``
* ``开始为 <Cluster Name> 集群订购 <quantity> 个 ESXi 服务器...``
* ``该集群的 ESXi 服务器准备就绪。``
* ``具有 <ip_addresses> 专用 IP 地址的 ESXi 服务器准备就绪，可供集群使用。``
* ``ESXi 服务器准备就绪。``
* ``ESXi 服务器配置完成。``
* ``ESXi 服务器已通过该属性成功添加。``
* ``所有用于添加 ESXi 服务器的请求均成功完成。``
* ``正在添加 ESXi 服务器...``
* ``正在为 ESXi 服务器订购裸机服务器...``
* ``新 ESXi 服务器已添加到 vCenter。``
* ``开始向新 ESXi 服务器添加服务...``
* ``所选 ESXi 服务器已成功取消。``
* ``新 ESXi 服务器已供应。``
* ``新 ESXi 服务器已通过验证并准备就绪。``
* ``开始为 <cluster_name> 集群订购 <quantity> 个新 ESXi 服务器...``
* ``所选 ESXi 服务器已成功从 vCenter Server 中除去。``
* ``开始除去服务以除去 ESXi 服务器...``
* ``正在验证 <cluster_name> 集群的 ESXi 服务器...``
* ``新的集群 ESXi 服务器已成功通过验证。``
* ``正在验证新 ESXi 服务器订单...``
* ``验证 ESXi 服务器订单失败。``
* ``正在拆分批量添加 ESXi 服务器请求。``
* ``成功完成除去 ESXi 服务器的所有请求。``
* ``主机已成功添加。``
* ``主机已成功除去。``
* ``正在取消裸机服务器...``
* ``裸机服务器取消完成。``
* ``正在从 vCenter Server 实例中除去 ESXi 服务器...``
* ``正在除去 ESXi 服务器。``
* ``正在除去 <server_id> ESXi 服务器。``
* ``正在从 vCenter Server 中除去所选 ESXi 服务器...``
* ``正在取消 ESXi 服务器...``
* ``正在取消所选 ESXi 服务器...``

### IBM CloudBuilder 历史记录消息
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} 会对 IBM CloudBuilder 发出以下消息：

* ``正在验证 IBM CloudBuilder 虚拟服务器实例订单...``
* ``开始订购 IBM CloudBuilder 虚拟服务器实例...``
* ``IBM CloudBuilder 虚拟服务器实例准备就绪。``
* ``IBM CloudBuilder 准备就绪，可用于服务。``
* ``正在关闭 IBM CloudBuilder 虚拟服务器实例...``

### 存储器历史记录消息
{: #ibm_use-msgs-storage}

{{site.data.keyword.vmwaresolutions_short}} 会对存储器设置发出以下消息：

* ``正在订购 vSAN 许可证...``
* ``正在取消 vSAN 许可证...``
* ``vSAN 许可证取消完成。``
* ``正在为 <cluster_name> 集群订购 <quantity> 个 NFS 存储器。``
* ``新 NFS 存储器已添加，并准备就绪可供使用。``
* ``正在取消管理 NFS 共享存储器...``
* ``所选 NFS 存储器已删除。``
* ``开始订购耐久性存储器...``
* ``正在取消耐久性存储器...``

### 网络历史记录消息
{: #ibm_use-msgs-network}

{{site.data.keyword.vmwaresolutions_short}} 会对网络设置发出以下消息：

* ``开始订购公用 VLAN...``
* ``成功完成 VLAN 配置。``
* ``正在订购其他专用 VLAN...``
* ``额外专用 VLAN 已供应。``
* ``额外专用 VLAN 虚拟服务器实例已供应。``
* ``正在将额外专用 VLAN 中继到裸机服务器...``
* ``已成功将额外专用 VLAN 中继到裸机服务器。``
* ``正在取消额外专用 VLAN 虚拟服务器实例...``
* ``正在取消 VLAN...``
* ``正在取消 VLAN...``
* ``VLAN 取消完成。`
* ``正在订购双套接字 <type> NSX 许可证...``
* ``新集群的 NSX 配置完成。``
* ``正在取消双套接字 NSX 许可证...``
* ``NSX 许可证已成功取消。``
* ``开始订购子网...``
* ``子网准备就绪。``
* ``可移植专用子网准备就绪。``
* ``正在授予新子网对 NFS 存储器的访问权...``
* ``正在取消子网...``
* ``正在取消子网...``
* ``正在取消客户可移植专用子网...``
* ``正在取消客户可移植公用子网...``
* ``正在取消耐久性存储器专用子网...``
* ``正在取消可移植公用子网...``
* ``可移植公用子网准备就绪。``
* ``开始订购可移植公用子网...``
* ``子网取消完成。``
* ``正在取消网络存储器...``

### 服务历史记录消息
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}} 会对服务发出以下消息：

* ``正在启动管理服务设置...``
* ``正在订购服务项...``
* ``完成订购服务项。``
* ``IBM 操作服务正在运行。``
* ``正在启用缺省服务...``
* ``缺省服务已成功启用。``
* ``正在取消服务项...``
* ``服务项取消完成。``

### vCenter Server with Hybridity Bundle 历史记录消息
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}} 会对 vCenter Server with Hybridity Bundle 实例发出以下消息：

* ``正在订购 vCenter Server with Hybridity Bundle 许可证...``
* ``正在启动 vCenter Server with Hybridity Bundle 转换...``
* ``vCenter Server with Hybridity Bundle 转换完成。``
* ``正在除去 vCenter Server with Hybridity Bundle...``
* ``vCenter Server with Hybridity Bundle 已成功除去。``
* ``正在取消 vCenter Server with Hybridity Bundle 转换...``

### Cloud Foundation 历史记录消息
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}} 会对 Cloud Foundation 实例发出以下消息：

* ``开始订购 Cloud Foundation 实例...``
* ``已收到 Cloud Foundation 订单。``
* ``正在处理 Cloud Foundation 订单...``
* ``正在订购要用于 Cloud Foundation 配置的虚拟服务器...``
* ``完成订购要用于 Cloud Foundation 配置的虚拟服务器。``
* ``已验证要用于 Cloud Foundation 配置的虚拟服务器的订单。``
* ``正在订购要用于 Cloud Foundation 配置的裸机服务器...``
* ``完成订购要用于 Cloud Foundation 配置的裸机服务器。``
* ``正在配置 Cloud Foundation 联网...``
* ``完成配置 Cloud Foundation 联网。``
* ``正在订购 Cloud Foundation 子网...``
* ``完成订购 Cloud Foundation 子网``
* ``正在配置 Cloud Foundation 实例...``
* ``正在定制和优化 Cloud Foundation 实例组件...``
* ``正在清除 Cloud Foundation...``
* ``Cloud Foundation 清除完成。``
* ``Cloud Foundation 实例准备就绪，可供使用。``
* ``正在定制和优化 Cloud Foundation 实例...``
* ``Cloud Foundation 实例配置完成。``
* ``定制和优化 Cloud Foundation 实例完成。``
* ``Cloud Foundation 组件订购完成。``
* ``Cloud Foundation 实例删除完成。``
* ``删除 Cloud Foundation 实例完成。``

### 错误消息
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}} 会发出以下实例历史记录错误消息：

* ``订购用于 Cloud Foundation 配置的虚拟服务器时出错。请开具服务凭单以获取帮助。``
* ``错误：SoftLayer 未能供应要用于 Cloud Foundation 配置的虚拟服务器。请开具服务凭单以获取帮助。``
* ``订购用于 Cloud Foundation 配置的裸机服务器时出错。请开具服务凭单以获取帮助。``
* ``订购要用于 Cloud Foundation 配置的 VLAN 时出错。请开具服务凭单以获取帮助。``
* ``配置 Cloud Foundation 联网时出错。请开具服务凭单以获取帮助。``
* ``订购 Cloud Foundation 子网时出错。请开具服务凭单以获取帮助。``
* ``为 Cloud Foundation 实例创建管理服务时出错。请开具服务凭单以获取帮助。``
* ``订购 VMware 许可证时出错。请开具服务凭单以获取帮助。``
* ``订购子网时出错。请开具服务凭单以获取帮助。``
* ``配置 Cloud Foundation 实例时出错。请开具服务凭单以获取帮助。``
* ``定制和优化 Cloud Foundation 实例时出错。请开具服务凭单以获取帮助。``
* ``错误：SoftLayer API 密钥无效。请开具服务凭单以获取帮助。``
* ``错误：SoftLayer 数据中心无效。请开具服务凭单以获取帮助。``
* ``在提供的 SoftLayer 帐户中使用共享映像时出错。请开具服务凭单以获取帮助。``
* ``订购服务项时出错。请开具服务凭单以获取帮助。``
* ``订购子网时出错。请开具服务凭单以获取帮助。``
* ``订购许可证时出错。请开具服务凭单以获取帮助。``
* ``订购服务时出错。请开具服务凭单以获取帮助。``


## 相关链接
{: #ibm_use-related}

* [关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

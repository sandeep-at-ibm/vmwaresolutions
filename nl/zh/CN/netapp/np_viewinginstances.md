---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 查看 NetApp ONTAP Select 实例
{: #np_viewinginstances}

查看针对不同用户帐户供应的 NetApp ONTAP Select 实例的摘要和详细信息。

## 查看 NetApp ONTAP Select 实例摘要的过程
{: #np_viewinginstances-procedure-view-inst-summary}

要查看针对用户帐户供应的所有 NetApp ONTAP Select 实例的摘要，请完成以下步骤：

1. 在 {{site.data.keyword.vmwaresolutions_full}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在控制台条幅中，单击您的用户帐户图标，然后单击**帐户**字段以选择要检查其实例的用户帐户。
3. 在 **NetApp ONTAP Select 实例**表中，查看所选用户帐户中供应的实例的列表。

表 1. NetApp ONTAP Select 实例项

|项|描述|  
|:------------- |:--------------- |
|名称|实例的名称。|
|版本|实例的版本。|  
|位置|托管实例的数据中心。|
|创建时间|创建实例的日期和时间。|   
|状态|实例的状态。状态可以是下列其中一个值：
    <ul><li>正在创建：正在创建实例。</li><li>正在构建：正在配置实例。</li><li>可供使用：实例准备就绪，可供使用。</li><li>正在修改：正在修改实例。</li><li>失败：创建、配置或修改过程失败。</li><li>正在删除：正在删除实例。</li><li>删除错误：删除实例时发生错误。</li><li>已删除：实例已删除。</li></ul>|

## 查看 NetApp ONTAP Select 实例属性详细信息的过程
{: #np_viewinginstances-procedure-view-inst-property}

要查看实例的属性详细信息，请执行以下操作：

1. 在 **NetApp ONTAP Select 实例**表中，单击实例名称。
2. 在**属性**下，查看实例的详细信息。

表 2. NetApp ONTAP Select 实例属性

|属性|描述|
|:--------------- |:----------------- |
|名称|实例的名称。|
|标识|实例的标识。|
|位置|托管实例的数据中心。|
|部署的版本|部署的 {{site.data.keyword.vmwaresolutions_short}} 版本。|
|vCenter 版本|VMware vCenter Server 的版本。<br><br>**注**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台与 VMware vSphere Web Client 上显示的 vCenter Server 版本之间略有差异。但这两个版本都是正确的。|
|NSX for vSphere|VMware NSX for vSphere 产品版本。|
|NSX 许可证版本|VMware NSX 许可证的版本和修订版。|
|NetApp 版本|NetApp ONTAP Select 的版本。|
|NetApp 许可证类型|NetApp ONTAP Select 许可证的类型。|
|DNS - 根域|根域名是实例的 DNS（域名系统）域名和 Microsoft Active Directory (AD) 林根名称。|
|DNS - SSO 域|SSO 域是 vSphere Single Sign-On 域。SSO 域名针对所有部署的 NetApp ONTAP Select 实例设置为值 `vsphere.local`。|
|DNS - 子域|子域是本地 NetApp ONTAP Select 实例主机名所在的根域名的 DNS 子域名。子域名的格式为 `<subdomain_label>.<root_domain>`。|
|状态|实例的状态。|

## 查看 NetApp ONTAP Select 实例的访问信息的过程
{: #np_viewinginstances-procedure-view-inst-access-info}

在**访问信息**下，查看与实例相关的组件的访问信息。这些密码是系统生成的初始密码。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部对这些信息进行更改，那么不会在实例摘要页面上更新这些信息。

表 3. 与 NetApp ONTAP Select 实例相关的组件的访问信息

|组件|描述|
|:---------------- |:----------------- |
|AD/DNS IP|两个 AD 服务器的 IP 地址。|
|AD/DNS FQDN|AD/DNS 服务器标准域名。|
|AD/DNS ADMIN（远程桌面）|可用于通过远程桌面连接访问 AD 服务器的用户名和密码。|
|NSX Manager IP|NSX Manager 的 IP 地址。|
|NSX Manager FQDN|NSX Manager 标准域名。|
|NSX Manager HTTP|可用于访问 NSX Manager Web 控制台的用户名和密码。|
|NetApp Cluster IP|NetApp ONTAP Select 集群的 IP 地址。|
|NetApp Cluster FQDN|NetApp ONTAP 集群标准域名。|
|NetApp Cluster HTTPS|可用于访问 NetApp ONTAP Select 集群的用户名和密码。|
|NetApp Deploy Tool IP|NetApp ONTAP Select Deploy 虚拟机的 IP 地址。|
|NetApp Deploy Tool FQDN|NetApp ONTAP Select Deploy 标准域名。|
|NetApp Deploy Tool HTTPS|可用于访问 NetApp ONTAP Select Deploy 虚拟机的用户名和密码。|
|vCenter IP|vCenter Server 的 IP 地址。|
|vCenter FQDN|vCenter Server 标准域名。|
|vCenter ADMIN|可用于通过 vSphere Web Client 登录到 vCenter Server 的 VMware vCenter Single Sign-On 用户名和密码。|
|vCenter SSH|可用于通过 SSH 连接访问 vCenter Server VM 的用户名和密码。|

## 查看 NetApp ONTAP Select 实例的部署历史记录的过程
{: #np_viewinginstances-procedure-view-inst-deploy-history}

单击左侧导航窗格中的**部署历史记录**，以查看实例的部署历史记录。

表 4. NetApp ONTAP Select 实例部署历史记录

|项|描述|  
|:------------|:------------- |
|日期|更改实例状态的日期和时间|
|摘要|更改的详细信息|

如果在实例部署或实例删除期间发生错误，就会自动通知 {{site.data.keyword.cloud_notm}} 支持团队。要查询凭单的状态，您可以[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。

## 查看 NetApp ONTAP Select 集群的过程
{: #np_viewinginstances-procedure-view-cluster}

1. 单击左侧导航窗格中的**基础架构**。
2. 在**集群**下，查看有关 NetApp ONTAP Select 集群的摘要。

	表 5. NetApp ONTAP Select 集群项

	 <table>
	   <tr>
	     <th>项</th>
	     <th>描述</th>
	   </tr>
	   <tr>
	     <td>名称</td>
	     <td>集群的名称。</td>
	   </tr>
	   <tr>
	     <td>ESXi 服务器</td>
	     <td>集群中的 ESXi 服务器数。</td>
	   </tr>
	   <tr>
	      <td>CPU</td>
	      <td>集群中 ESXi 服务器的 CPU 规范。</td>
	   </tr>
	   <tr>
	      <td>有效存储</td>
	      <td>集群中 ESXi 服务器的总磁盘容量。</td>
	   </tr>
	   <tr>
	      <td>内存</td>
	      <td>集群中 ESXi 服务器的内存总大小。</td>
	   </tr>
	   <tr>
	      <td>数据中心位置</td>
	      <td>托管集群的数据中心。与实例的数据中心位置相同。</td>
	   </tr>
		 <tr>
		   <td>pod</td>
			 <td>在其中创建集群的 pod。</td>
		 </tr>
		 <tr>
		  <td>状态</td>
			<td>集群的状态。状态可以是下列其中一个值：
    <ul><li>正在初始化：正在创建并配置集群。</li><li>正在修改：正在修改集群。</li><li>可供使用：集群准备就绪，可供使用。</li></ul></td>
		 </tr>
		 <tr>
		  <td>操作</td>
			<td>单击**删除**图标以删除集群。</td>
		 </tr>
	 </table>

3. 单击集群名称以查看其 ESXi 服务器详细信息。

表 6. NetApp ONTAP Select 集群的 ESXi 服务器详细信息

|项|描述|  
|:------------|:----------------- |
|名称|ESXi 服务器名称的格式为 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：<br><br>`host_prefix` 是主机名前缀，`n` 是服务器的序列，`subdomain_label` 是子域标签，`root_domain` 是根域名。|
|版本|ESXi 服务器的版本。|
|凭证|用于访问 ESXi 服务器的用户名和密码。|
|专用 IP|ESXi 服务器的专用 IP 地址。|
|状态|ESXi 服务器的状态，可以是下列某个值：<ul><li>活动：ESXi 服务器准备就绪，可供使用。</li><li>正在删除：正在删除 ESXi 服务器。</li></ul> |

## 后续步骤
{: #np_viewinginstances-next}

通过 {{site.data.keyword.vmwaresolutions_short}} 控制台、VMware vSphere Web Client 或 NetApp 控制台来管理实例。

在实例摘要页面上单击 **vCenter 控制台**以转至 vSphere Web Client 并开始管理 ESXi 服务器之前，必须先登录到 {{site.data.keyword.CloudDataCent_notm}} 的 VPN 门户网站。请将鼠标悬停在 **vCenter 控制台**按钮上，并遵循指示信息以确保在访问 vSphere Web Client 之前满足所有需求并完成了必需的步骤。
{:important}

有关帮助您完成登录的指示信息的更多信息，请查看以下主题：

*  有关访问 vSphere Web Client 之前的需求和必需步骤，请参阅[连接到 vSphere Web Client 时发生超时](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console)。
*  有关使用 VPN 登录到 {{site.data.keyword.cloud_notm}} 基础架构专用网络的访问点的列表，请参阅 [VPN 访问](http://www.softlayer.com/vpn-access){:new_window}。
*  如果使用 vSphere Web Client 部署 OVF（开放式虚拟化格式）文件时发生问题，请参阅[使用 vSphere Web Client 部署 OVF 文件](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_deploy_ovf)。

## 相关链接
{: #np_viewinginstances-related}

* [订购 NetApp ONTAP Select 实例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)
* [删除 NetApp ONTAP Select 实例](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_deletinginstance)
* [将专用存储器连接到 NetApp ONTAP Select 部署](https://developer.ibm.com/recipes/tutorials/steps-to-attach-dedicated-storage-to-existing-ic4v-deployments-on-ibm-cloud/)

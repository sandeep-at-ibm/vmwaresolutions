---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

# 查看 VMware Federal 实例

查看针对不同用户帐户供应的 VMware Federal 实例的摘要和详细信息。

## 查看 VMware Federal 实例摘要

要查看针对用户帐户供应的所有 VMware Federal 实例的摘要，请完成以下步骤：
1. 在 {{site.data.keyword.vmwaresolutions_full}} 控制台中，单击左侧导航窗格中的**部署的实例**。
2. 在控制台的右上角，单击您的头像，然后单击**帐户**字段以选择要检查其实例的用户帐户。 
3. 在 **vCenter Server** 表中，查看所选用户帐户中供应的实例的列表。

表 1. VMware Federal 实例项

|项|描述|  
|:------------- |:------------- |
|名称|实例的名称。|
|版本|实例部署或升级到的发行版版本。|  
|位置|托管实例的 {{site.data.keyword.CloudDataCent_notm}}。|  
|创建时间|创建实例的日期和时间。| 
|状态|实例的状态。|

实例可以有一系列状态。

表 2. VMware Federal 数据中心实例状态描述

|状态|描述|
|:------------- |:------------- |
|正在创建|正在创建实例。|
|正在构建|正在配置实例。|
|可供使用|实例准备就绪，可供使用。|
|正在修改|正在修改实例。|
|已保护|部署的实例已与打开的管理连接和自动化断开连接。
|失败|创建、配置或修改过程失败。|
|正在删除|正在删除实例。|
|删除错误|删除实例时发生错误。|
|已删除|实例已删除。|

## 查看 VMware Federal 实例属性详细信息

要查看实例的属性详细信息，请执行以下操作：

1. 在 **vCenter Server 实例**表中，单击实例名称。
2. 在**属性**下，查看实例的详细信息。

表 3. VMware Federal 实例属性

|属性|描述|
|:------------- |:------------- |
|名称|实例的名称。|
|标识|实例的标识。|
|位置|托管实例的 {{site.data.keyword.CloudDataCent_notm}}。|
|当前版本|{{site.data.keyword.vmwaresolutions_short}} 的当前版本。|
|vCenter 版本|VMware vCenter Server 的版本。<br><br>**注**：在 {{site.data.keyword.vmwaresolutions_short}} 控制台与 VMware vSphere Web Client 上显示的 vCenter Server 版本之间略有差异。但这两个版本都是正确的。|
|NSX for vSphere|VMware NSX for vSphere 产品版本。|
|NSX 许可证版本|VMware NSX 许可证的版本和修订版。|
|DNS 根域|根域名是 DNS（域名系统）域名和 Microsoft Active Directory (AD) 林根名称。|
|DNC SSO 域|SSO 域是 vSphere Single Sign-On 域。SSO 域名针对所有部署的 vCenter Server 实例是固定的，值为 <samp class="ph codeph">vsphere.local</samp>。|
|DNS 子域|子域是本地 vCenter Server 实例主机名所在的根域名的 DNS 子域名。子域名的格式为 <samp class="ph codeph"><var class="keyword varname">vcenter_server_instance_name</var>.<var class="keyword varname">root.domain_name</var></samp>。|
|状态|实例的状态。|

## 查看 VMware Federal 实例的访问信息

在**访问信息**下，查看与实例相关的组件的访问信息。显示的密码是系统生成的初始密码。如果在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部对这些信息进行更改，那么不会在实例摘要页面上更新这些信息。

表 4. 与实例相关的组件的访问信息

|组件|描述|
|:------------- |:------------- |
|AD/DNS IP|两个 AD 服务器的 IP 地址。|
|AD/DNS FQDN|AD/DNS 服务器标准域名。<br><br>**注**：可使用相同的管理员密码通过远程桌面连接到所有 AD/DNS 服务器。|
|AD/DNS ADMIN（远程桌面）|对于主实例，会显示用于通过远程桌面连接访问 AD 服务器的用户名和密码。|NSX Manager IP|NSX Manager 的 IP 地址。|
|NSX Manager FQDN|NSX Manager 标准域名 (FQDN)。|
|NSX Manager HTTP|用于访问 NSX Manager Web 控制台的用户名和密码。|
|PSC IP|Platform Services Controller (PSC) 的 IP 地址。|
|PSC FQDN|PSC 标准域名 (FQDN)。|    
|PSC ADMIN|可用于访问 PSC Web 控制台的 VMware vCenter Single Sign-On 用户名和密码。|
|PSC SSH|可用于通过 SSH 连接访问 PSC VM 的用户名和密码。|
|vCenter IP|vCenter Server 的 IP 地址。|
|vCenter FQDN|vCenter Server 标准域名 (FQDN)。|
|vCenter ADMIN|可用于通过 vSphere Web Client 登录到 vCenter Server 的 VMware vCenter Single Sign-On 用户名和密码。|
|vCenter SSH|可用于通过 SSH 连接访问 vCenter Server VM 的用户名和密码。|

## 查看 VMware Federal 实例的部署历史记录

单击左侧导航窗格中的**部署历史记录**，以查看实例的部署历史记录。

表 5. VMware Federal 实例部署历史记录

|项|描述|  
|:------------- |:------------- |
|日期|更改实例状态的日期和时间。|
|摘要|更改的详细信息。|

## 发生错误时要执行的操作

如果在实例部署或实例删除期间发生错误，就会自动通知 {{site.data.keyword.cloud_notm}} 支持团队。要查询凭单的状态，您可以[联系 IBM 支持](../vmonic/trbl_support.html)。

## 后续步骤

通过 {{site.data.keyword.vmwaresolutions_short}} 控制台或 VMware vSphere Web Client 来管理实例。

**重要信息**：在实例摘要页面上单击 **vCenter 控制台**以转至 vSphere Web Client 并开始管理 ESXi 服务器之前，必须先登录到 {{site.data.keyword.CloudDataCent_notm}} 的 VPN 门户网站。请将鼠标悬停在 **vCenter 控制台**按钮上，并遵循指示信息以确保在访问 vSphere Web Client 之前满足所有需求并完成了必需的步骤。

查看以下主题，以获取有关帮助您完成登录指示信息的信息：
*  有关访问 vSphere Web Client 之前的需求和必需步骤，请参阅[连接到 vSphere Web Client 时发生超时](../vmonic/trbl_timeout_vc_console.html)。
*  有关使用 VPN 登录到 {{site.data.keyword.cloud_notm}} 基础架构专用网络的访问点的列表，请参阅 [VPN 访问](http://www.softlayer.com/vpn-access){:new_window}。
*  如果使用 vSphere Web Client 部署 OVF（开放式虚拟化格式）文件时发生问题，请参阅[使用 vSphere Web Client 部署 OVF 文件](../vmonic/trbl_deploy_ovf.html)。

### 相关链接

* [VMware Federal on {{site.data.keyword.cloud_notm}} 概述](vc_fed_overview.html)
* [订购 VMware Federal 实例](vc_fed_orderinginstance.html)
* [删除 VMware Federal 实例](vc_fed_deletinginstance.html)
* [联系 IBM 支持](../vmonic/trbl_support.html)

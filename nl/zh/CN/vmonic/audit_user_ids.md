---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: user IDs vCenter, PSC user, user ID service

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM 用户标识
{: #audit_user_ids}

{{site.data.keyword.vmwaresolutions_short}} 在您的帐户中维护有一组用户，在您执行操作（例如，向 VMware 实例添加主机、集群或存储器）时，{{site.data.keyword.cloud_notm}} 自动化会使用这些用户。您帐户中的用户还可以用于通过 {{site.data.keyword.cloud_notm}} 服务自动化来安装和配置服务。请查看有关 {{site.data.keyword.cloud_notm}} 自动化用户标识的以下各部分。

如果删除或禁用了 IBM 用户标识，或者更改了其密码，那么 VMware 实例操作会失败。
{:important}

## vCenter 和 Platform Services Controller 用户标识
{: #audit_user_ids-vcenter-psc}

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

## NSX Manager 用户标识
{: #audit_user_ids-nsx-mgr}

表 2. NSX Manager 用户标识

| User |用户标识|描述|
|:---------|:-------------|:------------|
|IBM|automation@``root_domain``<br/>（Active Directory 用户）|在部署后用于管理 NSX VTEP IP 地址，在添加和除去主机和集群时管理主机和集群配置，以及管理需要公共网络访问权以进行许可、激活或使用情况报告的附加组件服务的 ESG 配置。|
|客户|管理员|创建仅供客户使用。|

## ESXi 主机用户标识
{: #audit_user_ids-esxi}

表 3. ESXi 主机用户标识

| User |用户标识|描述|
|:---------|:-------------|:------------|
|IBM|ic4vroot|在部署后用于添加其他 NFS 存储器，为该存储器配置路径并运行所有服务器验证代码。|
|客户|root|创建仅供客户使用。|

## Microsoft Active Directory 用户标识
{: #audit_user_ids-ad}

表 4. Active Directory 用户标识

| User |用户标识|描述|
|:---------|:------------- |:------------|
|IBM|automation|用于添加主机，为服务添加虚拟机以及设置 Active Directory 和 DNS 条目。|
|客户|管理员|创建仅供客户使用。|

## 服务用户标识
{: #audit_user_ids-services}

表 5. 服务用户标识

|用户标识|描述|
|:-------------------------------------------|:----------- |
| prod-BigIP-``dynamic_ID``-@``domain name`` | 用于安装和配置 F5 on {{site.data.keyword.cloud_notm}} 服务。|
| prod-Caveonix-``dynamic_ID``-@``domain name`` | 用于安装和配置 Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 服务。|
| prod-Fortigate-``dynamic_ID``-@``domain name`` | 用于安装和配置 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服务。|
| prod-FortigateVM-``dynamic_ID``-@``domain name`` | 用于安装和配置 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务。|
| prod-HyTrustCC-``5_letter_ID``-@``domain name`` | 用于安装和配置 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服务。|
| prod-HyTrustDC-``5_letter_ID``-@``domain name`` | 用于安装和配置 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服务。|
| prod-HyTrustKC-``5_letter_ID``-@``domain name`` | 用于安装和配置 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 服务。|
| prod-KMIPAdapter-``dynamic_ID``-@``domain name`` | 用于安装和配置 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务。|
| prod-ICP-``dynamic_ID``-@``domain name`` | 用于安装和配置 {{site.data.keyword.cloud_notm}} Private Hosted 服务。|
| prod-SPPlus-``dynamic_ID``-@``domain name`` | 用于安装和配置 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服务。|
| prod-Veeam-``dynamic_ID``-@``domain name`` | 用于安装和配置 Veeam on {{site.data.keyword.cloud_notm}} 服务。|
| prod-HCX-``dynamic_ID``-@``domain name`` | 用于安装和配置 VMware HCX on {{site.data.keyword.cloud_notm}} 服务。|
| prod-Zerto-``dynamic_ID``-@``domain name`` | 用于安装和配置 Zerto on {{site.data.keyword.cloud_notm}} 服务。|

动态标识的长度为 8 到 10 个字母。
{:note}

## 相关链接
{: #audit_user_ids-related}

* [关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker 事件](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

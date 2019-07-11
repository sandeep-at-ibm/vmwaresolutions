---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: SPP management console, apply SPP updates, login SPP console

subcollection: vmware-solutions


---

# 管理 IBM Spectrum Protect Plus on IBM Cloud
{: #managingspp}

## 访问 IBM Spectrum Protect Plus 管理控制台
{: #managingspp-console}

要管理 {{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 服务，必须通过完成以下步骤来访问 IBM Spectrum Protect Plus 管理控制台：
1. 使用 {{site.data.keyword.cloud_notm}} 基础架构 VPN 或跳板机来允许访问 IBM Spectrum Protect Plus 虚拟机 (VM) 的 IP 地址。可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台上 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的服务详细信息页面中找到该 IP 地址。
2. 要访问 IBM Spectrum Protect Plus 管理控制台，请单击 IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} 的服务详细信息页面上的**查看 IBM Spectrum Protect Plus 控制台**，然后使用此服务详细信息页面上列出的凭证进行登录。

## 对 IBM Spectrum Protect Plus on IBM Cloud 应用更新
{: #managingspp-updates}

您应负责维护 IBM Spectrum Protect Plus，以使其保持为最新版本。可以从 [IBM Spectrum Protect Plus 支持](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus){:new_window}页面下载所需的更新。

有关更多信息，请参阅[订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 更新 IBM Spectrum Protect Plus VM 的操作系统
{: #managingspp-update-os}

要更新 IBM Spectrum Protect Plus VM 的操作系统，您必须以 **root** 用户的身份登录。**root** 用户密码与 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的服务详细信息页面中的密码相同。

## 相关链接
{: #managingspp-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations){:new_window}
* [如何向部署后的 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 添加 vSnap 存储](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/){:new_window}
* [How to configure IBM Spectrum Protect Plus to offload to IBM Cloud Object Storage](https://developer.ibm.com/recipes/tutorials/how-to-configure-ibm-spectrum-protect-plus-to-offload-to-ibm-cloud-object-storage/){:new_window}
* [IBM Spectrum Protect Plus 文档](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:new_window}

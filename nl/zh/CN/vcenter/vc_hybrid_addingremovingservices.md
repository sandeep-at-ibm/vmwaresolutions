---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-10"

keywords: vCenter Server Hybridity add service, view service vCenter Server Hybridity, remove service vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 订购、查看和除去 vCenter Server with Hybridity Bundle 实例的服务
{: #vc_hybrid_addingremovingservices}

可以为 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 实例订购服务，例如灾难恢复解决方案。不再需要这些服务时，可以将其从实例中除去。

## vCenter Server with Hybridity Bundle 实例的可用服务
{: #vc_hybrid_addingremovingservices-available-services}

下面是可用于 vCenter Server with Hybridity Bundle 实例的服务以及已安装服务的版本。

表 1. 可用于 vCenter Server with Hybridity Bundle 实例的服务

|服务名称|当前服务版本|实例版本|
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2 | V2.9 和更高版本|
|[F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)| BIG-IP VE v14.1.0.2 | V1.9 和更高版本 |
|[FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)|300 系列| V1.8 和更高版本 |
|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)|6.0.3| V2.0 和更高版本 |
|[HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)| 5.5.1 | V2.3 和更高版本 |
|[HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)| 4.3.2 | V2.3 和更高版本 |
|[HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)| 4.3.2 |V2.5 和更高版本|
|[{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)|3.1.2|V2.7 和更高版本|
|[IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)|10.1.3| V2.2 和更高版本 |
|[KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)|2.0|不适用|
|[Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)| 9.5u4 | V1.8 和更高版本 |
|[VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)|3.5.1| V2.3 和更高版本 |
|[Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)| 6.5 update 3 | V1.2 和更高版本 |

## 向 vCenter Server with Hybridity Bundle 实例添加服务的过程
{: #vc_hybrid_addingremovingservices-adding-procedure}

要将服务应用于 vCenter Server with Hybridity Bundle 实例，请单击表中的相应链接以查看服务的注意事项。然后，检查部署的组件，并遵循订购主题中的指示信息来下订单。

### 服务安装结果
{: #vc_hybrid_addingremovingservices-adding-results}

安装服务成功完成后，系统将通过电子邮件通知您，并且该服务会显示在实例详细信息的**服务**选项卡上，状态为**已安装**。

## 查看 vCenter Server with Hybridity Bundle 实例的服务的过程
{: #vc_hybrid_addingremovingservices-viewing-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要查看其服务的实例。
3. 在左侧导航窗格上，单击**服务**。
4. 在**服务**页面上，单击某个服务以查看相关信息，例如服务状态和其他详细信息。
5. 根据查看的服务，可以使用服务详细信息上提供的凭证来访问服务控制台，并在其中管理该服务。

## 除去 vCenter Server with Hybridity Bundle 实例的服务的过程
{: #vc_hybrid_addingremovingservices-removing-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格上的**资源**。
2. 在 **vCenter Server 实例**表中，单击要除去其服务的实例。
3. 在左侧导航窗格上，单击**服务**。
4. 在**服务**页面上，找到要除去的服务实例，然后单击**删除**图标。
5. 在**删除服务**窗口中，查看注意事项或警告（如有）。选中**我了解**，然后单击**删除**。

### 服务除去结果
{: #vc_hybrid_addingremovingservices-removing-results}

接受服务除去请求后，服务状态会更改为**正在除去**。

服务除去成功完成后，系统将通过电子邮件通知您，并且该服务会从实例的**服务**页面中除去。

在所除去服务的 {{site.data.keyword.cloud_notm}} 基础架构计费周期结束之前，仍然会对您计费。
{:note}

## 相关链接
{: #vc_hybrid_addingremovingservices-related}

* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

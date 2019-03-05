---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# 请求 Zerto on IBM Cloud 的受管服务

Zerto on {{site.data.keyword.cloud}} 服务提供了复制和灾难恢复功能。这些功能可以集成到部署产品中，以在 {{site.data.keyword.cloud_notm}} 上保护和恢复 VMware 虚拟环境中的数据。

请求 Zerto on {{site.data.keyword.cloud_notm}} 的受管服务后，可以使用 Zerto 灾难恢复 (DR) 软件和 IBM Resiliency Services 来部署完全受管的 DR 环境。

提供了 Zerto on {{site.data.keyword.cloud_notm}} 的受管服务的以下模型。

## IBM Orchestrated Managed Services for Zerto

如果使用的是 Zerto on {{site.data.keyword.cloud_notm}} 产品，那么此模型适用。

在此模型中，供应了 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 服务以用于 Zerto on {{site.data.keyword.cloud_notm}}。此模型可以通过不间断 DR 测试、RTO/RPO（恢复时间目标/恢复点目标）可视性、故障转移和故障恢复能力，持续保护 {{site.data.keyword.cloud_notm}} 上的虚拟机、操作系统和数据。

所有功能都通过 IBM Resiliency Services 全球指挥中心的 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 仪表板进行管理。

有关更多信息，请参阅 [IBM Resiliency Orchestration](https://www.ibm.com/us-en/marketplace/disaster-recovery-orchestration)。

## IBM Managed Services for Zerto（无编排）

在此模型中，针对 Zerto on {{site.data.keyword.cloud_notm}} 供应了完全受管的 DR 解决方案。如果仅需要 Zerto Virtual Replication 的受管服务，而不需要 {{site.data.keyword.cloud_notm}} 上的 {{site.data.keyword.cloud_notm}} Resiliency Orchestration 服务，那么此模型适用。

有关更多信息，请参阅 [IBM Resiliency Disaster Recovery as a Service](https://www.ibm.com/us-en/marketplace/disaster-recovery-as-a-service#product-header-top)。

## 请求 Zerto on IBM Cloud 的受管服务的过程

1. 在 {{site.data.keyword.vmwaresolutions_short}} 控制台中，单击左侧导航窗格中的**开始**。
2. 向下滚动该页面，在**订购更多受管服务**下，单击 **Zerto on IBM Cloud 的受管服务**卡。
3. 在 **Zerto on IBM Cloud** 页面上，查看 Zerto on {{site.data.keyword.cloud_notm}} 作为受管服务的描述和技术规范，然后单击**创建**。
4. 根据需求指定配置设置，或者接受缺省值。
5. 单击 **vCenter Server** 或 **Cloud Foundation** 以将相应服务添加到其中一个实例。
6. 要在订购新实例期间添加服务，请单击**添加到新实例**，然后继续订购新的 [vCenter Server](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)、[vCenter Server with Hybridity](/docs/services/vmwaresolutions/vcenter/vc_hybrid_orderinginstance.html) 或 [Cloud Foundation](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html) 实例。
7. 要将服务添加到现有实例，请单击**添加到现有实例**，从列表中选择所需实例，然后通过单击**供应**以确认要继续处理订单。

### 相关链接

* [订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservices.html)
* [订购、查看和除去 Cloud Foundation 实例的服务](/docs/services/vmwaresolutions/sddc/sd_addingremovingservices.html)
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic/trbl_support.html)

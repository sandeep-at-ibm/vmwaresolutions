---

copyright:

  years:  2016, 2018

lastupdated: "2017-01-23"

---

# V1.3 发行说明

此发行版包含新增功能、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## vCenter Server 实例的共享文件级别存储器

现有，可以向 vCenter Server 实例添加共享 NAS（网络连接的存储器）。通过添加此功能部件，可以在 vCenter Server 上运行生产工作负载，并防止在发生节点故障时丢失数据。在 vCenter Server 实例订购过程中，NFS（网络文件系统）文件存储器作为选件提供。有关更多信息，请参阅[订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)。

## 除去 Zerto 灾难恢复

无论是将 Zerto 灾难恢复作为实例的一部分来订购，还是将其添加到现有实例，现在如果不再需要此服务，都可将其除去。在控制台中请求除去此服务后，IBM 支持人员会指导您完成除去过程。

有关更多信息，请参阅以下主题：

* [除去灾难恢复](../services/removingzertodr.html)
* [查看 Cloud Foundation 实例](../sddc/sd_viewinginstances.html)
* [查看 vCenter Server 实例](../vcenter/vc_viewinginstances.html)

## Cloud Foundation 实例的 VMware NSX Edge

NSX Edge 现在包含在要订购的新 Cloud Foundation 实例中。NSX Edge 提供网络边缘安全性和网关服务，以隔离虚拟化网络。

在实例部署期间，IBM 会部署“管理 NSX Edge 服务网关 (ESG)”。IBM 管理虚拟机使用此 ESG 与自动化相关的特定外部 IBM 管理组件进行通信。此 ESG 部署为包含两个接口：一个接口连接到 {{site.data.keyword.cloud_notm}} 专用 VLAN，另一个接口连接到 {{site.data.keyword.cloud_notm}} 公用 VLAN。

为了确保安全性，采用了防火墙规则，以仅允许由管理虚拟机发起的出站 HTTPS 通信。此 ESG 部署在大型配置中，只有 IBM 支持人员才能修改该配置。

有关更多信息，请参阅以下主题：

* [Cloud Foundation 实例的技术规范](../sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [管理服务 NSX Edge 会构成安全风险吗？](../vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX 文档](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 实例订购过程

改进了 Cloud Foundation 实例和 vCenter Server 实例的实例订购过程：

* 摘要页面会显示所订购的所有组件和服务的全部适用条款和条件，以便在您下订单之前轻松访问以复查并同意这些条款。
* 可以在下订单之前保存并打印实例的订单摘要。通过此新功能，可以复查实例设置和成本，根据需要修改订购的组件，获取核准，然后返回到订单。

有关更多信息，请参阅以下主题：

* [订购 Cloud Foundation 实例](../sddc/sd_orderinginstance.html)
* [订购 vCenter Server 实例](../vcenter/vc_orderinginstance.html)

## 实例管理

为实例管理过程提供了以下新功能和改进：

* 对于 Cloud Foundation 实例和 vCenter Server 实例，在决定将 ESXi 服务器添加到实例之前，可以先查看并复查这些服务器的估算成本。指定要添加的服务器数后，控制台上将显示每月每个服务器的估算成本。有关更多信息，请参阅[扩展和收缩 Cloud Foundation 实例的容量](../sddc/sd_addingremovingservers.html)以及[扩展和收缩 vCenter Server 实例的容量](../vcenter/vc_addingremovingservers.html)。
* 对于 Cloud Foundation 实例和 vCenter Server 实例，总实例数会显示在摘要页面的顶部。还可以在实例摘要页面中，通过一次单击来订购实例。此外，在供应期间，还可以在摘要页面上查看详细订单状态。将鼠标悬停在显示的状态上时，可以查看有关当前步骤或错误（如有）的更多详细信息。
* 对于 Cloud Foundation 实例，实例详细信息页面会显示实例的部署历史记录，以及有关部署状态的逐步信息。有关更多信息，请参阅[查看 Cloud Foundation 实例](../sddc/sd_viewinginstances.html)。
* 对于 Cloud Foundation 实例，通过在**更新和补丁**页面上提供有关更新的更多详细信息（例如：补丁所需的停机时间、更新的安排时间以及应用当前补丁之前需要应用必需补丁时的可视指示），提高了更新和补丁应用过程的易用性。有关更多信息，请参阅[对 Cloud Foundation 实例应用更新和补丁](../sddc/sd_applyingupdates.html)。

## 电子邮件通知

现在，在下新订单进行实例部署时，以及在实例中添加、部署或除去服务时，您都会收到电子邮件通知。缺省情况下，通知设置已启用。您可以根据自己的偏好，在**设置**页面上设置要接收的通知。有关更多信息，请参阅[用户帐户和设置](useraccount.html)。

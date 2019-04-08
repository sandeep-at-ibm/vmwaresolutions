---

copyright:

  years:  2016

lastupdated: "2016-12-12"

subcollection: vmwaresolutions


---

# V1.2 发行说明
{: #relnotes_v12}

此发行版包含新增功能、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## 组件更新
{: #relnotes_v12-comp}

VMware ESXi 的新版本为 vSphere 6.0 u2 p03，是从前发行版中的 ESXi 6.0 u2 更新的。

## IBM 标识和 Bluemix 帐户关联
{: #relnotes_v12-ibm-id}

{{site.data.keyword.vmwaresolutions_full}} 作为基础架构解决方案在 IBM Bluemix®“目录”中提供。必须将 **IBM 标识**帐户与 Bluemix 帐户相关联，才能使用 **IBM 标识**帐户登录到 {{site.data.keyword.vmwaresolutions_short}} 控制台。

有关更多信息，请参阅以下主题：
* [入门](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Bluemix 访问故障诊断](/docs/account?topic=account-accessing){:new_window}

## Zerto 灾难恢复
{: #relnotes_v12-zerto}

您可以在订购实例时订购包含 Zerto 灾难恢复的 VMware Cloud Foundation 实例和 VMware vCenter Server 实例。还可以在实例详细信息页面中向现有 Cloud Foundation 实例和 vCenter Server 实例添加 Zerto 灾难恢复。

有关更多信息，请参阅以下主题：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [查看 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Zerto 灾难恢复](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)

## 定价信息
{: #relnotes_v12-price}

现在，在决定下订单之前，可以查看并复查所订购实例的估算成本。订购实例时，在选择组件后，所有组件的总成本和详细定价将显示在**摘要**页面上。

有关更多信息，请参阅[订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)。

## 实例订购过程的增强功能
{: #relnotes_v12-inst-order}

通过以下增强功能，极大改进了实例订购过程：
* 对于 Cloud Foundation 实例和 vCenter Server 实例，采用了新的验证检查，以确保您使用的 SoftLayer® 用户帐户具有必需的用户许可权，VLAN 生成功能已启用，以及提供了正确的 API 密钥。如果不满足任一需求，您都会直接在用户界面上收到用于解决问题的相关指示信息。
*  对于 vCenter Server 实例，优化了在其中选择实例组件的订单，以便仅显示具有您需要的可用硬件和 ESXi 服务器的数据中心。此更改可最大限度降低稍后发生错误的可能性。

有关更多信息，请参阅[订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)。

## 其他电子邮件通知
{: #relnotes_v12-email}

现在，向实例添加新的 ESXi 服务器时，以及除去现有 ESXi 服务器时，都会收到电子邮件通知。此外，删除实例时，也会收到电子邮件通知。缺省情况下，通知设置已启用。您可以根据自己的偏好，在**设置**页面上设置要接收的通知。

有关更多信息，请参阅[用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。

---

copyright:

  years:  2016

lastupdated: "2016-11-04"

subcollection: vmwaresolutions


---

# V1.1 发行说明
{: #relnotes_v11}

此发行版包含新增功能、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VLAN 生成需求
{: #relnotes_v11-vlan-spanning}

如果使用的是经典（非 VRF）SoftLayer® 帐户，那么必须启用 VLAN 生成。如果经典帐户未启用 VLAN 生成，那么 VMware 虚拟化环境的各种组件可能无法相互通信。要启用 SoftLayer 帐户中的 VLAN 生成，请参阅[启用或禁用 VLAN 生成](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}。

## 电子邮件设置和通知
{: #relnotes_v11-email}

可以在**设置**页面上配置电子邮件通知。缺省情况下，此设置已启用，这意味着对于任何新订购的实例，在该实例已供应并准备就绪可供使用时，您会收到电子邮件通知。还可以在**设置**页面上禁用电子邮件通知。有关更多信息，请参阅[用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。

## 详细状态信息
{: #relnotes_v11-status-info}

现在，提供了 Cloud Foundation 实例的详细状态信息。单击实例名称时，显示的状态信息将提供有关部署进度的更多详细信息。如果发生错误，那么会显示消息以帮助您解决该问题。

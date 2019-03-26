---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

---

# V1.5 发行说明
{: #relnotes_v15}

此发行版包含新增功能、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## VRF 与经典 SoftLayer 帐户需求
{: #relnotes_v15-vrf}

对于经典 SoftLayer® 帐户，VLAN 生成是可以在帐户级别启用的设置。{{site.data.keyword.vmwaresolutions_short}} 需要启用 VLAN 生成。

对于 VRF（虚拟路由和转发）SoftLayer 帐户，VLAN 生成的等效功能是永久性设置，无法更改。VRF 帐户不需要用户配置。

下实例订单之前，请确保 SoftLayer 帐户是 VRF 帐户或者启用了 VLAN 生成的经典（非 VRF）帐户。否则，订单可能会失败。

要确认 SoftLayer 帐户是否为 VRF 帐户，请向 IBM Bluemix 支持进行验证。对于经典帐户，必须遵循[启用或禁用 VLAN 生成](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}中的指示信息来启用 VLAN 生成。

## 服务收费模型更新
{: #relnotes_v15-svc-charge}

对于 Cloud Foundation 实例，引入了新的 _SDDC Manager_ 许可证，将按每个节点每月收取费用。

## 易用性增强功能
{: #relnotes_v15-ui}

对整个用户界面进行了改进：

* 用户界面上清晰地指明各个 {{site.data.keyword.CloudDataCents_notm}} 的可用性以及它们是否有足够的库存来执行订单。使用这些详细信息可在订购实例时，针对要选择的 {{site.data.keyword.CloudDataCent_notm}} 做出知情决策。有关更多信息，请参阅[针对 vCenter Server 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)。
* 对于 Cloud Foundation 实例，在输入字段中输入必需信息时，实例名称、域名和子域名以及数据中心位置等信息会自动以图形格式显示。

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 缩放在控制台外部创建的集群
{: #vs_orderingforclustersoutside}

可以使用 VMware vSphere 产品扩展在 {{site.data.keyword.vmwaresolutions_full}} 控制台外部创建的现有 vSphere 集群。要缩放在控制台外部创建的 vSphere 集群，请使用与控制台相同的设置重新创建集群，然后缩放集群。

## 需求
{: #vs_orderingforclustersoutside-req}

确保已完成以下任务：
*  已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[管理用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
*  已查看[针对 VMware vSphere on {{site.data.keyword.cloud_notm}} 的需求和规划](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)中的需求和注意事项。

## 缩放在控制台外部创建的集群的过程
{: #vs_orderingforclustersoutside-procedure}

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格上的 **VMware**，然后单击**虚拟数据中心**部分中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 页面上，单击**创建**。  
   确保位于**新建**选项卡上，并且**集群配置**列表中显示了**新集群**。
3. 使用与现有集群（在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部创建）相同的设置来创建集群。有关更多信息，请参阅[订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)。  
   对于网络接口，要扩展在 {{site.data.keyword.vmwaresolutions_short}} 控制台外部创建的集群，必须选择集群的现有 VLAN。
   {:note}
4. 在**订单摘要**窗格中，验证集群配置，然后单击**保存配置**。   
5. 在**开始**页面上，单击 **VMware vSphere on IBM Cloud** 卡。
6. 在 **VMware vSphere on IBM Cloud** 页面上，单击**创建**。
7. 单击**扩展现有**选项卡。从**集群配置**列表中，选择最近创建的集群。
8. 在 **{{site.data.keyword.baremetal_short}}** 部分中，指定要添加到集群的 {{site.data.keyword.baremetal_short}} 数。
9. 如果集群在其公用 VLAN 上不包含 FortiGate Security Appliance 300 系列 HA 对，那么可以通过选择 **FortiGate Physical Appliance 300 系列 HA 对**下的**购买时包含**来进行订购。
10. 在**订单摘要**窗格中，验证实例配置和估算成本，确保要向其收费的帐户正确，复查并接受条款，然后单击**供应**。

## 结果
{: #vs_orderingforclustersoutside-results}

集群部署会自动启动，并且您将收到电子邮件确认，指示正在处理订单。集群准备就绪可供使用时，将通过电子邮件通知您。

vSphere 集群不会与 vCenter Server 和 Cloud Foundation 实例一起显示在**资源**页面上。
{:note}

## 相关链接
{: #vs_orderingforclustersoutside-related}

* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [基于现有配置订购 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [缩放现有 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)

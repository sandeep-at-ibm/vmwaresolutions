---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: vSphere order cluster, vSphere configuration, order vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 基于现有配置订购 vSphere 集群
{: #vs_orderingbasedonexistingconfig}

您可以基于保存的配置模板来订购 VMware vSphere 集群。使用此过程可根据现有集群配置来定义新集群配置。

## 需求
{: #vs_orderingbasedonexistingconfig-req}

确保已完成以下任务：
*  已在**设置**页面上配置 {{site.data.keyword.cloud}} 基础架构凭证。有关更多信息，请参阅[用户帐户和设置](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)。
*  已查看[针对 vSphere 集群的需求和规划](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)中的需求和注意事项。
*  已创建要复用的配置模板。

## 基于现有配置订购 vSphere 集群的过程
{: #vs_orderingbasedonexistingconfig-procedure}

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格上的 **VMware**，然后单击**虚拟数据中心**部分中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 页面上，单击**创建**。  
3. 单击**新建**选项卡，然后从**集群配置**列表中选择配置模板。
4. 输入新的集群名称。
5. 复查自动填写的集群设置，并根据需要更新设置。有关设置的更多信息，请参阅[订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)。
6. 在**订单摘要**窗格中，验证实例配置和估算成本。
   * 要将配置另存为模板而不下订单，请单击**保存配置**。
   * 要下订单，请确保要向其收费的帐户正确，复查并接受条款，然后单击**供应**。

   这将仅安装 {{site.data.keyword.baremetal_short}}。您负责在集群部署后安装和配置各种组件（例如，VMware vCenter、VMware NSX 和 VMware vSAN）。
   {:note}

## 结果
{: #vs_orderingbasedonexistingconfig-results}

如果已将集群配置另存为模板，那么会收到控制台通知，指示配置已保存。然后可以在**集群配置**列表中找到该模板。

如果已下订单，那么将自动开始部署集群。您将收到电子邮件确认，指示正在处理订单。集群准备就绪可供使用时，还将通过电子邮件通知您。

与 vCenter Server 实例不同，vSphere 集群不会显示在**资源**页面上。
{:note}

## 相关链接
{: #vs_orderingbasedonexistingconfig-related}

* [订购新的 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [缩放现有 vSphere 集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [缩放在控制台外部创建的集群](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-11"

---

# 扩展现有 vSphere 集群

对于您在 {{site.data.keyword.vmwaresolutions_full}} 控制台中订购或保存的 VMware vSphere 集群，可以进行向外扩展。要执行此操作，请为集群添加 ESXi 服务器或者订购 FortiGate 300 Series Security Appliance HA 对。

## 需求

确保已完成以下任务：
*  已在**设置**页面上配置 {{site.data.keyword.cloud_notm}} 基础架构凭证。有关更多信息，请参阅[用户帐户和设置](../vmonic/useraccount.html)。
*  已查看[针对 vSphere 集群的需求和规划](vs_planning.html)中的需求和注意事项。

## 过程

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击左侧导航窗格中的 **VMware**，然后单击**虚拟数据中心**部分中的 **VMware vSphere**。
2. 在 **VMware vSphere on IBM Cloud** 页面上，单击**创建**。  
3. 单击**扩展现有**选项卡，然后从**集群配置**列表中选择要扩展的集群。
4. 复查自动填写的集群设置。
5. 在 **{{site.data.keyword.baremetal_short}}** 部分中，指定要添加到集群的 {{site.data.keyword.baremetal_short}} 数。
6. 如果集群在其公用 VLAN 上不包含 FortiGate Security Appliance 300 系列 HA 对，那么可以通过选择 **FortiGate Physical Appliance 300 系列 HA 对**下的**购买时包含**来进行订购。
7. 在**订单摘要**窗格中，验证实例配置和估算成本。
   * 要将配置另存为模板而不下订单，请单击**保存配置**。
   * 要下订单，请确保要向其收费的帐户正确，复查并接受条款，然后单击**供应**。

### 结果

自动开始集群扩展。您将收到电子邮件确认，指示正在处理订单。集群准备就绪可供使用时，将通过电子邮件通知您。

**注**：与 vCenter Server 和 Cloud Foundation 实例不同，vSphere 集群不会显示在**部署的实例**页面。

### 相关链接

* [订购新的 vSphere 集群](vs_orderinginstances.html)
* [基于现有配置订购 vSphere 集群](vs_orderingbasedonexistingconfig.html)
* [扩展在控制台外部创建的集群](vs_orderingforclustersoutside.html)

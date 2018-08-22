---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# Zerto on IBM Cloud 的除去过程

Zerto on {{site.data.keyword.cloud}} 服务的除去过程会自动执行。将完成以下步骤，以成功除去 Zerto on {{site.data.keyword.cloud_notm}} 服务。

## 如何除去 Zerto on IBM Cloud

1. 在左侧导航窗格中，单击**部署的实例**，然后单击要从中除去此服务的实例。
2. 单击**服务**选项卡。
3. 在**安装的服务**选项卡上，单击服务卡右上角的溢出菜单图标，然后单击**除去服务**。
4. 在**除去服务**窗口中，查看注意事项或警告（如有）。单击**我了解**。
5. 接受服务除去请求后，服务状态会更改为**正在除去**，并且会完成以下除去步骤：   
   1. 除去部署到所有 ESXi 服务器的 Zerto Virtual Replication 设备。
   2. 卸载 Zerto Virtual Replication。
   3. 删除安装了 Zerto Virtual Replication 的 Windows VSI（虚拟服务实例）。
   4. 退回为 Zerto Virtual Replication 与 {{site.data.keyword.cloud_notm}} 基础架构之间的通信订购的专用可移植子网。   
   5. 从 {{site.data.keyword.cloud_notm}} 计费结算表中除去 Zerto 灾难恢复服务的费用。

      **注**：在所除去的 Zerto 灾难恢复服务的计费周期结束之前，仍然会对您计费。

## 结果

服务除去成功完成后，系统将通过电子邮件通知您，并且该服务条目会从**安装的服务**选项卡中删除。

### 相关链接

* [订购 Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Cloud Foundation 实例](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 实例](../vcenter/vc_vcenterserveroverview.html)
* [zerto.com Web 站点](https://www.zerto.com){:new_window}
* [Zerto 技术文档](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

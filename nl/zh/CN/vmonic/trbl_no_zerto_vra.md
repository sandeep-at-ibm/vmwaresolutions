---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# 对于新创建的 ESXi 服务器，未显示 Zerto Virtual Replication 设备
{: #trbl_no_zerto_vra}

## 问题
{: #trbl_no_zerto_vra-problem}

向已安装 Zerto 灾难恢复的 VMware vCenter Server 实例添加 ESXi 服务器后，Virtual Replication 设备 (VRA) 未显示在 Zerto Virtual Replication 控制台上。

## 解决方法
{: #trbl_no_zerto_vra-resolution}

对于 vCenter Server 实例，Zerto 灾难恢复服务仅安装在缺省集群 **cluster1** 中的 ESXi 服务器上。在同一 vCenter Server 环境中创建其他集群时，或将 ESXi 服务器添加到其他集群时，不会在这些其他集群上自动安装 Zerto 灾难恢复。

在其他集群上，必须单独安装 Zerto 灾难恢复。

开具 {{site.data.keyword.cloud}} 支持凭单，并与 IBM 支持人员合作来获取可用 IP 地址，以通过 Zerto 控制台而不是 {{site.data.keyword.vmwaresolutions_short}} 控制台来安装 VRA。

要访问 Zerto 控制台，请单击实例的**服务**选项卡中的 Zerto 卡，单击**查看详细信息**，然后单击**查看 Zerto 控制台**。

有关联系 IBM 支持人员的更多信息，请参阅[联系 IBM 支持人员](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-trbl_support#trbl_support)。

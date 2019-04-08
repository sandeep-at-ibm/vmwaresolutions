---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmwaresolutions


---

# 在添加 HA 集群时发现的 vSphere 控制台配置问题
{: #trbl_add_ha_cluster_config}

## 问题
{: #trbl_add_ha_cluster_config-problem}

添加仅有一个文件共享的 HA（高可用性）集群配置时，在 ESXi 主机上看到以下配置问题：

> 主机的脉动信号数据存储数为 1，低于必需值：2

## 解决方法
{: #trbl_add_ha_cluster_config-resolution}

如果共享存储器中没有冗余可支持数据存储脉动信号传递，那么会发生此问题。

有关如何解决该问题的更多信息和步骤，请参阅 [HA error: The number of heartbeat data stores for host is 1, which is less than required: 2 (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739)。

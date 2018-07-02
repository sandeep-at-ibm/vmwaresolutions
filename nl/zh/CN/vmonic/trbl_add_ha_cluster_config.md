---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# 添加 HA 集群时看到 vSphere 控制台配置问题

## 问题
添加仅具有一个文件共享的 HA（高可用性）集群配置时，在 ESXi 主机上看到以下配置问题：

`主机的脉动信号数据存储数为 1，低于必需值：2`

## 解决方法
如果共享存储器中没有冗余可支持数据存储脉动信号传递，那么会发生此问题。

有关如何解决该问题的更多信息和步骤，请参阅 [HA 错误： 主机的检测信号数据存储的数量为 1，小于所要求的数量： 2 (2095769)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739)。

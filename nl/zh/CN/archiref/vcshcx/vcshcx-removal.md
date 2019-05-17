---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

subcollection: vmware-solutions


---

# 除去 HCX
{: #vcshcx-removal}

除去 HCX 的操作假定延伸网络已不再使用。请使用以下过程来除去 HCX。

1. 取消延伸所有延伸网络。
2. 在客户机用户界面 (UI) 中，删除任何 L2C 设备。等待 L2C 设备不再显示在 Web UI 中。
3. 删除 CGW。这还将除去 WAN Opt。等待除去 CGW 和 WAN Opt 设备。
4. 关闭并删除客户机和云端的 HCX Manager 设备虚拟机 (VM)。
5. 从 NSX 云端除去 HCX ESG。
6. 使用 vCenter Mob 浏览器来除去 HCX 插入件。

## 相关链接
{: #vcshcx-removal-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 概述](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

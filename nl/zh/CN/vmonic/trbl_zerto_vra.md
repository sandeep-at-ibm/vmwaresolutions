---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Zerto VRA, Zerto uninstall

subcollection: vmware-solutions


---

# 卸载 Zerto on IBM Cloud 后，在 vCenter 控制台中仍可看到 ESXi 主机上显示有 Zerto VRA
{: #trbl_zerto_vra}

## 问题
{: #trbl_zerto_vra-problem}

使用 {{site.data.keyword.slportal}} 成功卸载 Zerto on {{site.data.keyword.cloud}} 服务后，不会除去 Zerto Virtual Replication 设备 (VRA)。

## 解决方法
{: #trbl_zerto_vra-resolution}

请在 vCenter 控制台中手动除去 VRA。

1. 登录到 vCenter 控制台。
2. 单击**主机和集群**，并找到名称以 **Z-VRA-** 开头的虚拟机。例如，**Z-VRA-host0-vcs40dal.vcs.icvs.org**。
3. 右键单击 **Z-VRA-** 虚拟机，并单击**从磁盘中删除**。

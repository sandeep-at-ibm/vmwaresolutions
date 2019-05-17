---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmware-solutions


---

# 在解除安裝 Zerto on IBM Cloud 之後，可在 ESXi 主機的 vCenter 主控台中看到 Zerto VRA
{: #trbl_zerto_vra}

## 問題
{: #trbl_zerto_vra-problem}

在使用 {{site.data.keyword.slportal}} 順利解除安裝 Zerto on {{site.data.keyword.cloud}} 服務之後，未移除 Zerto Virtual Replication Appliance (VRA)。

## 解決方法
{: #trbl_zerto_vra-resolution}

請從 vCenter 主控台手動移除 VRA。

1. 登入 vCenter 主控台。
2. 按一下**主機及叢集**，然後找出名稱開頭為 **Z-VRA-** 的虛擬機器。例如，**Z-VRA-host0-vcs40dal.vcs.icvs.org**。
3. 在 **Z-VRA-** 虛擬機器上按一下滑鼠右鍵，然後按一下**從磁碟中刪除**。

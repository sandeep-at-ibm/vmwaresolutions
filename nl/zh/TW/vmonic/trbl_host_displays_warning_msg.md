---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, configuration issue, ESXi server issue

subcollection: vmware-solutions


---

# ESXi 伺服器顯示配置問題
{: #trbl_host_displays_warning_msg}

## 問題
{: #trbl_host_displays_warning_msg-problem}

配置問題會顯示在 vSphere 用戶端的 VMware ESXi 伺服器**監視器**標籤的**問題**標籤中。

在 ESXi 伺服器的**問題**標籤中，會顯示下列訊息：

`This host currently has no management network redundancy`

即使提供備援的專用分散式交換器有兩個可用的上行鏈路，也會顯示此訊息。

## 解決方法
{: #trbl_host_displays_warning_msg-resolution}

這是 VMware 已知問題。若要解決這個問題，請遵循 [ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/s/article/2008602){:new_window} 中的指示。

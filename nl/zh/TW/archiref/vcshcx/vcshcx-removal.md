---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# HCX 移除
{: #vcshcx-removal}

HCX 移除假設已不再使用延伸網路。請使用下列程序來移除 HCX。

1. 將所有延伸網路取消延伸。
2. 在用戶端使用者介面 (UI) 中，刪除任何 L2C 應用裝置。等待 L2C 應用裝置從 Web 使用者介面中消失。
3. 刪除 CGW。這也會移除「WAN 最佳化工具」。等待移除 CGW 及 WAN 最佳化工具應用裝置。
4. 從用戶端和雲端關閉及刪除「HCX Manager 應用裝置」虛擬機器 (VM)。
5. 從 NSX 雲端移除 HCX ESG。
6. 使用 vCenter Mob 瀏覽器來移除 HCX 嵌入式管理單元。

## 相關鏈結
{: #vcshcx-removal-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

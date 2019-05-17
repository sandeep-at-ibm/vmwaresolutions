---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# 升級 HCX 元件
{: #vcshcx-upgrade}

升級 HCX 是一個簡單的處理程序，它在用戶端 HCX Manager 更新時使用用戶端 Web 使用者介面 (UI)，在雲端 HCX Manager 更新時使用雲端 Web 使用者介面。您必須同時升級兩端，因為任何機群元件更新會導致兩端使用該管理程式所安裝的程式碼層次重新部署機群元件。如果 VMware 支援要求「系統 ID」，請同時提供用戶端和雲端。使用 SSH 至 HCX Manager（用戶端或雲端），然後執行 'cat/common/location' 來尋找「系統 ID」。

## 相關鏈結
{: #vcshcx-upgrade-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

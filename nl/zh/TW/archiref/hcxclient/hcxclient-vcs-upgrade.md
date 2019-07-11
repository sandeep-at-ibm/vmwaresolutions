---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# 升級 HCX 元件
{: #hcxclient-vcs-upgrade}

升級 HCX 是一個簡單的處理程序，它在用戶端 HCX Manager 更新時使用用戶端 Web 使用者介面 (UI)，在雲端 HCX Manager 更新時使用雲端 Web 使用者介面。

您必須同時升級這兩端，因為任何機群元件更新都會導致這兩端使用 HCX Manager 上所安裝程式碼的層次重新部署機群元件。

如果 VMware 支援中心要求提供系統 ID，請同時提供用戶端和雲端兩端的 ID。使用 SSH 至 HCX Manager（用戶端或雲端），然後執行 `cat /common/location` 來尋找「系統 ID」。

## 相關鏈結
{: #hcxclient-vcs-upgrade-related}

* [HCX 元件和術語的名詞解釋](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [準備安裝環境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 用戶端部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 內部部署服務網](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合雲端移轉](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [監視參數及元件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

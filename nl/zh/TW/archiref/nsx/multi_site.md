---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

# 多站台架構
{: #nsx-multi_site}

{{site.data.keyword.cloud}} 與其他雲端供應項目之間的一個關鍵差異因子，在於全球佈建專用運算功能並自動將隨需應變基礎架構連接至專用 {{site.data.keyword.cloud_notm}} 帳戶內之網路的能力。VMware vCenter Server 的軟體定義網路功能與 {{site.data.keyword.cloud_notm}} 一起，提供了可在數天內建置的精細廣域基礎架構。下列各節說明一個多站台架構的範例，它說明使用 vCenter Server 的現成功能可以實現的目標。

## 跨 vCenter NSX 環境
{: #nsx-multi_site-cross-env}

跨 vCenter NSX 功能容許在主要及次要關係中鏈結最多九個 NSNX 管理程式：一個主要及八個次要。雖然在「加強型鏈結模式 (ELM)」關係中不需要有 vCenter Server，跨 vCenter NSX 即可運作，但它提供下列好處：

* 使用「單一登入 (SSO)」認證來簡化主要及次要關係的建立
* vCenter Server 自動化會為所有鏈結在一起的站台配置 DNS 名稱解析
* 針對 NSX 及一般 vCenter 功能，在所有站台之間使用單一管理畫面

## 多站台範例
{: #nsx-multi_site-example}

下列範例會將 NSX 通用傳輸區域新增至前幾節中討論的基本管理及工作負載拓蹼，同時包括下列特徵：

* 通用傳輸區域跨越 {{site.data.keyword.CloudDataCent_notm}} 內的兩個 {{site.data.keyword.CloudDataCents_notm}} 或 POD。
* 新增傳輸區域之後，會新增多個 VXLAN，以及跨越新 VXLAN 的「通用分散式路由器」。
* 您必須配置通往這兩個站台之工作負載 ESG 的上行鏈路。此配置容許本端站台中的虛擬機器 (VM) 能遍訪至其本端 ESG。
* 對於入埠資料流量，需要廣域負載平衡器。請參閱 {{site.data.keyword.cloud_notm}} 廣域負載平衡供應項目，以符合此需求。
* 此範例需要 VMware NSX Enterprise 版本。

圖 1. 多站台拓蹼

![多站台拓蹼](multisite_topology.svg "多站台拓蹼")

## 相關鏈結
{: #nsx-multi_site-related}

* [{{site.data.keyword.cloud_notm}} 上的網路服務](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx-networking_services)

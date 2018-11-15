---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 連接儲存空間基礎架構設計

{{site.data.keyword.vmwaresolutions_full}} 提供的 VMware 技術是以自動化方式部署在全球各地的 {{site.data.keyword.CloudDataCents_notm}} 內。在 {{site.data.keyword.cloud_notm}} 解決方案組合中，基礎 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 供應項目包含最多 10 個叢集，且各包含最多 59 部 vSphere 主機、單一 Platform Services Controller (PSC)，以及有能力管理最多 400 部主機和 4,000 部虛擬機器的 vCenter Server Appliance。

這裡呈現的架構會藉由新增連接儲存空間作為環境的共用儲存裝置，補足 vCenter Server 解決方案。連接儲存裝置是位於與 vCenter Server 部署相同的 {{site.data.keyword.CloudDataCent_notm}} 內，它包含單一「網路檔案系統 (NFS)」共用，或是來自 {{site.data.keyword.cloud_notm}} 的多個 NFS 匯出。

下圖說明 vCenter Server 部署上連接儲存空間的整體架構。

圖 1. {{site.data.keyword.cloud_notm}} 上連接儲存空間的高階架構

![連接儲存空間架構](../solution/physical_nfs.svg "IBM Cloud 上連接儲存空間的高階架構")

## 實體基礎架構設計

實體基礎架構由三大元件組成，包括實體運算、實體儲存空間及實體網路。這包括 {{site.data.keyword.cloud_notm}} 服務網路以及基礎架構所使用的實體儲存空間。

## 實體網路設計

實體網路是由 {{site.data.keyword.cloud_notm}} 處理。本節說明 {{site.data.keyword.cloud_notm}} 提供的實體網路與連接儲存空間的關係。

### IBM Cloud 網路概觀

{{site.data.keyword.cloud_notm}} 的實體網路分成三個不同的網路：公用、專用和管理。如需公用、專用和管理網路的相關資訊，請參閱[解決方案概觀](../solution/solution_overview.html)。

如需 {{site.data.keyword.cloud_notm}} 網路的相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 網路](https://www.ibm.com/cloud-computing/bluemix/our-network){:new_window}。

如需屬於專用網路一部分之服務網路的說明，請檢閱下列資訊。

### 專用服務網路

{{site.data.keyword.cloud_notm}} 包含的專用服務網路提供共用服務，例如區塊儲存空間、檔案儲存空間、物件儲存空間、DNS 解析器及 NTP 伺服器。此專用網路與客戶專用網路區隔，而且它可讓環境無縫連接到位於 {{site.data.keyword.cloud_notm}} 的服務。此專用網路為多層式，伺服器和其他基礎架構是連接到聚集的後端客戶交換器 (BCS)。這些聚集交換器連接到一對個別路由器，亦即後端客戶路由器或 BCR，以執行 L3 網路功能。此專用網路也支援使用巨大訊框的功能，亦即 MTU 9000，以建立實體主機連線。

### VLAN

如需 VLAN 的相關資訊，請參閱[實體基礎架構設計](../solution/design_physicalinfrastructure.html)中的_實體網路設計_ 一節。

## 實體儲存空間設計

本節呈現出現在 {{site.data.keyword.cloud_notm}} 中的連接儲存裝置配置。連接儲存裝置補足了現有的 vCenter Server 解決方案。因此，不會呈現實體主機內部的本端連接磁碟。

## 連接儲存空間效能

效能和耐久性儲存空間是 {{site.data.keyword.cloud_notm}} 儲存空間解決方案，其設計是為了支援需要可預測效能等級的高 I/O 應用程式。此項可預測的效能，是透過將每秒通訊協定層次輸入/輸出作業數 (IOPS) 配置給個別磁區來達成。

IOPS 的範圍是從 100 到 48,000，可使用範圍從 20 GB - 12 TB 的儲存空間大小來佈建它。效能和耐久性儲存空間磁區可用於區塊儲存空間和檔案儲存空間。

在本設計中，vCenter Server 解決方案針對連接儲存空間提供耐久性儲存空間。因此，您可以選取及連接（透過自動化）耐久性 NFS 匯出，其大小的範圍是從 20 GB 到上限 12 TB。{{site.data.keyword.cloud_notm}} 容許最多 64 部 vSphere ESXi 主機連接到單一耐久性 NFS 匯出。

耐久性提供三種 IOPS 效能層級，以支援不同的應用程式需求。

在佈建 NFS 共用之後，可以調整其大小或重新配置，以容許更多或更少 IOPS。{:note}

如需詳細的 IOPS 選項，請參閱[訂購 vCenter Server 實例](../../vcenter/vc_orderinginstance.html)中的_儲存空間設定_ 一節。

除了儲存空間層級之外，{{site.data.keyword.cloud_notm}} 耐久性儲存空間還支援廣泛的應用程式需求選擇，包括 Snapshot 和抄寫，以及 {{site.data.keyword.CloudDataCent_notm}} 位置的靜態加密。

### 相關鏈結

* [解決方案概觀](../solution/solution_overview.html)

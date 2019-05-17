---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-26"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted 概觀
{: #icp_overview}

{{site.data.keyword.cloud}} Private Hosted 服務會自動將 {{site.data.keyword.cloud_notm}} Private Hosted 及 {{site.data.keyword.cloud_notm}} Automation Manager 部署在 VMware vCenter Server 實例上。此服務會將微服務和容器的功能帶入 {{site.data.keyword.cloud_notm}} 上的 VMware 環境。使用此服務，您可以將熟悉的相同 VMware 與 {{site.data.keyword.cloud_notm}} Private 作業模型和工具，從內部部署延伸到 {{site.data.keyword.cloud_notm}}。

此服務適用於下列實例：
* 部署在（或升級至）2.7 版及更新版本的 vCenter Server with Hybridity Bundle 實例
* 部署在（或升級至）2.5 版及更新版本的 vCenter Server 實例

對於部署在（或升級至）3.0 版或更新版本中的實例，{{site.data.keyword.cloud_notm}} Automation Manager 也會部署為 {{site.data.keyword.cloud}} Private Hosted 服務訂購的一部分。
{:note}

## IBM Cloud Private Hosted 的技術規格
{: #icp_overview-specs}

下表列出為**正式作業就緒**環境和**開發/測試**環境訂購 IBM Cloud Private Hosted 服務的最低需求。

表 1.「正式作業就緒」和「開發/測試」環境的最低需求

|環境 | 核心 |  記憶體 (GB) | 主機 | 儲存空間 (GB) |
|:---------- |:---- |:------ |:---- |:------- |
| 正式作業就緒 | 52 | 640 | 3 | 8,000 |
| 開發/測試 | 30 | 200 | 3 | 4,000 |

### IBM Cloud Private Hosted 的資源需求
{: #icp_overview-resource-req}

下表列出「正式作業就緒」和「開發/測試」環境中 {{site.data.keyword.cloud_notm}} Private Hosted 服務的資源需求。

表 2.「正式作業就緒」環境中的 {{site.data.keyword.cloud_notm}} Private Hosted 資源需求

| 節點類型  | CPU 核心   |  記憶體 (GB) | 磁碟 1 (GB) | 磁碟 2 (GB) | VM 數目 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 開機       | 12 | 24 | 100 |1 |1 |   
| 管理 | 8                                   | 64 | 500 | 3 | 3 |
| 主節點     | 8                                   | 64 | 200 | 3 | 3 |  
| Proxy      |2 |4 | 150 | 3 | 3 |
| 工作者節點 |4 | 16 | 200 | 300 | 6 |
| 漏洞警告器 | 8                                   | 16 | 500 |1 |1 |
| GlusterFS  | 8                                   | 16 | 150 | 50 | 3 |
| NFS 伺服器 | 8                                   |4 | 350 |1 |1 |
|NSX Edge Services Gateway|2 |1 | 0.5 | 0.5 |2 |
| 記載的限制 | 52 | 640 |  | 8,000 |   |

表 3.「開發/測試」環境中的 {{site.data.keyword.cloud_notm}} Private Hosted 資源需求

| 節點類型  | CPU 核心   |  記憶體 (GB) | 磁碟 1 (GB) | 磁碟 2 (GB) | VM 數目 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 開機       | 12 | 24 | 100 |1 |1 |   
| 管理 | 8                                   | 16 | 150 |1 |1 |
| 主節點     | 8                                   | 16 | 200 |1 |1 |  
| Proxy      |2 |4 | 150 |1 |1 |
| 工作者節點 |4 | 16 | 200 | 300 | 3 |
| 漏洞警告器 | 8                                   | 16 | 150 |1 |1 |
| GlusterFS  | 8                                   | 16 | 150 | 50 | 3 |
| NFS 伺服器 | 8                                   |4 | 350 |1 |1 |
|NSX Edge Services Gateway|2 |1 | 0.5 | 0.5 |2 |
| 記載的限制 | 30 | 200 |  | 4,000 |  |

### 計算 IBM Cloud Private Hosted 空間需求的公式
{: #icp_overview-formulas}

下列公式用來計算 IBM Cloud Private 的空間需求及管理上的額外需要。

#### 公式 1
{: #icp_overview-formulas-1}

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

表 4. 公式 1 中的變數說明

| 變數	|說明              |	單位 |	vSAN 範例 | NFS 範例 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |可供環境中工作負載和服務使用的實際核心數 | 核心 | 38 | 43 |
| HostCount | 預設叢集中的主機數目	| 主機 |4 |4 |
| HostCoreCount | 預設叢集中每一部主機可用的原始核心數 | 核心 | 16 | 16 |
| HostOverheadCores | ESXi 伺服器保留給額外需要的核心數（等於 0.1 核心）| 核心 | 0.1 | 0.1 |
| MgmtOverheadCores | vCenter Server 管理元件（vCenter Server、PSC、AD/DNS、Edges）保留的核心數（等於 5 核心）| 核心 | 5 | 5 |
| vSphereHAHostTolerance |vSphere HA 配置中容忍的主機數（等於一部主機）|	主機	 |1 |1 |
| HostVsanOverheadCorePercentage | vSAN 所使用的主機核心百分比，其等於 10%，如果主機非 vSAN，則等於 0%| % | 10% |0% |

#### 公式 2
{: #icp_overview-formulas-2}

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

表 5. 公式 2 中的變數說明

| 變數	|說明              |	單位 |	vSAN 範例 | NFS 範例 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| 可供環境中工作負載和服務使用的記憶體 GB 數 | GB | 	693	| 860 |
| HostCount	| 預設叢集中的主機數目	| 主機  | 6	| 6 |
| HostMemory |	 預設叢集中每一部主機可用的原始 GB 數 |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | 在此主機上每一個 vSAN 容量 SSD 磁碟容量的 GB 數（等於 960、1,946 或 3,891），如果主機非 vSAN，則等於 0 GB| GB |	960 | 0 |
| HostOverheadMemory |	ESXi 伺服器保留給額外需要的記憶體 GB 數（等於 4.6 GB）|	GB	| 4.6 |	4.6 |
| MgmtOverheadMemory |	vCenter Server 管理元件（vCenter Server、PSC、AD/DNS、Edges）保留的記憶體 GB 數（等於 77 GB）| GB | 77 | 77 |
| vSphereHAHostTolerance |vSphere HA 配置中容忍的主機數（等於一部主機）| 主機	|1 |1 |
| HostVsanOverheadMemoryDiskPercentage | vSAN 管理所保留的記憶體 GB 數（以其中一個容量 vSAN 磁碟的百分比表示），其等於 2.75%|	% | 2.75% | 2.75% |
| HostVsanOverheadMemory | vSAN 管理所保留的記憶體 GB 數（不論磁碟大小為何）（等於 7 GB），如果主機非 vSAN，則等於 0 GB| GB |  7	| 0 |

## 安裝 IBM Cloud Private Hosted 時的考量
{: #icp_overview-install}

* 請先收集必要的授權，再安裝 {{site.data.keyword.cloud_notm}} Private Hosted 服務。這同時包括 {{site.data.keyword.cloud_notm}} Private 及 {{site.data.keyword.cloud_notm}} Automation Manager 授權。確定您的授權不僅支援起始服務部署，還支援基礎架構中的未來大小擴充。
* 對於「正式作業就緒」環境中的 {{site.data.keyword.cloud_notm}} Private Hosted 部署，不支援每部主機 64 GB RAM。因此，您必須對 **RAM** 選取大於 64 GB 的選項。
* 在您的環境中安裝 {{site.data.keyword.cloud_notm}} Private Hosted 服務之前，會針對環境中預設叢集的可用容量執行檢查，以確保服務元件適合。如果容量檢查未通過，則不會安裝該服務，且主控台上的服務狀態會設為**容量驗證失敗**。此外，還會顯示具有更多詳細資料的主控台訊息，並透過電子郵件通知您。若要安裝服務，您必須新增多部主機，或者透過釋放 RAM、CPU 或磁碟空間來增加預設叢集中的容量，然後在主控台中再次新增服務。之後，您可以按一下它旁邊的**刪除**圖示，來移除處於**容量驗證失敗**狀態中的現有服務。
* 如果您想要部署其他節點，請使用 {{site.data.keyword.cloud_notm}} Private Ubuntu 範本，此範本是使用您的起始 {{site.data.keyword.cloud_notm}} Private Hosted 安裝所部署的。若要尋找範本，請在 VMware vSphere Web Client 中，移至 `cam` 資料夾下的 **VM 及範本**標籤。Ubuntu 範本的預設密碼是 `icponcloud`，建議您在使用範本之前先予以變更。

## 移除 IBM Cloud Private Hosted 時的考量
{: #icp_overview-remove}

* 只會刪除 {{site.data.keyword.cloud_notm}} Private Hosted 服務起始安裝期間所部署的虛擬機器 (VM)。不會清除安裝後部署的任何節點。
* {{site.data.keyword.cloud_notm}} 將會刪除 {{site.data.keyword.cloud_notm}} Private Hosted 起始部署期間所建立的 VXLAN、DLR 和「邊緣閘道」。開始移除 {{site.data.keyword.cloud_notm}} Private Hosted 服務之後，您部署在 VXLAN 上的 VM 就會失去連線功能。

## 相關鏈結
{: #icp_overview-related}

* [訂購 {{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)
* [vCenter Server 和 {{site.data.keyword.cloud_notm}} Private 手冊](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [開立 {{site.data.keyword.cloud_notm}} Private 的問題單](https://www.ibm.com/mysupport/s/?language=en_US){:new_window}
* [{{site.data.keyword.cloud_notm}} Automation Manager 授權](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/licensing.html){:new_window}
* [{{site.data.keyword.cloud_notm}} Automation Manager 元件](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_managed_components.html){:new_window}

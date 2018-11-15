---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted 概觀

{{site.data.keyword.cloud}} Private Hosted 服務會自動將 {{site.data.keyword.cloud_notm}} Private Hosted 部署在 VMware vCenter Server 實例上。此服務會將微服務和容器的功能帶入 {{site.data.keyword.cloud_notm}} 上的 VMware 環境。使用此服務，您可以將熟悉的相同 VMware 與 {{site.data.keyword.cloud_notm}} Private 作業模型和工具，從內部部署延伸到 {{site.data.keyword.cloud_notm}}。

此服務可用於：
* 部署在（或升級至）2.5 版和更新版本的 vCenter Server 實例
* 部署在（或升級至）2.7 版和更新版本的 vCenter Server with Hybridity Bundle 實例。
{:note}

## IBM Cloud Private Hosted 的技術規格

下表列出為**正式作業就緒**環境和**開發/測試**環境訂購 IBM Cloud Private Hosted 服務的最低需求。

表 1.「正式作業就緒」和「開發/測試」環境的最低需求

|環境 | 核心 | 記憶體 | 主機 | 儲存空間 |
|:---------- |:---- |:------ |:---- |:------- |
| 正式作業就緒 | 52 | 640 | 3 | 8000 |
| 開發/測試 | 30 | 200 | 3 | 4000 |

### IBM Cloud Privated Hosted 的資源需求

下表列出「正式作業就緒」和「開發/測試」環境中 {{site.data.keyword.cloud_notm}} Private Hosted 服務的資源需求。

表 2. 「正式作業就緒」環境中的 {{site.data.keyword.cloud_notm}} Private Hosted 資源需求

| 節點類型  | CPU 核心   |  記憶體 (GB) | 磁碟 1 (GB) | 磁碟 2 (GB) | VM 數目 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 開機       | 8                                   | 16 | 100 |1 |1 |   
| 管理 | 8                                   | 64 | 500 | 3 | 3 |
| 主節點     | 8                                   | 64 | 200 | 3 | 3 |  
| Proxy      |2 |4 | 150 | 3 | 3 |
| 工作者節點 |4 | 16 | 200 | 300 | 6 |
| 漏洞警告器 | 8                                   | 16 | 500 | 3 | 3 |
| GlusterFS  | 8                                   | 16 | 150 | 50 | 3 |
| 引導 ICP/CAM | 16 | 32 | 250 |1 |1 |
| NFS 伺服器 | 8                                   |4 | 350 |1 |1 |
|邊緣|2 |1 | 0.5 | 0.5 |2 |
| 總計 | 162 | 642 | 6401 | 1951 | 26 |
| 記載的限制 | 52 | 640 |  | 8000 |   |
|   | 1:3 比例 | 1:1 比例 |  | 1:1 比例 |  |

表 3. 「開發/測試」環境中的 {{site.data.keyword.cloud_notm}} Private Hosted 資源需求

| 節點類型  | CPU 核心   |  記憶體 (GB) | 磁碟 1 (GB) | 磁碟 2 (GB) | VM 數目 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 開機       | 8                                   | 16 | 100 |1 |1 |   
| 管理 | 8                                   | 16 | 150 |1 |1 |
| 主節點     | 8                                   | 16 | 200 |1 |1 |  
| Proxy      |2 |4 | 150 |1 |1 |
| 工作者節點 |4 | 16 | 200 | 300 | 3 |
| 漏洞警告器 | 8                                   | 16 | 150 |1 |1 |
| GlusterFS  | 8                                   | 16 | 150 | 50 | 3 |
| 引導 ICP/CAM | 16 | 32 | 250 |1 |1 |
| NFS 伺服器 | 8                                   |4 | 350 |1 |1 |
|邊緣|1 | 0.5 | 0.5 |2 |2 |
| 總計 | 96 | 201 | 2401 | 1050 | 15 |
| 記載的限制 | 30 | 200 |  | 4000 |  |
|  | 1:3 比例 | 1:1 比例 |  | 1:1 比例 |  |

### 計算 IBM Cloud Private Hosted 空間需求的公式

下列公式可用來計算 IBM Cloud Private 和管理額外負擔的空間需求。

公式 1：`AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

表 4. 公式 1 中的變數說明

| 變數	|說明              |	單位 |	vSAN 範例 | NFS 範例 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	可供環境中工作負載和服務使用的實際核心數 |	核心 |	38	| 43 |
| HostCount	| 預設叢集中的主機數目	| 主機 | 4	|4 |
| HostCoreCount	| 預設叢集中每一個主機可用的原始核心數 |	核心 |	16 | 16 |
| HostOverheadCores	|ESXi 伺服器保留作為額外負擔的核心數（等於 0.1 核心）| 核心	| 0.1 |	0.1 |
| MgmtOverheadCores |vCenter Server 管理元件（vCenter Server、PSC、AD/DNS、Edges）保留的核心數目（等於 5 個核心）| 核心	| 5	| 5 |
| vSphereHAHostTolerance |	vSphere HA 配置中可容忍的主機數目（等於 1 個主機） |	主機	 |1 |1 |
| HostVsanOverheadCorePercentage | vSAN 利用的主機核心數目百分比（等於 10%；若為非 vSAN 主機，則等於 0%）	| % | 10% |	0% |

公式 2：`AvailableMemory = [ HostMemory - HostOverheadMemory - HostVsanOverheadMemory - ( HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadMemory`

表 5. 公式 2 中的變數說明

| 變數	|說明              |	單位 |	vSAN 範例 | NFS 範例 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| 可供環境中工作負載和服務使用的記憶體 GB 數 | GB | 	693	| 860 |
| HostCount	| 預設叢集中的主機數目	| 主機 | 6	| 6 |
| HostMemory |	 預設叢集中每一個主機可用的原始 GB 數 |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | 此主機上每一個 vSAN 容量 SSD 磁碟容量的 GB 數（等於 960、1946 或 3891；如果沒有 vSAN，則等於 0） | GB |	960 | 0 |
| HostOverheadMemory |	ESXi 伺服器保留作為額外負擔的 GB 數（等於 4.6 GB）|	GB	| 4.6 |	4.6 |
| MgmtOverheadMemory |	vCenter Server 管理元件（vCenter Server、PSC、AD/DNS、Edges）保留的記憶體 GB 數（等於 77 GB）| GB | 77 | 77 |
| vSphereHAHostTolerance |vSphere HA 配置中可容忍的主機數目（等於 1 個主機） | 主機	|1 |1 |
| HostVsanOverheadMemoryDiskPercentage | vSAN 管理所保留的記憶體 GB 數（以其中一個容量 vSAN 磁碟的百分比表示）（等於 2.75%） |	% | 2.75%	| 2.75% |
| HostVsanOverheadMemory | vSAN 管理所保留的記憶體 GB 數（無論磁碟大小為何）（等於 7 GB；如果沒有 vSAN，則等於 0 GB）	| GB |  7	| 0 |

## 安裝 IBM Cloud Private Hosted 時的考量

請先收集必要的授權，再安裝 {{site.data.keyword.cloud_notm}} Private Hosted 服務。建議您確保授權不僅可以支援起始 {{site.data.keyword.cloud_notm}} Private Hosted 部署，還可以支援基礎架構中未來的 {{site.data.keyword.cloud_notm}} Private Hosted 大小擴充。

## 移除 IBM Cloud Private Hosted 時的考量

* {{site.data.keyword.cloud_notm}} 只會刪除 {{site.data.keyword.cloud_notm}} Private Hosted 服務起始安裝期間所部署的虛擬機器 (VM)，不會清除安裝後部署的任何節點。
* {{site.data.keyword.cloud_notm}} 將會刪除 {{site.data.keyword.cloud_notm}} Private Hosted 服務起始部署期間所建立的 VXLAN、DLR 和邊緣閘道。一旦開始移除 {{site.data.keyword.cloud_notm}} Private Hosted 服務，您部署在 VXLAN 上的 VM 就會失去連線功能。

### 相關鏈結

* [訂購 IBM Cloud Private Hosted](../services/icp_ordering.html)
* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)（PDF 下載）
* [開立 IBM Cloud Private 的問題單](https://www.ibm.com/mysupport/s/?language=en_US)

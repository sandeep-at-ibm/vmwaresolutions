---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

# VMware 元件版本的比較圖表
{: #solution-appendix}

## VMware NSX 版本比較
{: #solution-appendix-nsx-editions}

在此設計內，有多個需要授權的元件。此資訊擷取環境正確運作所需的最低授權。

表 1. 授權需求

元件                            | 用途 |授權
----------|---------|-------------
**vSphere** | 運算虛擬化 | vSphere 6.7 Enterprise Plus
**vCenter Server**
   |基礎架構管理| vCenter Server 6.7 Standard
**NSX** | 網路虛擬化 | NSX Base for Service Providers 6.4
**vSAN** | 儲存空間虛擬化 | vSAN 6.6 Advanced  

僅透過 VMware vCloud Air Network (vCAN) 提供適用於服務提供者的 NSX Base for Service Providers 版本。下表提供此版本的特性。
{:note}

表 2. VMware NSX 版本比較圖表

| NSX 特性                                      | Base |Advanced                 |Enterprise |
|-----------------------------------------------|------|----------|------------|
| 分散式交換及遞送                              | •    | •        | •          |
| NSX Edge 防火牆                               | •    | •        | •          |
| NAT                                           | •    | •        | •          |
| NSX Edge 負載平衡                             | •    | •        | •          |
| VPN (IPsec)                                   | •    | •        | •          |
| VPN (SSL)                                     | •    | •        | •          |
| API 驅動的自動化                              | •    | •        | •          |
| 與 vRealize 及 OpenStack 整合\*               | •    | •        | •          |
| 利用 vRealize 自動化安全原則                  |      | •        | •          |
| SW L2 橋接至實體環境                          |      | •        | •          |
| 利用 ECMP 的動態遞送（主動-主動）             |      | •        | •          |
| 分散式防火牆                                  |      | •        | •          |
| 與 Active Directory 整合                      |      | •        | •          |
| 伺服器活動監視                                |      | •        | •          |
| 服務插入項目（協力廠商整合）                  |      | •        | •          |
| 分散式負載平衡                                |      |          | •          |
| 跨 vCenter NSX                                |      |          | •          |
| 多站台 NSX 最佳化                             |      |          | •          |
| 遠端閘道                                      |      |          | •          |
| 與 HW VTEP 整合                               |      |          | •          |
\*僅限 L2、L3 & NSX Edge 整合。不使用安全群組

## VMware vSAN 版本比較
{: #solution-appendix-vsan-editions}

下表列出解決方案所支援之 VMware vSAN 的 **Advanced** 及 **Enterprise** 版本的可用特性。

表 3. VMware vSAN 版本比較圖表

| vSAN 特性                                       |Advanced                 |Enterprise |
|-------------------------------------------------|----------|------------|
| 儲存空間原則型管理                              | •        | •          |
| 快閃記憶體讀寫快取                              | •        | •          |
| 分散式 RAID                                     | •        | •          |
| 虛擬分散式交換器                                | •        | •          |
| 機架狀態提示                                    | •        | •          |
| vSphere 抄寫                                    | •        | •          |
| 軟體總和檢查                                    | •        | •          |
| 全快閃記憶體硬體                                | •        | •          |
| iSCSI 目標服務                                  | •        | •          |
| IOPS 限制                                       | •        | •          |
| 刪除重複及壓縮                                  | •        | •          |
| RAID-5/6 消除編碼                               | •        | •          |
| 靜止中資料加密                                  |          | •          |
| 含有本端失敗保護的延伸叢集                      |          | •          |

## 相關鏈結
{: #solution-appendix-related}

* [解決方案概觀](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [設計概觀](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [備份元件](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)

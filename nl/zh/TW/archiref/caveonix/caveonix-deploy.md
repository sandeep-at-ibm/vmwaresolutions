---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight 的部署模型
{: #caveonix-deploy}

本節說明 Caveonix RiskForesight 的部署模型以及安裝解決方案的安裝程序。

當您選取 {{site.data.keyword.vmwaresolutions_full}} RiskForesight 選項時，您不需要遵循部署中的所有步驟，因為起始步驟已自動執行。不過，若想要瞭解完整的部署和架構，以及在起始部署之後想要擴充解決方案的話，則需要詳細瞭解。

RiskForesight 安裝包含下列高階步驟：

1. [起始規劃和必要條件](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step1) - 瞭解並選取部署選項，配置 DNS 來提供應用程式元件的 FQDN/IP 解析。
2. [虛擬機器部署](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step2) - 從 OVF 範本部署 VM。VM 上已安裝所有應用程式元件。
3. [應用程式配置](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step3) - 執行 Caveonix 配置 Script，它會在每一個 VM 上配置應用程式元件。
4. [應用程式設定](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-step4) - 設定「服務提供者」及「承租戶」或「組織」，以便使用者可以存取應用程式。

自動安裝，會佈建一個 VM，並在該 VM 上配置所有應用程式元件。
{:note}

## 部署大小
{: #caveonix-deploy-sizing}

部署大小是使用下列磁區進行計算。

表 1. 磁區

|資料類型	|磁區 |
|---|---|
|每天的掃描數|1 |
|掃描資料 (MB) |20 |
|日誌資料 (MB) |500 |
|流量資料 (MB) |200 |
|資產資料 (MB) |46 |
|每天每個資產的總儲存空間 (MB)	|766 |
|資料抄寫乘數 |2 |
|總索引儲存空間 / 資產 / 天 (MB)	|1532 |

「資料抄寫乘數」設為 2，因為「索引」儲存庫（彈性搜尋）依預設使用 n+1 個索引抄寫。
{:note}

「調整 VM」數目的計算結果是來自「資產數目」及進行索引之「資料天數」。

表 2. 調整 VM 參數

|資產數目 |100	|500	|5000 |
|---|---|---|---|
|資料天數	|30	|30	| 30 |
|總索引儲存空間 / 資產 / 天 (MB)	|1532	|1532	|1532 |
|總索引儲存空間 / 資產 / 30 天 (TB)	|4	|22	|219 |
|每個調整節點支援的資料 (TB) |0	|8	|8 |
|需要的調整 VM |0	|3	|27 |

需要的儲存空間數量計算如下：

表 3. 儲存空間參數

|資產數目 |100	|500	|5000 |
|---|---|---|---|
|長期資料保留（月）|8	|8	|8 |
|每天每個資產的總儲存空間 (MB)	|766	|766	|766 |
|資料天數	|30	|30	| 30 |
|近期資料保留（月）|  7	|33	|329 |
|長期資料保留 (TB) |18	|88	|877 |

從資料的觀點來看，資料的用途如下：

-	掃描資料使用於「法規遵循管理」
-	日誌資料使用於鑑識管理
-	原則和流量資料使用於風險管理，且流量資料僅來自 NSX Manager

「資料儲存空間」有三層：

-	抄寫
-	近期
-	長期

下表提供部署的摘要：

表 4. 摘要

|部署模型 |全功能|局部分散|完全分散|
|---|---|---|---|
|資產數目 |100	|500	|5000 |
|30 天內產生的線上資料 (TB) |4	|22	|219 |
|近線資料保留（90 天）(TB) |  7	|33	|329 |
|離線資料保留（8 個月）(TB) |18	|88	|877 |
|資料儲存空間保留量總計（1 年）(TB) |28	|142	|1425 |
|基本 VM |1	|1	|20 |
|調整 VM |0	|3	|28 |
|VM 總計|1	|4	|48 |

## 相關鏈結
{: #caveonix-deploy-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

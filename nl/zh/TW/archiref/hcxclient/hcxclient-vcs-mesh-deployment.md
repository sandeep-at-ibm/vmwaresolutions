---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 內部部署服務網
{: #hcxclient-vcs-mesh-deployment}

下列區段詳細介紹了配置 HCX 用戶端實例的步驟。
  1. 為 IBM Cloud for VMware Solutions 環境進行網站配對
  2. 建立 HCX 內部部署網路設定檔
  3. 建立 HCX 內部部署運算設定檔
  4. 建立 HCX 服務網
  5. 延伸網路

## 為 IBM Cloud for VMware Solutions 環境進行網站配對
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. 登入 vSphere Web Client。
2. 從**首頁**功能表，選取 **HCX** 選項。
3. 在**基礎架構** -> **InterConnect** 下，按一下**新增網站配對**。
   1. 網站 Url：HCX Cloud Manager URL
     * 例如，`https://x.x.x.x.x`
   2. 使用者名稱及密碼：HCX Manager 管理詳細資料
     * 管理/密碼
   3. 先前的詳細資料可以從 IBM Cloud 入口網站取得，位於**服務**下，IBM Cloud for VMware 解決方案實例的 HCX on IBM Cloud**。
4. 按一下**連接**。

### 結果
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

網站配對已順利登錄並顯示在使用者介面中。

## 建立 HCX 內部部署設定檔
{: #hcxclient-vcs-mesh-deployment-profiles}

## 內部部署服務網網路設定檔
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. 登入 vSphere Web Client。
2. 從**首頁**功能表，選取 **HCX** 選項。
3. 在**基礎架構** -> **InterConnect** 下
4. 在「多站台服務網」下，按一下**網路設定檔**。
5. 從**建立網路設定檔**開始
   1. 選取分散埠群組：例如，外部
   2. 提供外部 IP 的 IP 位址範圍
   3. 提供外部子網路字首長度
   4. 提供外部閘道
   5. 提供 DNS 詳細資料
   6. 將 MTU 設定為 1500。
   7. 按一下「建立」。
6. 對管理網路和 vMotion 網路重複上述步驟。
   附註：MTU 應該設定為 9000。

## 結果
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

|網路名稱| MTU |
| -----| ----|
| 外部                                | 1500|
| 管理 |9000|
| vMotion |9000|

## 內部部署服務網運算設定檔
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. 登入 vSphere Web Client。
2. 從**首頁**功能表，選取 **HCX** 選項。
3. 在**基礎架構** -> **InterConnect** 下
4. 在「多站台服務網」下，按一下**運算設定檔**
5. 從**建立運算設定檔**開始
   1. 提供運算設定檔名稱
   2. 選取要啟用的所有服務，按一下**繼續**
   3. 選取叢集，按一下**繼續**
   4. 選取資料儲存庫，按一下**繼續**
   5. 選取「管理的網路設定檔」，按一下**繼續**
   6. 選取「外部/上行鏈路的網路設定檔」，按一下**繼續**
   7. 選取「vMotion 的網路設定檔」，按一下**繼續**
   8. 選取「vSphere 抄寫（管理）的網路設定檔」，按一下**繼續**
   9. 選取用於延伸的「分散交換器」，例如，專用交換器
   10. 按一下「完成」。

## 結果
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

已建立叢集/儲存空間組合的運算設定檔，可用於建立服務網。

## HCX 內部部署服務網
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## 內部部署服務網建立
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. 登入 vSphere Web Client。
2. 從**首頁**功能表，選取 **HCX** 選項。
3. 在**基礎架構** -> **InterConnect** 下
4. 在「多站台服務網」下，按一下**服務網**
5. 從**建立服務網**開始
   1. 選取網站；內部部署和 vCloud 組織，按一下「繼續」
   2. 選取「來源運算設定檔」
   3. 選取「遠端運算設定檔」。例如，CloudCompute。
   4. 選取「所有服務」，按一下「繼續」
   5. 在「進階配置 - 置換上行鏈路網路設定檔（選用）」頁面上，按一下「繼續」
   6. 按一下「繼續」
   7. 按一下「繼續」，在「進階配置 - 配置 WAN 最佳化服務頻寬限制」頁面上保留預設
   8. 提供服務名稱，按一下**完成**
6. 監視服務網建立的作業清單，尾端應該有三個 HCX 應用裝置位於內部部署位置，三個位於雲端位置。

## 結果
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

HCX 服務網是來源站台和目的地站台的有效 HCX 服務配置。可以將服務網新增到這兩個站台上建立的有效運算設定檔的已連線站台對組。

新增服務網會在這兩個站台上起始 HCX 交互連接虛擬應用裝置的部署。交互連接服務網一律會建立在來源站台上。

## 網路延伸
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## 延伸網路的處理程序
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

若要以 HCX 來延伸網路（VLAN 或 VXLAN），請從用戶端 vCenter Web 使用者介面完成下列步驟。

1. 登入 vSphere Web Client。
2. 從**首頁**功能表，選取 **HCX** 選項。
3. 在左側功能表中的**服務** -> **網路延伸**下
4. 按一下**延伸網路**
   1. 選取要延伸的網路
   2. 輸入 CIDR 格式的現行預設閘道及子網路遮罩。
   3. 按一下畫面底端的**延伸**，以開始網路延伸工作流程。

在 vCenter 用戶端作業窗格中監視網路進度。

## 網路延伸的概念及最佳作法
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

橋接用戶端網路至雲端 VXLAN 的中介，是一個複雜的多通道 VPN，其包含專利的 HCX 技術。它不是以 NSX 為基礎，但會與 NSX 搭配運作並延伸其功能。此處理程序是由用戶端 vCenter Web 使用者介面 (UI) 控制，它會自動部署，並同時啟動用戶端和雲端的兩個端點。選取延伸的網路可個別執行或批次處理。

此外，在網路延伸工作流程中，雲端上的 NSX 獲得授權建置 VXLAN，該 VXLAN 之後將連接至所指定雲端 L3 裝置上建立的介面（DLR 或 ESG 處於未連接狀態），以及雲端網路延伸應用裝置。

一般而言，當您移轉特定應用程式時，適用的虛擬機器 (VM) 正在使用的所有網路都必須延伸跨越 {{site.data.keyword.cloud}} 實例。

為什麼是一般而不是一律這樣？在 VM 移轉之後，從用戶端中斷特定資料流量會有幫助。例如，VM 來賓備份用戶端，這可能導致移至雲端時的高頻寬使用率。當移轉 VM 時，並不需要來賓備份用戶端，因為在雲端上會有更現代的區塊層次備份自動挑選它。

用戶端的備份網路配接卡未被存取，因為這可能表示存取每部 VM 來關閉來賓內用戶端備份排程。因此，如果使用備份網路，備份可能會失敗。這是暫時狀況，直到移轉後能呼叫到所有 VM 來停用來賓備份用戶端，此狀況才會結束。

理論上，單一網路延伸的頻寬為 4 Gbps，但是這可能是針配對單一網路延伸配對中所有延伸網路的限制，單一延伸網路是不會達到此頻寬的。假設有分配到足夠的基礎頻寬，且延遲很低（<~10 毫秒），則單一延伸網路可以達到 ~1 Gbps。

### 近似性遞送選項
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

如果沒有任何類型的遞送最佳化，則延伸網路遞送回到用戶端以存取任何 L3。這樣的拉長作用會產生沒有效率的資料流量模式，因為封包需要在用戶端（來源）與雲端之間來回傳送，即使來源與目的地 VM 都在雲端內的情況下也是如此。HCX 的「近似性遞送」特性是設計來處理這項以及資料流量的本端出口。

## 相關鏈結
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [HCX 元件和術語的名詞解釋](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [準備安裝環境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 用戶端部署](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [VMware 混合雲端移轉](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [監視參數及元件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

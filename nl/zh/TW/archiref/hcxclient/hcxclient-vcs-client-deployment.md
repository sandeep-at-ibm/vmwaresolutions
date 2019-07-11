---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 用戶端部署
{: #hcxclient-vcs-client-deployment}

最小 HCX 安裝由單一雲端和用戶端部署所組成。

假設用戶端與雲端之間有網路連線功能，HCX 用戶端可安裝在 HCX 所支援的任何 vSphere 版本上。

## 需求
{: #hcxclient-vcs-client-deployment-req}

|元件|CPU 計數|  記憶體 (GB) | 磁碟 (GB) |
|--------|--------|---------|-------|
|HCX Manager|4 | 12G |  60G |
| HCX Interconnect (HCX-IX) |4 | 3G |  2G |
| HCX Network Extension (HCX-NE) |4 | 3G |  2G |
| HCX WAN Optimizer (HCX-WAN) | 8                                   | 14G |  100G |

## 用戶端授權
{: #hcxclient-vcs-client-deployment-licensing}

HCX 是一項服務。透過 VMware 所維護的授權伺服器管理每個網站及每部虛擬機器 (VM) 的 HCX 授權。HCX 雲端和用戶端實例在其整個生命週期中需要與 VMware 登錄網站進行通訊。
- 80 和 443 的資料流量必須容許傳輸至 `https://connect.hybridity.vmware.com`
- 針對 {{site.data.keyword.vmwaresolutions_full}} 主控台提供的用戶端安裝，提供了單次使用的登錄金鑰。每一個用戶端 HCX 安裝都需要一個金鑰。

### 訂購內部部署 HCX 授權的程序
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. 在 {{site.data.keyword.vmwaresolutions_short}} 主控台中，從左導覽窗格按一下**資源**。
2. 捲動到**內部部署 HCX 授權**表格，然後按一下**佈建新的項目**。
3. 指定授權名稱。
4. 按一下適用於您的訂單的條款鏈結，並先確認您同意這些條款，然後訂購授權。
5. 按一下**佈建**。

## IP 位址需求
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

若要部署 HCX，內部部署及目標 IBM Cloud 中必須有適當的 IP 位址數目。

* vMotion 位址
  維護 vMotion 的不同網路是內部部署資料中心內的一般作法。「雲端閘道」必須具有 vMotion 網路的存取權。否則，需要有額外 IP 位址，才能與 vMotion 網路通訊。

* 內部部署
  * HCX Manager 應用裝置有一個 IP 位址。
  * 每個互聯應用裝置對應一個 IP 位址，如果有個別的 vMotion 網路，請新增一個 IP 位址。
  * 每個標準網路延伸對應一個 IP 位址

* IBM Cloud

  * 每個連接至 IBM Cloud 的 HCX Manager 應用裝置都有兩個 IP 位址。這些位址可以用來連接至網際網路或一個以上的 Direct Connect 線路。
  * 如果有不同的 vMotion 網路連線，則請新增一個。

## 用戶端 OVA 下載
{: #hcxclient-vcs-client-deployment-client-ova}

用戶端 HCX 是由使用者部署，需要對來源 vCenter 具有管理者層次許可權。在撰寫本文之際，HCX 用戶端管理程式的 ova 大約是 1.7 GB。當使用 {{site.data.keyword.vmwaresolutions_short}} 主控台來訂購 HCX，就會提供一個 URL 鏈結來下載用戶端的 HCX 版本，其符合已部署在雲端上的 HCX 版本。此鏈結在雲端 HCX Manager 使用者介面 (UI) 中提供。

也會提供單次使用登錄金鑰。請使用下列步驟來配置使用登錄。

1. 從雲端 HCX 使用者介面中所提供的鏈結，下載 HCX 用戶端（企業）OVA。
    1. 利用 IBM 請使用 HCX 登錄使用者介面來登入雲端 HCX 使用者介面。
    2. 使用雲端 vCenter ID 和密碼來登入使用者介面。
    3. 在**管理**標籤上，選取**要求下載鏈結**以下載用戶端 OVA。使用已部署 OVA 的來源 vCenter 的本端「跳轉盒」，來完成此步驟。

## 在來源上安裝及配置 HCX
{: #hcxclient-vcs-client-deployment-install-cfg-src}

內部部署安裝需要部署 HCX 管理應用裝置，並向 vCenter 環境登錄該應用裝置。

### 安裝 HCX Manager 應用裝置
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

在內部部署 vCenter 中安裝 HCX Manager 應用裝置。
1. 登入**我的 VMware**，然後從產品下載頁面下載 Hybrid Cloud Services OVA 檔案。
2. 開啟瀏覽器，並登入 vSphere Web Client。檢視**首頁**標籤。
3. 在**庫存樹狀結構**清單中，按一下**主機及叢集**。
4. 展開階層，以顯示資料中心。
5. 在目標資料中心按一下滑鼠右鍵，然後從功能表選取**部署 OVF 範本**。可能需要幾秒鐘，才會出現**部署 OVF 範本**功能表項目。
6. 選擇**部署 OVF 範本**。
  1. 選取**本端檔案**，然後按一下**瀏覽**以尋找下載至電腦的 OVA 檔案。按**下一步**。
  2. 在**檢閱詳細資料**頁面上，勾選**接受額外配置選項**方框，然後按**下一步**。
  3. 在**接受 EULA** 頁面上，向下捲動以檢閱 VMware 使用者授權合約。按一下**接受**及**下一步**。
  4. 在**選取名稱及資料夾**頁面上，視需要編輯名稱，並選取 Hybrid Cloud Services 的位置。按**下一步**。
  5. 在**選取資源**頁面上，選取安裝位置。
  6. 在**選取儲存空間**頁面上，選取 Hybrid Cloud Services 的儲存空間，然後按**下一步**。從**選取虛擬磁碟格式**清單中，您可以選取**精簡佈建**或**完整佈建**。
  7. 在**設定網路**頁面上，將 Hybrid Cloud Services 配接器對映至從**目的地**清單選擇的主機網路。
7. 在**自訂的範本**頁面上，輸入環境特定的值：
  * 針對密碼，指令行介面 (CLI) 及 Web 使用者介面的預設使用者名稱為 **admin**。需要登入 Web 使用者介面用的 **admin** 使用者及密碼，也需要具有可設定之密碼的 **root** 使用者帳戶。
  * 輸入並重新輸入 CLI **admin** 使用者密碼。
  * 輸入並重新輸入 **root** 使用者密碼。在日後，如果需要 VMware Global Support Services (GSS) 的協助，則可能需要共用此密碼，他們才能對系統進行疑難排解。
  * 針對網路內容，輸入 HCX Manager VM 的主機名稱。輸入網路 IPv4 位址、IPv4 字首 (CIDR) 及預設閘道。下表顯示範例值：

表 1. 網路內容的範例值

| 欄位                    | 值  |
|--------------------------|-----------------|
| 主機名稱 | HCM_1           |
| 網路 1 IPv4 地址   | 192.168.200.101 |
| 網路 1 IPv4 字首   | 24 |
| 預設 IPv4 閘道     | 192.168.200.1   |
| 網路 1 IPv6 位址   |                 |
| 網路 1 IPv6 字首   |                 |

8. 檢閱「vService 連結」頁面。按**下一步**繼續。
9. 在**準備完成**頁面上，遵循下列步驟：
  * 勾選**在部署之後開啟電源**方框。
  * 檢閱 Hybrid Cloud Services 設定，然後按一下**完成**。可能需要幾分鐘，才會開啟 Hybrid Cloud Services 應用裝置的電源。
  * 若要檢查狀態，請移至 vSphere Web Client 首頁，在**首頁**標籤上移至**庫存**，然後按一下**主機及叢集**。展開資料中心階層，然後按一下 Hybrid Cloud Services 服務虛擬機器，以在中心窗格內顯示摘要。
  * 檢視**摘要**標籤，主控台會顯示**已開啟電源**，而且**播放**按鈕是綠色的。
10. HCX Manager 已開啟電源並準備好向內部部署 vCenter 登錄。

## HX Manager Appliance 的初始配置
{: #hcxclient-vcs-client-deployment-inital-config}

1. 確保混合式雲端服務虛擬應用裝置具有對 `https://connect.hcx.vmware.com` 的出埠存取權
2. 使用 **admin** 登入到混合式雲端服務虛擬應用裝置管理介面 `https://<ip>:9443`
3. 提供用戶端必要條件中收集的授權碼。
4. HCX 雲端資料中心位置
    - 輸入離 HCX 雲端實例所在資料中心最近的城市。如果該城市不存在，請選取最近的主要城市。
5. 提供系統名稱

## 匯入 vSphere 伺服器憑證
{: #hcxclient-vcs-client-deployment-import-cert}

1. 登入到 HCX Manager 管理介面 `https://<ip>:9443`
2. 選取**管理**標籤，在**憑證** -> **授信 CA 憑證**下
3. 匯入 vSphere 伺服器網站
   1. 選取從 URL 匯入憑證，並鍵入 HCX 雲端登錄 URL。
     * 聖保羅：`https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## 向 vCenter/SSO/NSX 登錄 HCX Manager 的程序
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. 登入 Hybrid Cloud Services 服務虛擬應用裝置。
2. 按一下**管理設定**磚。
  1. 在左窗格的**配置系統**下，選取 vCenter。
  2. 按一下右上方的**新增 vCenter**。
  3. 輸入格式為 `https://vCenter` 或 `https://vCenter` 的 vCenter Server 的 IP 位址。
    * 例如，`https://My-vCenter` 或 `https://10.108.26.211`。
  4. 輸入 vCenter Server 使用者名稱及密碼。使用的帳戶必須有「vCenter 管理者」角色。
  5. 按一下**確定**。當顯示_您需要重新啟動應用程式_ 訊息時，請不要重新啟動。
3. 配置 SSO/查閱服務。
  6. 按一下**管理**標籤。
  7. 按一下**查閱服務 URL** 文字框旁邊的**編輯**。
  8. 以下列形式輸入查閱網路服務端點：
    * 對於 vCenter Server 6.5 `https://psc/`
  9.  必要時，提供 NSX 詳細資料。
  10. 按一下**確定**。當顯示重新啟動 Web 引擎的訊息時，請不要重新啟動。
4. 按一下**摘要**標籤，並尋找**混合管理元件**區段。停止並啟動應用程式引擎和 Web 引擎。
5. 若要終結登錄，請登出 vSphere Web Client。重新登入到 vSphere Web Client，驗證 HCX 標籤是否存在。

## 結果
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

請注意現有 **Hybrid Cloud** 圖示及左側的 **Hybrid Cloud Services** 功能表項目。Hybrid Cloud Services 登錄會更新這些標籤。在庫存中，圖示標籤會變成 **Hybrid Cloud Services**。

## 相關鏈結
{: #hcxclient-vcs-client-deployment-related}

* [HCX 元件和術語的名詞解釋](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [準備安裝環境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 內部部署服務網](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 混合雲端移轉](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [監視參數及元件](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 疑難排解](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

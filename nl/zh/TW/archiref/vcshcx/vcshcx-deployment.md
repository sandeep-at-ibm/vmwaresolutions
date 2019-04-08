---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

subcollection: vmwaresolutions


---

# 雲端及用戶端部署
{: #vcshcx-deployment}

最小 HCX 安裝由單一雲端和用戶端部署所組成。假設用戶端與雲端之間有網路連線功能，HCX 用戶端可安裝在 HCX 所支援的任何 vSphere 版本上。

## 需求
{: #vcshcx-deployment-req}

- HCX Manager - CPU 計數 4、記憶體 12G、磁碟 60G
- CGW - CPU 計數 8、記憶體 3G、磁碟 2G
- L2C - CPU 計數 8、記憶體 3G、磁碟 2G
- WAN 最佳化工具 - CPU 計數 8、記憶體 14G、磁碟 100G

## 雲端
{: #vcshcx-deployment-cloud}

雲端 HCX 部署是由 {{site.data.keyword.vmwaresolutions_full}} 自動化處理。預設配置會使用公用埠群組，來配置任何機群元件端點連線功能。雲端上的機群元件使用以公用 IP 位址配置的端點介面來部署，因為它們是安全強化的應用裝置。可以將它們部署在防火牆後面。不支援透過現有 VPN 通道，將用戶端和雲端彼此連接。如果您想要對 HCX 端點連線功能使用專用網路，您可以訂購 HCX 雲端來進行專用網路機群部署，以用於 MPLS 之類的專用鏈結。

## 用戶端
{: #vcshcx-deployment-client}

用戶端 HCX 是由使用者部署，需要對來源 vCenter 具有管理者層次權限。在撰寫本文之際，HCX 用戶端管理程式的 ova 大約是 1.7 GB。當使用 {{site.data.keyword.vmwaresolutions_short}} 主控台來訂購 HCX，就會提供一個 URL 鏈結來下載用戶端的 HCX 版本，其符合已部署在雲端上的 HCX 版本。此鏈結在雲端 HCX Manager 使用者介面 (UI) 中提供。

也會提供單次使用登錄金鑰。請使用下列步驟來配置使用登錄。

1. 從雲端 HCX 使用者介面中所提供的鏈結，下載 HCX 用戶端（企業）OVA。
    1. 利用 IBM 請使用 HCX 登錄使用者介面來登入雲端 HCX 使用者介面。
    2. 使用雲端 vCenter ID 和密碼來登入使用者介面。
    3. 在**管理**標籤上，選取**要求下載鏈結**以下載用戶端 OVA。使用已部署 OVA 的來源 vCenter 的本端「跳轉盒」，來完成此步驟。
2. 登入 vSphere C++ 用戶端（或具有能發揮作用的用戶端整合嵌入式管理單元的 Web 用戶端），並使用 vCenter 匯入精靈匯入 OVA。
    1. 請確保配置 HCX Manager 的網路同時具有來源 vCenter 及網際網路的存取權。  
    2. 系統提示時，請輸入登錄金鑰。（如果您有用戶端工具嵌入式管理單元設定程式，請使用此 Web 用戶端。）  
3. 登出再登入 vCenter Web 用戶端。**HCX** 功能表選項圖示會顯示在主畫面功能表下。
4. 如果是自簽憑證，請選取 HCX 功能表項目來存取 HCX 嵌入式管理單元使用者介面。選取**管理**標籤。
    1. 選取這個項目，可從 HCX 的 {{site.data.keyword.vmwaresolutions_short}} 主控台所提供的 HCX 雲端登錄 URL 中的 URL 和金鑰匯入憑證。
    2. 在**儀表板**標籤內的**網站配對**窗格中，選取**新建網站配對**。
    3. 遵循提示並提供 HCX 雲端登錄 URL 及雲端 vCenter 管理者 ID 及密碼。
    4. 繼續遵循網站登錄精靈中的提示來配置「機群」元件，包括「雲端閘道」、「第 2 層集中器」及「WAN 最佳化工具」。  

若為用戶端，請使用**作業**功能表來監視「機群」元件的部署。若為雲端部署，請針對特定 vCenter Server 實例，使用 vCenter Web 使用者介面中的**作業**功能表。

如果任一端發生部署失敗，則會取消並刪除機群元件部署。判斷失敗原因之後，請按一下用戶端中 HCX vCenter Web 使用者介面的**交互連接**標籤，然後選取畫面頂端的**安裝 HCX 元件**。

順利部署機群元件並經過幾分鐘之後，**交互連接**標籤中的 CGW 及 L2C 元件的通道狀態會顯示為**啟動**。

## 相關鏈結
{: #vcshcx-deployment-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

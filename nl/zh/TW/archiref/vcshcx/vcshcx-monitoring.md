---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-05"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 監視參數及元件
{: #vcshcx-monitoring}

## 使用 WAN 最佳化工具來監視
{: #vcshcx-monitoring-using-wan}

Silver Peak WAN 最佳化應用裝置是部署為 HCX 的一部分，它未配置其管理介面。當您要評量出資料傳輸量和節流控制網路移轉頻寬用量的基準線時，Web 使用者介面 (UI) 是一個可用的重要工具。

只有 HCX CGW 閘道 WAN 通道資料流量會流經 WAN 最佳化工具應用裝置。因此，它無法監視延伸 L2 資料流量。
{:note}

### 配置使用者介面
{: #vcshcx-monitoring-config-ui}

除非受到 {{site.data.keyword.IBM}} 或 VMware 支援人員指示，否則，除了配置 Web 使用者介面的 IP 位址之外，請勿對 WAN 最佳化工具應用裝置進行配置變更。   

若要配置「WAN 最佳化工具」Web 使用者介面，請執行下列動作：
1.	在 vCenter 用戶端內尋找 WAN 最佳化工具虛擬機器 (VM) 應用裝置。
2.	將主控台開啟至使用 vCenter 用戶端的 VM。
3.	在主控台內，按一下 **F4** 以配置管理介面。
4.	選取以配置靜態 IP。
5.	在管理 {{site.data.keyword.cloud}} 指派的可攜式 IP 範圍及預設閘道上使用 IP 位址。
6.	按下一個畫面上的**套用**以儲存。
7.  按一下以編輯 vCenter 主控台內的 WAN 最佳化工具 VM 的設定。
8.	選取**開啟電源時連線**和**網路配接卡 1 連線**。
9.	按一下**確定**以儲存。
10.	在 vCenter 中尋找 CGW-<xxx>-WANOPT。
11.	編輯 VM 上的設定。
12.	按一下勾選框以連接網路配接卡 1。
13.	按一下**確定**。
14.	移至 `https://<configured_WAN_OPT_IP>`.
15.	使用 `admin` 預設使用者及 `admin` 密碼登入。

您現在可以使用 WAN 最佳化工具 Web 使用者介面監視傳輸率、壓縮比例，以及設定頻寬限制。

### 移轉頻寬節流控制
{: #vcshcx-monitoring-mig-bandwidth}

在移轉 VM 之前，先對所使用的網路鏈結執行評量。與網路工程師一起處理包含 vSphere 來源實例的網路，或檢閱每週及每月資料流量使用情形。如果資料流量遍訪您企業的重要鏈結，尤其該鏈結小於 1 Gbps 時，請限制用於移轉的可用頻寬。請使用頻寬受最大限制的那一端，通常是用戶端。

當您在 HCX 用戶端使用者介面中部署機群元件時，請這麼做，但後置部署需要您進入 WAN 最佳化工具使用者介面。

如果您從 HCX Web 使用者介面重新部署 HCX CGW，則會失去變更。
這只會對移轉資料流量設定頻寬限制。延伸 L2 資料流量不受此設定的影響。{:note}

1. 登入 WAN 最佳化工具 Web 使用者介面。
2. 從**配置**標籤中，選取下拉功能表中的**調整功能**。
3. 在**頻寬上限**方框中，設定 WAN 最佳化工具應用裝置可用的頻寬上限。請勿超出 WAN 鏈結的頻寬上限。若要以 Mbps 為單位來設定值，請乘以 1,000。若要以 Gbps 為單位來設定值，請乘以 1,000,000。預設值為 10 Gbps (10,000,000 Kbps)。
4. 按一下**套用**。

以延伸 L2 頻寬節流控制而言，針對 L2C 應用裝置之間的通道資料流量，可以對 UDP 500 和 4500 採用 Qos（服務品質）。

## 監視 HCX 元件
{: #vcshcx-monitoring-hcx-comp}

利用下列方式來監視 HCX 元件，例如 HCX Manager、「雲端閘道」、「WAN 最佳化工具」和「第 2 層集中器」作業：

- 配置 HCX Manager 將日誌傳送至 syslog 伺服器。使用 HCX Manager 應用裝置管理公用程式來執行 `https://<hcxhostname or
IP>:9443` 指令。
- 針對每一個延伸 L2 網路，對網路擺盪之前移轉的 VM 設定連線測試。
- 使用 VMware vRealize Operations Manager 或其他 VMware VM 監視工具來監視 HCX 元件 VM 性能。

## 頻寬使用
{: #vcshcx-monitoring-band-use}

請使用下列方法來監視頻寬的使用和延遲。

- 使用 WAN 最佳化工具 Web 使用者介面最能達成 vMotion Traffic。WAN 最佳化工具會大幅減少發生在 WAN 上的資料流量，並傳送備用封包來減少封包流失。我們發現，典型的 LAN 到 WAN 頻寬使用比例大約為 3:1 (350 Mbps LAN = 90-120Mbps WAN)。

- 在 HCX 內以抄寫方式（大量）移轉 VM 會導致完整佈建移動 VM。這並非我們所樂見，WAN 最佳化工具使用者介面會在您移動未使用的磁碟資料時，顯示 LAN 與 WAN 之間有很高使用率。反之，我們發現，在移轉不可壓縮的資料時，例如 DB 資料和數位媒體，WAN 使用率會達到最高，並接近 LAN 使用率。

觀察：
- 在 HCX 內 VM 的 vMotion 移轉產生的傳輸量，不會超過單一 ESXi 主機的 vMotion 網路傳輸量。
- 因為大量移轉可能同步飛快進行多項移轉，它達到的頻寬使用會比 vMotion 移轉還要高。在具有 1 Gbps vMotion 鏈結至 ESX 主機的客戶端觀察到的比例為：8 個抄寫 = 頻寬使用 1 個 vMotion。
- 在磁碟上移動空的空間，會導致顯示高 LAN 使用率，其 WAN 使用率先高後低。請注意，1 Gbps 似乎是限制。實際上，在這種特殊情況下，vMotion 網路只能有 1 Gbps，這就是瓶頸。
- 以 vMotion 移轉多個 TB Oracle DB。當 WAN 鏈結為 1 Gbps 時，此限制為 vMotion 網路 1 Gbps。

## 延伸第 2 層資料流量
{: #vcshcx-monitoring-stretched-layer-2-traffic}

HCX 機群元件第 2 層集中器對於所遍訪的所有 L2 網路資料流量具有大約 4 Gbps 的頻寬限制。視資料流量類型而定，個別延伸網路的頻寬限制大約為 1 Gbps 或更小。單一 L2C 配對可以有許多個延伸 L2 網路（每個 L2C 配對理論上可容許的上限為 4096 個網路）。L2C 的設計是為了偵測及保護小型資料流量不被相同 L2C 配對內的大型資料流量壓倒，但是識別是否發生此狀況，並啟動更多 L2C 來增加整體頻寬功能會有幫助。

當客戶站台與 {{site.data.keyword.cloud}} 之間存在多個路徑時（例如直接鏈結和網際網路），部署多個 L2C 會有幫助。在多個 L2C 配對之間，單一網路無法提供備援或增加頻寬。

監視使用 L2C VM 監視標籤的所有介面之間的資料流量。如果總資料傳送速率接近 8 Gbps（4 Gbps 輸入 / 輸出），請考慮新增另一個 L2 配對，然後重新配送延伸網路來重新平衡。

## 相關鏈結
{: #vcshcx-monitoring-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

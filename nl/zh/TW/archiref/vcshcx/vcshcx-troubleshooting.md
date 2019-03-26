---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

# HCX 疑難排解
{: #vcshcx-troubleshooting}

請檢閱關於常見 HCX 問題和解決方法的資訊。

## HCX 用戶端使用者介面問題
{: #vcshcx-troubleshooting-hcx-client-issues}

### HCX 使用者介面記號逾時
{: #vcshcx-troubleshooting-hcx-ui-issues}

一般而言，如果 vCenter 使用者介面 (UI) 已保持開啟一段時間，您可能會在 HCX 使用者介面中遭遇到逾時。這是因為 HCX Manager 伺服器的登入記號已逾時。請登出 vSphere Web 使用者介面後再登入，以重新整理該記號。

### HCX 用戶端使用者介面在儀表板畫面上顯示所有度量為“NaN”
{: #vcshcx-troubleshooting-nan-display}

這個問題與目前登入的 vCenter 帳戶的許可權有關。請確定 HCX 雲端應用裝置管理程式使用者介面中已設定「企業管理者」群組。

## 移轉問題
{: #vcshcx-troubleshooting-mig-issues}

HCX 現行版本的移轉問題通常分成三大類：授權、雲端閘道網路連線及目的地硬體相容性。

### 授權
{: #vcshcx-troubleshooting-licensing}

如果由於授權問題而導致移轉失敗，HCX 的現行版本會在 vCenter 使用者介面內使用用戶端 Web 使用者介面，以錯誤訊息明確顯示此失敗。

### 網路 (WAN) 連線功能
{: #vcshcx-troubleshooting-wan-connect}

如果 WAN 連線發生問題，請一律檢查 HCX 使用者介面內的**交互連接 -> HCX 元件**畫面的通道狀態。通常不需要重設或重新啟動機群元件。如果已還原 WAN 連線功能，則會自動重新連接。

如果有已套用至 HCX Manager（用戶端和雲端）的修正程式和更新項目，且那些更新項目也修補機群元件的問題，則您必須重新部署「雲端閘道」及任何已部署的 L2C。透過 SSH 用戶端（例如 ccli）連接至 HCX Manager，可以執行進一步的通道狀態除錯  

1. 使用 admin 帳戶和提供的密碼以 SSH 連接到 HCX Manager。
2. 執行 `su -` 指令並輸入 `root` 使用者的密碼（與 admin 密碼相同），來變更為 root。
3. 將目錄切換至 `/opt/vmware/bin`，並執行 `./ccli` 指令。如果因為環境不是針對 root 設定而未成功，請執行 `./ccliSetup.pl` 指令。
4. 在 `ccli` Shell 內執行 `list` 指令來列出向 HCX Manager 登錄的機群元件。
5. 輸入針對機群元件列出的 ID，來指定 `ccli` 的機群 ID。例如，`go 8`。
6. 執行 `debug remoteaccess enable` 指令，來使用 SSH 連接到所要的機群元件。
7. 結束 `ccli` 並使用 SSH 來連接至已啟用 SSH 的機群元件的 IP 位址。
9. 繼續進行疑難排解。
10. 回到 `ccli`，然後對元件停用 `ssh` 服務。
11. 必要的話，請使用 `hc` ccli 指令，對元件執行性能檢查。

## 目的地硬體相容性問題
{: #vcshcx-troubleshooting-hw-compatibility}

如果用戶端來源端的硬體版本和 vSphere 版本比雲端還要新，則 vMotion 移轉可能會有問題。由於抄寫型移轉會將資料複製到目的端新建的虛擬機器 (VM)，因此將移轉類型變更為「大量移轉」，在大部分情況下，移轉作業應該會成功。

## 延伸 L2 集中器問題
{: #vcshcx-troubleshooting-stretched-l2}

「L2 集中器 (L2C)」作業至今很少發生問題。與 CGW 類似，如果 L2C 失去連線，當網路連線功能還原之後，它會自動重新連接。使用 ccli Shell 來檢查性能和作業。在啟用 SSH 且已連接 L2C 之後，請執行 `ip tunnel` 及 `ip link |grep t_` 指令，以檢視通道的狀態。

## 相關鏈結
{: #vcshcx-troubleshooting-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

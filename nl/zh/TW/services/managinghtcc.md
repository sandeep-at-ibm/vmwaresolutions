---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: HTCC WebGUI, HTCC console, enable internet HTCC

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 HyTrust CloudControl on IBM Cloud
{: #managinghtcc}

若要管理 HyTrust CloudControl on {{site.data.keyword.cloud}} 服務 (HTCC)，請從 {{site.data.keyword.vmwaresolutions_short}} 主控台存取 HTCC WebGUI，或從 vSphere Web Client 存取 HTCC 主控台。

## 從 IBM Cloud for VMware Solutions 主控台存取 HyTrust CloudControl WebGUI
{: #managinghtcc-accessing-webgui}

若要登入主要或次要 HTCC 應用裝置的 WebGUI，請使用在 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的 WebGUI 認證。

## 從 vSphere Web Client 存取 HyTrust CloudControl 主控台
{: #managinghtcc-accessing-console}

若要從 vSphere Web Client 存取 HTCC 主控台，請使用下列程序：
1. 在 vSphere Web Client 中，找到名為 **CC1** 和 **CC2** 的虛擬機器。
2. 以滑鼠右鍵按一下 **CC1** 或 **CC2**，然後按一下**開啟主控台**。
3. 使用您可以在 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的主控台認證，登入主控台。

如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 為 HyTrust CloudControl VM 啟用網際網路存取
{: #managinghtcc-internet-access}

對於 HTCC 5.5.1 和更高版本，{{site.data.keyword.vmwaresolutions_short}} 為已啟用「回撥」特性的 HyTrust 授權提供自動更新支援。對於不是僅專用的 vCenter Server 實例，HTCC 使用防火牆和 SNAT（來源網址轉換）規則進行部署，這些規則是在管理服務 ESG **mgmt-nsx-edge** 上定義的。

這些規則容許您為 HyTrust 虛擬機器 (VM) 啟用網際網路存取。如果未啟用網際網路存取，套用至您 HTCC 安裝的授權將在一年後到期。

對於僅限專用的 vCenter Server 環境，未新增 VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge**，因此未定義防火牆及 SNAT 規則。因此，無法針對僅限專用的實例啟用網際網路連線功能，HyTrust 授權會每年到期。
{:note}

### 尋找所定義之防火牆及 SNAT 規則的程序
{: #managinghtcc-proc-find-firewall}

1. 登入 VMware vSphere Web Client (FLEX) 並找到 ESG **mgmt-nsx-edge**。
2. 按一下**首頁 > 網路與安全 > NSX Edge**。
3. 按兩下 ESG **mgmt-nsx-edge** 並按一下**管理**標籤。
4. 前往**防火牆**標籤並找到 HyTrust 規則。記下來源 IP 位址。這些是 HyTrust VM 的 IP 位址。
5. 前往 **NAT** 標籤並找到為 HyTrust VM 建立的 SNAT 規則。來源 IP 位址將符合您在前一步驟中記下的 IP 位址。

### 啟用 HTCC 網際網路連線功能的程序
{: #managinghtcc-enable-internet}

下列步驟適用於更新用於授權升級的主要虛擬機器 (VM) 上的 HTCC 網路設定。無需更新次要 VM 的設定。
{:note}

1. 完成上一個程序中的步驟 1-3。
2. 按一下**設定**，然後按一下**介面**。記下專用上行鏈路的 IP 位址，這將成為新的預設閘道。
3. 移至 HyTrust CloudControl on IBM Cloud 服務詳細資料頁面，按一下**檢視 HTCC Web 使用者介面**，然後使用服務詳細資料頁面中的認證登入。
4. 記下現有預設閘道。例如，對於 HTCC 5.5.1，按一下**配置 > 網路**。記下列出的閘道 IP 位址，這將成為靜態路徑的閘道。
5. 新增靜態路徑。例如，對於 HTCC 5.5.1，按一下**配置 > 靜態路徑**。按一下**新增**，輸入下列資訊，然後按一下**確定**。

  ```
  網址：10.0.0.0
  遮罩：255.0.0.0
  閘道：步驟 4 中記下的 IP
  裝置：網路 1
  ```

6. 變更預設閘道。例如，對於 HTCC 5.5.1，按一下**配置 > 網路**，並將**閘道**欄位中的 IP 位址取代為您在步驟 3 中記下的位址，然後按一下**儲存**。

  請務必在變更預設閘道之前設定靜態路徑，否則可能無法到達 Web 主控台。
  {:important}

  主要 VM 現在就可以存取網際網路了。

7. 若要確認主要 VM 能存取網際網路，請對公用 IP 位址或網站執行 `wget` 指令。若要這麼做，請回到 vCenter 並用滑鼠右鍵按一下 **CC1 > 開啟主控台**。使用 HyTrust CloudControl on IBM Cloud 服務詳細資料頁面的主控台認證登入到主控台。執行 `wget` 指令（例如 `wget www.ibm.com`），您應該會立即獲得回應。請確認已傳送要求，且收到 `200` 回應。

## 相關鏈結
{: #managinghtcc-related}

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 網站](https://www.hytrust.com/){:external}

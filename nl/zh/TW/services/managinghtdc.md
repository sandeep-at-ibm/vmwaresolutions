---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: HTDC WebGUI, HTDC console, enable internet HTDC

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 HyTrust DataControl on IBM Cloud
{: #managinghtdc}

若要管理 HyTrust DataControl on {{site.data.keyword.cloud}} 服務 (HTDC)，請從 {{site.data.keyword.vmwaresolutions_short}} 主控台存取 HTDC WebGUI，或從 vSphere Web Client 存取 HTDC 主控台。

## 從 IBM Cloud for VMware Solutions 主控台存取 HyTrust DataControl WebGUI
{: #managinghtdc-accessing-webgui}

若要登入主要或次要 HTDC 應用裝置的 WebGUI，請使用在 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的 WebGUI 認證。

## 從 vSphere Web Client 存取 HyTrust DataControl 主控台
{: #managinghtdc-accessing-console}

若要從 vSphere Web Client 存取 HTDC 主控台，請使用下列程序：
1. 在 vSphere Web Client 中，找到名為 **KC1** 和 **KC2** 的虛擬機器。
2. 以滑鼠右鍵按一下 **KC1** 或 **KC2**，然後按一下**開啟主控台**。
3. 使用您可以在 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的主控台認證，登入主控台。

如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 為 HyTrust DataControl VM 啟用網際網路存取
{: #managinghtdc-internet-access}

對於 HTDC 4.3.2 和更高版本，{{site.data.keyword.vmwaresolutions_short}} 為已啟用「回撥」特性的 HyTrust 授權提供自動更新支援。對於不是僅專用的 vCenter Server 實例，HTDC 使用防火牆和 SNAT（來源網址轉換）規則進行部署，這些規則是在管理服務 ESG **mgmt-nsx-edge** 上定義的。

這些規則容許您為 HyTrust 虛擬機器 (VM) 啟用網際網路存取。如果未啟用網際網路存取，則套用於 HTDC 安裝的授權將在一年後到期。

對於僅限專用的 vCenter Server 環境，未新增 VMware NSX Edge Services Gateway (ESG) **mgmt-nsx-edge**，因此未定義防火牆及 SNAT 規則。因此，無法針對僅限專用的實例啟用網際網路連線功能，HyTrust 授權會每年到期。
{:note}

### 尋找所定義之防火牆及 SNAT 規則的程序
{: #managinghtdc-proc-find-firewall}

1. 登入 VMware vSphere Web Client (FLEX) 並找到 ESG **mgmt-nsx-edge**。
2. 按一下**首頁 > 網路與安全 > NSX Edge**。
3. 按兩下 ESG **mgmt-nsx-edge** 並按一下**管理**標籤。
4. 前往**防火牆**標籤並找到 HyTrust 規則。記下來源 IP 位址。這些是 HyTrust VM 的 IP 位址。
5. 前往 **NAT** 標籤並找到為 HyTrust VM 建立的 SNAT 規則。來源 IP 位址將符合您在前一步驟中記下的 IP 位址。

### 啟用 HTDC 網際網路連線功能的程序
{: #managinghtdc-proc-enable-internet}

1. 完成前一個程序中的步驟 1 - 3。
2. 按一下**設定**、**介面**。記下專用上行鏈路的 IP 位址。這個位址變成新的預設閘道。
3. 按一下**首頁 > 主機及叢集**，並找到 HyTrust VM。在其中一個 VM 按一下滑鼠右鍵，然後按一下**開啟主控台**。
4. 使用可在 {{site.data.keyword.vmwaresolutions_short}} 主控台上的 HyTrust DataControl on IBM Cloud 服務詳細資料頁面上找到的主控台認證，登入到主控台。
5. 若要從 VM 取得現行預設閘道 IP 位址，請按一下**管理網路設定 > 顯示現行網路配置**。記下針對**閘道**列出的 IP 位址。此位址將成為用於靜態路徑的閘道。
6. 若要設定 VM 的靜態路徑，請按一下**管理網路設定 > 管理靜態路徑 > 新增靜態路徑**。將**網址**設定為 `10.0.0.0/8`，將**閘道**設定為前一步驟中記下的 IP 位址。
7. 若要設定 VM 的預設閘道 IP，請按一下**管理網路設定 > 顯示現行網路配置**。如果得到警告訊息，請按一下**確定**，然後按一下**自訂配置**。將**閘道**欄位設定為步驟 2 中記下的專用上行鏈路 IP 位址，然後按一下**確定**。等待直到新的網路配置已安裝且網路服務已重新啟動。
8. 如果您看到訊息，要求 HyTrust SecureOS 重新鑑別，請按一下**確定**，並輸入此安裝之另一台 HyTrust VM 的 IP 位址。如果系統要求您輸入 16 個字元的通行詞組，請按 Enter 鍵回到主功能表。驗證現行網路配置，以確保您的變更已套用。
9. 若要確認 VM 能存取網際網路，請對公用 IP 位址或網站執行連線測試 (ping)。按一下**管理網路設定 > 網路診斷工具 > Ping 另一台伺服器**。鍵入公用網站位址，例如 `www.ibm.com`，按一下**確定**，然後等待顯示訊息，例如 `www.ibm.com responds to ping`。
10. 針對另一台 HyTrust VM 重複步驟 3 - 9。


## 相關鏈結
{: #managinghtdc-related}

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 網站](https://www.hytrust.com/)

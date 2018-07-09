---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-20"

---

# 訂購 VMware HCX on IBM Cloud

您可以在訂購包含服務的新 VMware vCenter Server with Hybridity Bundle 實例時，同時訂購 VMware HCX on {{site.data.keyword.cloud_notm}} 服務，或將服務新增至現有實例。

## 為新實例訂購 VMware HCX on IBM Cloud

若要訂購包含 VMware HCX on {{site.data.keyword.cloud_notm}} 的新 VMware vCenter Server on IBM Cloud with Hybridity Bundle 實例，當您從 {{site.data.keyword.vmwaresolutions_full}} 主控台訂購實例時，請選取**服務**區段中的 **VMware HCX on IBM Cloud**。


## 為現有實例訂購 VMware HCX on IBM Cloud

若要將 VMware HCX on {{site.data.keyword.cloud_notm}} 服務新增至現有 VMware vCenter Server on IBM Cloud with Hybridity Bundle 實例，請檢視您要為其新增服務的實例，按一下左導覽窗格上的**服務**，然後按一下**新增服務**。

## VMware HCX on IBM Cloud 配置

若要在 {{site.data.keyword.cloud_notm}} 上安裝 HCX，請完成下列設定：
1. 選取下列其中一個選項，以指定 **HCX 交互連接類型**：
  * **公用網路**：HCX 會透過公用網路建立站台之間的已加密連線。
  * **專用網路**：HCX 會透過專用網路建立站台之間的已加密連線。
2. 指定**公用端點憑證類型**。如果您選取 **CA 憑證**，請配置下列設定：
  * **憑證內容**：輸入 CA 憑證的內容。
  * **私密金鑰**：輸入 CA 憑證的私密金鑰。
  * （選用）**密碼**：如果私密金鑰已加密，請輸入密碼。
  * （選用）**重新輸入密碼**：再次輸入私密金鑰的密碼。
  * （選用）**主機名稱**：要對映至 CA 憑證通用名稱 (CN) 的主機名稱。HCX on {{site.data.keyword.cloud_notm}} 要求 NSX Edge 必須接受 CA 憑證的格式。如需 NSX Edge 憑證格式的相關資訊，請參閱 [Importing SSL Certificates](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html)。
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## HCX on IBM Cloud 的部署處理程序

自動部署 HCX on {{site.data.keyword.cloud_notm}}。不論您要訂購包含此服務的 vCenter Server with Hybridity Bundle 實例，還是稍後將服務部署至實例，下列步驟都會透過 {{site.data.keyword.vmwaresolutions_short}} 自動化處理程序完成：
1. 從 {{site.data.keyword.cloud_notm}} 基礎架構訂購三個 HCX 的子網路：
   * 一個專用可攜式子網路，以進行 HCX 管理。
   * 一個專用可攜式子網路，以進行 HCX 交互連接（如果針對 **HCX 交互連接類型**選取**專用網路**）。
   * 一個公用可攜式子網路，以進行 HCX 交互連接（如果針對 **HCX 交互連接類型**選取**公用網路**）。這個子網路也用於使用 VMware 啟動及維護。

   **重要事項：**針對 HCX 訂購之子網路中的 IP 位址，是要供 VMware on {{site.data.keyword.cloud_notm}} 自動化進行管理。這些 IP 位址無法指派給您建立的 VMware 資源（例如 VM 及 NSX Edge）。如果您需要 VMware 構件的其他 IP 位址，則必須從 {{site.data.keyword.cloud_notm}} 訂購自己的子網路。
2. 如果已針對 **HCX 交互連接類型**選取了**專用網路**，即會在專用「分散式虛擬交換器 (DVS)」上建立一個名為 **SDDC-DPortGroup-HCX-Private** 的埠群組。
3. 從 VMware 訂購 HCX 啟動金鑰。
4. 為 HCX 建立三個資源儲存區及 VM 資料夾，而 HCX 交互連接、本端 HCX 元件及遠端 HCX 元件需要這些資源儲存區及 VM 資料夾。
5. 針對 HCX 管理資料流量，部署及配置一組「VMware NSX Edge Services 閘道 (ESG)」：
   * 使用訂購的子網路來配置公用及專用上行鏈路介面。
   * 將 ESG 配置為一組啟用「高可用性 (HA)」的額外大型邊緣應用裝置。
   * 配置防火牆規則及網址轉換 (NAT) 規則，以容許與 HCX Manager 之間往返的入埠及出埠 HTTPS 資料流量。
   * 配置負載平衡器規則及資源儲存區。這些規則是資源儲存區，用來將 HCX 相關入埠資料流量轉遞至 HCX Manager、vCenter Server 及 Platform Services Controller (PSC) 的適當虛擬應用裝置。
   * 套用 SSL 憑證，以加密來自 ESG 的 HCX 相關入埠 HTTPS 資料流量。

   **重要事項**：HCX 管理邊緣專用於內部部署 HCX 元件與雲端 HCX 元件之間的 HCX 管理資料流量。請不要修改 HCX 管理邊緣，或對 HCX 網路延伸使用它。請改為建立網路延伸的個別邊緣。此外，請注意，使用防火牆或停用與專用 IBM 管理元件或公用網際網路的 HCX 管理邊緣通訊，可能會對 HCX 功能造成負面影響。

6. 部署、啟動及配置 HCX Manager on {{site.data.keyword.cloud_notm}}：
   * 向 vCenter Server 登錄 HCX Manager。
   * 配置 HCX Manager、vCenter Server、PSC 及 NSX Manager。
   * 配置 HCX 機群。
   * 配置本端及遠端 HCX 部署容器。
7. 向 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的 DNS 伺服器登錄 HCX Manager 的主機名稱及 IP 位址。

## 相關鏈結

* [HCX on {{site.data.keyword.cloud_notm}} 概觀](hcx_considerations.html)
* [管理 HCX on {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [訂購、檢視及移除 vCenter Server with Hybridity Bundle 實例的服務](../vcenter/vc_hybrid_addingremovingservices.html)
* [HCX 術語名詞解釋](hcx_glossary.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension 概觀](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 文件](https://hcx.vmware.com/#vm-documentation)

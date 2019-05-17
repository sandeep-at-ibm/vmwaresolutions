---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---
# 在來源上安裝及配置 HCX
{: #hcx-archi-install-cfg-src}

內部部署安裝需要部署 HCX 管理應用裝置，並向 vCenter 及一個以上已啟用 VCS HCX 功能的雲端端點進行登錄。

## 安裝 HCX Manager 應用裝置
{: #hcx-archi-install-cfg-src-install-hma}

在內部部署 vCenter 中安裝 HCX Manager 應用裝置。

1. 登入**我的 VMware**，然後從產品下載頁面下載 Hybrid Cloud Services OVA 檔案。
2. 開啟瀏覽器，並登入 vSphere Web Client。無法從 vSphere Client 執行此作業。檢視**首頁**標籤。
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
10. HCX Manager 已開啟電源，並準備好向 vCenter 進行登錄。

## 相關鏈結
{: #hcx-archi-install-cfg-src-related}

* [準備安裝環境](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-prep-install)

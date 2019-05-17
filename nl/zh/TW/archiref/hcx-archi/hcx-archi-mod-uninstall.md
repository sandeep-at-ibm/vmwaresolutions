---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 修改或解除安裝 HCX
{: #hcx-archi-mod-uninstall}

可以升級現有安裝，或者可以移除部分或所有 Hybrid Cloud Services 部署。

##  解除延伸第 2 層網路
{: #hcx-archi-mod-uninstall-unstretch-layer2}

需要先解除延伸第 2 層網路，然後再移除關聯的第 2 層集中器服務虛擬應用裝置，或解除安裝 Hybrid Cloud Services。

1. 檢查延伸網路。
2. 從 Hybrid Cloud Services 外掛程式頁面中，檢視「混合式服務」標籤，以及檢查「網路延伸服務」區段。如果正在進行作用中或排定的工作，請等待它們完成，或先予以停止，再繼續。
3. 若要移除網路，請按一下右側的「刪除（紅色 X）」圖示。
4. 按一下**確定**以確認。

## 解除安裝 HCX 虛擬應用裝置
{: #hcx-archi-mod-uninstall-uninst-hva}

為了準備解除安裝 Hybrid Cloud Services，或基於安裝架構中的變更，可能會解除安裝服務應用裝置。使用 Hybrid Cloud Services 來管理應用裝置，如下列程序所述。

### HCX 虛擬應用裝置的解除安裝必要條件
{: #hcx-archi-mod-uninstall-prereq-uninst-hva}

* 針對任何可能在解除安裝作業期間發生的移轉，取消或重設執行時間。
* 為任何執行中移轉檢查 vSphere Web Client 作業主控台，並等待它們完成。
* 確定沒有任何類型的作用中 Hybrid Cloud Services 作業。

永遠不要從 vSphere 庫存刪除虛擬應用裝置。請一律使用管理入口網站，以與服務虛擬應用裝置互動。
{:note}

### HCX 虛擬應用裝置的解除安裝程序
{: #hcx-archi-mod-uninstall-proc-uninst-hva}

1. 在 vSphere Web Client 介面中，從左窗格選取 Hybrid Cloud Services 外掛程式。
2. 在中心窗格中，按一下**混合式服務**標籤。
3. 找到「混合式雲端閘道」應用裝置，然後按一下項目以顯示詳細資料。
4. 在右下方，按一下「刪除」圖示以移除應用裝置。
5. 如果延伸網路未與「混合式雲端閘道」共用 IP 位址，則必須將它個別移除。展開「網路延伸服務」詳細資料，然後按一下「刪除」圖示以移除「第 2 層集中器」。

即會從 vCenter 及 VCS Hybrid Cloud Services Cloud 中移除「混合式雲端閘道」以及任何使用「混合式雲端閘道」的混合式服務虛擬應用裝置。

## 解除安裝 HCX Manager
{: #hcx-archi-mod-uninstall-unist-hcxm}

應該先解除安裝 HCX Manager 應用裝置，然後再從內部部署資料中心移除 HCX 解決方案。請遵循下列步驟，以解除安裝 Hybrid Cloud Services 虛擬機器。

1. 解除延伸所有第 2 層網路。
2. 移除混合式服務虛擬應用裝置。
3. 在內部部署 vCenter 中，關閉 Hybrid Cloud Services 虛擬機器的電源。
4. 刪除 Hybrid Cloud Services 虛擬機器。

即會移除所有虛擬服務應用裝置。可能會留下下列元素：
* 日誌
* 移轉 VM

### 下一步
{: #hcx-archi-mod-uninstall-what-next}

可以手動備份或刪除移轉 VM 及日誌。

## 登入 HCX 管理入口網站
{: #hcx-archi-mod-uninstall-log-hcxmp}

可以使用瀏覽器型使用者介面，從「管理入口網站」管理 Hybrid Cloud Services 部署。

1. 在 Web 瀏覽器中，輸入指派給 Hybrid Cloud Services 的 IP 位址，然後指定埠號 9443。例如，`https://HCXip:9443`。
2. 使用 SSL，在 Web 瀏覽器視窗中開啟 Hybrid Cloud Services 使用者介面。必要的話，請接受安全憑證。即會開啟 VMware Hybridity and Networking 登入畫面。
3. 輸入使用者名稱及密碼。依預設，使用者名稱為 Admin。密碼為安裝 Hybrid Cloud Services 虛擬應用裝置時所提供的值。

## 相關鏈結
{: #hcx-archi-mod-uninstall-related}

* [HCX on IBM Cloud 疑難排解](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-trbl)

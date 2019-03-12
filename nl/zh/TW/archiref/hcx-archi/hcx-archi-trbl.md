---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# HCX on IBM Cloud 疑難排解
{: #hcx-archi-trbl}

## 雲端登錄失敗
{: #hcx-archi-trbl-cloud-reg}

* 如果認證不正確，則 Hybrid Cloud Services 不會重試。認證必須在 Hybrid Cloud Services 嘗試登入並啟動雲端登錄之前鑑別。
* 如果認證拼寫錯誤，或 VCF/VCS Hybrid Cloud Services Cloud 認證在 Hybrid Cloud Services 向 VCF/VCS Hybrid Cloud Services Cloud 登錄之後變更因而導致不符，則雲端登錄可能會失敗。
* 若要更新 Web 用戶端中的認證，請移至 Hybrid Cloud Services「開始使用」標籤，然後在**基本作業**下選擇**登錄新雲端**。

## 重複 MAC 位址
{: #hcx-archi-trbl-dupl-mac-addr}

移轉之後，虛擬機器之間可能會發生通訊問題。在移轉期間保留 MAC 位址時，可能會不小心地建立重複 MAC 位址。

可以變更移轉虛擬機器的 MAC 位址，以解決此問題。

1. 在 vSphere Client 中，關閉虛擬機器的電源。
2. 在庫存中，用滑鼠右鍵按一下虛擬機器，然後從功能表中選擇**編輯設定**。
3. 在**虛擬硬體**標籤上，展開網路配接卡。
4. 在「MAC 位址」文字框旁邊，從功能表中選擇**手動**。
5. 指定唯一的 MAC 位址，然後按一下**確定**。
6. 確認唯一的 MAC 位址是否可解決通訊問題。

## 高主機資源耗用
{: #hcx-archi-trbl-high-host-resource}

在少數情況下，如果所有服務虛擬應用裝置都位於相同的主機上，則 Hybrid Cloud Services 服務虛擬機器可能會耗盡主機的 CPU 及磁碟資源。

在某個實體主機上安裝所有虛擬應用裝置時，部分使用者會看到此問題。在具有此配置的情況下，若同時發生下列事項時，效能會降低：
* 網路具有高延遲及（或）封包流失。當您使用公用網際網路或忙碌網路時，移轉或資料傳輸會變慢。
* 「WAN 最佳化工具」會耗用頻寬來加密及壓縮（或解密及解壓縮）大量工作負載。
* 內部部署 VM 與移轉 VM 之間有高應用程式資料流量。

若要解決此問題，請遵循下列步驟：

1. 在您變更資料中心配置之前，請檢閱穩定狀態支援的需求。
2. 如果資源即將耗盡，請聯絡穩定狀態支援。他們可以建議如何在具有最少關閉時間量的情況下重新配置環境。

## 相關鏈結
{: #hcx-archi-trbl-related}

* [向 vCenter 登錄 HCX Manager](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-reg-vcenter)
* [修改或解除安裝 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)

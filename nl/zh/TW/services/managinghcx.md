---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# 管理 VMware HCX on IBM Cloud

## 存取 HCX on IBM Cloud 管理主控台

若要管理 HCX on {{site.data.keyword.cloud}} 服務，您必須存取「HCX Cloud 主控台」或「HCX Manager 管理主控台」：
1. 使用 {{site.data.keyword.cloud_notm}} 基礎架構 VPN 或跳躍伺服器，以容許存取 HCX Manager 虛擬應用裝置 (HCX Manager) 的 IP 位址。您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台的 HCX on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到 IP 位址。
2. 若要存取「HCX Cloud 主控台」，請在 HCX on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上按一下**檢視 HCX Cloud 主控台**，然後使用 vCenter Server 認證來登入。
3. 若要存取「HCX Manager 管理主控台」，請在 HCX on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上按一下**檢視 HCX Manager 管理主控台**，然後使用相同服務詳細資料頁面上所列出的 HCX Manager 認證來登入。

如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server with Hybridity Bundle 實例的服務](../vcenter/vc_hybrid_addingremovingservices.html)。

## 將更新套用至 HCX on IBM Cloud

HCX on {{site.data.keyword.cloud_notm}} 已部署最新已測試建置的 VMware Hybrid Cloud Extension 技術。VMware 會定期提供這些建置的更新項目，其中包括重要修正程式及新增特性。這些建置會自動推送至 HCX on {{site.data.keyword.cloud}} 安裝（包括內部部署 HCX 安裝）。

若要套用任何已推送至環境的維護修正程式，您必須使用內部部署資料中心及 vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 實例中的「HCX Manager 管理主控台」。

如果您看不到預期的建置更新、HCX 發生問題，或要立即將最新的 HCX 建置推送至系統，請遵循[與 IBM 支援中心聯絡](../vmonic/trbl_support.html)中的步驟來開立支援問題單。

### 相關鏈結

* [HCX on {{site.data.keyword.cloud_notm}} 概觀](hcx_considerations.html)
* [HCX 術語名詞解釋](hcx_glossary.html)
* [VMware Hybrid Cloud Extension 概觀](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 文件](https://hcx.vmware.com/#vm-documentation)

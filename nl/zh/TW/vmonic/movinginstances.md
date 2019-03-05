---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 從 1.4 版之前的版本升級您的實例

## 問題

1.4 版以及更新版本中的實例網路拓蹼不同於比 1.4 版更早的版本。由於這項變更，部署在 1.4 版之前版本的實例無法在現行版本中以其原本狀態使用。

## 解決方法

在 1.4 版以及更新版本中，有數個網路拓蹼加強功能可用於您的實例：
* （適用於所有實例）：最佳化的網路配置。由於您使用的 {{site.data.keyword.cloud}} 帳戶必須是 VRF（虛擬遞送和轉遞）帳戶，如果是典型（非 VRF）帳戶，則必須已啟用 VLAN 跨越，因此不需要第二個可攜式 IP 位址。部署時只需要主要 {{site.data.keyword.cloud_notm}} 基礎架構可攜式 IP 位址。
* （僅適用於 Cloud Foundation 實例）：多站台部署功能及 Microsoft Windows AD SSO (Active Directory Single Sign-On) 和「網域名稱系統 (DNS)」伺服器。

如果您尚未從 1.4 版之前的版本中移轉或刪除實例，則在 {{site.data.keyword.vmwaresolutions_short}} 主控台上，它們可能仍會以僅限檢視模式出現。在使用者介面中這些實例將標示為**已淘汰**，且具有警告符號圖示。

實例內容中顯示的資訊反映到 1.4 版發行日期當時的資料，且不再重新整理。
{:note}

下列動作可用於 1.4 版之前的實例：
*  檢視實例詳細資料頁面上的資訊。
*  檢視實例備份資訊。
*  開啟 vSphere Web Client 並使用 vCenter 中的實例。
*  透過開立 {{site.data.keyword.cloud_notm}} 支援問題單來要求實例還原。
*  刪除實例。

1.4 版之前的實例上的所有其他動作皆不再可用。

如果您有 1.4 版之前的實例，且您打算繼續使用它們，則可以透過建立新實例，然後將現有的配置移至這些新實例，來升級它們。

若要將 1.4 版之前的實例移至新實例，請在 vSphere Web Client 中完成下列步驟：
1. 從 1.4 版之前的實例中，匯出所有 VM（虛擬機器）。
2. 在現行版本中建立實例。
3. 從**步驟 1** 匯入所有匯出的 VM。
4. 使用新的實例。

如需匯出及匯入 VM 的相關資訊，請參閱 VMware vSphere 文件。

如果您需要 {{site.data.keyword.vmwaresolutions_short}} 方面的協助，請透過其中一個支援管道[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)。

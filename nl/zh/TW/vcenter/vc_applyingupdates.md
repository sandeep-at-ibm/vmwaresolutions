---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: vCenter Server update, patch vCenter Server, IBM component update

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 將 IBM 管理元件更新套用至 vCenter Server 實例
{: #vc_applyingupdates}

本節中的程序適用於針對部署在 2.1 版至 2.4 版中的實例，來更新 IBM 管理元件。

對於部署在（或升級至）2.5 或更新版本的實例，會視需要自動套用 IBM 管理元件的更新和修補程式。

對於部署在 2.0 版及更早版本的實例，您必須手動套用更新。

此外，當您在實例上完成特定作業時，請注意下列行為：
* 當您訂購新服務時，實例會更新為最新版本。
* 新增叢集時，會使用最新的 VMware 元件來佈建這些叢集，但不會佈建現有的叢集。
* 新增 ESXi 伺服器時，會使用最新的 VMware 元件來佈建這些 ESXi 伺服器，但不會佈建現有的 ESXi 伺服器。

{{site.data.keyword.vmwaresolutions_short}} 不支援套用 VMware 元件的更新及修補程式。您必須自行監視並套用這些更新。
{:important}

## 套用 IBM 管理元件更新之前
{: #vc_applyingupdates-prereq}

按一下向下箭頭來展開更新項目，然後驗證下列資訊：
* 更新的版本。您必須依最早到最新的時間順序來套用更新。套用最新的更新之前，請確定已套用所有先前的更新。例如，嘗試套用 2.4 版更新之前，您必須套用 2.3 版更新。
* 是否需要關閉時間。
* 完成更新的總估計時間。
* 更新對 VMware 虛擬環境的影響。表 1 顯示不同的更新層次對於系統有何影響。
* 更新詳細資料。

表 1. 更新層次及影響

<table>
  <tr>
    <th>更新層次</th>
    <th>影響</th>
  </tr>
  <tr>
    <td>低</td>
    <td>此更新不會影響任何系統。您不需要在排定的關閉時間套用它。</td>
  </tr>
  <tr>
    <td>中</td>
  <td>此更新可能會影響部分系統。建議您在排定的關閉時間套用它。</td>
  </tr>
    <tr>
    <td>重大</td>
  <td>此更新會影響部分或所有系統。您必須在排定的關閉時間套用它。</td>
  </tr>
</table>

## 套用 IBM 管理元件更新的程序（實例 2.1 版至 2.4 版）
{: #vc_applyingupdates-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **vCenter Server 實例**表格中，按一下要更新的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。
   

   如果未顯示詳細資料，這可能表示因為防火牆規則或網路問題的緣故，而有 IBM CloudDriver 虛擬伺服器實例 (VSI) 連線問題。請先解決問題，再繼續下一步，否則更新可能會失敗。

4. 在左側導覽窗格上按一下**更新及修補程式**，並按一下向下箭頭來展開您要套用的 IBM 管理更新，然後完成下列其中一個步驟：
   * 若要立即啟動更新，請按一下更新項目之**動作**直欄中的溢位功能表圖示，然後按一下**立即更新**。
   * 若要排定未來的更新，請按一下更新項目之**動作**直欄中的溢位功能表圖示，然後按一下**排定更新**。選取您要啟動更新的日期、時間及時區。按一下**確定**。
5. 如果您要在多站台部署配置中將更新套用至實例，則會顯示標題為**更新所需的步驟**的區段。本節列出多站台部署中所有實例所需的更新作業。您必須對每個步驟按一下**套用更新**，來依序完成步驟。您必須先等待上一步完成，再開始下一步。

## 套用 IBM 管理元件更新之後的結果
{: #vc_applyingupdates-results}

1. 在您套用更新之後，軟體更新狀態清單中會出現一筆記錄，您可以在其中檢視更新的詳細進度及狀態。更新順利完成時，已安裝的軟體更新清單中會出現一筆記錄。

  若要擷取更新工作的最新狀態，請按一下頁面右上角的重新整理圖示。
  {:tip}

2. 如需更新狀態的詳細資料，請參閱下表。

   表 2. 更新狀態的詳細資料

    <table>
      <tr>
        <th>狀態</th>
        <th>詳細資料      </th>
      </tr>
      <tr>
        <td>可用</td>
        <td>更新可供套用。在套用所有先前的更新之前，您無法選取可用的更新。</td>
      </tr>
      <tr>
        <td>進行中</td>
      <td>更新工作已起始，但尚未完成。在現行更新工作完成之前，您無法套用任何其他更新。</td>
      </tr>
        <tr>
        <td>已安裝</td>
      <td>更新工作已完成。會更新 VMware 平台的對應元件。</td>
      </tr>
        <tr>
        <td>失敗</td>
      <td>更新工作失敗。主控台會報告更新失敗的錯誤。請先檢閱錯誤並修正報告的問題，再重新套用更新。</td>
      </tr>
          <tr>
        <td>已排定</td>
      <td>已排定稍後執行更新工作。更新工作會在您排定的時間自動啟動。</td>
      </tr>
          <tr>
        <td>不明</td>
      <td>無法取得更新工作的狀態。請與 IBM 支援中心聯絡，以取得協助。</td>
      </tr>
    </table>

3. 如果更新處理程序在特定步驟失敗，請[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)以取得協助。支援中心會建議您如何解決問題，並引導您從失敗的步驟套用更新及修補程式。

## 相關鏈結
{: #vc_applyingupdates-related}

* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [升級 vCenter Server 實例的授權](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)

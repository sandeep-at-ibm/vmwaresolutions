---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 將更新套用至 vCenter Server with Hybridity Bundle 實例

只會針對管理元件，將修補程式及更新套用至 vCenter Server with Hybridity Bundle 實例的處理程序自動化。必須手動套用 VMware 更新。

## 開始之前

因為已啟用自動更新，所以從 2.5 版開始，不再列出 IBM CloudDriver 更新。例如新增主機、新增叢集及訂購服務等動作，會自動將實例更新至最新版本。如需自動更新的相關資訊，請參閱 [2.5 版的版本注意事項](/docs/services/vmwaresolutions/vmonic/relnotes_v25.html)中的 *IBM CloudDriver 備援* 小節。{:note}

在您嘗試套用更新之前，請按一下向下箭頭來展開更新項目，並驗證下列資訊：
* 更新的版本。您必須依最早到最新的時間順序來套用更新。套用最新的更新之前，請確定已套用所有先前的更新。例如，嘗試套用 2.4 版更新之前，您必須套用 2.3 版更新。
* 是否需要關閉時間。
* 完成更新的總估計時間。
* 更新對 VMware 虛擬環境的影響。
* 更新詳細資料。

下表顯示不同的更新層次對於系統有何影響。

表 1. 更新層次及影響

|更新層次|影響|  
|:------------- |:------------- |
|低|此更新不會影響任何系統。您不需要在排定的關閉時間套用它。|  
|中|此更新可能會影響部分系統。建議您在排定的關閉時間套用它。|  
|重大|此更新會影響部分或所有系統。您必須在排定的關閉時間套用它。|  

## 將更新套用至 vCenter Server with Hybridity Bundle 實例的程序

1. 從 {{site.data.keyword.vmwaresolutions_full}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下要更新的實例。
3. 在**摘要**頁面上，驗證所有實例詳細資料都已正確顯示。然後，按一下左導覽窗格上的**基礎架構**，以驗證**基礎架構**頁面上的詳細資料。如果未顯示詳細資料，這可能表示因為防火牆規則或其他網路問題的緣故，而有 IBM CloudDriver 虛擬伺服器實例 (VSI) 連線問題。請先解決問題，再繼續下一步，否則更新可能會失敗。
4. 在左導覽窗格上，按一下**更新及修補程式**。

   **更新及修補程式**頁面只包含用來更新 IBM 管理元件的套件，而不包含 VMware 更新。{{site.data.keyword.vmwaresolutions_short}} 會針對下列作業套用 VMware 更新：
   * 部署新的 vCenter Server 實例時。
   * 新增 ESXi 伺服器時，會使用 VMware 更新來佈建新的 ESXi 伺服器，但不會更新現有的 ESXi 伺服器。
   * 新增叢集時，會使用 VMware 更新來佈建新的叢集，但不會更新現有的叢集。
   {:note}

5. 若要升級授權，請按一下**升級**。從清單中選取您要升級至的版本，然後按一下**升級**。無法進行授權版本降級。

   授權升級會取代實例上的所有現有 NSX 授權。如果您在計費週期中途進行升級，則可能因為新舊授權重疊而產生其他費用。為了避免產生其他費用，建議在計費週期結束時升級授權。{:note}

6. 對於軟體更新，請按一下向下箭頭來展開您要套用的更新，然後完成下列其中一個步驟：
   *  若要立即啟動更新，請按一下更新項目之**動作**直欄中的溢位功能表圖示，然後按一下**立即更新**。
   *  若要排定未來的更新，請按一下更新項目之**動作**直欄中的溢位功能表圖示，然後按一下**排定更新**。選取您要啟動更新的日期、時間及時區。按一下**確定**。
7. 如果您要在多站台部署配置中將更新套用至 vCenter Server 實例，則會顯示標題為**更新所需要的步驟**的區段。本節列出多站台部署中所有實例所需的更新作業。您必須對每個步驟按一下**套用更新**，來依序完成步驟。您必須先等待上一步完成，再開始下一步。   

## 結果

2. 在您套用更新之後，軟體更新狀態清單中會出現一筆記錄，您可以在其中檢視更新的詳細進度及狀態。更新順利完成時，已安裝的軟體更新清單中會出現一筆記錄。

  若要擷取更新工作的最新狀態，請按一下頁面右上方的重新整理圖示。
  {:tip}

3. 如需更新狀態的詳細資料，請參閱下列清單：
<dl class="dl">
<dt class="dt dlterm">可用</dt>
<dd class="dd">更新可供套用。在套用所有先前的更新之前，您無法選取可用的更新。</dd>
<dt class="dt dlterm">進行中</dt>
<dd class="dd">更新工作已起始，但尚未完成。在現行更新工作完成之前，您無法套用任何其他更新。</dd>
<dt class="dt dlterm">已安裝</dt>
<dd class="dd">更新工作已完成。會更新 VMware 平台的對應元件。</dd>
<dt class="dt dlterm">失敗</dt>
<dd class="dd">更新工作失敗。主控台會報告更新失敗的錯誤。請先檢閱錯誤並修正報告的問題，再重新套用更新。</dd>
<dt class="dt dlterm">已排定</dt>
<dd class="dd">已排定稍後執行更新工作。更新工作會在您排定的時間自動啟動。</dd>
<dt class="dt dlterm">不明</dt>
<dd class="dd">無法取得更新工作的狀態。請與 IBM 支援中心聯絡，以取得協助。</dd>
</dl>

4. 如果更新處理程序在特定步驟失敗，請[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)以取得協助。會建議您如何解決問題，並引導您從失敗的步驟重新嘗試升級。

### 相關鏈結

* [vCenter Server with Hybridity Bundle 概觀](/docs/services/vmwaresolutions/vcenter/vc_hybrid_overview.html)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
* [常見問題](/docs/services/vmwaresolutions/vmonic/faq.html)

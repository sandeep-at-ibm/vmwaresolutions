---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-11"

keywords: notifications console, filter notifications, system notification

subcollection: vmware-solutions


---

# 管理系統通知
{: #notifications}

您可以檢查通知，以瞭解系統或使用者作業的狀態。您也可以使用該資訊來調查可能發生的問題。

## 檢視通知
{: #notifications-view}

1. 從 {{site.data.keyword.vmwaresolutions_full}} 主控台，按一下左導覽窗格中的**通知**。
2. 檢視關於所有通知的摘要。

   表 1. 通知歷程

    <table>
      <tr>
        <th>直欄</th>
        <th>說明       </th>
      </tr>
      <tr>
        <td>嚴重性</td>
        <td>通知所報告事件的嚴重性。<dl class="dl">
          <dt class="dt dlterm">嚴重 </dt>
          <dd class="dd">嚴重事件可能會影響整個系統或服務。</dd>
          <dt class="dt dlterm">錯誤</dt>
          <dd class="dd">在可能需要管理者或使用者人為介入的作業期間，發生錯誤事件。</dd>
          <dt class="dt dlterm">警告</dt>
          <dd class="dd">元件失敗或未正常運作。不過，失敗不會干擾元件的進行中程序。</dd>
            <dt class="dt dlterm">參考資訊</dt>
            <dd class="dd">已完成系統作業或使用者作業。通常，下列事件會報告參考資訊通知：<br>已安裝服務。<br>已升級服務。<br>已移除服務。<br>會針對已新增的 ESXi 伺服器重新配置所有服務。<br>會針對已移除的 ESXi 伺服器重新配置所有服務。</dd>
          </dl>
        </td>
       </tr>
       <tr>
         <td>類型      </td>
         <td>所報告事件相關的元件類型：<br>vCenter Server 實例<br>服務<br>系統</td>
       </tr>
       <tr>
         <td>資源</td>
         <td>傳送通知的實例或服務名稱。</td>
       </tr>
       <tr>
         <td>說明       </td>
         <td>通知的簡要說明。</td>
       </tr>
       <tr>
         <td>日期 </td>
         <td>傳送通知的日期和時間。</td>
       </tr>
    </table>                                       

3. 按一下通知列，以檢視通知的詳細資料。

## 過濾通知
{: #notifications-filter}

依預設，會顯示所有未讀取通知。您可以依狀態、嚴重性和類型來過濾通知。若要過濾通知，請僅針對要在**狀態**、**嚴重性**或**類型**清單中顯示的項目來選取勾選框。

## 相關鏈結
{: #notifications-related}

* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [使用者帳戶及設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)

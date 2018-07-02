---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-24"

---

# 維護 VMware Federal 實例的安全

請完成下列程序來保護已部署 VMware Federal 實例的安全，亦即，移除已開啟的管理連線，以持續存取該實例。

## 開始之前

請檢閱下列資訊，以瞭解維護您所部署之 VMware Federal 實例安全的結果：

* 在完成此程序之前，請記錄及儲存您環境可能需要的任何認證。您環境的所有認證會從 {{site.data.keyword.vmwaresolutions_full}} 資料庫中消除，而且在呼叫安全動作之後，無法再擷取它們。
* 在呼叫安全動作之後，會停用除了完整實例刪除以外的所有管理功能。
* 用於出埠 HTTPS 管理資料流量及 IBM CloudDriver 虛擬機器的 VMware NSX Edge Services Gateway (ESG) 會被刪除，這屬於維護所部署之 VMware Federal 實例的安全的動作。

## 程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下要維護安全的實例。
3. 按一下 **vCenter 主控台**右側的溢位功能表圖示。
4. 按一下**維護實例安全**。
5. 按一下**確定**以確認您要中斷實例自動化。
   
   **附註**：完成此步驟之前，請確定您已檢閱**開始之前**小節中的資訊。

## 結果

實例的狀態會變更為**正在修改**。

當順利維護實例的安全時，實例的狀態會變更為**安全**，且只會提供實例內容和部署歷程。

## 相關鏈結

* [VMware Federal on IBM Cloud 概觀](vc_fed_overview.html)
* [訂購 VMware Federal 實例](vc_fed_orderinginstance.html)
* [檢視 VMware Federal 實例](vc_fed_viewinginstance.html)
* [刪除 VMware Federal 實例](vc_fed_deletinginstance.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-20"

---

# 維護 VMware Federal 實例的安全

請完成下列程序來保護已部署 VMware Federal 實例的安全，亦即，移除已開啟的管理連線，以持續存取該實例。

## 開始之前

請檢閱下列資訊，以瞭解維護您所部署之 VMware Federal 實例安全的結果：

* 在完成此程序之前，請記錄並儲存您環境可能需要的所有認證。會從 {{site.data.keyword.vmwaresolutions_full}} 資料庫中消除您環境的所有認證，而且在啟動安全動作之後，無法再擷取它們。
* 除了完整實例刪除之外，在啟動安全動作之後，會停用所有其他管理功能。

## 維護 VMware Federal 實例安全的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下要維護安全的實例。
3. 按一下 **vCenter 主控台**旁的溢位功能表圖示。
4. 按一下**維護實例安全**。
5. 按一下**確定**以確認您要中斷實例自動化。

  **附註**：在完成此步驟之前，請確定已檢閱**開始之前**小節中的資訊。

6. 從環境中移除公用管理服務 VMware NSX Edge Services Gateway (ESG)，以及選擇性地移除在自動化期間部署的用戶端管理 ESG。
7. 重設 IBM 自動化所使用之所有帳戶的密碼或金鑰。如需相關資訊，請參閱 [How can I secure my environment to remove access by IBM automation and support?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)

## 結果

實例的狀態會變更為**正在修改**。

當順利維護實例的安全時，實例的狀態會變更為**安全**，且只會提供實例內容和部署歷程。

### 相關鏈結

* [VMware Federal on {{site.data.keyword.cloud_notm}} 概觀](vc_fed_overview.html)
* [訂購 VMware Federal 實例](vc_fed_orderinginstance.html)
* [檢視 VMware Federal 實例](vc_fed_viewinginstance.html)
* [刪除 VMware Federal 實例](vc_fed_deletinginstance.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)

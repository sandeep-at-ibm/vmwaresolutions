---

copyright:

  years:  2016, 2018

lastupdated: "2017-08-16"

---

# Virtual SAN 性能警示及警告

## 問題
在 VMware vSphere Web Client **監視**頁面上，您可能會看到與「Virtual SAN 性能」問題相關的警示及警告。

## 解決方法
這些警告不是問題，不代表功能有問題。不過，如果您想要從 vSphere Web Client 清除警告，請使用下列程序。

1. 移至 http://partnerweb.vmware.com/service/vsan/all.json，並以 `all.json` 的名稱將 JSON 檔案儲存在本端系統上。
2. 請確定您已完成 [vCenter 主控台逾時](trbl_timeout_vc_console.html)中的步驟。
3. 在 Cloud Foundation 實例的詳細資料頁面上，按一下 **vCenter 主控台**，並使用 {{site.data.keyword.vmwaresolutions_full}} 主控台所顯示的認證登入 vSphere Web Client。
4. 在 vSphere Web Client 上，移至**管理 > 設定**，然後開啟 **Virtual SAN > 性能 > HCL 資料庫**區段。按一下**更新來源檔案**，然後上傳您先前儲存的 `all.json` 檔案。
5. 若要清除警告，請移至 vSphere Web Client 右上方的**警示**窗格。用滑鼠右鍵按一下每一個警示，然後選取**重設為綠色**。

如需相關資訊，請參閱[如何為 vSAN 性能檢查外掛程式下載離線 vSAN HCL 檔案](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}。

---

copyright:

  years:  2016, 2019

lastupdated: "2018-11-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud 的移除處理程序

自動化 Zerto on {{site.data.keyword.cloud}} 服務的移除處理程序。請完成下列步驟，以順利移除 Zerto on {{site.data.keyword.cloud_notm}} 服務。

## 如何移除 Zerto on IBM Cloud

1. 從左導覽窗格中，按一下**已部署的實例**，然後按一下您要從中移除服務的實例。
2. 按一下**服務**標籤。
3. 在**已安裝的服務**標籤上，按一下服務卡右上方的溢位功能表圖示，然後按一下**移除服務**。
4. 在**移除服務**視窗中，檢閱任何考量或警告。按一下**我瞭解**。
5. 接受服務移除的要求之後，服務狀態會變更為**正在移除**，並完成下列移除步驟：   
   1. 移除已部署至所有 ESXi 伺服器的 Zerto Virtual Replication Appliance。
   2. 解除安裝 Zerto Virtual Replication。
   3. 刪除已安裝 Zerto Virtual Replication 的 Windows VSI（虛擬服務實例）。
   4. 傳回針對 Zerto Virtual Replication 與 {{site.data.keyword.cloud_notm}} 基礎架構的通訊所訂購的專用可攜式子網路。   
   5. 從 {{site.data.keyword.cloud_notm}} 計費對帳單移除 Zerto 災難回復服務費用。

      將針對已移除的 Zerto 災難回復服務，向您收取到計費週期結束為止的費用。
      {:note}

## 結果

順利完成服務移除之後，會透過電子郵件通知您，而且會從**已安裝的服務**標籤刪除服務項目。

### 相關鏈結

* [訂購 Zerto on {{site.data.keyword.cloud_notm}}](zerto_ordering.html)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](managingzertodr.html)
* [Cloud Foundation 實例](../sddc/sd_cloudfoundationoverview.html)
* [vCenter Server 實例](../vcenter/vc_vcenterserveroverview.html)
* [zerto.com 網站](https://www.zerto.com){:new_window}
* [Zerto 技術文件](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# 關於 ESXi 伺服器的常見問題

尋找在 {{site.data.keyword.vmwaresolutions_full}} 主控台上管理的 ESXi 伺服器之相關常見問題的回答。

## 我可以新增多少部 ESXi 伺服器至實例中？

* 對於 vCenter Server 實例，您可以將預設叢集擴充為具有多達 51 部 ESXi 伺服器。每一個非預設叢集可以擴充為具有多達 59 部 ESXi 伺服器。由於您最多可以將 10 個叢集新增至實例中，因此每一個已部署的實例在所有叢集中最多可以有 51 + 9x59 = 582 部 ESXi 伺服器。
* 若為 Cloud Foundation 實例，標準配置有四部 ESXi 伺服器。您最多可以新增 28 部伺服器（總共最多 32 部伺服器）。對於多站台配置中的 Cloud Foundation 實例，在所有實例中最多可以有 128 部 ESXi 伺服器。

  **附註**：如果 Cloud Foundation 配置需要超過 128 部 ESXi 伺服器的多站台部署，[請與 IBM 支援中心聯絡](trbl_support.html)以取得協助。

## 我可以新增多少部 ESXi 伺服器至叢集？

對於 2.2 版以及更新版本，您最多可以將 51 部 ESXi 伺服器新增至起始叢集，以及最多可以將 59 部 ESXi 伺服器新增至已新增的叢集。

如果是部署在 2.1 版或更舊版本中的實例，您必須啟用必要的 vSAN 支援，才能將叢集大小增加到超過 32。請完成下列步驟以啟用必要的 vSAN 支援：

1. 在每一部已部署的 ESXi 伺服器上，執行下列指令：

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. 重新啟動每一部 ESXi 伺服器。如需相關資訊，請參閱[建立最多具有 64 部主機的 vSAN 6.x 叢集](https://kb.vmware.com/s/article/2110081)。
3. 您可能需要增加 vCenter Server 的大小，以容納所新增的虛擬機器及 ESXi 伺服器。
4. 開啟「IBM 支援中心」問題單，指出您完成步驟 1 - 3 來手動套用 vSAN 變更。在問題單中，要求針對超過 32 部的 ESXi 伺服器啟用已升級實例。

## 我可以變更 ESXi 伺服器名稱及 IP 位址嗎？

無法變更 ESXi 伺服器名稱及 IP 位址，因為已登錄它們以進行 Windows DNS 解析。變更可能會導致部署期間失敗或 vCenter Server 功能失敗。

**附註**：請不要在 {{site.data.keyword.cloud_notm}} 使用者介面上使用**重新命名裝置**特性來變更 ESXi 伺服器名稱。此功能的確會變更 ESXi 伺服器的 FQDN，但所配置的 vCenter Center 及 Windows VSI 主機登錄將不正確，而可能導致失敗。

## 我可以在 ESXi 伺服器上停用 root 存取權嗎？

建議在 ESXi 伺服器上保持啟用 root 存取權，否則可能會發生 {{site.data.keyword.vmwaresolutions_short}} 功能失敗。

必要的話，當 {{site.data.keyword.vmwaresolutions_short}} 主控台上的 ESXi 伺服器狀態為**備妥使用**之後，您可以停用 root 存取權。

您必須重新啟用 root 存取權，以進行後續的自動化作業，例如，新增或移除檔案共用時，或在安裝附加程式服務時（例如 Zerto on {{site.data.keyword.cloud_notm}}）。

## 我可以在我的 ESXi 伺服器上新增靜態路徑，以便從其他位置裝載儲存空間嗎？

可以為儲存空間新增靜態路徑，但必須非常小心地執行作業。否則，現有的共用可能會變成未裝載。

**附註**：不支援為 vMotion 新增靜態路徑。vMotion 子網路配置中的變更可能會導致 {{site.data.keyword.vmwaresolutions_short}} 功能失敗。

### 相關鏈結

* [擴充及縮減 vCenter Server 實例的容量](../vcenter/vc_addingremovingservers.html)
* [擴充及縮減 Cloud Foundation 實例的容量](../sddc/sd_addingremovingservers.html)
* [新增、檢視及刪除 vCenter Server 實例的叢集](../vcenter/vc_addingviewingclusters.html)
* [新增、檢視及刪除 Cloud Foundation 實例的叢集](../sddc/sd_addingviewingclusters.html)
* [與 IBM 支援中心聯絡](trbl_support.html)

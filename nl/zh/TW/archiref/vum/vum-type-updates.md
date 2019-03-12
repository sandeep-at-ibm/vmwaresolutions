---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# VMware 軟體更新類型
{: #vum-type-updates}

VMware 使用下列術語來說明軟體更新。

表 1. VMware 軟體更新術語及定義

| 術語 | 定義 |
|:------- |:----------- |
| 公告 |	一個以上 VIB 分組。公告是在 meta 資料內進行定義。|
| 保存庫 |	線上發佈之 VIB 及關聯 meta 資料的邏輯分組|
| 主機升級映像檔 |	ESXi 映像檔，您可以在 Update Manager 儲存庫中匯入並用於將 ESXi 5.5 或 ESXi 6.0 主機升級至 ESXi 6.5。|
| 延伸規格 | 	用於定義將選用元件新增至 ESXi 主機的 VIB 群組的一種公告。同時負責延伸規格修補程式或更新的協力廠商通常會提供延伸規格。|
| meta 資料 |	用於定義相依關係資訊、文字說明、系統需求及公告的額外資料。|
| 離線組合壓縮檔 |	用於將 VIB 及對應 meta 資料封裝至適用於離線修補的自行包含套件的保存檔。您無法將協力廠商離線組合或您從自訂 VIB 集合產生的離線組合，用於從 ESXi 5.5 或 ESXi 6.0 到 ESXi 6.5 的主機升級。|
| 修補程式 |	用於將一個以上 VIB 群組在一起以處理特定問題或加強功能的一種公告。|
| 累積更新 |	群組在一起以輕鬆下載及部署的修補程式集合。|
| VA 升級 |	供應商視為升級的虛擬應用裝置更新。|
| VIB |	VIB 是單一軟體套件。|

## 相關鏈結
{: #vum-type-updates-related}

* [VMware HCX on {{site.data.keyword.cloud}} 解決方案架構](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware)（示範）

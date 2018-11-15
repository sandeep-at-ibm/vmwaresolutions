---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-13"

---

# 關於 vCenter Server 的連接儲存空間

連接儲存空間是 VMware vCenter Server on {{site.data.keyword.cloud}} 供應項目的延伸。VMware vCenter Server on {{site.data.keyword.cloud_notm}} 的連接儲存空間解決方案架構，詳述了解決方案的元件，和本設計每個元件的高階配置。

如需 vCenter Server 設計的相關資訊，請參閱[解決方案概觀](../solution/solution_overview.html)。

## vCenter Server 連接儲存空間的主要好處

雖然連接儲存空間並不是 VMware 環境的必要條件，但它用來作為共用儲存裝置，可為使用者提供 IT 作業方面的許多好處。使用共用儲存裝置可透過啟用下表說明的 vSphere 功能來幫助您達到高可用性、分散式資源排程器、有效率地使用儲存空間容量，以及簡化管理。

表 1. vCenter Server 連接儲存空間的功能說明

|功能                          |說明              |
|:------- |:----------- |
| vSphere 分散式資源排程器和資源儲存區 |此特性容許透過負載平衡和虛擬機器 (VM) 放置來達成資源的抽象化和彈性管理。資源儲存區可依階層分組，並用來階層式地分割可用的 CPU 和記憶體資源。|
| vSphere 高可用性 |此特性為 VM（透過將它們集合到儲存區中）和位於叢集裡的主機提供 HA。叢集裡的主機會受到監視。萬一發生失敗，失敗主機上的 VM 會在替代主機上重新啟動。|
| vSphere 資料儲存庫叢集 |此特性提供含有共用資源的資料儲存庫集合，以及共用管理介面。|
| vSphere 容錯 |即使發生完全主機失敗，此特性也能免除關閉時間和中斷，為 VM 提供連續可用性。|

### 相關鏈結

* [解決方案概觀](../solution/solution_overview.html)

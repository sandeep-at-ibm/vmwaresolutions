---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# 新增 HA 叢集時發現 vSphere 主控台配置問題

## 問題
當您新增只有一個檔案共用的 HA（高可用性）叢集配置時，在 ESXi 主機上發現下列配置問題：

`The number of heartbeat datastores for host is 1, which is less than required: 2`

## 解決方法
如果共用儲存空間沒有備援空間可以供資料儲存庫活動訊號使用，則會發生此問題。

如需相關資訊以及如何解決此問題的步驟，請參閱 [HA 錯誤："The number of heartbeat data stores for host is 1, which is less than required: 2" (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739)。

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 新增 HA 叢集時發現 vSphere 主控台配置問題
{: #trbl_add_ha_cluster_config}

## 問題
{: #trbl_add_ha_cluster_config-problem}

當您新增只有一個檔案共用的 HA（高可用性）叢集配置時，在 ESXi 主機上發現下列配置問題：

> 主機的活動訊號資料儲存庫數目為 1，這小於必要值：2

## 解決方法
{: #trbl_add_ha_cluster_config-resolution}

如果共用儲存空間沒有備援空間可以供資料儲存庫活動訊號使用，則會發生此問題。

如需相關資訊以及如何解決此問題的步驟，請參閱 [HA 錯誤：主機的活動訊號資料儲存庫數目為 1，這小於必要值：2 (2004739)](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2004739)。

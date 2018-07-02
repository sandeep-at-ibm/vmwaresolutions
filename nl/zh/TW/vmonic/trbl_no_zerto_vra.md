---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-19"

---

# 未針對新建的 ESXi 伺服器顯示 Zerto Virtual Replication Appliance

## 問題
將 ESXi 伺服器新增至已安裝 Zerto 災難回復的 VMware vCenter Server 實例之後，Virtual Replication Appliances (VRA) 並未會顯示在 Zerto Virtual Replication 主控台上。

## 解決方法
對於 vCenter Server 實例，Zerto 災難回復服務只從預設叢集 **cluster1** 安裝在 ESXi 伺服器上。不是建立其他叢集，或是將 ESXi 伺服器新增至其他叢集，相同 vCenter Server 環境中的任何其他叢集都不會自動安裝 Zerto 災難回復。

在其他叢集上，您必須個別安裝 Zerto 災難回復。

開立 {{site.data.keyword.cloud}} 支援問題單，並與「IBM 支援中心」合作，以取得可用的 IP 位址，讓您從 Zerto 主控台而非 {{site.data.keyword.vmwaresolutions_short}} 主控台安裝 VRA。

如果要存取 Zerto 主控台，請從該實例的**服務**標籤按一下 Zerto 服務卡，然後按一下**檢視詳細資料**，再按一下**檢視 Zerto 主控台**。

如需與 IBM 支援中心聯絡的相關資訊，請參閱[與 IBM 支援中心聯絡](trbl_support.html)。

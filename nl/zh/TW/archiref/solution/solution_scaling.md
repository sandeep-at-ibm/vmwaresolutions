---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 調整容量

起始部署之後，您可以從 {{site.data.keyword.vmwaresolutions_full}} 主控台橫向擴充運算容量。此設計支援下列橫向擴充路徑：
* 新增由個別 vCenter Server 管理的新站台
* 新增叢集
* 將新的主機新增至現有叢集

## 新增其他站台

{{site.data.keyword.vmwaresolutions_short}} 可以運用 {{site.data.keyword.cloud_notm}} 全球資料中心顯示狀態及整合式網路骨幹，容許在從頭開始建置這類基礎架構所需的一小段時間內部署及操作各種跨地理位置使用案例。

在此設計中，多站台部署的定義包含下列項目：
* 包含要提供之新 DNS/AD 根網域、子網域、SSO 網域及 SSO 站台名稱的起始或主要 VMware 部署。
* 佈建至需要下列配置之主要站台 SSO 網域的單一或多個次要站台：
   * 新的 SSO 站台名稱
   * 關聯至主要網域根的新 DNS 站台/子網域
   * 次要與主要站台 AD VM 之間的 DNS 及 AD 抄寫設定
   * 已部署並配置成與主要站台 PSC 同步化的 PSC
   * 「加強型鏈結模式」設為主要站台 vCenter 的 vCenter 設定

此外，次要站台中的 NSX Manager 可能設定為主要站台上 NSX Manager 的次要 NSX Manager。

## 新增叢集

您也可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台建立新的叢集，並訂購自動新增至新叢集的新主機，以橫向擴充運算容量。

此方法可讓您達成下列事項：
* 在環境中建立其他個別叢集。
* 在實際及邏輯上隔離管理工作負載與應用程式工作負載。
* 根據其他特徵（例如，Microsoft SQL 資料庫叢集）來隔離工作負載。
* 在高可用性拓蹼中部署應用程式。

將起始叢集轉換為僅限管理叢集時，移轉現有工作負載會涉及使用者所要採取的手動步驟。這可能涉及將資料儲存庫重新連接至新的叢集，或是交替地儲存空間移轉。如果新叢集位於不同的 {{site.data.keyword.cloud_notm}} Pod，或獲指派不同的 VLAN ID，則可能需要變更工作負載的 IP 位址。{:note}

## 將 ESXi 主機新增至現有叢集

您可以從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購主機，以橫向擴充現有叢集。新的主機會自動新增至叢集。請注意，您可能需要根據保留需求來調整叢集的 HA 保留原則。

### 相關鏈結

* [解決方案概觀](solution_overview.html)
* [設計概觀](design_overview.html)
* [備份元件](solution_backingup.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud 概觀
{: #addingzertodr}

Zerto on {{site.data.keyword.cloud}} 服務可將抄寫及災難回復功能整合到部署供應項目，以保護及回復 {{site.data.keyword.cloud_notm}} 上位於您 VMware 虛擬環境中的資料。

只有在 1.2 版或更新版本中部署的實例，才能使用此服務。目前安裝的 Zerto 版本為 6.0 Update 3。
{:note}

## Zerto on IBM Cloud 的技術規格
{: #technical-considerations-for-zerto-on-ibm-cloud}

下列元件已訂購並包括在 Zerto on {{site.data.keyword.cloud_notm}} 服務中。

Zerto Virtual Replication Appliance (VRA) 元件只會部署至預設叢集。
{:note}

### VSI
{: #addingzertodr-specs-vsi}

* 一個虛擬服務實例 (VSI) - Zerto Virtual Manager
* 2 x 2.0 GHz 核心
* 4 GB RAM
* Windows Server 2016 Standard Edition（64 位元）

### 儲存空間
{: #addingzertodr-specs-storage}

100 GB (SAN) 磁碟

### 網路
{: #addingzertodr-specs-network}

* 一個主要專用 IP 位址
* 1 Gbps 專用網路上行鏈路

### 授權及費用
{: #addingzertodr-specs-licenses}

Zerto Replication 6.0 版更新 3 授權

## 相關鏈結
{: #addingzertodr-related}

* [關於 {{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-prod_overview)
* [訂購 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [管理 Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [要求 Zerto on {{site.data.keyword.cloud_notm}} 的受管理服務](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com 網站](https://www.zerto.com){:new_window}
* [Zerto 技術文件](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

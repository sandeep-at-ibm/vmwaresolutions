---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-06"

keywords: planning vCenter Server, data center, vCenter Server data centers

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 實例的需求及規劃
{: #vc_planning}

在訂購 VMware vCenter Server 實例之前，請先檢閱下列需求。請根據 {{site.data.keyword.CloudDataCent}} 位置、工作負載容量需求及附加程式服務需求來規劃實例。

## IBM Cloud 帳戶需求
{: #vc_planning-account-req}

您使用的 {{site.data.keyword.cloud_notm}} 帳戶必須符合特定需求。如需相關資訊，請參閱 [{{site.data.keyword.cloud_notm}} 帳戶的需求](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)。

## IBM Cloud Data Center 可用性
{: #vc_planning-dc-availability}

vCenter Server 部署具有嚴格的實體基礎架構需求。因此，您只能在符合需求的 {{site.data.keyword.CloudDataCents_notm}} 中部署實例。下列 {{site.data.keyword.CloudDataCents_notm}} 可用於 vCenter Server 部署。

Cascade Lake {{site.data.keyword.baremetal_short}} 提供於多區域地區的 {{site.data.keyword.CloudDataCents_notm}}。如需相關資訊，請參閱[多區域地區 (MZR) 概觀](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)。
{:note}

| {{site.data.keyword.CloudDataCent_notm}} |位置|地區           |伺服器選項     |
|:----------------------|:---------|:-------|:---------------|
|AMS01 |阿姆斯特丹|歐洲| Skylake、SAP 認證、Broadwell |
|AMS03 |阿姆斯特丹|歐洲| Skylake、SAP 認證、Broadwell |
|CHE01 |清奈|亞太地區| Skylake、SAP 認證、Broadwell |
|DAL09 |達拉斯|NA 南部| Skylake、SAP 認證、Broadwell |
|DAL10 |達拉斯|NA 南部| Skylake、SAP 認證、Broadwell |
|DAL12 |達拉斯|NA 南部| Skylake、SAP 認證、Broadwell |
|DAL13 |達拉斯|NA 南部| Skylake、SAP 認證、Broadwell |
|FRA02 |法蘭克福|歐洲| Skylake、SAP 認證、Broadwell |
|FRA04 |法蘭克福|歐洲| Skylake、SAP 認證、Broadwell |
|FRA05 |法蘭克福|歐洲| Skylake、SAP 認證、Broadwell |
|HKG02 |香港|亞太地區| Skylake、SAP 認證、Broadwell |
|LON02 |倫敦|歐洲| Skylake、Broadwell |
|LON04 |倫敦|歐洲| Skylake、SAP 認證、Broadwell |
|LON05 |倫敦|歐洲| Skylake、Broadwell |
|LON06 |倫敦|歐洲| Skylake、SAP 認證、Broadwell |
|MEL01 |墨爾本|亞太地區| Skylake、SAP 認證、Broadwell |
|MEX01 |克雷塔羅|NA 南部| Skylake、SAP 認證、Broadwell |
|MIL01 |米蘭|歐洲| Skylake、SAP 認證、Broadwell |
|MON01 |蒙特婁|NA 東部| Skylake、SAP 認證、Broadwell |
|OSL01 |奧斯陸|歐洲| Skylake、SAP 認證、Broadwell |
|PAR01 |巴黎|歐洲| Skylake、SAP 認證、Broadwell |
|SAO01 |聖保羅|南美洲| Skylake、SAP 認證、Broadwell |
|SEO01 |首爾|亞太地區| Skylake、SAP 認證、Broadwell |
|SJC03 |聖荷西|NA 西部| Skylake、Broadwell |
|SJC04 |聖荷西|NA 西部| Skylake、Broadwell |
|SNG01 |新加坡|亞太地區| Skylake、SAP 認證、Broadwell |
|SYD01 |雪梨|亞太地區| Skylake、SAP 認證、Broadwell |
|SYD04 |雪梨|亞太地區| Skylake、SAP 認證、Broadwell |
|SYD05 |雪梨|亞太地區| Skylake、SAP 認證、Broadwell |
|TOK02 |東京|亞太地區| Skylake、SAP 認證、Broadwell |
| TOK04 |東京|亞太地區| Skylake、SAP 認證、Broadwell |
|TOK05 |東京|亞太地區| Skylake、SAP 認證、Broadwell |
|TOR01 |多倫多|NA 東部| Skylake、SAP 認證、Broadwell |
|WDC04 |華盛頓特區|NA 東部| Skylake、SAP 認證、Broadwell |
|WDC06 |華盛頓特區|NA 東部| Skylake、SAP 認證、Broadwell |
|WDC07 |華盛頓特區|NA 東部| Skylake、SAP 認證、Broadwell |
{: caption="表 1. vCenter Server 實例可用的 {{site.data.keyword.CloudDataCents_notm}}" caption-side="top"}

根據可用性及庫存供應，{{site.data.keyword.CloudDataCents_notm}} 可能會在 {{site.data.keyword.vmwaresolutions_short}} 主控台中顯示狀態指示器，以協助您規劃部署。

|狀態|狀態詳細資料|
|:------------------------------|:--------------------------------------------------|
|即將推出                   |目前並未提供 {{site.data.keyword.CloudDataCent_notm}}。|
|暫時沒有庫存                  |目前並未提供 {{site.data.keyword.CloudDataCent_notm}}。|
|庫存受限             |{{site.data.keyword.CloudDataCent_notm}} 的可用性受限，可能無法完成訂單。|
{: caption="表 2. 訂購 vCenter Server 實例時 {{site.data.keyword.CloudDataCents_notm}} 的狀態指示器" caption-side="top"}

## 管理元件的備份
{: #vc_planning-backup-mgmt-components}

您負責維護及確保所有實例元件的可用性。強烈建議您規劃所有管理元件的備份或高可用性。如需相關資訊，請參閱[備份元件](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)。

## 適用於 vCenter Server 實例的服務
{: #vc_planning-addon-services}

您可以根據需要來訂購實例基礎的附加程式服務（例如災難回復）。如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

對 vCenter Server with NSX-T 實例提供服務。
{:note}

### 規劃 VMware HCX on IBM Cloud
{: #vc_planning-addon-services-hcx}

VMware HCX on {{site.data.keyword.cloud_notm}} 服務可以將內部部署資料中心的網路無縫延伸到 {{site.data.keyword.cloud_notm}}，這容許虛擬機器 (VM) 在不進行任何轉換或變更的情況下，移轉到 {{site.data.keyword.cloud_notm}} 或從中移轉出來。

當您部署此服務時，請完成下列設定：
* 選取下列其中一個選項，以指定 **HCX 交互連接類型**：
  * **公用網路**：HCX 會透過公用網路建立站台之間的已加密連線。
  * **專用網路**：HCX 會透過專用網路建立站台之間的已加密連線。
* 指定**公用端點憑證類型**。如果您選取 **CA 憑證**，請配置下列設定：
  * **憑證內容**：輸入 CA 憑證的內容。
  * **私密金鑰**：輸入 CA 憑證的私密金鑰。
  * （選用）**密碼**：如果私密金鑰已加密，請輸入密碼。
  * （選用）**重新輸入密碼**：再次輸入私密金鑰的密碼。
  * （選用）**主機名稱**：輸入要對映至 CA 憑證通用名稱 (CN) 的主機名稱。HCX on {{site.data.keyword.cloud_notm}} 要求 CA 憑證為 NSX Edge 接受的格式。如需 NSX Edge 憑證格式的相關資訊，請參閱[匯入 SSL 憑證](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}。

## 容量考量
{: #vc_planning-capacity-considerations}

如需容量考量的相關資訊，請參閱[調整容量](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)。

## 相關鏈結
{: #vc_planning-related}

* [vCenter Server 概觀](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [訂購 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Security Appliance on IBM Cloud 概觀

FortiGate Security Appliance on {{site.data.keyword.cloud}} 服務會以高可用性模式部署一組 FortiGate Security Appliance (FSA) 300 系列裝置，以提供防火牆、遞送、NAT 及 VPN 服務，來保護實例之公用 VLAN 上的所有伺服器及虛擬機器。

您可以透過 SSH 使用 FortiOS Web Client 或指令行介面，來管理此服務。

只有在 1.8 版或更新版本中部署的實例，才能使用此服務。
{:note}

## FortiGate Security Appliance on IBM Cloud 的技術規格

下列元件已訂購並包括在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務中：

### 硬體

FortiGate Security Appliance 300 系列。

### 高可用性

在主動-被動配置中部署兩個應用裝置。

### 網路

* 上游及下游網路上結合的雙重 1 GbE
* 一個新的上游 {{site.data.keyword.cloud_notm}} 公用 VLAN
* 一個現有的下游 {{site.data.keyword.cloud_notm}} 公用 VLAN

## 安裝 FortiGate Security Appliance on IBM Cloud 時的考量

請先檢閱下列考量，再安裝 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務：
* 確定您要使用的 {{site.data.keyword.cloud_notm}} 帳戶具有**硬體防火牆**許可權。需要此許可權，才能編輯或檢視您實例之 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務的防火牆日誌及設定。
* 如果您要將 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務新增至已部署的實例，則請確定實例的公用 VLAN 上沒有來自 {{site.data.keyword.cloud_notm}} 基礎架構的其他防火牆。
* 安裝 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務時會新增公用 VLAN。
* 在服務部署期間，您的實例可能無法暫時存取網際網路。
* 順利安裝 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務之後，即可從 FortiGate 主控台管理及配置 FSA 的防火牆規則。您必須確定已定義 FSA 防火牆規則，以容許管理元件（例如 Zerto Virtual Manager）所啟動的出埠 HTTPS（TCP 埠 443）通訊，透過網際網路與 {{site.data.keyword.cloud_notm}} 上的外部管理資料庫通訊。出埠 HTTPS（TCP 埠 443）通訊源自實例中管理服務 VMware NSX Edge Services Gateway (ESG) 的公用 IP 位址。
* 您必須謹慎地管理 FortiGate Security Appliance 配置，僅容許必要通訊以及拒絕所有其他通訊。
* 如果您訂購其他叢集，則這些新增叢集的公用 VLAN 不會有 Security Appliance 的 HA 配對。

## 移除 FortiGate Security Appliance on IBM Cloud 時的考量

請先檢閱下列考量，再移除 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務：
* 移除 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務時會移除已新增的公用 VLAN。
* 在服務移除期間，您的實例可能無法暫時存取網際網路。
* 一併移除所有允許、檢查、封鎖及遞送 NAT 資料流量的 FortiGate 規則以及 Fortinet 服務。如果您有任何 NAT 規則，則必須重新配置它們。

### 相關鏈結

* [訂購 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](fsa_ordering.html)
* [管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](managingfsa.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [Fortinet 網站](https://www.fortinet.com/){:new_window}
* [Fortinet 文件庫](http://docs.fortinet.com/fortigate/admin-guides){:new_window}

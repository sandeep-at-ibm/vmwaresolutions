---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: FortiGate Security console, FortiGate 300 console, login FortiGate console

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 FortiGate Security Appliance on IBM Cloud
{: #managingfsa}

順利安裝 FortiGate Security Appliance on {{site.data.keyword.cloud}} 服務之後，即可從 FortiGate 主控台管理及配置 FSA 的防火牆規則。

您必須確定已定義 FSA 防火牆規則，以容許管理元件（例如 Zerto Virtual Manager）起始的出埠 HTTPS（TCP 埠 443）通訊，透過網際網路與 {{site.data.keyword.cloud_notm}} 基礎架構上的外部管理資料庫通訊。出埠 HTTPS（TCP 埠 443）通訊源自實例中管理服務 VMware NSX Edge Services Gateway (ESG) 的公用 IP 位址。
{:important}

## 存取 FortiGate 300 系列主控台
{: #managingfsa-access-console}

若要管理 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務，您必須使用下列其中一種方式來存取 FortiGate® 300 系列主控台：
* 使用您可以在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的認證，登入 FortiOS Web Client。
* 使用您可以在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的認證，透過 SSH 連線存取主控台。

如需相關資訊，請參閱[訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)。

## 相關鏈結
{: #managingfsa-related}

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [fortinet.com 網站](https://www.fortinet.com/)
* [Fortinet 文件庫](https://docs.fortinet.com/product/fortigate/6.2)

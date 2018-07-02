---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-11"

---

# 管理 FortiGate Security Appliance on IBM Cloud

順利安裝 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務之後，即可從 FortiGate 主控台管理及配置 FSA 的防火牆規則。

**重要事項**：您必須確定已定義 FSA 防火牆規則為容許由管理元件（例如 IBM CloudDriver 虛擬機器或 Zerto Virtual Manager）起始的出埠 HTTPS（TCP 埠 443）通訊，以透過網際網路與 IBM Cloud 基礎架構上的外部管理資料庫通訊。出埠 HTTPS（TCP 埠 443）通訊源自實例中管理服務「VMware NSX Edge Services 閘道 (ESG)」的公用 IP 位址。

## 存取 FortiGate 300 系列主控台

若要管理 FortiGate Security Appliance on {{site.data.keyword.cloud}} 服務，您必須使用下列其中一種方式來存取 FortiGate® 300 系列主控台：
* 使用您可以在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的認證，登入 FortiOS Web Client。
* 使用您可以在 FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到的認證，透過 SSH 連線存取主控台。

如需相關資訊，請參閱下列主題：
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)

## 相關鏈結

* [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 概觀](fsa_considerations.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [fortinet.com 網站](https://www.fortinet.com/)
* [Fortinet 技術文件](http://docs.fortinet.com/fortigate/admin-guides)

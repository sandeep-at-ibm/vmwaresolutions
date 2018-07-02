---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# 協助的疑難排解

## 問題

在某些狀況下，可能會發生更複雜的問題，而日誌檔不足以完成主要原因分析及提供解決方案。

## 解決方法

為了對這種類型的問題進行疑難排解及解決問題，{{site.data.keyword.vmwaresolutions_full}} 支援團隊需要存取 {{site.data.keyword.cloud_notm}} 管理虛擬機器 (VM)。這部管理 VM 稱為 IBM CloudDriver，是用來管理已部署的 VMware Cloud Foundation 實例及 VMware vCenter Server 實例的主要介面。

基於安全理由，會限制 IBM CloudDriver 的存取權。{{site.data.keyword.vmwaresolutions_short}} 支援團隊會要求客戶核准，並且在取得它之後，團隊可以使用 {{site.data.keyword.cloud_notm}} 基礎架構虛擬伺服器來存取 CloudDriver 元件。此伺服器透過 {{site.data.keyword.cloud_notm}} 基礎架構前端客戶路由器 (FCR) 公用網路來橋接至環境。

接下來，{{site.data.keyword.vmwaresolutions_short}} 支援團隊會使用為了該實例的訂購及配置而提供的 {{site.data.keyword.cloud_notm}} 基礎架構 {{site.data.keyword.slapi_short}} 金鑰（或者，如有必要，則為客戶所提供的已更新金鑰），來部署每小時的 {{site.data.keyword.cloud_notm}} 基礎架構虛擬伺服器。

基於疑難排解目的，會向客戶帳戶收取使用 IBM CloudBuilder 工具的費用。完成除錯及補救之後，會釋放 IMB CloudBuilder 元件。

用於疑難排解的 {{site.data.keyword.cloud_notm}} 基礎架構虛擬伺服器是使用下列規格來部署：

* CentOS 7 公用節點 VSI（虛擬服務實例）與 1 個 CPU 和 1 GB RAM 搭配使用。
* VSI 會部署在該實例所在的相同主要公用和專用 VLAN 上的相同資料中心。
* 後置安裝 Script 與 VSI 部署搭配使用，以設定防火牆規則，此規則只容許從 {{site.data.keyword.vmwaresolutions_short}} 支援團隊所擁有及使用的一組特定 IP 位址送入的 SSH 連線。
* 一個支援啟動系統，它使用在 {{site.data.keyword.cloud_notm}} 基礎架構 VM 上執行的那些 IP 位址，且只能透過專用的 {{site.data.keyword.cloud_notm}} 基礎架構網路進行存取，並受到一對 HA（高可用性）{{site.data.keyword.cloud_notm}} 基礎架構 Vyatta 系統保護。
* 使用了 IBM Security 工具（例如 QRadar®、Nessus 及 IBM BigFix®）來監視支援啟動系統，以防範任何安全威脅。

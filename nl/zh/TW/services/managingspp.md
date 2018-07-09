---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# 管理 IBM Spectrum Protect Plus on IBM Cloud

## 存取 IBM Spectrum Protect Plus 管理主控台

若要管理 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} 服務，您必須完成下列步驟來存取 IBM Spectrum Protect Plus 管理主控台：
1. 使用 {{site.data.keyword.cloud_notm}} 基礎架構 VPN 或跳躍伺服器，以容許存取 IBM Spectrum Protect Plus 虛擬機器 (VM) 的 IP 位址。您可以在 {{site.data.keyword.vmwaresolutions_short}} 主控台的 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務詳細資料頁面上找到 IP 位址。
2. 若要存取 IBM Spectrum Protect Plus 管理主控台，請在 IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} 服務詳細資料頁面上按一下**檢視 IBM Spectrum Protect Plus 主控台**，然後使用相同服務詳細資料頁面上所列出的認證來登入。

## 將更新套用至 IBM Spectrum Protect Plus on IBM Cloud

您負責維護 IBM Spectrum Protect Plus，以保持更新至最新版本。您可以從[IBM Spectrum Protect Plus 支援中心](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus)頁面下載必要更新。

如需相關資訊，請參閱下列主題：
* [訂購、檢視及移除 Cloud Foundation 實例的服務](../sddc/sd_addingremovingservices.html)
* [訂購、檢視及移除 vCenter Server 實例的服務](../vcenter/vc_addingremovingservices.html)

## 更新 IBM Spectrum Protect Plus VM 的作業系統

若要更新 IBM Spectrum Protect Plus VM 的作業系統，您必須以 **root** 使用者身分登入。**root** 使用者是與 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 的服務詳細資料頁面上的密碼相同。

## 備份及還原已安裝 IBM Spectrum Protect Plus on IBM Cloud 之實例的管理元件

**附註**：下列資訊適用於部署在（或升級至）2.3 版或更新版本之實例上的 IBM Spectrum Protect Plus 安裝。對於 2.2 版實例，此服務僅為工作負載 VM 提供資料保護。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務已預先配置管理備份工作，而此管理備份工作會自動執行。此工作每日執行，且最多使用七個還原點來備份下列管理元件：
* VMware vCenter Server
* Platform Services Controller (PSC)
* IBM CloudDriver
* **僅限 Cloud Foundation 實例**：VMware SDDC Manager
* **僅限含 HA AD/DNS 的 vCenter Server 實例**：AD/DNS 的高可用性配對

如果管理元件失敗，您可以藉由[與 IBM 支援中心聯絡](../vmonic/trbl_support.html)來開立問題單，要求將管理元件還原至前一個備份。

## 相關鏈結

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 概觀](spp_considerations.html)
* [如何增加 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 後置部署的 vsnap 儲存空間](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [IBM Spectrum Protect Plus 文件](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)

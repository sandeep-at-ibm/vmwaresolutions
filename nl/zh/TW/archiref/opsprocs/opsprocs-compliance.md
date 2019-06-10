---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# 法規遵循
{: #opsprocs-compliance}

「法規遵循」是一組必須符合最低控制的需求，這些控制是由管制機構或產業最佳作法所建立。法規遵循架構通常是廣泛的架構，提供廣泛範圍的技術指引，而來自廠商的產業最佳作法則通常是專門解決技術風險的技術。

對於您的 vCenter Server 實例，我們建議使用專用團隊後置部署來管理安全。這項權責區分應該會擴增並監視您實例的安全狀態。HyTrust CloudControl 可以藉由以角色為基礎的分隔來協助您的團隊。

HyTrust DataControl 和 KeyControl 可以協助您提供工作負載保護，例如靜態加密和地理柵欄。您可能會想要部署 Caveonix RiskForesight 服務，以協助您的法規遵循需求，同時也協助您的網路風險與鑑識管理。

VMware Security Hardening Guide 提供關於如何以安全方式部署和操作 VMware 產品的規定指引。vSphere 的手冊以輕鬆使用的試算表格式提供，並附有豐富的 meta 資料，以容許進行準則分類及風險評量。它們也包含用於啟用安全自動化的 Script 範例。已提供比較文件，列出在本手冊的連續版本中，指引的變更。

雖然在 VMware Security Hardening Guide 中所記載的許多控制都已納入 {{site.data.keyword.vmwaresolutions_full}} 參考架構中，而因此會自動部署，但請務必根據自己的需要和企業原則，量身打造平台的安全狀態。VMware Security Hardening Guide 提供您需要執行這項檢閱所需的技術特有控制。Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 會自動執行這項法規遵循作業，並提供其他的法規機構指引。

vRealize Operations Manager 容許您針對 vSphere Security Configuration Guide 中的法規遵循規則，監視 VMware 物件是否發生違規。法規遵循警示會針對 vCenter Server 實例、主機、虛擬機器、分散式埠群組或分散式交換器觸發，容許進行法規遵循的違規調查。此外，對於醫療保險轉移和責任法 (HIPAA) 及支付卡產業資料安全標準 (PCI DSS) 法規遵循有興趣的客戶，可以從 VMWare Solutions Exchange 網站下載 vRealize Operations Manager 法規遵循套件、取得授權然後安裝。這些法規遵循套件提供警示、原則及報告，可根據 HIPAA 和 PCI 強化手冊驗證 vSphere 資源。


## 相關鏈結
{: #opsprocs-compliance-links}

* [VMware Security Hardening Guide](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [vSphere Security Guide](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fsa_considerations#fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-f5_considerations#f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html#hytrust-cloudcontrol-on-ibm-cloud-overview)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html#hytrust-datacontrol-on-ibm-cloud-overview)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html#hytrust-keycontrol-on-ibm-cloud-overview)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/caveonix/caveonix-intro.html#caveonix-riskforesight)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)

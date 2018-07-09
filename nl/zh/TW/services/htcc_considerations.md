---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# HyTrust CloudControl on IBM Cloud 概觀

HyTrust CloudControl on {{site.data.keyword.cloud}} 服務會施行並控制是否符合安全標準，並提供詳細角色型存取控制 (RBAC)、核准及審核功能。與 HyTrust DataControl 結合時，此服務可確保虛擬機器及工作負載資料不會離開 {{site.data.keyword.CloudDataCent_notm}} 內的特定地區、叢集或 ESXi 伺服器。

**可用性：**只有執行 vSphere 6.5 並且部署在（或升級至）2.3 版或更新版本的實例，才能使用此服務。

## HyTrust CloudControl on IBM Cloud 的元件

以「主動-被動」模式將 HyTrust CloudControl (HTCC) 應用裝置的高可用性 (HA) 配對部署至預設叢集。

每一對 HTCC 應用裝置都會部署至針對管理虛擬機器 (VM)（例如 NSX Manager、vCenter Server Appliance 及 Platform Services Controller）所指定的相同專用可攜式子網路。

應用裝置的配對用來作為 vSphere 主機的 Proxy、vCenter Server Appliance，以及實例的 NSX Manager。因此，使用者會透過管理者所指派的已發佈 IP (PIP) 位址來存取 vSphere 主機、vCenter Server Appliance 及 NSX Manager，而不是透過 {{site.data.keyword.cloud}} 所指派的實際 IP 位址 (RIP)。

HTCC 應用裝置會與 Microsoft Active Directory 整合，以強制執行角色型存取控制。

## 移除 HyTrust CloudControl on IBM Cloud 時的考量

請確定您停用已配置的 **Root 密碼加密配置檔**，並且已從 HyTrust CloudControl 中刪除所有受保護主機，再移除 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 服務。

## 相關鏈結

* [訂購 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](htcc_ordering.html)
* [管理 HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](managinghtcc.html)
* [與 IBM 支援中心聯絡](../vmonic/trbl_support.html)
* [常見問題](../vmonic/faq.html)
* [HyTrust 網站](https://www.hytrust.com/)

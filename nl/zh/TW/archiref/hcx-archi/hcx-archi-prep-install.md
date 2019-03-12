---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# 準備安裝環境
{: #hcx-archi-prep-install}

VMware HCX on IBM Cloud 安裝具有下列軟體需求：
* vSphere 5.5 U3，或是 vSphere 6.0u2 或更新版本。
* 如果使用 NSX，則為 6.2.2 版或更新版本。原則移轉需要 NSX。
* 若要使用跨雲端 vMotion，則相同親緣性限制會套用至雲端，就像在內部部署上一樣。如需相關資訊，請參閱 [VMware EVC 及 CPU 相容性常見問題](http://bit.ly/2vK6Sp5)。

## 配置網路連線功能
{: #hcx-archi-port-req-config-net}

HCX 必須遍訪公用網際網路及專用線路，並連接至資料中心元件（例如網路、交換器及埠群組）。
* [埠存取需求](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req)列出的埠必須開啟，才能順利安裝 HCX 虛擬應用裝置。
* 內部部署 vSphere 環境及 VCF/VCS HCX Cloud 環境都必須允許 vSphere 內部部署裝置及 VCF/VCS HCX 裝置中的「網路時間通訊協定 (NTP)」時鐘同步化。HCX 虛擬應用裝置及網路必須可存取 UDP 埠 123。

## 內部部署環境
{: #hcx-archi-port-req-on-prem-env}

在您安裝 HCX 之前，請驗證環境可以支援您要完成的作業。內部部署環境必須先支援下列作業，才能安裝 HCX。
* 具有 vSphere 5.5 Update 3 或 6.0 Update 2 的「虛擬中心」。
* vMotion 及原則移轉特性需要 NSX 6.2.2 版或更新版本。
* 獲指派「管理者 vCenter Server」系統角色的 vSphere 服務帳戶。
* 在 vCenter 中，要安裝的 HCX 應用裝置要有足夠的磁碟空間。
* 足夠用於安裝期間所佈建之內部部署 VM 的 IP 位址。
* 如「埠存取需求」所記載，視需要開啟埠及防火牆。
* 如果單一登入 (SSO) 伺服器在遠端，則必須識別 vCenter、「外部 SSO 伺服器」或執行外部查閱服務之 Platform Services Controller (PSC) 的 URL。向 vCenter 登錄 HCX Manager 時，必須提供此 URL。
* 如果 vCenter 沒有自己的內部查閱服務實例，則可能是因為下列其中一個原因：
  * vCenter 6.0u2 正在執行外部 Platform Services Controller。
  * vCenter 處於鏈結模式（其中，次要 vCenter 使用主要 vCenter 或外部 SSO 服務中的 SSO 服務）。

## 驗證第 2 層安裝環境
{: #hcx-archi-port-req-verify-layer-2-inst}

第 2 層網路延伸具有下列需求：
* vSphere Enterprise Plus 版本。
* vSphere vCenter 必須滿足下列需求，才能支援第 2 層延伸：
  * vSphere Enterprise Plus 授權
  * 必須有 vSphere Distributed Switch (vDS)。vSphere Enterprise Plus Edition 提供分散式交換器。
  * 安裝時，內部部署第 2 層集中器服務應用裝置必須可以存取 vNIC 埠以及任何要延伸的 VLAN。
  * 如果要透過公用網際網路或 VPN（在替代路徑上）來延伸網路，則 VCF/VCS 中的 L2C 虛擬機器需要 IP 位址。需要有遠端 IP 位址，才能配置第 2 層集中器。
  * 如果想要多個第 2 層集中器，則各在內部部署及雲端中都必須有 IP 位址。

## 相關鏈結
{: #hcx-archi-port-req-related}

* [在來源上安裝及配置 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [VMware EVC 及 CPU 相容性常見問題](http://bit.ly/2vK6Sp5)

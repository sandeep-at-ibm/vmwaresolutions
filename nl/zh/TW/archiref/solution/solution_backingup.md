---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# 備份元件

您負責配置、管理及監視所有軟體元件（包括管理基礎架構及工作負載的備份和可用性）。

在解決方案當中，您可以選擇部署 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 附加程式服務。Veeam 及 IBM Spectrum Protect Plus 可協助您滿足備份管理元件的需求。

這些附加程式服務會與「{{site.data.keyword.cloud_notm}} 耐久性」儲存空間一起部署。這些服務可協助您備份工作負載及管理元件。[IBM Spectrum Protect Plus architecture overview](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window} 及 [Veeam architecture overview](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window} 提供有關規劃及調整部署大小的有用指引。您也可以要求[受管理服務](/docs/services/vmwaresolutions/services/managing_veeam_services.html)以進行 Veeam 部署。

不同的解決方案元件需要不同的備份策略。部分元件是使用映像檔層次備份進行保護，其他元件的保護則是針對其配置及資料使用檔案型備份。

## 檔案型備份用的檔案伺服器

部分元件（例如 VMware vCenter Server、Platform Services Controller (PSC) 及 VMware NSX）需要將其配置備份至檔案伺服器。

若要管理這些備份，請使用下列步驟，將 Linux 檔案伺服器部署至叢集：

1. 從 {{site.data.keyword.cloud_notm}} 基礎架構訂購專用可攜式子網路，並將它放置在與系統元件相同的 VLAN 上。這是您主機之管理 IP 位址所在的專用 VLAN。
2. 將作業系統映像檔從 {{site.data.keyword.cloud_notm}} 專用鏡映上傳至 VMware 管理資料儲存庫（例如 Ubuntu Server 18.04 LTS）。
3. 使用先前訂購的專用可攜式 IP 位址，將此虛擬機器 (VM) 部署至管理埠群組上的叢集。請確定 VM 配置成指向 AD/DNS 伺服器，並選擇性地將 VM 新增至子網域的 DNS。
4. 在此伺服器上建立非 root 的備份使用者 ID，並確定已配置並啟動所有必要服務來進行檔案傳送。例如，FTP 或 SSH。
5. 確定此 VM 包含在您的 Veeam 或 IBM Spectrum Protect Plus 管理備份工作中。

## vCenter 檔案型備份

VMware vCenter Server 及 PSC 提供[應用裝置管理使用者介面及 API，以便使用各種通訊協定將資料庫及配置匯出至檔案伺服器](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window}。VMware 記載了如何將此作業配置成直接在 vCenter Server Appliance 及 PSC 上[以 Cron 工作的方式定期執行](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window}，且您可以針對用途進行調整的範例。

如果您有外部 PSC，則必須使用此技術個別備份 vCenter Server Appliance 及 PSC。如果您有內嵌的 PSC，則會在 vCenter 備份中包括 PSC 備份。請充分瞭解並規劃 VMware 所記載的考量及限制。此外，也請規劃檔案伺服器上檔案備份的定期輪替及到期。

VMware 需要備份位置是空的資料夾，因此，請規劃備份輪替或自動化，將位置保留空白以容納每個後續備份工作。
{:note}

## NSX 檔案型備份

發生故障時，所有 NSX 元件的適當備份對於將系統還原到工作狀態而言十分重要。此設計需要您透過 NSX Manager 備份功能來配置 NSX 備份。基於此目的，您可以[配置 NSX Manager 定期執行備份](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}至檔案伺服器。請確定正確地備份您的檔案伺服器或其資料，並確定輪替舊的 NSX 備份。

## 管理虛擬機器的映像檔型備份

部署實例並部署 IBM Spectrum Protect Plus 服務或 Veeam 備份服務之後，請配置管理虛擬機器的備份工作。請規劃備份下列 VM，至少要有 7 天的每日備份：

* （如果存在）VMware SDDC Manager
* （如果存在）Active Directory 伺服器
* 檔案備份伺服器

規劃配置足夠的 Veeam 或 IBM Spectrum Protect Plus 授權來備份這些虛擬機器，並為 VM 規劃至少 2 TB 的備份儲存空間。

## 附加服務               

如果您將附加程式解決方案元件部署至實例，則也應該規劃這些元件的備份，作為管理備份策略的一部分：

* Zerto Virtual Replication：Zerto Virtual Manager (ZVM) 系統部署為 {{site.data.keyword.cloud_notm}} 虛擬伺服器實例 (VSI)，而且 Veeam 或 IBM Spectrum Protect Plus 不支援其備份。如果災難回復策略需要您回復 ZVM，而不執行站台失效接手，則您應該使用偏好的 Windows 備份解決方案來備份及還原 ZVM。
* F5 BIG-IP：F5 建議 [F5 配置的檔案型備份](https://support.f5.com/csp/article/K13132){:new_window}，您可以將它導向至檔案伺服器。
* FortiGate Security Appliance 或 VM：Fortinet 建議 [FortiGate 配置的檔案型備份](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}，您可以將它導向至檔案伺服器。
* HyTrust CloudControl 及 DataControl：HyTrust 同時支援 HyTrust 伺服器應用裝置的映像檔及檔案型備份。如需相關資訊，請參閱 HyTrust 管理手冊。
* VMware HCX：HCX 應用裝置管理介面容許您建立及下載與 vCenter Server Appliance 類似的 HCX 管理程式配置檔案型備份。

## 其他考量

如果您選擇將 AD/DNS 伺服器部署為 {{site.data.keyword.cloud_notm}} 虛擬伺服器實例 (VSI)，則無法使用 Veeam 或 IBM Spectrum Protect Plus 進行備份。在此情況下，請使用偏好的 Windows 備份解決方案來進行備份及還原作業，或規劃使用 VMware 叢集內的 AD/DNS VM 來部署實例，如此便可藉由 Veeam 或 IBM Spectrum Protect Plus 進行備份。

從 VMware vCenter 6.5u2 開始，VMware 支援使用映像檔型備份來備份 vCenter Postgres 資料庫，並且在備份時間範圍期間可以使用資料庫的整合式暫停及繼續 Script，以確保資料庫完整性。如果您將 VMware 實例升級至 vCenter 6.5u2，則可以選擇使用 Veeam 或 IBM Spectrum Protect Plus 來備份 vCenter Server 及 PSC，而不使用檔案型備份。如果您這麼做，則必須使用 Veeam 或 IBM Spectrum Protect Plus 靜止特性，以確保資料庫完整性。

## 從備份還原

當您還原管理備份時，有數個特殊考量：

* 對於 vCenter 及 PSC，VMware 提供安裝程式，以部署新的虛擬應用裝置並從備份還原配置。
* 從備份中還原應用裝置時，安裝程式會根據您提供的備份資訊，來偵測應用裝置的類型（vCenter Server、PSC 或具有內嵌 PSC 的 vCenter）。
* 因為您直接部署至其中一部主機，所以可能無法部署至分散式交換器或埠群組。您可能需要建立暫時標準交換器及埠群組來部署已回復的應用裝置，並暫時將其中一張 vmnic 移轉至此交換器，以提供 VM 的網路連線功能。部署之後，您可以將 VM 移轉至分散式埠群組，並將 vmnic 退回給 dvSwitch。
* 對於 NSX，您可能需要先重新部署 NSX Manager 及控制器，再從備份還原配置。
* 確定您充分瞭解 vCenter 備份及還原的 VMware 考量和限制。

## 摘要 

經過適當的規劃，您可以確保 VMware 實例能夠承受遺失其管理元件，並順利回復。請務必定期監視備份工作的成功執行，以及備份資料的可用性，並且務必針對您的管理基礎架構及工作負載定期測試備份及還原方案。

### 相關鏈結

* [解決方案概觀](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
* [設計概觀](/docs/services/vmwaresolutions/archiref/solution/design_overview.html)
* [調整容量](/docs/services/vmwaresolutions/archiref/solution/solution_scaling.html)

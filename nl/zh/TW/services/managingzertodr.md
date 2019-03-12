---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 管理 Zerto on IBM Cloud
{: #managingzertodr}

將 Zerto on {{site.data.keyword.cloud}} 服務部署至實例之後，即可配置或更新 Zerto Virtual Replication，並將更多 Virtual Replication Appliance 部署至新增的 ESXi 伺服器。

## 使用您自己的 Zerto 憑證
{: #managingzertodr-ssl-cert}

最佳作法是將您自己的 SSL 憑證用於 Zerto Virtual Manager (ZVM)。部署 Zerto on {{site.data.keyword.cloud_notm}} 之後，請將 ZVM 的 SSL 憑證取代為您自己的憑證。如需相關資訊，請參閱[如何使用 CER SSL 憑證以取代 ZVM、ZSSP 或 ZCM 的自簽憑證](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window}。

## 管理 Zerto 抄寫的配置
{: #managingzertodr-manage}

若要管理 Zerto 抄寫的配置，請使用具有管理者許可權的 vCenter 認證來登入 Zerto Virtual Replication 主控台。例如，修復 Zerto 實例或配置虛擬保護群組以抄寫虛擬機器。

當您要在不同的 {{site.data.keyword.cloud_notm}} Zerto 實例之間抄寫時，可以直接在 Zerto 實例之間配置抄寫。如果您要在 {{site.data.keyword.cloud_notm}} Zerto 實例與您自己的資料中心之間進行抄寫，則必須自行在自己的資料中心內安裝 Zerto。此實例與 {{site.data.keyword.cloud_notm}} Zerto 實例配對時，本身可以自動授權它自己。

Zerto 抄寫不支援「網址轉換 (NAT)」遍訪。在 {{site.data.keyword.cloud_notm}} Zerto 實例與您自己的資料中心之間建立連線時，可能需要自訂另一端之 Zerto Virtual Manager (ZVM) 應用裝置或 Zerto Virtual Replication Appliance (VRA) 上的路徑。建立連線也可能需要站台之間進行安全通道作業。當您要配置或重新配置 ZVM 應用裝置上的路徑時，必須確定所有 ZVM 應用裝置都可以順利連接至 `zerto.com` 以進行使用情形報告。您可以從 ZVM 應用裝置將瀏覽器階段作業開啟到 `https://www.zerto.com`，來驗證此連線。

{{site.data.keyword.cloud_notm}} 上 Cloud Foundation 實例及 vCenter Server 實例的 Management VMware NSX Edge Services Gateway (ESG)，已預先配置成容許源自 ZVM 的出埠 HTTP（TCP 埠 443）通訊。{:note}

## 更新 Zerto Virtual Replication
{: #managingzertodr-update}

若要更新 Zerto Virtual Replication，請登入 Zerto Virtual Replication 主控台。

## 將 VRA 部署至新增的 ESXi 伺服器
{: #managingzertodr-deploy}

當您新增或移除實例主要叢集的 ESXi 伺服器時，會自動部署或移除 VRA。VRA 不會自動部署至實例次要叢集裡的 ESXi 伺服器。您可以從 Zerto Virtual Replication 主控台自行部署 VRA。

## 相關鏈結
{: #managingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [要求 Zerto on {{site.data.keyword.cloud_notm}} 的受管理服務](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com 網站](https://www.zerto.com){:new_window}
* [Zerto 技術文件](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Zerto 災難回復](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Zerto Virtual Replication 警示說明](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)

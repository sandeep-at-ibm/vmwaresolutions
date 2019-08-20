---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-30"

keywords: vCenter Server networking, networking components, networking vCenter

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}

# vCenter Server 實例的網路考量
{: #vc_networkingonvcenterserver}

如需 vCenter Server on {{site.data.keyword.cloud}} 實例之網路考量及需求的詳細資料，請檢閱下列資訊。請確定您符合需求，讓實例能夠正常運作。

## vCenter Server 實例的網路元件
{: #vc_networkingonvcenterserver-networking-components}
{: faq}

若要檢閱 vCenter Server 實例中所含的網路元件，請參閱 [vCenter Server 實例的技術規格](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)。

## 防火牆考量
{: #vc_networkingonvcenterserver-firewall-considerations}
{: faq}

如果您使用防火牆，則必須針對來自 {{site.data.keyword.IBM}} CloudDriver 虛擬伺服器實例 (VSI) 及 SDDC Manager 虛擬機器 (VM) 的所有通訊配置規則。這些規則必須容許所有通訊協定在 IP 位址 `10.0.0.0/8` 及 `161.26.0.0/16` 上進行通訊。這類防火牆的範例包含 NSX Distributed Firewall (DFW) 或 Vyatta 防火牆。

## 使用 NSX 與虛擬機器搭配
{: #vc_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

在 vCenter Server 實例部署期間，會在實例中訂購、安裝、授權及配置 VMware NSX。同時，會設定 NSX Manager、NSX Controller 及「NSX 傳輸區域」，且每一部 ESXi 伺服器中都配置了 NSX 元件。

也會部署 NSX Edge Services Gateway，供您的工作負載虛擬機器 (VM) 使用。如需相關資訊，請參閱[配置網路以使用客戶管理的 NSX ESG 來搭配您的 VM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

## 變更 NSX 元件密碼時的考量
{: #vc_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

在嘗試變更 NSX Manager、NSX Controller 及 NSX Edge 的密碼之前，請檢閱下列考量：
* 您可以變更 NSX Manager 密碼。此密碼顯示在 {{site.data.keyword.vmwaresolutions_short}} 主控台中實例的**摘要**頁面上。
* 您可以變更 NSX Controller 的密碼。如需如何變更這些密碼的指示，請參閱[變更控制器密碼](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html){:external}。
* 您可以變更客戶管理的 VMware NSX Edge Services Gateway (ESG) 的密碼和 SSH 設定。 
* 不要變更 Management VMware NSX Edge Services Gateway (ESG) 及相關「分散式邏輯路由器」的密碼。

## 相關鏈結
{: #vc_networkingonvcenterserver-related}

* [Overview of NSX](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:external}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:external}
* [Managing NAT Rules](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}

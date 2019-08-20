---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-16"

keywords: vCenter Server multi-site, multi-site configuration, multi-site deployment vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server on IBM Cloud 實例的多站台配置
{: #vc_multisite}

{{site.data.keyword.vmwaresolutions_full}} 容許在不同的位置部署實例，並在短時間內啟動並執行它們。

僅針對 2.0 版以及更新版本的實例支援 vCenter Server 實例的多站台配置。
{:note}

## 多站台部署元件
{: #vc_multisite-deployment-components}

多站台部署包含下列元件。

* **主要實例**：主要 VMware vCenter Server 實例具有下列配置：
  * Microsoft Active Directory (AD) 及 DNS（網域名稱系統）根網域
  * vCenter Server 子網域
  * SSO（單一登入）網域
  * SSO 站台名稱
  * 若為 2.8 版或更新版本中部署的主要實例：具有內嵌 Platform Services Controller (PSC) 的 vCenter Server Appliance (vCSA)
* **次要實例**：一個以上鏈結至主要實例的次要 vCenter Server 實例，其具有下列配置：
  * SSO 站台名稱
  * 鏈結至主要實例上之根網域的 DNS 子網域
  * 主要實例及次要實例上的 AD 虛擬機器之間的 DNS 及 AD 抄寫設定
  * 使用「加強型鏈結模式」將次要實例上的 VMware vCenter 設定為主要實例上的 vCenter

## vCenter Server 多站台部署
{: #vc_multisite-deployment}

多站台配置特性會搭配使用中心及分支拓蹼與主要站台及最多七個次要站台。支援單層站台，亦即，您無法配置鏈結至其他次要站台的後續站台。在所有實例中，您在多站台配置中共有 128 部 ESXi 伺服器。

如果您的配置需要超過 128 部 ESXi 伺服器的多站台部署，請與「IBM 支援中心」聯絡以取得協助。如需相關資訊，請參閱[與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。
{:note}

下圖說明 vCenter Server 多站台部署的整體視圖。

![vCenter Server 多站台部署](../images/multisite-hub-spoke.svg "vCenter Server 多站台部署")

此模型包含下列各層：

* **主要實例**：在多站台配置中，若要部署第一個實例，請在實例訂購處理程序期間將該實例定義為主要實例。
* **次要實例**：在多站台配置中，您會在訂購處理程序期間將連接至主要實例的實例定義為次要實例。

一次只能將一個次要實例指派給主要實例。您無法同時將多個次要實例指派給主要實例。若要這麼做，您必須重新進行訂購處理程序，並選取先前定義的主要實例作為次要實例的主要實例。您必須對您要建立的所有次要實例重複此程序。

您最多可以在多站台配置中部署 8 個（1 個主要及 7 個次要）實例。

刪除屬於多站台配置的 vCenter Server 實例需要特殊規劃。如需相關資訊，請參閱[刪除多站台配置中的 vCenter Server 實例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance_multi)。
{:note}

## 相關鏈結
{: #vc_multisite-related}

* [Assign Primary Role to NSX Manager](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:external}
* [Configuring Secondary NSX Managers](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:external}
* [Microsoft Active Directory Trusts supported with VMware vCenter Single Sign-On](https://kb.vmware.com/s/article/2064250){:external}

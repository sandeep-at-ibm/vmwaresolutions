---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:faq: data-hd-content-type='faq'}

# vCenter Server with Hybridity Bundle インスタンスのネットワーキングに関する考慮事項
{: #vc_hybrid_networkingonvcenterserver}

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスのネットワーキングの考慮事項と要件についての詳細情報を以下に示します。 インスタンスが正常に機能するように、要件を満たしていることを確認してください。

## vCenter Server with Hybridity Bundle インスタンスのネットワーキング・コンポーネント
{: #vc_hybrid_networkingonvcenterserver-networking-components}
{: faq}

vCenter Server with Hybridity Bundle インスタンス内に組み込まれているネットワーキング・コンポーネントを確認するには、[vCenter Server with Hybridity Bundle インスタンスの技術仕様](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs)を参照してください。

## ファイアウォールに関する考慮事項
{: #vc_hybrid_networkingonvcenterserver-firewall-considerations}
{: faq}

ファイアウォールを使用している場合は、{{site.data.keyword.IBM}} CloudDriver 仮想サーバー・インスタンス (VSI) と SDDC Manager 仮想マシン (VM) からのすべての通信に関してルールを構成する必要があります。 これらのルールでは、すべてのプロトコルが IP アドレス `10.0.0.0/8` と `161.26.0.0/16` 上で通信できるよう許可する必要があります。 このようなファイアウォールの例としては、NSX Distributed Firewalls (DFW)、Vyatta ファイアウォールなどがあります。

## 仮想マシンでの NSX の使用
{: #vc_hybrid_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

vCenter Server インスタンスのデプロイメント中に、インスタンスで VMware NSX が注文され、インストールされ、ライセンスを適用され、構成されます。 また、NSX Manager、NSX Controllers、および NSX Transport Zone がセットアップされ、各 ESXi サーバーに NSX コンポーネントが構成されます。

ワークロード仮想マシン (VM) で使用するための NSX Edge Services Gateway もデプロイされます。 詳しくは、[ユーザー管理の NSX ESG を VM で使用するためのネットワークの構成](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)を参照してください。

## NSX コンポーネントのパスワードを変更する際の考慮事項
{: #vc_hybrid_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

NSX Manager、NSX Controllers、NSX Edges のパスワードを変更する前に、以下の考慮事項を確認してください。
* {{site.data.keyword.vmwaresolutions_short}} コンソールのインスタンスの**「サマリー」**ページに表示される NSX Manager のパスワードは変更しないでください。
* NSX Controller のパスワードは変更できます。 NSX Controller のパスワードを変更する方法については、[コントローラ パスワードの変更](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)を参照してください。
* ユーザー管理の VMware NSX Edge Services Gateway (ESG) のパスワードと SSH 設定を変更できます。 Management VMware NSX Edge Services Gateway (ESG) および関連する Distributed Logical Router のパスワードは変更しないでください。

## 関連リンク
{: #vc_hybrid_networkingonvcenterserver-related}

* [NSX の概要](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [NAT ルールの管理](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
* [VMware HCX on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vmware-hcx-on-ibm-cloud-overview)

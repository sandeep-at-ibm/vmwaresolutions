---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# vCenter Server with Hybridity Bundle インスタンスのネットワーキングに関する考慮事項

VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスのネットワーキングの考慮事項と要件についての詳細情報を以下に示します。 インスタンスが正常に機能するように、要件を満たしていることを確認してください。

## vCenter Server with Hybridity Bundle インスタンスのネットワーキング・コンポーネント

vCenter Server with Hybridity Bundle インスタンスに含まれているネットワーキング・コンポーネントを確認するには、[vCenter Server with Hybridity Bundle の概要](vc_hybrid_overview.html)の『_vCenter Server with Hybridity Bundle の技術仕様_』セクションを参照してください。

## NSX ファイアウォールに関する考慮事項

NSX 分散ファイアウォール (DFW) を使用する場合は、以下の要件を確認してください。
* {{site.data.keyword.IBM}} CloudDriver 仮想マシン (VM) からのすべての通信のために、IP アドレス `10.0.0.0/8` および `161.26.0.0/16` でのすべてのプロトコルの通信を許可するルールを構成する必要があります。
* IBM CloudDriver VM から任意の宛先への HTTPS トラフィックが可能になるように、DFW ルールを作成する必要があります。
* DFW ルールは、これらの VM との間のトラフィックをブロックする他のルールの前に配置する必要があります。

## 仮想マシンでの NSX の使用

vCenter Server インスタンスのデプロイメント中に、インスタンスで VMware NSX が注文され、インストールされ、ライセンスを適用され、構成されます。 また、NSX Manager、NSX Controllers、および NSX Transport Zone がセットアップされ、各 ESXi サーバーに NSX コンポーネントが構成されます。

ワークロード VM で使用するための NSX Edge Services Gateway もデプロイされます。 詳しくは、[ユーザー管理の NSX ESG を VM で使用するためのネットワークの構成](vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)を参照してください。

## NSX コンポーネントのパスワードを変更する際の考慮事項

NSX Manager、NSX Controllers、NSX Edges のパスワードを変更する前に、以下の考慮事項を確認してください。
* {{site.data.keyword.vmwaresolutions_short}} コンソールのインスタンスの**「サマリー」**ページに表示される NSX Manager のパスワードは変更しないでください。
* NSX Controller のパスワードは変更できます。 NSX Controller のパスワードを変更する方法については、[コントローラ パスワードの変更](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)を参照してください。
* ユーザー管理の VMware NSX Edge Services Gateway (ESG) のパスワードと SSH 設定を変更できます。 Management VMware NSX Edge Services Gateway (ESG) および関連する Distributed Logical Router のパスワードは変更しないでください。

## 関連リンク

* [NSX の概要](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [NAT ルールの管理](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}
* [VMware HCX on IBM Cloud の概要](../services/hcx_considerations.html)

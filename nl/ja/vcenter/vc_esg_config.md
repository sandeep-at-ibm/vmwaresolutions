---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server network config, network configuration, manage NSX ESG

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# ユーザー管理の NSX ESG を VM で使用するためのネットワークの構成
{: #vc_esg_config}

VMware vCenter Server インスタンスにデプロイされている VMware NSX Edge Services Gateway (ESG) を活用できるように、仮想マシンのネットワークを構成します。 セキュリティー・リスクを最小化するために適用されるセキュリティー対策について詳しくは、[管理サービスの NSX Edge にはセキュリティーのリスクがありますか?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-) を参照してください。

VMware NSX は、分離したネットワークの仮想化を可能にし、スイッチ、ルーティング、ファイアウォールなどの複数のネットワーク・サービスを提供するネットワーク仮想化プラットフォームです。 NSX について詳しくは、[NSX の概要](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:external}を参照してください。

vCenter Server インスタンスの注文プロセスの中で、以下のアクションが自動的に実行されます。
* VM (仮想マシン) が {{site.data.keyword.cloud}} インフラストラクチャーのプライベート・ネットワークにアクセスするために使用する、プライベート・カスタマー・サブネットが注文されます。
* VM がインターネットにアクセスするための、パブリック・カスタマー・サブネットが注文されます。
* NSX が vCenter Server インスタンスにデプロイされ、構成されます。
* サンプルの NSX 論理スイッチが、お客様のワークロード VM で使用するためにデプロイされます。
* レイヤー 2 (L2) ネットワークに接続されているローカル・ワークロード間で実行される可能性のある東西通信用のサンプル NSX 分散論理ルーター (DLR) がデプロイされます。
* NSX Edge アプライアンスがデプロイされ、NAT ルールでワークロード論理スイッチの IP アドレスの範囲をパブリック IP アドレスに変換するネットワーク・アドレス変換 (NAT) を実行するように構成されます。

  プライベート専用であるインスタンスの場合、NSX edge はデプロイされません。
  {:note}

* {{site.data.keyword.cloud_notm}} サービスに Veeam をインストールした場合は、NSX Manager が NSX 構成の日次バックアップを実行するように構成されます。 詳しくは、[{{site.data.keyword.cloud_notm}} に Veeam をインストールする際の考慮事項](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations#considerations-when-you-install-veeam-on-ibm-cloud)を参照してください。

## VM のネットワーク設定を構成する手順
{: #vc_esg_config-procedure-config-networking}

ワークロード VM に NSX を利用するには、VM の作成時に次の手順を実行して、いくつかの設定を構成する必要があります。

1. VM のネットワーク・アダプターにワークロード論理スイッチを設定します。
   1. **「新規仮想マシン」**ダイアログ・ボックスで、**「ハードウェアのカスタマイズ」**タブをクリックします。
   2. **「新規デバイス」**メニューで、**「ネットワーク」**を選択し、**「追加」**をクリックします。
   3. 新しく追加されたネットワーク・アダプターで、メニューからワークロード論理スイッチを選択します。 ワークロード論理スイッチの名前の例は **vxw-dvs-17-virtualwire-1-sid-6000-Workload** です。

   **「ワークロード・トランジット」**スイッチを選択しないようにしてください。
   {:important}

2. VM で使用可能な IP アドレスを指定します。
   *  IP アドレスは `192.168.10.0/24` の範囲内にする必要があります。 IP アドレス `192.168.10.1` は予約されていることに注意してください (**手順 3** を参照)。
   *  VM で実行するオペレーティング・システムのネットワーキングを構成するときに、選択した IP アドレスとネットマスク `255.255.255.0` を使用します。

   VM に割り当てた IP アドレスの範囲を管理する作業は、お客様が行います。
   {:note}

3. VM のデフォルト・ゲートウェイに `192.168.10.1` を割り当てます。 このアドレスは、ワークロード VM と同じ論理スイッチ上の NSX DLR の IP アドレスです。

## SNAT ルールを有効にする手順
{: #vc_esg_config-procedure-enable-snat-rule}

ワークロード VM にインターネットへのアウトバウンド・アクセスを許可するには、関連付けられた SNAT (送信元ネットワーク・アドレス変換) ルールを有効にする必要があります。 SNAT ルールを有効にすると、VM からのインターネット・アクセスを単一のパブリック IP アドレスに変換できます。 VMware vSphere Web Client で以下の手順を実行します。

1. **「ホーム」>「ネットワークとセキュリティ」**をクリックします。
2. ナビゲーター・ペインで**「NSX Edge」**をクリックし、**customer-nsx-edge** という名前のエッジをダブルクリックします。
3. **「管理」>「NAT」**をクリックして、**「NAT」**タブを開きます。
4. テーブルでデフォルトの SNAT ルールを選択し、テーブルの上にある緑色のチェック・マークをクリックしてそのルールを有効にします。

NSX Edge NAT ルールについて詳しくは、[NAT ルールの管理](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}を参照してください。

## カスタマー・サブネットの詳細を指定する手順
{: #vc_esg_config-procedure-identify-customer-subnets-details}

**customer-nsx-edge** はお客様専用のエッジであるため、変更して、インバウンドまたはアウトバウンドのトラフィックに対する追加の NAT ルールを定義できます。 それらのルールでは、自動的に注文されたパブリックまたはプライベートのカスタマー・サブネットの IP アドレスだけを使用する必要があります。

注文された IP アドレスを使用するためにカスタマー・サブネットの詳細を確認するには、VMware vSphere Web Client で以下の手順を実行します。

1. **「ホーム」>「ネットワークとセキュリティ」**をクリックします。
2. ナビゲーター・ペインで、**「NSX Edge」**をクリックし、右側のペインのエッジ・リストで **customer-nsx-edge edge** を見つけます。
3. **「説明」**列で、**customer-nsx-edge** のエッジの説明にカーソルを合わせると、プライベートおよびパブリックのカスタマー・サブネットのサブネット識別子が表示されます。

また、{{site.data.keyword.slportal}}で以下の手順を実行して、カスタマー・サブネットについてのさらに詳しい情報を得ることができます。

1. **「ネットワーキング」>「IP 管理」>「サブネット」**をクリックします。
2. フィルター・メニューをクリックし、VMware vSphere Web クライアントの **customer-nsx-edge** の説明に表示されていた識別子を**「サブネット」**フィールドに入力します。
3. IP アドレスについて表示されるメモを確認します。 これらのメモに、初期セットアップ時に注文され、使用されたサブネットと IP アドレスが示されています。

   初期セットアップ時に注文され、使用された IP アドレスは使用しないでください。 ただし、必要に応じてこれらのサブネット上の他の IP アドレスを使用できます。 追加のネットワーク・アドレス変換ルールをセットアップするには、[NAT ルールの管理](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}を参照してください。
   {:important}

## 関連リンク
{: #vc_esg_config-related}

* [トラブルシューティング](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:external}

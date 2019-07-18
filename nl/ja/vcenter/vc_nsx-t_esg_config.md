---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: vCenter Server network config, network configuration NSX-T, manage NSX-T ESG

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# ユーザー管理の NSX-T ESG を VM で使用するためのネットワークの構成
{: #vc_nsx-t_esg_config}

VMware vCenter Server インスタンスにデプロイされている VMware NSX-T Edge Services Gateway (ESG) を活用できるように、仮想マシンのネットワークを構成します。 セキュリティー・リスクを最小化するために適用されるセキュリティー対策について詳しくは、[管理サービスの NSX Edge にはセキュリティーのリスクがありますか?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-) を参照してください。

VMware NSX-T は、分離したネットワークの仮想化を可能にし、スイッチ、ルーティング、ファイアウォールなどの複数のネットワーク・サービスを提供するネットワーク仮想化プラットフォームです。 NSX について詳しくは、[NSX の概要](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:external}を参照してください。

vCenter Server with NSX-T インスタンスの注文プロセスの中で、以下のアクションが自動的に実行されます。
* VM (仮想マシン) が {{site.data.keyword.cloud}} インフラストラクチャーのプライベート・ネットワークにアクセスするために使用する、プライベート・カスタマー・サブネットが注文されます。
* VM がインターネットにアクセスするための、パブリック・カスタマー・サブネットが注文されます。
* NSX-T が vCenter Server with NSX-T インスタンスにデプロイされ、構成されます。
* サンプルの NSX-T 論理スイッチが、お客様のワークロード VM で使用するためにデプロイされます。
* レイヤー 2 (L2) ネットワークに接続されているローカル・ワークロード間で実行される可能性のある東西通信用のサンプル NSX-T ティア 1 ルーターがデプロイされます。
* NSX-T Edge アプライアンスがデプロイされ、NAT ルールでワークロード論理スイッチの IP アドレスの範囲をパブリック IP アドレスに変換するネットワーク・アドレス変換 (NAT) を実行するように構成されます。

  プライベート専用であるインスタンスの場合、NSX-T edge はデプロイされません。
  {:note}

## VM のネットワーク設定を構成する手順
{: #vc_nsx-t_esg_config-procedure-config-networking}

ワークロード VM に NSX-T を利用するには、VM の作成時に次の手順を実行して、いくつかの設定を構成する必要があります。

1. VM のネットワーク・アダプターにワークロード論理スイッチを設定します。
   1. **「新規仮想マシン」**ダイアログ・ボックスで、**「ハードウェアのカスタマイズ」**タブをクリックします。
   2. **「新規デバイス」**メニューで、**「ネットワーク」**を選択し、**「追加」**をクリックします。
   3. 新しく追加されたネットワーク・アダプターで、メニューからワークロード・オーバーレイ論理スイッチを選択します。 サンプルのスイッチの名前は **overlay-ls** です。

   **「ワークロード・トランジット」**スイッチを選択しないようにしてください。
   {:important}

2. VM で使用可能な IP アドレスを指定します。
   *  IP アドレスは `192.168.10.0/24` の範囲内にする必要があります。 IP アドレス `192.168.10.1` は予約されていることに注意してください (**手順 3** を参照)。
   *  VM で実行するオペレーティング・システムのネットワーキングを構成するときに、選択した IP アドレスとネットマスク `255.255.255.0` を使用します。

   VM に割り当てた IP アドレスの範囲を管理する作業は、お客様が行います。
   {:note}

3. VM のデフォルト・ゲートウェイに `192.168.10.1` を割り当てます。 これは、お客様のティア 1 論理ルーターのダウンリンク・ルーター・ポートの IP アドレスで、接続先はワークロード VM と同じオーバーレイ論理スイッチになります。

## SNAT ルールの有効化
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

NSX-T では、デフォルトで SNAT ルールが有効になります。 既存のルールの変更については、[Configure Source and Destination NAT on a Tier-0 Logical Router](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:external} を参照してください。

## カスタマー・サブネットの詳細を指定する手順
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

論理ルーター **Customer-T1-LR** と **Customer-T0-LR** も、エッジ **cust-nsx-edge0** と **cust-nsx-edge1** もお客様用として用意されているので、お客様の側で変更して、インバウンド・トラフィックやアウトバウンド・トラフィックに関する NAT ルールをさらに定義できるようになっています。 それらのルールでは、自動的に注文されたパブリックまたはプライベートのカスタマー・サブネットの IP アドレスだけを使用する必要があります。

注文された IP アドレスを使用するためにカスタマー・サブネットの詳細を確認するには、NSX-T Web Client で以下の手順を実行します。

1. **「拡張ネットワーキングとセキュリティー (Advanced Networking & Security)」**タブをクリックします。
2. 左側のペインで**「ファブリック」**をクリックし、ドロップダウン・リストから**「ノード」**を選択します。
3. そのタブで**「エッジ・トランスポート・ノード (Edge Transport Nodes)」**を選択します。
4. いずれかのカスタマー・エッジをクリックします。 例えば、**cust-nsx-edge0** です。 パブリックとプライベートのカスタマー・サブネットが**「説明」**フィールドに表示されます。

また、{{site.data.keyword.slportal}}で以下の手順を実行して、カスタマー・サブネットについてのさらに詳しい情報を得ることができます。

1. **「ネットワーキング」>「IP 管理」>「サブネット」**をクリックします。
2. フィルター・メニューをクリックし、NSX-T Web クライアントの **customer-nsx-edge0** の説明に表示されていた識別子を**「サブネット」**フィールドに入力します。
3. IP アドレスについて表示されるメモを確認します。 これらのメモに、初期セットアップ時に注文され、使用されたサブネットと IP アドレスが示されています。

   初期セットアップ時に注文され、使用された IP アドレスは使用しないでください。 ただし、必要に応じてこれらのサブネット上の他の IP アドレスを使用できます。 追加のネットワーク・アドレス変換ルールをセットアップするには、[NAT ルールの管理](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:external}を参照してください。
   {:important}

## 関連リンク
{: #vc_nsx-t_esg_config-related}

* [vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge Services Gateway](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:external}

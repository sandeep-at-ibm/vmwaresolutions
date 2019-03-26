---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-30"

---

# V1.5 のリリース・ノート
{: #relnotes_v15}

このリリースには、新機能、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VRF アカウントとクラシック SoftLayer アカウントの要件
{: #relnotes_v15-vrf}

クラシック SoftLayer® アカウントの場合、VLAN スパンニングはアカウント・レベルで有効にできる設定です。 {{site.data.keyword.vmwaresolutions_short}} を使用するには、VLAN スパンニングを有効にする必要があります。

VRF (Virtual Routing and Forwarding) SoftLayer アカウントの場合、変更不可の永続的な設定として VLAN スパンニングに相当する機能があります。 VRF アカウントの場合は、ユーザー構成は不要です。

インスタンスを注文する前に、使用する SoftLayer アカウントが、VRF アカウントであるか、VLAN スパンニングを有効にしたクラシック (非VRF) アカウントであることを確認してください。 そうでない場合は、注文が失敗する可能性があります。

使用する SoftLayer アカウントが VRF アカウントかどうかを確認するには、IBM Bluemix サポートにお問い合わせください。 クラシック・アカウントの場合は、[VLAN スパンニングの有効化または無効化](/docs/infrastructure/vlans?topic=vlans-vlan-spanning){:new_window}の手順に従って VLAN スパンニングを有効にする必要があります。

## サービス料金モデルの更新
{: #relnotes_v15-svc-charge}

Cloud Foundation インスタンスには、新しい _SDDC Manager_ ライセンスが導入されています。これは、各ノードに適用される月額料金です。

## 使いやすさの向上
{: #relnotes_v15-ui}

ユーザー・インターフェース全体が以下のように改善されました。

* さまざまな {{site.data.keyword.CloudDataCents_notm}}の使用可否や、注文に対応する十分な在庫があるかどうかが、ユーザー・インターフェースに明確に表示されます。 これらの詳細を使用すると、インスタンスの注文時に選択する {{site.data.keyword.CloudDataCent_notm}}に関して、十分な情報に基づく決定を行えます。 詳しくは、[vCenter Server インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)を参照してください。
* Cloud Foundation インスタンスの場合は、入力フィールドに必要な情報を入力すると、インスタンス名、ドメイン・ネームとサブドメイン・ネーム、データ・センターの場所などの情報が自動的にグラフィカル形式で表示されます。

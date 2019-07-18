---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: VMware HCX deployment, HCX configuration, order HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud の注文
{: #hcx_ordering}

VMware HCX on {{site.data.keyword.cloud}} サービスを注文するには、そのサービスを組み込む形で新しい VMware vCenter Server with Hybridity Bundle インスタンスを注文するか、そのサービスを既存のインスタンスに追加します。

## 新しいインスタンスでの VMware HCX on IBM Cloud の注文
{: #hcx_ordering-new}

VMware HCX on {{site.data.keyword.cloud_notm}} を組み込む形で新しい VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle インスタンスを注文する場合は、{{site.data.keyword.vmwaresolutions_short}} コンソールからインスタンスを注文する時に、**「サービス」**セクションで**「VMware HCX on IBM Cloud」**を選択します。


## 既存のインスタンスでの VMware HCX on IBM Cloud の注文
{: #hcx_ordering-existing}

既存の VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle インスタンスに VMware HCX on {{site.data.keyword.cloud_notm}} サービスを追加する場合は、サービスを追加する対象のインスタンスを表示し、左側のナビゲーション・ペインにある**「サービス」**をクリックし、**「追加」**をクリックします。

## VMware HCX on IBM Cloud の構成
{: #hcx_ordering-config}

HCX on {{site.data.keyword.cloud_notm}} をインストールするには、以下の設定を行います。
1. **「HCX interconnect type」**を指定します。以下のいずれかのオプションを選択します。
  * **Public network:** HCX がパブリック・ネットワークでサイト間の暗号化接続を作成します。 ライセンスの登録と課金は、パブリック・ネットワークを介して行われます。
  * **Private interconnect:** HCX がプライベート・ネットワークでサイト間の暗号化接続を作成します。 ライセンスの登録と課金は、パブリック・ネットワークを介して行われます。
  * **Private network:** HCX がプライベート・ネットワークでサイト間の暗号化接続を作成します。 ライセンスの登録と課金は、HTTP プロキシーを介してプライベート・ネットワーク上で行われます。
3. **「Private network」**を選択した場合は、以下のフィールドに入力します。
  * **プロキシー・アドレス (Proxy Address):** プロキシー・サーバーの IPv4 アドレス。
  * **プロキシー・ポート (Proxy Port):** プロキシー・サーバーのポート。 ポート番号は通常、8080 または 3128 です。
  * **ユーザー名 (Username):** プロキシー認証が必要な場合のユーザー名。
  * **パスワード (Password):** プロキシー認証が必要な場合のパスワード。
  * **パスワードの再入力 (Reenter Password):** プロキシー認証の検証のためにパスワードを再入力します。
2. **「Public endpoint certificate type」**を指定します。 **「CA 証明書」**を選択する場合、以下の設定を構成してください。
  * **証明書の内容:** CA 証明書の内容を入力します。
  * **秘密鍵:** CA 証明書の秘密鍵を入力します。
  * (オプション) **パスワード:** 秘密鍵が暗号化されている場合は、秘密鍵のパスワードを入力します。
  * (オプション) **パスワードの再入力:** 秘密鍵のパスワードをもう一度入力します。
  * (オプション) **ホスト名:** CA 証明書の共通名 (CN) にマップするホスト名。 HCX on {{site.data.keyword.cloud_notm}} では、CA 証明書の形式を NSX Edge で有効な形式にしなければなりません。 NSX Edge の証明書の形式について詳しくは、[SSL 証明書のインポート](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html){:external}を参照してください。
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## HCX on IBM Cloud のデプロイメント・プロセス
{: #hcx_ordering-deploy}

HCX on {{site.data.keyword.cloud_notm}} のデプロイメントは自動的に行われます。 このサービスを組み込む形で vCenter Server with Hybridity Bundle インスタンスを注文する場合でも、このサービスを後でインスタンスにデプロイする場合でも、{{site.data.keyword.vmwaresolutions_short}} の自動化プロセスによって以下の手順が実行されます。
1. {{site.data.keyword.cloud_notm}} インフラストラクチャー上の HCX 用に、次の 3 つのサブネットが注文されます。
   * HCX 管理用プライベート・ポータブル・サブネットを 1 つ。
   * HCX 相互接続用プライベート・ポータブル・サブネットを 1 つ。 このサブネットは、**「HCX interconnect type」**として**「Private network」**オプションを選択した場合に使用されます。
   * VMware でのアクティベーションやメンテナンスで使用されるパブリック・ポータブル・サブネットを 1 つ。 **「HCX interconnect type」**として**「Public network」**オプションを選択した場合、このサブネットは HCX 相互接続用としても使用されます。

   HCX 用に注文されたサブネット内の IP アドレスは、VMware on {{site.data.keyword.cloud_notm}} の自動化機能によって管理されるようになっています。 ユーザーが作成した VMware リソース (VM や NSX Edge など) にこれらの IP アドレスを割り当てることはできません。 VMware 成果物用に追加の IP アドレスが必要な場合は、{{site.data.keyword.cloud_notm}} 上の独自のサブネットを注文する必要があります。
   {:important}
2. **「HCX interconnect type」**に対して**「Private network」**が選択された場合、**SDDC-DPortGroup-HCX-Private** という名前のポート・グループがプライベート分散仮想スイッチ (DVS) に作成されます。
3. HCX アクティベーション・キーが VMware から注文されます。
4. HCX 用のリソース・プールと VM フォルダーが 3 つずつ作成されます。これらは、HCX 相互接続、ローカル HCX コンポーネント、リモート HCX コンポーネントに必要です。
5. HCX 管理トラフィック用の VMware NSX Edge Services Gateway (ESG) のペアがデプロイされ、構成されます。
   * 注文したサブネットに基づいて、パブリック・アップリンク・インターフェースとプライベート・アップリンク・インターフェースが構成されます。
   * ESG がエクストラ・ラージ・エッジ・アプライアンスのペアとして構成され、高可用性 (HA) が有効になります。
   * HCX Manager との間のインバウンドとアウトバウンドの HTTPS トラフィックが可能になるように、ファイアウォール・ルールとネットワーク・アドレス変換 (NAT) ルールが構成されます。
   * ロード・バランサー・ルールとリソース・プールが構成されます。 これらのルールとリソース・プールを使用して、HCX 関連のインバウンド・トラフィックが、HCX Manager および vCenter Server (Platform Services Controller が組み込まれたもの) の適切な仮想アプライアンスに転送されます。
   * ESG を通ってくる HCX 関連のインバウンド HTTPS トラフィックを暗号化するための SSL 証明書が適用されます。

   HCX 管理エッジは、オンプレミスの HCX コンポーネントとクラウド・サイドの HCX コンポーネントの間の HCX 管理トラフィック専用です。 HCX 管理エッジは、変更したり、HCX ネットワーク拡張に使用したりしないでください。 ネットワーク拡張用には別のエッジを作成してください。 また、ファイアウォールを使用したり、プライベート IBM 管理コンポーネントやパブリック・インターネットへの HCX 管理エッジ通信を無効にしたりすると、HCX の機能に悪影響を与える恐れがあります。
   {:important}

6. {{site.data.keyword.cloud_notm}} 上の HCX Manager がデプロイされ、アクティブにされ、構成されます。
   * HCX Manager が vCenter Server に登録されます。
   * HCX Manager、vCenter Server (Platform Services Controller が組み込まれたもの)、および NSX Manager が構成されます。
   * HCX フリートが構成されます。
   * ローカルとリモートの HCX デプロイメント・コンテナーが構成されます。
7. HCX Manager のホスト名と IP アドレスが VMware vCenter Server on {{site.data.keyword.cloud_notm}} の DNS サーバーに登録されます。

## 関連リンク
{: #hcx_ordering-related}

* [HCX on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [HCX on {{site.data.keyword.cloud_notm}} の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [vCenter Server with Hybridity Bundle インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [HCX の用語集](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension の概要](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension の資料](https://cloud.vmware.com/vmware-hcx/resources){:external}

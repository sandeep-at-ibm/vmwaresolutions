---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-27"

keywords: change vCenter Server artifacts, automation ID, VMware resource

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# vCenter Server 成果物の変更に関する考慮事項
{: #vcenter_chg_impact}

{{site.data.keyword.vmwaresolutions_full}} 用に予約されたユーザー、リソース、またはサブネットを変更すると、管理操作に影響を与える可能性があります。

VMware vSphere Web Client の**「ユーザーおよびグループ」**ページで**「ic4v-vCenter」**グループのグローバル許可を編集しないでください。 例えば、ユーザー名を変更する、ユーザーを削除する、パスワードを変更するなどです。
**root** ホスト・ユーザー ID を使用してください。 **ic4vroot** ホスト・ユーザー ID は、IBM 専用に作成されたものです。
{:important}

## 自動化 ID
{: #vcenter_chg_impact-automation-id}
{: faq}

**自動化** ID は、{{site.data.keyword.vmwaresolutions_short}} コンソールで利用できる自動操作に使用されるユーザー・アカウントです。

コンソールの自動操作用のユーザーおよびパスワードは、これらの資格情報に依存するコンソール操作が失敗する可能性があるため、変更しないでください。

## サービス固有のユーザー・アカウント
{: #vcenter_chg_impact-service-usr-account}
{: faq}

サービスごとに、vCenter Server 内に内部ユーザー・アカウントが作成されます。 このアカウントは、サービスに関連付けられている管理操作が vCenter Server に接続できるようにすることで、サービスに対して操作を実行できるようにするために必要になります。

障害や接続の問題を防止するために、このユーザー・アカウントのユーザー ID、パスワード、またはパスワードの有効期限設定を変更する場合は、必ず、関連付けられたサービスの情報も更新してください。
{:important}

このアカウントのユーザー ID の形式は、`<service_name>-<truncated service_uuid>@test.local` または`<service_name>-<truncated service_uuid>@example-domain.local` です。 例えば、vCenter Server に接続して定期バックアップを実行するために Veeam on {{site.data.keyword.cloud_notm}} サービスで使用するユーザー ID は、`Veeam-<Veeam_uuid>@test.local` です。

`<service_uuid>` を含む `<service_name>` は 20 文字で切り捨てられます。
{:note}

## vCenter Server インスタンスの VMware リソース (V1.9 以降)
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.9-and-later}
{: faq}

V1.9 以降でデプロイされたインスタンスの場合は、vCenter Server インスタンスが**「使用可能」**状態であれば、VMware vSphere Web Client から VMware 仮想データ・センター、クラスター、スイッチ、ポート・グループ、およびカスタマー・データ・ストア名を変更できます。

ただし、管理データ・ストアの名前は、デフォルト値の **vsanDatastore** (vSAN インスタンスの場合) と **management-share** (ネットワーク・ファイル・システム (NFS) インスタンスの場合) から変更しないでください。 また、プロビジョニング中に作成されたネットワーク・アップリンクの名前も変更しないでください。

## vCenter Server インスタンスの VMware リソース (V1.8 以前)
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.8-and-earlier}
{: faq}

次の表に、SSO 管理者が {{site.data.keyword.vmwaresolutions_short}} コンソール以外で VMware vCenter Server リソースを変更した場合に影響を受ける可能性がある操作を示します。 正常な状態に戻す解決方法がある場合は、その方法も示しています。

以下の表は、V1.8 以前でデプロイされたインスタンスと、V1.8 以前でデプロイされてから V1.9 以降にアップグレードされたインスタンスに適用されます。

表 1. VMware リソースの変更によって影響を受ける操作

| 試された変更  | 影響を受ける操作  | 重大度  | 復旧方法  |
|:------------- |:------------- |:--------------|:--------------|
| VMware 仮想データ・センター名を変更する。 | 変更された仮想データ・センターに新規 ESXi サーバーは参加できないので、VMware 仮想データ・センターの追加が失敗する可能性があります。 | 重要 | VMware 仮想データ・センターを元の名前に戻す。 |
| ポート・グループ名を変更する。    | ESXi サーバーの追加に失敗する可能性があります。 | 重要 | ポート・グループ名を元の名前に戻す。 |
| クラスター名を変更する。 | ESXi サーバーの追加に失敗する可能性があります。 | 重要 | クラスター名を元の名前に戻す。
| パブリックまたはプライベートの分散仮想スイッチ (DVS) 名を変更する。 | ESXi サーバーの追加に失敗する可能性があります。 | 重要 | パブリックまたはプライベートの分散仮想スイッチ (DVS) 名を元の名前に戻す。
| vSAN を使用するインスタンスの vSAN データ・ストア名を変更する。 | ESXi サーバーの追加に失敗する可能性があります。<br><br>インスタンスのアップグレードに失敗する可能性があります。 | 重要 | vSAN データ・ストア名を変更して、元の名前 **vsanDatastore** に戻します。
| NFS を使用するインスタンスの管理 NFS データ・ストア名を変更する。 | ESXi サーバーの追加に失敗する可能性があります。<br><br>インスタンスのアップグレードに失敗する可能性があります。 | 重要 | NFS 管理データ・ストア名を変更して元の名前の **management-share** に戻し、ESXi サーバーに NFS データ・ストアを読み取り専用として再マウントする。

以下の表に、さまざまなリソースに対して SSH アクセスまたはシェル・アクセスを無効にした場合に影響を受ける可能性がある操作を示します。

表 2. SSH アクセスおよびシェル・アクセスの影響を受ける操作 (ローカル)

| 試された変更  | 影響を受ける操作  | 重大度  | 復旧方法  |
|:------------- |:------------- |:--------------|:--------------|
| vCenter Server または PSC の SSH アクセスまたはシェル・アクセスを無効にする。 | 1 次インスタンスと 2 次インスタンスのペア化が失敗する可能性があります。    | 重要    | N/A    |

SSH アクセスまたはシェル・アクセスを無効にした場合は、ここに示す操作を実行する前に、無効にしたアクセスを一時的に再有効化する必要があります。

## vCenter Server インスタンスの管理サブネット
{: #vcenter_chg_impact-mgmt-subnets}
{: faq}

{{site.data.keyword.vmwaresolutions_short}} によって注文されるサブネットについて以下に説明します。また、専用のサブネットを追加注文するオプションについても説明します。

**注意:** これらのコンポーネントを他の目的で使用しないでください。環境の安定性が著しく損なわれます。

{{site.data.keyword.cloud_notm}}でベア・メタル・サーバーを注文するたびに、デフォルトで以下の IP アドレス範囲が注文されます。
*  32 個の IP アドレスを含むプライマリー・パブリック範囲
*  64 個の IP アドレスを含むプライマリー・プライベート範囲

さらに、{{site.data.keyword.vmwaresolutions_short}} 用に以下の管理サブネットが予約されます。
*  最初の VLAN 上の 64 個の IP アドレスを含むポータブル・プライベート・サブネット 2 つ: 1 つが管理用、もう 1 つが VTEPS 用
*  2 番目の VLAN 上の 64 個の IP アドレスを含むポータブル・プライベート・サブネット 2 つ: 1 つが VMotion 用、もう 1 つが vSAN 用
*  パブリック VLAN 上の 16 個の IP アドレスを含むパブリック・ポータブル・サブネット

追加のサブネットを使用する必要がある場合は、以下のいずれかの方法で、使用する IP アドレスを取得できます。
*  **オプション 1 (推奨)**: VMware NSX 仮想ネットワーク・オーバーレイを使用します。 注文時に、サンプルの VXLAN テンプレートが提供されます。 この VXLAN を、ソフトウェア定義ネットワーク (SDN) を構築するための開始点として使用できます。 詳しくは、[ユーザー管理の NSX Edge を使用するためのネットワークの構成](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)を参照してください。
*  **オプション 2**: IP アドレスを取得するために、独自のポータブル・パブリック・サブネットまたはプライベート・サブネットを注文します。 注文するサブネットと管理サブネットを区別するために、注文するすべてのサブネットにメモを追加することができます。

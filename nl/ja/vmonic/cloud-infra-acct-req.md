---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

keywords: user account, user permissions, VRF account

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud インフラストラクチャー・アカウントの要件
{: #cloud-infra-acct-req}

{{site.data.keyword.vmwaresolutions_full}} を使用してインスタンスを注文するには、{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントが必要です。 インスタンス内で注文したコンポーネントの費用は、その {{site.data.keyword.cloud_notm}} アカウントに請求されます。

## IBM Cloud インフラストラクチャー・アカウントの権限
{: #cloud-infra-acct-req-permissions}

使用する {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントには、お客様に代わってインスタンス内でコンポーネントを注文して操作を実行できるだけの権限がなければなりません。 この権限の要件は、{{site.data.keyword.vmwaresolutions_short}} コンソールから注文するすべてのタイプのインスタンスとサービスに適用されます。

許可ユーザーは、{{site.data.keyword.slportal}}で {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントの権限を確認したり更新したりできます。 詳しくは、『[ユーザーのカスタマー・ポータル許可の編集](/docs/customer-portal?topic=customer-portal-customerportal_accuserprof#cp_editusercpperm){:new_window}』を参照してください。

表 1. {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントに必要な権限

| 権限         | 詳細                                 |
|:------------------ |:--------------------------------------- |
| サーバーの追加 | この権限は、VMware ESXi を実行する {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}を注文するときと、インスタンスの構成、保守、サポートの操作に使用する仮想サーバーを時間単位でプロビジョンするときに必要です。 |
| サーバーのキャンセル | この権限は、VMware ESXi を実行する{{site.data.keyword.baremetal_short}}を解放/再利用するときに必要です。 インスタンスを削除すると、注文したコンポーネントは、適切な従属関係シーケンスで自動的に解放されます。 |
| 仮想サーバーの詳細の表示 | この権限は、注文の確認や自動化構成に必要なサーバー・プロビジョニングの詳細を取得するときに必要です。 |
| ストレージの追加 | この権限は、インスタンスのバックアップ・ストレージと共有ストレージを注文するときに必要です。 |
| ストレージの管理 | この権限は、インスタンスのバックアップ・ストレージと共有ストレージを管理するときに必要です。 |
| ハードウェア・ファイアウォール | この権限は、インスタンスに Fortinet on {{site.data.keyword.cloud_notm}} サービスをインストールした場合に、そのサービスのファイアウォールのログ・ファイルと設定を編集または表示するときに必要です。 |
| パブリック・ネットワーク・ポートのコンピュートを追加 | この権限は、パブリック・ネットワーク・ポートと一緒にハードウェアと VSI (仮想サーバー・インスタンス) を注文するときに必要です。 |
| IP アドレスの追加 | この権限は、vSphere クラスター内で実行される仮想マシンを管理するために必要なポータブル・プライベート・サブネットの範囲を自動的に注文するときに必要です。 インスタンスにサービスを追加すると、帯域幅を分離して割り振るために、これらのポータブル・プライベート IP アドレスが VMware ESXi サーバーに割り当てられます。 |
| チケットの追加 | この権限は、サービス・チケットを自動的に開くために必要です。 リストア操作を開始したり、問題が検出されて問題解決プロセスが自動的に開始されたりすると、チケットが作成されます。 |
| チケットの編集 | この権限は、作成されたサービス・チケットを自動的に編集するときに必要です。 |
| チケットの表示 | この権限は、{{site.data.keyword.cloud_notm}} インフラストラクチャーのプロビジョニングの遅延や問題についての、インスタンス内のコンポーネントに関連するサービス・チケットをモニターするときに必要です。 |
| ハードウェアの詳細の表示 | この権限は、注文の確認や自動化構成に必要なハードウェアの詳細を取得するときに必要です。 |
| リブート/コントロール | この権限は、インスタンスを削除する際に、ハードウェアの取り消しプロセスでハードウェアの電源を切るときに必要です。 |
| ライセンスの表示 | この権限は、インスタンスで使用しているライセンスを取得して確認するときに必要です。 |
| パスワードの表示 | この許可は注文した VSI を管理するために必要です。 |
| サーバー・モニタリングの管理 | この権限は、注文を実行するときには不要ですが、インスタンス内で VMware ESXi サーバーを実行している {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}のモニタリング状況を取得して確認するときに必要です。 |

## サービス・エンドポイントを有効にした VRF
{: #cloud-infra-acct-req-vrf-se}

{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントは、Virtual Routing and Forwarding (VRF) アカウントでなければなりません。 VRF 以外のアカウントは、VRF アカウントに変換する必要があります。 また、VRF アカウントでサービス・エンドポイントを使用できるようにすることも推奨されています。

詳しくは、以下を参照してください。
* [IBM Cloud での VRF の概要](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
* [アカウントでサービス・エンドポイントを使用できるようにする方法](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)

## 関連リンク
{: #cloud-infra-acct-req-related}

* [vCenter Server インスタンスの要件](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [IBM Cloud での VRF の概要](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)

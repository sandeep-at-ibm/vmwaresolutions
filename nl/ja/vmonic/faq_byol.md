---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: FAQ, license, BYOL

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# ライセンスと BYOL に関するよくある質問
{: #faq_byol}

{{site.data.keyword.vmwaresolutions_full}} のライセンス持ち込み (BYOL) 機能など、ライセンスに関するよくある質問への回答をご覧ください。

## BYOL とは何ですか?
{: #faq_byol-def}
{: faq}

ライセンス持ち込み (BYOL) は、V2.0 以降の VMware vCenter Server および VMware vSphere クラスターで使用できる機能です。 BYOL を利用すると、所有している VMware ライセンスを、以下の 1 つ以上の VMware ソフトウェア・コンポーネントに使用できます。
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

自分で所有しているライセンスを VMware コンポーネントで使用することを選択し、有効なライセンス・キーを提供する場合、そのコンポーネントのライセンスは IBM から注文されません。そのコンポーネントの月単位のライセンス料金は、{{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントに請求されません。

ビジネス・パートナーであるユーザーは、BYOL 機能を使用できません。
{:note}

## VMware vSphere on IBM Cloud を通して注文されたライセンスとコンポーネントの管理はどこで行うのでしょうか?
{: #faq_byol-license-mgmt}
{: faq}

VMware vSphere on {{site.data.keyword.cloud_notm}} で新規クラスター作成の注文を実行すると、VMware ライセンス、ESXi サーバー、およびその他のネットワーキング・コンポーネントが提供されます。これらは、{{site.data.keyword.slportal}}から管理できます。

デプロイメント後に、保管された構成を使用して新規クラスターを拡張するには、{{site.data.keyword.vmwaresolutions_short}} コンソールにアクセスしてください。 詳しくは、[既存の vSphere クラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)を参照してください。

## BYOL を行うために必要なライセンス・エディションと CPU は何ですか?
{: #faq_byol-license-cpu-reqs}
{: faq}

BYOL のライセンス・エディションには、以下の要件が適用されます。

### vCenter Server インスタンスの BYOL 要件
{: #faq_byol-vcs-reqs}

表 1. vCenter Server インスタンスのライセンス・エディションと最少 CPU 数についての要件

  | VMware コンポーネント | 必要なライセンス・エディション | 必要な最少 CPU 数
  |:-------------  |:-------------  |:-------|
  | vCenter Server | 標準                | N/A |
  | vSphere        | Enterprise Plus | CPU 8 個 |
  | vSAN           | Advanced または Enterprise | CPU 8 個 |
  | NSX            | Standard、Advanced、Enterprise | CPU 8 個 |

## 提供したライセンス・キーが正しくない場合はどうなりますか?
{: #faq_byol-incorrect-license}
{: faq}

お客様から提供されたすべてのライセンス・キーは、対応する VMware コンポーネントにとって適切なキーであるか、また、VMware コンポーネントの最小エディションと最少 CPU 数の要件を満たしているか検査されます。 ライセンス・キーの検査に合格しなかった場合は、通知が送られ、インスタンスの注文を先に進めることはできません。

## 8 つを超える CPU のライセンス・キーを提供することはできますか?
{: #faq_byol-license-key}
{: faq}

はい。 どの VMware コンポーネントも CPU ごとにライセンスが 1 つ必要です。 現在、すべての vCenter Server サーバーは CPU を 2 つ使用します。 そのため、サーバーごとにライセンスが 2 つ必要です。 基本インスタンスと、将来的にインスタンスに追加する拡張ノードに対応できるライセンス・キーを提供することをお勧めします。

## 一部の VMware コンポーネントでは BYOL 機能を使用して、他の VMware コンポーネントでは月単位のライセンスを購入することはできますか?
{: #faq_byol-mthly-license}
{: faq}

はい。 4 つの VMware コンポーネントのうち、BYOL 機能を使用するものとライセンスを購入するものを任意に組み合わせられます。 {{site.data.keyword.vmwaresolutions_short}} コンソールで、インスタンスを注文する際に、簡単にライセンス・オプションを選択できます。 最初のインスタンスの注文時のライセンス・オプションが、そのインスタンスの存続期間にわたって適用されます。

## 特定の VMware コンポーネントで、一部のライセンスに BYOL を使用し、他のライセンスを IBM から購入することはできますか?
{: #faq_byol-purchase}
{: faq}

はい。 クラスターを作成するときに、特定の VMware コンポーネントに BYOL を選択した場合、以下の方法を選択できます。
* 新規 BYOL キーを入力する
* 既存の BYOL キーを引き続き使用する
* そのクラスター用に IBM 提供のライセンスを購入する

現時点では、クラスター単位でライセンスを適用できるのは、VMware vSphere Enterprise と VMware vSAN だけです。

## クラスターを作成するときに BYOL を使用できますか?
{: #faq_byol-cluster}
{: faq}

はい。 クラスターの作成時には、既存の BYOL ライセンスを使用して BYOL を利用することも、新規 BYOL を入力して BYOL を利用することもできます。 また、クラスターの作成時に、IBM 提供のサブスクリプション・ライセンスを購入することもできます。

現時点では、クラスター単位でライセンスを適用できるのは、VMware vSphere Enterprise と VMware vSAN だけです。

## BYOL ライセンスを管理するにはどうすればよいですか?
{: #faq_byol-mgmt}
{: faq}

インスタンスのデプロイメントが完了したら、VMware vSphere Web Client を使用して、BYOL ライセンスを管理できます。

## インスタンスに後から ESXi サーバーを追加するときに、BYOL ライセンスの容量が十分かどうかはインスタンスで検証されますか?
{: #faq_byol-add-esxi}
{: faq}

はい。 デプロイ済みのインスタンスに ESXi サーバーを追加するときには、指定された ESXi サーバー数に対応できるか、BYOL ライセンスの容量が自動的に検査されます。 容量が十分でない場合、ESXi サーバーは追加されず、コンソール通知が表示されます。

## BYOL でクラスターに利用できるライセンス・キャパシティーを確認するにはどうすればよいですか?
{: #faq_byol-capacity}
{: faq}

ライセンス・キーで使用可能な CPU の数を検出するには、以下の手順を実行します。
1. **「リソース」**ページに進みます。
2. インスタンスを見つけてクリックします。
3. **「インフラストラクチャー」**タブで、ライセンス・キャパシティーを確認するクラスターをクリックします。
   使用可能な CPU の数が、**「ユーザー提供ライセンス」**表にリストされます。

## BYOL ライセンス・オプションを選択した場合、IBM からサポートを受けられますか?
{: #faq_byol-support}
{: faq}

インスタンスの構成の問題については、引き続き IBM サポートが窓口になります。 ただし、報告された問題が BYOL の VMware コンポーネントの問題であると判断された場合は、VMware サポートに連絡するように案内します。

## BYOL を使用するのに vSphere ライセンス料が価格見積もりリストに表示されるのはなぜですか? このライセンス料が請求されるのでしょうか?
{: #faq_byol-vsphere}
{: faq}

{{site.data.keyword.baremetal_short}}は、VMware vSphere が既にインストールされ、vSphere ライセンスが既に含まれた状態でプロビジョンされます。 vSphere に BYOL を選択した場合は、インスタンスのデプロイメント時に、含まれている vSphere ライセンスを削除するプロセスが自動的に開始されます。 その後、ライセンス料がお客様の {{site.data.keyword.cloud_notm}} アカウントにクレジットされます。 このプロセスでは、お客様による操作は不要です。

## BYOL に既存の手動プロセスを引き続き使用できますか?
{: #faq_byol-manual-process}
{: faq}

BYOL 機能を導入した場合、手動プロセスを引き続き使用することは推奨されません。 BYOL を使用する場合は、所有しているライセンスを、インスタンスの注文時に提供してください。

## VMware vRealize Automation、VMware vRealize Operations、VMware vRealize Log Insight などの他の VMware 製品でも BYOL はサポートされますか?
{: #faq_byol-other-support}
{: faq}

いいえ。これらの VMware 製品はインスタンスのデプロイメントに含まれないのでサポートされません。 これらの VMware 製品は、一般に初期デプロイメントに追加してインストールされるため、クライアントまたはエージェントが、製品のインストールとライセンス適用を実行する必要があります。

## 関連リンク
{: #faq_byol-related}

* [コンソールへのアクセス](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-loginmethod)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

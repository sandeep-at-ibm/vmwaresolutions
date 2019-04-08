---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# VMware および Skate Advisor コンセプト・カーの概要
{: #vcscar-intro}

以下のリファレンス・アーキテクチャーは、「コンセプト・カー」です。つまり、現実の世界の問題を解決するテクノロジーに焦点を当てて見せるためのメカニズムです。 当然ですが、「コンセプト・カー」は、現在提供されているサービスを表すものではありません。

このリファレンス・アーキテクチャーは、以下の情報も表しています。

-   さまざまな関係者が共通言語を利用できるようにします。
-   統一された方法でテクノロジーを実装して問題解決できるようにします。
-   実証済みのリファレンス・アーキテクチャーと比較してソリューションを検証できるようにします。
-   一般的な標準、仕様、およびパターンへの順守を促進します。

## ACME Skate Advisor について
{: #vcscar-intro-about}

わたしたちは、Watson の人工知能との対話や現実的な機械学習を実際に見せたい、そしてそのなかでスケートボードの文化を探索したいと考えていました。 提供しているサービスとクラウド・インフラストラクチャーをユニークな方法で使用する方法を見せ、この分野の技術的な能力と進歩を実証していきます。 この「コンセプト・カー」は、Skate Advisor というデモ用の Acme Skateboard アプリケーションの機能拡張として実装します。 Skate Advisor は、Watson 駆動型エンジンとの間でスケートボードの技についての会話ができるツールです。以下の引用文は、会話の例です。

-   “Watson、キャスパー・トリックのコンビネーションを見せて”
-   “Watson、トリックがよく行われている場所を見せて”
-   “Watson、キャスパー・トリックのビデオを見せて”

Acme Skate Advisor は、Watson Discovery Service を利用して、記事、ビデオ、ブログ、およびその他のインターネット・ベースのコンテンツを取り込み、トリックの学習データベースを作成します。このデータベースをアプリケーションで照会できます。

また、Skate Advisor アプリケーションはアプリケーション・モダナイゼーション・プラットフォームに実装されています。
このプラットフォームは、{{site.data.keyword.cloud_notm}} for VMware Services プラットフォームでホストされる
{{site.data.keyword.icpfull_notm}} を介してコンテナー・ベースのサービスを提供します。

Acme Skate Advisor アプリケーションは、Watson プラットフォームとアプリケーション・モダナイゼーション・プラットフォームの両方を利用します。

## ユース・ケース
{: #vcscar-intro-use-cases}

### アプリケーション・モダナイゼーションのデモンストレーション
{: #vcscar-intro-app-mod-demo}

アプリケーション・モダナイゼーション・プラットフォームにデプロイされたアプリケーションをデモンストレーションします。 このプラットフォームには、VMware vCenter Server on {{site.data.keyword.cloud_notm}} オファリングで {{site.data.keyword.cloud_notm}} に
デプロイされた {{site.data.keyword.icpfull_notm}}、CAM、および NSX の各コンポーネントが含まれています。

### Watson Assistant を使用した Watson 音声認識
{: #vcscar-intro-speech}

Acme Skate Advisor は、Watson プラットフォームで提供されている音声認識サービスと音声合成サービスを介してユーザーと会話します。

### Watson Discovery Service の使用およびトレーニング
{: #vcscar-intro-watson-disc}

Acme Skate Advisor は、Watson Discovery Services を使用して、分類言語を適用するトリックと、オンライン・サービスから検出したトリックをデータベースに記録します。

### Watson サービスの使用
{: #vcscar-intro-watson-services}

Acme Skate Advisor の作成には、以下の Watson サービスを使用しました。
-   Watson Text to Speech。
-   Watson Speech to Text。
-   Watson Advisor。
-   Watson Discovery Service。
-   Watson Knowledge Studio。

## IBM Cloud でのアプリケーション・モダナイゼーション
{: #vcscar-intro-app-mod}

アプリケーション・モダナイゼーションとは、クラウドの新しい開発・デリバリー手法を使用するように既存のアプリケーションを移行するプロセスを表す用語です。 昨今のお客様は、ビジネスやアプリケーションの複雑さに基づいてこの移行を行うために役立つ革新的で効率的なアプローチを模索しています。

ビジネスのプレッシャーにより、市場投入までの時間を短縮することが求められています。 お客様の既存の資産には、アプリケーションだけでなく、データ、プロセス、ビジネス・ロジック、ユーザー・インターフェースが含まれ、これらはすべて、新しいビジネス要求に対応するための適合が必要になっています。

次のリストはアプリケーション・モダナイゼーションの利点を示しています。
- 開発者の生産性が向上する
- 運用効率が向上する
- 新機能の構築コストが削減する
- 提供する性能を短時間で拡張できる

IBM は、プライベート・クラウドの 70% が、アプリケーション環境をモダナイズする必要性によって導入されたものであると認識しています。 しかし、ほとんどの組織は段階的なアプローチでアプリケーション・モダナイゼーションを進めているので、以下のようなハイブリッドやマルチクラウドの環境が必要になっています。

- メインフレームまたは UNIX システムで通常実行される複雑でモノリシックな従来型アプリケーションは、オンプレミスに残します。
- SoR (Systems of Record、定型業務処理システム) で使用される x86 環境、セキュリティー・センシティブなワークロード、および規制されたワークロードのアプリケーションは、仮想化インフラストラクチャーまたはプライベート・クラウドに配置されます。
- SAP やハイパフォーマンス・コンピューティングなどのアプリケーションは、ベアメタル・リソースを使用します。
- パブリック・クラウドに移行できる、セキュリティー・センシティブなワークロードと規制されたワークロードは、専用の環境に移行します。
- Web、モバイル、IoT、AI、ビデオなどの SoE (Systems of Engagement、協働のための情報活用システム) は、パブリック・クラウドに移動します。

例えば、フロントエンド SoE アプリケーションをコンテナーとしてデプロイし、データベースと従来型ミドルウェアをプライベート・クラウド上の VM にデプロイするのが一般的なパターンです。

IT インフラストラクチャーとビジネス・ニーズは固有であるため、モダナイゼーションのアプローチでは次の優先事項を実現する必要があります。

* ビジネス・バリューを加速する
* デリバリー時間を最短化する
* リスクを軽減する
* 既存の投資を保持する

IBM が提供しているアプリケーション・モダナイゼーション・アプローチはまさにこのようなアプローチであり、お客様固有のビジネス・ニーズやテクノロジー・ニーズに合わせてカスタマイズできます。

次のドキュメントは、{{site.data.keyword.cloud_notm}} へのアプリケーション・モダナイゼーション・ジャーニーで使用されるテクノロジーをさまざまな観点で説明しています。

* [vCenter Server および {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - 以下のプラットフォームをデプロイするためのリファレンス・アーキテクチャー。
   - **VMware vCenter Server on IBM Cloud** - vCenter Server は、{{site.data.keyword.vmwaresolutions_short}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMware ベースのプラットフォームです。
   - **{{site.data.keyword.icpfull_notm}}** – {{site.data.keyword.icpfull_notm}} は、コンテナー化されたアプリケーションを開発して管理するためのアプリケーション・プラットフォームです。 {{site.data.keyword.icpfull_notm}} は、コンテナー・オーケストレーター Kubernetes、プライベート・イメージ・リポジトリー、管理コンソール、モニター・フレームワーク、およびグラフィカル・ユーザー・インターフェースを含む統合環境です。 このユーザー・インターフェースが、アプリケーションをデプロイ、管理、モニター、およびスケーリングできる一元的な場所になります。
   - **IBM Cloud Automation Manager** – CAM は、エンタープライズ対応の Infrastructure as Code プラットフォームであり、リポジトリーで保管およびバージョン管理されるテンプレートを使用して、単一画面で VM ベースのワークロードと Kubernetes ベースのワークロードをプロビジョンできます。
* [vCenter Server および {{site.data.keyword.containerlong_notm}} サービス](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 以下のプラットフォームをデプロイするためのリファレンス・アーキテクチャー。
   - **VMware vCenter Server on IBM Cloud** - vCenter Server は、{{site.data.keyword.vmwaresolutions_short}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMware ベースのプラットフォームです。
   - **{{site.data.keyword.containerlong_notm}}** – {{site.data.keyword.containerlong_notm}} は、シングル・テナント・クラスターを対象としたアプリケーション・コンテナーのデプロイメント自動化、スケーリング、および運用を行うオーケストレーション・エンジンとして Kubernetes を使用する、{{site.data.keyword.cloud_notm}} 上の管理対象サービスです。
* [vCenter Server ネットワーキング](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - vCenter Server、{{site.data.keyword.icpfull_notm}}、および {{site.data.keyword.containerlong_notm}} 間の統合に使用されるネットワーク・テクノロジー (NSX-V や Calico など) 、およびテクノロジー・プレビューの NSX-T に焦点を当てて説明しています。
* _VMware および Skate Advisor コンセプト・カー・ガイド_ - 「コンセプト・カー」であるリファレンス・アーキテクチャー。コンセプト・カーとは、現実の世界の問題を解決するテクノロジーに焦点を当てて見せるためのメカニズムです。 IBM が実演したかったのは、Watson AI と機械学習の対話です。 スケートボードの文化を通してユニークな方法でクラウド・サービスを披露しています。 この「コンセプト・カー」は、Skate Advisor という Acme Skateboard アプリケーションの機能拡張として実装されています。 Skate Advisor は、Watson 駆動型エンジンとの間でスケートボードの技についての会話ができるツールです。
* [VMware: Stock Trader のモダナイゼーション・ジャーニー](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - このリファレンス・ユース・ケースでは、クラシックな WebSphere Application Server アプリケーションを、{{site.data.keyword.cloud_notm}} Private、IBM Middleware コンテンツ、{{site.data.keyword.containerlong_notm}}、および vCenter Server on {{site.data.keyword.cloud_notm}} を利用してモダナイズする方法について説明しています。 だれもがクラウド・ジャーニーの途上にいますが、ジャーニーのどの段階にいるかは人それぞれです。 アプリケーション設計者 Jane とクラウド・インフラストラクチャー設計者 Todd が段階的に手順を踏んで、Stock Trader という既存のアプリケーションをモダナイズしていきます。 ジャーニーの段階を踏んでいくときに参考になる例や、各段階の規模に関係なくビジネスにもたらされる価値を記載しています。 アプリケーション、DevOps、統合、および管理という 4 つのテーマに焦点を当てています。 すべてのテーマが組み合わさって目標の実現を可能にします。 他を残して 1 つのテーマだけをモダナイズしてもうまくいかない可能性があります。

## 関連リンク
{: #vcscar-intro-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

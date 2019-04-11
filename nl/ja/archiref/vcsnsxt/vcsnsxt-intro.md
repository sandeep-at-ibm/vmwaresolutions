---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

# vCenter Server ネットワーキングの概要
{: #vcsnsxt-intro}

このドキュメントでは、{{site.data.keyword.cloud}} へのアプリケーション・モダナイゼーション・ジャーニーについて、マルチクラウド統合環境をアプリケーション・モダナイゼーションで使用できるようにする次のプラットフォームのネットワークの側面に焦点を当てて説明します。

- **VMware vCenter Server on IBM Cloud** - {{site.data.keyword.vmwaresolutions_short}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMWare ベースのプラットフォームです。
- **IBM Cloud Private** - コンテナー化アプリケーションを開発および管理するためのアプリケーション・プラットフォームです。コンテナー化アプリケーションは、仮想化インフラストラクチャー・プラットフォーム (vCenter Server やオンプレミス vSphere 環境など) にデプロイされます。
- **{{site.data.keyword.containerlong_notm}}** - シングル・テナント・クラスターを対象としたアプリケーション・コンテナーのデプロイメント自動化、スケーリング、および運用を行うオーケストレーション・エンジンとして Kubernetes を使用する、{{site.data.keyword.cloud_notm}} 上の管理対象サービスです。

アプリケーション・モダナイゼーションの最大の課題は、マイグレーション、ネットワーキング、およびセキュリティーです。 vCenter Server、VMware Hybrid Cloud Extension (HCX)、VMware NSX、{{site.data.keyword.containerlong_notm}}、{{site.data.keyword.icpfull_notm}} を利用してこれらの課題をいくつか解決することができます。 以下のネットワーク・アーキテクチャーでは、Acme Skateboards 社を例として使用して、クラウド環境とオンプレミス環境に分かれたコンポーネントを接続する方法について説明します。

[NSX-T プレビュー](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-techpreview)は、将来のリファレンス・アーキテクチャーで VMware NSX Transformers (NSX-T) を使用する方法を説明するためのテクノロジー・プレビューです。 NSX-T は、異種のエンドポイントや技術スタックが混在したアプリケーション・フレームワークおよびアーキテクチャー向けに設計されています。 このような環境には、vSphere の他にも異種のハイパーバイザー、KVM、コンテナー、ベアメタルが存在することがあります。 NSX-T を使用すると、IT チームも開発チームも自分たちのアプリケーションに最適なテクノロジーを選択できます。 NSX-T は、ネットワーク・チームだけでなく開発組織も管理、運用、利用できるように設計されています。

## IBM Cloud でのアプリケーション・モダナイゼーション
{: #vcsnsxt-intro-app-mod}

アプリケーション・モダナイゼーションとは、クラウドの新しい開発・デリバリー手法を使用するように既存のアプリケーションを移行するプロセスを表す用語です。 昨今のお客様は、ビジネスやアプリケーションの複雑さに基づいてこの移行を行うために役立つ革新的で効率的なアプローチを模索しています。

ビジネスのプレッシャーにより、市場投入までの時間を短縮することが求められています。 お客様の既存の資産には、アプリケーションだけでなく、データ、プロセス、ビジネス・ロジック、ユーザー・インターフェースが含まれ、これらはすべて、新しいビジネス要求に対応するための適合が必要になっています。

アプリケーション・モダナイゼーションの利点には、以下が含まれます。

- 開発者の生産性が向上する
- 運用効率が向上する
- 新機能の構築コストが削減する
- 提供する性能を短時間で拡張できる

IBM では、プライベート・クラウドの 70% がアプリケーション環境をモダナイズする必要性に迫られて導入されたものであると認識していますが、ほとんどの組織では段階的なアプローチでアプリケーション・モダナイゼーションが進んでいるため、以下のようにハイブリッド環境とマルチクラウド環境が必要になっています。

- メインフレームまたは UNIX システムで通常実行される一体構造の複雑なレガシー・アプリケーションは、オンプレミスのまま運用されます。
- SoR (Systems of Record、定型業務処理システム) で使用される x86 環境、セキュリティー・センシティブなワークロード、および規制されたワークロードのアプリケーションは、仮想化インフラストラクチャーまたはプライベート・クラウドに配置されます。
- SAP やハイパフォーマンス・コンピューティングなどのアプリケーションは、ベアメタル・リソースを消費します。
- パブリック・クラウドに移行できる、セキュリティー・センシティブなワークロードと規制されたワークロードは、専用の環境に移行します。
- Web、モバイル、IoT、AI、ビデオなどの SoE (Systems of Engagement、協働のための情報活用システム) は、パブリック・クラウドに移動します。

例えば、一般的なパターンは、フロントエンド SOE アプリケーションをコンテナーとしてデプロイし、データベースとレガシー・ミドルウェアをプライベート・クラウド上の VM にデプロイすることです。

IT インフラストラクチャー・ニーズとビジネス・ニーズはお客様ごとに固有であるため、ビジネス価値の提供を促進し、デリバリー時間を短縮し、リスクを軽減し、既存の投資を無駄にしないモダナイゼーション・アプローチが必要になります。 IBM が提供しているアプリケーション・モダナイゼーション・アプローチはまさにこのようなアプローチであり、お客様固有のビジネス・ニーズやテクノロジー・ニーズに合わせてカスタマイズできます。

このドキュメントは、{{site.data.keyword.cloud_notm}} へのアプリケーション・モダナイゼーション・ジャーニーで使用するテクノロジーについてさまざまな観点で説明しています。

* [vCenter Server および {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - 以下のプラットフォームをデプロイするためのリファレンス・アーキテクチャー。
   - **VMware vCenter Server on IBM Cloud** - {{site.data.keyword.vmwaresolutions_short}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMware ベースのプラットフォームです。
   - **{{site.data.keyword.icpfull_notm}}** – {{site.data.keyword.icpfull_notm}} は、コンテナー化されたアプリケーションを開発して管理するためのアプリケーション・プラットフォームです。 これは、コンテナー・オーケストレーター Kubernetes、プライベート・イメージ・リポジトリー、管理コンソール、モニター・フレームワーク、グラフィカル・ユーザー・インターフェースで構成される統合環境であり、ユーザーがアプリケーションのデプロイ、管理、モニター、スケーリングを行うことができる一元的な場所を提供します。
   - **IBM Cloud Automation Manager** – CAM は、エンタープライズ対応の Infrastructure as Code プラットフォームであり、リポジトリーで保管およびバージョン管理されるテンプレートを使用して、単一画面で VM ベースのワークロードと Kubernetes ベースのワークロードをプロビジョンできます。
* [vCenter Server および {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 以下のプラットフォームをデプロイするためのリファレンス・アーキテクチャー。
   - **VMware vCenter Server on IBM Cloud** - {{site.data.keyword.vmwaresolutions_short}} のオファリングであり、{{site.data.keyword.cloud_notm}} に自動的にプロビジョンされる VMware ベースのプラットフォームです。
   - **{{site.data.keyword.containerlong_notm}}** – シングル・テナント・クラスターを対象としたアプリケーション・コンテナーのデプロイメント自動化、スケーリング、および運用を行うオーケストレーション・エンジンとして Kubernetes を使用する、{{site.data.keyword.cloud_notm}} 上の管理対象サービスです。
* _vCenter Server networking_ - 最新のガイドでは、vCenter Server、{{site.data.keyword.icpfull_notm}}、および {{site.data.keyword.containerlong_notm}} 間の統合で使用されるネットワーク・テクノロジー (NSX-V や Calico など) と NSX-T のテクノロジー・プレビューに焦点を当てています。
* [VMware および Skate Advisor コンセプト・カー](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro) - このリファレンス・アーキテクチャーは、「コンセプト・カー」です。つまり、現実の世界の問題を解決するテクノロジーに焦点を当てて見せるためのメカニズムです。 IBM が実演したかったのは、Watson AI と機械学習の対話です。 スケートボードの文化を通してユニークな方法でクラウド・サービスを披露しています。 この「コンセプト・カー」は、Skate Advisor という Acme Skateboard アプリケーションの機能拡張として実装されています。 Skate Advisor は、Watson 駆動型エンジンとの間でスケートボードの技についての会話ができるツールです。
* [VMware: Stock Trader のモダナイゼーション・ジャーニー](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - このリファレンス・ユース・ケースでは、クラシックな WebSphere Application Server アプリケーションを、{{site.data.keyword.cloud_notm}} Private、IBM Middleware コンテンツ、{{site.data.keyword.containerlong_notm}}、および vCenter Server on {{site.data.keyword.cloud_notm}} を利用してモダナイズする方法について説明しています。 だれもがクラウド・ジャーニーの途上にいますが、ジャーニーのどの段階にいるかは人それぞれです。 アプリケーション設計者 Jane とクラウド・インフラストラクチャー設計者 Todd が段階的に手順を踏んで、Stock Trader という既存のアプリケーションをモダナイズしていきます。 ここでは、ジャーニーで各段階を進むときに参考になる例、および各段階の規模に関係なくビジネスに実現される価値を示します。 アプリケーション、DevOps、統合、および管理という 4 つのテーマに焦点を当てています。 すべてのテーマが組み合わさって目標の実現を可能にします。 他を残して 1 つのテーマだけをモダナイズしてもうまくいかない可能性があります。

## 関連リンク
{: #vcsnsxt-intro-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

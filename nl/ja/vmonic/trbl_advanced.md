---

copyright:

  years:  2016, 2018

lastupdated: "2017-12-29"

---

# トラブルシューティングの支援

## 問題

時により、複雑な問題が発生し、根本原因分析を行って解決策を得られるだけの十分な情報がログ・ファイルにないことがあります。

## 解決方法

このような問題をトラブルシューティングして解決するためには、{{site.data.keyword.vmwaresolutions_full}} サポート・チームが {{site.data.keyword.cloud_notm}} 管理仮想マシン (VM) にアクセスする必要があります。 この管理 VM (IBM CloudDriver) とは、デプロイした VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスを管理するために使用されるメインのインターフェースです。

セキュリティー上の理由により、IBM CloudDriver へのアクセスは制限されています。 {{site.data.keyword.vmwaresolutions_short}} サポート・チームがお客様に承認を要求し、承認が得られると、チームは {{site.data.keyword.cloud_notm}} インフラストラクチャー仮想サーバーを使用して CloudDriver コンポーネントにアクセスできるようになります。 このサーバーは、{{site.data.keyword.cloud_notm}} インフラストラクチャー Frontend Customer Router (FCR) パブリック・ネットワークを介して環境にブリッジされます。

次に、{{site.data.keyword.vmwaresolutions_short}} サポート・チームは、インスタンスの注文と構成のときに指定された {{site.data.keyword.cloud_notm}} インフラストラクチャー {{site.data.keyword.slapi_short}} キー (または、必要であればお客様から指定された更新済みキー) を使用して、{{site.data.keyword.cloud_notm}} インフラストラクチャー仮想サーバーを時間単位でデプロイします。

トラブルシューティングのために使用された IBM CloudBuilder ツールについては、お客様のアカウントに課金されます。 デバッグと修復が完了すると、IBM CloudBuilder コンポーネントは解放されます。

トラブルシューティングに使用される {{site.data.keyword.cloud_notm}} インフラストラクチャー仮想サーバーは、以下の仕様でデプロイされます。

* CentOS 7 パブリック・ノード VSI (仮想サービス・インスタンス) が使用されます (1 CPU、1 GB RAM)。
* VSI は、同じデータ・センター内で、インスタンスが存在しているのと同じプライマリーのパブリック VLAN とプライベート VLAN にデプロイされます。
* VSI デプロイメントでは、ポストインストール・スクリプトによって、特定の IP アドレスのセット ({{site.data.keyword.vmwaresolutions_short}} サポート・チームが所有、使用するもの) からの着信 SSH 接続のみを許可するファイアウォール・ルールが設定されます。
* それらの IP アドレスを使用する開始サポート・システムが、{{site.data.keyword.cloud_notm}} インフラストラクチャー VM 上で実行されます。この VM は、プライベート {{site.data.keyword.cloud_notm}} インフラストラクチャー・ネットワークからのみアクセス可能であり、HA (高可用性) {{site.data.keyword.cloud_notm}} インフラストラクチャー Vyatta システムのペアで保護されます。
* セキュリティー脅威に対して開始サポート・システムを監視するために、QRadar®、Nessus、IBM BigFix® などの IBM セキュリティー・ツールが使用されます。

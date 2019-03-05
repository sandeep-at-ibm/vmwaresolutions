---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# ステップ 2 - 仮想マシンのデプロイメント
{: #caveonix-step2}

{{site.data.keyword.vmwaresolutions_full}} の自動処理では、追加のポータブル・プライベート IP サブネットが要求されます。「オールインワン」の仮想マシン (VM) では、そのサブネットからの IP アドレスが構成され、Caveonix RiskForesight の各コンポーネントが以下の処理を実行できるようになります。

- BCR 経由で vCenter と NSX Manager に接続する。
- VXLAN かホスト対象オフプレミスのどちらかで Remote Collector に接続する。
- スケールアップ時にクライアント側で IP アドレス・スペースを管理できるようにする。


## 関連リンク
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)

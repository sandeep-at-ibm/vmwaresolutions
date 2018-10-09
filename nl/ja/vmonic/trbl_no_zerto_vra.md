---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# 新しく作成した ESXi サーバーに Zerto Virtual Replication Appliance が表示されない

## 問題
Zerto 災害復旧がインストールされている VMware vCenter Server インスタンスに ESXi サーバーを追加した後に、Zerto Virtual Replication コンソールに Virtual Replication Appliance (VRA) が表示されません。

## 解決方法
vCenter Server インスタンスでは、Zerto 災害復旧サービスは、デフォルト・クラスター **cluster1** に含まれる ESXi サーバーにのみインストールされます。 同じ vCenter Server 環境内に追加のクラスターを作成しても、その追加クラスターに Zerto 災害復旧が自動的にインストールされるわけではありません。その追加クラスターに ESXi サーバーを追加してもインストールされません。

別途、追加クラスターに Zerto 災害復旧をインストールする必要があります。

{{site.data.keyword.cloud}} サポート・チケットを開き、IBM サポートと連携して使用可能な IP アドレスを取得して、{{site.data.keyword.vmwaresolutions_short}} コンソールではなく Zerto コンソールから VRA をインストールしてください。

Zerto コンソールにアクセスするには、インスタンスの **「サービス」**タブの Zerto カードをクリックし、**「詳細を表示」**をクリックしてから**「Zerto コンソールの表示」**をクリックします。

IBM サポートへの連絡について詳しくは、[IBM サポートへのお問い合わせ](trbl_support.html)を参照してください。

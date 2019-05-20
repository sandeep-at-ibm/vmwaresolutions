---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# VMware ソフトウェア更新のタイプ
{: #vum-type-updates}

VMware では、ソフトウェア更新の説明に以下の用語を使用します。

表 1. VMware ソフトウェア更新の用語と定義

| 用語 | 定義 |
|:------- |:----------- |
| ブルティン |	1 つ以上の VIB をグループ化したもの。 ブルティンはメタデータ内で定義されます。 |
| デポ |	オンラインで公開される VIB および関連メタデータの論理グループ |
| ホスト・アップグレード・イメージ |	Update Manager リポジトリーにインポートして、ESXi 5.5 ホストまたは ESXi 6.0 ホストを ESXi 6.5 にアップグレードするために使用する ESXi イメージ。 |
| 拡張機能 | 	オプションのコンポーネントを ESXi ホストに追加するための VIB のグループを定義するブルティン。 通常、拡張機能はサード・パーティーによって提供され、拡張機能に対するパッチまたは更新についてもサード・パーティーが行います。 |
| メタデータ |	従属情報、テキスト記述、システム要件、およびブルティンを定義する追加データ。 |
| オフライン・バンドルの圧縮ファイル |	オフラインのパッチ適用に役立つ自己完結型パッケージに VIB および対応するメタデータをカプセル化したアーカイブ。 サード・パーティーのオフライン・バンドルまたはカスタム VIB セットから生成したオフライン・バンドルを、ESXi 5.5 または ESXi 6.0 から ESXi 6.5 へのホストのアップグレードに使用することはできません。 |
| パッチ |	特定の問題または機能拡張に対処するために 1 つ以上の VIB をグループ化するブルティン。 |
| ロールアップ |	ダウンロードとデプロイメントを容易にするためにグループ化されたパッチの集合。 |
| VA アップグレード |	ベンダーがアップグレードを検討する仮想アプライアンスの更新。 |
| VIB |	VIB は、単一のソフトウェア・パッケージです。 |

## 関連リンク
{: #vum-type-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)

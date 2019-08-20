---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-22"

keywords: vmware offering, vmware solutions functions, function support

subcollection: vmware-solutions


---

# オファリングの比較表
{: #inst_comp_chart}

次の表で、VMware vCenter Server インスタンスと VMware vSphere クラスターの機能サポートの違いを確認してください。

| 機能 | vCenter Server | VMware vSphere |
|:--- |:--- |:--- |:--- |
| {{site.data.keyword.IBM}} の高度な自動化機能による起動 <sup>1</sup> | はい | いいえ。自己構築および自己構成 |
| ストレージ・オプション | vSAN または NFS (ファイル・レベルの共有ストレージ) | vSAN または NFS |
| 初期クラスター内の ESXi サーバーの数 | vSAN の場合は 4、NFS の場合は 2 以上 (3 を推奨) | 既存のクラスターを拡張する場合は 1、新しい vSAN クラスターの場合は 4、NFS を使用する新しいクラスターの場合は 3 以上 |
| ESXi サーバーの最大数 <sup>2</sup> | 1 クラスターあたり 59 | 1 クラスターあたり 60 |
| クラウド自動化マルチサイト・デプロイメント |V2.0 以降でデプロイされた新しいインスタンスでサポート | サポートあり。 自動構成は含まない |
| ESXi サーバーの追加 | サポートあり | サポートあり。 自動構成は含まない |
| ESXi サーバーの削除 | サポートあり | サポートあり。 自動構成は含まない |
| マルチクラスター・サポート | 最大数は VMware のサイズ設定についてのガイドラインによる | サポートあり。 自動構成は含まない |
| クライアント管理による VMware スタックの更新とパッチ適用 | クライアント管理による更新:<br/>ネイティブ VMware ツール (VMware Update Manager) | クライアント管理による更新:<br/>ネイティブ VMware ツール (VMware Update Manager) |
| バックアップとリストア | IBM Spectrum Protect Plus または Veeam の手動使用 | バックアップとリストアのソリューションは含まれない |
| ソフトウェア定義ネットワーキング | NSX Base、Advanced、Enterprise | NSX Standard、Base、Enterprise。 自動構成は含まない |
| vSphere と vSAN の BYOL | クラスター単位で完全にサポート | サポートあり |
| vCenter と NSX の BYOL | インスタンス単位で完全にサポート | サポートあり |
| NSX ライセンス・アップグレード・オプション | NSX Base から Advanced または Enterprise へのアップグレード、NSX Advanced から Enterprise へのアップグレードが可能。 | なし |
| vSAN ライセンス・エディション | vSAN Advanced または Enterprise | vSAN Advanced または Enterprise  |
| アドオン・サービス | サポートあり | このソリューションの自動化によってはサポートされませんが、独自のソフトウェアを持ち込んでインストールできます。 |
{: caption="表 1. vCenter Server クラスターと vSphere クラスターでサポートされる機能" caption-side="top"}

## メモ
{: #inst_comp_chart-notes}

<sup>1</sup> 設計の検証とデプロイメント時の検証に基づきます。

<sup>2</sup> vSAN クラスターの ESXi サーバー数は最大 64 台まで増やすことができます。 詳しくは、[ESXi サーバーに関するよくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi)の_クラスターには ESXi サーバーをいくつ追加できますか?_ を参照してください。

## 関連リンク
{: #inst_comp_chart-related}

* [よくある質問](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [vCenter Server の概要](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)
* [VMware vSphere の概要](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)
* [vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [VMware vSphere の部品構成表](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

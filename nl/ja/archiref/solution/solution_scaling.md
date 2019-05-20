---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# キャパシティーの拡張
{: #solution_scaling}

初期デプロイメントの後に、{{site.data.keyword.vmwaresolutions_full}} コンソールからコンピュート・キャパシティーを拡張することができます。 この設計では、以下のような拡張方法がサポートされています。
* 別々の vCenter Server が管理する新規サイトを追加する
* 新規クラスターを追加する
* 既存クラスターに新規ホストを追加する

## その他のサイトの追加
{: #solution_scaling-sites}

{{site.data.keyword.vmwaresolutions_short}} は {{site.data.keyword.cloud_notm}} の世界規模のデータ・センターおよび統合されたネットワーク・バックボーンを利用して、地域をまたがるさまざまなユース・ケースをデプロイし、インフラストラクチャーを一から構築するよりもずっと短時間で機能できるようにします。

この設計では、マルチサイト・デプロイメントの定義は以下の内容で構成されます。
* 提供する新規 DNS/AD ルート・ドメイン、サブドメイン、SSO ドメイン、および SSO サイト名を含む初期または 1 次 VMwareデプロイメント。
* 以下の構成を必要とする 1 次サイト SSO ドメインにプロビジョンされた単一または複数の 2 次サイト。
   * 新規 SSO サイト名
   * 1 次ドメインのルートに結合された新規 DNS サイト/サブドメイン
   * 2 次および 1 次のサイト AD VM 間にセットアップされた DNS および AD レプリケーション
   * 1 次サイト vCenter への拡張リンク・モードでセットアップされた vCenter

さらに、2 次サイトの NSX マネージャーが 1 次サイト上の NSX マネージャーの 2 次 NSX マネージャーとしてセットアップされることもあります。 これはお客様が完了しなければならない手動のプロセスです。

## 新規クラスターの追加
{: #solution_scaling-clusters}

{{site.data.keyword.vmwaresolutions_short}} コンソールから新規クラスターを作成し、新規クラスターに自動的に追加される新規ホストを注文することによって、コンピュート・キャパシティーを拡張することもできます。

この方式によって以下のことができます。
* 環境内に追加の別々のクラスターを作成する。
* 管理ワークロードをアプリケーション・ワークロードから物理的および論理的に隔離する。
* 他の特性 (例えば Microsoft SQL データベース・クラスターなど) に基づいてワークロードを隔離する。
* アプリケーションを高可用トポロジーにデプロイする。

初期クラスターを管理専用クラスターに変換する場合、既存ワークロードのマイグレーションでユーザーが手動で行う手順が必要になります。 その場合は、データ・ストアを新規クラスターに接続し直すか、ストレージをマイグレーションする必要がある場合があります。 新規クラスターが別の {{site.data.keyword.cloud_notm}} ポッドにあるか、そのクラスターに別の VLAN ID が割り当てられている場合は、ワークロードの IP アドレスを変更しなければならない可能性があります。
{:note}

## ESXi ホストの既存クラスターへの追加
{: #solution_scaling-hosts}

{{site.data.keyword.vmwaresolutions_short}} コンソールからホストを注文することによって、既存のクラスターを拡張できます。  新規ホストはクラスターに自動的に追加されます。 予約要件に基づいて、クラスターの HA 予約ポリシーを調整する必要があることにご注意ください。

## 関連リンク
{: #solution_scaling-related}

* [ソリューションの概要](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [設計の概要](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [コンポーネントのバックアップ](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)

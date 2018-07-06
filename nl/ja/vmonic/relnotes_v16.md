---

copyright:

  years:  2016, 2018

lastupdated: "2017-05-22"

---

# V1.6 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VMware Cloud Foundation インスタンスの更新

以下のコンポーネントが新規追加または更新されました。

*  SDDC Manager 2.2.1
*  IBM 管理コンポーネント V1.6
*  新しいハードウェア仕様: **スモール**または**標準** (要件に従う)。
*  デプロイメントに使用できる新しいデータ・センター: **HKG02 - 香港**、**OSL01 - オスロ**、**SEO01 - ソウル**、**SNG01 - シンガポール**、**SYD04 - シドニー**。

コンポーネントの完全なリストについては、[VMware Cloud Foundation の概要](../sddc/sd_cloudfoundationoverview.html)を参照してください。

## VMware vCenter Server インスタンスの更新

### vCenter Server インスタンスのハードウェア強化

V1.6 リリース以降、vCenter Server インスタンスでは以下の複数の機能拡張を利用できます。

*  vCenter Server オファリングの V2.0 仕様の完全実装。 詳しくは、[VMware vCenter Server on IBM Cloud ソリューションのアーキテクチャー](https://www.ibm.com/devops/method/content/architecture/virtualizationArchitecture#2_0)を参照してください。
*  新しいハードウェア仕様: **スモール**、**ミディアム**、**ラージ** (要件に従う)。
*  デプロイメントに使用できる新しいデータ・センター: **HKG02 - 香港**、**OSL01 - オスロ**、**SEO01 - ソウル**、**SNG01 - シンガポール**、**SYD04 - シドニー**。
*  インスタンスの注文時に 2 つ以上の ESXi サーバーで VMware vSphere DRS (Distributed Resource Scheduler) と VMware HA (High Availability) がデフォルトで有効になります。
*  インスタンスの注文時に最大 7 つの NFS ファイル共有を追加できます。 高可用性のために、管理コンポーネント (vCenter、PSC、NSX Manager および Controllers、CloudDriver) が NFS ファイル共有で実行されるようになりました。
*  ユーザー管理の VMware NSX Edge Services Gateway の自動によるデプロイメントと構成

これらの変更により、既存の vCenter Server インスタンスを現行リリースでそのまま使用することはできません。現行リリースにアップグレードすることもできません。 V1.6 より前のリリースの vCenter Server インスタンスも、{{site.data.keyword.vmwaresolutions_short}} コンソールに表示専用モードで表示されます。 これらのインスタンスには、ユーザー・インターフェース上で**「非推奨」**のマークが付けられ、警告シンボル・アイコンが表示されます。

V1.6 より前の vCenter Server インスタンスでは、以下のアクションを実行できます。

*  インスタンスの詳細ページで情報を参照する。 インスタンスのプロパティーに表示される情報は、V1.6 リリース日時点のデータを表していて、それ以降は更新されません。
*  VMware vSphere Web Client を開き、vCenter でインスタンスを使用する。
*  インスタンスを削除する。

V1.6 より前のインスタンスではこれ以外のアクションは使用できなくなりました。

### vCenter Server インスタンスのネットワーキングの機能強化

*  パブリック VLAN 上の 16 個の IP アドレスをカバーするパブリック・サブネットが自動的に注文され、VM (仮想マシン) からインターネットにアクセスすることが可能になります。
*  プライベート VLAN 上の 64 個の IP アドレスをカバーするプライベート・サブネットが自動的に注文され、VM から SoftLayer® 内部ネットワークにアクセスすることが可能になります。
*  3 ノードのデプロイメント構成で NSX コントローラーがアンチアフィニティー・ルールを使用してデプロイされ、別々の ESXi サーバー上で実行されます。
*  ユーザーが使用するための新しい VMware NSX Edge Services Gateway が導入されました。

   追加の NSX Edge Services Gateway (ESG) が、注文した新しい vCenter Server インスタンスの一部としてデプロイされるようになりました。

   この ESG は、自動的に注文されるプライベート・サブネットとパブリック・サブネットの間でお客様の VM が通信を行うための機能です。
   この ESG には  2 つのインターフェースがあります。お客様の VM に関連付けられている仮想化 VXLAN に接続するインターフェースと、
   パブリック VLAN に接続するインターフェースです。 さらに、以下の設定が構成されます。
   *  プライベート・サブネット範囲の IP アドレスからのすべての発信トラフィックを許可するファイアウォール・ルール。
   *  プライベート・サブネットのすべての IP アドレスをパブリック・サブネット上の単一の IP アドレスに変換する SNAT (送信元ネットワーク・アドレス変換) ルール (デフォルトでは無効)。
   * VMware HA (High Availability) は、管理 ESG とユーザー管理 ESG で共有される新しいポート・グループを使用するように構成されます。

   この ESG は、インスタンス・ハードウェアのタイプにかかわらずデプロイされ、お客様が構成を変更できます。 詳しくは、以下のトピックを参照してください。
   *  [ユーザー管理の NSX Edge Services Gateway を VM で使用するためのネットワークの構成](../vcenter/vc_esg_config.html)
   *  [VMware NSX 資料](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## 使いやすさの向上

ユーザー・インターフェース全体が以下のように改善されました。

*  ユーザー・インターフェースのすべての領域にアクセスできるナビゲーション・ペインが左側に導入されたことで、コンソールのメイン・ナビゲーションが大幅に改善されました。 新規インスタンスの注文、デプロイ済みのインスタンスの表示、システム通知の確認、設定の変更、オンライン・ドキュメントのアクセスを簡単に行えます。
*  左側のナビゲーション・ペインからアクセスできる新しい**「開始」**ページにより、十分に詳しい情報がコンソールで直接得られるので、注文するインスタンスのコンポーネントについて、情報に基づいた決定を行うことができます。 **「開始」**ページでは、インスタンスを注文するプロセスの手順が、インスタンスを注文するためのすべての前提条件 (必要なユーザー・アカウントなど) を満たすところから始まり、最終的に注文を実行するところまで順を追って説明されます。
*  Cloud Foundation インスタンスと vCenter Server インスタンスの両方のサマリーの詳細が、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**メニューからアクセスできる単一のページに統合されました。 このページから、適切なタブを選択して、Cloud Foundation インスタンスまたは vCenter Server インスタンスをフィルタリングできます。
* インスタンスに Zerto 災害復旧がインストールされている場合は、サービスの詳細のページから Zerto コンソールにワンクリックで直接アクセスできます。 詳しくは、[Cloud Foundation インスタンスのサービスの注文、表示、削除](../sddc/sd_addingremovingservices.html)および[vCenter Server インスタンスのサービスの注文、表示、削除](../vcenter/vc_addingremovingservices.html)を参照してください。

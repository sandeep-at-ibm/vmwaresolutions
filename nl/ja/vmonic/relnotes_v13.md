---

copyright:

  years:  2016, 2019

lastupdated: "2017-01-23"

---

# V1.3 のリリース・ノート

このリリースには、新機能、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## vCenter Server インスタンスのファイル・レベルの共有ストレージ

共有 NAS (Network Attached Storage) を vCenter Server インスタンスに追加できるようになりました。 この機能を追加すると、vCenter Server 上で実動ワークロードを実行し、ノード障害時のデータ損失を防止できます。 NFS (ネットワーク・ファイル・システム) ファイル・ストレージは、vCenter Server インスタンスの注文プロセスでオプションとして提供されます。 詳しくは、[vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)を参照してください。

## Zerto 災害復旧の削除

Zerto 災害復旧をインスタンスの一部として注文した場合でも、既存のインスタンスに追加した場合でも、不要になったらこのサービスを削除できるようになりました。 コンソールからサービスの削除を要求すると、削除プロセスの実行方法が IBM サポートから説明されます。

詳しくは、以下のトピックを参照してください。

* [災害復旧の削除](/docs/services/vmwaresolutions/services/removingzertodr.html)
* [Cloud Foundation インスタンスの表示](/docs/services/vmwaresolutions/sddc/sd_viewinginstances.html)
* [vCenter Server インスタンスの表示](/docs/services/vmwaresolutions/vcenter/vc_viewinginstances.html)

## VMware NSX Edge for Cloud Foundation インスタンス

新たに注文する Cloud Foundation インスタンスには、NSX Edge が一部として組み込まれるようになりました。 NSX Edge は、ネットワーク・エッジ・セキュリティーとゲートウェイ・サービスを提供して、仮想化ネットワークを分離します。

インスタンスのデプロイメント中に、管理 NSX Edge Services Gateway (ESG) が IBM によってデプロイされます。 この ESG は、IBM 管理仮想マシンが、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。 この ESG は、2 つのインターフェースを含むようにデプロイされます。一方のインターフェースは {{site.data.keyword.cloud_notm}} のプライベート VLAN に接続され、もう一方のインターフェースは {{site.data.keyword.cloud_notm}} のパブリック VLAN に接続されます。

セキュリティーを確保するため、管理仮想マシンから開始されたアウトバウンド HTTPS 通信のみを許可するようにファイアウォール・ルールが適用されます。 この ESG は「ラージ」構成でデプロイされ、IBM サポートのみが構成を変更できます。

詳しくは、以下のトピックを参照してください。

* [Cloud Foundation インスタンスの技術仕様](/docs/services/vmwaresolutions/sddc/sd_cloudfoundationoverview.html#technical-specifications-for-cloud-foundation-instances)
* [管理サービスの NSX Edge にはセキュリティーのリスクがありますか?](/docs/services/vmwaresolutions/vmonic/faq.html#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX 資料](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

## インスタンスの注文プロセス

Cloud Foundation インスタンスと vCenter Server インスタンスの両方について、インスタンスの注文プロセスが改善されました。

* サマリー・ページに、注文したすべてのコンポーネントとサービスに適用されるすべての条件が表示されるので、注文前にそれらの条件を簡単に確認して同意することができます。
* 注文を実行する前に、インスタンスの注文のサマリーを保存および印刷できます。 この新機能により、インスタンスの設定とコストを確認し、必要に応じて注文するコンポーネントを変更し、承認を得てから注文に戻ることができます。

詳しくは、以下のトピックを参照してください。

* [Cloud Foundation インスタンスの注文](/docs/services/vmwaresolutions/sddc/sd_orderinginstance.html)
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter/vc_orderinginstance.html)

## インスタンス管理

インスタンス管理プロセスの新機能と改善点は以下のとおりです。

* Cloud Foundation インスタンスと vCenter Server インスタンスの両方で、ESXi サーバーをインスタンスに追加する前に、ESXi サーバーの見積もりコストを確認して検討できます。 追加するサーバーの数を指定すると、1 カ月あたりのサーバー単位の見積もりコストがコンソールに表示されます。 詳しくは、[Cloud Foundation インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/sddc/sd_addingremovingservers.html)および [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter/vc_addingremovingservers.html)を参照してください。
* Cloud Foundation インスタンスと vCenter Server インスタンスの両方で、インスタンスの合計数がサマリー・ページの上部に表示されます。 また、インスタンスのサマリー・ページからワンクリックでインスタンスを注文することもできます。 さらに、プロビジョン中にサマリー・ページで注文状況の詳細を確認することもできます。 表示された状況にマウスオーバーすると、現在の段階やエラーの詳細が表示されます。
* Cloud Foundation インスタンスの場合、インスタンスの詳細ページにインスタンスのデプロイメント履歴が表示され、デプロイメント状況に関する情報が段階ごとに表示されます。 詳しくは、[Cloud Foundation インスタンスの表示](/docs/services/vmwaresolutions/sddc/sd_viewinginstances.html)を参照してください。
* Cloud Foundation インスタンスでは、**「更新およびパッチ」**ページに更新に関する詳細情報が表示されるため、更新とパッチのプロセスの使いやすさが向上しています。例えば、パッチに必要なダウン時間や、更新がスケジュールされた時刻が表示されたり、現在のパッチより前に適用する必要がある必須パッチが視覚的に表示されたりします。 詳しくは、[Cloud Foundation インスタンスへの更新とパッチの適用](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)を参照してください。

## E メール通知

インスタンスのデプロイメントで新たな注文を実行したとき、また、インスタンスのサービスが追加、デプロイ、または削除されたときに、E メールで通知されるようになりました。 通知設定はデフォルトで有効になっています。 必要に応じて、受け取る通知を**「設定」**ページで設定できます。 詳しくは、[ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic/useraccount.html)を参照してください。

---

copyright:

  years:  2016, 2018

lastupdated: "2016-12-12"

---

# V1.2 のリリース・ノート

このリリースには、新機能、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## コンポーネントの更新

VMware ESXi のバージョンが、前のリリースの ESXi 6.0 u2 から、新しく vSphere 6.0 u2 p03 に更新されました。

## IBMid と Bluemix のアカウントの関連付け

{{site.data.keyword.vmwaresolutions_full}} は、IBM Bluemix® カタログのインフラストラクチャー・ソリューションとして提供されています。 したがって、**IBMid** アカウントを使用して {{site.data.keyword.vmwaresolutions_short}} コンソールにログインするために、**IBMid** アカウントを Bluemix アカウントに関連付ける必要があります。

詳しくは、以下のトピックを参照してください。
* [概説](../index.html)
* [Bluemix へのアクセスに関するトラブルシューティング](https://console.bluemix.net/docs/troubleshoot/ts_accessing.html){:new_window}

## Zerto 災害復旧

VMware Cloud Foundation インスタンスも VMware vCenter Server インスタンスも、Zerto 災害復旧を組み込んだ形での注文が可能です。 また、インスタンスの詳細ページで、既存の Cloud Foundation インスタンスおよび vCenter Server インスタンスに Zerto 災害復旧を追加することもできます。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)
* [Cloud Foundation インスタンスの表示](../sddc/sd_viewinginstances.html)
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [vCenter Server インスタンスの表示](../vcenter/vc_viewinginstances.html)
* [Zerto 災害復旧](../services/addingzertodr.html)

## 料金情報

注文するインスタンスの見積もりコストを確認して検討してから、注文を決定できるようになりました。 インスタンスを注文する際にコンポーネントを選択すると、すべてのコンポーネントの合計コストと詳細な料金が**「サマリー」**ページに表示されます。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)

## インスタンスの注文プロセスの機能強化

インスタンスの注文プロセスが、以下の機能強化によって大幅に改善されました。
* Cloud Foundation インスタンスと vCenter Server インスタンスの両方で、使用している SoftLayer® ユーザー・アカウントに必要なユーザー権限があるか、VLAN スパンニングが有効になっているか、正しい API 鍵が指定されているかを確認する新しい検証チェックが行われます。 要件が満たされていない場合は、問題の解決方法がユーザー・インターフェースに明確に表示されます。
*  vCenter Server インスタンスについては、インスタンスのコンポーネントを選択する順序が最適化され、必要なハードウェアと ESXi サーバーを提供しているデータ・センターのみが表示されるようになりました。 この変更により、後になってエラーが発生する可能性が最小限に抑えられました。

詳しくは、以下のトピックを参照してください。
* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)

## 追加の E メール通知

新規 ESXi サーバーがインスタンスに追加されたとき、および既存の ESXi サーバーが削除されたときに、E メールで通知されるようになりました。 また、インスタンスが削除されたときにも E メールで通知されます。 通知設定はデフォルトで有効になっています。 必要に応じて、受け取る通知を**「設定」**ページで設定できます。

詳しくは、[ユーザー・アカウントと設定](useraccount.html)を参照してください。

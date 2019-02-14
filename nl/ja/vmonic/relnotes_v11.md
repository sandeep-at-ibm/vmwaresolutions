---

copyright:

  years:  2016, 2019

lastupdated: "2016-11-04"

---

# V1.1 のリリース・ノート

このリリースには、新機能、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## VLAN スパンニング要件

クラシック (非 VRF) SoftLayer® アカウントを使用する場合は、VLAN スパンニングを有効にする必要があります。 クラシック・アカウントの VLAN スパンニングを有効にしないと、VMware 仮想化環境のさまざまなコンポーネントが相互通信できない可能性があります。 SoftLayer アカウントで VLAN スパンニングを有効にするには、[VLAN スパンニングの有効化または無効化](/docs/infrastructure/vlans/vlan-spanning.html){:new_window}を参照してください。

## E メール設定と通知

**「設定」**ページで E メール通知を構成できます。 デフォルトで、この設定は有効になっています。つまり、新しく注文したインスタンスがプロビジョンされて使用可能になると、E メールで通知されます。 **「設定」**ページで E メール通知を無効にすることもできます。 詳しくは、[ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic/useraccount.html)を参照してください。

## 詳細な状況情報

Cloud Foundation インスタンスの詳細な状況情報が表示されるようになりました。 インスタンス名をクリックすると、表示される状況情報に、デプロイメントの進行状況の詳細が示されます。 エラーが発生した場合は、問題の解決に役立つメッセージが表示されます。 詳しくは、[Cloud Foundation インスタンスの表示](/docs/services/vmwaresolutions/sddc/sd_viewinginstances.html)を参照してください。

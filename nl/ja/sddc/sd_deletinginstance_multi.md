---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# マルチサイト構成での Cloud Foundation インスタンスの削除

マルチサイト構成で Cloud Foundation インスタンスを削除する前に、以下の考慮事項を確認してください。

Cloud Foundation インスタンスを削除すると、以下のコンポーネントが順次解放されます。
1. デプロイされたすべてのサービス
2. サポートとサービスの料金
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、サブネットと VLAN は、{{site.data.keyword.cloud}} インフラストラクチャーによって ESXi サーバーが完全にレクラメーション処理されるまで削除できませんが、この処理は {{site.data.keyword.cloud_notm}} 請求処理サイクルの終わりに行われます。 {{site.data.keyword.cloud_notm}} 請求処理サイクル (標準的には 30 日) の終わりに、サブネットと VLAN は削除され、インスタンスの削除が完了します。

**注意:** 削除対象のインスタンスに関する請求は、{{site.data.keyword.cloud_notm}} 請求処理サイクルの終わりまで行われます。

## マルチサイト構成で Cloud Foundation インスタンスを削除する手順

1. 2 次 Cloud Foundation インスタンスからサービスをすべて削除します。
2. 削除するセカンダリー・インスタンスに NSX オブジェクトを展開していないことを確認します。
3. プライマリー SSO (シングル・サインオン) ドメインからセカンダリー vCenter および PSC (Platform Services Controller) を削除します。 詳しくは、[シングル・サインオンからの vCenter Server の登録解除](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}を参照してください。
4. ローカル・ドメイン・コントローラー VSI (仮想サービス・インスタンス) を降格します。 詳しくは、[ドメイン・コントローラーとドメインの降格](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}を参照してください。
5. {{site.data.keyword.vmwaresolutions_short}} コンソールから 2 次 Cloud Foundation インスタンスを削除します。
6. マルチサイト構成のすべてのセカンダリー Cloud Foundation インスタンスについて手順 1 から 5 までを繰り返します。
7. すべてのセカンダリー・インスタンスを削除したら、{{site.data.keyword.vmwaresolutions_short}} コンソールからプライマリー・インスタンスも削除できます。

### 関連リンク

* [Cloud Foundation インスタンスの削除](sd_deletinginstance.html)
* [Cloud Foundation インスタンス用サービスの注文、表示、削除](sd_addingremovingservices.html)

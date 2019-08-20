---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: vCenter Server delete instance, delete vCenter Server, delete multi-site

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# マルチサイト構成での vCenter Server インスタンスの削除
{: #vc_deletinginstance_multi}

マルチサイト構成に含まれている vCenter Server インスタンスを削除する場合は、事前に以下の特別な考慮事項を確認してください。

vCenter Server インスタンスを削除すると、以下のコンポーネントが順次解放されます。
1. デプロイされたすべてのサービス
2. サポートとサービスの料金
3. VMware 製品ライセンス
4. ESXi サーバー
5. サブネット
6. VLAN

リソースに依存関係があるため、インスタンスのコンポーネントは、インスタンスを削除してもすぐには解放されません。 例えば、{{site.data.keyword.cloud}} インフラストラクチャーの請求サイクルの終わりに、ESXi サーバーが {{site.data.keyword.cloud_notm}} によって完全に回収されるまで、サブネットと VLAN は削除できません。 {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常は 30 日) の最後に、サブネットと VLAN が削除され、インスタンスの削除が完了します。

削除したインスタンスについての {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
{:note}

## マルチサイト構成で vCenter Server インスタンスを削除する手順
{: #vc_deletinginstance_multi-procedure}

1. セカンダリー vCenter Server インスタンスからすべてのサービスを削除します。
2. 削除するセカンダリー・インスタンスに NSX オブジェクトを展開していないことを確認します。
3. プライマリー SSO (シングル・サインオン) ドメインからセカンダリー vCenter Server を削除します。 詳しくは、[シングル・サインオンからの vCenter Server の登録解除](https://kb.vmware.com/s/article/2106736){:external}を参照してください。
4. ローカル・ドメイン・コントローラー VSI (仮想サービス・インスタンス) を降格します。 詳しくは、[ドメイン・コントローラーとドメインの降格](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:external}を参照してください。
5. {{site.data.keyword.vmwaresolutions_short}} コンソールからセカンダリー vCenter Server インスタンスを削除します。
6. マルチサイト構成のすべてのセカンダリー vCenter Server インスタンスについて手順 1 から 5 までを繰り返します。
7. すべてのセカンダリー・インスタンスを削除したら、{{site.data.keyword.vmwaresolutions_short}} コンソールからプライマリー・インスタンスも削除できます。

## 関連リンク
{: #vc_deletinginstance_multi-related}

* [vCenter Server インスタンスの削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
* [vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [仮想サーバーのキャンセル](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)

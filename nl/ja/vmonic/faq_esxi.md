---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# ESXi サーバーに関するよくある質問
{: #faq_esxi}

{{site.data.keyword.vmwaresolutions_full}} コンソールで管理されている ESXi サーバーに関するよくある質問への回答をご覧ください。

## インスタンスには ESXi サーバーをいくつ追加できますか?
{: #faq_esxi-instance}
{: faq}

vCenter Server インスタンスでは、デフォルトのクラスターを拡張して、最大 51 台の ESXi サーバーを含めることができます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。 1 インスタンスに最大 10 個のクラスターを追加できるので、デプロイされたインスタンスごとに、すべてのクラスターの ESXi サーバーの合計数は、最大で 51 + 9x59 = 582 になります。

## クラスターには ESXi サーバーをいくつ追加できますか?
{: #faq_esxi-cluster}
{: faq}

V2.2 以降でデプロイされたインスタンスの場合、初期クラスターには最大 51 台の ESXi サーバーを、追加クラスターには最大 59 台の ESXi サーバーを追加できます。

V2.1 以前でデプロイされたインスタンスの場合は、必要な vSAN サポートを有効にして、クラスター・サイズを 32 より大きくする必要があります。 必要な vSAN サポートを有効にするには、以下の手順を実行します。

1. デプロイされた各 ESXi サーバーで、以下のコマンドを実行します。

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. 各 ESXi サーバーを再始動します。 詳しくは、[Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081) を参照してください。
3. 追加の仮想マシンと ESXi サーバーに対応できるように、vCenter Server のサイズを拡張する必要がある場合があります。
4. ステップ 1 - 3 を実行して vSAN の変更を手動で適用したことを示すために IBM サポート・チケットを開きます。 チケットで、アップグレードされたインスタンスが 32 を超える ESXi サーバーに対して有効になることを要求します。

## ESXi サーバー名と IP アドレスは変更できますか?
{: #faq_esxi-change-name-ip}
{: faq}

ESXi サーバー名と IP アドレスは、Windows DNS 解決のために登録されているため、変更できません。 変更すると、デプロイ中に問題が生じたり、vCenter Server の機能に問題が生じたりする可能性があります。

ESXi サーバー名を変更するために、{{site.data.keyword.cloud_notm}} ユーザー・インターフェースの**「デバイス名を変更」**機能を使用しないでください。 この機能によって ESXi サーバーの FQDN が変更されますが、構成済みの vCenter Server と Windows VSI ホストの登録が不正確になり、問題が生じる可能性があります。
{:note}

## ESXi サーバーのルート・アクセスを無効にすることはできますか?
{: #faq_esxi-disable-root}
{: faq}

ESXi サーバーのルート・アクセス有効にしておくことをお勧めします。無効にすると、{{site.data.keyword.vmwaresolutions_short}} 機能に問題が生じる可能性があります。

必要に応じて、{{site.data.keyword.vmwaresolutions_short}} コンソールで ESXi サーバーが**「使用可能」**状況になった後にルート・アクセスを無効にできます。

それ以降、例えば、ファイル共有を追加/削除するときや、{{site.data.keyword.cloud_notm}} に Zerto などのアドオン・サービスをインストールするときなど、自動化操作を行うときにはルート・アクセスを再度有効にする必要があります。

## ESXi サーバーに静的ルートを追加して、他の場所からストレージをマウントすることはできますか?
{: #faq_esxi-static-routes}
{: faq}

ストレージ用に静的ルートを追加できますが、その操作には細心の注意を払う必要があります。 注意を怠ると、既存の共有がアンマウントされる可能性があります。

vMotion の静的ルートの追加はサポートされていません。 vMotion サブネット構成を変更すると、{{site.data.keyword.vmwaresolutions_short}} の機能に問題が生じる可能性があります。
{:note}

## 関連リンク
{: #faq_esxi-related}

* [vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_addingviewingclusters#vc_hybrid_addingviewingclusters)
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

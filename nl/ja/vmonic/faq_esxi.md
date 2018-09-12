---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# ESXi サーバーに関するよくある質問

{{site.data.keyword.vmwaresolutions_full}} コンソールで管理されている ESXi サーバーに関するよくある質問への回答をご覧ください。

## インスタンスには ESXi サーバーをいくつ追加できますか?

* vCenter Server インスタンスの場合、デフォルトのクラスターを拡張して、最大 51 台の ESXi サーバーを含めることができます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。 1 インスタンスに最大 10 個のクラスターを追加できるので、デプロイされたインスタンスごとに、すべてのクラスターの ESXi サーバーの合計数は、最大で 51 + 9x59 = 582 になります。
* Cloud Foundation インスタンスの場合、標準構成には 4 つの ESXi サーバーが含まれています。 最大 28 台のサーバーを追加できます (合計サーバー数は最大 32 台)。 マルチサイト構成の Cloud Foundation インスタンスの場合、すべてのインスタンスの ESXi サーバーの合計数は、最大で 128 になります。

  **注**: 128 台を超える ESXi サーバーのマルチサイト・デプロイメントが必要な Cloud Foundation 構成を使用する場合は、[IBM サポートにお問い合わせ](trbl_support.html)ください。

## クラスターには ESXi サーバーをいくつ追加できますか?

V2.2 以降のリリースでは、初期クラスターには最大 51 台の ESXi サーバーを、追加クラスターには最大 59 台の ESXi サーバーを追加できます。

V2.1 以前のリリースでデプロイされたインスタンスの場合は、必要な vSAN サポートを有効にして、クラスター・サイズを 32 より大きくする必要があります。 必要な vSAN サポートを有効にするには、以下の手順を実行します。

1. デプロイされた各 ESXi サーバーで、以下のコマンドを実行します。

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. 各 ESXi サーバーを再始動します。 詳しくは、[Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081) を参照してください。
3. 追加の仮想マシンと ESXi サーバーに対応できるように、vCenter Server のサイズを拡張する必要がある場合があります。
4. ステップ 1 - 3 を実行して vSAN の変更を手動で適用したことを示すために IBM サポート・チケットを開きます。 チケットで、アップグレードされたインスタンスが 32 を超える ESXi サーバーに対して有効になることを要求します。

## ESXi サーバー名と IP アドレスは変更できますか?

ESXi サーバー名と IP アドレスは、Windows DNS 解決のために登録されているため、変更できません。 変更すると、デプロイ中に問題が生じたり、vCenter Server の機能に問題が生じたりする可能性があります。

**注**: ESXi サーバー名を変更するために、{{site.data.keyword.cloud_notm}} ユーザー・インターフェースの**「デバイス名を変更」**機能を使用しないでください。 この機能は実際に ESXi サーバーの FQDN を変更しますが、構成済みの vCenter Center と Windows VSI ホストの登録が不正確になり、問題が生じる可能性があります。

## ESXi サーバーのルート・アクセスを無効にすることはできますか?

ESXi サーバーのルート・アクセス有効にしておくことをお勧めします。無効にすると、{{site.data.keyword.vmwaresolutions_short}} 機能に問題が生じる可能性があります。

必要に応じて、{{site.data.keyword.vmwaresolutions_short}} コンソールで ESXi サーバーが**「使用可能」**状況になった後にルート・アクセスを無効にできます。

それ以降、例えば、ファイル共有を追加/削除するときや、{{site.data.keyword.cloud_notm}} に Zerto などのアドオン・サービスをインストールするときなど、自動化操作を行うときにはルート・アクセスを再度有効にする必要があります。

## ESXi サーバーに静的ルートを追加して、他の場所からストレージをマウントすることはできますか?

ストレージ用に静的ルートを追加することはできますが、その操作には細心の注意を払う必要があります。 注意を怠ると、既存の共有がアンマウントされる可能性があります。

**注**: vMotion の静的ルートの追加はサポートされていません。 vMotion サブネット構成を変更すると、{{site.data.keyword.vmwaresolutions_short}} の機能に問題が生じる可能性があります。

### 関連リンク

* [vCenter Server インスタンスの容量の拡張と縮小](../vcenter/vc_addingremovingservers.html)
* [Cloud Foundation インスタンスの容量の拡張と縮小](../sddc/sd_addingremovingservers.html)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](../vcenter/vc_addingviewingclusters.html)
* [Cloud Foundation インスタンスのクラスターの追加、表示、削除](../sddc/sd_addingviewingclusters.html)
* [IBM サポートへのお問い合わせ](trbl_support.html)

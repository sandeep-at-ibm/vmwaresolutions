---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# VMware HCX on IBM Cloud の概要

HCX on {{site.data.keyword.cloud}} サービスでは、オンプレミス・データ・センターのネットワークを {{site.data.keyword.cloud_notm}} にシームレスに拡張できるので、変換も変更も行わずに {{site.data.keyword.cloud_notm}} との間で仮想マシン (VM) をマイグレーションできます。

**利用可否**: このサービスは、V2.3 以降のリリースでデプロイされた VMware vCenter Server on IBM Cloud with Hybridity Bundle インスタンスでのみ利用可能です。

既存の vCenter Server インスタンスを vCenter Server with Hybridity Bundle インスタンスにアップグレードできます。 インスタンスをアップグレードして HCX on {{site.data.keyword.cloud_notm}} サービスをデプロイする方法について詳しくは、[vCenter Server with Hybridity Bundle インスタンスへのアップグレード](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance)を参照してください。

**注:** vCenter Server with HCX on {{site.data.keyword.cloud_notm}} インスタンスでは、オンプレミス・サイトからの同時接続が 3 つまでに制限されています。

## HCX on IBM Cloud をインストールする際の考慮事項

HCX on {{site.data.keyword.cloud_notm}} をインストールしようとする前に、以下の考慮事項を確認してください。

### ESXi サーバーの数に関する要件

デフォルト・クラスターに 51 台を超える ESXi サーバーがあるインスタンスに HCX on {{site.data.keyword.cloud_notm}} サービスをインストールすることはできません。 HCX on {{site.data.keyword.cloud_notm}} は、デフォルト・クラスターの vMotion サブネット内に 8 つの IP アドレスを必要とするため、ESXi サーバーの数が 51 を超えると、HCX on {{site.data.keyword.cloud_notm}} で使用できる vMotion サブネット内の IP アドレスがなくなります。

### ファイアウォール・ルールに関する要件

HCX on {{site.data.keyword.cloud_notm}} サービスをインストールする前に、HCX Manager 仮想アプライアンス (HCX Manager) が自己登録できるように、すべてのアウトバウンド HTTPS トラフィックを許可するファイアウォール・ルールを既存のファイアウォールに追加する必要があります。 HCX Manager のインストールが完了したら、ファイアウォール・ルールを除去してもかまいません。 さらに、HCX を適切に機能させるためのファイアウォール・ルールを構成する必要があります。 詳しくは、「[HCX on {{site.data.keyword.cloud_notm}} Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)」の『*Appendix A - Port Access Requirements*』を参照してください。

## HCX on IBM Cloud を削除する際の考慮事項

HCX on {{site.data.keyword.cloud_notm}} サービスを削除する前に、以下の考慮事項を確認してください。
* オンプレミス・ソース・サイトと {{site.data.keyword.cloud_notm}} ターゲット・サイトの間の相互接続と拡張ネットワークを削除しておきます。 相互接続と拡張ネットワークを削除するには、オンプレミスの VMware vSphere Web Client で HCX ユーザー・インターフェースを使用します。
* オンプレミス・ソース・サイトと {{site.data.keyword.cloud_notm}} ターゲット・サイトの間のサイト・ペアを削除しておきます。 サイト・ペアを削除するには、オンプレミスの VMware vSphere Web Client で HCX ユーザー・インターフェースを使用します。
* HCX on {{site.data.keyword.cloud_notm}} の削除は自動的に行われます。 このサービスを正しく削除するためには、以下の手順を実行します。
   * クラウド・サイドの HCX Manager 用に注文した HCX ライセンスを非アクティブにします。
   * HCX Manager を削除します。
   * HCX 用に予約されていた vMotion IP アドレスを解放します。
   * HCX 関連リソース・プールが空であれば、それらを削除します。
   * HCX 関連フォルダーが空であれば、それらを削除します。
   * HCX 管理エッジ・アプライアンスを削除します。

## 関連リンク

* [HCX on {{site.data.keyword.cloud_notm}} の注文](hcx_ordering.html)
* [HCX on {{site.data.keyword.cloud_notm}} の管理](managinghcx.html)
* [HCX の用語集](hcx_glossary.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [VMware Hybrid Cloud Extension の概要](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension の資料](https://hcx.vmware.com/#vm-documentation)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Zerto on IBM Cloud の管理

インスタンスに Zerto on {{site.data.keyword.cloud}} サービスをデプロイすると、Zerto Virtual Replication の構成や更新が可能になり、新しく追加した ESXi サーバーにさらに Virtual Replication Appliance をデプロイできるようになります。

## 独自の証明書を Zerto に使用する

ベスト・プラクティスとして、Zerto Virtual Manager (ZVM) には独自の SSL 証明書を使用することをお勧めします。 Zerto on {{site.data.keyword.cloud_notm}} をデプロイした後、[How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window} に示されている手順に従って、ZVM 用の SSL 証明書を独自の証明書に置き換えてください。

## Zerto レプリケーションの構成の管理

Zerto レプリケーションの構成を管理する (例えば、仮想マシンを複製するための Zerto インスタンスの再ペア化や仮想保護グループの構成) には、vCenter 資格情報を使用して管理者権限で Zerto Virtual Replication コンソールにログインします。

2 つの異なる {{site.data.keyword.cloud_notm}} Zerto インスタンス間で複製する場合は、それらの Zerto インスタンス間で直接複製するように構成できます。 {{site.data.keyword.cloud_notm}} Zerto インスタンスとお客様所有のデータ・センターの間で複製する場合は、お客様所有のデータ・センターに自分で Zerto をインストールする必要があります。 お客様所有のデータ・センターにインストールするこの Zerto インスタンスのライセンスは、このインスタンスと {{site.data.keyword.cloud_notm}} Zerto インスタンスをペアにすると自動的に交付されます。

Zerto レプリケーションはネットワーク・アドレス変換 (NAT) トラバーサルをサポートしていないため、{{site.data.keyword.cloud_notm}} Zerto インスタンスとお客様所有のデータ・センターの間の接続を確立するためには、いずれかの側の Zerto Virtual Manager (ZVM) アプライアンスまたは Zerto Virtual Replication Appliance (VRA) 上の経路のカスタマイズが必要になる場合があります。さらに、両サイト間のセキュア・トンネリングが必要になる場合もあります。 ZVM アプライアンス上の経路を構成したり再構成したりするときは、使用レポートが作成されるように、すべての ZVM アプライアンスが `zerto.com` に正常に接続できるようにする必要があります。 この接続は、`https://www.zerto.com` へのブラウザー・セッションを ZVM アプライアンスから開くことによって確認できます。

**注**: {{site.data.keyword.cloud_notm}} 上の Cloud Foundation インスタンスと vCenter Server インスタンスの Management VMware NSX Edge Services Gateway (ESG) は、ZVM から発信されるアウトバウンド HTTPS (TCP ポート 443) 通信を許可するように事前構成されています。

## Zerto Virtual Replication の更新

Zerto Virtual Replication を更新するには、Zerto Virtual Replication コンソールにログインします。

## 新しく追加した ESXi サーバーへの VRA のデプロイ

インスタンスの 1 次クラスター用の ESXi サーバーを追加または削除すると、VRA は自動的にデプロイまたは削除されます。 インスタンスの 2 次クラスター内の ESXi サーバーには VRA が自動デプロイされませんが、Zerto Virtual Replication コンソールから自分でデプロイできます。

## 関連リンク

* [Zerto on IBM Cloud の概要](addingzertodr.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](managing_zerto_services.html)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Zerto 災害復旧](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/zerto){:new_window}
* [Explanation of Zerto Virtual Replication Alerts](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)

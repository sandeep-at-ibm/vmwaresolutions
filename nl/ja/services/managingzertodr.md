---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud の管理
{: #managingzertodr}

インスタンスに Zerto on {{site.data.keyword.cloud}} サービスをデプロイすると、Zerto Virtual Replication の構成や更新が可能になり、新しく追加した ESXi サーバーにさらに Virtual Replication Appliance をデプロイできるようになります。

## 独自の証明書を Zerto に使用する
{: #managingzertodr-ssl-cert}

ベスト・プラクティスとして、Zerto Virtual Manager (ZVM) には独自の SSL 証明書を使用します。 Zerto on {{site.data.keyword.cloud_notm}} をデプロイした後、ZVM 用の SSL 証明書を独自の証明書に置き換えてください。 詳しくは、[How to use a CER SSL Certificate to Replace the Self-Signed Certificate for the ZVM, ZSSP, or ZCM](https://www.zerto.com/myzerto/knowledge-base/how-to-use-a-cer-ssl-certificate-to-replace-the-self-signed-certificate-for-the-zvm-zssp-or-zcm/){:new_window} を参照してください。

## Zerto レプリケーションの構成の管理
{: #managingzertodr-manage}

Zerto レプリケーションの構成を管理するには、vCenter 資格情報を使用して管理者権限で Zerto Virtual Replication コンソールにログインします。 例えば、仮想マシンを複製するには、Zerto インスタンスを再ペア化したり、仮想保護グループを構成したりします。

2 つの異なる {{site.data.keyword.cloud_notm}} Zerto インスタンス間で複製する場合は、それらの Zerto インスタンス間で直接複製するように構成できます。 {{site.data.keyword.cloud_notm}} Zerto インスタンスとお客様所有のデータ・センターの間で複製する場合は、お客様所有のデータ・センターに自分で Zerto をインストールする必要があります。 このインスタンスのライセンスは、このインスタンスと {{site.data.keyword.cloud_notm}} Zerto インスタンスをペアにすると自動的に交付されます。

Zerto レプリケーションでは、ネットワーク・アドレス変換 (NAT) トラバーサルはサポートされていません。 {{site.data.keyword.cloud_notm}} Zerto インスタンスとお客様所有のデータ・センターの間の接続を確立するためには、いずれかの側の Zerto Virtual Manager (ZVM) アプライアンスまたは Zerto Virtual Replication Appliance (VRA) 上の経路のカスタマイズが必要になる場合があります。 接続を確立するには、サイト間のセキュア・トンネリングが必要になる場合もあります。 ZVM アプライアンス上の経路を構成したり再構成したりするときは、使用レポートが作成されるように、すべての ZVM アプライアンスが `zerto.com` に正常に接続できるようにする必要があります。 この接続は、`https://www.zerto.com` へのブラウザー・セッションを ZVM アプライアンスから開くことによって確認できます。

{{site.data.keyword.cloud_notm}} 上の Cloud Foundation インスタンスと vCenter Server インスタンスの Management VMware NSX Edge Services Gateway (ESG) は、ZVM から発信されるアウトバウンド HTTPS (TCP ポート 443) 通信を許可するように事前構成されています。
{:note}

## Zerto Virtual Replication の更新
{: #managingzertodr-update}

Zerto Virtual Replication を更新するには、Zerto Virtual Replication コンソールにログインします。

## 新しく追加した ESXi サーバーへの VRA のデプロイ
{: #managingzertodr-deploy}

インスタンスの 1 次クラスター用の ESXi サーバーを追加または削除すると、VRA は自動的にデプロイまたは削除されます。 インスタンスの 2 次クラスター内の ESXi サーバーには VRA が自動デプロイされません。 VRA は、Zerto Virtual Replication コンソールから自分でデプロイできます。

## 関連リンク
{: #managingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}
* [Zerto 災害復旧](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture/zerto){:new_window}
* [Explanation of Zerto Virtual Replication Alerts](https://www.zerto.com/myzerto/knowledge-base/explanation-of-zvr-alerts/)

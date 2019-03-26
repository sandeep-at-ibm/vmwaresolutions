---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation インスタンスのマルチサイト構成
{: #sd_multisite}

{{site.data.keyword.vmwaresolutions_full}} を使用すると、短時間でインスタンスをさまざまな場所にデプロイして稼働させることができます。

## メモ
{: #sd_multisite-notes}

* マルチサイト構成では、VMware Cloud Foundation インスタンスと VMware vCenter Server インスタンスをリンクすることはできません。
* V2.0 にデプロイされたインスタンスを、それより前のリリースからのインスタンスとリンクすることはできません (旧リリースを V2.0 にアップグレードした場合でも同様です)。

## マルチサイト・デプロイメントのコンポーネント
{: #sd_multisite-deployment-components}

マルチサイト・デプロイメントは以下のコンポーネントで構成されます。

* **プライマリー・インスタンス**: VMware Cloud Foundation の プライマリー・インスタンスには以下の構成があります。
  *  Microsoft Active Directory (AD) および DNS (ドメイン・ネーム・システム) ルート・ドメイン
  *  Cloud Foundation サブドメイン
  *  SSO (シングル・サインオン) ドメイン
  *  SSO サイト名
* **セカンダリー・インスタンス**: プライマリー・インスタンスにリンクしている 1 つ以上の Cloud Foundation セカンダリー・インスタンス。以下の構成があります。
   *  SSO サイト名
   *  プライマリー・インスタンスのルート・ドメインにリンクされた DNS サブドメイン
   *  プライマリー・インスタンス上の AD 仮想マシンとセカンダリー・インスタンス上の AD 仮想マシン間に DNS と AD の複製がセットアップされます
   *  プライマリー・インスタンスの PSC (Platform Services Controller) と複製するためにデプロイされ、構成された PSC
   *  セカンダリー・インスタンスの VMware vCenter には、プライマリー・インスタンスの vCenter との拡張リンク・モードがセットアップされます

## Cloud Foundation のマルチサイト・デプロイメント
{: #sd_multisite-deployment}

マルチサイト構成機能では、1 つのプライマリー・サイトおよび最大 7 つのセカンダリー・サイトから成る、ハブ・アンド・スポーク・トポロジーを使用します。 サポートされるのは単一層のサイトであるため、他のセカンダリー・サイトにリンクされた後続のサイトは構成できません。 マルチサイト構成では、すべてのインスタンスにわたって、ESXi サーバーを合計 128 台使用できます。

128 台を超える ESXi サーバーのマルチサイト・デプロイメントが必要な構成を使用する場合は、IBM サポートにお問い合わせください。 詳しくは、[IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)を参照してください。
{:note}

以下の図は、Cloud Foundation のマルチサイト・デプロイメントの全体図を示しています。

図 1. Cloud Foundation のマルチサイト・デプロイメント

![Cloud Foundation のマルチサイト・デプロイメント](multisite-hub-spoke.svg "Cloud Foundation のマルチサイト・デプロイメント")

このモデルには以下の層が含まれています。

* **プライマリー・インスタンス**: マルチサイト構成では、インスタンスの注文プロセス時に、最初のインスタンスがプライマリーとして定義されます。
* **セカンダリー・インスタンス**: マルチサイト構成では、注文プロセス時に、プライマリー・インスタンスに接続するインスタンスがセカンダリーとして定義されます。

マルチサイト構成では、最大 8 つのインスタンス (プライマリー・インスタンス 1 つとセカンダリー・インスタンス 7 つ) をデプロイできます。

マルチサイト構成の一部になっている Cloud Foundation インスタンスを削除するには、特別な計画が必要です。 詳しくは、[ マルチサイト構成での Cloud Foundation インスタンスの削除](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)を参照してください。
{:note}

## 関連リンク
{: #sd_multisite-related}

* [NSX Manager へのプライマリ ロールの割り当て](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [セカンダリ NSX Manager の設定](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [Active Directory Trusts supported with VMware vCenter Single Sign-On](https://kb.vmware.com/kb/2064250){:new_window}
* [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}

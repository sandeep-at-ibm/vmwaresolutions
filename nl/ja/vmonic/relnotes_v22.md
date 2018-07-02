---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-18"

---

# V2.2 のリリース・ノート

このリリースには、新機能、コンポーネントの更新、使いやすさの向上、バグ修正などが含まれています。 各リリースの修正された問題のリスト、製品に関する既知の問題、および {{site.data.keyword.vmwaresolutions_full}} を使用するためのその他のヒントについては、[{{site.data.keyword.vmwaresolutions_short}} dW の回答](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}を参照してください。

## Spectre および Meltdown への対処

{{site.data.keyword.vmwaresolutions_short}} は、Spectre および Meltdown と呼ばれる脆弱性 (CVE-2017-5753、CVE-2017-5715、CVE-2017-5754) に対して VMware から提供されたパッチをリリースしました。

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

詳しくは、[Spectre および Meltdown 脆弱性への対処](../vmonic/trbl_fix_spectre.html)を参照してください。

## IBM CloudDriver 仮想マシンのアップグレード

IBM CloudDriver 仮想マシンは、V2.2 へのアップグレード処理中に、CentOS Linux リリース 7.4.1708 を使用して再デプロイされます。 また、新たにプロビジョンされるすべてのインスタンスの IBM CloudDriver には CentOS Linux リリース 7.4.1708 が含まれています。

**重要:**

* IBM CloudDriver 仮想マシンを参照するバックアップ・ソリューションを使用している場合は、V2.2 にアップグレードした後、バックアップ・ソリューションが新しい IBM CloudDriver 仮想マシンを参照していることを確認してください。
* V2.2 にアップグレードする前に、レガシー Veeam VSI を Veeam on {{site.data.keyword.cloud_notm}} サービスに置き換えてください。 レガシー Veeam は V2.2 以降のリリースではサポートされないため、レガシー Veeam に関連付けられた管理コンポーネントのバックアップからリストアすることはできません。

Veeam on {{site.data.keyword.cloud_notm}} サービスを使用する方法について詳しくは、以下を参照してください。
* [Veeam on {{site.data.keyword.cloud_notm}} のコンポーネントと考慮事項](../services/veeam_considerations.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](../services/managingveeam.html)

## VMware Federal on IBM Cloud のサポート

VMware Federal on {{site.data.keyword.cloud_notm}} では、WDC03 の Federal on {{site.data.keyword.CloudDataCent_notm}}で基本 vCenter Server インスタンスを注文できます。 VMware Federal on {{site.data.keyword.cloud_notm}} は、vCenter Server インスタンスのオファリングの一部をサポートするだけでなく、米国連邦政府機関に、デプロイされた VMware vCenter Server インスタンスを保護するオプションを提供します。 デプロイされたインスタンスを保護するオプションを選択すると、インスタンスに関する保管済みの機密情報が削除され、ホストとクラスターの追加や削除など、管理機能の目的でインスタンスに継続してアクセスするために開かれている管理接続が削除されます。 この保護オプションを選択すると、インスタンスの完全削除を除くすべての管理機能が無効になります。

VMware Federal インスタンスを保護する前に考慮すべき重要な事項については、[VMware Federal インスタンスの保護](../vcenter/vc_fed_securinginstance.html)を参照してください。

(2018 年 4 月 2 日更新) ESXi サーバーを追加または削除することによって、VMware Federal インスタンスの容量を拡張または縮小できるようになりました。 このオプションは、保護されていない VMware Federal インスタンスでのみ使用できます。

詳しくは、以下を参照してください。

* [VMware Federal on {{site.data.keyword.cloud_notm}} の概要](../vcenter/vc_fed_overview.html)
* [VMware Federal インスタンスのクラスターの追加、表示、削除](../vcenter/fed_addviewdeleteclusters.html)
* [VMware Federal インスタンスの容量の拡張と縮小](../vcenter/vc_fed_addingremovingservers.html)

## ESXi サーバーの拡張構成設定

V2.2 以降のリリースでは、新規インスタンスは、ESXi サーバーの新しい拡張構成設定を使用して注文されます。
前のリリースから V2.2 以降のリリースにアップグレードしたインスタンスの場合は、ESXi サーバーを再始動しなければならない設定があるので、自動的に適用される構成設定は一部だけです。

ストレージ拡張が適切にサポートされるように、残りの構成設定を新しい値に変更してすべてのインスタンスで統一することをお勧めします。 IBM は、{{site.data.keyword.cloud_notm}} for VMware Solutions の今後のすべてのリリースで、これらの新しい設定だけを使用してテストする予定です。

詳しくは、以下の _ESXi サーバーの拡張構成設定_を参照してください。
* [vCenter Server の部品構成表](../vcenter/vc_bom.html#advanced-configuration-settings-for-esxi-servers)
* [Cloud Foundation の部品構成表](../sddc/sd_bom.html#advanced-configuration-settings-for-esxi-servers)

## 初期クラスターで最大 51 台の ESXi サーバーをサポートし、追加のクラスターで最大 59 台の ESXi サーバーをサポート

V2.2 以降のリリースでは、ESXi サーバー数を初期クラスターについては最大 51 台まで、追加のクラスターについては最大 59 台まで増やせるようになりました。

**重要:** V2.1 以前のリリースでデプロイされたインスタンスの場合、クラスター・サイズを 32 より増やすには、必要な vSAN サポートを有効にする必要があります。 ESXi サーバー数を増やす方法と手順について詳しくは、[ESXi サーバーに関するよくある質問](../vmonic/faq_esxi.html#how-many-esxi-servers-can-i-add-to-a-cluster-)の_クラスターには ESXi サーバーをいくつ追加できますか?_ を参照してください。

## vCenter Server および Cloud Foundation インスタンスのその他のネットワーク構成オプション

vCenter Server および Cloud Foundation インスタンスの注文で、既存のパブリック VLAN とプライベート VLAN をネットワーク構成に再利用できるようになりました。 既存の VLAN がない場合は、従来どおり、新規パブリック VLAN 1 つと新規プライベート VLAN 2 つを注文するオプションを利用できます。

既存の VLAN を選択する前に考慮すべき重要な事項については、以下の資料にある『*ネットワーク・インターフェースの設定*』セクションを参照してください。
* [vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html)
* [Cloud Foundation インスタンスの注文](../sddc/sd_orderinginstance.html)

## VMware vCenter Server インスタンスの更新

### NSX コンポーネントとポート・グループの構成設定の更新

現行リリースでは、VMware NSX for vSphere 6.3.5 コンポーネントの更新が適用されます。 コンポーネントについて詳しくは、[vCenter Server の部品構成表](../vcenter/vc_bom.html)を参照してください。

V2.2 以降のリリースでデプロイされる VMware vCenter Server インスタンスでは、NSX およびポート・グループの構成設定が変更されています。 詳しくは、[vCenter Server Software 部品構成表](../vcenter/vc_bom.html#nsx-and-port-group-configuration-settings)の『*NSX とポート・グループの構成設定*』セクションを参照してください。

### DNS 構成の新しいオプション

管理クラスターに、Microsoft Active Directory (AD) として単一の Microsoft Windows Server 仮想サーバー・インスタンス (VSI) をデプロイするか、2 つの高可用性 Microsoft Windows 仮想マシンをデプロイするかを選択できるようになりました。 V2.2 より前のリリースでは、デフォルトで単一の Microsoft Windows VSI が Microsoft AD として自動的にデプロイされていました。 2 つの Microsoft Windows 仮想マシンを選択する新しいオプションを使用すると、プライバシーを強化できるうえに、Veeam サービスを使用してそれらの仮想マシンをバックアップおよびリストアできます。

**注:** 2 つの Microsoft Windows 仮想マシンを使用するようにインスタンスを構成する場合は、2 つの Microsoft Windows Server 2012 R2 ライセンスを提供する必要があります。 Microsoft Windows Server 2012 R2 Standard エディションのライセンスと Microsoft Windows Server 2012 R2 Datacenter エディションのライセンスを使用してください。 仮想マシンは 30 日以内に有効にしてください。

詳しくは、[vCenter Server インスタンスの注文](../vcenter/vc_orderinginstance.html#system-settings)の『*システム設定*』セクションを参照してください。

### インスタンスあたりのクラスター数の増加

V2.2 以降のリリースでデプロイまたは V2.2 以降のリリースにアップグレードされた VMware vCenter Server インスタンスには、最大 10 個のクラスターを追加できるようになりました。 詳しくは、[vCenter Server インスタンスのクラスターの追加と表示](../vcenter/vc_addingviewingclusters.html)を参照してください。

## VMware vSphere クラスターの更新

### ビジネス・パートナーのお客様が利用できるコンポーネント・ライセンス・バンドル

ビジネス・パートナーのユーザーは、新規 vSphere クラスターを注文するときに、4 つのコンポーネント・ライセンス・バンドルから選択できるようになりました。 「Standard with Management」、「Advanced」、「Advanced with Networking」、または「Advanced with Networking and Management」から選択します。 追加の VMware コンポーネントを注文に含めることもできます。 ただし、ライセンス持ち込みのオプションは利用できません。

詳しくは、[新規 vSphere クラスターの注文](../vsphere/vs_orderinginstances.html)の『*ライセンス交付の設定*』セクションを参照してください。

## NetApp ONTAP Select インスタンスの更新

現行リリースでは、NetApp ONTAP Select 9.3 の更新が適用されます。

### 大容量の IBM Cloud ベア・メタル・サーバーのための SATA ドライブ数の増加

NetApp ONTAP Select の大容量の{{site.data.keyword.baremetal_short}}では、34 個の SATA ドライブを使用できるようになりました。 詳しくは、[NetApp ONTAP Select の概要](../netapp/np_netappoverview.html#netapp-ontap-select-instance-components)の『*NetApp ONTAP Select インスタンスのコンポーネント*』セクションを参照してください。

## アドオン・サービスの更新

### F5 on IBM Cloud の帯域幅オプションの拡張

Cloud Foundation および vCenter Server インスタンスに F5 on {{site.data.keyword.cloud_notm}} サービスをインストールするときに、最大帯域幅として 10 Gbps を選択できるようになりました。 詳しくは、[F5 on {{site.data.keyword.cloud_notm}} の考慮事項](../services/f5_considerations.html)を参照してください。

### KMIP for VMware on IBM Cloud

KMIP for VMware on {{site.data.keyword.cloud_notm}} サービスを含めて Cloud Foundation または vCenter Server インスタンスを注文したり、初期デプロイメントの後に既存の Cloud Foundation または vCenter Server インスタンスにこのサービスを追加したりできるようになりました。

このサービスは、24 時間 365 日の高可用性サービスを提供し、{{site.data.keyword.cloud_notm}} で VMware が使用する暗号鍵を管理します。 このサービスは、お客様が暗号鍵を作成、取得、有効化、取り消し、破棄できるようにするランタイム機能を提供します。また、クライアントの資格情報と暗号鍵の関連付けを管理する管理機能も提供します。

詳しくは、[KMIP for VMware on {{site.data.keyword.cloud_notm}} に関する考慮事項](../services/kmip_considerations.html)を参照してください。

### IBM Spectrum Protect Plus on IBM Cloud

IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスが、V2.2 以降のリリースでデプロイまたは V2.2 以降のリリースにアップグレードされたインスタンスでのみ使用できるようになりました。

このサービスは、仮想環境のデータ保護、データ再使用、データ・リカバリーのための効率的でスケーラブルなソリューションを提供します。 スタンドアロン・ソリューションとして実装することも、お客様の IBM Spectrum Protect&trade; Plus 環境と統合して長期保管とデータ・ガバナンスのためにコピーをオフロードすることもできます。

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスは、ワークロード VM にのみデータ保護を提供します。

詳しくは、[IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の管理](../services/managingspp.html)を参照してください。

### マネージド・サービス

Veeam on {{site.data.keyword.cloud_notm}} および Zerto on {{site.data.keyword.cloud_notm}} のマネージド・サービスを、VMware vCenter Server および VMware Cloud Foundation インスタンスで使用できるようになりました。 複雑なソリューションと環境を自分で管理したくない場合には、マネージド・サービスを要求することをお勧めします。

Veeam on {{site.data.keyword.cloud_notm}} サービスは、VMware ハイパーバイザーとシームレスに統合され、企業が高可用性 (HA) を実現するのを支援します。 Veeam バックアップ・ソフトウェアと IBM Resiliency Backup as a Service の両方を使用して、完全に管理されたバックアップ環境をデプロイできます。

Zerto on {{site.data.keyword.cloud_notm}} サービスは、レプリケーション機能と災害復旧機能を提供します。これをデプロイメント・オファリングに統合すると、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータを保護および復旧できるようになります。 Zerto DR ソフトウェアと IBM レジリエンシー・サービスの両方を使用して、完全に管理される災害復旧 (DR) 環境をデプロイできます。

インスタンスのマネージド・サービスは、**「開始」**ページから要求できます。新規インスタンスを注文することも、既存のインスタンスにこのサービスを追加することもできます。

詳しくは、以下を参照してください。
* [Veeam on {{site.data.keyword.cloud_notm}} のサービスの要求](../services/managing_veeam_services.html)
* [Zerto on {{site.data.keyword.cloud_notm}} のサービスの要求](../services/managing_zerto_services.html)

## 新規資料および更新された資料

* VMware vSphere クラスターだけでなく、Cloud Foundation インスタンスと vCenter Server インスタンスのサポート機能を含む比較表が、資料に追加されました。 各タイプのインスタンスで利用できる機能の違いを一目で確認できます。 詳しくは、[オファリングの比較表](../vmonic/inst_comp_chart.html)を参照してください。

* VMware vSphere クラスターだけでなく、Cloud Foundation インスタンスと vCenter Server インスタンスの資料にも、VLAN とソフトウェアの部品構成表 (BOM) が追加されました。

  詳しくは、以下を参照してください。

  * [vCenter Server の部品構成表](../vcenter/vc_bom.html)
  * [Cloud Foundation の部品構成表](../sddc/sd_bom.html)
  * [VMware vSphere の部品構成表](../vsphere/vs_bom.html)

## ユーザー・インターフェースの更新と向上

ユーザー・インターフェース全体が以下のように改善されました。

* インスタンスを注文するときに、すべてのハードウェア・オプションがロケーションでフィルタリングされ、選択できないオプションは無効状態として表示されるようになりました。
* 既存の構成に基づいて vSphere クラスターを注文するときには、**{{site.data.keyword.baremetal_short}}**構成が自動的に入力されるようになりました。 その構成は要件に応じて更新できます。
* ユーザー・インターフェースで適切な設定を選択できるように、エラー・メッセージとツールチップにさまざまな改善が行われました。

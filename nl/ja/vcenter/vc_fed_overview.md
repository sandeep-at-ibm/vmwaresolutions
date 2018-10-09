---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-19"

---

# VMware Federal on IBM Cloud の概要

VMware Federal on {{site.data.keyword.cloud}} では、基本 vCenter Server インスタンスを注文できるだけでなく、デプロイした vCenter Server インスタンスを保護するための米国連邦政府機関向けのオプションも用意されています。デプロイされたインスタンスを保護すると、インスタンスに関して保管された機密情報が削除されます。また、インスタンスにアクセスするために開かれている接続も削除されます。つまり、ホストとクラスターの追加や削除などの管理機能は使用できなくなります。この保護オプションを選択した場合、使用できる唯一の機能はインスタンスの削除です。

vCenter Server on {{site.data.keyword.cloud_notm}} および vCenter Server アーキテクチャーについて詳しくは、[vCenter Server の概要](vc_vcenterserveroverview.html)を参照してください。

**注意:** VMware Federal on {{site.data.keyword.cloud_notm}} は、vCenter Server オファリングの一部のみを提供しています。 マルチサイト構成、事前構成型の {{site.data.keyword.cloud_notm}} ベア・メタル・サーバー、ライセンス持ち込み (BYOL)、アドオン・サービスの注文のオプションはサポートされません。

## VMware Federal on IBM Cloud インスタンスの技術仕様

以下のコンポーネントが含まれています。

### ベア・メタル・サーバー

以下のいずれかの構成でカスタマイズ型{{site.data.keyword.baremetal_short}}を 2 つ以上注文できます。

* 2-CPU Intel Broadwell 世代 (Intel Xeon E5-2600 v4 シリーズ)
* 2-CPU Intel Skylake 世代 (Intel Xeon 4100/5100/6100 シリーズ)

NFS ストレージ構成の場合、推奨する{{site.data.keyword.baremetal_short}}の数はデフォルトの 3 です。

**注:** vSAN ストレージを選択する構成には、4 つの{{site.data.keyword.baremetal_short}}が必要です。

### ネットワーキング

以下のネットワーキング・コンポーネントが注文されます。
*  VLAN (仮想 LAN) 3 つ: パブリック VLAN 1 つとプライベート VLAN 2 つ
*  レイヤー 2 (L2) ネットワークに接続されたローカル・ワークロード間で実行される可能性のある東西通信用の DLR (分散論理ルーター) を備えた VXLAN (仮想拡張可能 LAN) 1 つ。 この VXLAN は、サンプルのルーティング・トポロジーとしてデプロイされるので、変更したり、作成の基礎として使用したり、削除したりできます。 また、DLR の新しい論理インターフェースにさらに VXLAN を接続してセキュリティー・ゾーンを追加することもできます。
*  以下の 2 つの VMware NSX Edge Services Gateway
  * アウトバウンド HTTPS 管理トラフィック用のセキュアな管理サービス VMware NSX Edge Services Gateway (ESG)。これは、管理ネットワーキング・トポロジーの一部として IBM がデプロイします。 この ESG は、IBM 管理仮想マシンが、自動化に関連する特定の外部 IBM 管理コンポーネントと通信するために使用します。 詳しくは、[ユーザー管理の ESG を使用するためのネットワークの構成](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)を参照してください。

    **重要**: ユーザーは、この ESG にアクセスすることはできず、使用できません。 これを変更すると、{{site.data.keyword.vmwaresolutions_short}} コンソールから vCenter Server インスタンスを管理できなくなる可能性があります。 また、ファイアウォールを使用したり、外部 IBM 管理コンポーネントへの ESG 通信を無効にしたりすると、{{site.data.keyword.vmwaresolutions_short}} が使用できなくなります。
  * アウトバウンドとインバウンドの HTTPS ワークロード・トラフィック用のユーザー管理のセキュアな VMware NSX Edge Services Gateway。これは、VPN アクセスまたはパブリック・アクセスを提供するためにユーザーが変更可能なテンプレートとして IBM がデプロイします。 詳しくは、[ユーザー管理の NSX Edge にはセキュリティーのリスクがありますか?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-) を参照してください。

  **注**: アウトバウンド HTTPS 管理トラフィック用の VMware NSX Edge Services (ESG) は、デプロイされた VMware Federal インスタンスを保護するアクションの一環として削除されます。 詳しくは、[VMware Federal インスタンスの保護](vc_fed_securinginstance.html)を参照してください。

### 仮想サーバー・インスタンス

以下の VSI (仮想サーバー・インスタンス) が注文されます。
* IBM CloudBuilder の VSI。これは、インスタンスのデプロイメントが完了した後にシャットダウンされます。
* (V2.3 以降のインスタンス) Microsoft Active Directory (AD) 用に 1 つの Microsoft Windows Server VSI をデプロイするか、管理クラスターに 2 つの高可用性 Microsoft Windows VM をデプロイしてセキュリティーと信頼性を強化するかを選択できます。
* (V2.2 のインスタンス) Microsoft Active Directory (AD) 用の Microsoft Windows Server VSI がデプロイされて参照可能になります。この VSI がインスタンスの DNS として機能し、ここにホストと仮想マシンが登録されます。

### ストレージ

最初のデプロイメントのときに、vSAN と NFS のどちらかのストレージ・オプションを選択できます。

#### vSAN ストレージ

vSAN オプションでは、構成をカスタマイズできます。ディスクのタイプと数にも次のように多様なオプションがあります。
* ディスクの数: 2、4、6、8。
* ストレージ・ディスク: 960 GB SSD SED、1.9 TB SSD SED、3.8 TB SSD SED。

  さらに、ホストごとに 960 GB のキャッシュ・ディスクが 2 つ注文されます。
* High-Performance Intel Optane オプション。合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されます。このオプションは CPU モデルに応じて異なります。

#### NFS ストレージ

NFS オプションでは、ワークロード用のファイル・レベルの共有ストレージをカスタマイズできます。サイズとパフォーマンスをさまざまなオプションから選択できます。
* サイズ: 1、2、4、8、12 TB。
* パフォーマンス: 2、4、10 IOPS/GB。
* ファイル共有は個々に構成します。

NFS オプションを選択すると、管理コンポーネント用の 2 TB の 4 IOPS/GB ファイル共有が 1 つ注文されます。

### IBM 提供のライセンスおよび料金

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition (Base、Advanced、または Enterprise) 6.4
* (vSAN クラスターの場合) VMware vSAN Advanced または Enterprise 6.6

## VMware Federal on IBM Cloud 拡張ノードの技術仕様

vCenter Server 拡張ノードごとに、{{site.data.keyword.cloud_notm}} アカウントに以下のコンポーネントがデプロイされ、料金が発生します。

### 拡張ノード用のハードウェア

[VMware Federal on {{site.data.keyword.cloud_notm}} インスタンスの技術仕様](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances)に示されている構成になっている、1 台のベア・メタル・サーバー。

### 拡張ノード用のライセンスと料金

* VMware vSphere Enterprise Plus 6.5u1 1 つ
* VMware NSX Service Providers Edition (Base、Advanced、Enterprise) 6.4 1 つ
* (vSAN クラスターの場合) VMware vSAN Advanced または Enterprise 6.6

**重要**: {{site.data.keyword.cloud_notm}} アカウントで作成した {{site.data.keyword.vmwaresolutions_short}} コンポーネントは、{{site.data.keyword.vmwaresolutions_short}} コンソールから管理する必要があります。{{site.data.keyword.slportal}}やその他の手段でコンソール以外から管理することはできません。 {{site.data.keyword.vmwaresolutions_short}} コンソール以外でコンポーネントを変更した場合、変更はコンソールと同期されません。

**注意**: インスタンスを注文したときに {{site.data.keyword.cloud_notm}} アカウントにインストールされた {{site.data.keyword.vmwaresolutions_short}} コンポーネントを、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で管理すると、環境が不安定になる可能性があります。 これには以下の管理アクティビティーが該当します。
*  コンポーネントの追加、変更、返却、または削除
*  ESXi サーバーの追加または削除によるインスタンス容量の拡張または縮小
*  コンポーネントのパワーオフ

   {{site.data.keyword.slportal}}での共有ストレージのファイル共有の管理は、上記アクティビティーに該当しません。 これには、共有ストレージのファイル共有の注文、削除 (マウントされている場合はデータ・ストアに影響する可能性があります)、承認、マウントなどのアクティビティーが含まれます。

### 関連リンク

* [VMware Federal インスタンスの要件と計画](vc_fed_planning.html)
* [VMware Federal インスタンスの注文](vc_fed_orderinginstance.html)
* [VMware Federal インスタンスのクラスターの追加、表示、削除](fed_addviewdeleteclusters.html)
* [VMware Federal インスタンスの容量の拡張と縮小](vc_fed_addingremovingservers.html)
* [VMware Federal インスタンスの保護](vc_fed_securinginstance.html)
* [{{site.data.keyword.cloud_notm}} のファイル・ストレージとブロック・ストレージ](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}

---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスの IBM ユーザー ID およびデプロイメント履歴のメッセージ
{: #ibm_use}

自動化機能と操作のロギングのために、{{site.data.keyword.cloud}} はお客様のアカウントにアクセスする必要があります。

## ユーザー ID
{: #ibm_use-user-ids}

{{site.data.keyword.vmwaresolutions_short}} では、VMware インスタンスにホスト、クラスター、ストレージを追加するなどの操作をお客様が行った場合に {{site.data.keyword.cloud_notm}} の自動化機能で使用するために、お客様のアカウント内に一連のユーザーが維持されます。以下のセクションで、{{site.data.keyword.cloud_notm}} の自動化機能のユーザー ID について説明します。

IBM ユーザー ID が削除または無効化された場合、あるいはそのパスワードが変更された場合、VMware インスタンスの操作は失敗します。
{:important}

### vCenter および Platform Services Controller のユーザー ID
{: #ibm_use-user-ids-vcenter-psc}

V2.5 以降、{{site.data.keyword.vmwaresolutions_short}} では、以下の ID を使用して、デフォルトで埋め込まれている ID ソースが vCenter に追加されます。

表 1. vCenter および Platform Services Controller のユーザー ID

| ユーザー     | ユーザー ID      | 方法 | 説明 |
|:---------|:-------------|:-------|:------------|
| IBM      | root         | SSH    | VMware 構成 (VMware 高可用性のセットアップや分散スイッチの作成など) に使用されます。デプロイメント後に、vCenter Server のプライマリー・インスタンスとセカンダリー・インスタンスをペアにするために使用されます。|
| お客様 | customerroot | SSH    | お客様専用に作成されます。|
| IBM      | automation@``root_domain``<br/>(Active Directory ユーザー) | HTTP | デプロイメント後に、ホストとクラスターの追加/削除、およびアドオン・サービスの仮想マシンのデプロイと構成を行うために使用されます。|
| お客様 | Administrator@vsphere.local | HTTP | お客様専用に作成されます。|

HTTP は、vCenter のセットアップと構成のほかに、VMware の操作 (vCenter のリソース管理のためのホスト、クラスター、ストレージの追加など) にも使用されます。
{:note}

### NSX Manager のユーザー ID
{: #ibm_use-user-ids-nsx-mgr}

NSX Manager のユーザー ID は、サービスの ESG ルールを追加するために使用します。

表 2. NSX Manager のユーザー ID

| ユーザー     | ユーザー ID      | 説明 |
|:---------|:-------------|:------------|
| IBM      | automation@``root_domain``<br/>(Active Directory ユーザー) | デプロイメント後に、NSX VTEP の IP アドレスの管理、ホストとクラスターの追加/削除時のホストとクラスターの構成の管理、アドオン・サービス (パブリック・ネットワーク・アクセスを使用してライセンス交付、アクティベーション、または使用量報告をする必要があるもの) のための ESG 構成の管理を行うために使用されます。|
| お客様 | 管理者        | お客様専用に作成されます。|

### ESXi ホストのユーザー ID
{: #ibm_use-user-ids-esxi}

ESXi ホストのユーザー ID は、ストレージの追加、パッチ適用、vSAN クラスターの構成、およびすべてのサーバー検証コードの実行に使用されます。

表 3. ESXi ホストのユーザー ID

| ユーザー     | ユーザー ID      | 説明 |
|:---------|:-------------|:------------|
| IBM      | ic4vroot     | デプロイメント後に、NFS ストレージの追加とそのストレージのルートの構成のために使用されます。|
| お客様 | root         | お客様専用に作成されます。|

### Microsoft Active Directory のユーザー ID
{: #ibm_use-user-ids-ad}

Active Directory のユーザー ID は、DNS エントリーのセットアップに使用されます。

表 4. Active Directory のユーザー ID

| ユーザー     | ユーザー ID       | 説明 |
|:---------|:------------- |:------------|
| IBM      | automation    | ホストの追加、サービスの仮想マシンの追加、および Active Directory と DNS エントリーのセットアップに使用されます。|
| お客様 | 管理者 | お客様専用に作成されます。|

## インスタンスの履歴メッセージ
{: #ibm_use-msgs}

{{site.data.keyword.cloud_notm}} で実行された VMware インスタンスに関するすべての操作が、インスタンスの履歴ログに記録されます。お客様はインスタンス履歴を参照資料として使用して、それらの操作を確認できます。インスタンスの履歴の表示方法について詳しくは、[vCenter Server インスタンスのデプロイメント履歴を表示する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history)を参照してください。

以下の各セクションに、インスタンスの履歴に発行される可能性があるすべてのメッセージを記載します。

### 一般的なインスタンスの履歴メッセージ
{: #ibm_use-msgs-general}

{{site.data.keyword.vmwaresolutions_short}} では、一般的な操作に対して以下のメッセージが発行されます。

* ``インスタンス・ユーザーと必要なサービスの作成を開始しています... (Starting to create the instance user and required services...)``
* ``インスタンス・ユーザーと必要なサービスの作成が完了しました。(The instance user and required services creation is complete.)``
* ``vCenter Server ライセンスを注文しています... (Ordering the vCenter Server license...)``
* ``VMware ライセンスを注文しています... (Ordering VMware licenses...)``
* ``VMware ライセンスの注文が完了しました。(Completed the order for VMware licenses.)``
* ``<quantity> の追加料金を要求しています... (Ordering <quantity> upcharges...)``
* ``<environment> のインストールと構成を開始しています... (Starting the <environment> installation and configuration...)``
* ``<environment> のインストールと構成が完了しました。(The <environment> installation and configuration is complete.)``
* ``VMware コンポーネントを開始しています... (Starting VMware components...)``
* ``インスタンスのデプロイを開始しています... (Starting to deploy the instance...)``
* ``<instance_name> インスタンスは使用可能です。``
* ``<version> へのアップグレードを開始しています... (Starting upgrade to <version>...)``
* ``<version> へのアップグレードが完了しました。(The upgrade to <version> is complete.)``
* ``VMware コンポーネントのアップグレードが完了しました。(VMware component upgrade is complete.)``
* ``<instance_name> インスタンスの削除を開始しています... (Starting the <instance_name> instance deletion...)``
* ``<instance_name> インスタンスが正常に削除されました。(The <instance_name> instance is successfully deleted.)``
* ``インスタンスのセキュア・ワイプが完了しました。(The secure wipe of the instance is complete.)``
* ``vCenter ライセンスを取り消しています... (Cancelling the vCenter license...)``
* ``インスタンス・ユーザーと必要なサービスを取り消しています... (Cancelling the instance user and required services...)``
* ``<environment> の追加料金を取り消しています... (Cancelling <environment> upcharges...)``
* ``VMware ライセンスの取り消しが進行中です... (VMware license cancellation in progres...) ``
* ``VMware ライセンスの取り消しが完了しました。(VMware license cancellation is complete.)``
* ``SoftLayer の注文が失敗したか、タイムアウトになりました。(The SoftLayer order failed or timed out.)``

### クラスターの履歴メッセージ
{: #ibm_use-msgs-cluster}

{{site.data.keyword.vmwaresolutions_short}} では、vCenter Server クラスターに関して、以下のメッセージが発行されます。

* ``クラスター構成を開始しています... (Starting the cluster configuration...)``
* ``<cluster_name> のクラスター構成を開始しています... (Starting the cluster configuration for <cluster_name>...)``
* ``クラスター構成が完了しました。(The cluster configuration is complete.)``
* ``<cluster_name> クラスターは使用可能です。``
* ``新規クラスターを vCenter に追加しています... (Adding the new cluster into vCenter...)``
* ``新規クラスターが vCenter に追加されました。(The new cluster is added to vCenter.)``
* ``<cluster_name> のクラスターの削除を開始しています... (Starting the cluster deletion for <cluster_name>...)``
* ``<cluster_name> クラスターを vCenter から削除しています... (Deleting the <cluster_name> cluster from vCenter...)``
* ``<cluster_name> クラスターが vCenter から削除されました。(The <cluster_name> cluster is deleted from vCenter.)``
* ``<cluster_name> クラスターが削除されました。(The <cluster_name> cluster is deleted.)``

### 仮想サーバー・インスタンスの履歴メッセージ
{: #ibm_use-msgs-vsi}

{{site.data.keyword.vmwaresolutions_short}} では、仮想サーバー・インスタンス (VSI) に関して、以下のメッセージが発行されます。

* ``IBM CloudDriver の新規仮想サーバー・インスタンスを注文しています... (Ordering a new virtual server instance for the IBM CloudDriver...)``
* ``<ip_address> の IBM CloudDriver 仮想サーバー・インスタンスがプロビジョンされました。(The <ip_address> IBM CloudDriver virtual server instance is provisioned.)``
* ``<ip_address> の IBM CloudDriver 仮想サーバー・インスタンスを取り消しています... (Cancelling the <ip_address> IBM CloudDriver virtual server instance...)``
* ``Microsoft Active Directory/DNS の Microsoft Windows 仮想サーバー・インスタンスの注文を開始しています... (Starting the order for the Microsoft Windows virtual server instance for Microsoft Active Directory/DNS...)``
* ``Active Directory/DNS の Microsoft Windows 仮想サーバー・インスタンスの注文を確認しています... (Verifying the Microsoft Windows virtual server instance order for Active Directory/DNS...)``
* ``Active Directory/DNS の Microsoft Windows 仮想サーバー・インスタンスの準備が完了しました。(The Microsoft Windows virtual server instance for Active Directory/DNS is ready.)``
* ``仮想サーバー・インスタンスの取り消しが進行中です... (Virtual server instance cancellation in progress...)``
* ``関連する仮想サーバー・インスタンスを取り消しています... (Cancelling associated virtual server instances...)``
* ``仮想サーバー・インスタンスの取り消しが完了しました。(Virtual server instance cancellation is complete.)``

### IBM CloudDriver の履歴メッセージ
{: #ibm_use-msgs-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} では、IBM CloudDriver に関して、以下のメッセージが発行されます。

* ``IBM CloudDriver を準備しています... (Preparing the IBM CloudDriver...)``
* ``IBM CloudDriver の準備が完了しました。(The IBM CloudDriver is ready.)``
* ``<ip_address> の IBM CloudDriver は使用可能です。(The <ip_address> IBM CloudDriver is ready to use.)``
* ``IBM CloudDriver の状況を確認しています... (Checking the IBM CloudDriver status...)``
* ``既存の <ip_address> の IBM CloudDriver を再使用しています... (Reusing the existing <ip_address> IBM CloudDriver...)``
* ``既存の IBM CloudDriver を (プロビジョニングで) 再使用しています... (Reusing the existing IBM CloudDriver (In Provisioning)...)``
* ``IBM CloudDriver を解放しています... (Releasing the IBM CloudDriver...)``
* ``<ip_address> の IBM CloudDriver を解放しています... (Releasing the <ip_address> IBM CloudDriver...)``
* ``IBM CloudDriver の削除を開始しています... (Starting the IBM CloudDriver deletion...)``
* ``IBM CloudDriver の削除が完了しました。(Completed the IBM CloudDriver deletion.)``

### ESXi サーバーの履歴メッセージ
{: #ibm_use-msgs-esxi}

{{site.data.keyword.vmwaresolutions_short}} では、ESXi サーバーに関して、以下のメッセージが発行されます。

* ``<quantity> 台の ESXi サーバーの注文を開始しています... (Starting the order for <quantity> ESXi servers...)``
* ``ESXi サーバーの注文を確認しています... (Verifying the ESXi server order...)``
* ``プライベート IP アドレス <ip_addresses> の ESXi サーバーの準備が完了しました。(The ESXi servers with the <ip_addresses> Private IP address are ready.)``
* ``すべての ESXi サーバーが再利用されます。(All ESXi servers are reclaimed.)``
* ``ESXi サーバーを vCenter Server インスタンスに追加しています... (Adding ESXi servers to the vCenter Server instance...)``
* ``ESXi サーバーが正常に更新されました。(The ESXi servers are successfully updated.)``
* ``クラスター用に ESXi サーバーの注文を開始しています... (Starting to order ESXi servers for cluster...)``
* ``<Cluster Name> クラスター用に <quantity> 台の ESXi サーバーの注文を開始しています... (Starting to order <quantity> ESXi servers for the <Cluster Name> cluster...)``
* ``クラスター用の ESXi サーバーの準備が完了しました。(The ESXi servers for the cluster are ready.)``
* ``クラスター用のプライベート IP アドレス <ip_addresses> の ESXi サーバーの準備が完了しました。(ESXi servers with the <ip_addresses> Private IP address are ready for the cluster.``
* ``ESXi サーバーの準備が完了しました。(The ESXi server is ready.)``
* ``ESXi サーバー構成が完了しました。(The ESXi server configuration is complete.)``
* ``ESXi サーバーにプロパティーが正常に追加されました。(The ESXi server is successfully added with the property.)``
* ``ESXi サーバーを追加するためのすべての要求が正常に完了しました。(All requests for adding ESXi servers are successfully completed.)``
* ``ESXi サーバーを追加しています... (Adding the ESXi server...)``
* ``ESXi サーバーのベア・メタル・サーバーを注文しています... (Ordering a Bare Metal Server for the ESXi server...)``
* ``新規 ESXi サーバーが vCenter に追加されました。(New ESXi servers are added to vCenter.)``
* ``新規 ESXi サーバーへのサービスの追加を開始しています... (Starting to add services to the new ESXi servers...)``
* ``選択された ESXi サーバーが正常に取り消されました。(The selected ESXi servers are successfully cancelled.)``
* ``新規 ESXi サーバーがプロビジョンされました。(New ESXi servers are provisioned.)``
* ``新規 ESXi サーバーの検証と準備が完了しました。(New ESXi servers are verified and ready.)``
* ``<cluster_name> クラスター用に <quantity> 台の新規 ESXi サーバーの注文を開始しています... (Starting to order <quantity> new ESXi servers for the <cluster_name> cluster...)``
* ``選択された ESXi サーバーが vCenter Server から削除されました。(The selected ESXi servers are removed from vCenter Server.)``
* ``ESXi サーバーを削除するために、サービスの削除を開始しています... (Starting to remove services to remove ESXi servers...)``
* ``<cluster_name> クラスター用の ESXi サーバーを検証しています... (Verifying ESXi servers for the <cluster_name> cluster...)``
* ``新規クラスターの ESXi サーバーが検証を正常にパスしました。(The new cluster ESXi servers successfully passed verification.)``
* ``新規 ESXi サーバーの注文を確認しています... (Verifying new ESXi server order...)``
* ``ESXi サーバーの注文の確認に失敗しました。(The verification of the ESXi servers order failed.)``
* ``ESXi サーバーのバッチ追加要求を分割しています。(Splitting batch add ESXi servers request.)``
* ``ESXi サーバーを削除する要求のすべてが正常に完了しました。``
* ``ホストが正常に追加されました。(The host is successfully added.)``
* ``ホストが正常に削除されました。(The host(s) are successfully removed.)``
* ``ベア・メタル・サーバーの取り消しが進行中です...``
* ``ベア・メタル・サーバーの取り消しが完了しました。``
* ``ESXi サーバーを vCenter Server インスタンスから削除しています... (Removing ESXi servers from the vCenter Server instance...)``
* ``ESXi サーバーを削除しています。(Removing the ESXi server.)``
* ``<server_id> の ESXi サーバーを削除しています。(Removing the <server_id> ESXi server.)``
* ``選択された ESXi サーバーを vCenter Server から削除しています... (Removing selected ESXi servers from vCenter Server...)``
* ``ESXi サーバーを取り消しています... (Cancelling the ESXi servers...)``
* ``選択された ESXi サーバーを取り消しています... (Cancelling the selected ESXi servers...)``

### IBM CloudBuilder の履歴メッセージ
{: #ibm_use-msgs-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} では、IBM CloudBuilder に関して、以下のメッセージが発行されます。

* ``IBM CloudBuilder 仮想サーバー・インスタンスの注文を確認しています... (Verifying the IBM CloudBuilder Virtual Server Instance order...)``
* ``IBM CloudBuilder 仮想サーバー・インスタンスの注文を開始しています... (Starting the order for the IBM CloudBuilder Virtual Server Instance...)``
* ``IBM CloudBuilder 仮想サーバー・インスタンスの準備が完了しました。(The IBM CloudBuilder Virtual Server Instance is ready.)``
* ``IBM CloudBuilder はサービス準備完了。``
* ``IBM CloudBuilder 仮想サーバー・インスタンスを終了しています... (Dismissing the IBM CloudBuilder Virtual Server Instance...)``

### ストレージの履歴メッセージ
{: #ibm_use-msgs-storage}

{{site.data.keyword.vmwaresolutions_short}} では、ストレージの設定に関して、以下のメッセージが発行されます。

* ``vSAN ライセンスを注文しています... (Ordering the vSAN license...)``
* ``vSAN ライセンスを取り消しています... (Cancelling the vSAN license...)``
* ``VSAN ライセンスの取り消しが完了しました。(The VSAN license cancellation is complete.)``
* ``<cluster_name> クラスター用に <quantity> 台の NFS ストレージを注文しています。(Ordering <quantity> NFS storage(s) for the <cluster_name> cluster.)``
* ``新規 NFS ストレージが追加されて使用準備が整いました。``
* ``管理 NFS 共有ストレージを取り消しています... (Cancelling Management NFS share storage...)``
* ``選択された NFS ストレージが削除されました。``
* ``エンデュランス・ストレージの注文を開始しています... (Starting the order for Endurance Storage...)``
* ``エンデュランス・ストレージを取り消しています... (Cancelling Endurance Storage...)``

### ネットワークの履歴メッセージ
{: #ibm_use-msgs-network}

{{site.data.keyword.vmwaresolutions_short}} では、ネットワークの設定に関して、以下のメッセージが発行されます。

* ``パブリック VLAN の注文を開始しています... (Starting the public VLAN order...)``
* ``VLAN 構成が正常に完了しました。(Successfully completed the VLAN configuration.)``
* ``追加のプライベート VLAN を注文しています... (Ordering additional private VLAN...)``
* ``追加のプライベート VLAN がプロビジョンされました。``
* ``追加のプライベート VLAN 仮想サーバー・インスタンスがプロビジョンされました。(An additional private VLAN Virtual Server Instance is provisioned.)``
* ``追加のプライベート VLAN をベア・メタル・サーバーにトランクしています... (Trunking additional private VLAN to Bare Metal Servers...)``
* ``追加のプライベート VLAN をベア・メタル・サーバーに正常にトランクしました。``
* ``追加のプライベート VLAN 仮想サーバー・インスタンスを取り消しています... (Cancelling the additional private VLAN Virtual Server Instance...)``
* ``VLAN を取り消しています... (Cancelling VLANs...)``
* ``VLAN の取り消しが進行中です...``
* ``VLAN の取り消しが完了しました。``
* ``2 ソケット <type> NSX ライセンスを注文しています... (Ordering a two socket <type> NSX license...)``
* ``新規クラスターの NSX 構成が完了しました。(NSX configuration for the new cluster is complete.)``
* ``2 ソケット NSX ライセンスを取り消しています... (Cancelling  the two socket NSX license...)``
* ``NSX ライセンスが正常に取り消されました。(The NSX license has been successfully cancelled.)``
* ``サブネットの注文を開始しています... (Starting the order for subnets...)``
* ``サブネットの準備が完了しました。(The subnet is ready.)``
* ``ポータブル・プライベート・サブネットの準備が完了しました。(The portable private subnet is ready.)``
* ``NFS ストレージに新規サブネット・アクセスを付与しています... (Granting new subnet access to NFS storage...)``
* ``サブネットを取り消しています...``
* ``サブネットの取り消しが進行中です...``
* ``カスタマー・ポータブル・プライベート・サブネットを取り消しています... (Cancelling the customer portable private subnet...)``
* ``カスタマー・ポータブル・パブリック・サブネットを取り消しています... (Canceling the customer portable public subnet...)``
* ``エンデュランス・ストレージのプライベート・サブネットを取り消しています... (Cancelling the Endurance Storage private subnet...)``
* ``ポータブル・パブリック・サブネットを取り消しています... (Cancelling the portable public subnet...)``
* ``ポータブル・パブリック・サブネットの準備が完了しました。(The portable public subnet is ready.)``
* ``ポータブル・パブリック・サブネットの注文を開始しています... (Starting the portable public subnet order...)``
* ``サブネットの取り消しが完了しました。(Subnet cancellation is complete.)``
* ``ネットワーク・ストレージを取り消しています... (Cancelling network storage...)``

### サービスの履歴メッセージ
{: #ibm_use-msgs-services}

{{site.data.keyword.vmwaresolutions_short}} では、サービスに関して、以下のメッセージが発行されます。

* ``管理サービスのセットアップを開始しています... (Starting the management services setup...)``
* ``サービス・エントリーを注文しています... (Ordering service entries...)``
* ``サービス・エントリーの注文が完了しました。(Completed the order for service entries.）``
* ``IBM オペレーション・サービスが稼働しています。(IBM operation services are running.)``
* ``デフォルト・サービスを有効にしています... (Enabling the default services...)``
* ``デフォルト・サービスが正常に有効化されました。(The default services are successfully enabled.)``
* ``サービス・エントリーの取り消しが進行中です...``
* ``サービス・エントリーの取り消しが完了しました。``

### vCenter Server with Hybridity Bundle の履歴メッセージ
{: #ibm_use-msgs-hybridity}

{{site.data.keyword.vmwaresolutions_short}} では、vCenter Server with Hybridity Bundle インスタンスに関して、以下のメッセージが発行されます。

* ``vCenter Server with Hybridity Bundle ライセンスを注文しています... (Ordering vCenter Server with Hybridity Bundle licenses...)``
* ``vCenter Server with Hybridity Bundle 変換を開始しています... (Starting the vCenter Server with Hybridity Bundle conversion...)``
* ``vCenter Server with Hybridity Bundle 変換が完了しました。(The vCenter Server with Hybridity Bundle conversion is complete.)``
* ``vCenter Server with Hybridity Bundle を削除しています... (Removing the vCenter Server with Hybridity Bundle...)``
* ``vCenter Server with Hybridity Bundle が正常に削除されました。(The vCenter Server with Hybridity Bundle is successfully removed.)``
* ``vCenter Server with Hybridity Bundle 変換を取り消しています... (Cancelling the vCenter Server with Hybridity Bundle conversion...)``

### Cloud Foundation の履歴メッセージ
{: #ibm_use-msgs-cf}

{{site.data.keyword.vmwaresolutions_short}} では、Cloud Foundation インスタンスに関して、以下のメッセージが発行されます。

* ``Cloud Foundation インスタンスの注文を開始しています... (Starting the Cloud Foundation instance order...)``
* ``Cloud Foundation の注文を受け付けました。(The Cloud Foundation order has been received.)``
* ``Cloud Foundation の注文を処理しています... (Processing the Cloud Foundation order...)``
* ``Cloud Foundation 構成に使用する仮想サーバーを注文しています... (Ordering a virtual server to use for the Cloud Foundation configuration...)``
* ``Cloud Foundation 構成に使用する仮想サーバーの注文が完了しました。(Completed the order of the virtual server to use for the Cloud Foundation configuration.)``
* ``Cloud Foundation 構成に使用する仮想サーバーの注文を確認しました。(Verified the order of the virtual server to use for the Cloud Foundation configuration.)``
* ``Cloud Foundation 構成に使用するベア・メタル・サーバーを注文しています... (Ordering Bare Metal Servers to use for the Cloud Foundation configuration...)``
* ``Cloud Foundation 構成に使用するベア・メタル・サーバーの注文が完了しました。(Completed the order of Bare Metal Servers to use for the Cloud Foundation configuration.)``
* ``Cloud Foundation ネットワーキングを構成しています...``
* ``Cloud Foundation ネットワーキングの構成が完了しました。(Completed the configuration of Cloud Foundation networking.)``
* ``Cloud Foundation サブネットを注文しています... (Ordering Cloud Foundation subnets...)``
* ``Cloud Foundation サブネットの注文が完了しました。(Completed order of the Cloud Foundation subnets.)``
* ``Cloud Foundation インスタンスを構成しています... (Configuring the Cloud Foundation instance...)``
* ``Cloud Foundation インスタンス・コンポーネントをカスタマイズおよび最適化しています... (Customizing and optimizing the Cloud Foundation instance components...)``
* ``Cloud Foundation のクリーンアップが進行中です... (The Cloud Foundation cleanup in progress...)``
* ``Cloud Foundation のクリーンアップが完了しました。(The Cloud Foundation cleanup is complete.)``
* ``Cloud Foundation インスタンスは使用可能です。``
* ``Cloud Foundation インスタンスをカスタマイズおよび最適化しています... (Customizing and optimizing the Cloud Foundation instance...)``
* ``Cloud Foundation インスタンスの構成が完了しました。``
* ``Cloud Foundation インスタンスのカスタマイズおよび最適化が完了しました。``
* ``Cloud Foundation コンポーネントの注文が完了しました。(The Cloud Foundation components order is complete.)``
* ``Cloud Foundation インスタンスの削除が完了しました。(The Cloud Foundation instance deletion is complete.)``
* ``Cloud Foundation インスタンスの削除が完了しました。(Deletion of the Cloud Foundation instance is complete.)``

### エラー・メッセージ
{: #ibm_use-msgs-error}

{{site.data.keyword.vmwaresolutions_short}} では、以下のインスタンス履歴エラー・メッセージが発行されます。

* ``Cloud Foundation 構成用の仮想サーバーの注文にエラーがありました。(Error ordering a Virtual Server used for the Cloud Foundation configuration.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``エラー: Cloud Foundation 構成に使用する仮想サーバーを SoftLayer でプロビジョニングできませんでした。(Error: SoftLayer failed to provision a virtual server to use for the Cloud Foundation configuration.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation 構成用のベア・メタル・サーバーの注文にエラーがありました。(Error ordering Bare Metal Servers used for the Cloud Foundation configuration.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation 構成用の VLAN の注文にエラーがありました。(Error ordering VLANs to use for the Cloud Foundation configuration.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation ネットワーキングの構成にエラーがありました。支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation サブネットの注文にエラーがありました。(Error ordering Cloud Foundation subnets.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation インスタンスの管理サービスの作成にエラーがありました。支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``VMware ライセンスの注文にエラーがありました。(Error ordering VMware licenses.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``サブネットの注文にエラーがありました。(Error ordering subnets.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation インスタンスの構成にエラーがありました。(Error configuring the Cloud Foundation instance.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``Cloud Foundation インスタンスのカスタマイズおよび最適化にエラーがありました。(Error customizing and optimizing the Cloud Foundation instance.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``エラー: SoftLayer API 鍵が無効です。支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``エラー: SoftLayer データ・センターが無効です。支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``指定された SoftLayer アカウントでの共有イメージの使用にエラーがありました。支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``サービス・エントリーの注文にエラーがありました。(Error ordering service entries.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``サブネットの注文にエラーがありました。(Error ordering subnets.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``ライセンスの注文にエラーがありました。(Error ordering licenses.) 支援が必要な場合は、サービス・チケットをオープンしてください。``
* ``サービスの注文にエラーがありました。(Error ordering services.) 支援が必要な場合は、サービス・チケットをオープンしてください。``


## 関連リンク
{: #ibm_use-related}

* [vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker イベント](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

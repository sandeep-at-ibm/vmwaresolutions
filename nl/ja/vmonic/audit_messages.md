---

copyright:

  years: 2016, 2019

lastupdated: "2019-07-24"

keywords: history message, audit history, error messages

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# インスタンスの履歴メッセージ
{: #audit_messages}

VMware インスタンスに対して {{site.data.keyword.cloud}} が実行した操作はすべて、インスタンス履歴に記録されます。 お客様は、インスタンス履歴を参照情報として使用して、それらの操作を確認することができます。 インスタンス履歴の確認方法について詳しくは、[vCenter Server インスタンスのデプロイメント履歴を表示する手順](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_viewinginstances#vc_viewinginstances-procedure-view-deploy-history)を参照してください。

ここでは、インスタンス履歴に対して発行される可能性があるすべてのメッセージを複数のセクションに分けて記載します。

## 一般的なインスタンスの履歴メッセージ
{: #audit_messages-general}

{{site.data.keyword.vmwaresolutions_short}} では、一般的な操作に関して以下のメッセージが発行されます。

* ``インスタンス・ユーザーおよび必要なサービスの作成を開始しています... (Starting to create the instance user and required services...)``
* ``インスタンス・ユーザーおよび必要なサービスの作成が完了しました。(The instance user and required services creation is complete.)``
* ``vCenter Server ライセンスを注文しています... (Ordering the vCenter Server license...)``
* ``VMware ライセンスを注文しています... (Ordering VMware licenses...)``
* ``VMware ライセンスの注文が完了しました。(Completed the order for VMware licenses.)``
* ``<quantity> の追加料金を要求しています... (Ordering <quantity> upcharges...)``
* ``<environment> のインストールおよび構成を開始しています... (Starting the <environment> installation and configuration...)``
* ``<environment> のインストールおよび構成が完了しました。(The <environment> installation and configuration is complete.)``
* ``VMware コンポーネントを開始しています... (Starting VMware components...)``
* ``インスタンスのデプロイを開始しています... (Starting to deploy the instance...)``
* ``<instance_name> インスタンスを使用する準備ができました。(The <instance_name> instance is ready to use.)``
* ``<version> へのアップグレードを開始しています... (Starting upgrade to <version>...)``
* ``<version> へのアップグレードが完了しました。(The upgrade to <version> is complete.)``
* ``VMware コンポーネントのアップグレードが完了しました。(VMware component upgrade is complete.)``
* ``<instance_name> インスタンスの削除を開始しています... (Starting the <instance_name> instance deletion...)``
* ``<instance_name> インスタンスが正常に削除されました。(The <instance_name> instance is successfully deleted.)``
* ``インスタンスのセキュア・ワイプが完了しました。(The secure wipe of the instance is complete.)``
* ``vCenter ライセンスを取り消しています... (Cancelling the vCenter license...)``
* ``インスタンス・ユーザーおよび必要なサービスを取り消しています... (Cancelling the instance user and required services...)``
* ``<environment> の追加料金を取り消しています... (Cancelling <environment> upcharges...)``
* ``VMware ライセンスの取り消しが進行中... (VMware license cancellation in progress...)``
* ``VMware ライセンスの取り消しが完了しました。(VMware license cancellation is complete.)``
* ``{{site.data.keyword.cloud_notm}} インフラストラクチャーの注文が失敗したか、タイムアウトになりました。(The {{site.data.keyword.cloud_notm}} infrastructure order failed or timed out.)``

## インスタンスのエラー・メッセージ
{: #audit_messages-error}

{{site.data.keyword.vmwaresolutions_short}} では、以下のインスタンス履歴エラー・メッセージが発行されます。

* ``VMware ライセンスのご注文において、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``サブネットのご注文において、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``エラー: {{site.data.keyword.cloud_notm}} インフラストラクチャー API キーが無効です。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``エラー: {{site.data.keyword.cloud_notm}} インフラストラクチャー・データ・センターが無効です。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``指定された {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントで共有イメージを使用しているときに、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``サービス・エントリーのご注文において、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``サブネットのご注文において、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``ライセンスのご注文において、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``
* ``サービスのご注文において、エラーがありました。 アシスタンスが必要であれば、サービス・チケットをオープンしてください。``

## クラスターの履歴メッセージ
{: #audit_messages-cluster}

{{site.data.keyword.vmwaresolutions_short}} では、vCenter Server クラスターに関して以下のメッセージが発行されます。

* ``クラスター構成を開始しています... (Starting the cluster configuration...)``
* ``<cluster_name> のクラスター構成を開始しています... (Starting the cluster configuration for <cluster_name>...)``
* ``クラスター構成が完了しました。(The cluster configuration is complete.)``
* ``<cluster_name> クラスターを使用する準備ができました。(The <cluster_name> cluster is ready to use.)``
* ``新規クラスターを vCenter に追加しています... (Adding the new cluster into vCenter...)``
* ``新規クラスターが vCenter に追加されました。(The new cluster is added to vCenter.)``
* ``<cluster_name> のクラスター削除を開始しています... (Starting the cluster deletion for <cluster_name>...)``
* ``<cluster_name> クラスターを vCenter から削除しています... (Deleting the <cluster_name> cluster from vCenter...)``
* ``<cluster_name> クラスターが vCenter から削除されました。(The <cluster_name> cluster is deleted from vCenter.)``
* ``<cluster_name> クラスターが削除されました。(The <cluster_name> cluster is deleted.)``

## ESXi サーバーの履歴メッセージ
{: #audit_messages-esxi}

{{site.data.keyword.vmwaresolutions_short}} では、ESXi サーバーに関して以下のメッセージが発行されます。

* ``<quantity> 台の ESXi サーバーの注文を開始しています... (Starting the order for <quantity> ESXi servers...)``
* ``ESXi サーバーの注文を検証しています... (Verifying the ESXi server order...)``
* ``プライベート IP アドレスが <ip_addresses> の ESXi サーバーの準備ができました。(The ESXi servers with the <ip_addresses> Private IP address are ready.)``
* ``すべての ESXi サーバーが再利用されました。(All ESXi servers are reclaimed.)``
* ``ESXi サーバーを vCenter Server インスタンスに追加しています... (Adding ESXi servers to the vCenter Server instance...)``
* ``ESXi サーバーが正常に更新されました。(The ESXi servers are successfully updated.)``
* ``クラスター用に ESXi サーバーの注文を開始しています... (Starting to order ESXi servers for cluster...)``
* ``<Cluster Name> クラスター用に <quantity> 台の ESXi サーバーの注文を開始しています... (Starting to order <quantity> ESXi servers for the <Cluster Name> cluster...)``
* ``クラスターの ESXi サーバーの準備ができました。(The ESXi servers for the cluster are ready.)``
* ``クラスター用にプライベート IP アドレスが <ip_addresses> の ESXi サーバーの準備ができました。(ESXi servers with the <ip_addresses> Private IP address are ready for the cluster.)``
* ``ESXi サーバーの準備ができました。(The ESXi server is ready.)``
* ``ESXi サーバーの構成が完了しました。(The ESXi server configuration is complete.)``
* ``指定されたプロパティーで ESXi サーバーが正常に追加されました。(The ESXi server is successfully added with the property.)``
* ``ESXi サーバーを追加する要求がすべて正常に完了しました。(All requests for adding ESXi servers are successfully completed.)``
* ``ESXi サーバーを追加しています... (Adding the ESXi server...)``
* ``ESXi サーバーのベアメタル・サーバーを注文しています... (Ordering a Bare Metal Server for the ESXi server...)``
* ``新規 ESXi サーバーが vCenter に追加されました。(New ESXi servers are added to vCenter.)``
* ``新規 ESXi サーバーへのサービスの追加を開始しています... (Starting to add services to the new ESXi servers...)``
* ``選択された ESXi サーバーが正常に取り消されました。(The selected ESXi servers are successfully cancelled.)``
* ``新規 ESXi サーバーがプロビジョンされました。(New ESXi servers are provisioned.)``
* ``新規 ESXi サーバーの検証と準備が完了しました。(New ESXi servers are verified and ready.)``
* ``<cluster_name> クラスター用に <quantity> 個の新規 ESXi サーバーの注文を開始しています... (Starting to order <quantity> new ESXi servers for the <cluster_name> cluster...)``
* ``選択された ESXi サーバーが vCenter Server から削除されました。(The selected ESXi servers are removed from vCenter Server.)``
* ``ESXi サーバーを削除するためにサービスの削除を開始しています... (Starting to remove services to remove ESXi servers...)``
* ``<cluster_name> クラスターの ESXi サーバーを検証しています... (Verifying ESXi servers for the <cluster_name> cluster...)``
* ``新規クラスターの ESXi サーバーが検証を正常にパスしました。(The new cluster ESXi servers successfully passed verification.)``
* ``新規 ESXi サーバーの注文を検証しています... (Verifying new ESXi server order...)``
* ``ESXi サーバーの注文の検証に失敗しました。(The verification of the ESXi servers order failed.)``
* ``ESXi サーバーのバッチ追加要求を分割。``
* ``ESXi サーバーを削除する要求のすべてが正常に完了しました。``
* ``ホストが正常に追加されました。(The host is successfully added.)``
* ``ホストが正常に削除されました。(The host(s) are successfully removed.)``
* ``ベア・メタル・サーバーの取り消しが進行中です...``
* ``ベア・メタル・サーバーの取り消しが完了しました。(Bare Metal Server cancellation is complete.)``
* ``ESXi サーバーを vCenter Server インスタンスから削除しています... (Removing ESXi servers from the vCenter Server instance...)``
* ``ESXi サーバーを削除しています。(Removing the ESXi server.)``
* ``<server_id> ESXi サーバーを削除しています。(Removing the <server_id> ESXi server.)``
* ``選択された ESXi サーバーを vCenter Server から削除...``
* ``ESXi サーバーを取り消しています... (Cancelling the ESXi servers...)``
* ``選択された ESXi サーバーを取り消しています... (Cancelling the selected ESXi servers...)``

## ネットワーキングの履歴メッセージ
{: #audit_messages-network}

{{site.data.keyword.vmwaresolutions_short}} では、ネットワーク設定に関して以下のメッセージが発行されます。

* ``パブリック VLAN の注文を開始しています... (Starting the public VLAN order...)``
* ``VLAN の構成が正常に完了しました。(Successfully completed the VLAN configuration.)``
* ``追加のプライベート VLAN のご注文...``
* ``追加のプライベート VLAN がプロビジョニングされました。``
* ``追加のプライベート VLAN 仮想サーバー・インスタンスがプロビジョンされました。(An additional private VLAN Virtual Server Instance is provisioned.)``
* ``追加のプライベート VLAN をベア・メタル・サーバーにトランク...``
* ``追加のプライベート VLAN をベア・メタル・サーバーに正常にトランクしました。``
* ``追加のプライベート VLAN 仮想サーバー・インスタンスを取り消しています... (Cancelling the additional private VLAN Virtual Server Instance...)``
* ``VLAN を取り消しています... (Cancelling VLANs...)``
* ``VLAN の取り消しが進行中です...``
* ``VLAN の取り消しが完了しました。(VLAN cancellation is complete.)``
* ``2 ソケットの <type> NSX ライセンスを注文しています... (Ordering a two socket <type> NSX license...)``
* ``新規クラスターの NSX 構成が完了しました。(NSX configuration for the new cluster is complete.)``
* ``2 ソケット NSX ライセンスを取り消しています... (Cancelling  the two socket NSX license...)``
* ``NSX ライセンスが正常に取り消されました。(The NSX license has been successfully cancelled.)``
* ``サブネットの注文を開始しています... (Starting the order for subnets...)``
* ``サブネットの準備ができました。(The subnet is ready.)``
* ``ポータブル・プライベート・サブネットの準備ができました。(The portable private subnet is ready.)``
* ``NFS ストレージへの新規サブネット・アクセスの付与中... (Granting new subnet access to NFS storage...)``
* ``サブネットを取り消しています...``
* ``サブネットの取り消しが進行中です...``
* ``カスタマー・ポータブル・プライベート・サブネットの取り消し...``
* ``カスタマー・ポータブル・パブリック・サブネットの取り消し...``
* ``エンデュランス・ストレージ・プライベート・サブネットの取り消し...``
* ``ポータブル・パブリック・サブネットの取り消し...``
* ``ポータブル・パブリック・サブネットは作動可能。``
* ``ポータブル・パブリック・サブネットの注文を開始しています... (Starting the portable public subnet order...)``
* ``サブネットの取り消しが完了しました。(Subnet cancellation is complete.)``
* ``ネットワーク・ストレージを取り消しています... (Cancelling network storage...)``

## 仮想サーバー・インスタンスの履歴メッセージ
{: #audit_messages-vsi}

{{site.data.keyword.vmwaresolutions_short}} では、仮想サーバー・インスタンス (VSI) に関して以下のメッセージが発行されます。

* ``IBM CloudDriver の新規仮想サーバー・インスタンスを注文しています... (Ordering a new virtual server instance for the IBM CloudDriver...)``
* ``<ip_address> の IBM CloudDriver 仮想サーバー・インスタンスがプロビジョンされました。(The <ip_address> IBM CloudDriver virtual server instance is provisioned.)``
* ``<ip_address> の IBM CloudDriver 仮想サーバー・インスタンスを取り消しています... (Cancelling the <ip_address> IBM CloudDriver virtual server instance...)``
* ``Microsoft Active Directory/DNS の Microsoft Windows 仮想サーバー・インスタンスの注文を開始しています... (Starting the order for the Microsoft Windows virtual server instance for Microsoft Active Directory/DNS...)``
* ``Active Directory/DNS の Microsoft Windows 仮想サーバー・インスタンスの注文を検証しています... (Verifying the Microsoft Windows virtual server instance order for Active Directory/DNS...)``
* ``Active Directory/DNS の Microsoft Windows 仮想サーバー・インスタンスの準備ができました。(The Microsoft Windows virtual server instance for Active Directory/DNS is ready.)``
* ``仮想サーバー・インスタンスの取り消しが進行中です... (Virtual server instance cancellation in progress...)``
* ``関連付けられた仮想サーバー・インスタンスを取り消しています... (Cancelling associated virtual server instances...)``
* ``仮想サーバー・インスタンスの取り消しが完了しました。(Virtual server instance cancellation is complete.)``

## IBM CloudBuilder の履歴メッセージ
{: #audit_messages-cloudbuilder}

{{site.data.keyword.vmwaresolutions_short}} では、IBM CloudBuilder に関して以下のメッセージが発行されます。

* ``IBM CloudBuilder 仮想サーバー・インスタンスの注文を検証しています... (Verifying the IBM CloudBuilder Virtual Server Instance order...)``
* ``IBM CloudBuilder 仮想サーバー・インスタンスの注文を開始しています... (Starting the order for the IBM CloudBuilder Virtual Server Instance...)``
* ``IBM CloudBuilder 仮想サーバー・インスタンスの準備ができました。(The IBM CloudBuilder Virtual Server Instance is ready.)``
* ``IBM CloudBuilder はサービス準備完了。``
* ``IBM CloudBuilder 仮想サーバー・インスタンスを終了しています... (Dismissing the IBM CloudBuilder Virtual Server Instance...)``

## IBM CloudDriver の履歴メッセージ
{: #audit_messages-clouddriver}

{{site.data.keyword.vmwaresolutions_short}} では、IBM CloudDriver に関して以下のメッセージが発行されます。

* ``IBM CloudDriver を準備しています... (Preparing the IBM CloudDriver...)``
* ``IBM CloudDriver の準備ができました。(The IBM CloudDriver is ready.)``
* ``<ip_address> の IBM CloudDriver を使用する準備ができました。(The <ip_address> IBM CloudDriver is ready to use.)``
* ``IBM CloudDriver の状況を検査しています... (Checking the IBM CloudDriver status...)``
* ``既存の <ip_address> の IBM CloudDriver を再使用しています... (Reusing the existing <ip_address> IBM CloudDriver...)``
* ``既存の IBM CloudDriver を (プロビジョニングで) 再使用しています... (Reusing the existing IBM CloudDriver (In Provisioning)...)``
* ``IBM CloudDriver を解放しています... (Releasing the IBM CloudDriver...)``
* ``<ip_address> の IBM CloudDriver を解放しています... (Releasing the <ip_address> IBM CloudDriver...)``
* ``IBM CloudDriver の削除を開始しています... (Starting the IBM CloudDriver deletion...)``
* ``IBM CloudDriver の削除が完了しました。(Completed the IBM CloudDriver deletion.)``

## ストレージの履歴メッセージ
{: #audit_messages-storage}

{{site.data.keyword.vmwaresolutions_short}} では、ストレージ設定に関して以下のメッセージが発行されます。

* ``vSAN ライセンスを注文しています... (Ordering the vSAN license...)``
* ``vSAN ライセンスを取り消しています... (Cancelling the vSAN license...)``
* ``VSAN ライセンスの取り消しが完了しました。(The VSAN license cancellation is complete.)``
* ``<cluster_name> クラスター用に <quantity> 台の NFS ストレージを注文しています。(Ordering <quantity> NFS storage(s) for the <cluster_name> cluster.)``
* ``新規 NFS ストレージが追加されて使用準備が整っています。``
* ``管理 NFS 共有ストレージの取り消し...``
* ``選択された NFS ストレージが削除されました。``
* ``エンデュランス・ストレージの注文を開始しています... (Starting the order for Endurance Storage...)``
* ``エンデュランス・ストレージの取り消し...``

## サービスの履歴メッセージ
{: #audit_messages-services}

{{site.data.keyword.vmwaresolutions_short}} は、サービスに関する以下のメッセージを発行します。

* ``管理サービスのセットアップを開始しています... (Starting the management services setup...)``
* ``サービス・エントリーのご注文...``
* ``サービス・エントリーの注文が完了しました。(Completed the order for service entries.)``
* ``IBM 操作サービスが稼働しています。(IBM operation services are running.)``
* ``デフォルト・サービスを有効にしています... (Enabling the default services...)``
* ``デフォルト・サービスが正常に有効化されました。(The default services are successfully enabled.)``
* ``サービス・エントリーの取り消しが進行中です...``
* ``サービス・エントリーの取り消しが完了しました。(Service entry cancellation is complete.)``

## 関連リンク
{: #audit_messages-related}

* [vCenter Server 成果物の変更に関する考慮事項](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact-automation-id)
* [Activity Tracker イベント](/docs/services/vmwaresolutions?topic=vmware-solutions-at-events#at-events)

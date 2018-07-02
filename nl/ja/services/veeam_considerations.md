---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud の概要

Veeam on {{site.data.keyword.cloud}} サービスは VMware ハイパーバイザーに直接、シームレスに統合され、企業での高可用性の実現を支援します。 このサービスを使用すると、アプリケーションとデータのリカバリー・ポイントと目標復旧時間を利用できます。 リカバリー・ポイントと目標復旧時間は、構成が完了してから 15 分以内に利用可能になります。 このサービスを使用することにより、ご使用のインフラストラクチャーに配置されたすべての仮想マシンのバックアップとリストアの両方を Veeam コンソールから直接制御できます。

**利用可否**: このサービスは、V1.8 以降のリリースでデプロイされたインスタンスでのみ利用可能です。

## Veeam on IBM Cloud のコンポーネント

以下のコンポーネントが注文され、Veeam on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。
* 1 次プライベート IP アドレスおよび 1 GbE インターフェースを備えた、1 つの Windows Server 2016 VSI
* サービスを注文したときに選択したサイズおよびパフォーマンスの、{{site.data.keyword.cloud_notm}} エンデュランス・ブロック・ストレージ

## Veeam on IBM Cloud をインストールする際の考慮事項

* このサービスは、以下の管理コンポーネントをバックアップします。
  - VMware vCenter Server
  - Platform Services Controller (PSC)
  - IBM CloudDriver
  - **Cloud Foundation インスタンスのみ**: VMware SDDC Manager
  - **HA AD/DNS を使用する vCenter Server インスタンスのみ**: AD/DNS サーバーの高可用性ペア

* ESXi サーバーの構成は、Veeam on {{site.data.keyword.cloud_notm}} サービスによってバックアップされません。

* デフォルトで、NSX Controller および NSX Edge の構成は、NSX Manager によって毎日バックアップされ、最大 14 個の回復ポイントが設定されます。 NSX 構成のフルリストアを利用するには、{{site.data.keyword.cloud_notm}} サポート・チケットを作成する必要があります。NSX 構成のバックアップは、{{site.data.keyword.vmwaresolutions_full}} 内部のストレージに保存されるためです。 NSX Manager を使用する NSX 構成のバックアップの管理について詳しくは、[VMware の技術情報](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html)を参照してください。
* Veeam サーバーとストレージのリポジトリーは、元のポッドおよびデータ・センターにあります。 そのため、リモート・クラスターのバックアップ操作のパフォーマンスが低下する可能性があります。

## Veeam on IBM Cloud を削除する際の考慮事項

Veeam on {{site.data.keyword.cloud_notm}} サービスを削除する前に、このサービスを削除するとすべてのバックアップ (管理 VM のバックアップを含む) が停止し、作成済みのバックアップがすべて削除されることに留意してください (削除操作は取り消しできません)。 その後に管理 VM が破損しても、リストアできません。

## 関連リンク

* [Veeam on {{site.data.keyword.cloud_notm}} の注文](veeam_ordering.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理](managingveeam.html)
* [Veeam on {{site.data.keyword.cloud_notm}} の管理対象サービスの要求](managing_veeam_services.html)
* [IBM サポートへのお問い合わせ](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam の Web サイト](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

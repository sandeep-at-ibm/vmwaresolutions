---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	メタデータの収集
{: #vum-metadata}

VUM は、変更可能な事前定義の自動プロセスを介して、アップグレード、パッチ、または拡張に関するメタデータをダウンロードします。 VUM は、構成可能な一定の間隔で、VMware またはサード・パーティーのソースにアクセスして、使用可能なアップグレード、パッチ、または拡張に関する最新のメタデータを収集します。 ただし、VMware のデフォルト設定は VMware vCenter Server on {{site.data.keyword.cloud}} インスタンスで使用でき、企業の要件に応じて変更できます。

VUM は、vSAN によって生成されたシステム管理ベースラインを表示します。 システム管理ベースラインによって定期的にコンテンツが自動的に更新されます。そのためには、VUM がインターネットに常時アクセスできる必要があります。 通常、vSAN システム・ベースラインは 24 時間ごとにリフレッシュされます。

システム管理ベースラインを使用して、推奨される重要なパッチ、ドライバー、更新、または vSAN でサポートされる最新の ESXi ホスト・バージョンに vSAN クラスターをアップグレードできます。

ほとんどの企業では、VUM の VMware デフォルト設定が適切であると見なされます。 以下の情報に、企業で別の設定を使用する場合にこれらの設定を変更する方法を示します。

##	ダウンロードのスケジュール
{: #vum-metadata-download-schedule}

更新は仮想アプライアンスのアップグレード、ホスト・パッチ、および拡張であり、デフォルトでは VUM によって更新が毎日ダウンロードされます。 ダウンロード・スケジュールを変更するには、vSphere Web Client にアクセスし、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**にナビゲートし、**「Download Schedule」**を選択し、**「Edit」**をクリックします。

##	通知チェックのスケジュール
{: #vum-metadata-notif-check-schedule}

通知は、パッチの再呼び出し、新しい修正、およびアラートに関する情報であり、デフォルトでは VUM によって 1 時間ごとに通知がダウンロードされます。 これを変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**にナビゲートして、**「Notification Check Schedule」**を選択して、**「Edit」**をクリックします。

##	仮想マシン設定
{: #vum-metadata-vm-settings}

仮想マシン (VM) 設定を変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**から**「VM Settings」**にナビゲートして、**「Edit」**をクリックします。

##	ホスト/クラスター設定
{: #vum-metadata-host-settings}

ホスト/クラスター設定を変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**から**「Host/Cluster Settings」**にナビゲートして、**「Edit」**をクリックします。

## 関連リンク
{: #vum-metadata-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)

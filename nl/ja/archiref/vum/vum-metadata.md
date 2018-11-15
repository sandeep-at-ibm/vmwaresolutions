---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

#	メタデータの収集

VUM は、変更可能な事前定義の自動プロセスを介して、アップグレード、パッチ、または拡張に関するメタデータをダウンロードします。 VUM は、構成可能な一定の間隔で、VMware またはサード・パーティーのソースにアクセスして、使用可能なアップグレード、パッチ、または拡張に関する最新のメタデータを収集します。 ただし、VMware のデフォルト設定は VCS インスタンスで使用でき、企業の要件に応じて変更できます。

VUM は、vSAN によって生成されたシステム管理ベースラインを表示します。 システム管理ベースラインによって定期的にコンテンツが自動的に更新されます。そのためには、VUM がインターネットに常時アクセスできる必要があります。 通常、vSAN システム・ベースラインは 24 時間ごとにリフレッシュされます。

システム管理ベースラインを使用して、推奨される重要なパッチ、ドライバー、更新、または vSAN でサポートされる最新の ESXi ホスト・バージョンに vSAN クラスターをアップグレードできます。

ほとんどの企業では、VUM の VMware デフォルト設定が適切であると見なされます。 以下に、企業で別の設定を使用する場合にこれらの設定を変更する方法を示します。

##	ダウンロードのスケジュール
更新は仮想アプライアンスのアップグレード、ホスト・パッチ、および拡張であり、デフォルトでは VUM によって更新が毎日ダウンロードされます。 これを変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**にナビゲートして、**「Download Schedule」**を選択して、**「Edit」**をクリックします。

##	通知チェックのスケジュール
通知は、パッチの再呼び出し、新しい修正、およびアラートに関する情報であり、デフォルトでは VUM によって 1 時間ごとに通知がダウンロードされます。 これを変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**にナビゲートして、**「Notification Check Schedule」**を選択して、**「Edit」**をクリックします。

##	VM 設定
VM 設定を変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**から**「VM Settings」**にナビゲートして、**「Edit」**をクリックします。

##	ホスト/クラスター設定
ホスト/クラスター設定を変更するには、vSphere Web Client にアクセスして、**「Home」**>**「Update Manager」**>**「Manage」**>**「Settings」**から**「Host/Cluster Settings」**にナビゲートして、**「Edit」**をクリックします。

### 関連リンク

* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (デモ)

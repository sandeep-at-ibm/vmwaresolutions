---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-14"

---

# コンポーネントのバックアップ

すべてのソフトウェア・コンポーネントの構成、管理、モニタリングに関する責任は、お客様側にあります。その中には、管理インフラストラクチャーとワークロードのバックアップと可用性も含まれます。

ソリューションの一部として、{{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} アドオン・サービスまたは Veeam on {{site.data.keyword.cloud_notm}} アドオン・サービスを必要に応じてデプロイできます。 Veeam と IBM Spectrum Protect Plus は、管理コンポーネントをバックアップするための要件を満たすことにつながります。

これらのアドオン・サービスは、{{site.data.keyword.cloud_notm}} エンデュランス・ストレージとともにデプロイされます。 これらのサービスにより、管理コンポーネントおよびワークロードをバックアップしやすくなります。[Spectrum Protect Plus アーキテクチャーの概要](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window}と [Veeam アーキテクチャーの概要](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window}は、デプロイメントの計画とサイジングに関するガイダンスとして役立ちます。 Veeam デプロイメントには、[マネージド・サービス](https://console.bluemix.net/infrastructure/vmware-solutions/console/gettingstarted/veeam/vcs/managed)も要求可能です。

必要なバックアップ戦略はソリューション・コンポーネントによって異なります。 イメージ・レベルのバックアップを使用して保護されるコンポーネントもあれば、構成とデータのファイル・ベースのバックアップを使用して保護されるコンポーネントもあります。

## ファイル・ベースのバックアップ用のファイル・サーバー

VMware vCenter Server、Platform Services Controller (PSC)、VMware NSX など、コンポーネントの中には、構成をファイル・サーバーにバックアップする必要があるものもあります。

これらのバックアップをホストするには、以下のステップに従って、ご使用のクラスターに Linux ファイル・サーバーをデプロイします。

1. {{site.data.keyword.cloud_notm}} インフラストラクチャーから、プライベート・ポータブル・サブネットを注文し、それをシステム・コンポーネントと同じ VLAN 上に配置します。これは、ホストの管理 IP アドレスが存在するプライベート VLAN です。
2. {{site.data.keyword.cloud_notm}} プライベート・ミラーから、[Ubuntu Server 18.04 LTS](http://mirrors.service.softlayer.com/ubuntu-releases/ubuntu-server/bionic/daily-live/current/){:new_window} などの VMware 管理データ・ストアに、オペレーティング・システム・イメージをアップロードします。
3. 既に注文したプライベート・ポータブル IP アドレスを使用して、この仮想マシン (VM) をクラスター内の管理ポート・グループにデプロイします。 AD/DNS サーバーを指すように VM を構成し、必要に応じてサブドメインの DNS に VM を追加しておいてください。
4. このサーバーのバックアップ・ユーザー ID として root 以外のユーザー ID を作成し、必要なすべてのサービスをファイル転送用に構成して開始しておきます。 例えば、FTP や SSH などです。
5. この VM が Veeam または IBM Spectrum Protect Plus 管理バックアップ・ジョブ (下記参照) に含まれているようにしてください。

## vCenter のファイル・ベースのバックアップ

VMware vCenter Server と PSC には、さまざまなプロトコルを使用して[データベースと構成をファイル・サーバーにエクスポートするためのアプライアンス管理用ユーザー・インターフェースと API](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window} が用意されています。 VMware は、直接 vCenter Server Appliance と PSC 上で[クーロン・ジョブとして定期的に実行する](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window}ようにこれを構成する方法の例が記述されています。この例を適応させて使用できます。

この手法を使用して、vCenter Server Appliance と PSC の両方を別々にバックアップする必要があります。 VMware が文書化した考慮事項と制限事項をよく理解し、それに基づいて計画を立ててください。 また、ファイル・サーバー上のファイル・バックアップの定期的ローテーションと有効期限の計画を立ててください。 VMware のバックアップ・ロケーションは空のフォルダーである必要があります。したがって、後続のバックアップ・ジョブのためにロケーションを空にしておくようにバックアップ・ローテーションや自動化の計画を立てる必要があります。

## NSX のファイル・ベースのバックアップ

障害が発生した場合にシステムをその動作状態にリストアするためには、すべての NSX コンポーネントを適切にバックアップしておくことが不可欠です。設計上、NSX マネージャーのバックアップ機能を使用して NSX バックアップを構成する必要があります。 この目的のために、ファイル・サーバーへの[バックアップを定期的に実行するように NSX マネージャーを構成する](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}ことができます。 ファイル・サーバーやそのデータが適切にバックアップされるようにし、古い NSX バックアップのローテーションが確実に行われるようにしてください。

## 管理仮想マシンのイメージ・ベースのバックアップ

インスタンスをデプロイし、IBM Spectrum Protect Plus サービスまたは Veeam バックアップ・サービスのいずれかをデプロイしたら、管理仮想マシンのためのバックアップ・ジョブを構成します。以下の VM を日次バックアップで少なくとも 7 日間バックアップすることを計画してください。

* VMware SDDC Manager (存在する場合)
* Active Directory サーバー (存在する場合)
* ファイル・バックアップ・サーバー (上記参照)

これらの仮想マシンをバックアップできるだけの Veeam ライセンスまたは IBM Spectrum Protect Plus ライセンスを割り振ることを計画し、VM 用として少なくとも 2 TB のバックアップ・ストレージを考慮に入れてください。

## アドオン・サービス

アドオン・ソリューション・コンポーネントをインスタンスにデプロイする場合は、以下のコンポーネントのバックアップも管理バックアップ戦略の一部として計画する必要があります。

* Zerto Virtual Replication: Zerto Virtual Manager (ZVM) システムは {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) としてデプロイされ、Veeam でも IBM Spectrum Protect Plus でもバックアップはサポートされません。 災害復旧戦略上、サイト・フェイルオーバーを行わずに ZVM をリカバリーする必要がある場合は、任意の Windows バックアップ・ソリューションを使用して ZVM のバックアップとリストアを行う必要があります。
* F5 BIG-IP: F5 は、[F5 構成のファイル・ベースのバックアップ](https://support.f5.com/csp/article/K13132){:new_window}を推奨しています。このバックアップの送信先をファイル・サーバーにすることができます。
* FortiGate Security Appliance または VM: Fortinet は、[FortiGate 構成のファイル・ベースのバックアップ](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}を推奨しています。このバックアップの送信先をファイル・サーバーにすることができます。
* HyTrust Cloud Control および Data Control: HyTrust は、HyTrust サーバー・アプライアンスのイメージ・ベースのバックアップとファイル・ベースのバックアップの両方をサポートしています。 詳しくは、HyTrust 管理ガイドを参照してください。
* VMware HCX: HCX アプライアンス管理インターフェースを使用することによって、vCenter Server Appliance に似た HCX マネージャー構成のファイル・ベースのバックアップを作成してダウンロードできます。

## 追加の考慮事項

AD/DNS サーバーを {{site.data.keyword.cloud_notm}} 仮想サーバー・インスタンス (VSI) としてデプロイすることを選択した場合は、Veeam または IBM Spectrum Protect Plus のいずれでバックアップすることもできません。 この場合は、バックアップとリストアの操作を行うための任意の Windows バックアップ・ソリューションを使用するか、VMware クラスター内の AD/DNS VM を使用してインスタンスをデプロイすることを計画します (Veeam または IBM Spectrum Protect Plus でバックアップ可能) 。

VMware vCenter 6.5u2 以降、VMware は、イメージ・ベースのバックアップを使用した vCenter Postgres データベースのバックアップをサポートするようになりました。データベース保全性を確保するために、バックアップ時間枠でデータベースの一時停止/再開統合スクリプトが使用されます。 VMware インスタンスを vCenter 6.5u2 にアップグレードする場合は、ファイル・ベースのバックアップを使用する代わりに Veeam または IBM Spectrum Protect Plus を使用して vCenter Server と PSC をバックアップすることを選択できます。 その場合は、Veeam または IBM Spectrum Protect Plus 静止機能を使用してデータベース保全性を確保する必要があります。

## バックアップからのリストア

管理バックアップをリストアする際の特別な考慮事項がいくつかあります。

* vCenter と PSC の場合、VMware には、新しい仮想アプライアンスをデプロイしてバックアップから構成をリストアできるインストーラーが用意されています。
* バックアップからアプライアンスをリストアする際に、インストーラーは、ユーザーが提供するバックアップ情報に基づいて、アプライアンスのタイプ (vCenter Server または PSC) を検出します。
* ホストのいずれかに直接デプロイすると、分散スイッチまたは分散ポート・グループにデプロイできないことがあります。 リカバリーされたアプライアンスをデプロイする目的で一時的な標準のスイッチとポート・グループを作成し、このスイッチに vmnic のいずれかを一時的に移行することで、VM がネットワーク接続できるようにしなければならない場合があります。デプロイメント後、VM を分散ポート・グループに移行し、vmnic を dvSwitch に返すことができます。
* NSX の場合は、バックアップから構成をリストアする前に、NSX Manager とコントローラーを再デプロイしなければならない場合があります。
* vCenter のバックアップとリストアに関する VMware の考慮事項と制限事項をよく理解しておいてください。

## サマリー

適切に計画すれば、VMware インスタンスはその管理コンポーネントを失うこともなく、正常にリカバリーできます。 管理インフラストラクチャーとワークロードの両方について、バックアップ・ジョブが成功していることとバックアップ・データが使用できることを定期的にモニターするようにしてください。またバックアップ計画とリストア計画も定期的に検証するようにしてください。

### 関連リンク

* [ソリューションの概要](solution_overview.html)
* [設計の概要](design_overview.html)
* [キャパシティーの拡張](solution_scaling.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware vSphere 6.5 から 6.7 への vCenter Server vSphere ソフトウェアのアップグレード
{: #vc_vsphere_upgrade}

vCenter Server on {{site.data.keyword.cloud}} オファリングは、vSphere、NSX、およびオプションの vSAN 製品を含む VMware vSphere SDDC スタックのデプロイメントを完全に自動化するソリューションです。vCenter Server は、VMware SDDC ベースのインフラストラクチャーのデプロイ、拡張、縮小という最も難しい部分を自動化するものですが、マネージド・サービスではありません。vCenter Server は、N-1 の範囲内の VMware SDDC ソフトウェア・バージョンの自動化機能をサポートするという方針を取っているので、{{site.data.keyword.vmwaresolutions_short}} の自動化機能を利用し続けるには、vCenter Server の既存のインスタンスをアップグレードする必要があります。

自動化サポートのために必要なレベルにない vCenter Server バージョンは VMware サポート・ポリシーに従って引き続きサポートされますが、{{site.data.keyword.vmwaresolutions_short}} の自動化機能はサポートされなくなります。vCenter Server インスタンスのライフサイクルを通じて、パッチ適用や VMware ソフトウェアのアップグレードを定期的に実施する必要があります。その一環として、VMware SDDC ソフトウェアを {{site.data.keyword.vmwaresolutions_short}} の自動化機能のサポート対象バージョンに適宜アップグレードする必要があります。

以下に、vCenter Server VMware vSphere 6.5 ベースのインスタンスを vCenter Server VMware vSphere 6.7 ベースのインスタンスに変換するために必要な手順を示します。この手順では、最新の 6.7 レベルの vSphere、NSX、および vSAN への初期アップグレードを実行できます。このアップグレードに続けて、vSphere 標準機能を使用して、仮想マシン (VM) のハードウェア・レベルとツールをアップグレードする必要がある場合があります。

vCenter Server は、「ローリング」アップグレードを行えるように設計されています。つまり、以下の手順を実行すれば、現在実行中の VM ワークロードを停止せずに実行し続けることができます。企業は、変更管理ポリシーを適用し、アップグレードおよび緊急時対応計画を作成して周知する必要があります。ただし、vCenter および NSX マネージャーなどの特定の管理機能のアップグレード処理中に、管理機能の一時停止、構成変更、VM の電源オフと再起動が発生する場合があります。
{:note}

## 始める前に
{: #vc_vsphere_upgrade-prereq}

アップグレードの推定所要時間は不明です。環境を完全にアップグレードするためには、保守時間枠が複数回必要になる場合があります。VMware は、アップグレード処理中にアップグレード後のレベルおよび前のレベルの SDDC ソフトウェアを実行することをサポートしています。ただし、vMotion などの一部の機能はこの処理中に制限される場合があります。

アップグレードを開始する前に、以下の要件を満たしてください。  
* vCenter Server 環境内の拡張機能またはスナップインのアップグレードは、お客様の責任で行ってください。アップグレードを計画する前に、以下の資料を確認してください。
  * [VMware vCenter Server 6.7 Update 1b リリース・ノート](https://docs.vmware.com/en/VMware-vSphere/6.7/rn/vsphere-vcenter-server-67u1b-release-notes.html){:new_window}
  * [About VMware ESXi Upgrade](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.esxi.upgrade.doc/GUID-65B5B313-3DBB-4490-82D2-A225446F4C99.html){:new_window}
* vCenter Server インスタンス内に vSphere Update Manager (VUM) をセットアップし、VMware vSphere から最新の更新をダウンロードします。詳しくは、[VMware Update Manager の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vum-intro#vum-intro)を参照してください。
*	{{site.data.keyword.vmwaresolutions_short}} チームのサポート・チケットを開き、アップグレードを実行することを通知します。アップグレードしたレベルのインスタンスが {{site.data.keyword.vmwaresolutions_short}} コンソールで登録されるまで、チケットは開いたままになります。
* {{site.data.keyword.vmwaresolutions_short}} コンソールで、アップグレードする vCenter Server インスタンスがプライマリーまたはセカンダリーとして別の vCenter Server インスタンスにリンクされているかどうかを確認します。リンクされているすべてのインスタンスの Platform Services Controller (PSC) を、特定のサイトのアップグレードの一部として、先にアップグレードする必要があります。
* vSAN ベースのインスタンスについて以下を確認します。
  * vSAN Health ツールが有効で、クリティカル・エラーが報告されていないことを確認します。クリティカル・エラーが存在する場合は、アップグレードのサポート・チケット ID を使用して IBM サポート・チームに連絡してください。
  * アップグレード中に ESXi ホストが起動しなくなった場合に vSAN オブジェクトを追加で構築できるように、余分なスペースが各ノードにあることを確認します。アップグレードの前に、ディスク使用量を減らすか、ESXi ホストを追加する必要がある場合があります。
  
  * vSAN ボリューム全体の使用率が 70 パーセントを超えていないか確認します。アップグレードの前に、ディスク使用量を減らすか、ESXi ホストを追加する必要がある場合があります。
* {{site.data.keyword.vmwaresolutions_short}} V2.5 以降に取得した vCenter Server インスタンスの場合は、**customerroot** アクセス権を持つサービス・アカウントしかポータルに表示されないので、PSC と vCenter の両方の **root** ユーザー ID のパスワードを IBM サポートに問い合わせる必要があります。PSC および vCenter の **root** ユーザー ID とパスワードが表示されている場合は、この手順は不要です。
* 必要なアップグレード・バイナリーをダウンロードするための https://my.vmware.com のユーザー ID を持っていることを確認します。持っていない場合は、アップグレードのサポート・チケット ID で IBM サポートにお問い合わせください。
* パッチをダウンロードするために、https://www.vmware.com にアクセスできるように VUM が構成されていることを確認します。セキュリティー・ポリシーのために構成できない場合は、手動で最新のパッチ・セットをダウンロードして VUM にアップロードする必要があります。詳しくは、[VMware Update Manager の概要](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro)を参照してください。

### ジャンプボックスの準備
{: #vc_vsphere_upgrade-prereq-jumpbox}

{{site.data.keyword.cloud_notm}} のクライアント・アクセス VPN は 512 Kbps に制限されるので、同じ {{site.data.keyword.CloudDataCent_notm}}内の別の vSphere vCenter Server 環境に、{{site.data.keyword.cloud_notm}} Windows 2012 から 2016 までのサーバーの仮想サーバー・インスタンス (VSI) をプロビジョンするか、同様の Windows VM をセットアップすることをお勧めします。これを、アップグレードする vCenter Server インスタンスへのジャンプボックスとして使用して、https://my.vmware.com からバイナリーを簡単にダウンロードすることができます。この VM をアップグレード対象の vCenter Server インスタンス上に置くこともできますが、推奨されていません。

以下の手順を実行して VSI ジャンプボックスを注文します。

既に VSI ジャンプボックスが存在する環境の場合は、最初の手順はスキップしてください。
{:note}

1. 時間単位または月単位の VSI を [IBM Cloud インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com/)から注文します。以下の属性を注文します。
  * Windows 2012 または 2016 Server Standard
  * CPU 2 個
  * メモリー 16 GB
  * ディスク 100 G
  * 1 Gbps のパブリックおよびプライベートのアップリンク
2. VSI がプロビジョンされたら、プライベート・リンクのすべての受信/発信とパブリック・リンクの発信のみを許可するように、コントロール・パネルで {{site.data.keyword.cloud_notm}} アクセス制御リスト (ACL) を構成します。この Windows VSI へのリモート・デスクトップ・プロトコル (RDP) セッションには、{{site.data.keyword.cloud_notm}} のクライアント・アクセス VPN を使用する必要があります。
3. Windows VSI に RDP 接続します。アップグレードする vCenter Server インスタンス内の Windows AD サーバーのみを指すように、プライベート・ネットワーク・アダプター上のドメイン・ネーム・システム (DNS) 設定を変更します。
4. Google Chrome ブラウザーをダウンロードしてインストールします。Mozilla Firefox は使用できますが、vCenter ユーザー・インターフェース内の VUM 画面を使用するときにキャッシュの問題が発生します。
5. 任意の SSH ターミナル・ソフトウェアをダウンロードします。例えば、Putty などです。
6. Google Chrome を使用して、アップグレードする vCenter Server インスタンスにアクセスします。**administrator@vsphere.local** を使用して、ユーザー・インターフェースを表示できることを確認します。  
7. 前のセクションに記載したように、vSphere 環境にエラーや問題がないか確認します。
8. SSH ターミナル・ソフトウェアで、ポータルまたはサポートで確認した **root** のパスワードを使用して PSC および vCenter にアクセスします。
9. オプションで、SL コントロール・パネルに表示されている **root** ユーザー ID とパスワードを使用して各 ESXi ホストにアクセスし、**root** パスワードを確認します。

#### バイナリーのダウンロード
{: #vc_vsphere_upgrade-prereq-jumpbox-binary}

Windows VSI ジャンプボックスを使用し、https://my.vmware.com アカウントにログインして以下のバイナリーをダウンロードします。

*	VMware vSphere 6.7u1 Hypervisor (ESXi ISO) イメージ (VMware Tools を含む)
* vCenter 6.7u1b アプライアンス ISO (更新バンドルではない)。
*	NSX for vSphere 6.4.4 アップグレード・バンドル

Intel Optane ドライブについては、次のファイルをダウンロードして、VMware Update Manager によるアップグレード後のパッチ適用処理で使用します。

https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX67-INTEL-INTEL-NVME-VMD-1401016&productId=742 で Intel® Optane™ SSD DC P4800X Series SSDPED1K750GA (750 GB、HHHL) 向け Intel NVMe ドライブ用の ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` ファイルを見つけます。

#### コンポーネントのバックアップ

アップグレードを開始する前に、各コンポーネントをバックアップします。

* vCenter Server および PSC のバックアップについて詳しくは、[Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window} を参照してください。
* vCenter Server および PSC のバックアップに関するその他の考慮事項や情報については、[vCenter のファイル・ベースのバックアップ](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup#solution_backingup-vcenter)を参照してください。
*	NSX のバックアップについては、[Backing Up NSX Manager Data](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window} を参照してください。

## IBM vCenter Server vSphere ソフトウェアの 6.5 から 6.7 へのアップグレード手順
{: #vc_vsphere_upgrade-procedure}

アップグレード処理中に問題が発生した場合は、処理の初めに開いた {{site.data.keyword.vmwaresolutions_short}} アップグレード・チケットを使用して、IBM サポートに連絡してください。IBM サポートが、必要に応じて VMware サポートのチケットを開きます。

{{site.data.keyword.vmwaresolutions_short}} が VMware サポートに vCenter Server の設計、セットアップ、{{site.data.keyword.cloud_notm}} に関する必要な情報をすべて提供できるように、このパスを使用する必要があります。このプロセスに従って VMware サポートと正確な情報を共有することで、サポートにかかる時間を短縮できます。IBM サポートが必要な情報を VMware サポートに提供した後に、お客様は必要に応じて VMware サポートと直接やり取りすることができます。
{:important}

### VMware NSX のアップグレード
{: #vc_vsphere_upgrade-procedure-nsx}

VMware NSX のアップグレード処理は、ESXi ホスト上の vSphere インストール・バンドルを更新して各ホストをリブートする必要があるので、時間がかかる場合があります。環境に応じて保守時間枠を計画してください。

#### VMware NSX をアップグレードする前に
{: #vc_vsphere_upgrade-procedure-nsx-before}

* Zerto for {{site.data.keyword.cloud_notm}} が環境にインストールされている場合は、Zerto ユーザー・インターフェースを使用して、各ホスト上の zVRA VM をシャットダウンしてください。Zerto ユーザー・インターフェースのサイト設定の「Policies」セクションで**「Allow Zerto to always enter hosts into maintenance mode during remediation」**を選択します。これを選択しないと、Zerto が zVRA を始動し、アップグレード対象の ESXi ホストの保守モードの開始を許可しないので、アップグレードの処理が進められません。
* VMware Tools がインストールされていない VM では、NSX ESXi ホスト・モジュールをインストールする前に、手動でシャットダウンするか、強制的に電源をオフにしてください。これらの VM が起動していると、ターゲットの ESXi ホストが保守モードを開始できません。

#### VMware NSX をアップグレードする手順
{: #vc_vsphere_upgrade-procedure-nsx-procedure}

以下の手順について詳しくは、[NSX アップグレード・ガイド](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}を参照してください。

1. NSX 6.4.4 のリリース・ノートを読み、お客様固有の環境構成に適合することを確認します。詳しくは、[VMware NSX Data Center for vSphere 6.4.4 リリース・ノート](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}を参照してください。
2. まず、NSX マネージャーをアップグレードします。クロス vCenter リンク・モードを使用する複数の NSX 環境がある場合は、NSX ユーザー・インターフェース **Upgrade Coordinator** でコンポーネントをアップグレードする前に、すべての NSX マネージャーをアップグレードします。
3.	vCenter ユーザー・インターフェース内の NSX ユーザー・インターフェースにある **Upgrade Coordinator** を使用して、NSX コンポーネントをアップグレードします。
4. すべてのコンポーネントがアップグレードされるまで、vCenter ユーザー・インターフェース内の NSX アップグレード・ユーザー・インターフェースの確認と監視を続けます。潜在的な問題が解決されてアップグレードが進められていきます。 

### Platform Services Controller のアップグレード
{: #vc_vsphere_upgrade-procedure-psc}

リンクされた vCenter Server インスタンスの場合は、vCenter Server のプライマリー・サイトおよびセカンダリー・サイトで、すべての PSC インスタンスをアップグレードする必要があります。リンクされた vCenter Server インスタンスは、プライマリー vCenter Server インスタンスをハブとするハブ・アンド・スポーク・トポロジーの PSC レプリケーションを行うので、まずはプライマリー vCenter Server インスタンスの PSC をアップグレードしてから、各セカンダリー・サイトの PSC をアップグレードすることをお勧めします。

#### Platform Services Controller をアップグレードする前に
{: #vc_vsphere_upgrade-procedure-psc-before}

* 次の手順で、vCenter および PSC の root パスワードを取得します。{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して、vCenter Server インスタンス・バージョンが V2.4 以前から V2.7 以降にアップグレードされているかどうかを確認します。
* {{site.data.keyword.vmwaresolutions_short}} コンソールには、PSC と vCenter の両方の root に 1 つのパスワードが表示されます。ただし、これは vCenter のみのパスワードです。PSC の root パスワードはサポートに確認する必要があります。
* 競合を避けるために、vCenter と PSC が現在使用している同じサブネットの上部の IP を使用します。新規アプライアンスのデプロイメントには、一時 IP を使用する必要があります。

#### Platform Services Controller をアップグレードする手順
{: #vc_vsphere_upgrade-procedure-psc-procedure}

1. PSC (``https://<psc-fqdn>:5480``) と vCenter 両方のアプライアンス管理ユーザー・インターフェースにログインし、root パスワードの有効期限が切れていないかどうかを確認します。パスワードの有効期限日が **1970** である場合は、有効期限が切れているので、PSC アプライアンス管理ユーザー・インターフェースで SSH と Bash シェルを有効にする必要があります。
    1. root ID とパスワードを使用して SSH で PSC に接続します。パスワードの有効期限が切れていても、ログインできます。
    2. シェル **passwd** コマンドを使用して、PSC と vCenter の両方に新しい root パスワードを設定します。
    3. {{site.data.keyword.vmwaresolutions_short}} コンソールに表示されたパスワード、または IBM サポートから提供されたパスワードを保存します。後でアプライアンスをアップグレードするときに、これらのパスワードをもう一度使用します。
2. 標準の Windows ISO マウント機能を使用して、vCenter 6.7u1b ISO をジャンプボックス内にマウントします。
3. まずは、VMware の手順に従い、すべての PSC をアップグレードします。詳しくは、[Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html) を参照してください。

「**アップグレードするアプライアンスと同じネットワーク内にある Windows、Linux、または Mac マシンから GUI アップグレードを実行する必要がある**」という要件は、お客様のアカウントの {{site.data.keyword.cloud_notm}} 内のすべてのサブネットに適用されます。
{:note}

アップグレードのソースとターゲットとして vCenter を使用することが推奨されています。

### vCenter のアップグレード
{: #vc_vsphere_upgrade-procedure-vcenter}

リンクされた vCenter Server インスタンスの場合は、vCenter Server のプライマリーとセカンダリーの両方のサイトのすべての vCenter インスタンスをアップグレードすることが推奨されていますが、必須ではありません。

#### vCenter をアップグレードする前に
{: #vc_vsphere_upgrade-procedure-vcenter-before}

* 次の手順で、vCenter および PSC の root パスワードを取得します。{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して、vCenter Server インスタンス・バージョンが V2.4 以前から V2.7 以降にアップグレードされているかどうかを確認します。
* 競合を避けるために、vCenter と PSC が現在使用している同じサブネットの上部の IP を使用します。新規アプライアンスのデプロイメントには、一時 IP を使用する必要があります。

#### vCenter をアップグレードする手順
{: #vc_vsphere_upgrade-procedure-vcenter-procedure}

1. PSC (``https://<psc-fqdn>:5480``) と vCenter 両方のアプライアンス管理ユーザー・インターフェースにログインし、root パスワードの有効期限が切れていないかどうかを確認します。パスワードの有効期限日が **1970** である場合は、有効期限が切れているので、PSC アプライアンス管理ユーザー・インターフェースで SSH と Bash シェルを有効にする必要があります。
    1. root ID とパスワードを使用して SSH で PSC に接続します。パスワードの有効期限が切れていても、ログインできます。
    2. シェル **passwd** コマンドを使用して、PSC と vCenter の両方に新しい root パスワードを設定します。
    3. {{site.data.keyword.vmwaresolutions_short}} コンソールに表示されたパスワード、または IBM サポートから提供されたパスワードを保存します。後でアプライアンスをアップグレードするときに、これらのパスワードをもう一度使用します。
2. 標準の Windows ISO マウント機能を使用して、vCenter 6.7u1b ISO をジャンプボックス内にマウントします。
3. まずは、VMware の手順に従い、すべての PSC をアップグレードします。詳しくは、[Upgrade a vCenter Server Appliance 6.0 or 6.5 with an External vCenter Single Sign-On or Platform Services Controller Instance by Using the GUI](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-37BB88CC-7A44-4EC9-8D7B-5D182E471654.html) を参照してください。

「**アップグレードするアプライアンスと同じネットワーク内にある Windows、Linux、または Mac マシンから GUI アップグレードを実行する必要がある**」という要件は、お客様のアカウントの {{site.data.keyword.cloud_notm}} 内のすべてのサブネットに適用されます。
{:note}

アップグレードのソースとターゲットとして vCenter を使用することが推奨されています。

#### PSC 機能の vCenter への統合

1. PSC と vCenter のアップグレードが正常に完了したら、vCenter FLEX ベースのユーザー・インターフェースにログインし、**「System Configuration」**セクションで vCenter と PSC に関連するすべてのサービスの正常性を確認します。  
2. PSC をバックアップします。
3. ``<VCSA 6.7 iso mount>:&#xa5;vcsa-converge-cli&#xa5;templates&#xa5;converge`` ディレクトリーに移動します。
4. ``converge.json`` ファイルをジャンプ VM のローカル・ドライブにコピーします。
5. ``<VCSA 6.7 iso mount>:&#xa5;vcsa-converge-cli&#xa5;templates&#xa5;decommission`` ディレクトリーに移動します。
  * 最初の PSC を統合するときには、``json`` ファイルの**「replication」**セクションを削除します。
  * 2 つ目以降のリンク PSC のときには、``json`` ファイルの**「replication」**セクションに必要な属性を入力します。
6. ``decommission_psc.json`` ファイルをジャンプ VM のローカル・ドライブにコピーします。
7. ``converge.json`` と ``decommission_psc.json`` ファイルを編集します。編集するフィールドについての説明が、``json`` ファイル内に記載されています。**「managing_esxi_or_vc」**セクションでは、vCenter ではなく、PSC が含まれている ESXi ホストを使用することが推奨されています。
8. コマンド・ウィンドウで ``<VCSA 6.7 iso mount>:&#xa5;vcsa-converge-cli&#xa5;win32`` ディレクトリーにナビゲートします。
9. **converge** スイッチと先ほど編集した ``converge.json`` ファイルのパスを指定して ``vcsa-util.exe`` を実行します (例: ``vcsa-util converge --no-ssl-certificate-verification c:&#xa5;temp&#xa5;converge.json -v``)。
  1. **Y** を入力し、PSC をバックアップしたことを確認して次に進みます。
  2. プロセスが完了したら、**Y** を入力して vCenter のリブートを確認します。
10. vCenter のリブートが完了したら、vCenter ユーザー・インターフェースにログインして正常に動作することを確認します。
11. コマンド・ウィンドウで ``<VCSA 6.7 iso mount>:&#xa5;vcsa-converge-cli&#xa5;win32`` ディレクトリーにナビゲートします。
12. **decommission** スイッチと先ほど編集した **decommission_psc.json** ファイルのパスを指定して ``vcsa-util.exe`` を実行します (例: ``vcsa-util decommission --no-ssl-certificate-verification c:&#xa5;temp&#xa5;decommission_psc.json -v``)。
13.	コマンドが正常に完了したら、vCenter FLEX ユーザー・インターフェースにログインし、その vCenter アプライアンスのみが非リンク環境にリストされていること、また、すべてのサービスが正常であることを確認します。
14. 古い PSC、vCenter、および使用されていない統合 PSC VM を削除します。
15. vCenter ユーザー・インターフェースで vCenter Server の名前を **<instancename>_vc_separate** に変更します。例えば、vCenter Server のインスタンス名が「**production**」であれば、vCenter ユーザー・インターフェース名は「**production_vc_separate**」になります。これは、この vCenter Server インスタンスで自動化機能の実行を再開するために必要になります。  

### ESXi ホストのアップグレード
{: #vc_vsphere_upgrade-procedure-esxi}

ESXi ホストを 6.7u1 レベルにアップグレードしてパッチを適用するためには、vCenter 内の VMware Update Manager 機能を使用します。この資料の NSX アップグレードのセクションと同様に、別のホストへの vMotion やシャットダウンで問題が発生した VM があると、アップグレード・プロセスが停止する可能があります。
{:note}

#### ESXi ISO の VUM へのアップロード
{: #vc_vsphere_upgrade-procedure-esxi-iso}

1. https://www.vmware.com からパッチをダウンロードするように VUM が構成されていることを確認します。詳しくは、[VMware Update Manager の概要](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro#vmware-update-manager-introduction)を参照してください。
2. Flex または HTML を使用して、vCenter ユーザー・インターフェースを開き、**「VUM 管理ビュー」**にナビゲートします。
3. **「VUM 管理ビュー」**で、**「ESXi イメージ」**タブを選択し、**「ESXi イメージのインポート」**を選択します。
4. VMware からダウンロードした **ESXi 6.7u1iso** イメージを参照し、VUM リポジトリーにインポートします。

#### ESXi ホストをアップグレードする手順
{: #vc_vsphere_upgrade-procedure-esxi-upgrade}

1. vCenter ユーザー・インターフェースで、アップグレードする ESXi ホストが含まれているクラスターの名前にナビゲートします。
2. **「修正」**をクリックします。
3. 選択ボックスの左側で**「アップグレード ベースライン」**を選択し、選択画面の右側で**「VMware ESXi 6.7.0 U1」**ベースラインを選択します。**「次へ」**をクリックします (注: ESXi 6.7.0 U1 の VUM ベースラインは、ISO イメージを VUM リポジトリーにアップロードしたときに作成されます)。
4. アップグレードするホストを選択し、**「次へ」**をクリックします。
5. EULA に同意するオプションを選択し、**「次へ」**をクリックします。
6. 「詳細オプション」画面で**「次へ」**をクリックしてデフォルトを受け入れます。
7. 「ホストの修正オプション」画面で、オプションでリムーバブル・メディアを無効にすることを選択し、**「次へ」**を選択します。
8. 「クラスタの修正オプション」画面で**「次へ」**をクリックしてデフォルトを受け入れます。
9. 「設定の確認」画面で**「修正の事前チェック」**をクリックします。HA アドミッション制御に関する警告メッセージが返されます。  
10. **「完了」**をクリックすると、ホストのアップグレードが開始されます。

アップグレード・プロセスがすぐに失敗し、**「host cannot enter maintenance mode」**エラー・メッセージが表示された場合、Zerto ZVA をシャットダウンしてから、もう一度試してください。各サーバーの修正が完了すると、ZVRA VM が自動的に始動します。アップグレード・プロセス中に Zerto レプリケーションを継続する方法については、[How to Place a Host with an Associated VRA into Maintenance Mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/){:new_window}を参照してください。
{:note}

#### Intel NVME ドライバー・パッチの VUM リポジトリーへの追加
{: #vc_vsphere_upgrade-procedure-esxi-nvme}

バイナリー・ダウンロードのセクションで説明したように、``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` ファイルのコンテンツをリポジトリーにインポートする必要があります。後述のセクションで、ESXi ホストの重要でない拡張機能としてこのファイルを適用します。

1. ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` ファイルをジャンプ VM のローカル・ドライブで解凍します。
2. Flex または HTML を使用して、vCenter ユーザー・インターフェースを開き、**「VUM 管理ビュー」**にナビゲートします。
3. **「VUM 管理ビュー」**で、**「パッチ リポジトリ」**タブを選択し、**「パッチのインポート」**を選択します。
4. ``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-8733247.zip`` ディレクトリーにある解凍したコンテンツを参照し、``VMW-ESX-6.7.0-intel-nvme-vmd-1.4.0.1016-offline_bundle-8733247.zip`` ファイルを選択します。ファイルが VUM リポジトリーにすぐにインポートされます。

パッチ・リポジトリーでイメージを見つけます (**重要**なホスト拡張機能としてリストされています)。

#### ESXi ホストへのパッチ適用
{: #vc_vsphere_upgrade-procedure-esxi-patch}

アップグレード後に、重要な ESXi ホスト・パッチおよび重要でない ESXi ホスト・パッチをすべて適用することが推奨されています。

1. vCenter ユーザー・インターフェースで、パッチを適用するホストが含まれているクラスターを選択し、**「Update Manager」**タブを選択します。
2. **「修正」**を選択し、**「重要でないホスト パッチ」**を選択します。
3. 先ほど ESXi をアップグレードしたときと同じように進めます。この処理の中で Zerto ZVRA VM をもう一度シャットダウンする必要があることに注意してください。

### 追加のアイテムのアップグレード
{: #vc_vsphere_upgrade-procedure-addtl}

#### vSAN オン・ディスク・フォーマット・バージョンのアップグレード
{: #vc_vsphere_upgrade-procedure-addtl-vsan}

vSAN ディスク・フォーマット・バージョンをバージョン 7 にアップグレードします。

1. vCenter ユーザー・インターフェースで、アップグレードする vSAN が含まれているクラスターにナビゲートします。
2. クラスター・オブジェクトから、**「設定」 > 「vSAN」> 「全般」**と選択します。
3. **「アップグレードの事前チェック」**をクリックして、アップグレードの互換性と起こりうる問題について確認します。検査から**「アップグレードの準備が完了しました...」**が返されるまで待機します。
4. **「アップグレード」**をクリックします。 アップグレードでは同時にディスク・グループも処理されるので、クラスターのサイズによっては、完了するまでに時間がかかる場合があります。オプションで、処理中に**「冗長性の低下を許可」**を選択します。これを選択すると、アップグレード時間を大幅に短縮できますが、アップグレード処理中にディスク障害が発生すると、データが失われる可能性があります。

#### 仮想分散スイッチのアップグレード
{: #vc_vsphere_upgrade-procedure-addtl-vds}

仮想分散スイッチ (VDS) を v6.6.0 にアップグレードすると、ネットワーク I/O 制御もアップグレードされ、強化された Link Aggregation Control Protocol (LACP) サポートが追加されます。

1.	HCX をデプロイしている場合は、HCX が存在する VDS をアップグレードする前に、HCX のクラウド・ゲートウェイの部分をアンデプロイする必要があります。HCX を最新バージョンに更新してから、クラウド・ゲートウェイを再デプロイする必要があります。
2.	vCenter ユーザー・インターフェースで、**「ネットワーク」**タブにナビゲートします。
3.	アップグレードする分散スイッチ (**SDDC-Dswitch-Private** または **SDDC-Dswitch-Public**) を右クリックし、**「Distributed Switch のアップグレード」**を選択します。

#### vCenter ユーザー・インターフェースの拡張機能およびプラグインのアップグレード
{: #vc_vsphere_upgrade-procedure-addtl-extension}

vCenter Server 環境内の拡張機能またはスナップインのアップグレードは、お客様の責任で行ってください。vCenter ユーザー・インターフェースで**「ホーム」 > 「管理」 > 「ソリューション」**の順にクリックしてステータスを表示し、vCenter の拡張機能とプラグインの有効/無効を切り替えます。

#### VMware ツールのアップグレード
{: #vc_vsphere_upgrade-procedure-addtl-tools}

vCenter ユーザー・インターフェースを使用して、VMware ゲスト・ツールのアップグレードを実行します。いくつかの VMware ツールが、vCenter Server 環境に移行された一部の古い VM で必要になる場合があります。  

#### 仮想マシンのハードウェア・レベルのアップグレード
{: #vc_vsphere_upgrade-procedure-addtl-vmhw}

VMware ゲスト・ツールと同様に、vCenter Server 環境のアップグレードが原因で、現行のハードウェア・レベルでは古い VM がサポートされない状態になる場合があります。vCenter ユーザー・インターフェースを使用して、そのような VM を探し、必要に応じて更新します。  

## vCenter Server vSphere ソフトウェアをアップグレードした結果
{: #vc_vsphere_upgrade-results}

アップグレードが完了した後に、vSAN ヘルス・チェックを実行すると、IBM Cloud が提供する RAID コントローラーやネットワーク・コントローラーのファームウェア更新に関する警告が表示されることがあります。ファームウェア更新が必要なホストを特定してから、IBM サポートのチケットを開き、推奨されるバージョンへのファームウェア更新を依頼してください。

1. vCenter ユーザー・インターフェースで、ヘルス・チェックを実行する vSAN ホストが含まれているクラスターを選択します。
2. **「監視」**タブを選択して、**「vSAN」**タブを選択します。
3. **「健全性」**を選択し、警告が表示されていないか確認します。
4. **「ハードウェア互換性」**の警告が表示されている場合は、その警告を展開表示し、警告の状態であれば、**「コントローラ ファームウェアが VMware により認定済み」**メッセージをクリックします。
5. リストされているホストとファームウェア更新の推奨情報をメモします。
6. IBM サポートのチケットを開き、ファームウェア更新を実行するために各ホストのサービス停止時間をスケジュールします。

アップグレードが完了したら、IBM サポートのチケットを更新します。その後、IBM サポートが {{site.data.keyword.vmwaresolutions_short}} コンソールを更新し、{{site.data.keyword.vmwaresolutions_short}} 自動化機能を 6.7 レベルで再開します。その一環として、サービス、ホスト、クラスター、セカンダリー vCenter Server インスタンスの追加と削除が実行されます。

## 関連リンク
{: #vc_vsphere_upgrade-related}

* [VMware NSX Data Center for vSphere 6.4.4 リリース・ノート](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/rn/releasenotes_nsx_vsphere_644.html){:new_window}
* [NSX アップグレード・ガイド](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.upgrade.doc/GUID-4613AC10-BC73-4404-AF80-26E924EF5FE0.html){:new_window}
* [IBM サポートへのお問い合わせ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

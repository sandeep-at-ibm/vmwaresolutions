---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-01"

keywords: vCenter Server add host, add server vCenter Server, remove host vCenter Server

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスの容量の拡張と縮小
{: #vc_addingremovingservers}

VMware vCenter Server インスタンスの容量は、ESXi サーバーまたはネットワーク・ファイル・システム (NFS) ストレージを追加/削除することで、ビジネス・ニーズに応じて拡張/縮小できます。

* V3.2 リリース以降では、vSphere Enterprise Plus 6.7u1 による既存のインスタンスに、vSphere Enterprise Plus 6.7u1 または vSphere Enterprise Plus 6.7u2 による新しいホストを追加するオプションがあります。
* V3.1 リリース以降では、既存のクラスターに新しい ESXi サーバーを追加できます。そのためには、既存の構成か、クラスター内の既存のホストとは別の代替の構成を選択します。 新しいサーバーを注文する際には、既存の構成がすぐに選択できるように表示されます。 パフォーマンスや安定性で問題が生じるのを避けるため、CPU、RAM、ストレージに関しては、すべてのクラスターで同じか類似した構成を使用することをお勧めします。 この機能は、同じクラスター内でハードウェア更新を行うときに役立ちます。 1 つのクラスターに設定できるのは 1 つのタイプのストレージのみです。
* V3.0 リリース以降、**「使用可能」**状態にある複数のクラスターで、NFS ストレージと ESXi サーバーを同時に追加/削除できるようになりました。 例えば、あるクラスターで ESXi サーバーを追加または削除したり、別のクラスターで NFS ストレージを追加または削除したりできます。
* V2.9 リリース以降では、サーバーが保守モードの間に、新規 ESXi サーバーをクラスターに追加できます。 また、複数のクラスター間で同時に ESXi サーバーを追加または削除できます。

**注**:
* 初期クラスターのストレージが vSAN の場合、デプロイメント後に 1 つ以上の ESXi サーバーを追加すると、クラスター・ストレージの容量を増やすことができます。
* 既存の NFS または vSAN vCenter Server クラスターの NFS ストレージ共有を追加/削除することができます。

## vCenter Server インスタンスへの ESXi サーバーの追加
{: #vc_addingremovingservers-adding}

### ESXi サーバーを追加する前に
{: #vc_addingremovingservers-adding-prereq}

* 可能であれば、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを追加してください。これは、VMware vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されないためです。 したがって、オンプレミスの ESXi サーバー、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できない、または管理しない ESXi サーバーに対してのみ、ESXiサーバーを vCenter Server に追加します。
* NFS ストレージのある vCenter Server インスタンスには、少なくとも 2 つの ESXi サーバーが必要です。 V2.1 以降にデプロイされたインスタンスの場合、デフォルト・クラスターについては、ESXi サーバーを最大 51 台まで配置して拡張できます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。
* vSAN ストレージのある vCenter Server インスタンスには、少なくとも 4 つの ESXi サーバーが必要です。
* V2.0 以前にデプロイされた vCenter Server インスタンスの場合、クラスターごとに、ESXi サーバーを最大 32 個まで配置して拡張できます。
* 一度に 1 台から 20 台の ESXi サーバーを追加できます。 最小限の ESXi サーバーについて詳しくは、[2 ノードの vCenter Server インスタンスの可用性は高いですか?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-) を参照してください。

### ESXi サーバーを追加する手順
{: #vc_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**セクションで**「追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を選択します。
7. オプションで、保守モード中にサーバーを追加するためのチェック・ボックスを選択します。 このチェック・ボックスはデフォルトで選択されます。

   新しい ESXi サーバーをプロビジョニングする際、**「保守モード (Maintenance Mode)」**チェック・ボックスを選択していない場合には仮想マシン (VM) が新しいサーバーにすぐにマイグレーションされます。 マイグレーション開始前に確認メッセージは表示されません。
   {:important}

8. ベア・メタル構成を次の手順で実行します。
   * クラスター内の既存のホストから構成を選択します。
   * 新しい {{site.data.keyword.baremetal_short_sing}} 構成を選択します。
      * vSphere Enterprise Plus 6.7u1 によるインスタンスの場合、新しいホストに Vmware vSphere バージョンを指定します。
      * **Skylake**、**Cascade**、または **Broadwell** の場合、**CPU モデル**、**RAM** の数、**{{site.data.keyword.baremetal_short}} の数**を指定します。     
      * **SAP 認定**の場合、**CPU モデル、RAM**、**{{site.data.keyword.baremetal_short}} の数**を指定します。
9. ストレージ構成を次の手順で実行します。 容量ディスクおよびキャッシュ・ディスクのディスク・タイプ、ディスク数、vSAN ライセンス・エディションを指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
10. 見積もりコストを確認し、**「追加」**をクリックします。

  また、**「見積もりに追加」**をクリックして、プロビジョン済みリソースを {{site.data.keyword.cloud_notm}} 見積もりツールに追加することもできます。 この操作は、購入を検討している他の {{site.data.keyword.cloud_notm}} リソースと一緒に、選択した {{site.data.keyword.vmwaresolutions_short}}リソースのコストを見積もる場合に役立ちます。

### ESXi サーバーを追加した結果
{: #vc_addingremovingservers-adding-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。
4. 以下のような状況では、Zerto Virtual Manager (ZVM) コンソールと事前定義済みの Zerto Virtual Replication Appliance (VRA) IP アドレスを使用して、手動で VRA 仮想マシンをデプロイする必要があります。
   * ESXi サーバーが保守モードで、Zerto for {{site.data.keyword.cloud_notm}} がインストールされているときに、デフォルト・クラスターに ESXi サーバーを追加する場合。
   * 保守モードの ESXi サーバーを持つ vCenter Server インスタンスに Zerto for {{site.data.keyword.cloud_notm}} を追加する場合。

保守モード時に ESXi サーバーを追加する場合、保守モードを解除するまで VM は新規サーバーにマイグレーションされません。   
{:important}

## vCenter Server インスタンスからの ESXi サーバーの削除
{: #vc_addingremovingservers-removing}

### ESXi サーバーを削除する前に
{: #vc_addingremovingservers-removing-prereq}

* 可能であれば、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを削除してください。これは、vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されないためです。 したがって、オンプレミスの ESXi サーバー、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できない、または管理しない ESXi サーバーに対してのみ、ESXiサーバーを vCenter Server から削除します。
* NFS ストレージを使用する vCenter Server インスタンスには、2 つ以上の ESXi サーバーが必要であり、vSAN ストレージを使用する vCenter Server インスタンスには、4 つ以上の ESXi サーバーが必要です。
* F5 on {{site.data.keyword.cloud_notm}} サービスまたは FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーの場合は、そのサーバーを削除する前に、F5 BIG-IP と FortiGate の VM を、VM をホスティングしている ESXi サーバーとは別のサーバーにマイグレーションする必要があります。
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーを削除する前に、アクティブな (失敗したか、進行中の) バックアップ操作またはリストア操作がないことを確認してください。こうしたアクティブな操作があると、ESXi サーバーが削除されない可能性があるためです。
* ESXi サーバーを削除する際には、そのサーバーは保守モードになります。その後、そこで実行されているすべての VM は、vCenter Server からそのサーバーが削除される前にマイグレーションされます。 VM の再配置を最大限に制御するために、VMware vSphere Web Client を使用して、手動により、削除する ESXi サーバーを保守モードにし、サーバーで実行されている VM を移行することをお勧めします。 その後、{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して ESXi サーバーを削除します。

VMware HCX on {{site.data.keyword.cloud_notm}} サービスを注文する際は、12 カ月間のコミットメントが必要です。12 カ月のコミットメント期間が終了する前にクラスターを削除した場合、アカウントには HCX コンポーネントに対する課金が引き続き発生します。12 カ月のコミットメント満了日は、HCX on {{site.data.keyword.cloud_notm}} の詳細ページに示されています。サービス詳細の表示について詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure)を参照してください。
{:important}

### ESXi サーバーを削除する手順
{: #vc_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを削除するクラスターをクリックします。
5. **「ESXi サーバー」**セクションで、削除するサーバーを選択し、**「削除」**をクリックします。

### ESXi サーバーを削除した結果
{: #vc_addingremovingservers-removing-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを削除する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって ESXi サーバーに全面的な再利用処理が施されます。

   削除した ESXi サーバーについては、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
   {:note}

## vCenter Server インスタンスへの NFS ストレージの追加
{: #section-adding-nfs-storage-to-vcenter-server-instances}

### NFS ストレージを追加する前に
{: #vc_addingremovingservers-adding-nfs-storage-prereq}

VMware vSphere Web クライアントから NFS ストレージの追加を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。 IBM は、お客様がインスタンスに手動で追加した NFS ファイル共有を管理しません。

### NFS ストレージを追加する手順
{: #vc_addingremovingservers-adding-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、NFS ストレージを追加するクラスターをクリックします。
5. **「ストレージ」**セクションで**「追加」**をクリックします。
6. **「ストレージ」**ウィンドウで、ストレージ構成を入力します。
   * 追加するすべてのファイル共有に同じ設定を構成する場合は、**「共有の数」**、**「パフォーマンス」**、**「サイズ (GB)」**を指定します。
   * ファイル共有を個々に追加して構成する場合は、**「共有を個別に構成」**を選択し、ファイル共有ごとに、** 「共有ストレージの追加」**ラベルの横にある**「+」**アイコンをクリックして、**「パフォーマンス」**と**「サイズ (GB)」**を選択します。 少なくとも 1 つのファイル共有を選択する必要があります。
7. 見積もりコストを確認し、**「NFS ストレージの追加 (Add NFS Storage)」**をクリックします。

  また、**「見積もりに追加」**をクリックして、プロビジョン済みリソースを {{site.data.keyword.cloud_notm}} 見積もりツールに追加することもできます。 この操作は、購入を検討している他の {{site.data.keyword.cloud_notm}} リソースと一緒に、選択した {{site.data.keyword.vmwaresolutions_short}}リソースのコストを見積もる場合に役立ちます。

### NFS ストレージを追加した結果
{: #vc_addingremovingservers-adding-nfs-storage-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. NFS ストレージを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、NFS ストレージに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した NFS ストレージがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

## vCenter Server インスタンスからの NFS ストレージの削除
{: #vc_addingremovingservers-removing-nfs-storage}

### NFS ストレージを削除する前に
{: #vc_addingremovingservers-removing-nfs-storage-prereq}

* VMware vSphere Web クライアントから NFS ストレージの削除を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。
* NFS ストレージを削除する前に、そのストレージにある VM をすべて削除したことを確認してください。
* 削除しようとしている共有が、正しい vCenter Server インスタンスと関連付けられていることを確認してください。
* クラスターの状況が**「使用可能」**でなければなりません。

### NFS ストレージを削除する手順
{: #vc_addingremovingservers-removing-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、NFS ストレージを削除するクラスターをクリックします。
5. **「ストレージ」**セクションで、削除するストレージ共有を選択し、**「削除」**をクリックします。
6. **「ストレージの削除 (Remove Storage)」**ウィンドウで**「削除」**をクリックします。

### NFS ストレージを削除した結果
{: #vc_addingremovingservers-removing-nfs-storage-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. NFS ストレージを削除する要求の処理中であることが、E メールで通知されます。 コンソールで、NFS ストレージに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって NFS ストレージに全面的な再利用処理が施されます。

   削除した NFS ストレージについては、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
   {:note}

## 関連リンク
{: #vc_addingremovingservers-related}

* [vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [vCenter Server インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)
* [ホストをメンテナンス モードに切り替える](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:external}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:external}

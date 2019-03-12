---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server インスタンスの容量の拡張と縮小
{: #vc_addingremovingservers}

VMware vCenter Server インスタンスの容量は、ESXi サーバーまたはネットワーク・ファイル・システム (NFS) ストレージを追加/削除することで、ビジネス・ニーズに応じて拡張/縮小できます。

既存の NFS または vSAN vCenter Server クラスターの NFS ストレージ共有を追加/削除することができます。
{:note}

初期クラスターのストレージが vSAN の場合、デプロイメント後に 1 つ以上の ESXi サーバーを追加すると、クラスター・ストレージの容量を増やすことができます。

## vCenter Server インスタンスへの ESXi サーバーの追加
{: #vc_addingremovingservers-adding}

### ESXi サーバーを追加する前に
{: #vc_addingremovingservers-adding-prereq}

* VMware vSphere Web クライアントから ESXi サーバーの追加を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_full}} コンソールと同期されません。
* NFS ストレージのある vCenter Server インスタンスには、少なくとも 2 つの ESXi サーバーが必要です。 V2.1 以降にデプロイされたインスタンスの場合、デフォルト・クラスターについては、ESXi サーバーを最大 51 台まで配置して拡張できます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。
* vSAN ストレージのある vCenter Server インスタンスには、少なくとも 4 つの ESXi サーバーが必要です。
* V2.0 以前にデプロイされた vCenter Server インスタンスの場合、クラスターごとに、ESXi サーバーを最大 32 個まで配置して拡張できます。 一度に追加できる{{site.data.keyword.baremetal_short}}の数は、以下のとおりです。
   * **「スモール」**、**「ミディアム」**、**「ラージ」**の各構成では、一度に 1 から 10 個の ESXi サーバーを追加できます。
   * **「Skylake」**構成と**「Broadwell」**構成の場合、一度に 1 台から 20 台までの ESXi サーバーを追加できます。 最小限の ESXi サーバーについて詳しくは、[2 ノードの vCenter Server インスタンスの可用性は高いですか?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-) を参照してください。

### ESXi サーバーを追加する手順
{: #vc_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**セクションで**「サーバーの追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を入力し、見積もりコストを確認して、**「サーバーの追加」**をクリックします。

### ESXi サーバーを追加した結果
{: #vc_addingremovingservers-adding-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

## vCenter Server インスタンスからの ESXi サーバーの削除
{: #vc_addingremovingservers-removing}

### ESXi サーバーを削除する前に
{: #vc_addingremovingservers-removing-prereq}

* VMware vSphere Web クライアントから ESXi サーバーの削除を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。
* NFS ストレージを使用する vCenter Server インスタンスには、2 つ以上の ESXi サーバーが必要であり、vSAN ストレージを使用する vCenter Server インスタンスには、4 つ以上の ESXi サーバーが必要です。
* F5 on {{site.data.keyword.cloud_notm}} サービスまたは FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーの場合は、そのサーバーを削除する前に、F5 BIG-IP と FortiGate の VM を、VM をホスティングしている ESXi サーバーとは別のサーバーにマイグレーションする必要があります。
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーを削除する前に、アクティブな (失敗したか、進行中の) バックアップ操作またはリストア操作がないことを確認してください。こうしたアクティブな操作があると、ESXi サーバーが削除されない可能性があるためです。
* ESXi サーバーを削除する際には、そのサーバーは保守モードになります。その後、そこで実行されているすべての仮想マシン (VM) は、vCenter Server からそのサーバーが削除される前にマイグレーションされます。 VM の再配置を最大限に制御するために、VMware vSphere Web Client を使用して、手動により、削除する ESXi サーバーを保守モードにし、サーバーで実行されている VM を移行することをお勧めします。 その後、{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して ESXi サーバーを削除します。

### ESXi サーバーを削除する手順
{: #vc_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
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

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、NFS ストレージを追加するクラスターをクリックします。
5. **「ストレージ」**セクションで**「追加」**をクリックします。
6. **「ストレージ」**ウィンドウで、ストレージ構成を入力します。
   * 追加するすべてのファイル共有に同じ設定を構成する場合は、**「共有の数」**、**「パフォーマンス」**、**「サイズ (GB)」**を指定します。
   * ファイル共有を個々に追加して構成する場合は、**「共有を個別に構成」**を選択し、ファイル共有ごとに、** 「共有ストレージの追加」**ラベルの横にある**「+」**アイコンをクリックして、**「パフォーマンス」**と**「サイズ (GB)」**を選択します。 少なくとも 1 つのファイル共有を選択する必要があります。
7. **「NFS ストレージの追加」**をクリックします。

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

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
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
* [vCenter Server インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)
* [ホストをメンテナンス モードに切り替える](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

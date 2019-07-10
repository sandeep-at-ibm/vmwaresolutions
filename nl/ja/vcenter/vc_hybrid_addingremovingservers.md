---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vCenter Server Hybridity add host, add server vCenter Server Hybridity, remove host vCenter Server Hybridity

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小
{: #vc_hybrid_addingremovingservers}

ビジネス・ニーズに応じて、ESXi サーバーを追加または削除することで VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスの容量を拡張または縮小できます。

V3.1 リリース以降では、既存のクラスターに新しい ESXi サーバーを追加できます。その場合には、既存の構成か、クラスター内の既存のホストとは別の代替の構成を選択します。新しいサーバーを注文する際には、既存の構成がすぐに選択できるように表示されます。パフォーマンスや安定性で問題が生じるのを避けるため、CPU、RAM、ストレージに関しては、すべてのクラスターで同じか類似した構成を使用することをお勧めします。この機能は、同じクラスター内でハードウェア更新を行うときに役立ちます。1 つのクラスターに設定できるのは 1 つのタイプのストレージのみです。

V2.9 リリース以降では、クラスターが保守モードの間に、新規 ESXi サーバーをクラスターに追加できます。 また、複数のクラスター間で同時に ESXi サーバーを追加または削除できます。 以下の同時操作が可能です。

* 1 つのクラスターへのホストの追加と、追加のクラスターへのホストの追加。
* 1 つのクラスターからのホストの削除と、追加のクラスターからのホストの削除。
* 1 つのクラスターへのホストの追加と、追加のクラスターからのホストの削除。
* 1 つのクラスターからのホストの削除と、追加のクラスターへのホストの追加。

初期クラスターのストレージが vSAN なので、デプロイメント後に 1 つ以上の ESXi サーバーを追加して、クラスター・ストレージの容量を増やすことができます。

## vCenter Server with Hybridity Bundle インスタンスへの ESXi サーバーの追加
{: #vc_hybrid_addingremovingservers-adding}

### ESXi サーバーを追加する前に
{: #vc_hybrid_addingremovingservers-adding-prereq}

* 可能であれば、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを追加してください。これは、VMware vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されないためです。 したがって、オンプレミスの ESXi サーバー、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できない、または管理しない ESXi サーバーに対してのみ、ESXiサーバーを vCenter Server に追加します。
* vSAN ストレージには 4 つ以上の ESXi サーバーが必要です。

## ESXi サーバーを追加する手順
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**テーブルで**「追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を入力します。
7. オプションで、保守モード中にサーバーを追加するためのチェック・ボックスを選択します。 このチェック・ボックスはデフォルトで選択されます。

   新しい ESXi サーバーをプロビジョニングする際、**「保守モード (Maintenance Mode)」**チェック・ボックスを選択していない場合には仮想マシン (VM) が新しいサーバーにすぐにマイグレーションされます。マイグレーション開始前に確認メッセージは表示されません。{:important}

8. ベア・メタル構成を次の手順で実行します。
   * クラスター内の既存のホストから構成を選択します。
   * 新しい {{site.data.keyword.baremetal_short_sing}} 構成を選択し、CPU モデルと RAM サイズを指定します。
9. ストレージ構成を次の手順で実行します。 容量ディスクおよびキャッシュ・ディスクのディスク・タイプ、ディスク数、vSAN ライセンス・エディションを指定します。 さらにストレージが必要な場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。
10. 見積もりコストを確認し、**「追加」**をクリックします。

  また、**「見積もりに追加」**をクリックして、プロビジョン済みリソースを {{site.data.keyword.cloud_notm}} 見積もりツールに追加することもできます。この操作は、購入を検討している他の {{site.data.keyword.cloud_notm}} リソースと一緒に、選択した {{site.data.keyword.vmwaresolutions_short}}リソースのコストを見積もる場合に役立ちます。

### ESXi サーバーを追加した結果
{: #vc_hybrid_addingremovingservers-adding-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

保守モード時に ESXi サーバーを追加する場合、クラスターの保守モードを解除するまで仮想マシン (VM) は新規サーバーにマイグレーションされません。   
{:important}

## vCenter Server with Hybridity Bundle インスタンスからの ESXi サーバーの削除
{: #vc_hybrid_addingremovingservers-removing}

### ESXi サーバーを削除する前に
{: #vc_hybrid_addingremovingservers-removing-prereq}

* 可能であれば、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを削除してください。これは、vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されないためです。 したがって、オンプレミスの ESXi サーバー、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できない、または管理しない ESXi サーバーに対してのみ、ESXiサーバーを vCenter Server から削除します。
* vSAN ストレージには 4 つ以上の ESXi サーバーが必要です。
* F5 on {{site.data.keyword.cloud_notm}} サービスまたは FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーの場合は、そのサーバーを削除する前に、F5 BIG-IP と FortiGate の VM を、VM をホスティングしている ESXi サーバーとは別のサーバーにマイグレーションする必要があります。
* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーを削除する前に、アクティブな (失敗したか、進行中の) バックアップ操作またはリストア操作がないことを確認してください。こうしたアクティブな操作があると、ESXi サーバーが削除されない可能性があるためです。
* ESXi サーバーを削除する際には、そのサーバーは保守モードになります。その後、そこで実行されているすべての仮想マシン (VM) は、vCenter Server からそのサーバーが削除される前にマイグレーションされます。 VM の再配置を最大限に制御するために、VMware vSphere Web Client を使用して、手動により、削除する ESXi サーバーを保守モードにし、サーバーで実行されている VM を移行することをお勧めします。 その後、{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して ESXi サーバーを削除します。

## ESXi サーバーを削除する手順
{: #vc_hybrid_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを削除するクラスターをクリックします。
5. **「ESXi サーバー」**テーブルで、削除するサーバーを選択し、**「削除」**をクリックします。

### ESXi サーバーを削除した結果
{: #vc_hybrid_addingremovingservers-removing-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを削除する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって ESXi サーバーに全面的な再利用処理が施されます。

   削除した ESXi サーバーについては、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
   {:note}

## 関連リンク
{: #vc_hybrid_addingremovingservers-related}

* [vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server with Hybridity Bundle インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [vCenter Server with Hybridity Bundle インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [ホストをメンテナンス モードに切り替える](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:new_window}

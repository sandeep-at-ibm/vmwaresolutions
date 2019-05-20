---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle インスタンスの容量の拡張と縮小
{: #vc_hybrid_addingremovingservers}

ビジネス・ニーズに応じて、ESXi サーバーを追加または削除することで VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle インスタンスの容量を拡張または縮小できます。

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

* VMware vSphere Web クライアントで加えた変更は {{site.data.keyword.vmwaresolutions_short}} コンソールと同期されないので、可能な限り、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを追加してください。つまり、オンプレミスの ESXi サーバー、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できない、あるいは管理しない ESXi サーバーの場合にのみ、ESXi サーバーを vCenter Server に追加してください。
* vSAN ストレージには 4 つ以上の ESXi サーバーが必要です。

## ESXi サーバーを追加する手順
{: #vc_hybrid_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**テーブルで**「追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を入力します。
7. オプションで、保守モード中にサーバーを追加するためのチェック・ボックスを選択します。
8. 見積もりコストを確認し、**「追加」**をクリックします。

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

* vSphere Web クライアントで加えた変更は {{site.data.keyword.vmwaresolutions_short}} コンソールと同期されないので、可能な限り、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを削除してください。つまり、オンプレミスの ESXi サーバー、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できない、あるいは管理しない ESXi サーバーの場合にのみ、ESXi サーバーを vCenter Server から削除してください。
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

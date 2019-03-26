---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation インスタンスの容量の拡張と縮小
{: #sd_addingremovingservers}

ESXi サーバーを追加または削除することによって、業務上の必要に従って VMware Cloud Foundation インスタンスの容量を拡張したり縮小したりできます。

Cloud Foundation インスタンスには 5 つまでクラスターを配置できます。そのうち 1 つはデフォルトです。 それぞれの初期クラスターには ESXi サーバーを 51 台まで配置することが可能で、追加のクラスターは 59 台まで配置できます。

## Cloud Foundation インスタンスへの ESXi サーバーの追加
{: #sd_addingremovingservers-adding}

### ESXi サーバーを追加する前に
{: #sd_addingremovingservers-adding-prereq}

* VMware vSphere Web クライアントから ESXi サーバーの追加を行わないでください。 VMware vSphere Web クライアントで加えた変更は、{{site.data.keyword.vmwaresolutions_full}} コンソールと同期されません。
* 注文した基本プラットフォームには、デフォルトで 4 台の ESXi サーバーがあります。 プラットフォームは、最大で 32 台の ESXi サーバーに拡張できます。 しかし、一度に追加できる{{site.data.keyword.baremetal_short}}の数は以下のとおりです。
   * **スモール** 構成と **ラージ** 構成の場合、一度に 1 台から 10 台まで ESXi サーバーを追加できます。
   * **「Skylake」**構成と**「Broadwell」**構成の場合、一度に 1 台から 20 台までの ESXi サーバーを追加できます。

## ESXi サーバーを追加する手順
{: #sd_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**セクションで**「追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を入力し、見積もりコストを確認して、**「追加」**をクリックします。

### ESXi サーバーを追加した結果
{: #sd_addingremovingservers-adding-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーが追加されるときには、E メールで通知されます。
3. リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

## Cloud Foundation インスタンスからの ESXi サーバーの削除
{: #sd_addingremovingservers-removing}

### ESXi サーバーを削除する前に
{: #sd_addingremovingservers-removing-prereq}

* VMware vSphere Web クライアントから ESXi サーバーの削除を行わないでください。 VMware vSphere Web クライアントで加えた変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。
* 注文した基本プラットフォームには、デフォルトで 4 台の ESXi サーバーがあります。 追加した ESXi サーバーを削除できます。 デフォルトの ESXi サーバーは削除できません。
* F5 on {{site.data.keyword.cloud_notm}} サービスまたは FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーの場合は、そのサーバーを削除する前に、F5 BIG-IP と FortiGate の VM を、VM をホスティングしている ESXi サーバーとは別のサーバーにマイグレーションする必要があります。
* IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} サービスがインストールされている ESXi サーバーを削除する前に、アクティブなバックアップ操作またはリストア操作がないことを確認してください。 アクティブな操作 (失敗または進行中) があると、ESXi サーバーが削除されない可能性があります。

## ESXi サーバーを削除する手順
{: #sd_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを削除するクラスターをクリックします。
6. **「ESXi サーバー」**セクションで、削除するサーバーを選択し、**「削除」**をクリックします。

### ESXi サーバーを削除した結果
{: #sd_addingremovingservers-removing-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーが削除されるときには、E メールで通知されます。
3. {{site.data.keyword.cloud_notm}} の請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって ESXi サーバーに全面的な再利用処理が施されます。

   削除対象の ESXi サーバーに関する請求は、{{site.data.keyword.cloud_notm}} 請求処理サイクルの終わりまで行われます。
   {:note}

## 関連リンク
{: #sd_addingremovingservers-related}

* [Cloud Foundation の部品構成表](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
* [Cloud Foundation インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-sd_addingviewingclusters#sd_addingviewingclusters)
* [ホストをメンテナンス モードに切り替える](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}

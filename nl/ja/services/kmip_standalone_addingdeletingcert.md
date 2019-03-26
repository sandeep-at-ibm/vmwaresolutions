---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud インスタンスの証明書の追加、表示、削除
{: #kmip_standalone_addingdeletingcert}

KMIP for VMware on {{site.data.keyword.cloud}} インスタンスの準備ができたら、インスタンスに証明書を追加する必要があります。 不要になった証明書は、インスタンスから削除してください。

## KMIP for VMware on IBM Cloud インスタンスに証明書を追加する手順
{: #kmip_standalone_addingdeletingcert-add}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「KMIP for VMware on IBM Cloud インスタンス」**表までスクロールダウンし、証明書を追加するインスタンスをクリックします。
3. **「追加」**をクリックします。
4. **「クライアント SSL 証明書の追加 (Add Client SSL Certificate)」**ウィンドウで、証明書の名前と内容を入力します。

   選択したインスタンス内で証明書の名前を再使用することはできません。 証明書の内容が有効でなければならず、「BEGIN CERTIFICATE」タグと「END CERTIFICATE」タグが含まれている必要があります。インスタンスがデプロイされている選択した領域内で証明書を再使用することはできません。
   {:note}
5. **「追加」**をクリックします。

## KMIP for VMware on IBM Cloud インスタンスの証明書を表示する手順
{: #kmip_standalone_addingdeletingcert-view}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「KMIP for VMware on IBM Cloud インスタンス」**表までスクロールダウンし、証明書を表示するインスタンスをクリックします。
3. **「クライアント SSL 証明書」**セクションの下にある追加された証明書のリストを表示します。
4. 特定の証明書の内容を表示するには、**「ダウンロード」**をクリックします。

## KMIP for VMware on IBM Cloud インスタンスから証明書を削除する手順
{: #kmip_standalone_addingdeletingcert-delete}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「KMIP for VMware on IBM Cloud インスタンス」**表までスクロールダウンし、証明書を削除するインスタンスをクリックします。
3. **「クライアント SSL 証明書」**表で、削除する証明書を見つけて**「削除」**アイコンをクリックします。

   ただちに、そのクライアントは、データの暗号化/復号またはバックアップの目的に鍵を利用することが一切できなくなります。 クライアントに再び鍵を利用させるためには、クライアント SSL 証明書をもう一度追加する必要があります。
   {:note}

## 関連リンク
{: #kmip_standalone_addingdeletingcert-related}

* [KMIP for VMware on IBM Cloud インスタンスの参照](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on IBM Cloud インスタンスの注文](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [KMIP for VMware on IBM Cloud インスタンスの削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker イベント](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)

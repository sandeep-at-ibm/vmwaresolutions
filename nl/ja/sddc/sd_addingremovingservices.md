---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Cloud Foundation インスタンス用サービスの注文、表示、削除

災害復旧ソリューションなどの、VMware Cloud Foundation インスタンス用サービスを注文できます。 これらのサービスが不要になった場合は、インスタンスから削除できます。

## Cloud Foundation インスタンス用の使用可能なサービス

Cloud Foundation インスタンスで使用できるサービスと、インストール済みのサービスのバージョンを以下の表にまとめます。

表 1. Cloud Foundation インスタンスに使用可能なサービス

| サービス名 | 現在のサービスのバージョン | インスタンスのバージョン |
|----------------------------------------------------------------------------------------|------------------|
| [F5 on {{site.data.keyword.cloud}}](/docs/services/vmwaresolutions/services/f5_considerations.html)                                 | BIG-IP VE v13.1.1.2 | V1.9 以降 |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fsa_considerations.html)       | 300 シリーズ | V1.8 以降 |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/fortinetvm_considerations.html) | 6.0.3 | V2.0 以降 |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html)              | 5.4.0 | V2.3 以降 |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html)              | 4.2.1 | V2.3 以降 |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html)              | 4.2 | V2.5 以降 |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/spp_considerations.html)  | 10.1.2 | V2.2 以降 |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html) |  2.0 | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/veeam_considerations.html)                          | 9.5u3 | V1.8 以降 |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/addingzertodr.html)                                 | 6.0 update 3 | V1.2 以降 |

## Cloud Foundation インスタンスにサービスを追加する手順

Cloud Foundation インスタンスにサービスを追加するには、前のテーブルで該当サービスのリンクをクリックし、そのサービスに関する考慮事項を確認し、デプロイするコンポーネントにチェック・マークを付けます。 その後、該当するサービス注文トピックに記されている指示に従って、インスタンスにサービスを追加します。

### サービスのインストールの結果

サービスのインストールが正常に完了すると、E メールで通知が届きます。また、そのサービスがインスタンスの**「サービス」**ページに表示され、サービスの状況が**「インストール済み」**になります。

## Cloud Foundation インスタンス用サービスを表示する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、サービスを表示するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「サービス」**をクリックします。
4. **「サービス」**ページでサービスをクリックし、そのサービスの情報 (サービス状況などの詳細) を確認します。
5. 表示したサービスによっては、サービスの詳細情報に記されている資格情報を使用してサービス・コンソールにアクセスし、そこからサービスを管理することもできます。

## Cloud Foundation インスタンス用サービスを削除する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、サービスを削除するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「サービス」**をクリックします。
4. **「サービス」**ページで、削除するサービス・インスタンスを見つけて**「削除」**アイコンをクリックします。
5. **「サービスの削除」**ウィンドウで、考慮事項または警告が示されているなら、それを確認します。 **「了解」**を選択し、**「削除」**をクリックします。

### サービスの削除結果

サービスの削除要求が受け入れられると、サービス状況が**「削除中」**に変更されます。

サービスの削除が正常に完了すると、お客様に E メールで通知され、サービスがインスタンスの**「サービス」**ページから削除されます。

削除したサービスは、{{site.data.keyword.cloud_notm}} の請求サイクルの最後まで課金されます。
{:note}

### 関連リンク

* [よくある質問](/docs/services/vmwaresolutions/vmonic/faq.html)

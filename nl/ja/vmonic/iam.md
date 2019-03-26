---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

---

# IAM でのユーザー・アクセス権限の管理
{: #iam}

アカウント内のユーザーの {{site.data.keyword.vmwaresolutions_full}} サービス・インスタンスへのアクセス権限は、{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) によって制御されます。 アカウント内で {{site.data.keyword.vmwaresolutions_short}} サービスにアクセスするすべてのユーザーには、IAM ユーザー役割の定義されたアクセス・ポリシーが割り当てられている必要があります。

アクセス・ポリシーは。選択したサービスまたはインスタンスのコンテキスト内でユーザーが実行できる操作を定義します。 許可される操作は、サービス上で実行できる操作として、{{site.data.keyword.cloud_notm}} サービスによってカスタマイズされて定義されます。 その後、操作は IAM ユーザー役割にマップされます。

ポリシーにより、さまざまなレベルでアクセス権限を付与できます。 一部のオプションには、以下のアクセス権限が含まれています。

* アカウント内のすべてのサービス・インスタンスに対するアクセス権限
* アカウント内の個別のサービス・インスタンスに対するアクセス権限
* インスタンス内の特定のリソースに対するアクセス権限
* アカウント内のすべての IAM 対応サービスに対するアクセス権限

アクセス・ポリシーの有効範囲を定義した後に、役割を割り当てることができます。

{{site.data.keyword.vmwaresolutions_short}} サービス内で各役割で実行できる操作をまとめた以下の情報を確認してください。

## プラットフォーム管理の役割および許可
{: #iam-roles}

プラットフォーム管理の役割を持つユーザーは、プラットフォーム・レベルでサービス・リソースに対してタスクを実行することができます。 これには、例えば、サービスに対するユーザー・アクセス権限の割り当て、サービス ID の作成または削除、インスタンスの作成、アプリケーションへのインスタンスのバインドなどがあります。

以下の表には、プラットフォーム管理の役割にマップされた操作についての情報が示されています。

表 1. プラットフォーム管理の役割および許可される操作

| プラットフォーム管理の役割 | アクション | 操作の例 |
|:----------------- |:----------------- |:----------------- |
| ビューアー | 読み取り専用の操作 | <ul><li>インスタンスのサマリーの表示</li><li>インスタンスの詳細を表示します</li></ul>|
| エディター | 特定のインスタンスの更新 |<ul><li>ESXi サーバーの追加または削除</li><li>クラスターの追加または削除</li><li>サービスの追加または削除</li><li>インスタンスをより高いバージョンにアップグレードします</li></ul> |
| オペレーター | 読み取り専用の操作 | <ul><li>インスタンスのリスト</li><li>インスタンスの詳細を表示します</li></ul> |
| 管理者 | 完全管理アクセス |<ul><li>新しいインスタンスの作成</li><li>インスタンスの削除</li><li>他のユーザーにプラットフォームのアクセス権限を付与します</li></ul>|

{{site.data.keyword.vmwaresolutions_short}} の場合、以下の操作が存在します。

表 2. 操作の説明と必要な役割

| アクション | サービスに対する操作 | 役割 |
|:------ |:-------------------- |:---- |
| vmware-solutions.instances.create | 新しいインスタンスの作成 | 管理者 |
| vmware-solutions.instances.delete | インスタンスの削除 | 管理者 |
| vmware-solutions.instances.view | <ul><li>インスタンスのリスト</li><li>インスタンスの詳細を表示します</li></ul> | ビューアー、オペレーター、エディター、および管理者 |
| vmware-solutions.instances.update | <ul><li>ESXi サーバーの追加または削除</li><li>クラスターの追加または削除</li><li>サービスの追加または削除</li><li>インスタンスをより高いバージョンにアップグレードします</li></ul> | エディターおよび管理者 |
| vmware-solutions.account.update | アカウント設定の更新 | 管理者 |

## ユーザーのアクセス権限の管理
{: #iam-users}

新しいユーザーを {{site.data.keyword.cloud_notm}} アカウントに追加して、それらのユーザーがアカウントに対してプロビジョンされているサービスやリソースを共有できるようにすることができます。 詳しくは、[サービスとリソースにアクセスするようにユーザーを招待する](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)を参照してください。

既存のユーザーのアクセス権限を管理することもできます。これには、既存のアクセス権限の変更、新しいアクセス権限の割り当て、割り当て済みのアクセス権限の検討などが含まれます。 ユーザーのアクセス権限を管理するには、アカウント所有者であるか、または**「管理者」**のプラットフォーム管理役割を持つ必要があります。 詳しくは、[リソースに対するアクセス権限の管理](/docs/iam?topic=iam-iammanidaccser)を参照してください。

## IBM Cloud アカウントへの既存のインスタンスのマイグレーション
{: #iam-migrate}

{{site.data.keyword.vmwaresolutions_short}} を IAM と統合したために、V2.5 以降のリリースで {{site.data.keyword.cloud_notm}} アカウントにデプロイされたインスタンスは、自動的にアカウントに追加されて IAM によって管理されます。

V2.4 以前のリリースでデプロイされた既存のインスタンスは、IAM 対応の管理のために指定された {{site.data.keyword.cloud_notm}} アカウントにマイグレーションできます。 詳しくは、以下のトピックを参照してください。
* [IBM Cloud アカウントへの V2.5 より前の vCenter Server インスタンスのマイグレーション](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [IBM Cloud アカウントへの V2.5 より前の vCenter Server with Hybridity Bundle インスタンスのマイグレーション](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [V2.5 以前の NetApp ONTAP Select インスタンスの IBM Cloud アカウントへのマイグレーション](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

## 関連リンク
{: #iam-related}

* [ID およびアクセス権限の管理](/docs/iam?topic=iam-getstarted)
* [ユーザーの招待](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [IAM とは](/docs/iam?topic=iam-iamoverview)

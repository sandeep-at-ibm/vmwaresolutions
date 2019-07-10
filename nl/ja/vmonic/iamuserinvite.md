---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: IAM user, invite user, service access

subcollection: vmware-solutions


---

# サービスとリソースにアクセスするようにユーザーを招待する
{: #iamuserinvite}

{{site.data.keyword.vmwaresolutions_full}} は、複数のユーザー間のコラボレーションのために {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) と統合されています。 {{site.data.keyword.cloud_notm}} アカウントを登録して {{site.data.keyword.vmwaresolutions_short}} コンソールにログインした後に、ユーザーを {{site.data.keyword.cloud_notm}} アカウントに追加することができます。 これらの追加されたユーザーは、アカウントに対してプロビジョンされているサービスやリソースを共有することができます。

## 始める前に
{: #iamuserinvite-reqs}

* アカウント所有者であるか、または **VMware Solutions** サービスに対して持っているプラットフォーム管理役割が**「管理者」**であることを確認します。
* [Identity and Access Management でのユーザー・アクセス権限の管理](/docs/services/vmwaresolutions?topic=vmware-solutions-iam#iam)で、ユーザー役割と許可を検討したことを確認します。

## サービスとリソースにアクセスするようにユーザーを招待する手順
{: #iamuserinvite-procedure}

1. バナーの左側の**「管理」>「セキュリティー」>「ID およびアクセス」**をクリックします。
2. **「ユーザー」**ページで、**「ユーザーの招待」**をクリックします。
3. **「ユーザー」**セクションの**「ユーザーの招待」**ページで、招待するユーザーの E メール・アドレスを**「E メール・アドレス」**フィールドに入力します。
4. **「アクセス」**セクションで**「サービス」**を展開してから、以下のタスクを実行します。
   1. **「アクセス権限の割り当て」**リストから**「リソース」**を選択します。
   2. **「VMware ソリューション」**リストから**「サービス」**を選択します。
   3. ユーザーに割り当てるプラットフォーム・アクセス役割を選択します。 これは、**管理者**、**エディター**、**オペレーター**、または**ビューアー**にすることができます。
5. **「ユーザーの招待」**をクリックします。

## 結果
{: #iamuserinvite-results}

追加されたユーザーは、招待を受け入れた後に {{site.data.keyword.vmwaresolutions_short}} コンソールにログインして、招待者のアカウントに切り替えることができます。 これを行うには、ユーザーは、プロファイル設定で {{site.data.keyword.vmwaresolutions_short}} コンソール・バナーにあるユーザー・アカウント・アイコンをクリックします。 これにより、追加されたユーザーは指定のアカウントでコラボレーションを行い、このアカウントで使用可能なサービスとリソースを共有できるようになります。

## 関連リンク
{: #iamuserinvite-related}

* [ユーザーの招待とアクセス権限の割り当て](/docs/iam?topic=iam-iamuserinv)
* [ID およびアクセス権限の管理](/docs/iam?topic=iam-getstarted)
* [ユーザーの招待](/docs/iam?topic=iam-iamuserinv#iamuserinv)
* [IAM とは](/docs/iam?topic=iam-iamoverview)
* [IBM Cloud アカウントへの V2.5 より前の vCenter Server インスタンスのマイグレーション](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addinstancetousraccount)
* [IBM Cloud アカウントへの V2.5 より前の vCenter Server with Hybridity Bundle インスタンスのマイグレーション](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addinstancetousraccount)
* [V2.5 以前の NetApp ONTAP Select インスタンスの IBM Cloud アカウントへのマイグレーション](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_addinstancetousraccount)

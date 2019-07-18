---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: vSphere order cluster, vSphere configuration, order vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 既存の構成を基にした vSphere クラスターの注文
{: #vs_orderingbasedonexistingconfig}

保存した構成テンプレートを基に VMware vSphere クラスターを注文できます。 以下の手順を使用すると、既存のクラスター構成を基に新規クラスター構成を定義できます。

## 要件
{: #vs_orderingbasedonexistingconfig-req}

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
*  [vSphere クラスターの要件と計画](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)に記載されている要件と考慮事項を確認する。
*  再使用する構成テンプレートを作成する。

## 既存の構成を基にした vSphere クラスターを注文する手順
{: #vs_orderingbasedonexistingconfig-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware 仮想データ・センター」**セクションの**「VMware vSphere on IBM Cloud」**カードをクリックします。
2. **「VMware vSphere on IBM Cloud」**ページで、**「作成」**をクリックします。  
3. **「新規作成」**タブをクリックして、**「クラスター構成」**リストから構成テンプレートを選択します。
4. 新規クラスター名を入力します。
5. 自動的に入力されたクラスター設定を確認し、必要に応じてその設定を更新します。 設定について詳しくは、[新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)を参照してください。
6. **「注文のサマリー」**ペインで、インスタンス構成と見積もりコストを確認します。
   * 注文を実行せずに構成をテンプレートとして保存するには、**「構成の保存」**をクリックします。
   * 注文を実行するには、課金されるアカウントが正しいことを確認し、使用条件を確認して承諾してから、**「プロビジョン」**をクリックします。

   {{site.data.keyword.baremetal_short}}だけがインストールされます。 クラスターのデプロイメントの後に、VMware vCenter、VMware NSX、VMware vSAN などの各種コンポーネントをインストールして構成する作業は、お客様が行う必要があります。
   {:note}

## 結果
{: #vs_orderingbasedonexistingconfig-results}

クラスター構成をテンプレートとして保存した場合は、構成が保存されたことを示すコンソール通知を受け取ります。 **「クラスター構成」**リストに、そのテンプレートが表示されます。

注文を実行した場合は、クラスターのデプロイメントが自動的に開始されます。 注文が処理中であることを示す E メール確認を受け取ります。 クラスターが使用可能になったときにも、E メールで通知されます。

vSphere クラスターは、vCenter Server インスタンスとは異なり、**「リソース」**ページに表示されません。
{:note}

## 関連リンク
{: #vs_orderingbasedonexistingconfig-related}

* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [既存の vSphere クラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [コンソール以外で作成されたクラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

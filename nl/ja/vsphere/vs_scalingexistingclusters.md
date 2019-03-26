---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 既存の vSphere クラスターの拡張
{: #vs_scalingexistingclusters}

{{site.data.keyword.vmwaresolutions_full}} コンソールで注文または保存した VMware vSphere クラスターを拡張できます。 これを行うには、ESXi サーバーを追加するか、クラスター用の FortiGate 300 シリーズ Security Appliance の HA ペアを注文します。

## 要件
{: #vs_scalingexistingclusters-req}

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings)を参照してください。
*  [vSphere クラスターの要件と計画](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)に記載されている要件と考慮事項を確認する。
*  拡張対象のクラスターを使用する準備ができたことが、確認の E メールで通知される。

## 既存のクラスターを拡張する手順
{: #vs_scalingexistingclusters-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「VMware vSphere」**をクリックします。
2. **「VMware vSphere on IBM Cloud」**ページで、**「作成」**をクリックします。  
3. **「既存の拡張」**タブをクリックして、拡張するクラスターを**「クラスター構成」**リストから選択します。
4. 自動的に入力されたクラスター設定を確認します。
5. **「{{site.data.keyword.baremetal_short}}」**セクションで、クラスターに追加する{{site.data.keyword.baremetal_short}}の数を指定します。
6. クラスターのパブリック VLAN 上に FortiGate 300 シリーズ Security Appliance の HA ペアが含まれていない場合は、アプライアンスを注文できます。 これを行うには、**「FortiGate Physical Appliance 300 シリーズ HA ペア」**の下の**「購入時に追加」**チェック・ボックスを選択します。
7. **「注文のサマリー」**ペインで、インスタンス構成と見積もりコストを確認します。
   * 注文を実行せずに構成をテンプレートとして保存するには、**「構成の保存」**をクリックします。
   * 注文を実行するには、課金されるアカウントが正しいことを確認し、使用条件を確認して承諾してから、**「プロビジョン」**をクリックします。

### 結果
{: #vs_scalingexistingclusters-results}

クラスターの拡張が自動的に開始されます。 注文が処理中であることを示す E メール確認を受け取ります。 クラスターが使用可能になると、E メールで通知されます。

拡張対象のクラスターを使用する準備ができていない場合は、エラー・メッセージが表示される可能性があります。

vSphere クラスターは、vCenter Server インスタンスや Cloud Foundation インスタンスとは異なり、**「リソース」**ページに表示されません。
{:note}

## 関連リンク
{: #vs_scalingexistingclusters-related}

* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [既存の構成を基にした vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [コンソール以外で作成されたクラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-20"

keywords: vSphere scale cluster, scale vSphere, external vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# コンソール以外で作成されたクラスターの拡張
{: #vs_orderingforclustersoutside}

{{site.data.keyword.vmwaresolutions_full}} コンソール以外で作成された既存の vSphere クラスターを、VMware vSphere オファリングを使用して拡張できます。 コンソール以外で作成された vSphere クラスターを拡張するには、コンソールで同じ設定のクラスターを再作成してから、クラスターを拡張します。

## 要件
{: #vs_orderingforclustersoutside-req}

以下の作業を完了していることを確認してください。
* **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定の管理](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)を参照してください。
* [VMware vSphere on {{site.data.keyword.cloud_notm}} の要件と計画](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)に記載されている要件と考慮事項を確認する。

## コンソール以外で作成されたクラスターを拡張する手順
{: #vs_orderingforclustersoutside-procedure}

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**アイコンをクリックしてから、**「VMware 仮想データ・センター」**セクションの**「VMware vSphere on IBM Cloud」**カードをクリックします。
2. **「VMware vSphere on IBM Cloud」**ページで、**「作成」**をクリックします。  
   **「新規作成」**タブが表示され、**「クラスター構成」**リストに**「新規クラスター」**が表示されていることを確認します。
3. {{site.data.keyword.vmwaresolutions_short}} コンソール以外で作成された既存のクラスターと同じ設定を使用して、クラスターを作成します。 詳しくは、[新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)を参照してください。  
   ネットワーク・インターフェースについては、{{site.data.keyword.vmwaresolutions_short}} コンソール以外で作成されたクラスターを拡張するには、クラスターの既存の VLAN を選択する必要があります。
   {:note}
4. **「注文のサマリー」**ペインで、クラスター構成を確認してから、**「構成の保存」**をクリックします。   
5. **「開始」**ページで、**「VMware vSphere on IBM Cloud」**カードをクリックします。
6. **「VMware vSphere on IBM Cloud」**ページで、**「作成」**をクリックします。
7. **「既存の拡張」**タブをクリックします。 **「クラスター構成」**リストから、最後に作成したクラスターを選択します。
8. **「{{site.data.keyword.baremetal_short}}」**セクションで、クラスターに追加する{{site.data.keyword.baremetal_short}}の数を指定します。
9. クラスターのパブリック VLAN 上に FortiGate 300 シリーズ Security Appliance の HA ペアが含まれていない場合は、**「FortiGate 物理アプライアンス 300 シリーズ HA ペア」**の下の**「購入に含める」**を選択して注文できます。
10. **「注文のサマリー」**ペインで、インスタンス構成と見積もりコストを確認し、課金されるアカウントが正しいことを確認し、使用条件を確認して承諾してから、**「プロビジョン」**をクリックします。

## 結果
{: #vs_orderingforclustersoutside-results}

クラスターのデプロイメントが自動的に開始され、注文が処理中であることを示す E メール確認を受け取ります。 クラスターが使用可能になると、E メールで通知されます。

vSphere クラスターは、vCenter Server インスタンスと一緒に**「リソース」**ページに表示されません。
{:note}

## 関連リンク
{: #vs_orderingforclustersoutside-related}

* [新規 vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [既存の構成を基にした vSphere クラスターの注文](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [既存の vSphere クラスターの拡張](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)

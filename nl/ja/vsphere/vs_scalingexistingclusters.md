---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-11"

---

# 既存の vSphere クラスターの拡張

{{site.data.keyword.vmwaresolutions_full}} コンソールで注文または保存した VMware vSphere クラスターを拡張できます。 これを行うには、ESXi サーバーを追加するか、クラスター用の FortiGate 300 シリーズ Security Appliance の HA ペアを注文します。

## 要件

以下の作業を完了していることを確認してください。
*  **「設定」**ページで {{site.data.keyword.cloud_notm}} インフラストラクチャーの資格情報を構成する。 詳しくは、[ユーザー・アカウントと設定](../vmonic/useraccount.html)を参照してください。
*  [vSphere クラスターの要件と計画](vs_planning.html)に記載されている要件と考慮事項を確認する。

## 手順

1. {{site.data.keyword.cloud_notm}} のカタログで、左側のナビゲーション・ペインの**「VMware」**をクリックしてから、**「仮想データ・センター」**セクションの**「VMware vSphere」**をクリックします。
2. **「VMware vSphere on IBM Cloud」**ページで、**「作成」**をクリックします。  
3. **「既存の拡張」**タブをクリックして、拡張するクラスターを**「クラスター構成」**リストから選択します。
4. 自動的に入力されたクラスター設定を確認します。
5. **「{{site.data.keyword.baremetal_short}}」**セクションで、クラスターに追加する{{site.data.keyword.baremetal_short}}の数を指定します。
6. クラスターのパブリック VLAN 上に FortiGate 300 シリーズ Security Appliance の HA ペアが含まれていない場合は、**「FortiGate 物理アプライアンス 300 シリーズ HA ペア」**の下の**「購入に含める」**を選択して注文できます。
7. **「注文のサマリー」**ペインで、インスタンス構成と見積もりコストを確認します。
   * 注文を実行せずに構成をテンプレートとして保存するには、**「構成の保存」**をクリックします。
   * 注文を実行するには、課金されるアカウントが正しいことを確認し、使用条件を確認して承諾してから、**「プロビジョン」**をクリックします。

### 結果

クラスターの拡張が自動的に開始されます。注文が処理中であることを示す E メール確認を受け取ります。 クラスターが使用可能になると、E メールで通知されます。

**注:** vSphere クラスターは、vCenter Server インスタンスや Cloud Foundation インスタンスとは異なり、**「デプロイ済みインスタンス」**ページに表示されません。

### 関連リンク

* [新規 vSphere クラスターの注文](vs_orderinginstances.html)
* [既存の構成を基にした vSphere クラスターの注文](vs_orderingbasedonexistingconfig.html)
* [コンソール以外で作成されたクラスターの拡張](vs_orderingforclustersoutside.html)

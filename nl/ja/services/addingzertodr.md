---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Zerto on IBM Cloud の概要

Zerto on {{site.data.keyword.cloud}} サービスは、複製と災害復旧の機能を提供します。これらの機能をデプロイメント・オファリングに組み込むことで、{{site.data.keyword.cloud_notm}} 上の VMware 仮想環境内のデータの保護と復旧を行えます。

## Zerto on IBM Cloud サービスのコンポーネント

以下のコンポーネントが注文されて Zerto on {{site.data.keyword.cloud_notm}} サービスに組み込まれます。

* Zerto Virtual Replication Appliance で使用される {{site.data.keyword.cloud_notm}} インフラストラクチャー上のプライベート・ポータブル・サブネット
* Zerto Virtual Replication がインストールされる Microsoft Windows VSI (Virtual Service Instance)
* すべての ESXi サーバーにデプロイされて構成される Zerto Virtual Replication Appliance

**注**: Zerto Virtual Manager (ZVM) コンポーネントはデフォルト・クラスターにのみデプロイされます。


## 関連リンク

* [{{site.data.keyword.vmwaresolutions_short}} について](../vmonic/prod_overview.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の注文](zerto_ordering.html)
* [Zerto on {{site.data.keyword.cloud_notm}} の管理](managingzertodr.html)
* [Zerto on {{site.data.keyword.cloud_notm}} 用マネージド・サービスの要求](managing_zerto_services.html)
* [zerto.com Web サイト](https://www.zerto.com){:new_window}
* [Zerto 技術資料](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

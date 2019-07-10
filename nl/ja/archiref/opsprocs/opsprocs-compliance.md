---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-31"

---

# コンプライアンス
{: #opsprocs-compliance}

コンプライアンスとは、規制機関が定めた最小限の規制または業界のベスト・プラクティスを満たすために必要な一連の要件のことです。 規制機関のコンプライアンスの枠組みは、広範な技術についてのガイダンスを提供する広範な枠組みになることが一般的です。一方、ベンダーが作成する業界のベスト・プラクティスは、技術的なリスクに対処するために特定の技術に固有の内容になることが一般的です。

vCenter Server インスタンスについては、デプロイメント後に専用のチームがセキュリティーを管理することをお勧めします。このように職務を分離して、インスタンスのセキュリティー態勢を強化し、監視する必要があります。 HyTrust CloudControl は、チームで役割ベースの分離を行う際に役立ちます。

HyTrust DataControl と KeyControl は、保存データの暗号化やジオフェンシングなどのワークロード保護を提供するのに役立ちます。コンプライアンスの要件だけでなく、サイバー・リスクやフォレンジックの管理にも役立つ Caveonix RiskForesight サービスをデプロイすることに興味を持っているお客様もいるでしょう。

「VMware Security Hardening Guide」には、VMware 製品を安全な方法でデプロイして運用するための規範的な方法が記載されています。 vSphere に関するガイドは使いやすいスプレッドシート形式で提供されており、ガイドラインの分類やリスク・アセスメントを行えるようにメタデータが豊富に含まれています。また、セキュリティーを自動化できるようにするスクリプトの例も記載されています。 このガイドの一連のバージョンで説明が変更された点をリストした比較文書が提供されています。

「VMware Security Hardening Guide」に記載されている制御の多くは {{site.data.keyword.vmwaresolutions_full}} のリファレンス・アーキテクチャーに組み込まれているので、自動的にデプロイされますが、必ず、お客様独自のニーズや企業ポリシーに合わせて、プラットフォームのセキュリティー態勢を調整してください。 「VMware Security Hardening Guide」には、この検討を行うのに必要な技術固有の制御が記載されています。 {{site.data.keyword.cloud_notm}} 上の Caveonix RiskForesight は、このコンプライアンス作業を自動化し、追加の規制機関のガイダンスを提供します。

vRealize Operations Manager を使用すると、「vSphere Security Configuration Guide」のコンプライアンス規則に照らして VMware オブジェクトの違反をモニターできます。 vCenter Server インスタンス、ホスト、仮想マシン、分散ポート・グループ、分散スイッチについてのコンプライアンス・アラートを起動し、コンプライアンス違反を調査できます。 さらに、医療保険の携行と責任に関する法律 (HIPAA) とクレジット・カード業界データ・セキュリティー基準 (PCI DSS) のコンプライアンスに関心のあるお客様の場合、vRealize Operations Manager のコンプライアンス・パックを VMWare Solutions Exchange の Web サイトからダウンロードし、ライセンスを取得し、インストールできます。 これらのコンプライアンス・パックを導入すると、HIPAA と PCI の Hardening Guide に照らして vSphere リソースを検証するアラート、ポリシー、レポートを利用できます。


## 関連リンク
{: #opsprocs-compliance-links}

* [VMware security hardening guide](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [vSphere security guide](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)

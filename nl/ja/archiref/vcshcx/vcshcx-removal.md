---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-16"

---

# HCX の除去
{: #vcshcx-removal}

HCX を除去するのは、ストレッチ・ネットワークをもう使用しなくなった場合です。 以下の手順を使用して HCX を除去できます。

1. すべてのストレッチ・ネットワークをストレッチ解除します。
2. クライアント・ユーザー・インターフェース (UI) で L2C アプライアンスを削除します。 L2C アプライアンスが Web UI に表示されなくなるまで待ちます。
3. CGW を削除します。 この操作で WAN オプティマイザーも除去されます。 CGW アプライアンスと WAN オプティマイザー・アプライアンスが除去されるまで待ちます。
4. HCX Manager アプライアンスの仮想マシン (VM) をシャットダウンしてクライアント・サイドとクラウド・サイドから削除します。
5. NSX クラウド・サイドから HCX ESG を除去します。
6. vCenter Mob ブラウザーを使用して HCX スナップインを除去します。

## 関連リンク
{: #vcshcx-removal-related}

* [vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle の概要](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

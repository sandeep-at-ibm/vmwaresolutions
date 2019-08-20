---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: SPP management console, apply SPP updates, login SPP console

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# IBM Spectrum Protect Plus on IBM Cloud の管理
{: #managingspp}

## IBM Spectrum Protect Plus 管理コンソールへのアクセス
{: #managingspp-console}

{{site.data.keyword.IBM}} Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスを管理するには、以下のステップを実行して IBM Spectrum Protect Plus 管理コンソールにアクセスする必要があります。
1. {{site.data.keyword.cloud_notm}} インフラストラクチャー VPN またはジャンプ・サーバーを使用して、IBM Spectrum Protect Plus 仮想マシン (VM) の IP アドレスへのアクセスを許可します。 この IP アドレスは、{{site.data.keyword.vmwaresolutions_short}} コンソールの IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のサービスの詳細ページで調べることができます。
2. IBM Spectrum Protect Plus 管理コンソールにアクセスするには、IBM Spectrum Protect Plus on {{site.data.keyword.cloud}} のサービスの詳細ページで**「IBM Spectrum Protect Plus コンソールの表示」**をクリックしてから、同じサービス詳細ページにリストされる資格情報を使用してログインします。

## IBM Spectrum Protect Plus on IBM Cloud への更新の適用
{: #managingspp-updates}

IBM Spectrum Protect Plus を最新バージョンに更新する責任は、ユーザー側にあります。 必要な更新を、[IBM Spectrum Protect Plus サポート](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus){:external}からダウンロードしてください。

詳しくは、[vCenter Server インスタンスのサービスの注文、表示、削除](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)を参照してください。

## IBM Spectrum Protect Plus VM のオペレーティング・システムの更新
{: #managingspp-update-os}

IBM Spectrum Protect Plus VM のオペレーティング・システムを更新するには、**root** ユーザーとしてログインする必要があります。 **root** ユーザーのパスワードは、IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} のサービスの詳細ページにあるパスワードと同じです。

## 関連リンク
{: #managingspp-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} の概要](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations){:new_window}
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/){:external}
* [{{site.data.keyword.cloud_notm}} Object Storage にオフロードするように IBM Spectrum Protect Plus を構成する方法](https://developer.ibm.com/recipes/tutorials/how-to-configure-ibm-spectrum-protect-plus-to-offload-to-ibm-cloud-object-storage/){:external}
* [IBM Spectrum Protect Plus の資料](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html){:external}

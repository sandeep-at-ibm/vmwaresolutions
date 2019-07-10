---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Windows automatic installation, Windows updates

subcollection: vmware-solutions


---

{:faq: data-hd-content-type='faq'}

# その他の制限事項と考慮事項
{: #trbl_limitations}

{{site.data.keyword.vmwaresolutions_full}} を使用する場合は、以下の考慮事項と制限事項を確認してください。

## Windows 更新プログラムの自動インストール
{: #trbl_limitations-windows-update}
{: faq}

Microsoft Active Directory (AD) / ドメイン・ネーム・サーバー (DNS) には、更新プログラムのダウンロードだけが自動的にセットアップされます。 それらの更新プログラムのインストールと再始動は、自動的には行われません。 更新プログラムを手動でインストールし、実行中の AD サーバーの構成ジョブやその他のバックアップ・ジョブが中断されないように計画した時刻に再始動する必要があります。 Windows 更新プログラムを適用するには、手動で更新プログラムをインストールしてください。

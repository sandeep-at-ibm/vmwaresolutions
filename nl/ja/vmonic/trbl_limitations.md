---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# その他の制限事項と考慮事項

{{site.data.keyword.vmwaresolutions_full}} を使用する場合は、以下の考慮事項と制限事項を確認してください。

## Windows 更新プログラムの自動インストール

Microsoft Active Directory (AD) / ドメイン・ネーム・サーバー (DNS) には、更新プログラムのダウンロードだけが自動的にセットアップされます。 それらの更新プログラムのインストールと再始動は、自動的には行われません。 更新プログラムを手動でインストールし、実行中の AD サーバーの構成ジョブやその他のバックアップ・ジョブが中断されないように計画した時刻に再始動する必要があります。 Windows 更新プログラムを適用するには、手動で更新プログラムをインストールしてください。

## Cloud Foundation インスタンスのルート・ドメイン・ネームを選択する際の考慮事項

プライマリーまたはセカンダリー Cloud Foundation インスタンスのデプロイメント時にドメイン・ネームを選択するときは、`ping` または `nslookup` コマンドを使用して、`sddcmanager.<subdomain>` ホスト名が外部ドメインに解決されないことを確認する必要があります。

Cloud Foundation インスタンスのサブドメインの構造は、`<VCF instance name>.<domain name>` です。 例えば、`<domain name>` が `test.local` で、Cloud Foundation インスタンス名が `mytest` である場合、Cloud Foundation インスタンスをデプロイしなければ `sddcmanager.mytest.test.local` ホスト名は IP アドレスに解決されません。 そうでなければ、インスタンスのデプロイメントは失敗する可能性があります。

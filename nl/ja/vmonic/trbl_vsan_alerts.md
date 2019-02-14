---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# 仮想 SAN 正常性のアラートと警告

## 問題
VMware vSphere Web Client の**「モニター」**ページに、仮想 SAN の正常性の問題に関するアラートと警告が表示されることがある。

## 解決方法
これらの警告は問題ではありません。機能的な問題を示すものでもありません。 ただし、vSphere Web Client から警告を消去する場合は、以下の手順を使用してください。

1. http://partnerweb.vmware.com/service/vsan/all.json に移動し、JSON ファイルを `all.json` という名前でローカル・システムに保存します。
2. [vCenter コンソールのタイムアウト](/docs/services/vmwaresolutions/vmonic/trbl_timeout_vc_console.html)の手順を完了したことを確認します。
3. Cloud Foundation インスタンスの詳細ページで、**「vCenter コンソール」**をクリックし、{{site.data.keyword.vmwaresolutions_full}} コンソールに表示される資格情報を使用して vSphere Web Client にログインします。
4. vSphere Web Client で、**「管理」>「設定」**に移動し、**「仮想 SAN」>「健全性」>「HCL データベース」**セクションを開きます。 **「ファイルから更新」**をクリックし、先ほど保存した `all.json` ファイルをアップロードします。
5. 警告を消去するには、vSphere Web Client の右上の**「アラーム」**ペインに移動します。 各アラームを右クリックし、**「緑にリセット」**を選択します。

詳しくは、[How to download offline vSAN HCL file for vSAN Health Check Plugin](http://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window} を参照してください。

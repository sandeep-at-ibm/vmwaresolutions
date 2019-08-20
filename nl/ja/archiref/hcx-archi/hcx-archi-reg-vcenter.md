---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-08"

subcollection: vmware-solutions


---
# vCenter への HCX Manager の登録
{: #hcx-archi-reg-vcenter}

VMware vSphere Web Client でハイブリッド・クラウド・サービス・プラグインを登録し、ハイブリッド・クラウド・サービスの管理サービスを開始します。

## 始める前に
{: #hcx-archi-reg-vcenter-prereq}

登録の前に、ハイブリッド・クラウド・サービス仮想アプライアンスを電源オンにする必要があります。

## HCX Manager を vCenter に登録する手順
{: #hcx-archi-reg-vcenter-proc-register}

1. ハイブリッド・クラウド・サービスのサービス仮想アプライアンスにログインします。 例えば、`https:My-HCX-Manager:9443/` などです。
2. **「ダッシュボード」**パネルで、以下の手順を実行します。
  1. 左のペインの**「システムの構成 (Configure Systems)」**で、vCenter を選択します。
  2. 右上の**「vCenter の追加 (Add vCenter)」**をクリックします。
  3. vCenter Server の IP アドレスを `https:vCenter-host-name` または `https:vCenter-IP-address` という形式で入力します。 例えば、`https:My-vCenter` や `https:10.108.26.211` などです。
  4. vCenter Server のユーザー名とパスワードを入力します。 使用するアカウントには、vCenter 管理者の役割が必要です。
  5. **「OK」**をクリックします。 _「アプリを再始動する必要があります (You need to restart the app)」_ というメッセージが表示された場合は、再始動しないでください。
3. ルックアップ・サービスを構成します。
  1. **「管理」**タブをクリックします。
  2. **「ルックアップ・サービス URL (Lookup Service URL)」**テキスト・ボックスの右端にある**「編集」**ボタンをクリックします。
  3. ルックアップ・ネットワーク・サービス・エンドポイントを次の形式で入力します。
    * vCenter Server 5.5u3 の場合は `https://ssoip:/7444/lookupservice/sdk`
    * vCenter Server 6.0u2 の場合は `https://ssoip/lookupservice/sdk`
  4. **「OK」**をクリックします。 Web エンジンを再始動するメッセージが表示された場合は、再始動しないでください。
4. **「サマリー」**タブをクリックし、**「ハイブリッド管理コンポーネント (Hybridity Management Components)」**セクションを見つけます。 アプリケーション・エンジンと Web エンジンの両方を停止してから始動してください。
5. 登録を確定するには、vSphere Web Client をログアウトします。 もう一度ログインして、画面が更新されたことを確認してください。

## 結果
{: #hcx-archi-reg-vcenter-results}

左側に既存の**「ハイブリッド・クラウド (Hybrid Cloud)」**アイコンと**「ハイブリッド・クラウド・サービス (Hybrid Cloud Services)」**メニュー項目があることに注目してください。 ハイブリッド・クラウド・サービスを登録すると、これらのラベルが更新されます。 インベントリーで、アイコンのラベルが**「ハイブリッド・クラウド・サービス (Hybrid Cloud Services)」**になります。

## 関連リンク
{: #hcx-archi-reg-vcenter-related}

* [ハイブリッド・サービスのインストールおよび構成](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-hybrid)

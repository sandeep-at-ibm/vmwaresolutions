---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# VCSA 更新および SSO がリンクされた vCenter
{: #vum-updating-vcsa}

## PSC および VCSA の更新
{: #vum-updating-vcsa-psc-vcsa-update}

このセクションは、vCentre Server Appliance (VCSA) と Platform Services Controller (PSC) の両方に関係します。 これらのアプライアンスは両方とも VCSA アプライアンスですが、役割が異なります。 外部 PSC を使用する vSphere をアップグレードする場合は、最初に PSC、次に VCSA、次に ESXi ホスト、最後に仮想マシンのハードウェア・バージョンおよび VMware Tools の順にアップグレードします。

VUM は PSC/VCSA を更新しません。 ここでは、それらのアプライアンスを更新するプロセスについて説明します。 VMware vCenter Server on {{site.data.keyword.cloud}} インスタンスにデプロイされた PSC/VCSA はインターネットにアクセスできないため、最初に更新バンドルをジャンプ・サーバーにダウンロードする必要があります。

PSC/VCSA は、vSphere Web Client ではなく、アプライアンス管理コンソールを介して更新されます。 PSC/VCSA アプライアンス管理コンソールには、ブラウザー、PSC/VCSA IP アドレス、およびポート 5480 を使用してアクセスします。

更新する前に、アプライアンスのスナップショットまたは PSC/VCSA のバックアップを開始する必要があります。 すべてが予想どおりに機能することを確認してから、数日以内にスナップショットを削除して、パフォーマンスが低下しないようにします。 さらに、指定されたリリースに対する特定の指示を把握するため、アップグレードを試みる前に VMware リリース・ノートを参照してください。

PSC/VCSA を更新するには、以下の手順を実行します。
1. 更新をダウンロードするには、[VMware パッチのダウンロード・センター](https://www.vmware.com/patchmgr/findPatchByReleaseName.portal)にアクセスし、ログインして**「Search by Product」**メニューから VC を選択します。適切なパッチを選択して、**「Download」**をクリックします。
2. vSphere Web Client を使用して、ISO ファイルを vCenter データ・ストア・リポジトリーにアップロードします。
3. 更新 ISO ファイルを vCenter サーバーにマウントします。
4. vCenter サーバーのスナップショットを取得します。
5. `https://pscip:5480` (PSC の場合) または `https://vcenterip:5480` (VCSA の場合) で、vCenter アプライアンス管理コンソールにログインします。
6. **「Update」**セクションに移動して**「Check Updates」**を選択してから、**「Check CDROM」**を選択します。 更新がリストされます。
7. **「Install Updates」**を選択して、EULA に**同意します**。 更新がインストールされます。
8. 更新が完了したら、アプライアンス管理コンソールに戻り、コンソールの再始動を選択する必要があります。
9. vSphere Web Client に再度ログインし、エラーがないか確認します。 VUM のスキャンを手動で実行し、**「Home」** > **「Hosts and Cluster」**に移動してデータ・センターまたはクラスターを選択し、**「Update Manager」**タブを選択してから**「Scan for Updates」**をクリックします。 手動スキャンでエラーが発生した場合は、[Resetting VMware Update Manager database on a vCenter Server appliance 6.5 (2147284)](https://kb.vmware.com/s/article/2147284) を参照してください。
10. テスト後、バックアウトする必要がある場合は、スナップショットに戻すか、以前のバックアップで vCenter をリストアします。

## SSO がリンクされた vCenter Server インスタンス
{: #vum-updating-vcsa-sso-vcenter}

プライマリー vCenter Server インスタンスおよびセカンダリー vCenter Server インスタンスが存在する場合、VCSA は単一の vCenter シングル・サインオン (SSO) ドメイン内に構成されます。 VCSA ごとに VUM インスタンスがデプロイされます。 変更した構成プロパティーは、指定した VUM インスタンスにのみ適用され、グループ内の他のインスタンスには伝搬されません。

VUM インスタンスを指定するには、VUM インスタンスが登録されている VCSA の名前をナビゲーション・バーから選択します。 また、ベースラインやベースライン・グループを管理することも、VUM インスタンスが登録されている VCSA によって管理されているインベントリー・オブジェクトのみをスキャンおよび修復することもできます。

## 関連リンク
{: #vum-updating-vcsa-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)

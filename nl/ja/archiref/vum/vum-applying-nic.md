---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-07"

subcollection: vmware-solutions


---

# ネイティブ NIC ドライバーの適用
{: #vum-applying-nic}

ESXi 6.5 には、以前の vmklinux ドライバーに置き換わる新しいネイティブ・ドライバーが多数含まれています。 ほとんどの新規ネイティブ・ドライバーは、インストールまたはアップグレード後にデフォルトで有効になっていますが、3 つの新規ネイティブ・ドライバーは、対応する vmklinux ドライバーの機能を完全にはサポートしないため、デフォルトで無効になっています。

ixgben は、vmklinux net-ixgbe ドライバーを置き換えるネイティブ・ドライバーですが、SR-IOV および SW FcOE をサポートしていません。 vSphere ESXi ホストがプロビジョンされたときに、ICVS 自動化機能はこのドライバーを有効にしていないはずです。 パフォーマンスの向上のため、このドライバーを有効にすることをお勧めします。 この付録で説明する以下の手順は、vSphere コマンド・ライン (vCLI) を使用してネイティブ・ドライバーを有効または無効にする方法を示しています。

このタスクを開始する前に、[{{site.data.keyword.cloud}} インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com/devices)からすべての物理ホストの IPMI IP アドレス、ログイン ID、およびパスワードを取得します。 これは、バックアウトの際、またはホストへの直接ネットワーク・アクセスが存在しないアップグレードの進行状況を確認するために必要です。

ホストごとに、連続して以下の手順を実行します。
1. vSphere Web Client を使用して、**「Home」** > **「Hosts and Clusters」**を選択し、vSphere ESXi ホストを保守モードにします。 「Navigator」ペインで vSphere ESXi ホストを選択して右クリックし、**「Maintenance Mode」** > **「Enter Maintenance Mode」**を選択します。 ホストが自動化 DRS クラスターの一部であるため、ホストが保守モードになると、仮想マシンは異なるホストにマイグレーションされます。
2. IBM Cloud for VMware Solutions コンソールからの詳細を使用して、vSphere ESXi ホストに SSH でログインします。
3. 次の vCLI コマンドを実行して、ixgben ネイティブ・ドライバーを有効にします。
`esxcli system module set --enabled=true --module=ixgben`
4. 次の vCLI コマンドを実行して、vSphere ESXi ホストを再始動します。
`system shutdown reboot --reason "Install ixgben driver"`
5. vSphere ESXI ホストが SSH を使用してリブートした後に、ホストに再度ログインし、次の vCLI コマンドを発行し、
ixgben ドライバーが「loaded」(最初の列) および「enabled」(2 番目の列) であることを確認します。
`esxcli system module list |grep ixg`
6. ドライバーが有効な場合、vSphere Web Client を使用して「Navigator」ペインでホストを選択して右クリックし、**「Maintenance Mode」** > **「Exit Maintenance Mode」**を選択します。 次のホストを選択し、すべてのホストが実行されるまでドライバーを有効にします。
7. 変更が機能しない場合は、次のコマンドを実行して戻ります。
`esxcli system module set --enabled=false --module=ixgben`

8. ネットワーク経由でホストに接続できない場合は、{{site.data.keyword.cloud_notm}} コントロール・ウィンドウを使用して、IPMI コンソールから前のコマンドを実行します。
9. vSphere ESXi ホストのリブート後に、ロードされて有効になっているデフォルトの ixgbe ドライバーが表示されます。

戻す必要があり、vSphere ESXi ホストに SSH で接続できない場合は、{{site.data.keyword.cloud_notm}} コントロール・ウィンドウを使用して、戻す必要があるホストの KVM コンソールにログインする必要があります。

{{site.data.keyword.cloud_notm}} コントロール・ウィンドウにリストされている ID とパスワードを IPMI IP アドレスと共に使用して、IPMI Web インターフェースにログインします。 VPN を介してホストが配置されているデータ・センターに接続する必要があります。 詳しくは、[VPN の概要](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started)を参照してください。

1. vSphere ESXi ホストの「デバイスの詳細、リモート管理 (Device Details, Remote Mgmt)」ページに移動し、**「Actions」**>**「KVM Console」**を選択します。 IPMI ユーザーとパスワードを入力するための別のウィンドウが開きます。
2. **「Remote Control」** > **「iKVM/HTML5」**を選択し、**「iKVM/HTML5」**をクリックして再起動します。 これで、vSphere ESXi ホストのコンソールにアクセスできるようになります。
3. ホストがコマンドに応答している場合は、コンソールで **ALT-F1** を使用して ESXi ホスト・コンソールにアクセスします。 ホストの資格情報を使用してログインします。
4. ホストが応答していない場合は、IPMI メニューを使用してホストの電源を入れなおします。
5. ホストの再始動時に HTML5 コンソールを注意深く確認します。 ESXi が再始動すると、リカバリー・モードになるまで数秒しかありません。
6. **CMD+R** キーを同時に押して、リカバリー・モードにします。
7. **"Y"** と入力してリカバリー・モードにし、前のバージョンで ESXi サーバーをブートします。
8. コンソールを使用して進行状況をモニターします。 ブートには、10 分から 20 分かかることがあります。

## 関連リンク
{: #vum-applying-nic-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_full}} デモ](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (デモンストレーション)

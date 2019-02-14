---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# インストール環境の準備

VMware HCX on IBM Cloud のインストールのソフトウェア要件は、以下のとおりです。
* vSphere 5.5 U3、または vSphere 6.0u2 以上。
* NSX を使用する場合は、バージョン 6.2.2 以上。 ポリシーのマイグレーションには NSX が必要です。
* クラウド間 vMotion を使用する場合は、オンプレミスの場合と同じアフィニティーの制限がクラウド間にも適用されます。 詳しくは、[VMware EVC and CPU Compatibility FAQ](http://bit.ly/2vK6Sp5) を参照してください。

## ネットワーク接続の構成

HCX は、公衆インターネットと専用回線を経由して、ネットワーク、スイッチ、ポート・グループなどのデータ・センターのコンポーネントに接続する必要があります。
* [ポートのアクセス要件](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-port-req.html)に、HCX 仮想アプライアンスを正常にインストールするために開く必要があるポートをリストしています。
* オンプレミス vSphere 環境と VCF/VCS HCX クラウド環境の両方で、vSphere オンプレミス・デバイスと VCF/VCS HCX デバイスが Network Time Protocol (NTP) のクロック同期を実行できなければなりません。 UDP ポート 123 に、HCX の仮想アプライアンスとネットワークがアクセスできる必要があります。

## オンプレミス環境

HCX をインストールする前に、実行したいタスクがサポートされる環境であることを確認してください。 HCX をインストールするには、オンプレミス環境が、以下のタスクをサポートする環境でなければなりません。
* vSphere 5.5 Update 3 または 6.0 Update 2 の仮想センター。
* vMotion およびポリシー・マイグレーション機能を使用するには、NSX バージョン 6.2.2 以上が必要です。
* vCenter Server システムの管理者の役割を割り当てられた vSphere サービス・アカウント。
* HCX アプライアンスをインストールするための十分なディスク・スペースが vCenter 内にあること。
* インストール中にプロビジョンされるオンプレミス VM 用の十分な IP アドレス。
* 『ポートのアクセス要件』に必要なものとして記載しているポートおよびファイアウォールが開かれていること。
* シングル・サインオン (SSO) サーバーがリモートにある場合は、外部ルックアップ・サービスを実行する vCenter、外部 SSO サーバー、または Platform Services Controller (PSC) の URL を確認する必要があります。 HCX Manager を vCenter に登録するときに、この URL を指定する必要があります。
* vCenter の内部に独自のルックアップ・サービス・インスタンスがない理由としては、以下のいずれかの理由が考えられます。
  * vCenter 6.0u2 が外部 Platform Services Controller を実行している。
  * vCenter がリンク・モードになっている (この場合、2 次 vCenter は 1 次 vCenter の SSO サービスまたは外部 SSO サービスを使用します)。

## レイヤー 2 インストール環境の確認

レイヤー 2 ネットワーク拡張には、次の要件があります。
* vSphere Enterprise Plus エディション。
* レイヤー 2 拡張をサポートするためには、vSphere vCenter が以下の要件を満たしている必要があります。
  * vSphere Enterprise Plus ライセンス
  * vSphere 分散スイッチ (vDS) を備えていること。 分散スイッチは、vSphere Enterprise Plus エディションで提供されます。
  * インストールする場合、オンプレミスのレイヤー 2 コンセントレーター・サービス・アプライアンスは、拡張する vNIC ポートと VLAN にアクセスできなければなりません。
  * 公衆インターネットまたは VPN を経由して (別のパスの) ネットワークを拡張する場合は、VCF/VCS 内の L2C 仮想マシンに IP アドレスが必要です。 そのリモート IP アドレスを使用して、レイヤー 2 コンセントレーターを構成する必要があります。
  * 複数台のレイヤー 2 コンセントレーターが必要な場合は、L2C ごとにオンプレミスとクラウドの両方の IP アドレスが必要です。

### 関連リンク

* [ソースでの HCX の構成およびインストール](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-install-cfg-src.html)
* [VMware EVC and CPU Compatibility FAQ](http://bit.ly/2vK6Sp5)

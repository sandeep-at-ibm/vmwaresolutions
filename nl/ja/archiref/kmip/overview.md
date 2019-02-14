---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware の概要

このソリューションのアーキテクチャーは、VMware on {{site.data.keyword.cloud_notm}} インスタンスを保護するための KMIP on VMware アーキテクチャーについてのものです。 VMware ワークロードを保護するためのストレージ暗号化オプションは多数存在します。 KMIP for VMware は、VMware のネイティブの vSphere 暗号化および vSAN 暗号化と連携してシンプルなストレージ暗号化管理を実現するうえに、{{site.data.keyword.cloud_notm}} Key Protect でユーザーが鍵を管理できるようにしてセキュリティーと柔軟性も提供します。

**注**: このリリースでは、KMIP for VMware on {{site.data.keyword.cloud_notm}} は vSphere 暗号化のみに限定されています。

このソリューションは、{{site.data.keyword.cloud_notm}} の vCenter Server と VMware Cloud Foundation の両方のソリューション・オファリングに対する追加コンポーネントであり、拡張機能と見なされます。 そのため、この資料では {{site.data.keyword.cloud_notm}} のこれらの基盤ソリューションの既存構成については説明しません。 基盤ソリューションのアーキテクチャーの詳細については、[VMware on {{site.data.keyword.cloud_notm}} のソリューション・アーキテクチャー](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)を参照してください。

## 主な利点

VMware ワークロードのためのストレージ暗号化ソリューションは多数存在しますが、KMIP for VMware には以下の利点があります。

* VMware の vSAN 暗号化および vSphere 暗号化と一体化する。どちらの暗号化もストレージ層や仮想マシン層ではなくハイパーバイザー層で実施されます。 この手法により、ストレージ・ソリューションやアプリケーションで意識することなく、簡単な管理が可能になります。
* 多数の IBM Cloud マルチゾーン領域 (MZR) で提供されているフルマネージドの鍵管理サーバー。
* VMware クラスターが IBM Cloud Key Protect と一体化するので、完全にユーザーが鍵を管理できる。ユーザーはいつでも鍵を無効化できます。

### 関連リンク

* [ソリューションの設計](/docs/services/vmwaresolutions/archiref/kmip/design.html)
* [実装と管理](/docs/services/vmwaresolutions/archiref/kmip/implementation.html)

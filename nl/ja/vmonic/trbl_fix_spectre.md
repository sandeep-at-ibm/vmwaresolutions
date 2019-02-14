---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Spectre および Meltdown 脆弱性への対処

Spectre および Meltdown 脆弱性に対処するには、いくつかのパッチを特定の順序で適用する必要があります。

## ファームウェアを更新する

ファームウェアの更新に関する最新情報については、[最近のセキュリティー脆弱性に対する保護](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)を参照してください。

## V2.0 以降でデプロイしたインスタンスを更新する

V2.0 以降のインスタンスは、VMware vSphere 6.5 および VMware vCenter Server 6.5 と一緒にデプロイされています。 これらのソフトウェア・コンポーネントはどちらもパッチ適用が必要です。

### V2.0 以降でデプロイされた vCenter Server インスタンス

#### VMware vSphere 6.5 について

* すべての新しい V2.6 インスタンスでは、次のパッチが適用された vSphere がデプロイされます: ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG、および ESXi650-201808403-BG。
* V2.5 より前にデプロイしたすべての既存のインスタンスでは、すべての新しいクラスターと ESXi サーバーは、次のパッチで更新されます: ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG、および ESXi650-201808403-BG。
* すべての既存の ESXi サーバー、および V2.5 にアップグレードする前にデプロイを続けるすべてのクラスターまたは ESXi サーバーには、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手した次のパッチを適用する必要があります: ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG、および ESXi650-201808403-BG。

#### VMware vCenter Server 6.5 について

* すべての新しい V2.6 インスタンスでは、vCenter 6.5 U2c 累積パッチが適用された vCenter Server がデプロイされます。
* V2.6 より前にデプロイしたすべての既存のインスタンスに、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手した vCenter 6.5 U2c パッチを適用する必要があります。

### V2.0 以降でデプロイされた Cloud Foundation インスタンス

VMware vSphere 6.5 および VMware vCenter Server 6.5 に必要なパッチを適用するには、Cloud Foundation インスタンスを最新の VMware パッチ・バンドルにアップグレードする必要があります。 既存のすべてのインスタンスと ESXi サーバーでは、{{site.data.keyword.vmwaresolutions_full}} コンソールの**「更新およびパッチ」**ページに、パッチを適用するようプロンプトが出されます。 詳しくは、[Cloud Foundation インスタンスへの更新の適用](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)を参照してください。

### V2.0 以降でデプロイされた VMware vSphere クラスター

新しいすべての VMware vSphere 6.5 クラスターおよび ESXi サーバーでは、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手したパッチ ESXi650-201808401-BG、ESXi650-201808402-BG、および ESXi650-201808403-BG を適用する必要があります。

既存のすべての VMware vSphere 6.5 クラスターでは、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手したパッチ ESXi650-201712101-SG、ESXi650-201803401-BG、ESXi650-201803402-BG、ESXi650-201808401-BG、ESXi650-201808402-BG、および ESXi650-201808403-BG を適用する必要があります。

VMware vCenter Server 6.5 では、新しくデプロイするものも既存のものも含め、すべての vCenter サーバーに、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手した vCenter 6.5 U2c パッチを適用する必要があります。

## V1.9 以前でデプロイされたインスタンス

V1.9 以前での Cloud Foundation インスタンス、vCenter Server インスタンス、および VMware vSphere クラスターは、VMware vSphere 6.0 と VMware vCenter Server 6.0 とともにデプロイされています。

### V1.9 以前でデプロイされた vCenter Server インスタンス

VMware vSphere 6.0 と VMware vCenter Server 6.0 では、新しくデプロイするものも既存のものも含め、すべてのインスタンスと ESXi サーバーに、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手したパッチ (vSphere 用の ESXi600-201711101-SG、ESXi600-201803401-BG、ESXi600-201803402-BG、ESXi600-201808401-BG、ESXi600-201808402-BG、および ESXi600-201808403-BG と vCenter Server 用の vCenter 6.0 U3h) を適用する必要があります。

### V1.9 以前でデプロイされた Cloud Foundation インスタンス

これらのインスタンスは、これらのインスタンスが依存しているベンダーの更新がリリースされたら、更新可能になります。

### V1.9 以前でデプロイされた VMware vSphere クラスター

VMware vSphere 6.0 と VMware vCenter Server 6.0 では、新しくデプロイするものも既存のものも含め、すべての vSphere クラスターと ESXi サーバーに、[VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)から入手したパッチ (vSphere 用の ESXi600-201711101-SG、ESXi600-201803401-BG、ESXi600-201803402-BG、ESXi600-201808401-BG、ESXi600-201808402-BG、および ESXi600-201808403-BG と vCenter Server 用の vCenter 6.0 U3h) を適用する必要があります。

### 関連リンク

* [Cloud Foundation インスタンスへの更新の適用](/docs/services/vmwaresolutions/sddc/sd_applyingupdates.html)
* [最近のセキュリティー脆弱性に対する保護](https://www.ibm.com/blogs/bluemix/2018/01/ibm-cloud-spectre-meltdown-vulnerabilities/)
* [VMware 製品パッチ・サイト](https://my.vmware.com/group/vmware/patch)

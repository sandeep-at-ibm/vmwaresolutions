---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, secondary vCenter, vSphere inventory issue

subcollection: vmware-solutions


---

# vSphere Web Client のインベントリーにセカンダリー vCenter Server システムが表示されない
{: #trbl_sec_inst_not_visible}

## 問題
{: #trbl_sec_inst_not_visible-problem}

マルチサイト構成で、新しいセカンダリー・インスタンスを追加した後に、前に注文したインスタンスの VMware vSphere Web Client にログインしても、新しいセカンダリー・インスタンスの vCenter Server システムが表示されない。

## 解決方法
{: #trbl_sec_inst_not_visible-resolution}

これは VMware 6.5 の既知の問題です。

この問題を解決するには、以下のようにして vSphere Web Client を再始動する必要があります。

1. **root** アカウントを使用して、前に注文したインスタンスの vCenter VM (仮想マシン) に **ssh** を介して接続します。
2. ``shell`` と入力して bash シェルに入ります。
3. `service-control --stop vsphere-client` と入力してクライアントを停止します。
4. `service-control --start vsphere-client` と入力してクライアントを再始動します。
5. 前に注文したインスタンスの vSphere Web Client が再始動されたら、新しく追加したセカンダリー・インスタンスの vCenter Server システムが vSphere Web Client に表示されていることを確認します。

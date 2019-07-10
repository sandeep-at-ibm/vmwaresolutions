---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-28"

keywords: troubleshooting, Zerto VRA, Zerto uninstall

subcollection: vmware-solutions


---

# Zerto on IBM Cloud のアンインストール後に ESXi ホストの vCenter コンソールで Zerto VRA が表示される
{: #trbl_zerto_vra}

## 問題
{: #trbl_zerto_vra-problem}

{{site.data.keyword.slportal}}を使用して Zerto on {{site.data.keyword.cloud}} サービスを正常にアンインストールしたのに、Zerto Virtual Replication Appliances (VRA) が削除されません。

## 解決方法
{: #trbl_zerto_vra-resolution}

vCenter コンソールから VRA を手動で削除します。

1. vCenter コンソールにログインします。
2. **「ホストとクラスター (Hosts and Clusters)」**をクリックして、**Z-VRA-** で始まる名前の仮想マシンを見つけます。 例えば、**Z-VRA-host0-vcs40dal.vcs.icvs.org** です。
3. **Z-VRA-** 仮想マシンを右クリックして、**「ディスクから削除 (Delete from Disk)」**をクリックします。

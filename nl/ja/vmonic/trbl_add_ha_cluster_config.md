---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: troubleshooting, vSphere configuration issue, HA cluster issue

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# HA クラスターを追加するときに vSphere コンソールに構成の問題が表示される
{: #trbl_add_ha_cluster_config}

## 問題
{: #trbl_add_ha_cluster_config-problem}

ファイル共有が 1 つだけの HA (高可用性) クラスター構成を追加すると、次の構成上の問題が ESXi ホストに表示されます。

> The number of heartbeat datastores for host is 1, which is less than required: 2

## 解決方法
{: #trbl_add_ha_cluster_config-resolution}

この問題は、共有ストレージが冗長化されていないためにデータ・ストアのハートビートを実行できない場合に発生します。

詳細と問題解決手順については、[HA error: The number of heartbeat data stores for host is 1, which is less than required: 2 (2004739)](https://kb.vmware.com/s/article/2004739) を参照してください。{:external}

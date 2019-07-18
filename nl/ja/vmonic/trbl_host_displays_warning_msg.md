---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-26"

keywords: troubleshooting, configuration issue, ESXi server issue

subcollection: vmware-solutions


---

{:external: target="_blank" .external}

# ESXi サーバーに構成の問題が表示される
{: #trbl_host_displays_warning_msg}

## 問題
{: #trbl_host_displays_warning_msg-problem}

vSphere クライアントで、VMware ESXi サーバーの**「モニター」**タブの**「問題」**タブに、構成の問題が表示されます。

ESXi サーバーの**「問題」**タブに、次のメッセージが表示されます。

`This host currently has no management network redundancy`

このメッセージは、プライベート分散スイッチのアップリンクが 2 つ使用可能で、冗長化されていても表示されます。

## 解決方法
{: #trbl_host_displays_warning_msg-resolution}

これは VMware の既知の問題です。 この問題を解決するには、[ESX/ESXi host displays warning message when test condition is false (2008602)](https://kb.vmware.com/s/article/2008602) の説明に従ってください。{:external}

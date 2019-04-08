---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:faq: data-hd-content-type='faq'}

# 更多限制和注意事项
{: #trbl_limitations}

使用 {{site.data.keyword.vmwaresolutions_full}} 时，请查看以下注意事项和限制。

## Windows 自动安装更新
{: #trbl_limitations-windows-update}
{: faq}

Microsoft Active Directory (AD) / 域名服务器 (DNS) 自动设置为仅下载更新。它不会自动安装这些更新或重新启动。您必须在安排的时间手动安装更新并重新启动，以避免对正在进行的 AD 服务器配置和其他备份作业造成任何中断。要应用 Windows 更新，请手动安装更新。

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

{:faq: data-hd-content-type='faq'}

# 其他限制及考量
{: #trbl_limitations}

使用 {{site.data.keyword.vmwaresolutions_full}} 時，請檢閱下列考量和限制。

## Windows 自動安裝更新
{: #trbl_limitations-windows-update}
{: faq}

Microsoft Active Directory (AD) / 網域名稱伺服器 (DNS) 自動設定為只下載更新。它不會自動安裝這些更新或重新啟動。您必須在排定的時間手動安裝更新並重新啟動，以避免中斷進行中的 AD 伺服器配置及其他備份工作。若要套用 Windows 更新，請手動安裝更新。

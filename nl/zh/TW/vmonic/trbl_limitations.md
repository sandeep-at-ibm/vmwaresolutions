---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 其他限制及考量

使用 {{site.data.keyword.vmwaresolutions_full}} 時，請檢閱下列考量和限制。

## Windows 自動安裝更新項目

Microsoft Active Directory (AD) / 網域名稱伺服器 (DNS) 自動設定為只下載更新項目。它不會自動安裝這些更新項目或重新開機。您必須在排定的時間手動安裝更新項目並重新開機，以避免中斷進行中的 AD 伺服器配置及其他備份工作。若要套用 Windows 更新項目，請手動安裝更新項目。

## 選擇 Cloud Foundation 實例的根網域名稱時的考量

在主要或次要 Cloud Foundation 實例的部署期間選擇網域名稱時，您需要使用 `ping` 或 `nslookup` 指令，來驗證 `sddcmanager.<subdomain>` 主機名稱未解析成外部網域。

Cloud Foundation 實例子網域的結構為 `<VCF instance name>.<domain name>`。例如，如果您的 `<domain name>` 是 `test.local`，而 Cloud Foundation 實例名稱是 `mytest`，則在部署 Cloud Foundation 實例之前，`sddcmanager.mytest.test.local` 主機名稱不得解析成 IP 位址。否則，實例部署可能會失敗。

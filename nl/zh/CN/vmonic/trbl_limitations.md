---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# 其他限制和注意事项

使用 {{site.data.keyword.vmwaresolutions_full}} 时，请查看以下注意事项和限制。

## Windows 自动安装更新

Microsoft Active Directory (AD) / 域名服务器 (DNS) 自动设置为仅下载更新。不会自动安装这些更新或重新引导。您必须以手动方式安装更新并在安排的时间重新引导，以避免对正在进行的 AD 服务器配置和其他备份作业造成任何中断。要应用 Windows 更新，请手动安装更新。

## 选择 Cloud Foundation 实例的根域名时的注意事项

在部署主或辅助 Cloud Foundation 实例期间选择域名时，需要使用 `ping` 或 `nslookup` 命令来验证 `sddcmanager.<subdomain>` 主机名是否不会被解析为外部域。

Cloud Foundation 实例子域的结构为 `<VCF instance name>.<domain name>`. 例如，如果 `<domain name>` 为 `test.local`，并且 Cloud Foundation 实例名称为 `mytest`，那么在部署 Cloud Foundation 实例之前，`sddcmanager.mytest.test.local` 主机名不应解析为 IP 地址。否则，实例部署可能会失败。

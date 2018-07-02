---

copyright:

  years:  2016, 2018

lastupdated: "2017-06-29"

---

# ESXi 服务器显示配置问题

## 问题
在 vSphere Client 中 VMware ESXi 服务器的**监视**选项卡的**问题**选项卡中显示了配置问题。

ESXi 服务器的**问题**选项卡中显示了以下消息：

`此主机当前没有管理网络冗余`

尽管有两个可用上行链路用于专用分布式交换机（提供了冗余），仍然显示了此消息。

## 解决方法
这是 VMware 的已知问题。要解决此问题，请遵循[当测试状况为 false 时，ESX/ESXi 主机显示警告消息 (2101965)](https://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2008602){:new_window} 中的指示信息。

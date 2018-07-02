---

copyright:

  years:  2016, 2018

lastupdated: "2018-01-03"

---

# 辅助 vCenter Server 系统未显示在 vSphere Web Client 库存中

## 问题

在多站点配置中，添加新的辅助实例后，当登录到先前所订购实例的 VMware vSphere Web Client 时，不显示该实例的 vCenter Server 系统。

## 解决方法

这是 VMware 6.5 的已知问题。

要解决此问题，必须重新启动 vSphere Web Client：

1. 使用 **root** 用户帐户，通过 **ssh** 连接到先前所订购实例的 vCenter VM（虚拟机）。
2. 输入 ``shell`` 以进入 bash shell。
3. 输入 `service-control --stop vsphere-client` 以停止该客户机。
4. 输入 `service-control --start vsphere-client` 以重新启动该客户机。
5. 重新启动先前所订购实例的 vSphere Web Client 后，请确认 vSphere Web Client 中是否显示新添加的辅助实例的 vCenter Server 系统。

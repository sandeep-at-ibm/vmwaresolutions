---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---
# 关于 HCX on IBM Cloud 的故障诊断

## 云注册失败

* 如果凭证不正确，Hybrid Cloud Services 不会重试。在 Hybrid Cloud Services 尝试登录并启动云注册之前，凭证必须进行认证。
* 如果凭证输入错误，或者如果在 Hybrid Cloud Services 向 VCF/VCS Hybrid Cloud Services Cloud 注册后更改了 VCF/VCS Hybrid Cloud Services Cloud 凭证，而导致凭证不匹配，那么云注册会失败。
* 要在 Web Client 中更新凭证，请转至“Hybrid Cloud Services 入门”选项卡，然后在**基本任务**下，选择**注册新云**。

## MAC 地址重复

迁移后，虚拟机之间可能会存在通信问题。在迁移期间保留 MAC 地址时，可能会无意中创建重复的 MAC 地址。

可以更改已迁移虚拟机的 MAC 地址来解决此问题。

1. 在 vSphere Client 中，关闭虚拟机的电源。
2. 在清单中，右键单击虚拟机，并从菜单中选择**编辑设置**。
3. 在**虚拟硬件**选项卡上，展开“网络适配器”。
4. 在“MAC 地址”文本框旁边，从菜单中选择**手动**。
5. 指定唯一的 MAC 地址，然后单击**确定**。
6. 检查以确定唯一的 MAC 地址是否解决了通信问题。

## 主机资源消耗量高

在极少数情况下，如果所有服务虚拟设备都位于同一主机上，那么 Hybrid Cloud Services 服务虚拟机可能会耗尽主机的 CPU 和磁盘资源。

将所有虚拟设备安装在一个物理主机上时，有些用户会看到此问题。对于此配置，如果以下情况同时发生，性能会下降：
* 网络的等待时间长和/或有丢包现象。使用公用因特网或繁忙网络时，迁移或数据传输速度很慢。
* WAN Optimizer 在耗用带宽来加密和压缩（或解密和解压缩）大型工作负载。
* 内部部署 VM 与已迁移 VM 之间存在高应用程序流量。

要解决此问题，请执行以下步骤：

1. 在更改数据中心配置之前，请查看稳态支持人员的需求。
2. 如果资源即将耗尽，请联系稳态支持人员。他们可以建议如何以最短的停机时间重新配置环境。

### 相关链接

* [向 vCenter 注册 HCX Manager](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-reg-vcenter.html)
* [修改或卸载 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi/hcx-archi-mod-uninstall.html)

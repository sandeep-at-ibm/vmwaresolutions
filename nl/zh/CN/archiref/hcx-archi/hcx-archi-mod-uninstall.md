---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 修改或卸载 HCX
{: #hcx-archi-mod-uninstall}

可以升级现有安装，也可以除去部分或全部 Hybrid Cloud Services 部署。

##  取消延伸第 2 层网络
{: #hcx-archi-mod-uninstall-unstretch-layer2}

必须先取消延伸第 2 层网络，然后才能除去关联的第 2 层集中器服务虚拟设备或卸载 Hybrid Cloud Services。

1. 检查延伸网络。
2. 在 Hybrid Cloud Services 插件页面中，查看“混合服务”选项卡，然后选中“Network Extension 服务”部分。如果正在执行活动作业或安排的作业，请等待作业完成或停止这些作业，然后再继续。
3. 要除去网络，请单击右侧的“删除”（红色 X）图标。
4. 单击**确定**以确认。

## 卸载 HCX 虚拟设备
{: #hcx-archi-mod-uninstall-uninst-hva}

为了准备好卸载 Hybrid Cloud Services，或者因为安装体系结构中发生更改，可能需要卸载服务设备。请使用 Hybrid Cloud Services 来管理设备，如以下过程所概述。

### 卸载 HCX 虚拟设备的先决条件
{: #hcx-archi-mod-uninstall-prereq-uninst-hva}

* 取消或重置卸载任务期间可能发生的任何迁移的执行时间。
* 检查 vSphere Web Client 任务控制台中是否有任何迁移正在运行，如果有，请等待迁移完成。
* 确保没有任何类型的活动 Hybrid Cloud Services 任务。

切勿从 vSphere 清单中删除虚拟设备。请始终使用管理门户网站与服务虚拟设备进行交互。
{:note}

### 卸载 HCX 虚拟设备的过程
{: #hcx-archi-mod-uninstall-proc-uninst-hva}

1. 在 VMware vSphere Web Client 界面的左窗格中，选择 Hybrid Cloud Services 插件。
2. 在中央窗格中，单击**混合服务**选项卡。
3. 找到 Hybrid Cloud Gateway 设备，然后单击该条目以显示详细信息。
4. 单击右下角的“删除”图标以除去该设备。
5. 如果延伸网络与 Hybrid Cloud Gateway 不共享 IP 地址，那么必须单独将其除去。展开 Network Extensions 服务详细信息，然后单击“删除”图标以除去第 2 层集中器。

Hybrid Cloud Gateway 和使用 Hybrid Cloud Gateway 的任何混合服务虚拟设备都将从 vCenter 和 VCF/VCS Hybrid Cloud Services Cloud 中除去。

## 卸载 HCX Manager
{: #hcx-archi-mod-uninstall-unist-hcxm}

在从内部部署数据中心除去 HCX 解决方案之前，应先卸载 HCX Manager 设备。执行以下步骤来卸载 Hybrid Cloud Services 虚拟机。

1. 取消延伸所有第 2 层网络。
2. 除去混合服务虚拟设备。
3. 在内部部署 vCenter 中，关闭 Hybrid Cloud Services 虚拟机的电源。
4. 删除 Hybrid Cloud Services 虚拟机。

这将除去所有虚拟服务设备。但可能会保留以下元素：
* 日志
* 已迁移的 VM

### 后续步骤
{: #hcx-archi-mod-uninstall-what-next}

可以手动备份或删除已迁移的 VM 和日志。

## 登录到 HCX 管理门户网站
{: #hcx-archi-mod-uninstall-log-hcxmp}

可以使用基于浏览器的用户界面通过管理门户网站来管理 Hybrid Cloud Services 部署。

1. 在 Web 浏览器中，输入分配给 Hybrid Cloud Services 的 IP 地址，并指定端口号 9443。例如，`https://HCXip:9443`。
2. Hybrid Cloud Services 用户界面使用 SSL 在 Web 浏览器窗口中打开。如果需要，请接受安全证书。这将打开 VMware Hybridity and Networking 登录屏幕。
3. 输入用户名和密码。缺省情况下，用户名为 Admin。密码是安装 Hybrid Cloud Services 虚拟设备时提供的值。

## 相关链接
{: #hcx-archi-mod-uninstall-related}

* [关于 HCX on IBM Cloud 的故障诊断](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-trbl)

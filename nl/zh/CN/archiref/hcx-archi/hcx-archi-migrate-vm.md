---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 迁移虚拟机
{: #hcx-archi-migrate-vm}

HCX 支持双向迁移：从内部部署迁移到云，或从云迁移到内部部署数据中心。HCX 在迁移过程中使用复制技术。复制技术集成在 Hybrid Cloud Gateway 虚拟设备中。无需安装其他复制软件。

## 短停机时间迁移

短停机时间迁移使用基于主机的复制，将活动虚拟机从 vCenter 迁移到虚拟数据中心，或者从虚拟数据中心迁移到 vCenter。为了减少停机时间，源 VM 在复制期间保持联机状态，在复制完成后会在目标 ESX 主机上进行引导。

1. 迁移请求会触发以下操作：
  * 首先，复制会执行到 VCF/VCS HCX 虚拟数据中心的完全同步传输。复制所需的时间取决于 VM 大小和可用带宽。
  * 复制带宽消耗量根据工作负载如何更改磁盘上的块而变化。
2. 完全同步完成后，将执行增量同步。
3. 增量同步完成时，HCX 会触发转换。转换可以立即启动，也可以安排在特定时间执行。
4. 执行转换后，源 VM 的电源关闭，已迁移副本的电源会打开。如果出于某种原因 VM 无法打开电源，那么新 VM 的电源关闭（或保持电源关闭状态），而原始 VM 的电源会打开。
5. HCX 对已关闭电源的原始 VM 重命名，以避免与已迁移 VM 发生命名冲突，并将二进制时间戳记附加到原始 VM 名称。
6. 如果 HCX 未指定为启用**保留 MAC**，那么已迁移 VM 会获取新 MAC 地址。
7. 迁移完成。Hybrid Cloud Services 会将原始 VM 复制到“vSphere 模板”视图中的**已迁移 VM** 文件夹中。

## 零停机时间 vMotion
{: #hcx-archi-migrate-vm-no-downtime-vm}

vMotion 将活动虚拟机从 vSphere vCenter 传输到 VCF/VCS Cloud。此 vMotion 需要延伸网络。vMotion 传输会捕获虚拟机的活动内存、执行状态、IP 地址和 MAC 地址。

虚拟机硬件版本必须至少为 V9，否则跨云 vMotion 可能会失败。
{:note}

## 冷迁移
{: #hcx-archi-migrate-vm-cold-mig}

冷迁移使用与跨云 vMotion 相同的数据平面，通过扩展网络来传输已关闭电源的虚拟机。虚拟机的 IP 地址和 MAC 地址会保留。虚拟机的需求和限制与 vMotion 的相同。

### 使用双向向导迁移 VM
{: #hcx-archi-migrate-vm-mig-bidir-wiz}

通过使用 vSphere Web Client，可以在“Hybrid Cloud Services 入门”选项卡中访问双向迁移向导。此向导处理所有迁移详细信息，包括多个虚拟机。

在 vSphere Web Client 中的“Hybrid Cloud Services 入门”选项卡中，可以访问双向迁移向导。此向导处理所有迁移详细信息，包括多个虚拟机。
* 从 vSphere 迁移到 VCF/VCS Hybrid Cloud Services
* 从 VCF/VCS HCX Cloud 迁移到 vSphere

### 迁移前检查 VM
{: #hcx-archi-migrate-vm-check-vms}

要迁移虚拟机，需要由 Hybrid Cloud Gateway 维护的安全连接，并且 VM 必须满足以下需求：
* 虚拟机电源必须已打开。
* 无论使用哪种操作系统，底层体系结构都必须是 x86。
* 要使用 vMotion 迁移，硬件版本必须高于 9。
* 硬件版本必须低于 10。
* 可以迁移兼容性方式下使用原始磁盘映射的 VM。

不支持迁移具有以下属性的 VM：
* 超过 2 TB。
* 共享 VMDK 文件。
* 连接有虚拟介质或 ISO。
* 硬件版本低于 9。

### 监视迁移
{: #hcx-archi-migrate-vm-monitor-mig}

可以通过用户界面或命令行来监视基于复制的迁移的进度。查看任务控制台（如“监视服务设备部署”中所述），并查找**迁移 VM** 任务。状态为**完成**时，说明 VM 已迁移并已打开电源。

以下过程使用同一 vCenter 中的不相关 VM 来跟踪所迁移 VM 的进度。

1. 确定要迁移的 VM，然后选择可以对迁移 VM 执行 ping 操作的观察者 VM。
2. 在用户界面中，开始迁移 VM，并通过任务控制台监视该 VM。
3. 使用 SSH 登录到运行观察者 VM 的 ESXi 主机。
4. 运行以下命令以获取 VM 标识 (vmid)：

  ```
  # vim-cmd vmsvc/getallvms | grep -i vmname 5
  ```

5. 运行以下命令以监视复制状态，其中 vmid 是在上一步中获得的值：

  ```
  # vim-cmd hbrsvc/vmreplica.getState vmid
  # vim-cmd hbrsvc/vmreplica.queryReplicationState vmid 6
  ```

6. ICMP Ping - 监视先前启动的连续 ping 操作。

转换期间，连续 ping 操作可能会发生中断。但是，在**迁移 VM** 任务完成后，测试 ping 会迅速恢复，这会反映在任务控制台中。

### 查看已迁移的 VM
{: #hcx-archi-migrate-vm-view-vms}

Hybrid Cloud Services 打开成功迁移的虚拟机的电源后，会关闭原始 VM 的电源，并将其存储在 vCenter 中的某个文件夹中。存储的虚拟机会保留，直到手动将其删除。

迁移后，查看 vCenter，并记下标记为**从云迁移的 VM** 和**迁移到云的 VM** 的文件夹。
* 作为副本，已关闭电源的 VM 的名称为原始名称附加二进制时间戳记。
* 已迁移 VM 可以视为其他任何 VM。例如，可以将这些 VM 移动到其他位置并打开电源。
* 可以删除这两个文件夹中不需要的 VM。
* 删除是不可改变的操作，除非落实了备份解决方案。

## 相关链接
{: #hcx-archi-migrate-vm-related}

* [修改或卸载 HCX](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-mod-uninstall)

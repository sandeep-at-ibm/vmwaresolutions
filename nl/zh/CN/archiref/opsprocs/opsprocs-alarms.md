---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 警报
{: #opsprocs-alarms}

## 简介
{: #opsprocs-alarms-intro}

vSphere 包含事件和警报子系统，用于跟踪 vSphere 环境中发生的事件，并在 vCenter 中提供这些信息。在此子系统中使用了以下术语：

* 事件 - 事件是 vCenter 中对象（例如，主机和虚拟机 (VM)）上发生的系统或用户操作的记录。事件数据包含有关事件的详细信息，例如事件生成方、事件发生时间以及事件类型。在 vSphere Web Client 中，事件数据显示在“监视”选项卡中。事件分类如下：
 * 错误 - 指示系统中发生了无法恢复的问题，将终止进程或操作。
 * 警告 - 指示系统存在潜在风险，需要进行修复。此事件不会终止进程或操作。
 * 参考 - 描述用户或系统操作已成功完成。
 * 审计 - 审计日志数据包含有关操作描述、操作执行者、操作执行时间以及用户 IP 地址的信息。
* 警报 - 警报是为了响应事件、一组条件或清单对象状态而激活的通知。在 vSphere Client 中，警报定义包含以下元素：
 * 名称和描述 - 提供标识性标签和描述。
 * 目标 - 定义受监视对象的类型。
 * 警报规则 - 定义触发警报的事件、条件或状态，以及定义通知严重性。此外，还定义为了响应触发的警报而执行的操作。
 * 上次修改时间 - 上次修改已定义警报的日期和时间。
 * 警报具有以下严重性级别：
   * 正常 - 绿色。
   * 警告 - 黄色。
   * 警报 - 红色。
* 警报定义 - 警报定义与清单中选择的对象相关联，并监视其定义中指定的清单对象的类型。警报定义包含以下元素：
 * 名称和描述 - 提供标识性标签和描述。
 * 警报类型 - 定义受监视对象的类型。
 * 触发器 - 定义触发警报的事件、条件或状态，以及定义通知严重性。
 * 容错阈值（报告）- 提供对条件和状态触发器阈值的更多限制，必须超过这些阈值后方可触发警报。
 * 操作 - 定义为了响应触发的警报而执行的操作。VMware 提供了特定于清单对象类型的预定义操作集。
* 警报操作 - 警报操作是为了响应触发器而执行的操作。例如，可以在触发警报时，向一个或多个管理员发送电子邮件通知。
* 确认触发的警报 - 确认警报后，将停止警报操作。确认警报后，不会清除或重置警报。通过确认警报，可以让其他用户知道您在负责处理此问题。
* 重置触发的警报 - 如果 vCenter 检索不到标识正常条件的事件，那么事件触发的警报可能无法重置为正常状态。在此类情况下，请手动重置警报。
* 预配置的 vSphere 警报 - vSphere 事件和警报子系统有若干缺省警报，用于监视 vSphere 清单对象的操作。您必须为这些警报设置操作。

## 警报设置工作流程
{: #opsprocs-alarms-setup-workflow}

VMware 提供了以下各表中所述的预配置 vCenter 警报，但为这些警报设置的操作仅在 vCenter Web Client 中显示。我们的指导信息用于配置 SMTP 服务器详细信息，然后将警报操作设置为仅在以下警报初始发生时向系统管理员发送电子邮件，以避免系统管理员团队收到海量电子邮件。有关更多信息，请参阅[将电子邮件作为警报操作发送](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-1F940DAF-933B-44B7-A200-7A11B5D3E3D5.html){:new_window}。

警报设置工作流程如下所示：
* 配置 SMTP 服务器详细信息。
* 为集群、主机、数据存储和关键虚拟设备（VCSA、PSC、NSX Manager 和 NSX Controller）配置警报操作：
 * 集群 - VMware 高可用性错误。
 * 主机 - CPU 状态、内存状态、存储器状态和硬件状态（即电压、温度或电源状态更改）。
 * 数据存储 - 可用磁盘空间不足。
 * 关键虚拟设备 - CPU 使用率、内存使用率和磁盘等待时间
* 使用主动每日任务：
 * 复查发送的警报 - 是否确实需要这些警报？
 * 复查未发送的警报 - 是否需要了解有关这些警报的信息？
 * 复查度量值 - 度量值是否正确；例如，既然您已了解基线，那么是否 CPU 使用率应该设置为 75%，而不是 90%？
 * 是否需要配置您自己的警报？
 * 是否需要包含虚拟机？

##  典型警报工作流程
{: #opsprocs-alarms- alarm-workflow}

警报设置后，下面是触发警报时警报工作流程的示例，系统管理员通常会采用此工作流程：

1. 主机设置了用于监视 CPU 使用率的警报，并且该警报的警报操作是在触发警报时向管理员发送电子邮件，如先前部分中所述。
3. 主机 CPU 使用率激增，触发了警报，从而向管理员发送电子邮件。
4. 其中一个管理员登录到 vCenter，并确认了触发的警报，以便让其他管理员知道正在解决该问题，并阻止警报发送更多电子邮件。但是，警报仍会在系统中显示。
5. 管理员找到导致 CPU 峰值的原因并进行纠正。
6. 警报自动重置。

## 预配置的警报 - 标准
{: #opsprocs-alarms-preconfigured-std}

下表描述了以下各项：

* 警报名称 - 在 vCenter 中显示的警报的名称。
* 指导信息 - 关于使用此警报的 IC4V 指导信息。
* 更多信息 - IBM 或 VMware 提供的其他信息，用于帮助在触发这些警报后加以解决。

表 1. 预配置的警报

|警报名称|指导信息|更多信息|
|---|---|---|
|主机连接和电源状态|配置为在设置为“未响应”或“备用”时发送一次电子邮件。|[主机连接状态警报频繁地从绿色变为红色 (1020210)](https://kb.vmware.com/s/article/1020210){:new_window}|
|主机 CPU 使用率|配置为在主机 CPU 使用率大于 90% 并持续 5 分钟时发送一次电子邮件。|[知识 - KB0012707 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=342e3d6adbc5730030c93a1b7c961976){:new_window}|
|主机内存使用率|配置为在主机内存使用率大于 95% 并持续 5 分钟时发送一次电子邮件。|[知识 - KB0012712 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=30110ee2db49730030c93a1b7c96194f){:new_window}|
|虚拟机 CPU 使用率|配置为在关键设备的 VM CPU 使用率大于 90% 并持续 5 分钟时发送一次电子邮件。|[虚拟机 CPU 使用情况警报 (2057830)](https://kb.vmware.com/s/article/2057830){:new_window}|
|虚拟机内存使用率|配置为在关键设备的 VM 内存使用率大于 95% 并持续 5 分钟时发送一次电子邮件。|[虚拟机内存使用情况警报 (2057846)](https://kb.vmware.com/s/article/2057846){:new_window}|
|磁盘上的数据存储使用率|对于 vSAN，配置为在数据存储使用率大于 70% 时发送一次电子邮件。对于非 VSAN，配置为在数据存储使用率大于 85% 时发送一次电子邮件。|[知识 - KB0012713 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=ddb3422edb89730030c93a1b7c9619f6){:new_window}|
|虚拟机 CPU 就绪时间|配置为在 5 分钟内关键设备的 VM CPU 就绪时间大于 2000 毫秒时发送一次电子邮件。|[知识 - KB0012718 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=7056426adb0d730030c93a1b7c9619e6){:new_window}|
|虚拟机磁盘总等待时间|配置为在 5 分钟内关键设备的 VM 磁盘总等待时间大于 30 毫秒时发送一次电子邮件。|[知识 - KB0012729 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=15dddea2db857300d5a971198c961995){:new_window}|
|虚拟机磁盘命令已取消|初始未设置。请考虑用于第二阶段的关键设备。|无其他信息|
|虚拟机磁盘重置|初始未设置。请考虑用于第二阶段的关键设备。|无其他信息|
|许可证清单监视|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window}以及[许可 ESXi 6.x 和 vCenter Server 6.x](https://kb.vmware.com/s/article/2107538){:new_window} |
|许可证用户阈值监视|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
|许可容量监视|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
|主机许可证版本与 vCenter Server 许可证版本不兼容|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [主机许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window} |
|启动辅助 VM 时超时*|未配置，因为此警报监视的是 VMware 容错，建议不要用于 vCenter Server 实例。| [启动辅助 VM 警报超时 (2064169)](https://kb.vmware.com/s/article/2064169){:new_window} |
|辅助 VM 的主机不兼容|未配置，因为此警报监视的是 VMware 容错，建议不要用于 vCenter Server 实例。|无其他信息|
|虚拟机容错状态已更改|未配置，因为此警报监视的是 VMware 容错，建议不要用于 vCenter Server 实例。|无其他信息|
|虚拟机容错 vLockStep 时间间隔状态已更改|未配置，因为此警报监视的是 VMware 容错，建议不要用于 vCenter Server 实例。|无其他信息|
|主机处理器状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机内存状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机硬件风扇状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机硬件电压|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机硬件温度状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机硬件电源状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机硬件系统板状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机电池状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|其他主机硬件对象的状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机存储器状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机 IPMI 系统事件日志状态|未配置，因为此警报不会影响服务。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机基板管理控制器状态|配置为在监视器从绿色变为红色时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|主机错误*|配置为在监视器更改为“错误”时发送一次电子邮件。|[联系 IBM 支持人员](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_support)|
|虚拟机错误*|配置为在关键设备发生严重错误时发送一次电子邮件。| [虚拟机故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window} |
|主机连接失败*|配置为当事件为“无法连接主机 - 网络错误”、“无法连接主机 - 超时”或“主机连接丢失”时发送一次电子邮件。|[主机连接状态警报频繁地从绿色变为红色 (1020210)](https://kb.vmware.com/s/article/1020210){:new_window}|
|在启用了 SIOC 的数据存储上检测到非受管工作负载|未配置，因为此警报不会影响服务。|[在运行 Storage I/O Control (SIOC) 进行拥堵管理的共享数据存储上检测到非受管 I/O 工作负载 (2075436)](https://kb.vmware.com/s/article/1020651){:new_window}|
|超过了自动精简配置卷容量阈值|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|无其他信息|
|数据存储功能警报|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|无其他信息|
|VASA 提供者已断开连接|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|无其他信息|
|VASA 提供者证书到期警报|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|无其他信息|
|VM 存储合规性警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[VM storage compliance alarm (2061940)](https://kb.vmware.com/s/article/2061940){:new_window}|
|数据存储合规性警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [使用数据存储](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-3CC7078E-9C30-402C-B2E1-2542BEE67E8F.html){:new_window} |
|刷新 VASA 提供者的 CA 证书和 CRL 失败|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|无其他信息|
|vSphere HA 故障转移资源不足|配置为在发生严重错误时发送一次电子邮件。|[知识 - KB0012739 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=fe1f0beedb8db300d5a971198c96191a){:new_window}|
|正在执行 vSphere HA 故障转移|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|找不到 vSphere HA 主节点代理程序|配置为在找不到 HA 主节点代理程序或无法与之通信时发送一次电子邮件。|[关于 vSphere 可用性](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.avail.doc/GUID-63F459B7-8884-4818-8872-C9753B2E0215.html){:new_window}|
|vSphere HA 主机状态|配置为在以下情况下发送一次电子邮件：主机上的 vSphere HA 代理程序发生错误，vSphere HA 检测到网络隔离的主机，vSphere HA 检测到网络分区的主机，或 vSphere HA 检测到主机故障。| [vSphere HA 主机状态故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}|
|vSphere HA 虚拟机故障转移失败|配置为在关键设备发生严重错误时发送一次电子邮件。|[创建和使用 vSphere HA 群集](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window}|
|vSphere HA 虚拟机监视操作|配置为在关键设备发生严重错误时发送一次电子邮件。|[创建和使用 vSphere HA 群集](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window}|
|vSphere HA 虚拟机监视错误|配置为在关键设备发生严重错误时发送一次电子邮件。|[创建和使用 vSphere HA 群集](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window}|
|vSphere HA VM 组件保护功能无法关闭虚拟机电源|配置为在关键设备发生严重错误时发送一次电子邮件。|[创建和使用 vSphere HA 群集](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.avail.doc/GUID-5432CA24-14F1-44E3-87FB-61D937831CF6.html){:new_window}|
|许可证错误*|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
|运行状态已更改*|配置为发生严重错误且状态变为“严重”时发送一次电子邮件。|[主机故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-6F6CE545-58FA-490B-8C8A-3CB8196CAEA8.html){:new_window}|
|Storage DRS 建议|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[DRS 故障排除信息](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window}|
|主机上不支持 Storage DRS|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[DRS 故障排除信息](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-5E7F6DEC-02A2-4221-AABA-EDFB9AE9EC70.html){:new_window}|
|数据存储集群的空间不足|配置为发生严重错误且磁盘使用率超过 85% 时发送一次电子邮件。|[向 vCenter Server 实例添加 NFS 存储器](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances)|
|数据存储位于多个数据中心内|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [Storage DRS 无法在数据存储上运行](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-976F5B21-8C64-4C85-BE75-0D86655E32DD.html){:new_window} |
|vSphere 分布式交换机内中继的 VLAN 的状态|配置为发生严重错误且并非 vSphere 分布式交换机中所有配置的 VLAN 都由物理交换机中继时发送一次电子邮件。|[在 vSphere Web Client 中启用 vSphere Distributed Switch 运行状况检查](https://kb.vmware.com/s/article/2032878){:new_window}|
|vSphere 分布式交换机 MTU 的状态匹配|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[在 vSphere Web Client 中启用 vSphere Distributed Switch 运行状况检查](https://kb.vmware.com/s/article/2032878){:new_window}|
|vSphere 分布式交换机 MTU 状态受支持|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[在 vSphere Web Client 中启用 vSphere Distributed Switch 运行状况检查](https://kb.vmware.com/s/article/2032878){:new_window}|
|vSphere 分布式交换机组队状态匹配|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[在 vSphere Web Client 中启用 vSphere Distributed Switch 运行状况检查](https://kb.vmware.com/s/article/2032878){:new_window}|
|虚拟机网络适配器保留状态|仅当启用了网络适配器保留时，才配置为发送电子邮件。| [为虚拟机配置带宽分配](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-FECAC41A-2C7A-4AD6-B740-7D8D44BADB52.html){:new_window}|
|虚拟机需要合并状态|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[使用快照管理虚拟机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-CA948C69-7F58-4519-AEB1-739545EA94E5.html){:new_window}|
|主机虚拟闪存资源状态|vCenter Server 实例上不支持主机虚拟闪存。|无其他信息|
|主机虚拟闪存资源使用情况|在 vCenter Server 实例中未配置，因为这些实例不支持主机虚拟闪存。|[关于虚拟闪存资源](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.storage.doc/GUID-E69F0809-3B19-483A-B906-4CE397CE56D6.html){:new_window}|
|在 vSAN 主机上注册/注销 VASA 供应商提供者失败|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|[VMware 兼容性指南](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window}|
|在主机上注册/注销第三方 IO 过滤器存储器提供者失败|在 vCenter Server 实例中未配置，因为这些实例不支持 VASA 存储器。|[VMware 兼容性指南](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=vasa){:new_window}|
|服务控制代理程序运行状况警报|配置为在组件标识为 sca 且“新状态”为“红色”时发送一次电子邮件。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|身份运行状况警报|配置为在组件标识为 identity 且“新状态”为“红色”时发送一次电子邮件。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|vSphere Web Client 运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[为 VMware vSphere 5.x/6.x Web Client 服务启用调试日志记录 (2011485)](https://kb.vmware.com/s/article/2011485){:new_window}|
|ESX 代理程序管理器运行状况警报|配置为在组件标识为 `eam` 且“新状态”为“`红色`”时发送一次电子邮件。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|消息传递总线配置运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|CIS 许可证运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|清单运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|vCenter Server 运行状况警报|配置为在组件标识为 vpxd 且“新状态”为“红色”时发送一次电子邮件。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|数据库运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|数据服务运行状况警报|配置为在组件标识为 vmware-dataservices-sca 且“新状态”为“红色”时发送一次电子邮件。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|RBD 运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|vService Manager 运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|性能图表服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|内容库服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|传输服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|VMware vSphere ESXi 转储收集器运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[VMware ESXi Dump Collector 支持](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-F8773E25-BD6A-4A6C-A999-D58CB853BA8A.html){:new_window}|
|VMware vAPI 端点服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|VMware 系统和硬件运行状况管理器服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[使用日志进行故障排除](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.troubleshooting.doc/GUID-552CC9E8-441C-434A-88FC-3F50881245D7.html){:new_window}|
|VMware vSphere 概要文件驱动的存储服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|VMware vFabric Postgres 服务运行状况警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[如何停止、启动或重新启动 vCenter Server 6.x 服务 (2109881)](https://kb.vmware.com/s/article/2109881){:new_window}|
|ESXi 主机证书更新失败状态|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vCenter Server 和 ESXi 主机证书故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window}|
|ESXi 主机证书状态|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vCenter Server 和 ESXi 主机证书故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window}|
|ESXi 主机证书验证失败状态|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vCenter Server 和 ESXi 主机证书故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window}|
|vSphere vCenter 主机证书管理方式|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vCenter Server 和 ESXi 主机证书故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window}|
|根证书状态|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vCenter Server 和 ESXi 主机证书故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-2C61E02D-D0D3-4BB5-B4FD-B0DD97791EE9.html){:new_window}|
|GPU ECC 未更正内存警报|在 vCenter Server 实例中未配置，因为这些实例不支持 GPU。|无其他信息|
|GPU ECC 已更正内存警报|在 vCenter Server 实例中未配置，因为这些实例不支持 GPU。|无其他信息|
|GPU 温度状况警报|在 vCenter Server 实例中未配置，因为这些实例不支持 GPU。|无其他信息|
|网络连接丢失|配置为在发生以下严重事件时发送一次电子邮件：网络连接丢失或与 DVPort 的网络连接丢失。|[网络故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}|
|网络上行链路冗余丢失|配置为在发生以下严重事件时发送一次电子邮件：网络冗余丢失或 DVPort 上的网络冗余丢失。|[网络故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}|
|网络上行链路冗余已降级*|配置为在发生以下严重事件时发送一次电子邮件：网络冗余已降级或 DVPort 上的网络冗余已降级。|[网络故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}|
|VMKernel NIC 未正确配置*|配置为在发生以下严重事件时发送一次电子邮件：在 `/Migrate/VMknic` 中指定的 `vmknic` 无效。|[网络故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}|
|无法连接到存储器*|配置为在发生以下严重事件时发送一次电子邮件：存储器连接丢失，存储路径冗余丢失，存储路径冗余已降级或失去与 NFS 服务器的连接。| [识别 ESX/ESXi 主机上的光纤通道、iSCSI 和 NFS 存储问题 (1003659)g](https://kb.vmware.com/s/article/1003659){:new_window} |
|迁移错误*|配置为在发生以下严重事件时发送一次电子邮件：无法迁移 VM，迁移错误，迁移主机错误，无法重定位 VM 或 VM 孤立。|[VM 的 vMotion 或 Storage vMotion 失败并显示以下错误：迁移超出了 100 秒的最长转换时间 (2141355)](https://kb.vmware.com/s/article/2141355){:new_window}|
|退出备用错误|在 vCenter Server 实例中未配置，因为不建议使用 DPM。|在低资源利用率期间，VM 会迁移到较少的主机上，并且不需要的 ESX 主机的电源会关闭，因此 vSphere 分布式电源管理 (DPM) 通过动态合并工作负载，节省内部部署的功耗。但通过关闭 IBM Cloud 裸机服务器的电源，无法实现节省功耗。|

\* 表示无状态警报。vCenter 不会保留无状态警报的数据，也不会计算或显示其状态。无法确认或重置无状态警报。
{:note}

## 预配置的警报 - vSAN
{: #opsprocs-alarms-preconfigured-vsan}

如果您有 vSAN 集群，那么下表中的其他预配置警报都适用：

* 警报名称 - 在 vCenter 中显示的警报的名称。
* 指导信息 - 关于使用此警报的 IC4V 指导信息。
* 更多信息 - IBM 或 VMware 提供的其他信息，用于帮助在触发这些警报后加以解决。

表 2. 预配置的警报 - vSAN

|警报名称|指导信息|更多信息|
|---|---|---|
|主机闪存容量超过 vSAN 的许可限制|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 许可证已到期|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3C4E8BF7-B0A9-46F0-BA50-D69F950AB958.html){:new_window} |
|vSAN 主机磁盘上发生错误|配置为在 vSAN 磁盘上发生永久错误时发送一次电子邮件。| [vSAN 设备在设备不可读或不可写时遇到永久性错误 (2071075)](https://kb.vmware.com/s/article/2071075){:new_window}  |
|vSAN 主机磁盘上发生错误|配置为在发生以下严重事件时发送一次电子邮件：虚拟 SAN 设备处于永久故障状态。| [vSAN 设备在设备不可读或不可写时遇到永久性错误 (2071075)](https://kb.vmware.com/s/article/2071075){:new_window}  |
|vSAN 许可证已到期|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[有关 vSAN 许可证的注意事项](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window}|
|vSAN 有时间限制的许可证已到期|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[有关 vSAN 许可证的注意事项](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-planning.doc/GUID-20731F2A-B001-4A05-AB4D-30C5B0044EC5.html){:new_window}|
|vSAN 硬件兼容性问题|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Check Information (2114803)](https://kb.vmware.com/s/article/2114803?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window} |
|vSAN 运行状况警报“活动多点广播连接检查”|配置为在发生严重事件时发送一次电子邮件。|[Virtual SAN 运行状况服务 - 网络运行状况 - 活动多播连接检查 (2116296)](https://kb.vmware.com/s/article/2116296){:new_window}|
|vSAN 运行状况警报“高级 vSAN 配置同步”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN Health Service - 群集运行状况 - 高级 vSAN 配置同步 (2107713)](https://kb.vmware.com/s/article/2107713){:new_window}|
|vSAN 运行状况警报“再次发生主机故障后”|配置为在发生严重事件时发送一次电子邮件。| [vSAN health warning “after one additional host failure” is reported incorrectly on two node ROBO/stretched clusters (2150568)](https://kb.vmware.com/s/article/2150568?lang=en_US){:new_window} |
|vSAN 运行状况警报“提供统计信息的所有主机”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[Virtual SAN 运行状况服务 - 性能服务 - 提供统计信息的所有主机检查 (2144400)](https://kb.vmware.com/s/article/2144400){:new_window}|
|vSAN 运行状况警报“所有主机均已配置 vSAN vmknic”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN 运行状况服务 - 网络运行状况 - 所有主机均已配置 vSAN vmknic (2108062)](https://kb.vmware.com/s/article/2108062){:new_window} |
|vSAN 运行状况警报“所有主机均具有匹配的多点广播设置”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[Virtual SAN 运行状况服务 - 网络运行状况 - 所有主机均具有匹配的多播设置 (2108092)](https://kb.vmware.com/s/article/2108092){:new_window}|
|vSAN 运行状况警报“所有主机都具有匹配的子网”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[Virtual SAN 运行状况服务 - 网络运行状况 - 所有主机都具有匹配的子网 (2108066)](https://kb.vmware.com/s/article/2108066){:new_window}|
|vSAN 运行状况警报“基本（单点广播）连接检查（正常 ping 操作）”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[Virtual SAN 运行状况服务 - 网络运行状况 - 主机小数据包 ping 测试（连接检查）和主机大数据包 ping 测试（MTU 检查）(2108285)](https://kb.vmware.com/s/article/2108285){:new_window}|
|vSAN 运行状况警报“集群运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 群集运行状况 - vSAN 运行状况服务安装 (2109874)](https://kb.vmware.com/s/article/2109874){:new_window}|
|vSAN 运行状况警报“组件元数据运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[组件元数据运行状况检查失败并显示无效状态错误 (2145347)](https://kb.vmware.com/s/article/2145347){:new_window}|
|vSAN 运行状况警报“拥堵”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 物理磁盘运行状况 - 拥堵 (2109255)](https://kb.vmware.com/s/article/2109255){:new_window}|
|vSAN 运行状况警报“控制器磁盘组方式经过 VMware 认证”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - vSAN HCL 运行状况 - vSAN HCL 上的 SCSI 控制器 (2109871)](https://kb.vmware.com/s/article/2109871){:new_window}|
|vSAN 运行状况警报“控制器驱动程序经过 VMware 认证”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - vSAN HCL 运行状况 - 控制器驱动程序 (2109263)](https://kb.vmware.com/s/article/2109263){:new_window}|
|vSAN 运行状况警报“控制器固件经过 VMware 认证”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[Controller firmware health check warning if multiple firmware versions are supported (2150398)](https://kb.vmware.com/s/article/2150398){:new_window}|
|vSAN 运行状况警报“对于 ESXi 发行版，控制器经过 VMware 认证”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - vSAN HCL 运行状况 - 控制器版本支持 (2109262)](https://kb.vmware.com/s/article/2109262){:new_window}|
|vSAN 运行状况警报“主机上禁用了 CPU AES-NI”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Encryption - CPU AES-NI Host Enablement Check (2149499)](https://kb.vmware.com/s/article/2149499){:new_window} |
|vSAN 运行状况警报“当前集群情况”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 限制运行状况 – 当前群集情况 (2108740)](https://kb.vmware.com/s/article/2108740){:new_window}|
|vSAN 运行状况警报“客户体验改进计划 (CEIP)”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Online Health - CEIP Check (2148866)](https://kb.vmware.com/s/article/2148866){:new_window} |
|vSAN 运行状况警报“数据运行状况”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 数据运行状况 - vSAN 对象运行状况 (2108319)](https://kb.vmware.com/s/article/2108319){:new_window}|
|vSAN 运行状况警报“磁盘容量”|配置为在发生警告事件时发送一次电子邮件。|[vSAN 运行状况服务 - 物理磁盘运行状况 - 磁盘容量 (2108907)](https://kb.vmware.com/s/article/2108907){:new_window}|
|vSAN 运行状况警报“磁盘格式版本”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 集群 - 磁盘格式版本 (2146135)](https://kb.vmware.com/s/article/2146135){:new_window}|
|vSAN 运行状况警报“ESXi vSAN 运行状况服务安装”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 群集运行状况 - 最新 VSAN 运行状况服务 (2107705)](https://kb.vmware.com/s/article/2107705){:new_window}|
|vSAN 运行状况警报“主目录对象”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - vSAN iSCSI target service - Home object (2147601)](https://kb.vmware.com/s/article/2147601){:new_window} |
|vSAN 运行状况警报“主机组件限制”|配置为在发生严重事件时发送一次电子邮件。| [vSAN 运行状况服务 - 限制 - 主机组件 (2146130)](https://kb.vmware.com/s/article/2146130){:new_window} |
|vSAN 运行状况警报“检索硬件信息时发生主机问题”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - HCL Health - Host issues retrieving hardware information (2149290)](https://kb.vmware.com/s/article/2149290){:new_window} |
|vSAN 运行状况警报“主机维护模式和取消配置状态”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 主机维护模式与 vSAN 节点取消配置状态同步 (51464)](https://kb.vmware.com/s/article/51464){:new_window}|
|vSAN 运行状况警报“主机已与 VC 断开连接”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 网络运行状况 - 主机与 vCenter 断开连接 (2108004)](https://kb.vmware.com/s/article/2108004){:new_window}|
|vSAN 运行状况警报“存在连接问题的主机”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 网络运行状况 - 存在连接问题的主机 (2108317)](https://kb.vmware.com/s/article/2108317){:new_window}|
|vSAN 运行状况警报“见证主机上的首选容错域无效”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 见证主机上的首选容错域无效 (2130589)](https://kb.vmware.com/s/article/2130589){:new_window} |
|vSAN 运行状况警报“单点广播代理程序无效”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[Virtual SAN 运行状况服务 - 无效的单播代理测试 (2144398)](https://kb.vmware.com/s/article/2144398){:new_window}|
|vSAN 运行状况警报“iSCSI 目标服务”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - vSAN iSCSI target service – Network configuration (2147602)](https://kb.vmware.com/s/article/2147602){:new_window} |
|vSAN 运行状况警报“限制运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“内存池（堆）”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 物理磁盘运行状况 - 内存池 (2109256)](https://kb.vmware.com/s/article/2109256){:new_window}|
|vSAN 运行状况警报“内存池（板）”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 物理磁盘运行状况 - 内存池 (2109256)](https://kb.vmware.com/s/article/2109256){:new_window}|
|vSAN 运行状况警报“MTU 检查（使用较大的包大小执行 ping 操作）”|配置为在发生严重事件时发送一次电子邮件。|[Virtual SAN 运行状况服务 - 网络运行状况 - 主机小数据包 ping 测试（连接检查）和主机大数据包 ping 测试（MTU 检查）(2108285)](https://kb.vmware.com/s/article/2108285){:new_window}|
|vSAN 运行状况警报“基于其他检查的多点广播评估”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 网络运行状况 – 基于其他检查的多播评估 (2108318)](https://kb.vmware.com/s/article/2108318){:new_window}|
|vSAN 运行状况警报“网络配置”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“网络运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“网络等待时间检查”|配置为在发生警告事件时发送一次电子邮件。| [vSAN Health Service - Network Health - Network Latency Check (2149511)](https://kb.vmware.com/s/article/2149511){:new_window} |
|vSAN 运行状况警报“见证主机上未声明任何磁盘”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 见证主机上未声明任何磁盘 (2130584)](https://kb.vmware.com/s/article/2130584){:new_window}|
|vSAN 运行状况警报“联机运行状况连接”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Online Health - Internet Connectivity Check (2149196)](https://kb.vmware.com/s/article/2149196){:new_window} |
|vSAN 运行状况警报“操作运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“性能数据收集”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[性能服务上的 vSAN 运行状况测试失败 (2150589)](https://kb.vmware.com/s/article/2150589){:new_window}|
|vSAN 运行状况警报“性能服务状态”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[性能服务上的 vSAN 运行状况测试失败 (2150589)](https://kb.vmware.com/s/article/2150589){:new_window}|
|vSAN 运行状况警报“物理磁盘组件限制运行状况”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 物理磁盘 - 组件数上限 (2146086)](https://kb.vmware.com/s/article/2146086){:new_window}|
|vSAN 运行状况警报“物理磁盘运行状况检索问题”|配置为在发生严重事件时发送一次电子邮件。| [vSAN Health Service - Physical Disk Health - Physical disk health retrieval issue (2149291)](https://kb.vmware.com/s/article/2149291){:new_window} |
|vSAN 运行状况警报“物理磁盘运行状况 - 元数据运行状况”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 物理磁盘运行状况 - 元数据运行状况 (2108690)](https://kb.vmware.com/s/article/2108690){:new_window}|
|vSAN 运行状况警报“首选容错域未设置”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 首选容错域未设置 (2130590)](https://kb.vmware.com/s/article/2130590){:new_window}|
|vSAN 运行状况警报“再同步操作调速”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Cluster Health - Resynchronization Operations Throttling Check (2149504)](https://kb.vmware.com/s/article/2149504){:new_window} |
|vSAN 运行状况警报“SCSI 控制器经过 VMware 认证”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - vSAN HCL 运行状况 - 控制器驱动程序 (2109263)](https://kb.vmware.com/s/article/2109263){:new_window}|
|vSAN 运行状况警报“服务运行时状态”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“站点等待时间运行状况”|仅当 vSAN 已延伸时，才视为警报。| [vSAN Health Service - Stretched cluster - Site latency (2146133)](https://kb.vmware.com/s/article/2146133){:new_window} |
|vSAN 运行状况警报“软件版本兼容性”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 群集 - 软件版本兼容性 (2146134)](https://kb.vmware.com/s/article/2146134){:new_window}|
|vSAN 运行状况警报“空间效率配置一致性”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“空间效率使用情况运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“统计数据库对象冲突”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 性能服务 - 统计数据库对象冲突检查 (2144405)](https://kb.vmware.com/s/article/2144405){:new_window}|
|vSAN 运行状况警报“统计数据库对象”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 性能服务 - 统计数据库对象检查 (2144403)](https://kb.vmware.com/s/article/2144403){:new_window}|
|vSAN 运行状况警报“统计主节点选举”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 性能服务 - 统计主节点选举检查 (2144408)](https://kb.vmware.com/s/article/2144408){:new_window}|
|vSAN 运行状况警报“延伸集群运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“时间在主机和 VC 之间未同步”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Cluster Health - Time Synchronization Across Hosts and VC (2149505)](https://kb.vmware.com/s/article/2149505){:new_window} |
|vSAN 运行状况警报“容错域数量异常”|仅当 vSAN 已延伸时，才视为警报。|[SAN 运行状况服务 - 容错域数量异常 (2130581)](https://kb.vmware.com/s/article/2130581){:new_window}|
|vSAN 运行状况警报“单点广播代理程序配置不一致”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 单播代理配置不一致 (2130580)](https://kb.vmware.com/s/article/2130580){:new_window}|
|vSAN 运行状况警报“单点广播代理程序未配置”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 单点代理未配置 (2130582)](https://kb.vmware.com/s/article/2130582){:new_window}|
|vSAN 运行状况警报“主机版本不受支持”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 主机版本不受支持 (2130583)](https://kb.vmware.com/s/article/2130583){:new_window}|
|vSAN 运行状况警报“vCenter 或主机未连接到密钥管理服务器”|仅当启用了 vSAN 加密时，才视为警报。| [vSAN Health Service - Unsupported host version (2130583)](https://kb.vmware.com/s/article/2149497){:new_window} |
|vSAN 运行状况警报“vCenter 状态具有权威性”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Cluster health – vCenter state is authoritative (2150916)](https://kb.vmware.com/s/article/2150916){:new_window} |
|vSAN 运行状况警报“详细模式”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务中的“性能服务 - 详细模式”(51527)](https://kb.vmware.com/s/article/51527){:new_window}|
|vSAN 运行状况警报“vSAN 构建推荐引擎构建建议”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - vSphere Update Manager - vSAN build recommendation engine health (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
|vSAN 运行状况警报“vSAN 构建推荐引擎运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - vSphere Update Manager - vSAN build recommendation engine health (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
|vSAN 运行状况警报“vSAN 构建推荐引擎运行状况”配置问题|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - vSphere Update Manager - vSAN build recommendation engine health (2150914)](https://kb.vmware.com/s/article/2150914){:new_window} |
|vSAN 运行状况警报“vSAN CLOMD 活动性”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 群集运行状况 - CLOMD 活动性检查 (2109873)](https://kb.vmware.com/s/article/2109873){:new_window}|
|vSAN 运行状况警报“vSAN 集群配置一致性”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 群集配置一致性 (2149506)](https://kb.vmware.com/s/article/2149506){:new_window}|
|vSAN 运行状况警报“vSAN 集群分区”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 网络运行状况 - vSAN 群集分区 (2108011)](https://kb.vmware.com/s/article/2108011){:new_window}|
|vSAN 运行状况警报“vSAN 磁盘平衡”|配置为在发生警告事件时发送一次电子邮件。|[vSAN 运行状况服务 - 群集运行状况 - vSAN 磁盘平衡 (2144278)](https://kb.vmware.com/s/article/2144278){:new_window}|
|vSAN 运行状况警报“vSAN HCL 数据库自动更新”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - 硬件兼容性 - vSAN HCL 数据库自动更新 (2146132)](https://kb.vmware.com/s/article/2146132){:new_window}|
|vSAN 运行状况警报“vSAN HCL 数据库已为最新”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|[vSAN 运行状况服务 - vSAN HCL 运行状况 - vSAN HCL 数据库已为最新 (2109870)](https://kb.vmware.com/s/article/2109870){:new_window}|
|vSAN 运行状况警报“vSAN HCL 运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“vSAN 运行状况服务已为最新”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - vSAN Build Recommendation - vSAN release catalog up-to-date (58891)](https://kb.vmware.com/s/article/58891){:new_window} |
|vSAN 运行状况警报“vSAN 对象运行状况”|配置为在发生严重事件时发送一次电子邮件。|[vSAN 运行状况服务 - 数据运行状况 - vSAN 对象运行状况 (2108319)](https://kb.vmware.com/s/article/2108319){:new_window}|
|vSAN 运行状况警报“vSAN 性能服务运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Performance Service - Status Check (2149406)](https://kb.vmware.com/s/article/2149406){:new_window} |
|vSAN 运行状况警报“vSAN VM 运行状况”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|vSAN 运行状况警报“vSphere 集群成员与 vSAN 集群成员不匹配”|不视为有必要通知。警报作为主动日常检查的一部分进行复查。| [vSAN Health Service - Cluster Health - vSphere and vSAN Cluster Members Match vSAN (2149507)](https://kb.vmware.com/s/article/2149507){:new_window} |
|vSAN 运行状况警报“见证主机容错域配置错误”| 仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 见证主机容错域配置错误 (2130586)](https://kb.vmware.com/s/article/2130586){:new_window}|
|vSAN 运行状况警报“找不到见证主机”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 找不到见证主机 (2130585)](https://kb.vmware.com/s/article/2130585){:new_window}|
|vSAN 运行状况警报“见证主机位于 vCenter 集群内”|仅当 vSAN 已延伸时，才视为警报。|[vSAN 运行状况服务 - 见证主机位于 vCenter 群集内 (2130587)](https://kb.vmware.com/s/article/2130587){:new_window}|
|针对 vMotion 的 vSAN 运行状况警报“基本（单点广播）连接检查（正常 ping 操作）”|配置为在发生严重事件时发送一次电子邮件。| [VSAN health shows connectivity errors](https://developer.ibm.com/answers/questions/452172/vsan-health-shows-connectivity-errors/){:new_window} |
|针对 vMotion 的 vSAN 运行状况警报“MTU 检查（使用较大的包大小执行 ping 操作）”|配置为在发生严重事件时发送一次电子邮件。|[Virtual SAN 运行状况服务 - 网络运行状况 - 主机小数据包 ping 测试（连接检查）和主机大数据包 ping 测试（MTU 检查）(2108285)](https://kb.vmware.com/s/article/2108285){:new_window}|
|vSAN 运行状况服务警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|
|针对总体运行状况摘要的 vSAN 运行状况服务警报|不视为有必要通知。警报作为主动日常检查的一部分进行复查。|无其他信息|


## 预配置的警报 - Hybridity Bundle
{: #opsprocs-alarms-preconfigured-hcx}

Hybridity Bundle 会安装 HCX，这将创建以下额外的预配置警报：

表 3. 预配置的警报 - HCX

|警报名称|指导信息|更多信息|
|---|---|---|
|批量迁移失败|由于将对迁移进行管理，因此不视为有必要通知。|请参阅 [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)和 [VMware HCX troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
|冷迁移失败|由于将对迁移进行管理，因此不视为有必要通知。|请参阅 [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)和 [VMware HCX troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
|HCX 云数据库升级失败|由于将对升级进行管理，因此不视为有必要通知。|请参阅 [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)和 [VMware HCX troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
|HCX 企业数据库升级失败|由于将对升级进行管理，因此不视为有必要通知。|请参阅 [HCX 故障诊断](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)和 [VMware HCX troubleshooting](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-B6CF4054-9C8C-43DE-AC67-01AE0679B190.html){:new_window}。|
|HCX 互连隧道状态|配置为针对“临界隧道状态是停止运行”事件发送一次电子邮件。|请参阅[网络 (WAN) 连接](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting#hcxclient-troubleshooting-wan-connect)。|

## 事件和警报过程
{: #opsprocs-alarms-procedures}

下表描述了事件和警报的若干过程。

表 4. 事件和警报过程

|标题|描述|
|---|---|
|查看事件|要查看事件，请导航至 vCenter，并选择清单对象。单击**监视**选项卡，单击**任务和事件**，然后单击**事件**。选择事件以查看详细信息。可以使用过滤器，并选择列标题以对列表进行排序。|
|导出事件|您可能需要导出事件，以使用 MS Excel 中的工具来提供帮助。选择必需的清单对象。单击**监视**选项卡，单击**事件**，然后单击**导出**图标。在**导出事件**窗口中，指定要导出的事件信息的类型。选择**生成 CSV 报告**，然后单击**保存**。指定文件名和位置并保存文件。|
|事件保留时间|缺省情况下，事件保留时间设置为 30 天。您需要在 VMware vSphere Web Client 中更改此设置。单击**配置**选项卡，单击**设置**，然后单击**常规**。单击**编辑**，将“事件保留时间”更改为所需的天数，然后单击**确定**。|
|查看触发的警报|要查看触发的警报，请导航至 vCenter，然后在**警报**窗格中选择**全部**或**新**。此列表每 120 秒刷新一次。要查看所选清单对象上触发的警报，请选择该对象。单击**监视**选项卡，单击**问题**，然后选择**触发的警报**。|

## 相关链接
{: #opsprocs-alarms-links}

* [vSphere 监控和性能](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-monitoring-performance-guide.pdf){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-17"

---

# 故障诊断
{: #opsprocs-trouble}

要对 vCenter Server 实例问题进行故障诊断，系统管理员必须识别问题的症状，确定哪些解决方案组件受影响，研究并建议修复或变通方法，以及测试修复。

* 识别症状 - 有多种潜在的原因可能导致实例性能不佳或无法运行。高效故障诊断的第一步是准确识别出发生了什么问题。这些症状可以通过以下各项进行报告：vSphere 事件和警报、{{site.data.keyword.cloud}} 中的 Operations Management 或通过其中一个用户的 Service Desk 进行报告。
* 隔离受影响的组件 - 识别到问题的症状后，必须确定受影响并可能导致问题的软件或硬件组件以及未涉及的组件。{{site.data.keyword.cloud_notm}} 中的 vCenter Operations Management 等工具可帮助您执行此步骤。
* 建议修复或变通方法 - 了解症状并隔离了组件后，就可以研究可能的修复和变通方法。系统管理员还可使用 {{site.data.keyword.cloud_notm}} 门户网站（其中包含本文档中的故障诊断场景）以及 IBM ServiceNow 和 VMware Knowledge Base。此外，还有许多 Wiki 和博客可能十分有用。为了更快速地解决问题，{{site.data.keyword.cloud_notm}} 中的 Operations Management 包含针对已识别的问题的一些修复措施。
* 测试可能的解决方案 - 在您了解问题的症状、涉及的组件并且建议了修复/变通方法后，系统管理员会系统地测试解决方案，直到问题解决为止。

vSphere 包含用户可配置的事件和警报子系统，用于跟踪在整个 vSphere 环境中发生的事件，并将数据存储在日志文件和 vCenter 数据库中。此子系统还支持系统管理员指定触发警报的条件。系统条件发生更改时，警报会将状态从警告更改为更严重的警报，并且可以触发自动警报操作，例如向系统管理员团队发送电子邮件。如果希望在特定清单对象或对象组发生特定事件或条件时获得通知或立即执行操作，那么此功能非常有用。

其他工具（例如，合并到 Operations Management on {{site.data.keyword.cloud_notm}} 体系结构中的工具）可在以下方面提供更多帮助：识别症状，隔离受影响的组件以及建议修复/变通方法。

## 准则
{: #opsprocs-trouble-guidelines}

以下准则被视为是对 {{site.data.keyword.vmwaresolutions_short}} 问题进行故障诊断的最佳实践：
* 系统地处理故障诊断并解决问题。
* 症状是否与以下方面相关：可用性、利用率或配置：
 *  可用性 - 这些症状与硬件和软件组件的可用性相关，典型特点是无响应。高可用性设计通常会掩盖这些问题，以便这些问题不会直接影响工作负载和用户。
 * 利用率 - 这些症状与容量和性能相关，典型特点是装入运行缓慢或无法装入。主动管理容量可显著减少这些问题。
 * 配置 - 通常在供应新服务或应用更改时会发现这些问题。不正确的设置可能会显示为可用性或利用率症状。例如，不正确的 IP 地址会显示为可用性问题，而虚拟机 (VM) RAM 设置太低会导致利用率症状。
* 尝试将问题隔离到环境中的组件。
* 进行记录，以便可以跟踪各个步骤。
* 了解并记录软件版本。
* 记录子网和 IP 地址使用情况，包括 VIP 和 NAT 地址。
* 获取网络图。您需要一些显示物理（底层）和逻辑（覆盖）层的图。
* 了解最近对环境所做的任何更改。
* 研究修复产生的影响，不要把自己排除在任何管理界面之外。
* 确保拥有所有关键组件的备份；在需要时，可重新装入或重置这些组件。
* 不要一次更改多项。
* 记录每个更改及其结果。
* 提出支持请求时，请确保仔细记录并提供相关信息。非常明确地说明看到的症状并识别您认为发生故障的组件。请确保使用正确的术语。尽量减少在选择用词方面产生的任何混淆或含糊之处。
* vSphere ESXi 和 vCenter Server 配置文件用于控制系统的行为，请了解这些文件的位置。大多数配置文件设置是在安装期间设置的，但在安装后可以进行修改。
* 日志文件用于捕获由内核以及不同子系统和服务生成的消息。vSphere ESXi 和 vCenter 服务维护有单独的日志文件，请了解这些文件的位置以及可以如何对其进行访问。
* 了解如何使用常用系统管理工具来获取诊断帮助。

有关更多信息，请参阅[故障诊断准则 KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}。

## 使用日志文件进行故障诊断
{: #opsprocs-trouble-logs}

日志文件是对问题进行故障诊断的绝佳信息来源，但考虑到实际的日志文件数量以及每个日志中的大量条目，要利用日志文件并不容易。[使用日志文件进行故障诊断 KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window} 中详细描述了这些日志文件在 VMware 环境中的位置。由于日志文件的数量和每个日志中的大量条目，您应该考虑使用 Operations Management on {{site.data.keyword.cloud_notm}} 中的工具来帮助捕获和分析事件日志。

## 常见场景故障诊断
{: #opsprocs-trouble-common}

为了帮助隔离受影响的组件，本文档有关对常见场景进行故障诊断的内容已分类如下：

* 虚拟机 - 这些故障诊断主题提供有关 VM 上潜在问题的指导信息。
* 主机 - 这些故障诊断主题提供有关 vSphere ESXi 主机问题的指导信息。
* 集群 - 这些故障诊断主题提供有关可用性和资源管理的指导信息。
* 存储器 - 这些故障诊断主题提供有关解决 vSAN 和 NFS 存储器问题的指导信息。
* 网络 - 这些故障诊断主题提供有关解决网络问题的指导信息。
* vCenter - 这些故障诊断主题提供有关解决 vCenter 问题的指导信息。
* 许可证 - 这些故障诊断主题提供有关解决许可证问题的指导信息。这些主题通常与在 {{site.data.keyword.cloud_notm}} 中使用自带许可证的客户机相关。

### 虚拟机
{: #opsprocs-trouble-common-vm}

表 1. 虚拟机故障诊断

|标题|描述|
|---|---|
|通用 VM 故障诊断|有关更多信息，请参阅[虚拟机故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE645240-83CA-4F9E-B2F7-BECE864982C3.html){:new_window}。|
|VM 性能问题|有关对 VM 性能问题的症状（包括访客操作系统引导缓慢、应用程序性能不佳、应用程序需要很长时间才能启动或应用程序无响应）进行故障诊断的信息，请参阅[对 ESX/ESXi 虚拟机性能问题进行故障排除 (2001003)](https://kb.vmware.com/s/article/2001003){:new_window}。|
|恢复孤立 VM|有关恢复孤立 VM（即，在 vCenter 数据库中存在，但 vSphere ESXi 主机未识别到的 VM）的信息，请参阅[知识 - KB0012862 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=57c90b74dbdd7300c4fa302f9d96199e){:new_window}。|
|VM 的电源无法打开|有关更多信息，请参阅[对无法打开电源的虚拟机进行故障排除 (2001005)](https://kb.vmware.com/s/article/2001005){:new_window}。|
|在通过模板克隆或部署后，VM 的电源无法打开| [VMware 文章](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2742CE14-20FD-416F-B89C-A156053A973F.html){:new_window}中讨论了通过模板克隆或部署 VM 后影响该 VM 的问题。|
|VMware Tools 已过期或未安装 - VMware Tools 应该安装在 VM 上，并保持最新。| [IBM Cloud KB0012161](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=797afaf0dbb477486001327e9d9619e6){:new_window} 提供了有关这些任务的指导信息。|
|旧 VM 网络设备|如果 VM 网络设备无法使网络性能保持最新，那么应用程序性能可能会因此受到影响。有关部署新的虚拟网络设备和驱动程序的更多信息，请参阅[为虚拟机选择网络适配器 (1001805)](https://kb.vmware.com/s/article/1001805){:new_window}。|
|虚拟机内存限制|通常会使用内存限制，但是，如果访客操作系统无法访问所需要的内存，那么访客操作系统内部的应用程序可能会性能不佳。有关解决此问题的更多信息，请参阅[配置资源分配设置](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-14102AB7-2CF9-42E3-9642-3EB6629EF530.html){:new_window}。|
|VM 快照|虽然快照非常有用，但 VM 快照的数量和寿命会直接影响 VM 的性能。有关解决此问题的信息，请参阅[整合快照](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-2F4A6D8B-33FF-4C6B-9B02-C984D151F0D5.html){:new_window}。|
|VM 日志记录|如果未正确配置日志记录，那么数据存储的容量可能会受到负面影响。有关解决此问题的信息，请参阅[配置客户机操作系统的日志记录级别](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.monitoring.doc/GUID-F465D340-6556-49E8-B137-C0B4A060E83B.html){:new_window}。|
|对网络连接问题进行故障诊断|症状可能包括 VM 无法连接到网络，或者无法与单个 VM 建立进出网络连接。有关解决问题的信息，请参阅[对虚拟机网络连接问题进行故障排除 (1003893)](https://kb.vmware.com/s/article/1003893?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
|确定多个虚拟 CPU 是否导致性能问题|有关对配置有多个 CPU 时遇到性能问题的 VM 进行故障诊断的信息，请参阅[确定多个虚拟 CPU 是否导致性能问题 (1005362)](https://kb.vmware.com/s/article/1005362?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。这些问题可能包括在将数据复制到 VM 或从 VM 复制数据时传输速度慢，备份作业超时或很慢，或者 VM 性能不佳。|
|VM 已关闭电源或重新启动|有关解决此问题的信息，请参阅[确定虚拟机关闭电源或重新启动的原因 (1019064)](https://kb.vmware.com/s/article/1019064?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
|一个或多个 VM 的响应时间不佳|有关隔离 vSphere ESXi 主机上性能问题的信息，请参阅[对 ESX/ESXi 虚拟机性能问题进行故障排除 (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}。性能问题可能是由于 CPU 约束、内存超配、存储器等待时间或网络等待时间而导致的。|

### vSphere ESXi 主机
{: #opsprocs-trouble-common-host}

表 2. 典型 vSphere ESXi 主机故障诊断

|标题|描述|
|---|---|
|ESXi 命令|有关 vSphere 中的命令行界面、ESXi Shell 命令以及 VMware vSphere 命令行界面 (vCLI) 命令的概述，请参阅 [Getting Started with vSphere Command-Line Interfaces](https://vdc-download.vmware.com/vmwb-repository/dcr-public/bc4fa31a-40ac-4aa9-a6a1-7171d1fff7f4/740990ee-4d65-4627-a9d4-0f046cb78aec/vsphere-esxi-vcenter-server-67-command-line-interface-getting-started-guide.pdf){:new_window}。|
|vSphere HA 主机状态|如果 vCenter 报告的 vSphere HA 主机状态指示主机上存在错误状况，那么需要对此进行修复，因为此问题会阻止 vSphere HA 在发生故障后重新启动 VM。有关更多信息，请参阅 [vSphere HA 主机状况故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-DF7CEF44-98EC-458A-8614-50CCAEC0A7C5.html){:new_window}。|
|vSphere ESXi 主机处于非响应状态|有关对显示为“未响应”或“已断开连接”的 vSphere ESXi 主机进行故障诊断，或者对主机上在 vCenter 中灰显的 VM 进行故障诊断的信息，请参阅 [ESX/ESXi 主机不响应且灰显 (1019082)](https://kb.vmware.com/s/article/1019082){:new_window}。|
|打开 VM 电源时，显示“找不到文件”错误|有关重新创建丢失的虚拟盘描述符文件 (VMDK) 的信息，请参阅[重新创建丢失的虚拟机磁盘描述符文件 (1002511)](https://kb.vmware.com/s/article/1002511){:new_window}。|
|VM 性能问题|有关隔离 vSphere ESXi 主机上性能问题的信息，请参阅[对 ESX/ESXi 虚拟机性能问题进行故障排除 (2001003)](https://kb.vmware.com/s/article/2001003?lang=en_US){:new_window}。性能问题可能是由于 CPU 约束、内存超配、存储器等待时间或网络等待时间而导致的。|
|裸机服务器停止运行|如果运行 vSphere ESXi 的裸机服务器无响应或停止运行，请登录到 {{site.data.keyword.cloud_notm}} 管理 UI 或控制台并检查相关状态。如果需要，请打开案例以获取有关裸机服务器的帮助。有关更多信息，请参阅[使用支持案例](/docs/get-support?topic=get-support-open-case#open-case){:new_window}。|
|vSphere ESXi 主机处于断开连接状态或无响应状态|有关更多信息，请参阅[排除一个在无响应的状态中的 ESXi/ESX 主机 (1003409)](https://kb.vmware.com/s/article/1003409?lang=en_US){:new_window}。|
|紫屏死机|紫屏死机 (PSOD) 属于内核严重错误，vSphere ESXi 内核 (vmkernel) 触发此安全措施以响应无法恢复的事件/错误，并且这意味着继续运行将对服务和 VM 构成高风险。发生此严重错误并且 vSphere ESXi 主机崩溃时，会终止在该主机上运行的所有服务以及所有托管的 VM。VM 不是正常关闭，而是相当突然地关闭电源。如果主机是集群的一部分，并且已配置 HA，那么会在集群中的其他主机上重新启动这些 VM。有关更多信息，请参阅[知识 - KB0012864 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=dd5d2330db11f300c4fa302f9d96198d){:new_window}。|

### 存储
{: #opsprocs-trouble-common-storage}

表 3. 典型存储器故障诊断

|标题|描述|
|---|---|
|存储器故障诊断|有关性能变慢、不可预测的故障、磁盘损坏或 VM 损坏的更多信息，请参阅 [Troubleshooting storage issues when using VMware products (2013160)](https://kb.vmware.com/s/article/2013160?lang=en_US){:new_window}。|
|vSAN 故障诊断|有关更多信息，请参阅 [vSAN 故障处理](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-35A4B700-6640-4519-A885-440A1AE8D3BD.html){:new_window}。|
|vSAN 磁盘故障|有关识别发生故障的磁盘和请求更换的更多信息，请参阅 [VMware vSAN 磁盘组中的一个硬盘/磁盘失败 (2077185)](https://kb.vmware.com/s/article/2077185){:new_window}。 |
|清除 vSAN 运行状况问题|在 VMware vSphere Web Client 的“监视”页面上，可能会看到与 vSAN 运行状况问题相关的警报和警告。有关清除这些问题的信息，请参阅[虚拟 SAN 运行状况警报和警告](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_vsan_alerts#trbl_vsan_alerts){:new_window}。|
|vSAN 重新均衡|如果磁盘在运行状况检查中报告错误，指示集群不均衡，一些磁盘的空间使用率高，而另一些磁盘的使用率却非常低，那么您应该运行主动重新均衡。这将手动启动 vSAN 集群中对象的重新均衡。有关 vSAN 主动重新均衡以及此操作可能的适用情况的更多信息，请参阅 [vSAN 主动再平衡 (2149809)](https://kb.vmware.com/s/article/2149809){:new_window}。|
|启动 vSAN 运行状况测试|如果您怀疑 vSAN 存在问题，那么可以启动运行状况测试，以验证集群组件是否按预期工作。运行 VM 创建测试会在集群中的每个主机上创建 VM，然后将其删除。如果这些任务成功，说明集群组件在按预期工作，并且集群在正常运行。然后，使用网络性能测试来检测和诊断连接问题，并确保主机之间有充足的网络带宽。有关更多信息，请参阅[主动测试](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-B88B5900-33A4-4821-9659-59861EF70FB8.html){:new_window}。|
|监视 vSAN 性能|有关更多信息，请参阅[监控 vSAN 性能](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-3D2D1382-9DDC-44D4-AF3B-ACA4F1DDBDCC.html){:new_window}。性能图表可用于集群、主机、物理磁盘、VM 和虚拟盘。|
|vSAN 故障诊断|有关更多信息，请参阅[处理故障以及对 vSAN 进行故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-0F3C4D3F-9B86-4879-9C60-D6A977523112.html){:new_window}。|


### 网络
{: #opsprocs-trouble-common-network}

表 4. 典型网络故障诊断

|标题|描述|
|---|---|
|NSX Edge 的 /var/log 在活动 Edge 上将满|如果获得警报称 Edge 磁盘将满，并发现 /var/log 分区将满，请参阅 [NSX Edge /var/log is getting full on active Edge (50108355)](https://kb.vmware.com/s/article/50108355){:new_window}，以获取针对此情况的变通方法的信息。|
|测试 HCX 带宽|有关使用“perftest”来查找 HCX 隧道内可用带宽（如果您认为 HCX 有网络带宽问题）的信息，请参阅 [Steps to Run Perftest in HCX (56211)](https://kb.vmware.com/s/article/56211?lang=en_US){:new_window}。对于每个 perftest，都会执行双向测试。对于网关对，一个网关位于称为 OnPrem 的源数据中心内，另一个位于 {{site.data.keyword.cloud_notm}} 中。对吞吐量工作执行 perftest 的方法是让发送方以链接可持续的最快速度执行发送。因此，对于每个测试，都会看到“发送方”速率高于“接收方”速率，并且可以使“接收方”速率与单向吞吐量结果的数字相同。|
|HCX 故障诊断|有关更多信息，请参阅 [HCX 故障诊断](/docs/services/vmwaresolutions?topic=vmware-solutions-vcshcx-troubleshooting#vcshcx-troubleshooting){:new_window}。|
|HCX 同步状态的进度为 0% ，字节数为 0，并且状态为“错误”|有关更多信息，请参阅 [HCX replication are in Syncing state with 0% progress and 0 bytes with status Error (56710)](https://kb.vmware.com/s/article/56710?lang=en_US#q=HCX){:new_window}。|
|VM 网络性能不佳|复查 VM 虚拟 NIC 设置。VMware 建议 VM 使用 VMXNET 3 虚拟 NIC，因为这是从头设计的最新一代半虚拟化 NIC，旨在实现高性能。使用 VMware 兼容性列表来检查 VMXNET 3 的兼容性，如果支持，请更改虚拟 NIC 以获取额外的网络性能。有关更多信息，请参阅[网络故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.networking.doc/GUID-217384C2-B361-471D-90C8-BC2676A0ECA6.html){:new_window}。|

### vCenter
{: #opsprocs-trouble-common-vcenter}

表 5. 典型 vCenter 故障诊断

|标题|描述|
|---|---|
|虚拟机控制台访问|有关更多信息，请参阅[知识 - KB0012863 v0.01](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=5446a73cdb1db300c4fa302f9d961934){:new_window}。|
|新 vCenter Server 证书似乎未装入|更换缺省 vCenter Server 证书后，新证书似乎未装入。有关更多信息，请参阅[似乎不加载新的 vCenter Server 证书](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-415CF843-42E8-4AD7-98EC-7265227337B6.html){:new_window}。|
|vCenter Server 无法连接到受管主机|更换缺省 vCenter Server 证书并重新启动系统后，vCenter Server 无法连接到受管主机。有关更多信息，请参阅 [vCenter Server 无法连接到受管主机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-8D3DCEC4-50B6-4523-BF24-0DE6C65600E9.html){:new_window}。|
|使用定制 SSL 证书时无法配置 vSphere HA|安装定制 SSL 证书后，尝试启用 vSphere 高可用性 (HA) 失败。有关更多信息，请参阅[使用自定义 SSL 证书时无法配置 vSphere HA](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-3FC16DC8-7157-4340-AB8A-B8DC87D7DC0F.html){:new_window}。|

### 许可证
{: #opsprocs-trouble-common-licenses}

表 6. 典型许可证故障诊断

|标题|描述|
|---|---|
|许可证配置不兼容或不正确|有关更多信息，请参阅[主机许可故障排除](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-B9DAAF47-94EC-47F5-8523-9C8C019412E1.html){:new_window}。|
|VM 的电源无法打开|如果在 vSphere ESXi 主机上无法打开 VM 电源，并且您收到``主机 60 天评估期已到期或主机许可证已到期``消息，说明可能存在许可证问题。有关更多信息，请参阅[无法打开虚拟机电源](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-D4770546-9F9A-4F1E-AC1C-CF313E6130F4.html){:new_window}。|
|功能不可用或无法更改配置|有关更多信息，请参阅[无法配置或使用功能](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vcenterhost.doc/GUID-26C0E2F0-A581-4A5A-B1F7-2BA4F151E27A.html){:new_window}。|


## 相关链接
{: #opsprocs-trouble-links}
* [联系 IBM 支持人员](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-trbl_support#trbl_support)
* [故障诊断准则 - KB0012073](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=4a205910dbe0f7c06001327e9d96197b){:new_window}
* [使用日志文件进行故障诊断 - KB0012074](https://watson.service-now.com/nav_to.do?uri=kb_knowledge.do?sys_id=c74f91d0dbe4f7c06001327e9d9619b1){:new_window}
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)
* [支持日志收集](https://kb.vmware.com/s/article/1010705){:new_window}
* [监控事件、警报和自动操作](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}
* [vSphere 系统日志文件](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-DABCB024-E083-4A4D-8AE0-D1AF4CB3800C.html){:new_window}
* [关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

# Mission Critical VMware on IBM Cloud 概述

Mission Critical VMware on {{site.data.keyword.cloud}} 交付多专区云体系结构，可帮助企业防止云应用程序发生停机时间，并可自动在云区域内执行故障转移。

利用这种云体系结构，客户可以实现的可用性和故障转移成功率，要高于大多数 VMware 客户机在内部部署环境或竞争对手的云平台中实现的可用性和故障转移成功率。

此体系结构支持现有旧的任务关键型工作负载（包括非云本机应用程序），目标总体可用性达 99.99%。IBM Cloud 多专区区域旨在确保在发生站点中断时，使任务关键型工作负载保持联机状态。故障站点中的工作负载将近实时自动重新启动，而相邻站点中的工作负载会保持联机且可用。

此体系结构涵盖各种企业服务，包括网络、存储器、弹性以及其他构建用于对基于云的应用程序进行监视和故障诊断的工具。此外，该体系结构还可与基于 {{site.data.keyword.cloud_notm}} 构建的 IBM Services Platform with Watson 相集成，以支持更广泛的服务用途。通过使用平台的认知能力，客户可以更有效地挖掘数据，以获取新的业务洞察，从而帮助保持持续运营。

## Mission Critical VMware on IBM Cloud 的技术规范

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 体系结构是一种端到端参考体系结构，可为客户的工作负载提供自动故障转移。此体系结构将 {{site.data.keyword.cloud_notm}} 多专区区域与涵盖以下组件的 IBM 管理的服务配合使用：

* 计算体系结构 (VMware vSphere)
* 网络体系结构（目前为 NSX-V）
* 存储体系结构 (VMware vSAN)
* 与 IBM Services Platform with Watson 集成，以支持使用服务
* 用于监视、故障诊断、性能和容量管理的工具：
  * vRealize Suite 模式（Operations、Log Insight 和 Network Insight）
  * Active Directory 模式
  * 与 Netcool/Bluecare 集成，用于自动生成凭单、警报和事件扩充
  * Resiliency 模式（备份和恢复）

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 在以下区域中可用：
* 美洲：北美南部 - 达拉斯的所有 IBM Cloud Data Center；北美东部 - 华盛顿的所有 IBM Cloud Data Center
* 欧洲：法兰克福和伦敦的所有 IBM Cloud Data Center
* 亚太地区：悉尼和东京的所有 IBM Cloud Data Center

### 基本基础架构体系结构规范

基本基础架构具有以下规范：
* 每个站点都有自己的专用 Edge 和管理集群
* 资源集群是 vSphere + vSAN 延伸集群
* 见证站点包含见证 ESXi 主机
* 单个 vCenter 和 NSX Manager 体系结构
* 具有嵌入式 Platform Services Controller (PSC) 的 vCenter Server 设备，使用基于 L3 网络体系结构的 vCenter 高可用性 (HA)
* NSX Manager 恢复使用热/备用方法来同步备份文件

### 工具和技术体系结构规范

工具和技术体系结构具有以下规范：
* vRealize Operations、vRealize Log Insight 和 vRealize Network Insight 用于提供特定于要使用的 VMware 产品（例如，NSX、vSAN 和 vSphere）的操作和管理功能
* IBM 软件定义的环境自动化工具运行状况检查 (SAT HC) 用于根据最佳实践和安全策略来验证部署
* 可选的灾难恢复 (DR) 用于恢复到区域外的 {{site.data.keyword.cloud_notm}} 站点
* Fortigate Security Appliance 或类似产品用于保护任何因特网访问以及方便与内部部署网络的活动/活动网络集成

### vSphere + vSAN 延伸集群体系结构规范

vSphere + vSAN 延伸集群体系结构具有以下规范：
* 集群提供了跨两个站点的存储和计算功能，以增强可用性。
* 来自虚拟机 (VM) 的写请求会同步写入到两个站点，从而导致发生站点到站点网络等待时间。
* 来自 VM 的读请求会在该 VM 所在的物理位置本地执行，因此避免了额外的等待时间。
* 见证站点和见证主机充当脑裂/仲裁。
* vSAN 本机加密（用于静态加密）可以与此体系结构组合使用。

### 网络体系结构规范

网络体系结构具有以下规范：
* Edge/DLR/VXLAN 与基于 BGP 度量值的路由组合使用，以方便将活动/活动站点设计为自动故障转移。
* 每个站点都有自己的一组 Edge/DLR 和 VXLAN 的概念。
* 在正常情况下，连接到 DLR-A 的任何 VM（例如 VM-A）都将位于 {{site.data.keyword.cloud_notm}} 可用性专区 #1 中，并且流量都将在本地流入流出。
* 在 VM-A 的 vMotion 活动期间，流量仍会通过 {{site.data.keyword.cloud_notm}} 可用性专区 #1 流入流出。
* 在站点或 Edge 故障期间，流量将从剩余的可用站点流出。

### 相关链接

* [请求 Mission Critical VMware on IBM Cloud](/docs/services/vmwaresolutions/services/managing_mcv.html)

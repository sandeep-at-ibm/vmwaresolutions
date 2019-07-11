---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-07"

---

# 配置任务
{: #opsprocs-configure}

供应 vCenter Server 实例后，系统管理员可能需要运行若干配置任务来定制初始环境，以符合其企业的需求，以及响应未来的服务请求。

这些配置任务包括：

* 实例和集群指南
* 虚拟机 (VM) 过程
* vCenter 过程
* vSphere ESXi 主机过程
* 存储器过程
* 网络过程

## 实例和集群指南
{: #opsprocs-configure-instance}

表 1. vCenter Server 实例和集群

|标题|描述|
|---|---|
|命名约定|首要任务之一是对 vCenter Server 实例采用命名约定。可以扩展组织使用的现有命名约定，也可以创建命名约定。有关更多信息，请参阅 [Naming Convention in VMware Validated Design 4.1](https://docs.vmware.com/en/VMware-Validated-Design/4.1/com.vmware.vvd.sddc-upgrade.doc/GUID-FCA126F1-E429-454E-B3BA-226525742DC1.html){:new_window}。在采用命名约定和更改 vCenter Server 实例中的任何名称之前，请参阅[关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact){:new_window}。|
|连接到 vCenter Server 实例|供应 vCenter 后，连接到 vCenter。初始有两种方法可执行此操作。第一种方法是部署“跳板机”服务器，以便可以使用因特网连接到跳板机，然后使用专用网络从跳板机连接到 vCenter。第二种方法是使用 {{site.data.keyword.cloud_notm}} VPN，这是从您所在位置到 {{site.data.keyword.cloud_notm}} 专用网络的 VPN 连接，允许带外管理和 vCenter 访问。有关更多信息，请参阅[虚拟专用联网 (VPN) 入门](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started)。|
|配置名称解析|要在 vCenter 中使用这些功能，请将 vCenter Server 组件的名称解析添加到工作站或跳板机，具体取决于连接方法。/etc/hosts 或 c:\Windows\System32\Drivers\etc\hosts 文件需要有 Platform Services Controller (PSC)、vCenter 和 vSphere ESXi 主机的相应条目。有关更多信息，请参阅[使用 VMware vSphere Web Client 部署 OVF 文件](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_deploy_ovf#trbl_deploy_ovf){:new_window}。|
|RBAC|有关 vSphere 环境中常见任务所需特权的信息，请参阅[常见任务的所需特权](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4D0F8E63-2961-4B71-B365-BBFA24673FDB.html){:new_window}。|
|使用定制认证中心签名证书|请查阅[将 vSphere 6.x 计算机 SSL 证书替换为证书颁发机构签名的自定义证书 (2112277)](https://kb.vmware.com/s/article/2112277){:new_window}。|
|配置 vSphere 监视|vSphere 包含用户可配置的事件和警报子系统，用于跟踪来自 vSphere 组件的事件，并将数据存储在日志文件和 vCenter 数据库中。事件是 vSphere 对象上发生的用户或系统操作的记录。有三种类型的事件：参考、警告和错误。警报是为了响应事件、一组条件或 vSphere 对象状态而激活的通知。警报具有以下严重性级别：正常（绿色）、警告（黄色）和警报（红色）。警报操作是为了响应警报而执行的操作，例如发送电子邮件通知。有关如何配置和使用 vSphere 监视的信息，请参阅[监控事件、警报和自动操作](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.monitoring.doc/GUID-9272E3B2-6A7F-427B-994C-B15FF8CADC25.html){:new_window}。|
|添加、查看和删除集群|vCenter Server 实例已部署有 vSphere ESXi 主机集群。可以向实例添加更多集群以扩展计算和存储容量。有关更多信息，请参阅[添加、查看和删除 vCenter Server 实例的集群](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters){:new_window}。|
|vCenter Server 容量|可以根据业务需求，通过添加或除去 vSphere ESXi 服务器或网络文件系统 (NFS) 存储器，扩展或收缩 VMware vCenter Server 实例的容量。有关更多信息，请参阅[扩展和收缩 vCenter Server 实例的容量](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers){:new_window}。|
|vCenter Server 实例服务|部署 vCenter Server 实例后，可以添加其他服务，例如灾难恢复、严重性或备份解决方案。不再需要这些服务时，可以将其从实例中除去。有关更多信息，请参阅[订购、查看和除去 vCenter Server 实例的服务](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices){:new_window}。|
|vCenter Server 实例更新|有关如何将更新应用于 vCenter Server 实例的信息，请参阅[将 IBM 管理组件更新应用于 vCenter Server 实例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_applyingupdates#vc_applyingupdates)。对 vCenter Server 实例应用补丁和更新的这一过程仅对管理组件自动执行。有关系统管理员手动应用 VMware 产品更新的信息，请参阅 [vCenter Server on IBM Cloud with Hybridity Bundle 概述](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-hybridity-intro#vcs-hybridity-intro){:new_window}。|
|多站点配置|多站点配置功能使用轴辐式拓扑，其中包含一个主站点和最多七个辅助站点。有关为 vCenter Server on {{site.data.keyword.cloud_notm}} 实例配置多站点配置的信息，请参阅 [vCenter Server on IBM Cloud 实例的多站点配置](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_multisite#vc_multisite){:new_window}。有关在多站点配置中删除 vCenter Server 实例的步骤的信息，请参阅[删除多站点配置中的 vCenter Server 实例](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_deletinginstance_multi#vc_deletinginstance_multi){:new_window}。|
|使用 VMware Update Manager|VMware 产品部署后，可由系统管理员进行更新。有关系统管理员如何能在 vCenter Server 实例中使用 VUM 的信息，请参阅 [VMware Update Manager 简介](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro){:new_window}。|
|关键 vCenter Server 实例组件备份|系统管理员负责 vCenter Server 实例的所有软件组件的配置、管理和监视，包括管理基础架构和工作负载的备份和可用性。作为解决方案的一部分，您可以选择部署 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 附加组件服务。Veeam 和 IBM Spectrum Protect Plus 可帮助满足备份管理组件的需求。有关备份机制和要备份的关键组件的信息，请参阅[备份组件](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup)。|
|收集 VMware 产品的诊断信息|在处理支持请求时，VMware 技术支持人员会定期请求提供诊断信息。这些诊断信息包含特定于产品的日志、配置文件以及与情境相应的数据。有关 VMware Knowledge Base 文章的 URL 以及用于收集这些信息的详细分步任务的信息，请参阅[收集 VMware 产品诊断信息 (1008524)](https://kb.vmware.com/s/article/1008524?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。有关收集 VMware NSX Edge 设备的必需诊断信息的过程的信息，请参阅 [Collecting diagnostic information for VMware NSX Edge (2079380)](https://kb.vmware.com/s/article/2079380?lang=en_US#q=Collecting%20diagnostic%20information%20for%20VMware%20NSX%20Edge%20){:new_window}。|

## VM 过程
{: #opsprocs-configure-vm}

表 2. VM 过程

|标题|描述|
|---|---|
|创建 VM|有关创建新 VM 的信息，请参阅[使用新建虚拟机向导创建虚拟机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-AE8AFBF1-75D1-4172-988C-378C35C9FAF2.html?hWord=N4IghgNiBcIMICcCmYAuSAEYMDUCWCqArpBgLJgDGAFngHaYDueq1GrmAcko7gcaQo16mAOp4AXmAQATEAF8gA)。|
|配置 VM|有关配置 VM 硬件的信息，请参阅[配置虚拟机硬件](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-4AB8C63C-61EA-4202-8158-D9903E04A0ED.html){:new_window}。|
|在 VM 上安装访客操作系统|有关将访客操作系统安装到 VM 的过程的信息，请参阅[安装客户机操作系统](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-90E7F734-D699-4603-B222-AF4DE84459C7.html){:new_window}。|
|创建快照|快照用于在生成快照时捕获 VM 的整个状态。可以在 VM 电源打开、电源关闭或暂挂时生成快照。有关更多信息，请参阅[在 VMware Host Client 中执行快照](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.html.hostclient.doc/GUID-A0D8E8E7-629B-466D-A50C-38705ACA7613.html){:new_window}。|
|还原快照|有关在快照启动时将 VM 状态复原到其先前状态的信息，请参阅[还原快照](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E0080795-C2F0-4F05-907C-2F976433AC0D.html){:new_window}。|
|除去和添加 VM 和模板|有关从 vCenter 清单中除去 VM 和 VM 模板或者从磁盘中将其删除的信息，请参阅[移除和重新注册虚拟机和虚拟机模板](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-376174FE-F936-4BE4-B8C2-48EED42F110B.html){:new_window}。|
|升级 VM / Tools |有关将 VM 升级到更高兼容性级别和更高版本 VMware Tools 的信息，请参阅[升级虚拟机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-EE77B0A9-F8FF-4785-BEAD-B6F04EE04492.html){:new_window}。|
|磁盘添加|有关将磁盘添加到现有 VM 的信息，请参阅[将硬盘添加到虚拟机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-79116E5D-22B3-4E84-86DF-49A8D16E7AF2.html){:new_window}。|
|磁盘缩减|有关缩减磁盘容量以适应现有 VM 的信息，请参阅[扩展、精简和压缩 VMware ESX 和 ESXi 的虚拟磁盘 (1002019)](https://kb.vmware.com/s/article/1002019){:new_window}。|
|磁盘扩展|有关扩展 VM 现有磁盘的大小的信息，请参阅[更改虚拟磁盘配置](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E1D541D1-DF96-467A-89B7-E84F83B2563D.html){:new_window}。|
|热迁移|有关如何通过 vMotion 在同一集群的不同 vSphere 主机之间迁移 VM 的信息，请参阅[管理虚拟机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-B7023DD7-F790-4DF8-89B4-FF09DA3DBFB1.html?hWord=N4IghgNiBcIBYHsAuACAtgSwOYCcxIFMUA3NEAXyA){:new_window}。|
|冷迁移|有关在 vCenter Server 实例之间迁移 VM 的信息，请参阅[迁移已关闭或已挂起的虚拟机](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8DE930E-8079-4AC0-AEC2-B6EA1604F4E3.html){:new_window}。|
|除去 VM|有关除去 VM 的信息，请参阅[从 vCenter Server 或从数据存储中移除虚拟机或虚拟机模板](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-27E53D26-F13F-4F94-8866-9C6CFA40471C.html){:new_window}。|
|磁盘除去|有关从 VM 中除去磁盘的信息，请参阅 [Remove a Hard Disk from a Virtual Machine](https://pubs.vmware.com/vsphere-4-esx-vcenter/index.jsp?topic=/com.vmware.vsphere.webaccess.doc_41/configuring_virtual_machine_options_and_resources/t_remove_an_existing_hard_disk.html){:new_window}。|
|VM Tools|有关 VM Tools 更新过程的信息，请参阅[创建基线并连接到清单对象](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines)。|
|确定虚拟盘格式，并将虚拟盘从精简配置格式转换为密集配置格式|有关将 VM 磁盘转换为密集配置格式（如果它创建为精简配置格式的虚拟盘）的过程的信息，请参阅[确定虚拟磁盘格式，并将虚拟磁盘从精简置备格式转换为厚置备格式](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vm_admin.doc/GUID-E8F50BEC-F575-4AB1-BC77-D9A13CDBDCF7.html){:new_window}。|
|AD/DNS 服务器操作系统更新|Microsoft Active Directory (AD) / 域名服务器 (DNS) 自动设置为仅下载更新。有关更多信息，请参阅 [Windows 自动安装更新](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_limitations#trbl_limitations-windows-update)。|

## vCenter 过程
{: #opsprocs-configure-vcenter}

表 3. vCenter 过程

|标题|描述|
|---|---|
|备份 VCSA |有关更多信息，请参阅 [vCenter Server Appliance 6.7 File-Based Backup and Restore Walkthroughs](https://blogs.vmware.com/vsphere/2018/05/vcenter-server-appliance-6-7-file-based-backup-and-restore-walkthroughs.html){:new_window}。|
|VSCA/PSC 打补丁|有关更多信息，请参阅[修补 vCenter Server Appliance 和 Platform Services Controller 设备](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vcenter.upgrade.doc/GUID-043EF6BD-78F7-412F-837F-CBDF844F850C.html){:new_window}。|
|停止、启动或重新启动 VCSA 服务|出于故障诊断和维护目的，有时需要更改 VMware vCenter Server Appliance (VCSA) 服务的状态。有关更多信息，请参阅[停止、启动或重新启动 VMware vCenter Server Appliance 6.x 服务 (2109887)](https://kb.vmware.com/s/article/2109887?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
|VCSA 的备份和复原选项概述|有关更多信息，请参阅 [Overview of Backup and Restore options in vCenter Server 6.x (2149237)](https://kb.vmware.com/s/article/2149237?lang=en_US){:new_window}。|
|配置 vCenter 电子邮件通知|有关配置在已定义的警报和定制创建的警报上触发特定条件时要发送到电子邮件地址的电子邮件通知的信息，请参阅 [Configuring an email alert for the vCenter Server alarm (2123925)](https://kb.vmware.com/s/article/2123925?lang=en_US){:new_window}。|

## vSphere ESXi 主机过程
{: #opsprocs-configure-host}

表 4. vSphere ESXi 主机过程

|标题|描述|
|---|---|
|vSphere 主机维护|需要运行维护任务（例如，升级或物理设备更换）时，会将主机置于维护模式。主机仅根据系统管理员请求才会进入或退出维护模式。在进入维护模式的主机上运行的 VM 需要迁移到其他主机（由 DRS 手动或自动迁移）或关闭。有关更多信息，请参阅[将主机置于维护模式](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html?hWord=N4IghgNiBcIG4GUAOALApgJzQAgBIHsBnAF2wFkwBLAO2LWrGoGM0QBfIA){:new_window}。|
|添加 vSphere ESXi 主机|有关更多信息，请参阅[向 vCenter Server 实例添加 ESXi 服务器](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}。
|除去 vSphere ESXi 主机|	有关更多信息，请参阅[除去 ESXi 服务器的过程](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-procedure){:new_window}。|
|裸机服务器固件修补|有关更多信息，请参阅[如果裸机服务器的固件已过时该怎么办？](/docs/bare-metal?topic=bare-metal-bm-faq#what-if-my-bare-metal-server-has-out-of-date-firmware-)|
|vSphere ESXi 主机修补|有关使用 VMware Update Manager (VUM) 不仅更新 vSphere ESXi 主机，还更新若干其他 vCenter Server 实例组件的信息，请参阅 [VMware Update Manager 简介](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-intro#vum-intro)。|
|测试主机网络连接|有关如何验证 vSphere ESXi 主机的物理网络适配器与物理交换机之间的网络链路是否在正常运行且可供使用的信息，请参阅[验证网络链接 (1003724)](https://kb.vmware.com/s/article/1003724?CoveoV2.CoveoLightningApex.getInitializationData=1&r=2&ui-communities-components-aura-components-forceCommunity-seoAssistant.SeoAssistant.getSeoData=1&other.KM_Utility.getArticleDetails=1&other.KM_Utility.getArticleMetadata=2&other.KM_Utility.getUrl=1&other.KM_Utility.getUser=1&other.KM_Utility.getAllTranslatedLanguages=2&ui-comm-runtime-components-aura-components-siteforce-qb.Quarterback.validateRoute=1){:new_window}。|
|确定 ESXi 中的网络/存储器固件版本和驱动程序版本|有关更多信息，请参阅[确定 ESXi/ESX 4.x 和更高版本中的网络/存储器固件版本和驱动程序版本 (1027206)](https://kb.vmware.com/s/article/1027206?lang=en_US#q=network%20interface%20card%20error){:new_window}。|
|对 ESXi 上的网络和 TCP/UDP 端口连接问题进行故障诊断|有关更多信息，请参阅[对 ESX/ESXi 上的网络和 TCP/UDP 端口连接问题进行故障排除 (2020669)](https://kb.vmware.com/s/article/2020669?lang=en_US#q=network%20interface%20card%20error){:new_window}。|

## 存储器过程
{: #opsprocs-configure-storage}

表 5. 存储器过程

|标题|描述|
|---|---|
|添加 {{site.data.keyword.cloud_notm}} 耐久性 NFS 存储器|有关将 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共享添加到现有集群的信息，请参阅[向 vCenter Server 实例添加 NFS 存储器](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#section-adding-nfs-storage-to-vcenter-server-instances)。|
|除去 {{site.data.keyword.cloud_notm}} 耐久性 NFS 存储器|有关从现有集群中除去 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共享的信息，请参阅[从 vCenter Server 实例中除去 NFS 存储器](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing-nfs-storage)。
|增加 {{site.data.keyword.cloud_notm}} 耐久性 NFS 存储器容量|有关向 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共享添加额外容量的信息，请参阅[扩展块存储器容量](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity)。|
|缩减 {{site.data.keyword.cloud_notm}} 耐久性 NFS 存储器容量|有关缩减 {{site.data.keyword.cloud_notm}} 耐久性 NFS 共享中的容量的信息，请参阅[扩展块存储器容量](/docs/infrastructure/BlockStorage?topic=BlockStorage-expandingcapacity#expandingcapacity)。|
|vSAN 策略最佳实践建议|有关更多信息，请参阅 [vSAN 策略设计](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure#design_virtualinfrastructure-storage-policy){:new_window}。|
|vSAN 运行状况检查启用|有关更多信息，请参阅[启用 vSAN 联机运行状况工作流程](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-updating-vsan#vum-updating-vsan-enable-vsan-workflow){:new_window}和 [vSAN Health Check Information (2114803)](https://kb.vmware.com/s/article/2114803){:new_window}。|
|启用加密|	有关使用 KMIP for VMware on {{site.data.keyword.cloud_notm}} 服务来启用加密的信息，请参阅 [KMIP for VMware on IBM Cloud 概述](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations)。有关启用 VM 加密的信息，请参阅[虚拟机加密](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.security.doc/GUID-E6C5CE29-CD1D-4555-859C-A0492E7CB45D.html){:new_window}。有关使用数据静态加密来保护 vSAN 集群中数据的信息，请参阅[在 vSAN 群集上使用加密](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-F3B2714F-3406-48E7-AC2D-3677355C94D3.html){:new_window}。|
|添加 vSAN 存储器|有关将更多 vSphere ESXi 主机添加到现有 vSAN 集群的信息，请参阅[向 vCenter Server 实例添加 ESXi 服务器](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-adding){:new_window}。添加更多主机会增加集群的 CPU、RAM 和存储器。有关 vSAN 技术的更多信息，请参阅[扩展 vSAN 群集](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-666D9839-2726-4936-8C0F-94476ECE0606.html){:new_window}。|
|除去 vSAN 存储器|有关从 vSAN 集群中除去存储器的信息，请参阅[从 vCenter Server 实例中除去 ESXi 服务器](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-vc_addingremovingservers#vc_addingremovingservers-removing){:new_window}。除去主机会减少集群的 CPU、RAM 和存储器。|
|使用缺省 vSAN 警报|缺省 vSAN 警报可用于监视集群、主机和现有 vSAN 许可证。当激活对应于警报的事件或者满足警报中指定的一个或所有条件时，会自动触发这些警报。无法编辑条件或删除缺省警报。要配置特定于需求的警报，请为 vSAN 创建定制警报。请参阅“为 vSAN 事件创建 vCenter Server 警报”。有关监视警报和事件，编辑现有警报设置，以及使用缺省 vSAN 警报来监视集群和主机、分析任何新事件并评估总体集群运行状况的信息，请参阅[使用 vSAN 默认警报](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.vsan-monitoring.doc/GUID-E7885CDE-654D-4732-A5FE-31D0AB2B2F57.html){:new_window}。|
|启用 SIOC|缺省情况下，Storage IO Control (SIOC) 处于禁用状态。如果数据存储中的 VM 性能不佳，那么可以启用 SIOC 以帮助划分存储资源的优先级。仅当存在存储争用时，才会激活 SIOC，以确保每个 VM 都能获得其在存储资源中的公平份额。使用 VM 存储策略并将该策略分配给 VM 或 VMDK 即会启用 SIOC。有关更多信息，请参阅[管理存储 I/O 资源](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-7686FEC3-1FAC-4DA7-B698-B808C44E5E96.html){:new_window}。|
|配置数据存储集群|数据存储集群是一个数据存储集合，这些存储具有共享的资源和共享的管理界面。数据存储集群对于数据存储的作用，就如同集群对于主机的作用。创建数据存储集群后，可以使用 vSphere Storage DRS 来管理存储资源。将数据存储添加到数据存储集群后，数据存储的资源即会成为数据存储集群资源的一部分。可以使用数据存储集群来聚集存储资源，这使您能够支持数据存储集群级别的资源分配策略。有关更多信息，请参阅[创建数据存储群集](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.resmgmt.doc/GUID-598DF695-107E-406B-9C95-0AF961FC227A.html){:new_window}。|

## 网络过程
{: #opsprocs-configure-networks}

表 6. 网络过程

|标题|描述|
|---|---|
|网络注意事项|有关更多信息，请参阅 [vCenter Server 实例的联网注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver){:new_window}。|
|规划 HCX|VMware Hybrid Cloud Services (HCX) 允许 vSphere 软件定义的数据中心 (SDDC) 的不同实例跨各种网络类型进行互操作。HCX 旨在解决在尝试实现 vSphere 的多实例多站点部署，以在内部部署和云提供者边界之间扩展时，用户会遇到的安全性、兼容性、复杂性和性能问题。有关更多信息，请参阅[准备安装环境](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)。|
|初始 NSX 配置|在部署 vCenter Server 实例的过程中，可以使用一个样本客户网络，此网络由专用子网、公用子网、NSX 逻辑交换机、分布式逻辑路由器和 NSX Edge 设备组成，部署并配置为执行网络地址转换。有关为 VM 配置此样本客户网络的步骤，请参阅[配置网络以将客户管理的 NSX ESG 用于 VM](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_esg_config#vc_esg_config){:new_window}。|
|添加逻辑交换机|逻辑交换机类似于 VLAN 之处是，提供了可以连接 VM 的网络连接。然后，如果 VM 连接到同一逻辑交换机，那么 VM 可以通过 VXLAN 相互通信。要添加逻辑交换机时，请务必记住要构建的特定拓扑。有关更多信息，请参阅[添加逻辑交换机](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}。|
|添加 DLR|分布式逻辑路由器 (DLR) 是一种虚拟设备，用于在连接的逻辑交换机之间进行路由（东西流量）。有关更多信息，请参阅[添加分布式逻辑路由器](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-E825C0C7-F4CC-4B26-90AF-A2167AC519DB.html){:new_window}。|
|添加 ESG|外部服务网关 (ESG) 是一种虚拟设备，用于在物理网络和逻辑网络之间进行路由（南北流量）。有关更多信息，请参阅[添加 Edge 服务网关](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-B9A97F20-4996-4E16-822C-0B98DDE70571.html){:new_window}。|
|配置 NSX Edge 防火墙规则|Edge 防火墙监视南北流量，以提供周界安全功能，包括防火墙、网络地址转换 (NAT) 以及站点到站点 IPSec 和 SSL VPN 功能。仅管理和/或上行链路接口的防火墙规则适用。有关更多信息，请参阅[使用 NSX Edge 防火墙规则](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-178B11B8-FEB1-49B8-B6FF-D069C41EEB32.html){:new_window}。|
|分布式防火墙|分布式防火墙是一种嵌入系统管理程序内核的防火墙，用于为 VM 提供网络访问控制。可以基于 VMware vCenter 对象（例如：数据中心、集群、VM 名称、IP、VLAN（DVS 端口组）、VXLAN（逻辑交换机）、安全组以及来自 Active Directory 的用户组身份）创建访问控制策略。防火墙规则在每个 VM 的 vNIC 级别强制实施，以提供一致的访问控制，即使在通过 vMotion 迁移 VM 时也同样有效。有关更多信息，请参阅[分布式防火墙](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-95600C1C-FE9A-4652-821B-5BCFE2FD8AFB.html){:new_window}。|
|配置 NAT 规则|NSX Edge 提供网络地址转换 (NAT) 服务，用于将不同的源或目标 IP 地址分配给一个 VM 或一组 VM。NAT 服务配置分为源 NAT (SNAT) 和目标 NAT (DNAT) 规则。有关更多信息，请参阅[管理 NAT 规则](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。|
|配置 NSX 负载均衡器|NSX Edge 负载均衡器支持高可用性服务，并在多个 VM 之间分发网络流量负载。它会在多个 VM 之间均匀分发入局服务请求，以便负载分发对于用户是透明的。负载均衡有助于实现最佳资源利用率，最大限度提高吞吐量，尽可能缩短响应时间，并避免超负荷。NSX Edge 提供最高至第 7 层的负载均衡。可将外部或公共 IP 地址映射到一组内部 VM，以实现负载均衡。负载均衡器在外部 IP 地址上接受 TCP、UDP、HTTP 或 HTTPS 请求，并决定要使用哪个内部服务器。端口 80 是 HTTP 的缺省端口，端口 443 是 HTTPS 的缺省端口。NSX 中提供了两种类型的负载均衡服务：单臂方式（代理方式）或内联方式（透明方式）。有关更多信息，请参阅[逻辑负载平衡器](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-152982CF-108F-47A6-B86A-0F0F6A56D628.html){:new_window}。|
|更改 NSX 密码|有关更多信息，请参阅[防火墙注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_networkingonvcenterserver#vc_networkingonvcenterserver-firewall-considerations)。|
|部署 Juniper vSRX 设备|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)用于将 FortiGate Virtual Appliance 成对部署到环境中，这可帮助通过在虚拟基础架构中实施关键安全控制来降低风险。但是，如果此服务对您不适用，那么您可以根据需要实现自己的第三方解决方案，并将 vSRX 网关添加到 vCenter Server 实例中。有关更多信息，请参阅 [Installing vSRX with VMware vSphere Web Client](https://www.juniper.net/documentation/en_US/vsrx/topics/task/installation/security-vsrx-vsphere-client-installing.html){:new_window}。|
|部署 Palo Alto VM 系列防火墙|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)用于将 FortiGate Virtual Appliance 成对部署到环境中，这可帮助通过在虚拟基础架构中实施关键安全控制来降低风险。但是，如果此服务对您不适用，那么您可以根据需要实现自己的第三方解决方案。有关将 Palo Alto VM 系列防火墙添加到 vCenter Server 实例的信息，请参阅 [Set Up a VM-Series Firewall on an ESXi Server](https://docs.paloaltonetworks.com/vm-series/8-0/vm-series-deployment/set-up-a-vm-series-firewall-on-an-esxi-server.html#){:new_window}。|
|部署 Cisco Firepower 设备|[FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服务](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)用于将 FortiGate Virtual Appliance 成对部署到环境中，这可帮助通过在虚拟基础架构中实施关键安全控制来降低风险。但是，如果此服务对您不适用，那么您可以根据需要实现自己的第三方解决方案。有关将 Cisco Firepower 设备添加到 vCenter Server 实例的信息，请参阅 [Deploy the Firepower Threat Defense Virtual Using the VMware vSphere Web Client or vSphere Hypervisor](https://www.cisco.com/c/en/us/td/docs/security/firepower/quick_start/vmware/ftdv/ftdv-vmware-qsg.html#17970){:new_window}。|
|直接链路|部署 vCenter Server 实例后，系统管理员可以通过 {{site.data.keyword.cloud_notm}} 管理 VPN 来连接到实例。然后，系统管理员可以配置对工作负载的因特网访问。但是，您可能希望使用直接连接，而不使用因特网。{{site.data.keyword.cloud_notm}} Direct Link 是 {{site.data.keyword.cloud_notm}} 网络中的一个套件，包含四个产品，在全球各地的位置可用。每个产品都支持客户在不使用公用因特网的情况下，在其远程网络环境与其 {{site.data.keyword.cloud_notm}} 部署之间创建直接专用连接。最常见的情况是，实施这些产品以支持混合工作负载、跨提供者工作负载、大型或频繁数据传输、专用工作负载或使得 {{site.data.keyword.cloud_notm}} 环境的管理工作更加轻松。有关更多信息，请参阅 [IBM Cloud Direct Link 入门](/docs/infrastructure/direct-link?topic=direct-link-get-started-with-ibm-cloud-direct-link#get-started-with-ibm-cloud-direct-link){:new_window}。有关仅可使用专用网络访问的 vCenter Server 实例的信息，请参阅[公用网络或专用网络](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-public-private-network){:new_window}。|
|部署 Web 代理|	部署 VMware Server 实例后，vCenter Server Appliance (VCSA) 无权直接访问 VMware 存储库来启用 vSAN 运行状况检查的更新。有关部署 Squid Web 代理 VM 以启用对这些存储库的访问的信息，请参阅[初始配置](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-init-config#vum-init-config-install-cfg-squid)。此过程还适用于来自不同供应商的其他代理应用程序。|
|防火墙日志记录|NSX Edge 和分布式防火墙会生成并存储日志文件，例如审计日志、规则消息日志和系统事件日志。必须为已启用防火墙的每个集群配置 syslog 服务器。有关更多信息，请参阅[防火墙日志](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-6F9DC53E-222D-464B-8613-AB2D517CE5E3.html){:new_window}。{{site.data.keyword.cloud_notm}} 中的 Operations Management 包含 vRealize Log Insights，可充当 syslog 服务器。|
|NSX 日志记录和系统事件|有关为 NSX 组件配置 syslog 服务器的信息以及有关系统事件、警报、审计日志和收集技术支持日志的信息，请参阅 [NSX 日志记录和系统事件](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.logging.doc/GUID-3F08DC2E-2D82-4C89-8829-EF1EA0160B13.html){:new_window}。|
|部署 HCX 内部部署 |有关更多信息，请参阅[内部部署 VMware HCX on IBM Cloud 实例的注意事项](/docs/services/vmwaresolutions/services?topic=vmware-solutions-standalone_considerations#standalone_considerations){:new_window}。|
|HCX 检查|HCX on {{site.data.keyword.cloud_notm}} 服务可将内部部署数据中心的网络无缝扩展到 {{site.data.keyword.cloud_notm}}，这允许 VM 在不进行任何转换或更改的情况下，迁移到 {{site.data.keyword.cloud_notm}} 或从中迁移出来。有关访问 HCX 云管理控制台并将更新应用于 HCX on {{site.data.keyword.cloud_notm}} 的信息，请参阅[管理 VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx#managing-vmware-hcx-on-ibm-cloud)。|


## 相关链接
{: #opsprocs-configure-links}

* [VMware vSphere 文档](https://docs.vmware.com/en/VMware-vSphere/index.html){:new_window}
* [NSX 安装指南](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.install.doc/GUID-DD31D6BC-2E56-4E91-B45F-FCA3E80FF786.html){:new_window}
* [NSX 管理指南](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.4/com.vmware.nsx.admin.doc/GUID-B5C70003-8194-4EC3-AB36-54C848508818.html){:new_window}
* [VMware vSAN 管理指南](https://docs.vmware.com/en/VMware-vSphere/6.7/com.vmware.vsphere.virtualsan.doc/GUID-AEF15062-1ED9-4E2B-BA12-A5CE0932B976.html){:new_window}
* [关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)

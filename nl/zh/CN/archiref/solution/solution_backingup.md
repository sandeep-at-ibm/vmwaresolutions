---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

# 备份组件
{: #solution_backingup}

您负责配置、管理和监视所有软件组件，包括管理基础架构和工作负载的备份和可用性。

作为解决方案的一部分，您可以选择部署 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 或 Veeam on {{site.data.keyword.cloud_notm}} 附加组件服务。Veeam 和 IBM Spectrum Protect Plus 可帮助满足备份管理组件的需求。

这些附加组件服务与 {{site.data.keyword.cloud_notm}} 耐久性存储器一起部署。这些服务可帮助您备份工作负载和管理组件。 [IBM Spectrum Protect Plus 体系结构概述](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_spplus){:new_window}和 [Veeam 体系结构概述](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_backup_veeam){:new_window}提供了有关规划部署和调整部署大小的有用指南。您还可以为 Veeam 部署请求[受管服务](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)。

不同的解决方案组件需要不同的备份策略。一些组件使用映像级别的备份进行保护，另一些组件通过将基于文件的备份用于其配置和数据进行保护。

## 用于基于文件的备份的文件服务器
{: #solution_backingup-fileserver-backup}

某些组件（例如，VMware vCenter Server、Platform Services Controller (PSC) 和 VMware NSX）需要将其配置备份到文件服务器。

要托管这些备份，请使用以下步骤将 Linux 文件服务器部署到集群中：

1. 从 {{site.data.keyword.cloud_notm}} 基础架构订购专用可移植子网，并在系统组件所在的 VLAN 上找到该子网。这是主机的管理 IP 地址所在的专用 VLAN。
2. 将操作系统映像上传到 VMware 管理数据存储，例如 {{site.data.keyword.cloud_notm}} 专用镜像中的 Ubuntu Server 18.04 LTS。
3. 使用先前订购的专用可移植 IP 地址将此虚拟机 (VM) 部署到管理端口组上的集群中。确保此 VM 已配置为指向 AD/DNS 服务器，并可选择将此 VM 添加到子域的 DNS。
4. 在此服务器上创建一个非 root 备份用户标识，并确保为文件传输配置并启动所有必需的服务。例如，FTP 或 SSH。
5. 确保此 VM 包含在 Veeam 或 IBM Spectrum Protect Plus 管理备份作业中。

## vCenter 基于文件的备份
{: #solution_backingup-vcenter}

VMware vCenter Server 和 PSC 提供了使用各种协议[将数据库和配置导出到文件服务器的设备管理用户界面和 API](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-3EAED005-B0A3-40CF-B40D-85AD247D7EA4.html){:new_window}。VMware 记录了一个示例，说明如何将这种情况配置为直接在 vCenter Server Appliance 和 PSC 上[作为定时作业定期运行](https://pubs.vmware.com/vsphere-6-5/index.jsp?topic=%2Fcom.vmware.vsphere.vcsapg-rest.doc%2FGUID-222400F3-678E-4028-874F-1F83036D2E85.html){:new_window}，您可以对其进行调整以适合您的使用情况。

如果您具有外部 PSC，那么必须使用此技术分别备份 vCenter Server Appliance 和 PSC。如果您具有嵌入式 PSC，那么 PSC 备份会包含在 vCenter 备份中。熟悉并计划 VMware 记录的注意事项和限制。另外，计划文件服务器上文件备份的定期轮换和到期时间。

VMware 要求备份位置为空文件夹，因此您应该计划备份轮换或自动化，使该位置保留为空以用于每个后续备份作业。
{:note}

## NSX 基于文件的备份
{: #solution_backingup-nsx}

如果发生故障，那么必须适当备份所有 NSX 组件才能将系统恢复到工作状态。此设计需要您通过 NSX Manager 备份功能来配置 NSX 备份。为此，可以[配置 NSX Manager 定期执行备份](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html){:new_window}到文件服务器。确保正确备份了文件服务器或其数据，并确保旧 NSX 备份轮换。

## 基于映像的管理虚拟机备份
{: #solution_backingup-image}

在部署实例并部署 IBM Spectrum Protect Plus 服务或 Veeam 备份服务后，为管理虚拟机配置备份作业。请计划通过至少 7 天的每日备份来备份以下 VM：

* VMware SDDC Manager（如果存在）
* Active Directory 服务器（如果存在）
* 文件备份服务器

计划分配足够的 Veeam 或 IBM Spectrum Protect Plus 许可证来备份这些虚拟机，并计划至少 2 TB 的备份存储器用于 VM。

## 附加组件服务
{: #solution_backingup-addons}

如果已将附加组件解决方案组件部署到您的实例，那么作为管理备份策略的一部分，还应计划备份这些组件：

* Zerto Virtual Replication：Zerto Virtual Manager (ZVM) 系统部署为 {{site.data.keyword.cloud_notm}} 虚拟服务器实例 (VSI)，但 Veeam 或 IBM Spectrum Protect Plus 不支持其备份。如果灾难恢复策略需要您在不执行站点故障转移的情况下恢复 ZVM，那么应使用首选 Windows 备份解决方案来备份和复原 ZVM。
* F5 BIG-IP：F5 建议使用[基于文件的 F5 配置备份](https://support.f5.com/csp/article/K13132){:new_window}，您可以将其定向到文件服务器。
* FortiGate Security Appliance 或 VM：Fortinet 建议使用[基于文件的 FortiGate 配置备份](http://help.fortinet.com/fos50hlp/54/Content/FortiOS/fortigate-best-practices-54/Firmware/Performing_Config_Backup.htm){:new_window}，您可以将其定向到文件服务器。
* HyTrust Cloud Control 和 Data Control：HyTrust 支持对 HyTrust 服务器设备进行基于映像和基于文件的备份。有关更多信息，请参阅 HyTrust 管理指南。
* VMware HCX：与 vCenter Server Appliance 类似，HCX 设备管理界面也支持创建和下载基于文件的 HCX Manager 配置备份。

## 更多注意事项
{: #solution_backingup-considerations}

如果选择将 AD/DNS 服务器部署为 {{site.data.keyword.cloud_notm}} 虚拟服务器实例 (VSI)，那么无法使用 Veeam 或 IBM Spectrum Protect Plus 对其进行备份。在这种情况下，请使用首选 Windows 备份解决方案进行备份和复原操作，或者计划使用 VMware 集群中的 AD/DNS VM 来部署实例，这可通过 Veeam 或 IBM Spectrum Protect Plus 进行备份。

从 VMware vCenter 6.5u2 开始，VMware 支持使用基于映像的备份来备份 vCenter Postgres 数据库，在备份时段内使用集成的数据库暂挂和恢复脚本来确保数据库完整性。如果已将 VMware 实例升级到 vCenter 6.5u2，那么可以选择使用 Veeam 或 IBM Spectrum Protect Plus 来备份 vCenter Server 和 PSC，而不使用基于文件的备份。如果这样做，那么必须使用 Veeam 或 IBM Spectrum Protect Plus 停顿功能来确保数据库完整性。

## 从备份复原
{: #solution_backingup-restore}

复原管理备份时有一些特殊注意事项：

* 对于 vCenter 和 PSC，VMware 提供了一个安装程序，可以部署新的虚拟设备以及从备份复原配置。
* 从备份复原设备时，安装程序会根据提供的备份信息来检测设备的类型（是 vCenter Server、PSC 还是具有嵌入式 PSC 的 vCenter）。
* 因为您是直接部署到其中一个主机，所以可能无法部署到分布式交换机或端口组。为了部署恢复的设备，您可能需要创建临时标准交换机和端口组，然后将其中一个 vmnic 临时迁移到此交换机，以便为 VM 提供网络连接。部署之后，可以将 VM 迁移到分布式端口组，然后将 vmnic 还给 dvSwitch。
* 对于 NSX，在从备份复原配置之前，可能需要重新部署 NSX Manager 和 NSX Controller。
* 确保您熟悉针对 vCenter 备份和复原的 VMware 注意事项及限制。

## 摘要
{: #solution_backingup-summary}

通过正确的规划，您可以确保 VMware 实例能够承受损失其管理组件的情况并成功恢复。对于管理基础架构和工作负载，确保定期监视备份作业的成功和备份数据的可用性，并确保定期测试备份和复原计划。

## 相关链接
{: #solution_backingup-related}

* [解决方案概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)
* [设计概述](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_overview)
* [缩放容量](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_scaling)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-11"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 将网络配置为将客户管理的 NSX ESG 用于 VM
{: #vc_esg_config}

为虚拟机配置网络，以便您可以利用 VMware vCenter Server 实例中部署的 VMware NSX Edge 服务网关 (ESG)。有关为帮助最大限度降低安全风险而实施的安全措施的更多信息，请参阅[管理服务 NSX Edge 会构成安全风险吗？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX 是一个网络虚拟化平台，支持对隔离的网络进行虚拟化，并提供多种联网服务，例如交换机、路由和防火墙。有关 NSX 的更多信息，请参阅 [NSX 概述](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}。

作为 vCenter Server 实例订购过程的一部分，将以您的名义完成以下操作：
* 订购专用客户子网供 VM（虚拟机）用于访问 {{site.data.keyword.cloud}} 基础架构专用网络。
* 订购公用客户子网以允许 VM 访问因特网。
* 在 vCenter Server 实例中部署和配置 NSX。
* 部署样本 NSX 逻辑交换机，以供客户工作负载 VM 使用。
* 部署样本 NSX 分布式逻辑路由器 (DLR)，以用于处理连接到第 2 层 (L2) 网络的本地工作负载之间的潜在东-西通信。
* 部署 NSX Edge 设备并将其配置为执行从工作负载逻辑交换机的 IP 地址范围到 NAT 规则上公共 IP 地址的网络地址转换 (NAT)。

  不会为仅供专用的实例部署 NSX Edge。
  {:note}

* 如果已安装 Veeam on {{site.data.keyword.cloud_notm}} 服务，那么会将 NSX Manager 配置为每天备份 NSX 配置。有关更多信息，请参阅[安装 Veeam on {{site.data.keyword.cloud_notm}} 时的注意事项](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations#considerations-when-you-install-veeam-on-ibm-cloud)。

## 配置 VM 联网设置的过程
{: #vc_esg_config-procedure-config-networking}

要将 NSX 用于工作负载 VM，必须在创建 VM 时完成以下步骤来配置一些设置：

1. 设置 VM 到工作负载逻辑交换机的网络适配器：
   1. 在**新建虚拟机**对话框中，单击**定制硬件**选项卡。
   2. 在**新建设备**菜单中，选择**网络**，然后单击**添加**。
   3. 在新添加的网络适配器上，从菜单中选择工作负载逻辑交换机。工作负载逻辑交换机的示例名称为 **vxw-dvs-17-virtualwire-1-sid-6000-Workload**。

   请确保未选中**工作负载转移**开关。
   {:important}

2. 确定 VM 的可用 IP 地址：
   *  IP 地址必须位于 `192.168.10.0/24` 范围内。请注意，IP 地址 `192.168.10.1` 是保留地址（请参阅**步骤 3**）。
   *  配置在 VM 上运行的操作系统的联网时，请使用所选 IP 地址和网络掩码 `255.255.255.0`。

   您负责管理分配给 VM 的 IP 地址范围。
   {:note}

3. 将 VM 的缺省网关分配为 `192.168.10.1`。此地址是工作负载 VM 所在逻辑交换机上的 NSX DLR 的 IP 地址。

## 启用 SNAT 规则的过程
{: #vc_esg_config-procedure-enable-snat-rule}

如果希望工作负载 VM 具有对因特网的出站访问权，那么必须启用关联的 SNAT（源网络地址转换）规则。通过启用 SNAT 规则，可将 VM 对因特网的访问转换到单个公共 IP 地址。在 VMware vSphere Web Client 中完成以下步骤：

1. 单击**主页 > 联网和安全性**。
2. 在导航器窗格上，单击 **NSX Edge**，然后双击名为 **customer-nsx-edge** 的边缘。
3. 单击**管理 > NAT** 以打开 **NAT** 选项卡。
4. 在表中选择缺省 SNAT 规则，然后单击表上方的绿色复选标记以启用规则。

有关 NSX Edge NAT 规则的更多信息，请参阅[管理 NAT 规则](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。

## 确定客户子网详细信息的过程
{: #vc_esg_config-procedure-identify-customer-subnets-details}

**customer-nsx-edge** 边缘旨在供您自己使用，因此您可以对其进行修改，以定义更多 NAT 规则用于入站或出站流量。这些规则必须仅使用以您的名义订购的公用或专用客户子网上的 IP 地址。

要确定客户子网的详细信息，以便可以使用订购的 IP 地址，请在 VMware vSphere Web Client 中完成以下步骤：

1. 单击**主页 > 联网和安全性**。
2. 在导航器窗格上，单击 **NSX Edge**，然后在右侧窗格的边缘列表中找到 **customer-nsx-edge**。
3. 在**描述**列中，将鼠标悬停在 **customer-nsx-edge** 的边缘描述上，以查看专用和公用客户子网的子网标识。

此外，还可以通过在 {{site.data.keyword.slportal}} 中完成以下步骤，找到有关客户子网的更多详细信息：

1. 单击**联网 > IP 管理 > 子网**。
2. 单击过滤器菜单，在**子网**字段中输入标识，如 VMware vSphere Web Client 中 **customer-nsx-edge** 的描述中所示。
3. 查看为 IP 地址显示的注释。这些注释用于确定在初始设置期间订购和使用的子网和 IP 地址。

   不要使用初始设置期间订购和使用的 IP 地址。但是，可以根据需求使用这些子网上的其他 IP 地址。要设置其他网络地址转换规则，请参阅[管理 NAT 规则](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。
   {:important}

## 相关链接
{: #vc_esg_config-related}

* [故障诊断](/docs/services/vmwaresolutions/vcenter//vcenter_chg_impact.html)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge 服务网关](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}

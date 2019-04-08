---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-21"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 将网络配置为将客户管理的 NSX-T ESG 用于 VM
{: #vc_nsx-t_esg_config}

为虚拟机配置网络，以便您可以利用 VMware vCenter Server 实例中部署的 VMware NSX-T Edge 服务网关 (ESG)。有关为帮助最大限度降低安全风险而实施的安全措施的更多信息，请参阅[管理服务 NSX Edge 会构成安全风险吗？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

VMware NSX-T 是一个网络虚拟化平台，支持对隔离的网络进行虚拟化，并提供多种联网服务，例如交换机、路由和防火墙。有关 NSX 的更多信息，请参阅 [NSX 概述](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}。

作为 vCenter Server with NSX-T 实例订购过程的一部分，将代表您完成以下操作：
* 订购专用客户子网供 VM（虚拟机）用于访问 {{site.data.keyword.cloud}} 基础架构专用网络。
* 订购公用客户子网以允许 VM 访问因特网。
* 在 vCenter Server with NSX-T 实例中部署和配置 NSX-T。
* 部署样本 NSX-T 逻辑交换机，以供客户工作负载 VM 使用。
* 部署样本 NSX-T 第 1 层路由器，以用于处理连接到第 2 层 (L2) 网络的本地工作负载之间的潜在东-西通信。
* 部署 NSX-T Edge 设备并将其配置为执行从工作负载逻辑交换机的 IP 地址范围到 NAT 规则上公共 IP 地址的网络地址转换 (NAT)。

  不会为仅供专用的实例部署 NSX-T Edge。
  {:note}

## 配置 VM 联网设置的过程
{: #vc_nsx-t_esg_config-procedure-config-networking}

要将 NSX-T 用于工作负载 VM，必须在创建 VM 时完成以下步骤来配置一些设置：

1. 设置 VM 到工作负载逻辑交换机的网络适配器：
   1. 在**新建虚拟机**对话框中，单击**定制硬件**选项卡。
   2. 在**新建设备**菜单中，选择**网络**，然后单击**添加**。
   3. 在新添加的网络适配器上，从菜单中选择工作负载覆盖逻辑交换机。交换机的示例名称为 **overlay-ls**。

   请确保未选中**工作负载转移**开关。
   {:important}

2. 确定 VM 的可用 IP 地址：
   *  IP 地址必须位于 `192.168.10.0/24` 范围内。请注意，IP 地址 `192.168.10.1` 是保留地址（请参阅**步骤 3**）。
   *  配置在 VM 上运行的操作系统的联网时，请使用所选 IP 地址和网络掩码 `255.255.255.0`。

   您负责管理分配给 VM 的 IP 地址范围。
   {:note}

3. 将 VM 的缺省网关分配为 `192.168.10.1`。这是客户第 1 层逻辑路由器的下行链路路由器端口的 IP 地址，此地址连接到工作负载 VM 所在的覆盖逻辑交换机。

## 启用 SNAT 规则
{: #vc_nsx-t_esg_config-procedure-enable-snat-rule}

缺省情况下，NSX-T 支持 SNAT 规则。有关修改现有规则的信息，请参阅 [Configure Source and Destination NAT on a Tier-0 Logical Router](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/2.4/administration/GUID-45949ACD-9029-4674-B29C-C2EABEB39E1D.html){:new_window}。

## 确定客户子网详细信息的过程
{: #vc_nsx-t_esg_config-procedure-identify-customer-subnets-details}

逻辑路由器 **Customer-T1-LR** 和 **Customer-T0-LR** 以及边缘 **cust-nsx-edge0** 和 **cust-nsx-edge1** 旨在供您自己使用，因此您可以对其进行修改，以定义更多 NAT 规则用于入站或出站流量。这些规则必须仅使用以您的名义订购的公用或专用客户子网上的 IP 地址。

要确定客户子网的详细信息，以便可以使用订购的 IP 地址，请在 NSX-T Web 客户机中完成以下步骤：

1. 单击**高级联网和安全性**选项卡。
2. 在左侧窗格上，单击**光纤网**，然后在下拉列表上选择**节点**。
3. 在选项卡上，选择**边缘传输节点**。
4. 单击其中一个客户边缘。例如，**cust-nsx-edge0**。公用和专用客户子网会显示在**描述**字段中。

此外，还可以通过在 {{site.data.keyword.slportal}} 中完成以下步骤，找到有关客户子网的更多详细信息：

1. 单击**联网 > IP 管理 > 子网**。
2. 单击过滤器菜单，在**子网**字段中输入标识，如 NSX-T Web 客户机中 **customer-nsx-edge0** 的描述中所示。
3. 查看为 IP 地址显示的注释。这些注释用于确定在初始设置期间订购和使用的子网和 IP 地址。

   不要使用初始设置期间订购和使用的 IP 地址。但是，可以根据需求使用这些子网上的其他 IP 地址。要设置其他网络地址转换规则，请参阅[管理 NAT 规则](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}。
   {:important}

## 相关链接
{: #vc_nsx-t_esg_config-related}

* [关于更改 vCenter Server 工件的注意事项](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact#vcenter_chg_impact)
* [常见问题](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [NSX Edge 服务网关](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}

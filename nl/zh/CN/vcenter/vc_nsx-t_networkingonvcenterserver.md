---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-28"

---

{:faq: data-hd-content-type='faq'}

# vCenter Server with NSX-T 实例的联网注意事项
{: #vc_nsx-t_networkingonvcenterserver}

请查看以下信息，以获取有关 vCenter Server on {{site.data.keyword.cloud}} with NSX-T 实例的联网注意事项和需求的详细信息。确保满足这些需求，以便实例能正常运行。

## vCenter Server with NSX-T 实例的联网组件
{: #vc_nsx-t_networkingonvcenterserver-networking-components}
{: faq}

要查看 vCenter Server NSX-T 实例中包含的联网组件，请参阅 [vCenter Server NSX-T 实例的技术规范](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_overview-specs)。

## 防火墙注意事项
{: #vc_nsx-t_networkingonvcenterserver-firewall-considerations}
{: faq}

如果在使用防火墙，那么必须针对来自 {{site.data.keyword.IBM}} CloudDriver 虚拟服务器实例 (VSI) 和 SDDC Manager 虚拟机 (VM) 的所有通信配置规则。这些规则必须允许所有协议在 IP 地址 `10.0.0.0/8` 和 `161.26.0.0/16` 上进行通信。此类防火墙的示例为 NSX 分布式防火墙 (DFW) 或 Vyatta 防火墙。

## 将 NSX 与虚拟机配合使用
{: #vc_nsx-t_networkingonvcenterserver-using-nsx-with-vm}
{: faq}

在使用 NSX-T 的 vCenter Server 实例部署期间，将在该实例中订购、安装、许可和配置 VMware NSX。此外，还会设置 NSX Manager、NSX Controller 和 NSX 传输区域，并且每个 ESXi 服务器都会配置有 NSX 组件。

此外，还部署了 NSX Edge 服务网关，以供工作负载 VM 使用。有关更多信息，请参阅[配置网络以将客户管理的 NSX ESG 用于 VM](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_esg_config#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)。

## 更改 NSX 组件密码时的注意事项
{: #vc_nsx-t_networkingonvcenterserver-change-nsx-component-password-considerations}
{: faq}

在更改 NSX Manager、NSX Controller 和 NSX Edge 的密码之前，请查看以下注意事项：
* 不要更改 NSX Manager 的密码，此密码可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中实例的**摘要**页面上找到。
* 可以更改 NSX Controller 的密码。有关如何更改 NSX Controller 密码的指示信息，请参阅[更改控制器密码](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)。
* 可以更改客户管理的 VMware NSX Edge 服务网关 (ESG) 的密码和 SSH 设置。不要更改“管理 VMware NSX Edge 服务网关 (ESG)”及相关分布式逻辑路由器的密码。

## 相关链接
{: #vc_nsx-t_networkingonvcenterserver-related}

* [NSX 概述](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge 服务网关](https://www.ibm.com/cloud/garage/architectures/implementation/virtualization_nsx){:new_window}
* [管理 NAT 规则](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}

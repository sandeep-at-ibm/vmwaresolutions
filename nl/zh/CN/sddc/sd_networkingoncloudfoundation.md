---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-04"

---

# Cloud Foundation 实例的联网注意事项

请查看以下信息，以获取有关 Cloud Foundation 实例的联网注意事项和需求的详细信息。确保满足这些需求，以便实例能正常运行。

## Cloud Foundation 实例的联网组件

要查看 Cloud Foundation 实例中包含的联网组件，请参阅 [Cloud Foundation 实例组件](sd_cloudfoundationoverview.html#cloud-foundation-instance-components)。

## 防火墙注意事项

如果使用的是 NSX 分布式防火墙 (DFW)，请查看以下需求：
* 必须针对来自 {{site.data.keyword.IBM}}CloudDriver 和 SDDC Manager 虚拟机 (VM) 的所有通信配置规则，以允许所有协议在 IP 地址 `10.0.0.0/8` 和 `161.26.0.0/16` 上进行通信。
* 必须创建允许将 HTTPS 流量从 IBM CloudDriver VM 传递到任何目标的 DFW 规则。
* 该 DFW 规则必须位于会阻止流量进出这些 VM 的其他任何规则之前。

## 将 VMware NSX 用于 VM

在 Cloud Foundation 实例部署期间，将在该实例中订购、安装、许可和配置 VMware NSX。此外，还会设置 NSX Manager、NSX Controller 和 NSX 传输区域，并且每个 ESXi 服务器都会配置有 NSX 组件。

但是，如果工作负载 VM 需要相互通信并访问因特网，那么由您负责配置 NSX 以供 VM 使用。

有关如何设置 NSX 的信息：
* 对于主（单个）Cloud Foundation 实例，请参阅[针对 VMware Cloud Foundation on IBM Cloud 上的工作负载 VM 设置 NSX](https://developer.ibm.com/recipes/tutorials/setting-up-nsx-for-workload-vms-on-vmware-cloud-foundation-on-ibm-cloud-vcf/)。
* 对于多站点 Cloud Foundation 实例，请参阅[安全连接 IBM Cloud 中的专用 VMware 工作负载](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html)。

## 更改 NSX 组件密码时的注意事项

在更改 NSX Manager、NSX Controller 和 NSX Edge 的密码之前，请查看以下注意事项：
* 不要更改 NSX Manager 密码。可以在 {{site.data.keyword.vmwaresolutions_short}} 控制台中实例的**摘要**页面上找到此密码。
* 可以更改 NSX Controller 的密码。有关如何更改 NSX Controller 密码的指示信息，请参阅[更改控制器密码](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-2667DD9E-E2F5-4403-BAC2-C7D1BBC23228.html)。
* 不要更改管理 VMware NSX Edge 服务网关 (ESG) 的密码。

## 相关链接

* [NSX 概述](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx-cross-vcenter-install.doc/GUID-10944155-28FF-46AA-AF56-7357E2F20AF4.html){:new_window}
* [NSX Edge 服务网关]( https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/nsx-esg){:new_window}
* [管理 NAT 规则](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.2/com.vmware.nsx.admin.doc/GUID-5896D8CF-20E0-4691-A9EB-83AFD9D36AFD.html){:new_window}

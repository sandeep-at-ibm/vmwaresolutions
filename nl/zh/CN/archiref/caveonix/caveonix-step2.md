---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# 步骤 2 - 虚拟机部署
{: #caveonix-step2}

{{site.data.keyword.vmwaresolutions_full}} 自动化请求额外的可移植专用 IP 子网，然后“一体化”虚拟机(VM) 会配置为使用此子网中的 IP 地址，以便 Caveonix RiskForesight 组件可以实现：

- 通过 BCR 连接到 vCenter 和 NSX Manager。
- 连接到远程收集器（在 VXLAN 或托管的外部部署上）。
- 允许客户机在纵向扩展时管理 IP 地址空间。


## 相关链接
{: #caveonix-step2-related}

* [VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# 合规性
{: #opsprocs-compliance}

合规性是一组必需的需求，目的是满足监管机构或行业最佳实践制定的最低控制措施。监管合规性框架通常是宽泛的框架，提供有关范围广泛的一系列技术的指南，而来自供应商的行业最佳实践通常是特定于技术的，旨在应对技术风险。

对于 vCenter Server 实例，建议在部署后采用专用团队来管理安全性。这种职责分离应该能扩充和监视实例的安全态势。HyTrust CloudControl 可帮助团队实现这种基于角色的分离。

HyTrust DataControl 和 KeyControl 可帮助您提供工作负载保护，例如静态加密和地理围栏。您可能有兴趣部署 Caveonix RiskForesight 服务，此服务不仅可帮助您满足合规性需求，还可帮助您进行网络风险和取证管理。

VMware 安全强化指南提供了有关如何以安全方式部署和操作 VMware 产品的规范性指导信息。这些 vSphere 指南以易于使用的电子表格格式提供，包含丰富的元数据，支持进行准则分类和风险评估。指南中还包含可实现安全自动化的脚本示例。此外，还提供了比较文档，其中列出了指南后续版本之间的指导信息更改情况。

虽然在 VMware 安全强化指南中记录的许多控制措施已包含在 {{site.data.keyword.vmwaresolutions_full}} 参考体系结构中，并因此会自动进行部署，但您仍应确保根据自己的需求和企业策略，定制平台的安全态势。VMware 安全强化指南提供了您在执行此复查时需要的特定于技术的控制措施。Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} 会自动执行此合规性任务，并提供其他监管机构指导信息。

vRealize Operations Manager 允许您根据《vSphere 安全配置指南》中的合规性规则来监视 VMware 对象是否发生违例。合规性警报会在 vCenter Server 实例、主机、虚拟机、分布式端口组或分布式交换机上触发，以允许调查合规性违例。此外，对于关注健康保险可移植性和责任法案 (HIPAA) 以及支付卡行业数据安全标准 (PCI DSS) 合规性的客户，可以从 VMWare Solutions Exchange Web 站点下载 vRealize Operations Manager 合规包，然后获得许可并进行安装。这些合规包提供了警报、策略和报告，可根据 HIPAA 和 PCI 强化指南来验证 vSphere 资源。


## 相关链接
{: #opsprocs-compliance-links}

* [VMware 安全强化指南](https://www.vmware.com/uk/security/hardening-guides.html){:new_window}
* [vSphere 安全指南](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:new_window}
* [Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fsa_considerations#fsa_considerations)
* [Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-fortinetvm_considerations#fortinetvm_considerations)
* [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-f5_considerations#f5_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htcc_considerations.html#hytrust-cloudcontrol-on-ibm-cloud-overview)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htdc_considerations.html#hytrust-datacontrol-on-ibm-cloud-overview)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services/htkc_considerations.html#hytrust-keycontrol-on-ibm-cloud-overview)
* [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/archiref/caveonix/caveonix-intro.html#caveonix-riskforesight)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)

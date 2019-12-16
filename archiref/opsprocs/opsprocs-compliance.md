---

copyright:

  years:  2016, 2019

lastupdated: "2019-11-07"

---

{:external: target="_blank" .external}

# Compliance
{: #opsprocs-compliance}

Compliance is a set of requirements necessary to meet the minimum controls established by either a regulatory agency or industry best practices. Regularity compliance frameworks are usually broad frameworks that provide guidance on a broad range of technology, whereas industry best practices from vendors are typically technology specific to address technological risks.

For your vCenter Server instance, it is recommended that security is managed by using a dedicated team post-deployment. This separation of duties should augment and monitor the security posture of your instance. HyTrust CloudControl can assist your teams with role-based separation.

HyTrust DataControl and KeyControl can assist you in delivering workload protection such as at-rest encryption and geo-fencing. You might be interested in deploying the Caveonix RiskForesight service to assist you in, not only your compliance requirements but also cyber-risk and forensic management.

The VMware Security Hardening Guides provide prescriptive guidance on how to deploy and operate VMware products in a secure manner. Guides for vSphere are provided in an easy to use spreadsheet format, with rich metadata to allow for guideline classification and risk assessment. They also include script examples for enabling security automation. Comparison documents are provided that list changes in guidance in successive versions of the guide.

While many of the controls documented in the VMware Security Hardening Guides have been incorporated in the {{site.data.keyword.vmwaresolutions_full}} reference architecture and, therefore, automatically deployed, ensure that you tailor the security posture of the platform to your own needs and enterprise policy. The VMware Security Hardening Guides provide the technology-specific controls that are required for you to carry out this review. Caveonix RiskForesight automates this compliance task and provides additional regulatory agency guidance.

vRealize Operations Manager allows you to monitor VMware objects for violations against the compliance rules in the vSphere Security Configuration Guide. The compliance alerts trigger on the vCenter Server instance, hosts, virtual machines, distributed port groups, or distributed switches, allowing the investigation of the compliance violation. Additionally, for clients that are interested in Health Insurance Portability and Accountability Act (HIPAA) and Payment Card Industry Data Security Standard (PCI DSS) compliance, vRealize Operations Manager Compliance Packs can be downloaded from the VMWare Solutions Exchange website, licensed, and installed. These Compliance Packs provide Alerts, Policies, and Reports to validate the vSphere resources against the HIPAA and PCI hardening guides.

## Related links
{: #opsprocs-compliance-links}

* [VMware security hardening guides](https://www.vmware.com/uk/security/hardening-guides.html){:external}
<!-- * [vSphere security](https://docs.vmware.com/en/VMware-vSphere/6.7/vsphere-esxi-vcenter-server-67-security-guide.pdf){:external} -->
* [Fortigate Security Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-fsa_considerations)
* [Fortigate Virtual Appliance](/docs/services/vmwaresolutions?topic=vmware-solutions-fortinetvm_considerations)
* [F5 BIG-IP](/docs/services/vmwaresolutions?topic=vmware-solutions-f5_considerations)
* [HyTrust CloudControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htcc_considerations)
* [HyTrust DataControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htdc_considerations)
* [HyTrust KeyControl](/docs/services/vmwaresolutions?topic=vmware-solutions-htkc_considerations)
* [Caveonix RiskForesight](/docs/services/vmwaresolutions?topic=vmware-solutions-caveonix_considerations)
* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-opsmgmt-intro)

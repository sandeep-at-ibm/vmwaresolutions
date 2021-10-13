---
copyright:
  years: 2020, 2021
lastupdated: "2021-09-10"

keywords: security and compliance for VMware Solutions, security for VMware Solutions, compliance for VMware Solutions

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Managing security and compliance with VMware Solutions
{: #manage-scc}

With {{site.data.keyword.cloud}} VMware® Solutions, you can integrate with the {{site.data.keyword.compliance_short}} to manage security and compliance for your organization.
{: shortdesc}

With the {{site.data.keyword.compliance_short}}, you can monitor for controls that pertain to your VMware Solutions infrastructure and workloads.

## Monitoring security and compliance posture with VMware Solutions by using Caveonix
{: #manage-scc-monitor}

With VMware Solutions, you can optionally use [Caveonix RiskForesight service](/docs/vmwaresolutions?topic=vmwaresolutions-caveonix_considerations) to report security and compliance posture and findings to {{site.data.keyword.compliance_short}}.

This integration requires you to [establish a public connection](/docs/security-advisor?topic=security-advisor-setup-caveonix#connect-caveonix) from RiskForesight™ to {{site.data.keyword.compliance_short}} and [schedule a job](/docs/security-advisor?topic=security-advisor-setup-caveonix#caveonix-job) to periodically report findings.

RiskForesight reports a compliance and security posture summary to {{site.data.keyword.compliance_short}}, and a categorized list of cyberrisk findings. Details of these findings are visible both in {{site.data.keyword.compliance_short}} and in RiskForesight.

As a security or compliance focal, you can use this information to ensure that your organization is adhering to the external and internal standards for your industry. You can also identify potential issues as they arise.

For more information about monitoring your resources, see [Getting started with {{site.data.keyword.compliance_short}}](/docs/security-compliance?topic=security-compliance-getting-started).

## Related links
{: #manage-scc-related}

* [Managing access for VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-iam)
* [Securing your data in VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-data-security-mng-data)
* [Auditing events for VMware Solutions](/docs/vmwaresolutions?topic=vmwaresolutions-at-events)

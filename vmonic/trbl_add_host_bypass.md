---

copyright:

  years:  2020, 2021

lastupdated: "2021-09-10"

keywords: troubleshooting, bypassing signing and acceptance, bypassing verification issue

subcollection: vmwaresolutions


---

{{site.data.keyword.attribute-definition-list}}

# Why do I see a bypassing verification message when I add a host?
{: #trbl_add_host_bypass}
{: troubleshoot}

When you add a host, you see the following event in VMware vCenter Server®:
{: tsSymptoms}

`Attempting to install an image profile bypassing signing and acceptance level verification.`

This event occurs because VMWare is installing the High Availability agent by intended bypassing acceptance level verification.
{: tsCauses}

This message does not indicate a problem and it can be ignored.
{: tsResolve}

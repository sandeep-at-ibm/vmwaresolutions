---

copyright:

  years:  2016, 2020

lastupdated: "2020-02-21"

keywords: vCenter Server Hybridity delete instance, delete vCenter Server Hybridity, delete multi-site

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deleting vCenter Server with Hybridity Bundle instances in a multi-site configuration
{: #vc_hybrid_deletinginstance_multi}

There are special considerations to be aware of before you plan to delete VMware vCenter Server with Hybridity Bundle instances that are part of a multi-site configuration.

When you delete a vCenter Server with Hybridity Bundle instance, the following components are released sequentially:
1. All deployed services
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by the {{site.data.keyword.cloud}} infrastructure, which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure billing cycle for the deleted instance.
{:note}

## Procedure to delete vCenter Server with Hybridity Bundle instances in a multi-site configuration
{: #vc_hybrid_deletinginstance_multi-procedure}

1. Remove all services from the secondary vCenter Server with Hybridity Bundle instance.
2. Ensure that you do not have any NSX objects that are expanded into the secondary instance that you want to delete.
3. Delete the secondary vCenter Server from the primary SSO (Single Sign-On) domain. For more information, see [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/s/article/2106736){:external}.
4. Demote the local domain controller Virtual Service Instance (VSI). For more information, see [Demoting domain controllers and domains](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:external}.
5. Delete the secondary vCenter Server with Hybridity Bundle instance from the {{site.data.keyword.vmwaresolutions_short}} console.
6. Repeat steps 1 - 5 for all secondary vCenter Server with Hybridity Bundle instances in your multi-site configuration.
7. After you delete all secondary instances, you can also delete the primary instance from the {{site.data.keyword.vmwaresolutions_short}} console.

## Related links
{: #vc_hybrid_deletinginstance_multi-related}

* [Deleting vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_deletinginstance)
* [Ordering, viewing, and removing services from vCenter Server with Hybridity Bundle instances](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Canceling virtual servers](/docs/vsi?topic=virtual-servers-managing-virtual-servers#cancel)

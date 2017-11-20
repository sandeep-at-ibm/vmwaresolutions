---

copyright:

  years:  2016, 2017

lastupdated: "2017-11-20"

---

# Deleting vCenter Server instances in a multi-site configuration

There are special considerations to be aware of before you plan to delete vCenter Server instances that are part of a multi-site configuration.

When you delete a vCenter Server instance, the following components are released sequentially:
1. All deployed services
2. Support and Services fee
3. VMware product licenses
4. ESXi servers
5. Subnets
6. VLANs

Because of resource dependencies, the components in your instance are not released immediately when you delete the instance. For example, the subnets and VLANs cannot be deleted until the ESXi servers are fully reclaimed by {{site.data.keyword.cloud}} infrastructure (SoftLayer), which happens at the end of the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) billing cycle. At the end of the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) billing cycle, which is typically 30 days, the subnets and VLANs are deleted and the instance deletion is completed.

**Attention**: You are billed until the end of the {{site.data.keyword.cloud_notm}} infrastructure (SoftLayer) billing cycle for the deleted instance.

## Procedure

1. Remove all services from the secondary vCenter Server instance.
2. Ensure that you do not have any NSX objects expanded into the secondary instance that you want to delete.
3. Delete the secondary vCenter and PSC (Platform Services Controller) from the primary SSO (Single Sign-On) domain. For more information, see [Unregister vCenter Server from Single Sign-On](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2106736){:new_window}.
4. Demote the local domain controller VSI (Virtual Service Instance). For more information, see [Demoting domain controllers and domains](https://technet.microsoft.com/en-us/windows-server-docs/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Delete the secondary vCenter Server instance from the {{site.data.keyword.vmwaresolutions_full}} console.
6. Repeat from steps 1 to 5 for all secondary vCenter Server instances in your multi-site configuration.
7. After deleting all secondary instances, you can also delete the primary instance from the {{site.data.keyword.vmwaresolutions_short}} console.

## Related links

* [Deleting vCenter Server instances](vc_deletinginstance.html)
* [Removing services from vCenter Server instances](vc_addingremovingservices.html)

---

copyright:

  years:  2021

lastupdated: "2021-10-26"

keywords: manage shared resources, access the vCloud Director Management console

subcollection: vmwaresolutions

---

{{site.data.keyword.attribute-definition-list}}

# Accessing the vCloud Director Management console
{: #shared_accessing-vcd-console}

You can use the vCloud Director Management console to manage the {{site.data.keyword.cloud}} for VMware® Solutions Shared virtual data centers. You can access the vCloud Director console from the virtual data center details page.

## Before you begin
{: #shared_accessing-vcd-console-prereq}

- The first time that you access the vCloud Director console for the virtual data center region, you must set the **admin** credentials to generate an initial, complex, and random password. After the first **admin** password is generated, the **vCloud Director console** option is enabled on the virtual data center details page.
- You do not need to generate an **admin** password for each virtual data center. Reuse the same password for all virtual data centers in the same region.

{{site.data.keyword.vmwaresolutions_short}} does not store the **admin** password. After a password is generated, you must capture it. If the password is lost or you get locked out of your account, you can generate a new password at any time.
{: note}

## Procedure to access the vCloud Director Management console
{: #shared_accessing-vcd-console-procedure}

1. From the **Properties** pane on the virtual data center details page, click **Set Organization Admin Password** to generate a random password.
2. On the upper right of the virtual data center details page, click **vCloud Director console** to access the console.
3. Use the **admin** username and password to log in to the vCloud Director console.

   After the **admin** is logged in to the vCloud Director console, you can create additional users who have roles that allow them to access the vCloud Director console.

   All virtual data centers in the same region have the same **admin** password. Resetting the password on a virtual data center resets the **admin** password for accessing the vCloud Director Management console for all virtual data centers in the same region.
   {: important}

## Related links
{: #shared_accessing-vcd-console-related}

* [Resizing virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_resize)
* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [Deleting VMware Solutions Shared virtual data centers](/docs/vmwaresolutions?topic=vmwaresolutions-shared_deletinginstance)
* [Viewing the virtual data center summary](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-summary)
* [Viewing virtual data center details](/docs/vmwaresolutions?topic=vmwaresolutions-shared_viewing-vdc-details)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){: external}

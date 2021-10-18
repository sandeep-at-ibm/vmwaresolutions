---

copyright:

  years:  2020, 2021

lastupdated: "2021-10-13"

keywords: troubleshooting VMware Solutions Shared, data center, VMware Solutions Shared data centers, Business Partners

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:term: .term}

# Limitations and workarounds for Business Partner users
{: #shared_bnpp}

Review the following considerations and limitations that Business Partner users can experience.

## High availability in stretched locations
{: #shared_bnpp-ha}

For Business Partner users, {{site.data.keyword.cloud}} for VMware® Solutions Shared virtual data centers support highly availability for in-cloud replication from one virtual data center to another. However, ordering a Zerto Cloud Connector (ZCC) to replicate on-premises virtual machines (VMs) to {{site.data.keyword.cloud_notm}} does not support high availability.

## Resetting passwords
{: #shared_bnpp-pw-reset}

Business Partner users cannot use one virtual data center to reset the vCloud Director account password for the entire data center region.

For Business Partner users, all virtual data centers in the same data center number group have the same password. Groups with the same data center number can reset the vCloud Director account password from any virtual data center in the number group.

For example, ``PAR04- windows`` and ``PAR04- linux`` are in a group with the same data center number. When you reset the vCloud Director password in either, the password is reset for any virtual data center in ``PAR04``. The password is not reset for the ``PAR05`` or ``PAR06`` data center number groups.

## Related links
{: #shared_bnpp-related}

* [Operating VMware Solutions Shared](/docs/vmwaresolutions?topic=vmwaresolutions-shared_vcd-ops-guide)
* [VMware vCloud Director](https://www.vmware.com/ca/products/vcloud-director.html){: external}

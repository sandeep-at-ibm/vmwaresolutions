---

copyright:

  years:  2016, 2020

lastupdated: "2020-09-22"

subcollection: vmwaresolutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto
{: #vum-zerto}

If you find that a vSphere ESXi host can't enter maintenance mode during remediation, it might be that Zerto is stopping it. If you've updated Zerto since the initial deployment, then complete the following steps to correct this. If you haven't updated, complete the following instructions at [How to place a host with an associated VRA into maintenance mode](https://www.zerto.com/myzerto/knowledge-base/how-to-place-a-host-with-an-associated-vra-into-maintenance-mode/){:external}.

1. Log in to the Zerto web user interface.
2. Select **Site Settings** from the menu.
3. Select the **Policies** tab and ensure that **Allow Zerto to always enter hosts to maintenance mode during remediation** is selected.
4. Log out of Zerto.

**Next topic:** [Host Profiles](/docs/vmwaresolutions?topic=vmwaresolutions-vum-host-profiles)

## Related links
{: #vum-zerto-related}

* [VMware HCX solution architecture](/docs/vmwaresolutions?topic=vmwaresolutions-hcx-archi-intro#hcx-archi-intro)
* [{{site.data.keyword.vmwaresolutions_short}} Demos](https://www.ibm.com/demos/collection/IBM-Cloud-for-VMware-Solutions/) (demonstrations)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Zerto
{: #vum-zerto}

If you find that a vSphere ESXi host can't enter maintenance mode during remediation, it might be that Zerto is stopping it. If you've updated Zerto since the initial deployment, then complete the following steps to correct this. If you haven't updated, complete the following instructions at [How to place a host with an associated VRA into maintenance mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Log in to the Zerto web user interface.
2. Select **Site Settings** from the drop-down menu.
3. Select the **Policies** tab and ensure that **Allow Zerto to always enter hosts to maintenance mode during remediation** is selected.
4. Log out of Zerto.

## Related links
{: #vum-zerto-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} solution architecture](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (demonstrations)

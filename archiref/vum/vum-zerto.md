---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-01"

---

# Zerto

If you find that a vSphere ESXi host cannot enter maintenance mode during remediation, it might be that Zerto is stopping it. If you have updated Zerto since the initial deployment, then carry out the following steps to correct this. If you have not updated, follow the instructions at  [How to place a host with an associated VRA into maintenance mode](https://www.zerto.com/myzerto/knowledge-base/place-host-into-maintenance-mode-with-vra/).

1. Log in to the Zerto web user interface.
2. Select **Site Settings** from the drop-down menu.
3. Select the **policies tab** and ensure that **Allow Zerto to always enter hosts to maintenance mode during remediation** is selected.
4. Log out of Zerto.

### Related links

* [VMware HCX on {{site.data.keyword.cloud}} Solution](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/ibm-vmware) (Demos)

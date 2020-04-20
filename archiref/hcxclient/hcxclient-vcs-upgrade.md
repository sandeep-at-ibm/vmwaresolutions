---

copyright:

  years:  2016, 2020

lastupdated: "2020-03-30"

subcollection: vmware-solutions


---

# Upgrading HCX components
{: #hcxclient-vcs-upgrade}

Upgrading HCX is a simple process that uses the client web user interface (UI) on the client-side HCX manager update and the cloud web UI on the cloud side HCX manager update.

You must upgrade both sides as any fleet component updates cause both to redeploy the fleet components with the level of code that is installed on HCX Manager.

If VMware Support asks for the System ID, provide both the client and cloud side. Use SSH into the HCX manager (client or cloud) and run `cat /common/location` to locate the System ID.

**Next topic:** [HCX troubleshooting](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-troubleshooting)

## Related links
{: #hcxclient-vcs-upgrade-related}

* [Glossary of HCX components and terms](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-components)
* [Preparing the installation environment](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX Client deployment](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX on-premises Service Mesh](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud migrations](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-migrations)
* [Monitoring parameters and components](/docs/vmwaresolutions?topic=vmware-solutions-hcxclient-monitoring)

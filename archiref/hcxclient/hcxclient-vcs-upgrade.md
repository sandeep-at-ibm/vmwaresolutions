---

copyright:

  years:  2016, 2021

lastupdated: "2021-04-19"

subcollection: vmwaresolutions


---

# Upgrading HCX components
{: #hcxclient-vcs-upgrade}

Upgrading VMware® HCX is a process that uses the client web UI on the client-side HCX Manager update and the cloud web UI on the cloud side HCX Manager update.

You must upgrade both sides as any fleet component updates cause both to redeploy the fleet components with the level of code that is installed on HCX Manager.

If VMware Support asks for the system ID, provide both the client and cloud side. Use SSH into HCX Manager (client or cloud) and run `cat /common/location` to locate the System ID.

**Next topic:** [HCX troubleshooting](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-troubleshooting)

## Related links
{: #hcxclient-vcs-upgrade-related}

* [Glossary of HCX components and terms](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-components)
* [Preparing the installation environment](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-planning-prep-install)
* [HCX Client deployment](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-vcs-client-deployment)
* [HCX on-premises Service Mesh](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-vcs-mesh-deployment)
* [VMware Hybrid Cloud migrations](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-migrations)
* [Monitoring parameters and components](/docs/vmwaresolutions?topic=vmwaresolutions-hcxclient-monitoring)

---

copyright:

  years: 2016, 2019

lastupdated: "2019-10-07"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmware-solutions


---

# Activity Tracker events
{: #at-events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in the {{site.data.keyword.cloud_notm}}. You can use this service to investigate for abnormal activity and critical actions, and comply with regulatory audit requirements. In addition, you can be alerted on actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see [{{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).

## Tracking instance management events
{: #at-events-instance-mgmt}

When you manage user accounts, instances, clusters, and services in {{site.data.keyword.vmwaresolutions_short}}, an event is generated and sent to a global domain or to an instance of the service in the location where the service is provisioned. For more information, see [Monitoring global and location-based events](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

The following table provides the actions that generate and send management events to Activity Tracker.

| Action                                   | Description |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | The infastructure API key for an account is updated. |
| `vmware-solutions.account-notification.update` | The notification setting for an account is updated. |
| `vmware-solutions.instance-secure-data.wipe` | The instance secure data is wiped. |
| `vmware-solutions.instance-bss-account.migrate` |	An instance is migrated to a BSS account. |
| `vmware-solutions.vcs.create` | A vCenter Server instance is created. |
| `vmware-solutions.vcs.delete` | A vCenter Server instance is deleted. |
| `vmware-solutions.vcs-host.add` | A host is added to a vCenter Server instance. |
| `vmware-solutions.vcs-host.remove` | A host is removed from a vCenter Server instance. |
| `vmware-solutions.vcs.update` | A vCenter Server instance is updated. |
| `vmware-solutions.vcs-cluster.create` | A cluster is created for a vCenter Server instance. |
| `vmware-solutions.vcs-cluster.delete` | A cluster is deleted for a vCenter Server instance. |
| `vmware-solutions.vcs-nsx-license.update` | The NSX license is updated for a vCenter server instance. |
| `vmware-solutions.vcs-nfs-storage.add` | NFS storage is added to a vCenter Server instance. |
| `vmware-solutions.vcs-nfs-storage.remove` | NFS storage is removed from a vCenter Server instance. |
| `vmware-solutions.vcs-plan.update` | A vCenter Server instance's plan is updated. |
| `vmware-solutions.vss.create` | A vSphere instance is created. |
| `vmware-solutions.vss.update` | A vSphere instance is updated. |
| `vmware-solutions.vss-template.remove` | A vSphere template is removed. |
| `vmware-solutions.service.create` | A service is created. |
| `vmware-solutions.service.delete` | A service is deleted. |
{: caption="Table 1. Description of actions that generate management events" caption-side="top"}

## Tracking events for the KMIP for VMware service
{: #at-events-kmip}

When you manage keys for the KMIP for VMware service, an event is generated and sent to a global domain or to an instance of the service in the location where the service is provisioned. For more information, see [Monitoring global and location-based events](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-monitor_events#mon_def_event_type).

The following table provides the actions that generate and send events for the KMIP for VMware service.

| Action                                      | Description                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | A KMIP key is created. |
| `vmware-solutions.kmip-key.retrieve` | A KMIP key is retrieved. |
| `vmware-solutions.kmip-key-attributes.retrieve` | A KMIP key's attributes are retrieved. |
| `vmware-solutions.kmip-key.activate` | A KMIP key is activated. |
| `vmware-solutions.kmip-key.revoke` | A KMIP key is revoked. |
| `vmware-solutions.kmip-key.destroy` | A KMIP key is destroyed. |
{: caption="Table 2. Description of actions that generate events for the KMIP for VMware service" caption-side="top"}

## Where to view the events
{: #at-events-viewing}

Events are available in the **Frankfurt** location.

There is only 1 {{site.data.keyword.at_full_notm}} instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_full_notm}} service in the **EU-DE** location. For more information, see [Launching the web UI through the IBM Cloud UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2).

## Related links
{: #at-events-related}

* [Provisioning an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Navigating to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

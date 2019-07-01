---

copyright:

  years: 2016, 2019

lastupdated: "2019-06-21"

keywords: vmware solutions events, activity tracker, event details

subcollection: vmware-solutions


---

# Activity Tracker events
{: #at-events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}}.

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. For more information, see the [About {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

## Activity Tracker events table
{: #at-events-table}

Check the following table for the description of the columns in the Activity Tracker events table.

| Column                | Value type | Description |
|:----------------------|:-----------|:------------|
| Time                  | N/A        | The date and time when the event is created. |
| initiator.name        | String     | The IBMid of the user that initiates the action. |
| target_name           | String     | The resource on which the action is run. |
| target.typeURI        | String     | The Universally Unique Identifier (UUID) of the target on which the action is run. |
| action                | String     | The action that triggers the event. The valid values are `create`, `update`, and `delete`. |
| outcome               | String     | The result of the action. The value is `success`, `failure`, or `pending`. |
| reason_reasonCode     | Integer    | The reason code of the outcome. |
| initiator_host_address| String     | The IP address where the request comes from. |
{: caption="Table 1. Description of the Activity Tracker events table" caption-side="top"}

For more information, see [Activity Tracker event fields](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-at_event).

## Tracking instance management events
{: #at-events-instance-mgmt}

When you manage user accounts, instances, clusters, and services in {{site.data.keyword.vmwaresolutions_short}}, an event is generated and sent to the **account domain** in Activity Tracker.

Check the following table for the actions that generate and send management events to Activity Tracker.

| Action                                   | Description | Outcome |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.account-apikey.update` |	The infastructure API key for an account is updated. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.account-notification.update` | The notification setting for an account is updated. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-secure-data.wipe` | The instance secure data is wiped. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.instance-bss-account.migrate` |	An instance is migrated to a BSS account. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.create` |	A vCenter Server instance is created. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.delete` |	A vCenter Server instance is deleted. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.add` |	A host is added to a vCenter Server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-host.remove` |	A host is removed from a vCenter Server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs.update`	| A vCenter Server instance is updated. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.create`	| A cluster is created for a vCenter Server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-cluster.delete`	| A cluster is deleted for a vCenter Server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nsx-license.update`	| The NSX license is updated for a vCenter server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.add`	| The hybridity bundle is upgraded for a vCenter server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-hybridity.remove`	| The hybridity bundle is removed from a vCenter server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.add`	| NFS storage is added to a vCenter Server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-nfs-storage.remove`	| NFS storage is removed from a vCenter Server instance. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vcs-plan.update`	| A vCenter Server instance's plan is updated. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.create`	| A vSphere instance is created. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss.update`	| A vSphere instance is updated. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vss-template.remove` |	A vSphere template is removed. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.create`	| A service is created. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service.delete`	| A service is deleted. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.service-hybridity.upgrade` | A hybridity bundle is upgraded to `version`. | `pending`<br>`success`<br>`failure` |
{: caption="Table 2. Description of actions that generate management events" caption-side="top"}

## Tracking events for the KMIP for VMware on IBM Cloud service
{: #at-events-kmip}

When you manage keys for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service, an event is generated and sent to the **account domain** in Activity Tracker.

Check the following table for the actions that generate and send events for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service.

| Action                                      | Description                               | Outcome |
|:--------------------------------------------|:------------------------------------------|:-------|
| `vmware-solutions.kmip-key.create` |	A KMIP key is created. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.retrieve` |	A KMIP key is retrieved. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key-attributes.retrieve` |	A KMIP key's attributes are retrieved. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.activate` |	A KMIP key is activated. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.revoke` |	A KMIP key is revoked. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.kmip-key.destroy` |	A KMIP key is destroyed. | `pending`<br>`success`<br>`failure` |
{: caption="Table 3. Description of actions that generate events for the KMIP for VMware on {{site.data.keyword.cloud_notm}} service" caption-side="top"}

## Where to view the events
{: #at-events-viewing}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} **account domain** that is available in the {{site.data.keyword.cloud_notm}} region where the events are generated.

Use {{site.data.keyword.cloud_notm}} Activity Tracker with LogDNA to view the instance. For more information, see [Viewing events](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-view_events).

## Related links
{: #at-events-related}

* [Provisioning an instance](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision)
* [Navigating to the web UI](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)

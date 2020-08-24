---

copyright:

  years: 2016, 2020

lastupdated: "2020-08-18"

keywords: IBM, activity tracker, LogDNA, event, security, VMware solutions events

subcollection: vmwaresolutions


---

# Auditing events for VMware Solutions
{: #at-events}

Use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with {{site.data.keyword.vmwaresolutions_short}} in {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in the {{site.data.keyword.cloud_notm}}. You can use this service to investigate for abnormal activity and critical actions, and comply with regulatory audit requirements. In addition, you can be alerted on actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see [Getting started with {{site.data.keyword.cloud_notm}} Activity Tracker](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-getting-started).

## Events for VMware Solutions Shared
{: #at-events-vdc}

When you use {{site.data.keyword.vmwaresolutions_short}} Shared, an event is generated to track how users and applications interact with virtual data centers.

The following table lists the actions that generate and send an event to Activity Tracker.

| Action                                   | Description | Outcome |
|:-----------------------------------------|:------------|:-------|
| `vmware-solutions.vdc.create` | An event is generated when a virtual data center instance is created. |`pending`<br>`success`<br>`failure` |
| `vmware-solutions.vdc.delete` | An event is generated when a virtual data center instance is deleted. | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.vdc.update` | An event is generated when capacity is added to a virtual data center instance.<br>An event is generated when capacity is removed from a virtual data center instance.  | `pending`<br>`success`<br>`failure` |
| `vmware-solutions.location.update` | An event is generated when the admin credential for a virtual data center organization is reset. | `pending`<br>`success`<br>`failure` |
{: caption="Table 1. Description of actions that generate VMware Solutions Shared events" caption-side="top"}


## Events for vCenter Server instance management
{: #at-events-instance-mgmt}

When you manage user accounts, instances, clusters, and services in {{site.data.keyword.vmwaresolutions_short}}, an event is generated.

The following table provides the actions that generate and send management events to Activity Tracker.

| Action                                   | Description |
|:-----------------------------------------|:------------|
| `vmware-solutions.account-apikey.update` | The infrastructure API key for an account is updated. |
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
| `vmware-solutions.vcs-nsx-license.update` | The NSX license is updated for a vCenter Server instance. |
| `vmware-solutions.vcs-nfs-storage.add` | NFS storage is added to a vCenter Server instance. |
| `vmware-solutions.vcs-nfs-storage.remove` | NFS storage is removed from a vCenter Server instance. |
| `vmware-solutions.vcs-plan.update` | A vCenter Server instance's plan is updated. |
| `vmware-solutions.vss.create` | A vSphere instance is created. |
| `vmware-solutions.vss.update` | A vSphere instance is updated. |
| `vmware-solutions.vss-template.remove` | A vSphere template is removed. |
| `vmware-solutions.service.create` | A service is created. |
| `vmware-solutions.service.delete` | A service is deleted. |
{: caption="Table 2. Description of actions that generate management events" caption-side="top"}

## Events for KMIP for VMware
{: #at-events-kmip}

When you manage keys for the KMIP for VMware service, an event is generated.

The following table provides the actions that generate and send events for KMIP for VMware. These actions are performed by an initiator from VMware vCenter Server and do not include the initiator's IP address. The requests for these actions run from within the IBM Cloud private network.

The initiator ID is derived from the TLS (Transport Layer Security) certificate of the vCenter Server that is used to authenticate the connection to the KMIP server. The initiator ID is in the format `CertificateID-<value>`, where the value matches the fingerprint of the corresponding TLS certificate. Using the fingerprint, you can identify the vCenter Server that triggered the action.

| Action                                      | Description                               |
|:--------------------------------------------|:------------------------------------------|
| `vmware-solutions.kmip-key.create` | A KMIP key is created. |
| `vmware-solutions.kmip-key.read` | A KMIP key is retrieved. |
| `vmware-solutions.kmip-key-attributes.retrieve` | A KMIP key's attributes are retrieved. |
| `vmware-solutions.kmip-key.activate` | A KMIP key is activated. |
| `vmware-solutions.kmip-key.revoke` | A KMIP key is revoked. |
| `vmware-solutions.kmip-key.destroy` | A KMIP key is destroyed. |
{: caption="Table 3. Description of actions that generate events for the KMIP for VMware service" caption-side="top"}

## Viewing events
{: #at-events-viewing}

VMware Solutions Shared and vCenter Server events are global events. KMIP for VMware events are location-based events that are automatically forwarded to the {{site.data.keyword.at_full_notm}} service instance that is available in the same location as the KMIP for VMware instance. For more information, see [Monitoring global and location-based events](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-monitor_events#mon_def_event_type).

{{site.data.keyword.at_full_notm}} can have only one instance per location. To view events, you must access the web UI of the {{site.data.keyword.at_full_notm}} service in the same location where your service instance is available. For more information, see [Navigating to the web UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch).

## Related links
{: #at-events-related}

* [Provisioning an instance](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-provision)
* [Navigating to the web UI](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-launch)
* [KMIP for VMware overview](/docs/vmwaresolutions?topic=vmwaresolutions-kmip_standalone_considerations)

---

copyright:

  years:  2019, 2021

lastupdated: "2021-03-21"

keywords: openshift for vmware, request openshift for vmware, tech specs openshift vmware

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Red Hat OpenShift for VMware overview
{: #ocp_overview}

The Red Hat® OpenShift® for VMware® service deploys a Red Hat OpenShift cluster by using an automated deployment of the VMware SDDC (Software Defined Data Center) architecture. The Red Hat OpenShift components are deployed as virtual machines (VM) or appliances by using VMware NSX® software-defined networking.

Review the following information before you install the Red Hat OpenShift for VMware service:
* Red Hat OpenShift for VMware cannot be installed on multiple VMware vCenter Server® instances in a multi-site configuration. Before you install Red Hat OpenShift for VMware on an instance, verify that the service is not installed on any other instances in the multi-site configuration.
* Red Hat OpenShift for VMware is supported on VMware vCenter Server instances with VMware vSphere® 7.0, only for VMware NSX-T 3.1.
* Red Hat OpenShift for VMware is not supported for new deployments or for ordering post deployment for the following instances:
   * vCenter Server with NSX-V for vSphere 6.7 or 6.5
   * vCenter Server with NSX-T for vSphere 6.7

   Existing installations of Red Hat OpenShift for VMware can be used or deleted.

{{site.data.keyword.vmwaresolutions_full}} offers promotions for some services. Promotional pricing offers a number of months free of charge for a service’s licenses, if the service has license charges. For more information, see [Promotions for VMware Solutions services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-service-promotions).

Currently, Red Hat OpenShift v4.6 is installed.
{: note}

The cluster consists of the following components:
* Three primary nodes
* Three worker nodes, all running Red Hat CoreOS
* Two VMware NSX® VMs
* A Red Hat CoreOS template
* A bastion VM running CentOS

For more information about the architecture, see [Red Hat OpenShift architecture](/docs/vmwaresolutions?topic=vmwaresolutions-vcs-openshift-redhat-arch).

## Technical specifications for OpenShift for VMware
{: #ocp_overview-specs}

The following capacity requirements apply only if your VMware vCenter Server instance is using vSAN™ storage. If you are using NFS, a new 2-TB NFS datastore, which is dedicated to OpenShift, is ordered.

The solution topology has the following requirements:

* 79 vCPUs
* 155 GB RAM
* 952 GB storage

For more information about resource requirements and capacity checking, see [Resource requirements for services](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices#vc_addingremovingservices-resource-requirements).

To successfully deploy Red Hat OpenShift on vCenter Server, you must have a Red Hat account and the pull secret key from your account. All Red Hat accounts have an associated pull secret, which you can retrieve by [logging in to your Red Hat account](https://cloud.redhat.com/openshift/install/vsphere/user-provisioned). You must purchase Red Hat support entitlements through Red Hat. You must also direct all Red Hat OpenShift support issues to Red Hat.

### Selection of the target cluster for installation
{: #ocp_overview-select-target-cluster}

During deployment and day 2 operations, you are prompted for the cluster. You can install the service to the management cluster or any workload cluster.

### Bastion details
{: #ocp_overview-bastion}

The bastion VM contains an installation directory with the files and tools that are needed to manage and expand the OpenShift cluster.   

You can log in to the bastion by using the SSH protocol and the credentials that are provided on the Red Hat OpenShift for VMware service details page. To run commands as the `root` user, use the command `sudo -i`.

In addition, most commands for OpenShift management must be run from the installation directory. You can change to the installation directory with the command `cd /opt/ocpinstall`.

Any commands that require the `openshift-install`, `oc`, or `kubeadmin` tools must reference the files that are located in the installation directory by prefixing the command name with `./`. For example, `./oc whoami` instead of `oc whoami`.

The OpenShift-related files from the bastion include an SSH key, an installation configuration file, command line tools, and a `kubeconfig` file. The exact location of the installation configuration directory on the bastion is shown on the service details page.

### SSH key
{: #ocp_overview-bastion-ssh-key}

The SSH key on the bastion is installed on all Red Hat OpenShift cluster VMs, which allows SSH login from the bastion into any cluster VM. The full path to the SSH key is displayed on the service details page. For security purposes, it is highly recommended that you generate a new SSH key and update the cluster VMs with the new key. For more information, see [Changing the SSH key on the OpenShift bastion](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_managing#ocp_managing-change-ssh-key).

The SSH key on the bastion is installed on all Red Hat OpenShift cluster VMs, which allows SSH login from the bastion into any cluster VM. When you log in to a cluster VM from the bastion, you must connect as the `core` user as shown in the following example: `root@bastion# ssh core@control-plane0`.

For security purposes, it is highly recommended that you generate a new SSH key and update the cluster VMs with the new key. The full path to the SSH key is displayed on the service details page. For more information, see [Changing the SSH key on the OpenShift bastion](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_managing#ocp_managing-change-ssh-key).

### High availability
{: #ocp_overview-high-avail}

The Red Hat OpenShift VMs are deployed with DRS rules to ensure that they are on physically separate hosts. If a host must be replaced or redeployed, you must adjust the preconfigured DRS rules before you can proceed.

### Installation configuration files
{: #ocp_overview-bastion-install-config-file}

The installation configuration file that is named `install-config.yaml.bak` is located in the installation directory on the bastion. The file is a copy of the original `install-config.yaml` file that was used by the `openshift-install` program to generate the ignition files. The generated ignition files can also be found in the installation directory on the bastion.

The `oc` and `kubectl` command line tools from the Red Hat OpenShift client software are on the bastion. The installer program, named `openshift-install`, is used to install OpenShift and can also be used to generate fresh ignition files.  

The bastion also holds a file that is named `auth/kubeconfig`, needed for authentication. This file holds the initial kubeadmin credentials that are created during installation. Before you initially use the `oc` or `kubectl` tools, you must set the KUBECONFIG environment variable with the path to this file. For example, `export KUBECONFIG=auth/kubeconfig`.

After that is done, any commands you run will be as the `kubeadmin` user. You can verify the user account by running the command `./oc whoami`.

After you configure your authentication and any additional users, you no longer need to source this file, and you can log in as the user that you created.

### Red Hat subscriptions
{: #ocp_overview-redhat-subscr}

The OpenShift cluster is associated with the Red Hat account from the pull secret that was provided during installation. To assign subscriptions or manage the cluster, you can view the cluster in the Red Hat Portal under **Systems** or **Clusters**.

## Assigning Red Hat subscriptions and entitlements to your Red Hat OpenShift cluster
{: #ocp_overview-assign-cluster}

1. Log in to your Red Hat OpenShift cluster web console.
2. Click **Home > Dashboards**. Make a note of the cluster ID that is displayed.
3. Click **Administration > Cluster Settings**.
4. Click **OpenShift Cluster Manager** under the channel, version, and update information.
  * Ensure that the cluster ID that is displayed matches the cluster ID from step 2.
  * If the cluster is not attached to a subscription, a message is displayed with a link that you can use to find this cluster in the Red Hat Customer Portal. Use the link to assign the appropriate subscription and entitlement to the cluster.

  If you do not have enough subscriptions and entitlements, you can also contact Sales.

For more information, see [OpenShift subscriptions information and known issues](https://access.redhat.com/articles/4105561){:external}.

## Configuring authentication
{: #ocp_overview-conf-auth}

By default, the Red Hat OpenShift installer creates a kubeadmin user that you can use to log in to the cluster. It is recommended that you create authentication backends or more users, as needed, for security purposes.

For more information about how to configure OpenShift authentication, see [Understanding authentication](https://docs.openshift.com/container-platform/4.6/authentication/understanding-authentication.html){:external}.

## Updating your Red Hat OpenShift cluster
{: #ocp_overview-update-clus}

For more information about updating Red Hat OpenShift, see [Updating a cluster between minor versions](https://docs.openshift.com/container-platform/4.6/updating/updating-cluster-between-minor.html){:external}.

## Considerations when you install Red Hat OpenShift for VMware
{: #ocp_overview-consid-install}

* Before the service is installed in your environment, a check is completed against the available capacity of the target cluster in the environment to ensure that the service components can fit. The storage capacity check applies only to vSAN storage. For NFS clusters, a new NFS datastore, dedicated to OpenShift, is added.
* The cluster is associated with the Red Hat account from the pull secret that is provided.
* The **Latency Sensitivity** setting of the OpenShift cluster VMs can affect Kubernetes scheduling performance. By default, the setting is set to **Normal**, but it can be set to **High** if you encounter Kubernetes performance issues.

## Considerations when you delete Red Hat OpenShift for VMware
{: #ocp_overview-consid-remove}

* Before you delete Red Hat OpenShift, you must remove any additional VMs that you created in the `ocp` directory on VMware. The VMware Solutions automation removes only the items that were deployed during the initial installation of OpenShift (VMs, storage, and NSX). Any node that is deployed after the installation is not cleaned up.
* The VXLAN, DLR, and the Edge Gateway that were created during the initial deployment of Red Hat OpenShift for VMware is deleted. The VMs that you deployed on VXLAN will lose connectivity after the removal of Red Hat OpenShift for VMware starts.
* If you are using a vSAN datastore, it is recommended to delete any persistent volumes that you no longer need before you uninstall OpenShift. Any volumes that are not deleted will remain in the vSAN storage after the OpenShift uninstallation.
* If your cluster uses NFS storage, deleting Red Hat OpenShift deletes the NFS datastore that was added during installation.
* Before you delete the service, you must remove any personal VMs from storage deployed with this service. Red Hat OpenShift only orders personal VMs if it’s not vSAN.

## Related links
{: #ocp_overview-related}

* [VMware vCenter Server and Red Hat OpenShift architecture overview](/docs/vmwaresolutions?topic=vmwaresolutions-vcs-openshift-intro)
* [IBM Cloud for VMware Solutions and Red Hat OpenShift overview](/docs/vmwaresolutions?topic=vmwaresolutions-openshift-runbook-runbook-intro)
* [OpenShift Container Platform 4.6 documentation](https://docs.openshift.com/container-platform/4.6/welcome/index.html){:external}
* [OpenShift Container Platform 4.6 release notes](https://docs.openshift.com/container-platform/4.6/release_notes/ocp-4-6-release-notes.html){:external}
* [What's new in Red Hat OpenShift](https://www.openshift.com/learn/whats-new){:external}
* [Red Hat OpenShift](https://www.openshift.com/){:external}
* [Succeeding with Red Hat OpenShift and VMware’s Software-Defined Datacenter (SDDC)](https://blog.openshift.com/red-hat-openshift-and-vmware-better-together/){:external}

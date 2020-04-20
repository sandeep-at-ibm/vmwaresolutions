---

copyright:

  years:  2019, 2020

lastupdated: "2020-03-30"

keywords: red hat openshift, request openshift for vmware, tech specs openshift vmware

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Red Hat OpenShift for VMware overview
{: #ocp_overview}

The Red Hat OpenShift for VMware service deploys a Red Hat OpenShift cluster by using an automated deployment of the VMware SDDC (Software Defined Data Center) architecture. The Red Hat OpenShift components are deployed as virtual machines (VM) or appliances by using VMware NSX software-defined networking.

The current Red Hat OpenShift version that is installed is 4.2.16.
{: note}

The cluster consists of three master nodes and three worker nodes, all running Red Hat CoreOS. In addition, there are also two VMware NSX VMs, a Red Hat CoreOS template, and a bastion VM running CentOS. 

For more information about the architecture, see [Red Hat OpenShift architecture](/docs/vmwaresolutions?topic=vmware-solutions-vcs-openshift-redhat-arch).

## Technical specifications for OpenShift for VMware
{: #ocp_overview-specs}

The following capacity requirements apply only if your vCenter Server instance is using vSAN storage. If you are using
NFS, a new 2-TB NFS datastore, which is dedicated to OpenShift, will be ordered. The solution topology requirements are:

* 79 vCPUs
* 155 GB RAM
* 952 GB storage

To successfully deploy Red Hat OpenShift on vCenter Server, you must have a Red Hat account and the Pull Secret key
from your account. All Red Hat accounts have an associated Pull Secret, which you can retrieve by [logging into your
Red Hat account](https://cloud.redhat.com/openshift/install/vsphere/user-provisioned){:external}. You must
purchase Red Hat support entitlements through Red Hat. You must also direct all Red Hat OpenShift support issues to Red Hat.

### Bastion details
{: #ocp_overview-bastion}

The bastion VM contains an installation directory with the files and tools that are needed to manage and expand the OpenShift cluster.   

You can log in to the bastion by using the SSH protocol and the credentials that are provided on the Red Hat OpenShift for VMware service details page. To run commands as the `root` user, use the command `sudo -i`

In addition, most commands for OpenShift management must be run from the installation directory. You can change to the installation directory with the command `cd /opt/ocp42install`

Any commands that require the `openshift-install`, `oc`, or `kubeadmin` tools must reference the files that are located in the installation directory by prefixing the command name with `./`. For example, `./oc whoami` instead of `oc whoami`

The OpenShift-related files from the bastion include: an SSH key, an installation configuration file, command-line tools, and a `kubeconfig` file. The exact location of the installation configuration directory on the bastion is shown on the service details page.

### SSH key
{: #ocp_overview-bastion-ssh-key}

The SSH key on the bastion is installed on all Red Hat OpenShift cluster VMs, which allows SSH login from the bastion into any cluster VM. The full path to the SSH key is displayed on the service details page. For security purposes, it is highly recommended that you generate a new SSH key and update the cluster VMs with the new key. For more information, see [Changing the SSH key on the OpenShift bastion](/docs/vmwaresolutions?topic=vmware-solutions-ocp_managing#ocp_managing-change-ssh-key).

The SSH key on the bastion is installed on all Red Hat OpenShift cluster VMs, which allows SSH login from the bastion into any cluster VM. When you log in to a cluster VM from the bastion, you must connect as the `core` user as shown in the following example: `root@bastion# ssh core@master0`

For security purposes, it is highly recommended that you generate a new SSH key and update the cluster VMs with the new key. The full path to the SSH key is displayed on the service details page. For more information, see [Changing the SSH key on the OpenShift bastion](/docs/vmwaresolutions?topic=vmware-solutions-ocp_managing#ocp_managing-change-ssh-key).

### Installation configuration files
{: #ocp_overview-bastion-install-config-file}

The installation configuration file named `install-config.yaml.bak` is located in the installation directory on the
bastion. The file is a copy of the original `install-config.yaml` file that was consumed by the `openshift-install` program to generate the ignition files. The generated ignition files can also be found in the installation directory on the bastion.

The `oc` and `kubectl` command-line tools from the Red Hat OpenShift client software are on the bastion. The installer program, named `openshift-install`, is used to install OpenShift and can also be used to generate fresh ignition files.  

The bastion also holds a file that is named `auth/kubeconfig`, needed for authentication. This file holds the initial kubeadmin credentials that are created during installation. Before you initially use the `oc` or `kubectl` tools, you must set the KUBECONFIG environment variable with the path to this file. For example, `export KUBECONFIG=auth/kubeconfig`

After that is done, any commands you run will be as the `kubeadmin` user. You can verify the user account by running the command `./oc whoami`

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

For more information about how to configure OpenShift authentication, see [Understanding authentication](https://docs.openshift.com/container-platform/4.2/authentication/understanding-authentication.html){:external}.

## Updating your Red Hat OpenShift cluster
{: #ocp_overview-update-clus}

For more information about updating Red Hat OpenShift, see [Updating a cluster between minor versions](https://docs.openshift.com/container-platform/4.2/updating/updating-cluster-between-minor.html){:external}.

## Considerations when you install Red Hat OpenShift for VMware
{: #ocp_overview-consid-install}

* Before the service is installed in your environment, a check is performed against the available capacity of the default cluster in the environment to ensure that the service components can fit. The storage capacity check only applies to
vSAN because NFS clusters will have a new NFS datastore dedicated to OpenShift added.
* The cluster will be associated with the Red Hat account from the pull secret that is provided.
* The **Latency Sensitivity** setting of the OpenShift cluster VMs can affect Kubernetes scheduling performance. By default, the setting is set to **Normal**, but it can be set to **High** if you encounter Kubernetes performance issues.

## Considerations when you remove Red Hat OpenShift for VMware
{: #ocp_overview-consid-remove}

* Before you remove Red Hat OpenShift, you must remove any additional VMs that you created in the "ocp" folder on
VMware. Automation only removes the items that were deployed during the initial installation of OpenShift (VMs, Storage, and NSX). Any node that is deployed after the installation is not cleaned up.
* The VXLAN, DLR, and the Edge Gateway that were created during the initial deployment of Red Hat OpenShift for VMware will be deleted. The VMs that you deployed on VXLAN will lose connectivity after the removal of Red Hat OpenShift for VMware starts.
* If you are using a vSAN datastore, it is recommended to delete any persistent volumes that you no longer need before you uninstall OpenShift. Any volumes that are not deleted will remain in the vSAN storage after the OpenShift uninstallation.
* If your cluster uses NFS storage, removing Red Hat OpenShift deletes the NFS datastore that was added during installation.

## Related links
{: #ocp_overview-related}

* [vCenter Server and Red Hat OpenShift architecture](/docs/vmwaresolutions?topic=vmware-solutions-vcs-openshift-intro)
* [vCenter Server and Red Hat OpenShift guide](/docs/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-intro)
* [OpenShift Container Platform documentation](https://docs.openshift.com/container-platform/4.2/welcome/index.html){:external}
* [Red Hat OpenShift](https://www.openshift.com/){:external}
* [Succeeding with Red Hat OpenShift and VMware’s Software-Defined Datacenter (SDDC)](https://blog.openshift.com/red-hat-openshift-and-vmware-better-together/){:external}

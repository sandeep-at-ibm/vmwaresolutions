---

copyright:

  years:  2019

lastupdated: "2019-09-11"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Prerequisites for installation
{: #openshift-runbook-runbook-prereq-intro}

Before you can start the build process to install the Red Hat Open Shift cluster the following steps are required.

* Ordering new subnets for the OpenShift environment:
  * A private portable subnet for the Red Hat OpenShift cluster NSX ESG.
  * A public portable subnet for the Red Hat OpenShift cluster NSX ESG.
* Downloading Red Hat OpenShift 4.1 - Access to a Red Hat subscription to download the installer, pull secret and Red Hat Enterprise CoreOS OVA.
* Downloading RHEL 7.6 ISO - Access to a Red Hat subscription to download the Red Hat Enterprise Linux 7.x ISO for the bastion host.
* IBM Cloud environment details - Collect the following details for {{site.data.keyword.cloud}} for VMware Solutions environment:
  * vCenter Server instance details and passwords
  * The additional private portable subnet information
  * The additional public portable subnet information
* Downloading and installing govc - govc is a vSphere CLI and is a user-friendly CLI alternative to the GUI and suited for automation tasks.

## Ordering new subnets for the OpenShift environment
{: #openshift-runbook-runbook-prereq-cloud-subnets}

1. Log in to the [{{site.data.keyword.vmwaresolutions_short}} console](https://cloud.ibm.com/infrastructure/vmware-solutions/console).
2. Select **Classic Infrastructure>Network>IP management>Subnets**.
3. Click **Order IP Subnets**.

Requirements:

* 8 Public portable addresses assigned to the Public VLAN collected in the previous step.
* 64 Private portable addresses assigned to the Private VLAN collected in the previous step.

## Downloading Red Hat OpenShift 4.1
{: #openshift-runbook-runbook-prereq-download41}

Access the [OpenShift Infrastructure Providers page](https://cloud.redhat.com/openshift/install/vsphere/user-provisioned){:external}.

1. Download the installer.
2. Download the Pull Secret.
3. Download the Red Hat Enterprise Linux CoreOS (RHEL CoreOS) OVA image or download the OVA using curl:
  `curl -O https://mirror.openshift.com/pub/openshift-v4/dependencies/rhcos/4.1/latest/rhcos-4.1.0-x86_64-vmware.ova`.
4. Download the command-line tools if you want to run the commands from a desktop or outside Bastion host.

## Downloading RHEL 7.6 ISO
{: #openshift-runbook-runbook-prereq-downloadiso}

Download the ISO image for the bastion host.

1. Go to the Red Hat [Product Downloads](https://access.redhat.com/downloads){:external} page.
2. Click **RHEL 7.x Release** and select the 7.6 version.
3. Download the source ISO images.
4. The ISO file name should be rhel-server-7.6-x86_64-dvd.iso

## vCenter Server instance details
{: #openshift-runbook-runbook-prereq-cloud}

Access the {{site.data.keyword.cloud_notm}} environment details:

1. Log in to the [{{site.data.keyword.vmwaresolutions_short}} console](https://cloud.ibm.com/infrastructure/vmware-solutions/console).
2. Click the {{site.data.keyword.vmwaresolutions_short}} instance under **Deployed Instances**.
3. From the **Summary** page, collect the vCenter and Active Directory information.
4. From the Infrastructure Menu,** select the cluster.
5. Under **Network Interfaces**, collect the Public and Private VLANs.

## Download and install govc
{: #openshift-runbook-runbook-prereq-govc}

govc will be used to upload the OVF and ISO to a datastore from the jump-server or remote device.

If your jump-host or remote device uses Windows, then download from [Downloads](https://github.com/vmware/govmomi/releases){:external}.

If your remote device uses macOS, then use the following terminal command; `brew install govmomi/tap/govc`.

If you need to install Homebrew, then review [Installing Homebrew on a Mac](https://treehouse.github.io/installation-guides/mac/homebrew){:external}.

If your jump-host or remote device uses Linux then:

1. Download govc and make it executable:
  `curl -L https://github.com/vmware/govmomi/releases/download/v0.20.0/govc_linux_amd64.gz | gunzip > /usr/local/bin/govc`.
2. `chmod +x /usr/local/bin/govc`.

## Uploading the OVA image to vCenter
{: #openshift-runbook-runbook-prereq-cloud-ic4v}

You must upload and import the RHEL ISO and RHEL CoreOS OVA downloads from the previous steps into the vCenter Server instance datastore. You must rename the OVA image to *rhcos-latest* in order for the image to work with the terraform templates used later in the build process.

On the jump-server or remote device, by using an editor of your choice, such as Visual Studio Code, copy the following and change for your values:

```bash
export GOVC_URL='10.208.17.2'
export GOVC_USERNAME='administrator@vsphere.local'
export GOVC_PASSWORD='xxxxx'
export GOVC_INSECURE=1
export GOVC_NETWORK='SDDC-DPortGroup-Mgmt'
export GOVC_DATASTORE='vsanDatastore'
govc import.spec ./rhcos-4.1.0-x86_64-vmware.ova | python -m json.tool > rhcos.json
vi rhcos.json
  - replace  "Network": "SDDC-DPortGroup-Mgmt"
  - leave name as "VM network"
govc import.ova -options=./rhcos.json -name=rhcos-latest ./rhcos-4.1.0-x86_64-vmware.ova
```

## Uploading the ISO image to vCenter storage
{: #openshift-runbook-runbook-prereq-cloud-iso}

Use the following govc example to upload the ISO image for the creation of the bastion node:

```bash
export GOVC_URL='10.208.17.2'
export GOVC_USERNAME='administrator@vsphere.local'
export GOVC_PASSWORD='xxx'
export GOVC_INSECURE=1
export GOVC_DATASTORE='vsanDatastore'
govc datastore.mkdir isos
govc datastore.upload rhel-server-7.6-x86_64-dvd.iso isos/rhel-server-7.6-x86_64-dvd.iso
```

## Related links
{: #openshift-runbook-runbook-prereq-related}

* [OpenShift NSX DLR configuration](/docs/services/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-nsxdlr-intro)
* [OpenShift Bastion host setup](/docs/services/vmwaresolutions?topic=vmware-solutions-openshift-runbook-runbook-bastion-intro)
* [Visual Studio Code](https://code.visualstudio.com/){:external}

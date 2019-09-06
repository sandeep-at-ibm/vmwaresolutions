---

copyright:

  years:  2019

lastupdated: "2019-09-03"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Troubleshooting
{: #openshift-runbook-runbook-trbl-intro}

This section lists some troubleshooting advice.

## RHEL Subscription
{: #openshift-runbook-runbook-trbl-intro-sub}

If you encounter a problem with your subscription, you can query by using the following command

```bash
subscription-manager list --available --all
```

## Load-balancer
{: #openshift-runbook-runbook-trbl-intro-lb}

To check that load balancing is working use the following command from the bastion node and it should return a full set of headers:

```bash
wget --no-check-certificate https://api.ocp.dallas.ibm.local:6443
```

## Red Hat CoreOS
{: #openshift-runbook-runbook-trbl-intro-coreos}

There should be no need to SSH to node, but if you do, you can via the bastion node. The following example connects to the bootstrap server using the following command:

```bash
ssh core@192.168.133.9
```

If you get an error, then try the following commands that disable the checking of the fingerprint:

```bash
ssh -o StrictHostKeyChecking=no core@192.168.133.9
```

This example shows how to connect to control-plane node from the bastion node to view the logs and change the permission to make them readable. Note the directory name might be different.

```bash
ssh -i /root/.ssh/id_rsa core@192.168.133.12
sudo su
chmod 777 /var/log/pods/b2810e842791d83d48a4684295b7cd01/etcd-member/0.log
```

This example shows how to download the log to the bastion node and then on to the jump-server or remote device for readability and the ability to parse the logs. Note the directory name might be different.

```bash
scp -i /root/.ssh/id_rsa core@192.168.133.10:/var/log/pods/b2810e842791d83d48a4684295b7cd01/etcd-member/0.log 0.log
```

## OpenShift
{: #openshift-runbook-runbook-trbl-intro-openshift}

Gets a list of nodes and their status:

```bash
oc get nodes
```

When using kubectl, there is a preference that takes effect while determining which kubeconfig file is used:

* use --kubeconfig flag, if specified.
* use KUBECONFIG environment variable, if specified.
* use $HOME/.kube/config file.

To export the kubeconfig created by the OpenShift Installer to an environment variable use the following command:

```bash
export KUBECONFIG=/opt/ocp41install/auth/kubeconfig
```

## Related links
{: #openshift-runbook-runbook-trbl-related}

* [OpenShift 4.1 Bare Metal Install Quickstart](https://blog.openshift.com/openshift-4-bare-metal-install-quickstart/){:external}
* [Install on vSphere: User-Provisioned Infrastructure](
https://cloud.redhat.com/openshift/install/vsphere/user-provisioned){:external}
* [Install a cluster on vSphere](https://docs.openshift.com/container-platform/4.1/installing/installing_vsphere/installing-vsphere.html#ssh-agent-using_installing-vsphere){:external}
* [Index of latest public OpenShift v4 clients](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/?extIdCarryOver=true&sc_cid=701f2000001Css5AAC){:external}
* [Deploying a User Provisioned Infrastructure environment for OpenShift 4.1 on vSphere](https://blog.openshift.com/deploying-a-user-provisioned-infrastructure-environment-for-openshift-4-1-on-vsphere/){:external}
* [Understanding persistent storage](https://docs.openshift.com/container-platform/4.1/storage/understanding-persistent-storage.html#understanding-persistent-storage){:external}
* [ssh-keygen - Generate a New SSH Key](https://www.ssh.com/ssh/keygen/){:external}
* [Configure PowerCLI and PowerNSX on macOS](https://readysetvirtual.wordpress.com/2018/04/06/configure-powercli-and-powernsx-on-macos/){:external}
* [Visual Studio Code](https://code.visualstudio.com/){:external}
* [Terraform Getting Started](https://learn.hashicorp.com/terraform#getting-started){:external}
* [Windows 2016 PowerShell DNS](https://docs.microsoft.com/en-us/powershell/module/dnsserver/?view=win10-ps){:external}
* [OpenShift cheat sheet](https://cheatsheet.dennyzhang.com/cheatsheet-openshift-a4){:external}
* [PowerCLI Core Docs](https://powercli-core.readthedocs.io/en/latest/index.html){:external}

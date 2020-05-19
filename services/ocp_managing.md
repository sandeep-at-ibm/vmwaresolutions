---

copyright:

  years:  2019, 2020

lastupdated: "2020-04-03"

keywords: Red Hat OpenShift for VMware, manage OpenShift, OpenShift operations

subcollection: vmwaresolutions


---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Managing Red Hat OpenShift for VMware
{: #ocp_managing}

Review the following information to manage your OpenShift for VMware service after deployment.

## Required rotation of the OpenShift certificates
{: #ocp_managing-cert-rotation}

Red Hat OpenShift for VMware uses kubelet client certificates that must be rotated periodically for security purposes. Red Hat OpenShift mainly automates the rotation process, but requires manual approval of Certificate Signing Requests (CSRs). Therefore, it is important that you understand the OpenShift certificate rotation schedule to avoid expired certificates.  

The initial certificates that are created during installation expire 24 hours after they are created. IBM's automation process, which installs Red Hat OpenShift, handles the approval of the CSRs for this initial rotation, which is done by running a script on the bastion for the first 30 hours. The script is named `/root/approve-csr.sh` and its log file is named `/root/approve-csr.log`. 

For the script to run successfully, the initial `kubeadmin` credentials must be the same until the initial certificate rotation is complete. Do not change the kubeadmin credentials for the first 24 hours. If the credentials are changed, you must monitor and approve the CSRs for the initial certificate rotation. For more information, see [Approving the CSRs for your machines](https://docs.openshift.com/container-platform/4.2/installing/installing_vsphere/installing-vsphere.html#installation-approve-csrs_installing-vsphere){:external}.

It is important not to restart any of the Red Hat OpenShift cluster virtual machines (VMs) or the bastion VM until the first certificate rotation is done.

After the initial certificate rotation, certificates are renewed every 30 days. You must establish a process to approve the CSRs for every certificate rotation. According to Red Hat, you can approve CSRs when they reach 80% of their expiration period, which is approximately 25 days into the lifespan of the CSRs.

If you do not approve CSRs in time and the certificates expire, you can recover from expired control plane certificates and get the OpenShift cluster operational again. For more information, see [Recovering from expired control
plane certificates](https://docs.openshift.com/container-platform/4.2/backup_and_restore/disaster_recovery/scenario-3-expired-certs.html){:external}.

## Changing the SSH key on the OpenShift bastion
{: #ocp_managing-change-ssh-key}

The SSH key pair that is generated during installation is on the OpenShift bastion VM. The location of the SSH key pair is shown in the OpenShift Service Details page. This SSH key was installed on all cluster virtual machines (VMs) to allow SSH logins from the bastion without requiring a password.

It is recommended that a new SSH key pair is generated and used to replace the existing key. To generate a new
SSH key pair, use the instructions in the Red Hat article about [updating an SSH key](https://access.redhat.com/solutions/4510281){:external}. You must run the commands from the bastion VM. For more information about logging in to the bastion, see [Bastion details](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview#ocp_overview-bastion).

## Expanding an OpenShift cluster with more workers
{: #ocp_managing-expand-cluster}

To expand your OpenShift cluster by adding more worker VMs, complete the following steps:

1. Create a worker VM from the RHCOREOS template.
  1. Ensure that the VM is connected to the same network as the other OpenShift worker VMs.
  2. Do not power on this VM yet, as there are more configuration steps ahead.

2. Prepare a worker ignition file on the bastion.
  1. For more information about logging in to the bastion, see [Bastion details](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview#ocp_overview-bastion).
  2. In the installation directory on the bastion, locate the worker ignition file named `worker.ign`. Create a base64 version of this file by using the command `base64 -w0 worker.ign > worker.ign.b64`. The contents of the newly created `worker.ign.b64` file is used in the next step.

3. Set the VM attributes.
  1. Edit the configuration parameters of the new worker VM. Power off the VM before you start. To go to the Configuration Parameters window, select the new worker VM and click **Actions > Edit Settings**.
  2. In the Edit Settings window, click the **VM Options** tab at the top. On the left, click **Advanced** to expand the **Advanced** section in the window. Then, scroll down to **Configuration Parameters** on the left. To open the Configuration Parameters window, click **Edit Configuration**.
  3. The Configuration Parameters window might have a long list of existing parameters for the VM. To add a value, click **Add Configuration Params** near the top of the window. Two empty fields that are labeled **Name** and **Value** are displayed for you to complete. This is the process to use for each of the following values.
  4. Create a value named `guestinfo.ignition.config.data`. Set the value to the contents of the base64-encoded ignition config file `worker.ign.b64` that was created earlier.
  5. Create a value named `guestinfo.ignition.config.data.encoding`. Set the value to the string `base64`.
  6. Create a value named `disk.EnableUUID`. Set the value to the string `TRUE`.
  7. After you create the new parameters, click **OK** to close the Configuration Parameters window. Click **OK** to close the Edit Settings window.

4. Create a DHCP binding for the worker VM.
  1. When the new worker VM comes online, it attempts to get its IP address by using DHCP. Your Red Hat OpenShift for VMware environment is already configured with the proper networking and DHCP settings to allow getting the IP address. However, you must create a new binding for this VM.
  2. Make a note of the new worker VM's name and MAC address.
  3. To go to the NSX edge configuration named `ocp-nsx-edge`, from the vSphere Web Client, go to to **Menu > Networking and Security**. On the left navigation pane, click **NSX Edges**.
  4. The list of NSX edges is displayed. Click the edge named `ocp-nsx-edge` to open its configuration window. If the edge is not listed, scroll down the list to locate it.
  5. In the configuration window for the `ocp-nsx-edge` NSX edge, click **DHCP** along the top bar and then click **Bindings** on the left. The list of existing DHCP bindings is displayed. The DHCP bindings associate VM MAC addresses to the IP address they are assigned.
 6. Look at the **IP Address** column for the existing bindings. Make a note of the next available **IP Address**, which is the address you will assign to the new worker VM.
  7. Locate worker0 in the **Host Name** column. To view the binding details for worker0, select the worker0 binding and click **Edit**.
  8. Make a note of all the settings on both the **General** and **DNS Settings** tabs. With the exception of the **MAC Address**, **Hostname**, and **IP Address**  fields, you will be creating a new binding with all the same settings as worker0. When you are finished viewing the information for worker0, click **Cancel** to close the window.
  9. To create a new DHCP binding for the new worker VM, click the **Add** button in the DHCP Bindings window. The New DHCP Binding window is displayed. Select the **Use MAC Binding** option at the top and enter the **MAC Address**, **Hostname**, and **IP Address** that correspond to the new worker VM you are adding. For the rest of the fields, enter the settings that you previously noted from the existing worker0 binding. Click the **Add** button.
  10. Your changes are saved and the New DHCP Binding window is closed.
  11. The Bindings window is displayed. A blue rectangular box is displayed at the top explaining that changes to the DHCP configuration take effect after they're published. To publish your changes, click the **PUBLISH** button inside the blue box. The blue box disappears after the changes are processed.

5. Add a worker to the Load Balancer pools.
  1. Go into the NSX edge configuration named `ocp-nsx-edge`. To do this, from the vSphere Web Client, go to **Menu > Networking and Security**. On the left navigation pane, click **NSX Edges**.
  2. On the list of NSX edges that is displayed, click the edge named `ocp-nsx-edge` to open its configuration window. If the edge is not listed, scroll down the list to locate it.
  3. In the configuration window for the `ocp-nsx-edge` NSX edge, click **Load Balancer** along the top bar and then click **Pools** on the left. The list of existing pools is displayed.
  4. Add the new worker VM as a member of the `api-pool-80` pool. To do this, select the `api-pool-80` pool and click **Edit**. Then, click **Members**.
  5. A list of existing pool members is displayed. Before you add the new worker as a member, select the existing **Compute_0** entry and click **Edit** to view the settings. Make note of all the settings shown. Be careful not to change any values.
  6. Click **Cancel** to return to the Edit Pool window. Then, click **Members**.
  7. Click **Add** to open the New Member window. Complete the **Name** and **IP Address / VC Container** fields with the values for the new worker VM. For all other fields, use the same values that you noted from the **Compute_0** member. Click **OK** to save the values and close the New Member window. Click **Save** to close the Edit Pool window.
  8. You must also add the new worker VM as a member of the `api-pool-443` pool. To do this, select the `api-pool-443` pool and click **Edit**. Then, click **Members**.
  9. A list of existing pool members is displayed. Before you add the new worker as a member, select the existing **Compute_0** entry and click **Edit** to view the settings. Make note of all the settings shown. Be careful not to change any values.
  10. Click **Cancel** to return to the Edit Pool window. Then, click **Members**.
  11. Click **Add** to open the New Member window. Complete the **Name** and **IP Address / VC Container** fields with the values for the new worker VM. For all other fields, use the same values that you noted from the **Compute_0** member. Click **OK** to save the values and close the New Member window. Click **Save** to close the Edit Pool window.

6. Create DNS records for the new worker.
  1. Log in to the AD NS server for your vCenter instance.
  2. Using the DNS Manager, add a new A record to the corresponding `ocp` zone. When you create the A record, make sure the option to create associated PTR record is selected.

7. Approve any certificate signing requests (CSRs) from the bastion. During the provisioning of the new worker, you might have to [approve CSRs](https://docs.openshift.com/container-platform/4.2/installing/installing_vsphere/installing-vsphere.html#installation-approve-csrs_installing-vsphere){:external} from the bastion.
  1. Log in to the bastion as the `root` user and change to the bastion installation directory, as described in [OpenShift bastion details](/docs/vmwaresolutions?topic=vmwaresolutions-ocp_overview#ocp_overview-bastion).
  2. Before you can run any commands, you must authenticate to OpenShift.
    * If authentication is not configured and you are using the default `kubeadmin` account and password, run the command `export KUBECONFIG=auth/kubeconfig` and verify that you are authenticated by running the command `./oc whoami`.
    * If other backends or users are authenticated, log in by using one of those accounts as explained in the Red Hat OpenShift documentation, for example, by running the command `./oc login`.
  3. Run `./oc get nodes` and you should see the new worker. If it is not yet in the **Ready** state, you must repeatedly check for pending CSRs by using the command `./oc get csr`, and then approve the CSRs by using the command `./oc adm certificate approve <csr_name>`. Continue to check until the configuration is complete and the new worked is in the **Ready** state.
  4. After the new worker is in **Ready** state, it can be used by OpenShift.

8. Power on the VM.
  * After the VM is powered on, you can monitor the VM to see whether there is a problem. The VM gets an IP address, then processes the ignition file, and then opens a login prompt. 
  * After the login prompt is shown, it might be covered by console log messages. If required, press the **Enter** key a few times on the console. If the login prompt is present but covered with console log messages, press **Enter** to display the login prompt again. 
  * If the login prompt does not appear, either the VM is not getting an IP address (check the network the VM is connected to, and the DHCP binding settings), or the base64 value from `worker.ign.64` is not correct (it might be missing some characters or it has some extra characters, check to confirm). If you must change any settings due to the VM not displaying a login prompt, power off the VM, change the necessary settings, and power it back on.

## Related links
{: #ocp_managing-related}

* [Ordering, viewing, and removing services for vCenter Server instances](/docs/vmwaresolutions?topic=vmwaresolutions-vc_addingremovingservices)
* [Contacting IBM Support](/docs/vmwaresolutions?topic=vmwaresolutions-trbl_support)
* [FAQ](/docs/vmwaresolutions?topic=vmwaresolutions-faq-vmwaresolutions)

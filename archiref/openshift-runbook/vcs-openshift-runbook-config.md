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

# Red Hat OpenShift 4.1 additional configuration
{: #openshift-runbook-runbook-config-intro}

## vSphere Storage for Kubernetes
{: #openshift-runbook-runbook-config-storage-vsphere}

You can use the vSphere datastores as a location for storing persistent volumes for Kubernetes by using the VMware Cloud Provider.

Complete the following steps to create a new volume.

1. From the Bastion host, use GOVC to enable the vSphere connection:

```bash
export GOVC_URL='10.208.17.2'
export GOVC_USERNAME='administrator@vsphere.local'
export GOVC_PASSWORD='xxx'
export GOVC_INSECURE=1
export GOVC_NETWORK='SDDC-DPortGroup-Mgmt'
export GOVC_DATASTORE='vsanDatastore'
```

2. Create a folder on the specified datastore:

```bash
govc datastore.mkdir ocp-volumes
```

3. Create a persistent volume (*.vmdk*):

```bash
govc datastore.disk.create -size 10G volumes/ocp-pv-001.vmdk
```

4. Use the command line to log in to your Kubernetes environment:

```bash
oc login
```

5. Create a persistent volume in Kubernetes for the recently created *.vmdk*. Replace volumePath with your *.vmdk*. The following example uses *vsphere-volume-pvc.yaml*.

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: ocpvsan002
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  vsphereVolume:
    volumePath: "[ESX_OCP] volumes/ocp-pv-001.vmdk"
    fsType: ext4
  storageClassName: "vsphere-standard"
```

```bash
kubectl create -f  vsphere-volume-pvc.yaml
```

6. Create a Persistent Volume Claim in Kubernetes.

Replace *volumePath* with your Persistent Volume name. The following example uses *vsphere-volume-pvc.yaml*.
{:note}

```yaml
apiVersion: "v1"
kind: "PersistentVolumeClaim"
metadata:
  name: "pvcvsan002"
spec:
  accessModes:
    - "ReadWriteOnce"
  resources:
    requests:
      storage: "1Gi"
  storageClassName: "vsphere-standard"
  volumeName: "ocpvsan002"
```

```bash
kubectl create -f vsphere-volume-pv.yaml
```

The persistent volume claim can now be mapped to the container application.  

## Related links
{: #openshift-runbook-runbook-config-related }

* [VMware vCenter Server and Red Hat OpenShift architecture overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-intro)
* [System context for vCenter Server and Red Hat OpenShift architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-syscontext)
* [Red Hat OpenShift architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-redhat-arch)
* [{{site.data.keyword.vmwaresolutions_short}} SDDC architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-arch)
* [{{site.data.keyword.cloud_notm}} networking and infrastructure](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-sddc-infra)
* [Storage options on {{site.data.keyword.cloud_notm}} and Red Hat OpenShift](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-storage)

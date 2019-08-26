---

copyright:

  years:  2019

lastupdated: "2019-08-25"

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Storage options on IBM Cloud and Red Hat OpenShift
{: #vcs-openshift-storage}

## vSphere Storage for Kubernetes

You can use the vSphere datastores as a location for storing persistent
volumes for Kubernetes by using the VMware Cloud Provider.

Complete the following steps to create a new volume:

1. From the bastion host, use govc to enable the vSphere connection.

  ```bash
  export GOVC_URL='10.208.17.2'
  export GOVC_USERNAME='administrator@vsphere.local'
  export GOVC_PASSWORD='xxx'
  export GOVC_INSECURE=1
  export GOVC_NETWORK='SDDC-DPortGroup-Mgmt'
  export GOVC_DATASTORE='vsanDatastore'
```

2. Create a folder on the specified datastore.

  ```bash
  govc datastore.mkdir ocp-volumes
  ```

3. Create a new persistent volume (vmdk).

  ```bash
  govc datastore.disk.create -size 10G volumes/ocp-pv-001.vmdk
  ```

4. Log in to your Kubernetes environment from the command line.

  ```bash
  oc login
  ```

5. Create a persistent volume in Kubernetes, for the recently created vdmk. Replace volumePath with your vmdk, in the example file called
 vsphere-volume-pv.yaml

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

6. Create a Persistent Volume Claim in Kubernetes. Replace volumePath with your Persistent Volume name, in the example file called vsphere-volume-pvc.yaml.

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

Now you have a persistent volume claim that can be mapped to container application.

## Related links
{: #vcs-openshift-storage-related}

* [VMware vCenter Server and Red Hat OpenShift architecture overview](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-intro)
* [System context for vCenter Server and Red Hat OpenShift architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-syscontext)
* [Red Hat OpenShift architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-redhat-arch)
* [IBM Cloud for VMware Solutions SDDC architecture](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-arch)
* [IBM Cloud networking and infrastructure](/docs/services/vmwaresolutions?topic=vmware-solutions-vcs-openshift-sddc-infra)

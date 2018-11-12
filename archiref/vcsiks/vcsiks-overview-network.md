---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-08"

---

# Networking, backup, disaster recovery, and scalability

## Networking

IBM Cloud has two networks. The public network allows servers to be reached from the internet and the private network allows servers to communicate with each other over a high-speed backbone in all IBM Cloud data centers.

By default, IKS sets up the cluster with access to a public VLAN and a private VLAN.
- A public IP address for each worker node, which gives worker nodes a public network interface.
  - All outbound network traffic is allowed for all worker nodes.
  - Inbound network traffic is blocked except for a few ports. These ports are opened so that IBM can monitor network traffic and automatically install security updates for the Kubernetes master.
- A private IP address for each worker node, which gives worker nodes a private network interface
- An automatic, secure OpenVPN connection between all worker nodes and the master node

Figure 1. VCS and IKS network
![VCS-IKS networking diagram](vcsiks-networking.svg)

### IKS and VCS integration

Currently, the following scenarios integrate IKS and VCS networking:
- **VRA Routing** - This scenario requires that the IKS worker nodes are deployed onto the same VLAN as the VCS instance. This allows an ESG to be BGP peered with VRA and enable routing from the overlay to the underlay network between VCS and IKS. A static route is needed on the IKS worker nodes for each VXLAN network to route these requests back to the BCR/VRA to correctly route.
- **strongSwan VPN** – This scenario uses the standard IKS-to-enterprise connectivity solution. A strongSwan container provides a VPN gateway for the cluster that forwards packets to remote networks across an IPSec
tunnel to the remote gateway. This remote gateway is an ESG on the VCS instance. On the gateways, routes are configure sending all cluster and service IP ranges to the StrongSwan container and all VCS BYOIP addresses to the ESG. The target IP addresses for the gateways are the private portable IP address of the load balancer service that is assigned to the strongSwan container and the private portable IP address of the ESG.

#### IKS networking VLANs

**Public VLAN subnets**
- The primary public subnet determines the public IP addresses that are assigned to worker nodes during cluster creation. Multiple clusters in on the same VLAN can share one primary public subnet.
- The portable public subnet is bound to one cluster only and provides the cluster with eight public IP addresses. Three IPs are reserved for network functions. One IP is used by the default public Ingress ALB and four IPs are used to create public load balancer networking services.

Portable public IPs are permanent, fixed IP addresses that are used to access load balancer services over the internet.

**Private VLAN subnets**
- The primary private subnet determines the private IP addresses that are assigned to worker nodes during cluster creation. Multiple clusters in on the same VLAN can share one primary private subnet.
- The portable private subnet is bound to one cluster only and provides the cluster with eight private IP addresses. Three IPs are reserved for network functions. One IP is used by the default private Ingress ALB and four IPs are used to create private load balancer networking services.

Portable private IPs are permanent, fixed IP addresses that are used to access load balancer services over the internet.

#### Calico

Every Kubernetes cluster is set up with a network plug-in called Calico.

##### Controlling traffic with network policies

Default network policies are set up to secure the public network interface of every worker node in the IBM Cloud Kubernetes Service. If you have unique security requirements or you have a multizone cluster with VLAN spanning enabled, you can use Calico and Kubernetes to create network policies for a cluster. With Kubernetes network policies, you can specify the network traffic that you want to allow or block to and from a pod within a cluster. To set more advanced network policies such as blocking inbound (ingress) traffic to LoadBalancer services, use Calico network policies.

###### Kubernetes network policies

These policies specify how pods can communicate with other pods and with external endpoints. Traffic can also be filtered based on pod and namespace labels. Kubernetes network policies are applied by using kubectl commands or the Kubernetes APIs. When these policies are applied, they are automatically converted into Calico network policies and Calico enforces these policies.

###### Calico network policies for Kubernetes

Calico network policies are a superset of the Kubernetes network policies and are applied by using calicoctl commands.

Calico policies add the following features:
  - Allow or block network traffic on specific network interfaces regardless of the Kubernetes pod source or destination IP address or CIDR.
  - Allow or block network traffic for pods across namespaces.
  - Block inbound (ingress) traffic to LoadBalancer or NodePort Kubernetes services.

Calico enforces these policies, including any Kubernetes network policies that are automatically converted to Calico policies, by setting up Linux iptables rules on the Kubernetes worker nodes. Iptables rules serve as a firewall for the worker node to define the characteristics that the network traffic must meet to be forwarded to the targeted resource.

### Traffic flows

#### External user on the internet to a web tier hosted in a container in IKS

1. The external user makes a request to the web tier by using the URL.
2. DNS is used to determine the IP address. This IP address is an IBM Cloud public address on a portable subnet that is assigned to the ALB or Ingress Service.
3. The public network will automatically forward the request to worker node hosting the ALB or Ingres Service.
4. The worker node forwards the request to the internal cluster IP address and port number of the ALB or Ingress Service. This internal cluster IP address is accessible inside the cluster only.
5. Within the worker node, kube-proxy routes the request to the ALB or Ingress Service.
6. If the app is on the same worker node, then iptables is used to determine which internal interface is used to forward the request. If the app is on a different worker node, then the Calico vRouter routes to the applicable worker node, by using IP-in-IP encapsulation only if the worker node is on a different subnet.

#### Web tier hosted in a container in IKS to database tier hosted in a VM in VCS

Endpoint resources are created that detail external database VMs that include the NAT IP address and port number of the mysql database VMs, for example.

- kind: Endpoints
- apiVersion: v1
- metadata:
  - name: mysqldb
- subsets:
  - addresses:
      - ip: 10.x.x.x
  - ports:
      - port: 3306

The Endpoint resource can have several addresses that are listed, and Kubernetes will round-robin between those addresses.  

Service resources are used to create an IP and a DNS name in kube-dns for services:

- kind: Service
- apiVersion: v1
- metadata:
  - name: mysqldb
- labels:
  - name: mysqldb
- spec:
  - ports:
    - protocol: TCP
    - port: 3306

**Flow**

1.	The web tier running in a container in IKS makes a request to the
database running on a VM in the VCS instance by calling mysqldb.
Kubernetes will resolve this name to an IP address and send this request
out of the cluster with a destination IP address of the NAT'ed IP of the
database server (10.x/26) and a source IP of the worker node (10.x/26).
2.	As the destination IP address is not on the same subnet as the
worker node, it will be forwarded to the IBM Cloud BCR.
3.	The BCR
will route the request and place the request on the Private A VLAN,
Customer Workloads subnet, on which the customer-nsx-edge is connected.
This NSX Edge has:
     - Firewall rule allowing this connection.
     - DNAT rule that changes the destination IP address from the
10.x address to the 192.168 address being used for the database server.
4.	The ESG then forwards to the DLR.
5.	The DLR places the request
onto the required VXLAN.
6.	The database VM receives the request.

## Backup and DR

### VCS backup
As part of IBM Cloud for VMware solution, Veeam backup software is
optionally deployed on an IBM Cloud virtual server instance (VSI) using
IBM Cloud Endurance storage outside the VMware cluster. The purpose of
this software is to back up the management components in this solution.

### NSX backup
Proper backup of all NSX components is crucial to restore the system to
its working state if failure occurs. It is not sufficient to back up the
NSX VMs. The NSX backup function within the NSX manager must be employed
for a proper backup. This backup requires that an FTP or SFTP server is
specified for the repository of NSX backup data. The NSX Manager backup
contains all of the NSX configuration, including controllers, logical
switching and routing entities, security, firewall rules, and everything
else that you configure within the NSX Manager UI or API. The vCenter
database and related elements like the virtual switches are backed up
separately. The NSX configuration should be backed up along with a
vCenter backup.

### Backup and DR for IKS
Backups of the etcd database are provided to the customer as part of the
managed service, any application data must be backed by yourself.

## Scalability

### VCS scalability
After the deployment of the initial hosts, the user has the ability to
scale out the compute capacity from within the IBM Cloud for VMware
portal. This scale out of the environment follows one of three paths:
- Addition of new sites managed by separate vCenter Servers.
- Addition of new clusters.
- Addition of new hosts to an existing cluster.

#### 	Multi–site deployments
VMware on IBM Cloud can use IBM Cloud’s world–wide data center presence
and integrated network backbone to allow for various cross–geography use
cases to be deployed and functioning within a fraction of the time it
would take to build such an infrastructure from scratch.

#### Scale out with new cluster
The user can also scale out the compute capacity by creating a new
cluster from within the console, ordering the hosts, and the new hosts
are automatically added to the new cluster. This option creates an extra
cluster in the environment and gives users the ability to physically and
logically segregate management workloads from application workloads, the
ability to segregate workloads based on other characteristics (for
example, Microsoft SQL database cluster), and the ability to deploy
applications in highly available topologies.

#### Scale out existing cluster
The user can scale out an existing cluster by ordering hosts from within
the console and the new hosts are automatically added to the cluster.
Users might need to adjust the HA reservation policy for the cluster
based on their reservation requirements.

### IKS expansion
Users can provision an IKS environment via the IBM Cloud Portal to
extend or use a container environment. Application deployments into IKS
can be done via:
  - IKS connection and services are developed in CAM and published to
ICP catalog.
  - Multi-Cloud Manager future enhancement to manage IKS instances.
  - Helm Command Line.
  - Use Multizone clusters to increase high availability.

[Planning your cluster and worker node setup](../../../../containers/cs_clusters_planning.html#plan_clusters) explains the options and process to design a solution to meet your requirements.

## Security and compliance
When it comes to meeting strict industry guidelines, IBM Cloud has done the work for you, fostering true compliance. [Compliance on the IBM Cloud](https://www.ibm.com/cloud/compliance) provides details on the specific compliance certifications, global regulations, alignments, and frameworks for security and privacy. [Security for IBM Cloud Kubernetes Service](../../../../containers/cs_secure.html#security) details IKS security features.

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)

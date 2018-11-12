---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-06"

---

# Network access and flows

## Container application access – ICP

There are three main ways to obtain external traffic/access into your Kubernetes cluster applications:
- NodePort
- LoadBalancer
- Ingress

### NodePort
Nodeports are a simple way of exposing external access to a workload for initial development and testing but not recommended for production. Ingress or load balancer is the recommended path.

### LoadBalancer
Currently, the ICP Platform supports an external Load Balancer for application workload.

### Ingress
An Ingress is a collection of rules that allow inbound connections to reach the cluster services. It can be configured to give services externally reachable URLs, load balance traffic, terminate SSL, offer name-based virtual hosting, and more.  The Proxy node in ICP infrastructure performs this function.

## Container application access – IKS
There are three main ways to obtain external traffic/access into your Kubernetes cluster applications:
- NodePort
- LoadBalancer
- Ingress

### NodePort
Nodeports are a simple way of exposing external access to a workload for initial development and testing but not recommended for production. Ingress or load balancer is the recommended path.

### LoadBalancer
Every IKS Cluster, is provisioned with a public/private Application Load Balancer (ALB). The ALB uses a secured and unique public or private entry point to route incoming requests to your apps.

### Ingress
An Ingress is a collection of rules that allow inbound connections to reach the cluster services. It can be configured to give services externally reachable URLs, load balance traffic, terminate SSL, offer name-based virtual hosting, and more.

## Traffic flows
The following traffic flows will be described:
- External user on the Internet to a web tier hosted in a container in ICP.
- Web tier hosted in a container in ICP to database tier hosted in a VM in VCS.
- Enterprise user on the corporate network access to a VM in VCS.

### External user on the Internet to a web tier hosted in a container in ICP
1. The external user makes a request to the web tier using the URL.
2.	DNS is used to determine the IP address. This IP address will be an {{site.data.keyword.cloud}} public address on a portable subnet that has been assigned to the VCS Instance.
3.	The public network will automatically forwarded the request to the vSphere ESXi host hosting the ESG.
4.	The ESG will forward the request to the internal cluster IP address and port number of the ALB or Ingress Service. The IP packet will be encapsulated in a VXLAN frame if the ESG and the ALB or Ingress Service are on different vSphere ESXi hosts. This internal cluster IP address is accessible inside the cluster only.
5.	Within the worker node, kube-proxy routes the request to the ALB or Ingress Service.
6.	If the application is on the same worker node, then iptables is used to determine which internal interface is used to forward the request. If the application is on a different worker node, then the Calico vRouter routes to the applicable worker node, using IP-in-IP encapsulation. The IP-in-IP packet will be encapsulated in a VXLAN frame for transport to the vSphere ESXi host where the worker node is located.

### Web tier hosted in a container in ICP to database tier hosted in a VM in VCS
How the route tables in the ESG and vRouters are populated depends on the method of integration. See ICP and VCS Integration.
1.	The web tier running in a container in ICP makes a request to a database running on a VM in the same VCS instance.
2.	DNS is used to resolve the request to the IP address of the database.
3.	The container sends the request to the Calico vRouter.
4.	The vRouter has its route table populated with the IP address ranges hosted on the VCS instance.
5.	The vRouter forwards the request but uses SNAT to change the source IP address from the IP address of the pod to the IP address of the worker node.
6.	The worker node hosting the vRouter sends the request to the ESG.
7.	The ESG then forwards to the DLR.
8.	The DLR places the request onto the required VXLAN.
9.	The database VM receives the request.

### 	Enterprise user on the corporate network access to a VM in VCS
1.	An enterprise user connected to the enterprise internal network makes a request of a resource on a VM hosted in VCS.
2.	DNS is used to determine the IP address of the VM. This IP address is on a network that has been stretched to {{site.data.keyword.cloud_notm}}.
3.	The on-premises router directs the traffic to the vSphere host that is hosting the L2 Concentrator.
4.	The L2 concentrator encapsulates the request in a secure tunnel and forwards it to the remote L2 Concentrator hosted in {{site.data.keyword.cloud_notm}} using the private portable subnet IP address assigned to the device, via the on-premises router.
5.	The on-premises route looks in its routing table and discerns that the IP address for the remote L2 Concentrator needs to be sent to the WAN interface and it forwards across the WAN, through the {{site.data.keyword.cloud_notm}} XCR router, via the BCR.
6.	The L2 Concentrator receives the request and places it on the VXLAN that hosts the stretched network.
7.	The VM receives the request.

## Public access network
ICP and CAM by default require Internet connectivity to retrieve Docker images, Helm charts, Terraform templates, and operating system package managers.
In the latest releases, there is now support for proxy based installs for installations that are not directly connected to the Internet and have options to install in an offline mode.

###	NSX firewall
The ICP NSX Edge firewall, is configured with rules to allow:
*	Enable VXLAN networks access to public access.
*	Enable VXLAN networks access to private {{site.data.keyword.cloud_notm}} network access.
*	Enable private {{site.data.keyword.cloud_notm}} network access to VXLAN networks.

### NSX NAT
The ICP NSX NAT, is configured with the following NATs:
*	SNAT for VXLAN networks access to public access.
*	SNAT for VXLAN networks access to private {{site.data.keyword.cloud_notm}} network access.
*	DNAT for ICP Cluster vIPs.

### Related links

* [VCS Hybridity Bundle overview](../vcs/vcs-hybridity-intro.html)

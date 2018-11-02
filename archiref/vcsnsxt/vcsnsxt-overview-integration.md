---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-29"

---

# Integration, IP addressing, and network flows

## ICP and VCS integration

IBM Cloud Private is installed on several virtual machines on a VCS instance. Within the VCS instance, the ICP instance is deployed with a dedicated NSX Edge Services Gateway (ESG) and Distributed Logical Router (DLR) and uses a VXLAN.

The ESG is configured with a SNAT rule to allow outbound traffic, enabling internet connectivity to download the ICP prerequisites and connectivity to GitHub and Docker. A web proxy server can be used to provide the internet connectivity if wanted. The ESG is configured with private connectivity to access DNS and NTP services. The ESG is also configured with a DNAT rule to enable the ICP Master and Proxy vIPs to be accessed from the IBM Cloud 10.x network.

## IKS and VCS integration

Currently, there are the following scenarios to integrate IKS and VCS networking:
- **Common VLAN** - This requires that the IKS worker nodes are deployed onto the same VLAN as the VCS instance. This allows an ESG to be a BGP peer to the worker nodes.
- **strongSwan VPN** – This scenario uses the standard IKS to enterprise connectivity solution. A strongSwan container provides a VPN gateway for the cluster that forwards packets to remote networks across an IPSec tunnel to the remote gateway. This remote gateway is an ESG on the VCS instance. On the gateways, routes are configure sending all cluster and service IP ranges to the strongSwan container and all VCS BYOIP addresses to the ESG. The target IP addresses for the gateways are the private portable IP address of the load balancer service that is assigned to the strongSwan container and the private portable IP address of the ESG.
- **Static routes and NAT**.
- **BGP Peering** – BGP peering is not a default offering in IBM Cloud and must be requested and approved. Once enabled, BGP peering allows the Calico vRouters and the ESG to advertise routes to the BCR.

## IKS and ICP integration

IKS and ICP integration uses strongSwan VPN connectivity with a strongSwan container in ICP and IKS.

## IP address allocation

From an administrative perspective, the reference architecture has the following conceptual network ranges:
-	**IKS pod network** - All pods that are deployed to a worker node are assigned a private IP address in the 172.30.0.0/16 range and are routed between worker nodes only. To avoid conflicts, don't use this IP range on any nodes that communicate with your worker nodes. Worker nodes and pods can securely communicate on the private network by using private IP addresses. However, when a pod crashes or a worker node needs to be re-created, a new private IP address is assigned.
-	**IKS service network** – IKS uses 172.21.0.0/16 for service addresses within the cluster. There are two other IP address ranges:
    - Public – A public portable subnet with an IP address range provided by IBM Cloud. This IP address range is used to expose apps to the internet via ALB or Ingress services.
    - Private – A private portable subnet with an IP address range provided by IBM Cloud. This IP address range is used to expose apps to the private network via ALB or Ingress services.
- **IKS worker nodes network** - There are two worker node network IP address ranges:
    - Public – A public primary subnet with an IP address range provided by IBM Cloud.
    - Private – A private primary subnet with an IP address range provided by IBM Cloud.
-	**VCS host network** - There are two VCS host network IP address ranges:
    - Public – A public primary subnet with an IP address range provided by IBM Cloud.
    - Private – A private primary subnet with an IP address range provided by IBM Cloud.
-	**VCS ESG network** - There are two VCS ESG network IP address ranges
    - Public – A public portable subnet with an IP address range provided by IBM Cloud.
    - Private – A private portable subnet with an IP address range provided by IBM Cloud.
-	**VCS VM network** – An enterprise IP address range that uses a BYOIP range that does not clash with any IBM Cloud provided subnet.
-	**ICP pod network** – An enterprise IP address range that uses a BYOIP range that does not clash with any IBM Cloud provided subnet. Pod and service IP address ranges can be configured in cluster/config.yaml.
-	**ICP service network** – An enterprise IP address range that uses a BYOIP range that does not clash with any IBM Cloud provided subnet. Pod and service IP address ranges can be configured in cluster/config.yaml.
-	**ICP worker nodes network** – An enterprise IP address range that uses a BYOIP range that does not clash with any IBM Cloud provided subnet.

## Network traffic flows

The following traffic flows are described:
-	External user on the internet to a web tier hosted in a container in IKS.
-	External user on the internet to a web tier hosted in a container in ICP.
-	Web tier hosted in a container in IKS to database tier hosted in a VM in VCS.
-	Web tier hosted in a container in ICP to database tier hosted in a VM in VCS.
-	Enterprise user on the corporate network access to a VM in VCS.

### External user on the internet to a web tier hosted in a container in IKS

1.	The external user makes a request to the web tier by using the URL.
2.	DNS is used to determine the IP address. This IP address is an IBM Cloud public address on a portable subnet that has been assigned to the ALB or Ingress Service.
3.	The public network will automatically forwarded the request to worker node hosting the ALB or Ingres Service.
4.	The worker node will forward the request to the internal cluster IP address and port number of the ALB or Ingress Service. This internal cluster IP address is accessible inside the cluster only.
5.	Within the worker node, kube-proxy routes the request to the ALB or Ingress Service.
6.	If the app is on the same worker node then iptables is used to determine which internal interface is used to forward the request. If the app is on a different worker node then the Calico vRouter routes to the applicable worker node, using IP-in-IP encapsulation only if the worker node is on a different subnet.

### External user on the internet to a web tier hosted in a container in ICP

1.	The external user makes a request to the web tier by using the URL.
2.	DNS is used to determine the IP address. This IP address will be an IBM Cloud public address on a portable subnet that has been assigned to the VCS Instance.
3.	The public network will automatically forwarded the request to the vSphere ESXi host hosting the ESG.
4.	The ESG will forward the request to the internal cluster IP address and port number of the ALB or Ingress Service. The IP packet will be encapsulated in a VXLAN frame if the ESG and the ALB or Ingress Service are on different vSphere ESXi hosts. This internal cluster IP address is accessible inside the cluster only.
5.	Within the worker node, kube-proxy routes the request to the ALB or Ingress Service.
6.	If the app is on the same worker node, then iptables is used to determine which internal interface is used to forward the request. If the app is on a different worker node then the Calico vRouter routes to the applicable worker node, by using IP-in-IP encapsulation. The IP-in-IP packet will be encapsulated in a VXLAN frame for transport to the vSphere ESXi host where the worker node is located.

### Web tier hosted in a container in IKS to database tier hosted in a VM in VCS

How the route tables in the ESG and vRouters are populated depends on the method of integration. See IKS and VCS Integration.
1.	The web tier running in a container in IKS makes a request to a database running on a VM in the VCS instance.
2.	DNS is used to resolve the request to the IP address of the database.
3.	The container sends the request to the Calico vRouter.
4.	The vRouter has its route table that is populated with the IP address ranges hosted on the VCS instance.
5.	The vRouter forwards the request but uses SNAT to change the source IP address from the IP address of the pod to the IP address of the worker node.
6.	The worker node hosting the vRouter sends the request to the BCR.
7.	The BCR forwards the request to the ESG.
8.	The ESG then forwards to the DLR.
9.	The DLR places the request onto the required VXLAN.
10.	The database VM receives the request.

### Web tier hosted in a container in ICP to database tier hosted in a VM in VCS

How the route tables in the ESG and vRouters are populated depends on the method of integration. See ICP and VCS Integration.
1.	The web tier running in a container in ICP makes a request to a database running on a VM in the same VCS instance.
2.	DNS is used to resolve the request to the IP address of the database.
3.	The container sends the request to the Calico vRouter.
4.	The vRouter has its route table that is populated with the IP address ranges hosted on the VCS instance.
5.	The vRouter forwards the request but uses SNAT to change the source IP address from the IP address of the pod to the IP address of the worker node.
6.	The worker node hosting the vRouter sends the request to the ESG.
7.	The ESG then forwards to the DLR.
8.	The DLR places the request onto the required VXLAN.
9.	The database VM receives the request.

### Enterprise user on the corporate network access to a VM in VCS

1.	An enterprise user connected to the enterprise internal network makes a request of a resource that is located on a VM hosted in VCS.
2.	DNS is used to determine the IP address of the VM. This IP address is on a network that has been stretched to IBM Cloud.
3.	The on-premises router directs the traffic to the vSphere host that is hosting the L2 Concentrator.
4.	The L2 concentrator encapsulates the request in a secure tunnel and forwards it to the remote L2 Concentrator hosted in IBM Cloud using the private portable subnet IP address assigned to the device, via the on-premises router.
5.	The on-premises route looks in its routing table and discerns that the IP address for the remote L2 Concentrator needs to be sent to the WAN interface and it forwards across the WAN, through the IBM Cloud XCR router, via the BCR.
6.	The L2 Concentrator receives the request and places it on the VXLAN that hosts the stretched network.
7.	The VM receives the request.

### More resources

* [IBM Cloud network](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [Container white paper](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf) (PDF download)
* [VMware HCX on IBM Cloud blog](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [VMware HCX on IBM Cloud data sheet](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on IBM Cloud Solution Architecture](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [NSX for vSphere 6.4.3 configuration maximums](https://configmax.vmware.com/guest)
* [IBM Cloud platform documentation](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [IBM Cloud Kubernetes service](https://console.bluemix.net/docs/containers/container_index.html#container_index)
* [Project Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)

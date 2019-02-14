---

copyright:

  years:  2016, 2019

lastupdated: "2018-01-14"

---

# 통합, IP 주소 지정 및 네트워크 플로우

## IBM Cloud Private 및 VMware vCenter Server on IBM Cloud 통합

{{site.data.keyword.cloud}} Private는 vCenter Server 인스턴스의 여러 가상 머신에 설치됩니다. vCenter Server 인스턴스 내에서, {{site.data.keyword.icpfull_notm}} 인스턴스는 전용 NSX ESG(Edge Services Gateway) 및 DLR(Distributed Logical Router)로 배치되고 VXLAN을 사용합니다. 

ESG는 아웃바운드 트래픽을 허용하도록 소스 NAT 규칙(SNAT)을 사용하여 구성되며, 인터넷 연결을 통해 {{site.data.keyword.icpfull_notm}} 전제조건을 다운로드하고 GitHub 및 Docker에 연결할 수 있습니다. 또는 인터넷 연결을 위해 웹 프록시를 사용할 수 있습니다. ESG는 사설 연결로 구성되어 DNS와 NTP 서비스에 액세스합니다. ESG는 {{site.data.keyword.icpfull_notm}} Master와 Proxy vIP가 {{site.data.keyword.cloud_notm}} 10.x 네트워크에서 액세스할 수 있도록 DNAT 규칙을 사용하여 구성됩니다. 

## IBM Cloud Kubernetes Service 및 vCenter Server 통합

현재 다음 시나리오는 {{site.data.keyword.containerlong_notm}} 및 vCenter Server 네트워킹을 통합합니다. 
- **공통 VLAN** - {{site.data.keyword.containerlong_notm}} 작업자 노드가 vCenter Server 인스턴스와 동일한 VLAN에 배치되어야 합니다. 공통 VLAN을 통해 ESG는 작업자 노드에 대한 BGP 피어가 됩니다.
- **strongSwan VPN** - 이 시나리오에서는 {{site.data.keyword.containerlong_notm}}-엔터프라이즈 연결 솔루션을 사용합니다. strongSwan 컨테이너는 원격 게이트웨이에 대한 IPSec 터널을 통해 패킷을 원격 네트워크로 전달하는 클러스터에 VPN
게이트웨이를 제공합니다. 이 원격 게이트웨이는 vCenter Server 인스턴스의 ESG입니다. 게이트웨이에서 라우트는 모든 클러스터와 서비스 IP 범위를 strongSwan 컨테이너로 보내고 모든 vCenter Server BYOIP 주소를 ESG로 보내도록 구성됩니다. 게이트웨이의 대상 IP 주소는 strongSwan 컨테이너에 지정된 로드 밸런서 서비스의 사설 포터블 IP 주소와 ESG의 사설 포터블 IP 주소입니다.
- **정적 라우트 및 NAT**.
- **BGP 피어링** – BGP 피어링은 {{site.data.keyword.cloud_notm}}의 기본 오퍼링이 아니므로 요청과 승인이 필요합니다. 이를 사용하도록 설정한 후 BGP 피어링을 사용하여 Calico vRouter와 ESG가 라우트를 BCR에 광고할 수 있습니다.

## IBM Cloud Kubernetes Service 및 IBM Cloud Private 통합

{{site.data.keyword.containerlong_notm}} 및 {{site.data.keyword.icpfull_notm}}의 통합은 {{site.data.keyword.icpfull_notm}}와 {{site.data.keyword.containerlong_notm}}에 있는 strongSwan 컨테이너와의 strongSwan VPN 연결을 사용합니다. 

## IP 주소 할당

관리적인 관점에서 참조 아키텍처에는 다음 개념 네트워크 범위가 있습니다.
-	**{{site.data.keyword.containerlong_notm}}팟(Pod) 네트워크** - 작업자 노드에 배치되는 모든 팟(Pod)은 172.30.0.0/16 범위의 사설 IP 주소가 지정되고, 작업자 노드 사이에서만 라우팅됩니다. 충돌을 방지하기 위해 작업자 노드와 통신하는 노드에서 이 IP 범위를 사용하지 마십시오. 작업자 노드와 팟(Pod)은 사설 IP 주소를 사용하여 사설 네트워크에서 안전하게 통신할 수 있습니다. 그러나 팟(Pod)이 충돌하거나 작업자 노드를 다시 작성해야 하는 경우 새 사설 IP 주소가 지정됩니다.
-	**{{site.data.keyword.containerlong_notm}}서비스 네트워크** - {{site.data.keyword.containerlong_notm}}는 클러스터 내의 서비스 주소에 172.21.0.0/16을 사용합니다. 두 가지 다른 IP 주소 범위는 다음과 같습니다. 
    - 공용 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
공용 포터블 서브넷. 이 IP 주소 범위는 ALB 또는 Ingress Service를 통해 앱을 인터넷에 노출시키는 데 사용됩니다. 
    - 사설 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
사설 포터블 서브넷. 이 IP 주소 범위는 ALB 또는 Ingress Service를 통해 앱을 사설 네트워크에 노출시키는 데 사용됩니다.
- **{{site.data.keyword.containerlong_notm}} 작업자 노드 네트워크** - 두 개의 작업자 노드 네트워크 IP 주소 범위가 있습니다.
    - 공용 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
공용 기본 서브넷.
    - 사설 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
사설 기본 서브넷.
-	**vCenter Server 호스트 네트워크** - 두 개의 vCenter Server 호스트 네트워크 IP 주소 범위가 있습니다.
    - 공용 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
공용 기본 서브넷.
    - 사설 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
사설 기본 서브넷.
-	**vCenter Server ESG 네트워크** - 두 개의 vCenter Server ESG 네트워크 IP 주소 범위가 있습니다.
    - 공용 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
공용 포터블 서브넷.
    - 사설 - {{site.data.keyword.cloud_notm}}에서 제공된 IP 주소 범위를 가진
사설 포터블 서브넷.
-	**vCenter Server VM 네트워크** - {{site.data.keyword.cloud_notm}} 제공 서브넷과 충돌하지 않는 BYOIP 범위를 사용하는 엔터프라이즈 IP 주소 범위. 
-	**{{site.data.keyword.icpfull_notm}} 팟(Pod) 네트워크** - {{site.data.keyword.cloud_notm}} 제공 서브넷과 충돌하지 않는 BYOIP 범위를 사용하는 엔터프라이즈 IP 주소 범위. 팟(Pod)과 서비스 IP 주소 범위는 cluster/config.yaml에서 구성될 수 있습니다.
-	**{{site.data.keyword.icpfull_notm}} 서비스 네트워크** - {{site.data.keyword.cloud_notm}} 제공 서브넷과 충돌하지 않는 BYOIP 범위를 사용하는 엔터프라이즈 IP 주소 범위. 팟(Pod)과 서비스 IP 주소 범위는 cluster/config.yaml에서 구성될 수 있습니다.
-	**{{site.data.keyword.icpfull_notm}} 작업자 노드 네트워크** - {{site.data.keyword.cloud_notm}} 제공 서브넷과 충돌하지 않는 BYOIP 범위를 사용하는 엔터프라이즈 IP 주소 범위. 

## 네트워크 트래픽 플로우

다음과 같은 트래픽 플로우에 대해 설명합니다.
-	인터넷 상의 외부 사용자와 {{site.data.keyword.containerlong_notm}}의 컨테이너에서 호스팅되는 웹 티어 사이의 트래픽 플로우
-	인터넷 상의 외부 사용자와 {{site.data.keyword.icpfull_notm}}의 컨테이너에서 호스팅되는 웹 티어 사이의 트래픽 플로우
-	{{site.data.keyword.containerlong_notm}}의 컨테이너에서 호스팅되는 웹 티어와 vCenter Server의 VM에서 호스팅되는 데이터베이스 티어 사이의 트래픽 플로우
-	{{site.data.keyword.icpfull_notm}}의 컨테이너에서 호스팅되는 웹 티어와 vCenter Server의 VM에서 호스팅되는 데이터베이스 티어 사이의 트래픽 플로우
-	회사 네트워크의 엔터프라이즈 사용자가 vCenter Server의 VM에 액세스하는 트래픽 플로우

### 인터넷 상의 외부 사용자와 IBM Cloud Kubernetes Service의 컨테이너에서 호스팅되는 웹 티어 사이의 트래픽 플로우

1.	외부 사용자는 URL을 사용하여 웹 티어에 요청을 작성합니다.
2.	DNS는 IP 주소를 판별하는 데 사용됩니다. 이 IP 주소는 ALB 또는 Ingress Service에 지정되는 포터블 서브넷의 {{site.data.keyword.cloud_notm}} 공용 주소입니다.
3.	공용 네트워크는 ALB 또는 Ingres Service를 호스트하는 작업자 노드에 자동으로 요청을 전달합니다. 
4.	작업자 노드는 ALB 또는 Ingress 서비스의 내부 클러스터 IP 주소 및 포트 번호로 요청을 전달합니다. 이 내부 클러스터 IP 주소는 클러스터 안에서만 액세스할 수 있습니다.
5.	작업자 노드 내에서, kube-proxy는 요청을 ALB 또는 Ingress 서비스로 라우팅합니다.
6.	애플리케이션이 동일한 작업자 노드에 있는 경우에는 iptables를 사용하여 요청을 전달하는 데 어떤 내부 인터페이스가 사용되는지 판별합니다. 애플리케이션이 서로 다른 작업자 노드에 있으면, 작업자 노드가 다른 서브넷에 있는 경우에만 IP-in-IP 캡슐화를 사용하여 Calico vRouter가 해당 작업자 노드로 라우트됩니다. 

### 인터넷 상의 외부 사용자와 IBM Cloud Private의 컨테이너에서 호스팅되는 웹 티어 사이의 트래픽 플로우

1.	외부 사용자는 URL을 사용하여 웹 티어에 요청을 작성합니다.
2.	DNS는 IP 주소를 판별하는 데 사용됩니다. 이 IP 주소는 vCenter Server 인스턴스에 지정되는 포터블 서브넷의 {{site.data.keyword.cloud_notm}} 공용 주소입니다.
3.	공용 네트워크에서는 ESG를 호스팅하는 vSphere ESXi 호스트에 요청을 자동으로 전달합니다.
4.	ESG는 ALB 또는 Ingress 서비스의 내부 클러스터 IP 주소 및 포트 번호로 요청을 전달합니다. ESG와 ALB 또는 Ingress 서비스가 서로 다른 vSphere ESXi 호스트에 있는 경우 IP 패킷은 VXLAN 프레임에서 캡슐화됩니다. 이 내부 클러스터 IP 주소는 클러스터 안에서만 액세스할 수 있습니다.
5.	작업자 노드 내에서, kube-proxy는 요청을 ALB 또는 Ingress 서비스로 라우팅합니다.
6.	애플리케이션이 동일한 작업자 노드에 있는 경우에는 iptables를 사용하여 요청을 전달하는 데 어떤 내부 인터페이스가 사용되는지 판별합니다. 애플리케이션이 서로 다른 작업자 노드에 있는 경우라면 Calico vRouter에서 IP-in-IP 캡슐화를 사용하여 해당 작업자 노드로 라우팅합니다. IP-in-IP 패킷은 작업자 노드가 위치하는 vSphere ESXi 호스트에 전송을 위한 VXLAN 프레임에서 캡슐화됩니다.

### IBM Cloud Kubernetes Service의 컨테이너에서 호스팅되는 웹 티어와 vCenter Server의 VM에서 호스팅되는 데이터베이스 티어 사이의 트래픽 플로우

통합 방법에 따라 ESG 및 vRouter에 있는 라우트 테이블이 채워지는 방법이 달라집니다. {{site.data.keyword.containerlong_notm}} 및 vCenter Server 통합을 참조하십시오.
1.	{{site.data.keyword.containerlong_notm}}의 컨테이너에서 실행 중인 웹 티어는 vCenter Server 인스턴스의 VM에서 실행 중인 데이터베이스에 요청을 작성합니다.
2.	DNS는 데이터베이스의 IP 주소에 대한 요청을 해결하는 데 사용됩니다.
3.	컨테이너는 Calico vRouter로 요청을 전송합니다.
4.	vRouter에는 vCenter Server 인스턴스에서 호스팅되는 IP 주소 범위로 채워진 라우트 테이블이 있습니다.
5.	vRouter는 요청을 전달하지만 SNAT를 사용하여 팟(Pod)의 IP 주소에서 작업자 노드의 IP 주소로 소스 IP 주소를 변경합니다.
6.	vRouter를 호스팅하는 작업자 노드는 BCR에 요청을 전송합니다.
7.	BCR은 요청을 ESG로 전달합니다.
8.	그런 다음 ESG에서 DLR로 전달합니다.
9.	DLR은 요청을 필요한 VXLAN에 배치합니다.
10.	데이터베이스 VM에서 요청을 수신합니다.

### IBM Cloud Private의 컨테이너에서 호스팅되는 웹 티어와 vCenter Server의 VM에서 호스팅되는 데이터베이스 티어 사이의 트래픽 플로우

통합 방법에 따라 ESG 및 vRouter에 있는 라우트 테이블이 채워지는 방법이 달라집니다. {{site.data.keyword.icpfull_notm}} 및 vCenter Server 통합을 참조하십시오.
1.	{{site.data.keyword.icpfull_notm}}의 컨테이너에서 실행 중인 웹 티어는 동일한 vCenter Server 인스턴스의 VM에서 실행 중인 데이터베이스에 요청을 작성합니다.
2.	DNS는 데이터베이스의 IP 주소에 대한 요청을 해결하는 데 사용됩니다.
3.	컨테이너는 Calico vRouter로 요청을 전송합니다.
4.	vRouter에는 vCenter Server 인스턴스에서 호스팅되는 IP 주소 범위로 채워진 라우트 테이블이 있습니다.
5.	vRouter는 요청을 전달하지만 SNAT를 사용하여 팟(Pod)의 IP 주소에서 작업자 노드의 IP 주소로 소스 IP 주소를 변경합니다.
6.	vRouter를 호스팅하는 작업자 노드는 ESG에 요청을 전송합니다.
7.	그런 다음 ESG에서 DLR로 전달합니다.
8.	DLR은 요청을 필요한 VXLAN에 배치합니다.
9.	데이터베이스 VM에서 요청을 수신합니다.

### 회사 네트워크의 엔터프라이즈 사용자가 vCenter Server의 VM에 액세스하는 트래픽 플로우

1.	엔터프라이즈 내부 네트워크에 연결된 엔터프라이즈 사용자는 vCenter Server에서 호스팅되는 VM에 있는 리소스를 요청합니다.
2.	DNS는 VM의 IP 주소를 판별하는 데 사용됩니다. 이 IP 주소는 {{site.data.keyword.cloud_notm}}로 확장된 네트워크에 있습니다.
3.	온프레미스 라우터는 L2 Concentrator를 호스팅하는 vSphere 호스트에 트래픽을 전달합니다.
4.	L2 Concentrator는 안전한 터널에 요청을 캡슐화하고, 디바이스에 지정된 개인용 포터블 서브넷 IP 주소를 사용하여 {{site.data.keyword.cloud_notm}}에 호스팅되는 원격 L2 Concentrator로 온프레미스 라우터를 통해 요청을 전달합니다. 
5.	온프레미스 라우트는 라우팅 테이블에 요청을 잠그고 원격 L2 Concentrator에 대한 IP 주소를 WAN 인터페이스에 전송해야 하는지 및 {{site.data.keyword.cloud_notm}} XCR 라우터를 통해 WAN 전체에 전달할지를 BCR을 통해 파악합니다.
6.	L2 Concentrator는 요청을 수신하여 확장된 네트워크를 호스팅하는 VXLAN에 배치합니다.
7.	VM이 요청을 수신합니다.

### 추가 리소스

* [{{site.data.keyword.cloud_notm}} 네트워크](https://www.ibm.com/cloud-computing/bluemix/our-network)
* [컨테이너 백서](https://communities.vmware.com/servlet/JiveServlet/download/2741654-198902/Containers%20and%20Container%20Networking%20for%20Network%20Engineers.pdf)(PDF 다운로드)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 블로그](https://www.ibm.com/blogs/bluemix/2018/01/vmware-hcx-ibm-cloud-aka-really-cool-space-age-kind-now-available/)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 데이터 시트](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=26012526USEN)
* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [NSX for vSphere 6.4.3 구성 최대](https://configmax.vmware.com/guest)
* [{{site.data.keyword.cloud_notm}} 플랫폼 문서](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.0/kc_welcome_containers.html)
* [{{site.data.keyword.containerlong_notm}}](https://console.cloud.ibm.com/docs/containers/container_index.html)
* [Project Calico](https://www.projectcalico.org/)
* [GitHub-Calico](https://github.com/projectcalico/calico)
* [Kubernetes](https://kubernetes.io/)
* [GitHub-Flannel](https://github.com/coreos/flannel/)
* [GitHub-Canal](https://github.com/projectcalico/canal)

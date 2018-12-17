---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# 네트워크 액세스 및 플로우

## 컨테이너 애플리케이션 액세스 - ICP

Kubernetes 클러스터 애플리케이션으로 외부 트래픽과 액세스를 가져오는 세 가지 주요 방법이 있습니다.

- NodePort
- LoadBalancer
- Ingress

### NodePort
Nodeport는 초기 개발 및 테스트를 위해 워크로드에 외부 액세스를 노출하는 간단한 방법이지만 프로덕션에는 권장하지 않습니다. Ingress 또는 로드 밸런서가 권장 경로입니다.

### LoadBalancer
현재 ICP 플랫폼은 애플리케이션 워크로드에 대한 외부 로드 밸런서를 지원합니다.

### Ingress
Ingress는 인바운드 연결이 클러스터 서비스에 도달하도록 허용하는 규칙 콜렉션입니다. 이는 서비스에 외부적으로 접근할 수 있는 URL, 로드 밸런스 트래픽, SSL 종료, 오퍼 이름 기반 가상 호스팅 등을 제공하도록 구성할 수 있습니다.  ICP 인프라의 프록시 노드가 이 기능을 수행합니다.

## 컨테이너 애플리케이션 액세스 - IKS
Kubernetes 클러스터 애플리케이션으로 외부 트래픽과 액세스를 가져오는 세 가지 주요 방법이 있습니다.

- NodePort
- LoadBalancer
- Ingress

### NodePort
Nodeport는 초기 개발 및 테스트를 위해 워크로드에 외부 액세스를 노출하는 간단한 방법이지만 프로덕션에는 권장하지 않습니다. Ingress 또는 로드 밸런서가 권장 경로입니다.

### LoadBalancer
모든 IKS 클러스터는 공용 또는 개인용 ALB(Application Load Balancer)를 사용하여 프로비저닝됩니다. ALB는 안전하고 고유한 공용 또는 개인 시작점을 사용하여 수신 요청을 애플리케이션에 라우팅합니다.

### Ingress
Ingress는 인바운드 연결이 클러스터 서비스에 도달하도록 허용하는 규칙 콜렉션입니다. 이는 서비스에 외부적으로 접근할 수 있는 URL, 로드 밸런스 트래픽, SSL 종료, 오퍼 이름 기반 가상 호스팅 등을 제공하도록 구성할 수 있습니다.

## 트래픽 플로우
다음과 같은 트래픽 플로우에 대해 설명합니다.

- 인터넷 상의 외부 사용자와 {{site.data.keyword.cloud}} Private(ICP)의 컨테이너에서 호스팅되는 웹 티어 사이의 트래픽 플로우
- ICP의 컨테이너에서 호스팅되는 웹 티어와 VMware vCenter Server on {{site.data.keyword.cloud_notm}}의 가상 머신(VM)에서 호스팅되는 데이터베이스 티어 사이의 트래픽 플로우
- 회사 네트워크의 엔터프라이즈 사용자가 vCenter Server의 VM에 액세스하는 트래픽 플로우

### 인터넷 상의 외부 사용자와 ICP의 컨테이너에서 호스팅되는 웹 티어 사이의 트래픽 플로우

1. 외부 사용자는 URL을 사용하여 웹 티어에 요청을 작성합니다.
2.	DNS는 IP 주소를 판별하는 데 사용됩니다. 이 IP 주소는 vCenter Server 인스턴스에 지정되는 포터블 서브넷의 {{site.data.keyword.cloud_notm}} 공용 주소입니다. 
3.	공용 네트워크에서는 ESG를 호스팅하는 vSphere ESXi 호스트에 요청을 자동으로 전달합니다.
4.	ESG는 ALB 또는 Ingress 서비스의 내부 클러스터 IP 주소 및 포트 번호로 요청을 전달합니다. ESG와 ALB 또는 Ingress 서비스가 서로 다른 vSphere ESXi 호스트에 있는 경우 IP 패킷은 VXLAN 프레임에서 캡슐화됩니다. 이 내부 클러스터 IP 주소는 클러스터 안에서만 액세스할 수 있습니다.
5.	작업자 노드 내에서, kube-proxy는 요청을 ALB 또는 Ingress 서비스로 라우팅합니다.
6.	애플리케이션이 동일한 작업자 노드에 있는 경우에는 iptables를 사용하여 요청을 전달하는 데 어떤 내부 인터페이스가 사용되는지 판별합니다. 애플리케이션이 서로 다른 작업자 노드에 있는 경우라면 Calico vRouter에서 IP-in-IP 캡슐화를 사용하여 해당 작업자 노드로 라우팅합니다. IP-in-IP 패킷은 작업자 노드가 위치하는 vSphere ESXi 호스트에 전송을 위한 VXLAN 프레임에서 캡슐화됩니다. 

### ICP의 컨테이너에서 호스팅되는 웹 티어와 vCenter Server의 VM에서 호스팅되는 데이터베이스 티어 사이의 트래픽 플로우

통합 방법에 따라 ESG 및 vRouter에 있는 라우트 테이블이 채워지는 방법이 달라집니다. ICP 및 vCenter Server 통합을 참조하십시오.

1.	ICP의 컨테이너에서 실행되는 웹 티어는 동일한 vCenter Server 인스턴스의 VM에서 실행되는 데이터베이스에 요청을 작성합니다.
2.	DNS는 데이터베이스의 IP 주소에 대한 요청을 해결하는 데 사용됩니다.
3.	컨테이너는 Calico vRouter로 요청을 전송합니다.
4.	vRouter에는 vCenter Server 인스턴스에서 호스팅되는 IP 주소 범위로 채워진 라우트 테이블이 있습니다.
5.	vRouter는 요청을 전달하지만 SNAT를 사용하여 팟(Pod)의 IP 주소에서 작업자 노드의 IP 주소로 소스 IP 주소를 변경합니다.
6.	vRouter를 호스팅하는 작업자 노드는 ESG에 요청을 전송합니다.
7.	그런 다음 ESG에서 DLR로 전달합니다.
8.	DLR은 요청을 필요한 VXLAN에 배치합니다.
9.	데이터베이스 VM에서 요청을 수신합니다.

### 	회사 네트워크의 엔터프라이즈 사용자가 vCenter Server의 VM에 액세스하는 트래픽 플로우

1.	엔터프라이즈 내부 네트워크에 연결된 엔터프라이즈 사용자는 vCenter Server에서 호스팅되는 VM에 리소스를 요청합니다.
2.	DNS는 VM의 IP 주소를 판별하는 데 사용됩니다. 이 IP 주소는 {{site.data.keyword.cloud_notm}}로 확장된 네트워크에 있습니다.
3.	온프레미스 라우터는 L2 Concentrator를 호스팅하는 vSphere 호스트에 트래픽을 전달합니다.
4.	L2 Concentrator는 안전한 터널에 요청을 캡슐화하고, 디바이스에 지정된 개인용 포터블 서브넷 IP 주소를 사용하여 {{site.data.keyword.cloud_notm}}에 호스팅되는 원격 L2 Concentrator로 온프레미스 라우터를 통해 요청을 전달합니다. 
5.	온프레미스 라우트는 라우팅 테이블에 요청을 잠그고 원격 L2 Concentrator에 대한 IP 주소를 WAN 인터페이스에 전송해야 하는지를 파악하고 {{site.data.keyword.cloud_notm}} XCR 라우터를 통해 WAN 전체에 전달합니다. 
6.	L2 Concentrator는 요청을 수신하여 확장된 네트워크를 호스팅하는 VXLAN에 배치합니다.
7.	VM이 요청을 수신합니다.

## 공용 액세스 네트워크
기본적으로 ICP 및 CAM은 Docker 이미지, Helm 차트, Terraform 템플리트 및 운영 체제 패키지 관리자를 검색하려면 인터넷에 연결되어 있어야 합니다.
최신 릴리스에서는 이제 인터넷에 직접 연결되지 않은 설치에 대한 프록시 기반 설치를 지원하고 오프라인 모드로 설치할 수 있는 옵션이 제공됩니다. 

###	NSX 방화벽
ICP NSX Edge 방화벽은 다음을 허용하기 위한 규칙으로 구성됩니다.
*	공용 액세스에 대한 VXLAN 네트워크 액세스 사용
*	사설 {{site.data.keyword.cloud_notm}} 네트워크 액세스에 대한 VXLAN 네트워크 액세스 사용
*	VXLAN 네트워크에 대한 사설 {{site.data.keyword.cloud_notm}} 네트워크 액세스 사용

### NSX NAT
ICP NSX NAT는 다음 NAT로 구성됩니다.
*	공용 액세스에 대한 VXLAN 네트워크 액세스용 SNAT
*	사설 {{site.data.keyword.cloud_notm}} 네트워크 액세스에 대한 VXLAN 네트워크 액세스용 SNAT
*	ICP 클러스터 vIP에 대한 DNAT

### 관련 링크

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 개요](../vcs/vcs-hybridity-intro.html)

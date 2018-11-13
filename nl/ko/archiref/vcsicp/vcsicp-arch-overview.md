---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# 아키텍처 개요

IBM Cloud for VMware 오퍼링은 VMware 기술 컴포넌트를 전 세계 IBM Cloud 데이터 센터에 배치하는 자동화 기능을 제공합니다. 이 아키텍처는 단일 클라우드 지역으로 구성되며 동일한 데이터 센터 내의 다른 지역 및/또는 다른 IBM Cloud 팟(Pod)에 위치한 여러 클라우드 지역으로 확장하는 기능을 지원합니다.

IBM Cloud Private(ICP) 및 CAM(Cloud Automation Manager) 제품은 온프레미스 가상화 플랫폼에 수동으로 배치할 수 있으며 온프레미스 위치에서 클라우드를 관리할 수 있습니다. 또는 ICP 및 CAM은 자동화를 통해 기존 또는 새로운 VMware vCenter Server on IBM Cloud(VCS) 배치에 대한 서비스 확장으로 제공되며 IBM Cloud에서 클라우드를 관리할 수 있습니다. 

ICP는 컨테이너화된 온프레미스 애플리케이션의 개발 및 관리를 위한 애프리케이션 플랫폼입니다. 컨테이너 오케스트레이터 Kubernetes, 개인용 이미지 저장소, 관리 콘솔 및 모니터링 프레임워크를 포함하는 컨테이너 관리를 위한 통합 환경입니다. 

IBM Multi-Cluster Manager(MCM)는 클라우드 및 클러스터에서 사용자 가시성, 애플리케이션 중심 관리(정책, 배치, 상태, 운영) 및 정책 기반 준수를 제공합니다. MCM을 사용하면 Kubernetes 클러스터를 제어할 수 있습니다. 클러스터가 개발자와 관리자가 비즈니스 요구를 충족시킬 수 있도록 ICP에서 실행되는 서비스 관리 플랫폼을 제공하고, 효율적으로 운영하며, 안전하게 보호하는지 확인할 수 있습니다.
Cloud Automation Manager Service Composer를 통해 ICP 카탈로그에서 하이브리드 클라우드 서비스를 노출시킬 수 있습니다. 

## IBM Cloud 측 클라우드 관리 플랫폼

그림 1. 클라우드 측에서 클라우드 관리

![클라우드에서 - 클라우드 관리](vcsicp-oncloud-cloudmgt.svg)

위의 다이어그램은 IBM Cloud에 배치된 온프레미스 vCenter 및 IBM Kubernetes Service(IKS) 서비스와의 연결을 통해 IBM Cloud 인프라와 함께 배치된 ICP 및 CAM을 나타냅니다. 사용자는 가상 머신을 온프레미스에, 가상 머신을 VCS 인스턴스에, 컨테이너를 ICP 및 IKS 클러스터에 배치할 수 있습니다. 

다이어그램에서 CAM은 vCenter, 클라우드 제공자, ICP 및 IKS 환경에 클라우드 연결을 논리적으로 작성합니다. ICP 클러스터를 단일 관리 보기로 연결하기 위한 메커니즘을 제공하는 MCM을 사용하여 각각의 데이터 센터/클라우드 환경에 ICP 클러스터를 배치해야 합니다. 

NSX-V 또는 NSX-T 컴포넌트로 ICP를 배치할 수 있습니다. NSX-V를 사용하는 ICP의 경우 ICP 가상 머신을 VXLAN 네트워크에서 실행하고 Kubernetes Calico 내부 네트워킹을 활용할 수 있습니다. 

NSX-T를 사용하는 ICP의 경우 사용자가 중앙 UI(NSX-T 관리자)에서 네트워킹, 서브넷, 정책을 제어하고 구성할 수 있습니다. NSX-V 및 NSX-T 간의 차이점에 대해서는 [IBM Cloud VCS 네트워킹 참조 아키텍처](../vcsnsxt/vcsnsxt-intro.html)를 참조하십시오.

## 온프레미스 클라우드 관리 플랫폼

그림 2. 온프레미스 측에서 클라우드 관리

![온프레미스 - 클라우드 관리](vcsicp-onprem-cloudmgt.svg)

위의 다이어그램은 IBM Cloud에 배치된 vCenter 및 IKS에 연결하여 온프레미스 인프라에 배치되는 ICP 및 CAM을 나타냅니다. 사용자는 가상 머신과 컨테이너를 온프레미스에, 가상 머신을 vCenter Server 인스턴스에, 컨테이너를 IKS 클러스터에 배치할 수 있습니다. 

strongSwan VPN은 배치된 IKS 컨테이너에 대한 연결을 설정하는 데 사용되며 나중에 Direct Link 연결로 대체될 수 있습니다. 

다이어그램에서 CAM은 vCenter, 클라우드 제공자, ICP 및 IKS 환경에 클라우드 연결을 논리적으로 작성합니다. ICP 클러스터를 단일 관리 보기로 연결하기 위한 메커니즘을 제공하는 MCM을 사용하여 각각의 데이터 센터/클라우드 환경에 ICP 클러스터를 배치해야 합니다. 

### 관련 링크

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

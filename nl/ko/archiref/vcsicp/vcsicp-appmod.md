---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-10"

---

# 애플리케이션 현대화 개요

다음 다이어그램은 Acme Skateboards에서 배치할 애플리케이션 현대화 참조 아키텍처를 보여주며 이 일련의 문서에서 자세히 설명합니다.

그림 1. 아키텍처 개요 다이어그램

![아키텍처 개요 다이어그램](vcsicp-arch-overview.svg)

이 하이브리드 아키텍처를 통해 Acme Skateboards에서는 다음을 수행할 수 있습니다.
- 애플리케이션 재구성 없이 가동 중단 시간이 짧거나 중단 없이 온프레미스에서 IBM Cloud로 VMware VM을 마이그레이션할 수 있습니다.
- 더 복잡한 데이터베이스를 VM 으로 유지할 수 있도록 허용하는 반면 보다 간단한 웹 인터페이스와 미들웨어를 컨테이너 저장할 수 있게 함으로써 애플리케이션 현대화 과정을 시작하도록 사용으로 설정할 수 있습니다.
- CAM(Cloud Automation Manager)을 활용하여 DevOps 도구 체인과 ITSM 솔루션을 통합하기 위해 VM 및 컨테이너 둘 다에서 작성된 서비스를 작성하고 조정하도록 IaC(Infrastructure as Code)를 스크립팅할 수 있습니다. 

참조 아키텍처에는 다음 주요 컴포넌트가 있습니다.
- **온프레미스 가상화** - Acme Skateboards VM을 현재 호스팅하고 있는 VMware 클러스터입니다. 현대화될 애플리케이션을 현재 호스팅하고 있는 VM입니다. 이 클러스터는 HCX를 실행할 수 있도록 [IBM Cloud vCenter Server with Hybridity Bundle](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)의 전제조건을 충족해야 합니다. HCX는 고객이 IBM Cloud에서 실행 중인 VMware vCenter Server on IBM Cloud(VCS) 인스턴스로 VM을 마이그레이션할 수 있는 IBM Cloud로 온프레미스 네트워크를 확장하며 필요한 경우 확장을 취소합니다. 

- **IBM Cloud for VMware Solutions** – VCS 인스턴스는 vSphere, vCenter Server, NSX-V와 같은 기본적인 VMware 빌딩 블록을 제공하며, VMware SDDC(Software Defined Data Center) 솔루션을 자동으로 배치하는 데 필요한 vSAN 또는 IBM Cloud Endurance 스토리지를 포함하여 스토리지 옵션을 제공합니다. VMware 클러스터는 ICP에서 호스팅되는 컨테이너의 일부 현대화된 애플리케이션 및 마이그레이션된 VM에 대한 대상입니다. VCS의 주요 컴포넌트는 다음과 같습니다.
    - **NSX-V** - NSX-V는 Acme Skateboards VM에 대한 네트워크 오버레이를 제공하는 VCS의 네트워크 가상화 계층입니다. NSX-V는 BYOIP를 사용으로 설정하고 IBM Cloud 네트워크에서 워크로드 네트워크를 격리합니다. NSX-V는 Acme Skateboards가 온프레미스에서 확장하는 네트워크를 작성하기 위해 HCX로 프로그래밍됩니다. 

    - **NSX-T** - NSX-T는 컨테이너 및 VM 모두에서 네트워크 및 보안 관리를 위한 공통 도구 세트를 제공합니다. NSX-T는 Kubernetes Container Networking Interface(CCNI)와 완전히 호환 가능하며 컨테이너 네트워킹을 제공하기 위해 CNI와 통합됩니다. NSX-T는 현대화된 애플리케이션이 사용하는 오버레이 네트워크를 제공하며 기본적으로 ICP및 IKS에서 사용하는 Calico를 대체합니다. 

- **IBM Cloud Private** - ICP는 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다. ICP는 컨테이너 오케스트레이터 Kubernetes, 개인용 이미지 저장소, 관리 콘솔, 모니터링 프레임워크 및 Acme Skateboards에서 애플리케이션을 배치, 관리, 모니터 및 확장할 수 있는 중앙 위치를 제공하는 그래픽 사용자 인터페이스가 포함된 통합 환경입니다. VCS 인스턴스는 VM으로 실행 중인 ICP 컴포넌트, 마스터 노드, 작업자 노드 등을 호스팅합니다. ICP는 다음을 호스팅합니다. 
    - **IBM Cloud Automation Manager** – CAM은 간단히 템플리트를 사용하여 Kubernetes 워크로드와 함께 ICP 또는 IKS의 온프레미스 또는 VCS에서 VM 워크로드를 프로비저닝하기 위해 단일 분할창 방식을 제공하는 엔터프라이즈용 IaC(Infrastructure as Code) 플랫폼입니다. CAM은 ICP의 상단에서 실행되는 도커화된 애플리케이션이며, 권한 부여, 역할 기반 액세스 제어(RBAC) 및 다른 기능을 위해 긴밀하게 통합됩니다. 
    - 이 환경에 배치하려는 컨테이너화된 Acme Skateboards 애플리케이션

- **IBM Kubernetes Service** – IKS를 통해 Acme Skateboards가 현대화된 애플리케이션을 Kubernetes 클러스터에서 실행되는 Docker 컨테이너에 배치할 수 있습니다. 작업자 풀에 있는 작업자 노드가 VCS 인스턴스와 동일한 IBM Cloud 계정으로 배치되는 동안 마스터 노드는 IBM에 의해 완전히 관리됩니다. 작업자 노드는 Bare Metal, 공용 또는 전용 가상 서버 인스턴스일 수 있습니다. Calico는 IKS에 자동으로 설치되고 구성됩니다. Calico는 컨테이너에 대한 안전한 네트워크 연결을 제공하며, 서브넷에서 이동하는 패킷에 IP-in-IP 캡슐화를 사용하고 컨테이너로부터의 발신 연결에 NAT를 사용하도록 KIS에 구성됩니다. 

- **Direct Link** – IBM Cloud Direct Link는 대기 시간이 짧고 신뢰할 수 있는 안전한 네트워크 연결을 제공하기 위해 Acme Skateboard의 WAN 제공자를 사용하여 데이터 센터를 IBM Cloud에 연결합니다. 이 연결은 다음을 제공합니다. 
    - 엔터프라이즈 사용자의 클라우드 호스팅 애플리케이션에 대한 액세스.
    - 온프레미스 VM과 클라우드 VM 간의 중간 VM 트래픽.
    - 온프레미스 데이터 센터의 레거시 시스템과 클라우드 VM 간의 트래픽.

## Acme Skateboards의 주요 이점

VMware vCenter Server on IBM Cloud(VCS)는 VMware vSphere, vCenter Server, NSX를 포함하는 기본적인 빌딩 블록을 제공하며, 클라이언트의 워크로드에 가장 적합한 VMware SDDC(Software Defined Data Center) 솔루션을 유연하게 설계하는 데 필요한 vSAN을 포함하는 공유 스토리지 옵션을 제공합니다. 

요약하자면, IBM Cloud for VMware 오퍼링은 

* 리소스의 조달, 아키텍처, 구현 및 배치에 걸리는 시간을 몇 주나 심지어는 몇 달에서 몇 시간으로 줄임으로써 개발자 및 비즈니스 라인을 위한 IT 프로젝트의 제공을 가속화합니다.
* 저장 데이터의 암호화를 포함하여 호스팅되는 프라이빗 클라우드의 전용 Bare Metal Server를 사용하여 보안을 개선합니다. 
* 가상화 관리에 대한 전체 관리 액세스를 제공하여 기존 VMware 도구, 스크립트 및 교육 투자를 그대로 유지함으로써 배치된 하이브리드 클라우드의 지속적인 관리 및 통제가 가능합니다. 
* 전세계 30여개의 IBM Cloud 데이터 센터에 걸쳐 있는 IBM Professional 및 Managed Services를 사용하여 글로벌 규모로 VMware 전문지식을 최대한 활용합니다. 

ICP및 IKS와 같은 클라우드 기반 애플리케이션 플랫폼으로 이동하는 고객은 속도와 혁신에 중점을 두고 있으며 항상 보안 및 네트워킹을 염두에 두고 있지는 않습니다. Load Balancer, 방화벽, 스위치, 라우터와 같은 서비스를 프로비저닝하기 위해 네트워킹 또는 보안 팀에서 대기하는 것은 가치 창출을 위한 애플리케이션 시간을 줄이는 것입니다. 이 참조 아키텍처는 VCS, ICP 및 IKS가 애플리케이션 현대화 과정을 따라 Acme Skateboards로 안전하게 이동하는 방법을 보여줍니다. 

## 관련 링크

* [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

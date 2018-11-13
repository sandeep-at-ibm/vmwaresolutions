---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

# vCenter Server 및 IBM Cloud Private 소개

이 문서는 통합된 다중 클라우드가 애플리케이션 현대화를 위해 활용되도록 하기 위해 클라우드 관리 컴포넌트를 중심으로 IBM Cloud에 대한 애플리케이션 현대화의 과정에 대한 보기를 제공합니다.

- **VMware vCenter Server on IBM Cloud** - VCS는 IBM Cloud for VMware Solutions의 오퍼링이며 IBM Cloud에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.

- **IBM Cloud Private** - ICP는 VMware와 같은 가상화된 인프라 플랫폼에 배치되도록 설계된 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다.

- **IBM Kubernetes Services** - IKS는 단일 테넌트 클러스터에서 애플리케이션 컨테이너의 운영, 확장 및 배치 자동화를 위한 오케스트레이션 엔진으로 Kubernetes를 활용하는 IBM Cloud의 관리 서비스입니다. 

- **IBM Multi-Cluster Manager** – MCM은 클라우드 및 클러스터에서 사용자 가시성, 애플리케이션 중심 관리(정책, 배치, 상태, 운영) 및 정책 기반 규제 준수를 제공합니다. MCM을 사용하면 Kubernetes 클러스터를 제어할 수 있습니다.

- **IBM Cloud Automation Manager** – CAM은 개발자와 관리자가 비즈니스 요구를 충족시킬 수 있는 ICP에서 실행되는 다중 클라우드의 셀프 서비스 관리 플랫폼입니다. 

## IBM Cloud의 애플리케이션 현대화
애플리케이션 현대화란 클라우드에 대한 새로운 접근 방식을 활용하기 위해 기존 애플리케이션을 전환하는 프로세스를 설명하는 용어입니다. 오늘날 고객들은 비즈니스 및 애플리케이션 복잡도를 기반으로 전환하는 데 도움이 되는 혁신적이고 효율적인 접근 방식을 찾고 있습니다. 

비즈니스에서는 출시 기간을 앞당기도록 요구하고 있습니다. 기존 자산에는 애플리케이션뿐만 아니라 데이터, 프로세스, 비즈니스 로직 및 사용자 인터페이스가 포함되며, 이들 모두 새로운 비즈니스 요구에 맞게 조정해야 합니다.

애플리케이션 현대화의 이점에는 다음이 포함됩니다.
- 개발자의 생산성 향상.
- 운영 효율성 증대.
- 새 기능을 구축하는 데 필요한 비용 절감.
- 짧은 시간에 제공되는 용량 증가.

IBM은 프라이빗 클라우드 도입의 70%가 애플리케이션 환경을 현대화할 필요성에 의해 수행되고 있다는 것을 알고 있지만, 대부분의 조직은 단계별 접근 방식으로 애플리케이션 현대화에 접근하고 있으며, 이는 다음과 같은 하이브리드 및 다중 클라우드 환경을 필요로 합니다.
- 일반적으로 메인프레임 또는 UNIX 시스템에서 실행되는 복잡한 모놀리식 레거시 애플리케이션은 온프레미스 환경에 남아 있습니다.
- SOR(System of Record)에 사용되는 x86 환경 또는 보안에 민감하거나 워크로드가 조정된 애플리케이션은 가상화된 인프라 또는 프라이빗 클라우드에 배치됩니다.
- SAP 또는 고성능 컴퓨팅과 같은 애플리케이션은 베어메탈 리소스를 사용합니다.
- 퍼블릭 클라우드로 이동할 수 있는 보안에 민감하고 일부 조정된 워크로드는 데디케이티드 환경으로 이동됩니다.
- 웹, 모바일, IoT, AI 또는 비디오 등의 SOE(System of Engagment)는 퍼블릭 클라우드로 이동합니다.

예를 들어, 공통적인 패턴은 데이터베이스와 함께 컨테이너로서 배치되는 프론트 엔드 SOE 애플리케이션과 프라이빗 클라우드에서 VM에 배치되는 레거시 미들웨어를 포함하는 것입니다.

IT 인프라 및 비즈니스의 요구는 고유하기 때문에, 비즈니스 가치 전달을 가속화하고, 위험을 줄이고, 기존 투자를 유지하는 데 도움을 주는 현대화의 접근 방식이 필요합니다. IBM에서는 애플리케이션 현대화와 관련된 고유한 비즈니스 및 기술 요구사항을 해결하기 위해 사용자 정의할 수 있는 이러한 접근 방식을 제공합니다.

이 문서는 IBM Cloud에 대한 애플리케이션 현대화 과정에서 사용되는 기술에 대해 서로 다른 보기를 제공하는 다섯 가지 문서 중 하나입니다.

참조 아키텍처 안내서, VCS - ICP 및 CAM - 현재 섹션.

다음 플랫폼을 배치하기 위한 참조 아키텍처:
  - **VMware vCenter Server on IBM Cloud** - IBM Cloud for VMware Solutions의 오퍼링이며 IBM Cloud에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
  - **IBM Cloud Private** – 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다. 컨테이너 오케스트레이터 Kubernetes뿐만 아니라 개인용 이미지 저장소, 관리 콘솔, 모니터링 프레임워크 및 애플리케이션을 배치, 관리, 모니터 및 확장할 수 있는 중앙 위치를 제공하는 그래픽 사용자 인터페이스가 포함된 통합 환경입니다. It is an integrated environment that includes the container orchestrator Kubernetes, as well as a private image repository, a management console, monitoring frameworks and a graphical user interface, which provides a centralized location from where you can deploy, manage, monitor, and scale your applications.
  - **IBM Cloud Automation Manager** – 저장소에 저장되고 버전화된 템플리트를 간단히 사용하여 Kubernetes 기반 워크로드와 함께 VM 기반 워크로드를 프로비저닝하기 위해 단일 분할창 방식을 제공하는 엔터프라이즈용 IaC(Infrastructure as Code) 플랫폼입니다. 

[참조 아키텍처 안내서, VCS - IKS](../vcsiks/vcsiks-intro.html)

  다음 플랫폼을 배치하기 위한 참조 아키텍처:
  - **VMware vCenter Server on IBM Cloud** - IBM Cloud for VMware Solutions의 오퍼링이며 IBM Cloud에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
  - **IBM Cloud Kubernetes Service** – 단일 테넌트 클러스터에서 애플리케이션 컨테이너의 운영, 확장 및 배치 자동화를 위한 오케스트레이션 엔진으로 Kubernetes를 활용하는 IBM Cloud의 관리 서비스입니다. 

[참조 아키텍처 안내서, VCS - 네트워킹](../vcsnsxt/vcsnsxt-intro.html)

이 문서는 NSX-V, NSX-T 및 Calico 등의 VCS, ICP 및 IKS 내에서 사용되는 네트워크 기술에 초점을 맞춥니다.

[참조 아키텍처 안내서, Watson 및 Sk8boarding 컨셉트 카](../vcscar/vcscar-intro.html)

이 문서는 Watson AI와 기계 학습 간의 상호작용을 보여주기 위해 “컨셉트 카” 접근 방식을 사용합니다.

문서에서는 다음과 같은 기술을 강조표시합니다.
  - **Pepper** - 애플리케이션을 수행하고 오퍼레이션을 검색하기 위해 클라우드 환경과 통합하는 기능이 포함되어 있는 인터페이스입니다. 
  - **VMware vCenter Server on IBM Cloud** - 데이터베이스 워크로드와 같은 애플리케이션의 요소를 호스팅하기 위해 활용합니다.
  - **IBM Cloud Kubernetes Service** - 애플리케이션의 컨테이너화된 요소를 호스팅하기 위해 활용합니다.
  - **IBM Cloud Private** - 플랫폼 및 서비스 레벨 오케스트레이션을 제공하기 위해 활용되며, VM 및 컨테이너 플랫폼에서 애플리케이션을 호스팅하고 확장하는 기능이 포함되어 있습니다. 또한 이 컴포넌트를 통해 플랫폼에 대한 Watson 개발자 서비스를 사용할 수 있으며 AI 기능에 대한 액세스를 허용합니다.

[참조 아키텍처 안내서, VCS – 컨텐츠](../vcscontent/vcscontent-intro.html)

이 문서는 IBM Cloud Automation Manager에서 사용 가능한 다음의 컨텐츠 유형에 집중합니다.
- 내부 카탈로그 컨텐츠(예: “사전 설치된” Helm 차트, Terraform 템플리트 및 Chef 레시피).
- 서비스 컨텐츠(예: Blockchain 및 Watson 서비스).

### 관련 링크

  * [VMware vCenter Server on IBM Cloud with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# vCenter Server 및 IBM Cloud Kubernetes Service 소개
{: #vcsiks-intro}

이 문서는 애플리케이션을 현대화하는 데 통합된 다중 클라우드를 사용할 수 있도록 다음 플랫폼의 네트워크 측면에 중점을 두고 {{site.data.keyword.cloud}}에 대한 애플리케이션 현대화 과정의 보기를 제공합니다.

이 문서는 애플리케이션을 현대화하는 데 통합된 다중 클라우드를 사용할 수 있도록 클라우드 관리 컴포넌트에 중점을 두고 {{site.data.keyword.cloud_notm}}에 대한 애플리케이션 현대화 과정의 보기를 제공합니다.

- **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - vCenter Server는 {{site.data.keyword.vmwaresolutions_full}}의 오퍼링이며 {{site.data.keyword.cloud_notm}}에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
- **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}}는 VMware와 같은 가상화된 인프라 플랫폼에 배치되는 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다.
- **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}}는 싱글 테넌트 클러스터에서 애플리케이션 컨테이너의 운영, 확장 및 배치 자동화를 위한 오케스트레이션 엔진으로 Kubernetes를 활용하는 {{site.data.keyword.cloud_notm}}의 관리 서비스입니다.
- **IBM Multi-Cluster Manager** – MCM은 클라우드 및 클러스터에서 사용자 가시성, 애플리케이션 중심 관리(정책, 배치, 상태, 운영) 및 정책 기반 규제 준수를 제공합니다. MCM을 사용하면 Kubernetes 클러스터를 제어할 수 있습니다.
- **{{site.data.keyword.cloud_notm}} Automation Manager** – CAM은 개발자와 관리자가 비즈니스 요구를 충족시킬 수 있는 {{site.data.keyword.icpfull_notm}}에서 실행되는 다중 클라우드 셀프 서비스 관리 플랫폼입니다.

## IBM Cloud의 애플리케이션 현대화
{: #vcsiks-intro-app-mod}

애플리케이션 현대화란 클라우드에 대한 새로운 접근 방식을 사용하기 위해 기존 애플리케이션을 전환하는 프로세스를 설명하는 용어입니다. 오늘날 고객들은 비즈니스 및 애플리케이션 복잡도를 기반으로 전환하는 데 도움이 되는 혁신적이고 효율적인 접근 방식을 찾고 있습니다.

비즈니스에서는 출시 기간을 앞당기도록 요구하고 있습니다. 기존 자산에는 애플리케이션뿐만 아니라 데이터, 프로세스, 비즈니스 로직 및 사용자 인터페이스가 포함되며, 이들 모두 새로운 비즈니스 요구에 맞게 조정해야 합니다.

애플리케이션 현대화의 이점에는 다음이 포함됩니다.
- 개발자의 생산성 향상.
- 운영 효율성 증대.
- 새 기능을 구축하는 데 필요한 비용 절감.
- 짧은 시간에 제공되는 용량 증가.

IBM은 프라이빗 클라우드 도입의 70%가 애플리케이션 환경을 현대화할 필요성에 의해 수행되고 있다는 것을 알고 있지만, 대부분의 조직은 단계별 접근 방식으로 애플리케이션 현대화에 접근하고 있으며, 이는 다음과 같은 하이브리드 및 다중 클라우드 환경을 필요로 합니다.
- 일반적으로 메인프레임 또는 UNIX 시스템에서 실행되는 복잡한 모놀리식 레거시 애플리케이션은 온프레미스 환경에 남아 있습니다.
- SOR(System of Record)에 사용되는 x86 환경, 보안에 민감한 애플리케이션 및 조정된 워크로드는 가상화된 인프라 또는 프라이빗 클라우드에 배치됩니다.
- SAP 또는 고성능 컴퓨팅과 같은 애플리케이션은 베어메탈 리소스를 사용합니다.
- 퍼블릭 클라우드로 이동할 수 있는 보안에 민감하고 일부 조정된 워크로드는 데디케이티드 환경으로 이동됩니다.
- 웹, 모바일, IoT, AI 또는 동영상 등의 SOE(System of Engagment)는 퍼블릭 클라우드로 이동합니다.

예를 들어, 공통적인 패턴은 데이터베이스와 함께 컨테이너로서 배치되는 프론트 엔드 SOE 애플리케이션과 프라이빗 클라우드에서 VM에 배치되는 레거시 미들웨어를 포함하는 것입니다.

IT 인프라 및 비즈니스의 요구는 고유하기 때문에, 비즈니스 가치 전달을 가속화하고, 위험을 줄이고, 기존 투자를 유지하는 데 도움을 주는 현대화의 접근 방식이 필요합니다. IBM에서는 애플리케이션 현대화와 관련된 고유한 비즈니스 및 기술 요구사항을 해결하기 위해 사용자 정의할 수 있는 이러한 접근 방식을 제공합니다.

이 문서는 {{site.data.keyword.cloud_notm}}의 애플리케이션 현대화 과정에서
사용되는 기술에 대한 다른 보기를 제공하는 5개 문서 중 하나입니다.

* [vCenter Server 및 {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro) - 다음 플랫폼을 배치하기 위한 참조 아키텍처입니다.
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - {{site.data.keyword.vmwaresolutions_full}}의 오퍼링이며 {{site.data.keyword.cloud_notm}}에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
  - **{{site.data.keyword.cloud_notm}} Private** – 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다. {{site.data.keyword.icpfull_notm}}는 컨테이너 오케스트레이터 Kubernetes, 개인용 이미지 저장소, 관리 콘솔, 모니터링 프레임워크 및 애플리케이션을 배치, 관리, 모니터 및 확장할 수 있는 중앙 위치를 제공하는 그래픽 사용자 인터페이스가 포함된 통합 환경입니다.
  - **{{site.data.keyword.cloud_notm}} Automation Manager** - 저장소에 저장되고 버전화된 템플리트를 사용하여 Kubernetes 기반 워크로드와 함께 VM 기반 워크로드를 프로비저닝하기 위해 단일 분할창 방식을 제공하는 엔터프라이즈용 IaC(Infrastructure as Code) 플랫폼입니다.
* [vCenter Server 및 {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro) - 다음 플랫폼을 배치하기 위한 참조 아키텍처입니다.
  - **VMware vCenter Server on {{site.data.keyword.cloud_notm}}** - {{site.data.keyword.vmwaresolutions_full}}의 오퍼링이며 {{site.data.keyword.cloud_notm}}에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
  - **{{site.data.keyword.containerlong_notm}}** - 싱글 테넌트 클러스터에서 애플리케이션 컨테이너의 운영, 확장 및 배치 자동화를 위한 오케스트레이션 엔진으로 Kubernetes를 활용하는 {{site.data.keyword.cloud_notm}}의 관리 서비스입니다.
* [vCenter Server 네트워킹](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro) - NSX-V, NSX-T 및 Calico 등 vCenter Server, {{site.data.keyword.icpfull_notm}} 및 {{site.data.keyword.containerlong_notm}} 내에서 사용되는 네트워크 기술을 설명합니다.
* [VMware 및 Skate Advisor Concept Car](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro) - 이 참조 아키텍처는 "컨셉트 카"입니다. 즉, 실제 문제점을 해결하는 기술을 강조표시하고 보여주기 위한 메커니즘입니다. 실질적인 방식으로 Watson AI와 기계 학습 간의 상호작용을 시연하려고 했습니다. 스케이트보드 문화를 통해 고유 방식으로 클라우드 서비스를 시연합니다. "컨셉트 카" 구현은 Skate Advisor라는 Acme Skateboard 애플리케이션에 대한 확장입니다. Skate Advisor는 사용자가 Watson 구동 엔진과 스케이트보드 트릭 대화를 할 수 있도록 하는 도구입니다.
* [VMware: Stock Trader의 현대화 과정](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney) - 이 참조 유스 케이스는 {{site.data.keyword.cloud_notm}} Private, IBM Middleware 컨텐츠, {{site.data.keyword.containerlong_notm}} 및 vCenter Server on {{site.data.keyword.cloud_notm}}를 사용하여 현대화되는 일반 WebSphere Application Server 애플리케이션에 대해 설명합니다. 모두가 클라우드 과정 중에 있으며 이 과정의 서로 다른 지점에 있습니다. 애플리케이션 설계자 Jane과 클라우드 인프라 설계자 Todd에 의한 점진적 단계를 통해 Stock Trader라는 기존 애플리케이션을 현대화합니다. 각 단계의 규모에 관계없이 과정의 각 단계를 수행하는 데 도움을 주는 예제와 비즈니스에 실현된 가치를 보여줍니다. 애플리케이션, DevOps, 통합 및 관리 등 4개의 테마에 초점을 맞춥니다. 모든 테마는 함께 작동하여 목표를 달성할 수 있도록 지원합니다. 하나의 테마(나머지 테마 없이)를 현대화하면 문제가 발생할 수 있습니다.

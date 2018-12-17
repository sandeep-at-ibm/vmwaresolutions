---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# VMware 및 Skate Advisor Concept Car 소개

다음 참조 아키텍처는 "컨셉트 카"입니다. 이는 실제 문제점을 해결하는 기술을 강조표시하고 보여주는 메커니즘입니다.
"컨셉트 카"는 오늘날 손쉽게 이용할 수 있는 서비스를 의미하지 않습니다.


또한 참조 아키텍처에서는 다음을 제공합니다.

-   여러 이해 당사자를 위한 공통 언어를 제공합니다.
-   문제를 해결하기 위해 기술 구현의 일관성을 제공합니다. 
-   증명된 참조 아키텍처에 대해 솔루션의 유효성 검증을 지원합니다. 
-   공통 표준, 스펙 및 패턴을 준수하도록 권장합니다. 

## ACME Skate Advisor 정보

실질적인 방식으로 Watson 인공 지능과 기계 학습 간의 상호작용을 시연하려고 하며, 이를 통해 스케이트보딩 문화를 보다 깊이 탐구합니다. 사용 가능한 서비스와 클라우드 인프라를 이 분야의 기술적 역량과 발전을 보여주는 고유한 방식으로 시연합니다.
"컨셉트 카"의 구현은 Skate Advisor라는 시범 Acme Skateboard 애플리케이션에 대한 확장입니다. Skate Advisor는 사용자가 Watson 구동 엔진과 스케이트보드 트릭 대화를 할 수 있도록 하는 도구입니다. 다음 인용은 샘플 대화입니다.

-   “Watson, 트릭 캐스퍼의 조합을 보여주세요”
-   “Watson, 트릭을 수행할 일반적인 위치를 보여주세요”
-   “Watson, 트릭 캐스퍼의 동영상을 보여주세요”

Acme Skate Advisor는 Watson Discovery Service를 활용하여 기사, 동영상, 블로그 및 기타 인터넷 기반 콘텐츠를 수집하여 학습된 트릭 데이터베이스 트릭을 작성하며, 애플리케이션에서 이를 조회할 수 있습니다.


또한 Skate Advisor 애플리케이션은 애플리케이션 현대화 플랫폼에서 구현되며, 이 플랫폼은
{{site.data.keyword.cloud_notm}} for VMware Services 플랫폼에 호스트된
{{site.data.keyword.cloud}} Private(ICP)를 통해 컨테이너 기반 서비스를 제공합니다.

Acme Skate Advisor 애플리케이션은 Watson 플랫폼과 애플리케이션 현대화 플랫폼을 모두 이용합니다. 

## 유스 케이스

### 애플리케이션 현대화 데모

애플리케이션 현대화 플랫폼에 배치된 애플리케이션을 시연합니다. 플랫폼에는
VMware vCenter Server on {{site.data.keyword.cloud_notm}} 오퍼링을 위해 {{site.data.keyword.cloud_notm}}에 배치된 ICP, CAM 및 NSX 컴포넌트가 포함되어 있습니다.


### Watson Assistant를 사용한 Watson 음성 인식

Acme Skate Advisor는 Watson 플랫폼에서 제공되는 음성-문자 변환 및 문자-음성 변환 서비스를 통해 사용자와 통신합니다.


### Watson Discovery Service 사용법 및 훈련

Acme Skate Advisor는 Watson Discovery Services를 사용하여 분류 언어를 적용하기 위한 트릭 데이터베이스와 온라인 서비스에서 검색된 트릭을 계속해서 추적합니다.


### Watson 서비스 사용법

다음 Watson 서비스를 사용하여 Acme Skate Advisor를 작성했습니다.
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## IBM Cloud의 애플리케이션 현대화

애플리케이션 현대화란 클라우드에 대한 새로운 개발 및 제공 방식을 사용하기 위해 기존 애플리케이션을 전환하는 프로세스를 설명하는 용어입니다. 오늘날 고객들은 비즈니스 및 애플리케이션 복잡도를 기반으로 전환하는 데 도움이 되는 혁신적이고 효율적인 접근 방식을 찾고 있습니다.

비즈니스에서는 출시 기간을 앞당기도록 요구하고 있습니다. 기존 자산에는 애플리케이션뿐만 아니라 데이터, 프로세스, 비즈니스 로직 및 사용자 인터페이스가 포함되며, 이들 모두 새로운 비즈니스 요구에 맞게 조정해야 합니다.

다음 목록은 애플리케이션 현대화의 이점을 설명합니다.

- 개발자의 생산성을 향상시킵니다.
- 작업 효율성을 높입니다.
- 새 기능을 빌드하기 위한 비용을 줄입니다.
- 짧은 시간에 제공되는 용량을 늘립니다.

IBM은 프라이빗 클라우드 도입의 70퍼센트가 애플리케이션 환경을 현대화할 필요성에 의해 수행되고 있다는 것을 알고 있습니다. 그러나 대부분의 조직은 단계별 접근 방식으로 애플리케이션 현대화에 접근하고 있으며, 이는 다음과 같은 하이브리드 및 다중 클라우드 환경을 필요로 합니다.

- 일반적으로 메인프레임 또는 UNIX 시스템에서 실행되는 복잡한 모놀리식 헤리티지 애플리케이션은 온프레미스 환경에 남아 있습니다.
- SOR(System of Record)에 사용되는 x86 환경 또는 보안에 민감하거나 워크로드가 조정된 애플리케이션은 가상화된 인프라 또는 프라이빗 클라우드에 배치됩니다.
- SAP 또는 고성능 컴퓨팅과 같은 애플리케이션은 베어메탈 리소스를 사용합니다.
- 퍼블릭 클라우드로 이동할 수 있는 보안에 민감하고 일부 조정된 워크로드는 데디케이티드 환경으로 이동됩니다.
- 웹, 모바일, IoT, AI 또는 비디오 등의 SOE(System of Engagment)는 퍼블릭 클라우드로 이동합니다.

예를 들어, 공통적인 패턴은 데이터베이스와 함께 컨테이너로서 배치되는 프론트 엔드 SoE 애플리케이션과 프라이빗 클라우드에서 VM에 배치되는 헤리티지 미들웨어를 포함하는 것입니다.

IT 인프라와 비즈니스 요구사항은 고유하므로, 현대화에 대한 접근 방식은 다음 우선순위를 제공해야 합니다.

* 비즈니스 가치 가속화
* 제공 시간 최소화
* 위험 감소
* 기존 투자 보존

IBM은 고유한 비즈니스 및 기술 요구사항을 해결하기 위해 사용자 정의할 수 있는 애플리케이션 현대화에 이러한 접근 방식을 제공합니다.

다음 문서는 {{site.data.keyword.cloud_notm}}의 애플리케이션 현대화 과정에서
사용되는 기술에 대한 다른 보기를 제공합니다.

* [vCenter Server 및 {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - 다음 플랫폼을 배치하기 위한 참조 아키텍처입니다.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server는 {{site.data.keyword.vmwaresolutions_short}}의 오퍼링이며 {{site.data.keyword.cloud_notm}}에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
   - **IBM Cloud Private** - ICP는 컨테이너화된 애플리케이션의 개발 및 관리를 위한 애플리케이션 플랫폼입니다. ICP는 컨테이너 오케스트레이터 Kubernetes, 개인용 이미지 저장소, 관리 콘솔, 모니터링 프레임워크 및 그래픽 사용자 인터페이스를 포함하는 통합 환경입니다. 사용자 인터페이스는 애플리케이션을 배치, 관리, 모니터 및 확장할 수 있는 중앙 위치를 제공합니다.
   - **IBM Cloud Automation Manager** - CAM은 저장소에 저장되고 버전화된 템플리트를 사용하여 Kubernetes 기반 워크로드와 함께 VM 기반 워크로드를 프로비저닝하기 위해 단일 분할창 방식을 제공하는 엔터프라이즈용 IaC(infrastructure as code) 플랫폼입니다.
* [vCenter Server 및 IBM Kubernetes 서비스](../vcsiks/vcsiks-intro.html) - 다음 플랫폼을 배치하기 위한 참조 아키텍처입니다.
   - **VMware vCenter Server on IBM Cloud** - vCenter Server는 {{site.data.keyword.vmwaresolutions_short}}의 오퍼링이며 {{site.data.keyword.cloud_notm}}에서 자동으로 프로비저닝되는 VMware 기반 플랫폼입니다.
   - **IBM Cloud Kubernetes Service** - IKS는 싱글 테넌트 클러스터에서 애플리케이션 컨테이너의 운영, 확장 및 배치 자동화를 위한 오케스트레이션 엔진으로 Kubernetes를 활용하는 {{site.data.keyword.cloud_notm}}의 관리 서비스입니다.
* [vCenter Server 네트워킹](../vcsnsxt/vcsnsxt-intro.html) - NSX-T의 기술 미리보기와 함께 NSX-V 및 Calico 등 vCenter Server, ICP 및 IKS 간의 통합에 사용되는 네트워크 기술을 설명합니다.
* _VMware 및 Skate Advisor Concept Car 안내서_ - "컨셉트 카"의 참조 아키텍처입니다. 즉, 실제 문제점을 해결하는 기술을 강조표시하고 보여주기 위한 메커니즘입니다. 실질적인 방식으로 Watson AI와 기계 학습 간의 상호작용을 시연하려고 했습니다. 스케이트보드 문화를 통해 고유 방식으로 클라우드 서비스를 시연합니다. "컨셉트 카" 구현은 Skate Advisor라는 Acme Skateboard 애플리케이션에 대한 확장입니다. Skate Advisor는 사용자가 Watson 구동 엔진과 스케이트보드 트릭 대화를 할 수 있도록 하는 도구입니다.
* [VMware: Stock Trader의 현대화 과정](../vcscontent/vcscontent-modjourney.html) - {{site.data.keyword.cloud_notm}} Private, IBM Middleware 컨텐츠, {{site.data.keyword.cloud_notm}} Kubernetes Service 및 vCenter Server on {{site.data.keyword.cloud_notm}}를 사용하여 현대화되는 일반 WebSphere Application Server 애플리케이션에 대해 설명하는 참조 유스 케이스입니다. 모두가 클라우드 과정 중에 있으며 이 과정의 서로 다른 지점에 있습니다. 애플리케이션 설계자 Jane과 클라우드 인프라 설계자 Todd에 의한 점진적 단계를 통해 Stock Trader라는 기존 애플리케이션을 현대화합니다. 각 단계의 규모에 관계없이 과정의 각 단계를 수행하는 데 도움을 주는 예제와 비즈니스에 실현되는 가치를 검토하십시오. 애플리케이션, DevOps, 통합 및 관리 등 4개의 테마에 초점을 맞춥니다. 각각은 함께 작동하여 목표를 달성할 수 있도록 지원합니다. 실제로 다른 것 없이 하나를 현대화하면 모든 면에서 문제점이 발생합니다.

### 관련 링크

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 개요](../vcs/vcs-hybridity-intro.html)

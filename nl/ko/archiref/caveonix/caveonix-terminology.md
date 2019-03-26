---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-06"

---

# Caveonix 용어집
{: #caveonix-terminology}

이 용어집에서는 Caveonix RiskForesight 솔루션과 연관된 용어의 설명을 제공합니다.

-	**NIST Special Publication 800-53:** 보안 제어를 처리하는 위험 관리 프레임워크입니다.
-	**SCAP(Security Content Automation Protocol):** 조직에 배치된 시스템의 취약성 관리, 측정 및 정책 규제 준수 평가를 자동화할 수 있는 특정 표준을 사용하는 방법입니다. 체크리스트를 통해 컴퓨터 보안 구성과 NIST Special Publication 800-53 제어 프레임워크 사이의 연계를 자동화하고 표준화합니다.
  - NVD(National Vulnerability Database)는 SCAP의 미국 정부 컨텐츠 저장소입니다.
  -	SCAP를 사용하면 보안 관리자가 사전 판별된 보안 기준선을 기반으로 컴퓨터, 소프트웨어 및 기타 디바이스를 스캔할 수 있으므로 구성과 소프트웨어 패치가 비교 기준인 표준에 맞게 구현되었는지 판별할 수 있습니다.
  SCAP 컴포넌트는 다음과 같습니다.
  -	CVE(Common Vulnerabilities and Exposures) - 공개적으로 알려진 사이버 보안 취약성 목록입니다.
  -	CCE(Common Configuration Enumeration) – 보안 관련 시스템 구성 문제 목록입니다.
  -	CPE(Common Platform Enumeration) - 정보 기술 시스템, 소프트웨어 및 패키지의 구조화된 이름 지정 스키마입니다.
  -	CWE(Common Weakness Enumeration) – 공통 소프트웨어 보안 약점 목록입니다.
  -	CVSS(Common Vulnerability Scoring System) - 취약성의 주요 특성을 캡처하고 해당 심각도를 나타내는 숫자 점수를 생성하는 방법을 제공합니다.
  -	XCCDF(eXtensible Configuration Checklist Description Format) - 보안 체크리스트, 벤치마크 및 관련 유형의 문서를 쓰는 데 사용하는 스펙 언어입니다. XCCDF 문서는 일부 대상 시스템 세트에 사용하는 보안 구성 규칙의 구조화된 콜렉션을 나타냅니다.
  -	Open Vulnerability and Assessment Language (OVAL) – 시스템 세부 정보를 인코딩하는 데 사용하고 컨텐츠 저장소를 분류하는 언어입니다. 이 언어에서는 분류 프로세스의 세 가지 기본 단계를 표준화합니다.
      - 테스트를 위해 시스템의 구성 정보 표시.
      -	시스템 분석(취약성, 구성 및 패치 상태).
      -	이 분류 결과 보고.
-	**STIG(Security Technical Implementation Guide):** 전체 보안을 강화하기 위해 네트워크, 서버, 컴퓨터 및 논리 디자인에서 보안 프로토콜을 표준화하는 사이버 보안 방법입니다. 이 안내서를 구현하면 소프트웨어, 하드웨어, 물리적 및 논리적 아키텍처의 보안이 강화되므로 취약성이 감소됩니다.
-	**서비스 제공자(Service Provider):** 최상위 레벨 조직입니다.
-	**클라우드 제공자(Cloud Provider)** - 소프트웨어 정의 클라우드가 작동하는 인프라를 제공합니다. 여러 클라우드 제공자에 맞게 RiskForesight를 구성할 수 있습니다.
-	**조직(Organizations):** 서비스 제공자의 테넌트 조직과 하위 조직입니다. 자산 저장소가 vCenter이면 조직 / 테넌트 목록은 수동으로 작성해야 합니다.
-	**역할(Roles):** 사전 구성된 역할 및 서비스 제공자가 작성한 역할입니다. 사전 구성된 역할은 서비스 제공자가 편집할 수 없습니다.
-	**조직 사용자(Organization Users):** 테넌트 조직 및 하위 조직의 사용자입니다.
-	**자산 저장소(Asset Repository):** RiskForesight를 사용하여 CSP 관리 구역 및 고객 구역 전체에서 현재 자산을 동기화할 수 있는 통합 지점입니다. 현재 버전의 RisForesight에서는 VMware vCloud Director 및 vCenter Server의 동기화를 지원합니다. VMware NSX Manager의 데이터 콜렉션도 지원합니다. 자산은 자산 저장소에서 수집합니다. 서비스 제공자가 vCenter에서 수집한 자산을 서비스 제공자의 테넌트 조직 및 하위 조직에 지정합니다. 자산은 하나의 조직에만 지정할 수 있습니다.
-	**원격 액세스(Remote Access):** 취약성 및 규제 준수 모니터링을 위해 스캔을 사용하고 시스템 이벤트 로그를 수집하도록 엔드 머신에 인증 정보를 제공합니다. 서비스 제공자는 고유 자산에 대해 원격 액세스만 사용으로 설정할 수 있습니다. 테넌트는 자산으로부터의 원격 액세스를 제어합니다.
-	**애플리케이션(Applications) 및 하위 애플리케이션(Subapplications):** 자산을 그룹화하는 논리적 방법입니다. 예제 애플리케이션: SAP, 예제 하위 애플리케이션: SAP 프론트 엔드, SAP 중간 계층, SAP 백엔드
-	**위치(Locations):** 자산은 위치, 클라우드 제공자 및 자산 저장소별로 고유하게 그룹화됩니다.
-	**환경(Environments):** 자산과 애플리케이션을 그룹화하는 방법입니다. 각 환경에는 위험 계수 1 - 10이 지정됩니다. 이 계수는 위험 점수 계산에 적용됩니다. 서비스 제공자가 환경을 정의합니다.
-	**태스크(Tasks):** RiskForesight에서 사용되어 다음을 수행합니다.
  -	자산 저장소를 RiskForesight와 주기적으로 동기화합니다.
  -	SCAP 취약성 및 규제 준수 스캔을 수행합니다.
  -	NSX 스캔을 사용하는 네트워크 플로우 및 기타 정보를 수집합니다.
  -	모니터링된 자산에서 실행되는 소프트웨어에 관한 정보를 수집합니다.
  -	자산의 syslog 및 시스템 이벤트를 수집합니다.
-	**태스크 유형(Task Types):** 다음 태스크가 지원됩니다.
  -	**VMware vCenter 스캔:** vCenter에서 자산을 수집합니다.
	- **VMware VCD 스캔:** VCD에서 자산을 수집합니다.
  -	**VMware NSX 스캔:** NSX Manager에서 네트워크 정보와 네트워크 플로우를 수집합니다.
  - **SCAP 스캔:** 이 스캔 유형은 규제 준수 및 사이버 위험이 있는지 확인하기 위해 워크로드를 스캔하는 데 사용합니다. 이 스캔은 SCAP(Security Content Automation Protocol)를 기반으로 합니다. 향후 릴리스에서는 OVAL 형식으로 사용자 정의 컨텐츠를 지원할 계획입니다.
  - **소프트웨어 스캔:** 이 스캔에서는 관리 중인 대상 워크로드에 설치된 소프트웨어 인벤토리를 수집합니다. 그러면 UI 맨 위 막대에 있는 검색 옵션을 통해 이 인벤토리를 검색할 수 있습니다.
  - **LogExtract:** 이 스캔에서는 Windows와 Linux 워크로드로부터의 로그 콜렉션을 지원합니다. 이 로그 콜렉션은 사후조사용으로 사용하며 유용한 정보를 생성하기 위해 기계 학습을 통해 수집합니다.
  - **AMQP 태스크:** 이 AMQP 태스크는 실시간 동기화를 사용하도록 VCD에서 라이브 이벤트를 수집하는 데 사용합니다. RiskForesight에서는 자산 추가, 삭제 및 업데이트 이벤트를 이용하고 해당 이벤트에 관한 조치를 수행합니다. 예를 들어 새 자산을 추가하고 RiskForesight에서 AMQP를 통해 해당 알림을 받는 경우 즉시 데이터베이스를 업데이트하고 규제 준수 및 사이버 위험 스캔을 시작합니다.
  - **VMware 인프라 스캔:** 이 스캔에서는 VMware 자산의 인프라 스캔을 수행합니다.
  -	**VMware 취약성 스캔:** 이 스캔에서는 VMware 자산의 취약성 스캔을 수행합니다.
-	**규제 준수 제도(Compliance Regime):** 라이센스를 통해 사용 가능합니다. NIST, NESA, PCI, ISO, HIPAA, GDPR, Custom, FFIEC, FedRAMP Low, FedRAMP Moderate, FedRAMP High.
-	**정책 관리자(Policy Manager):** 정책 관리자에서는 기계 학습 출력을 기반으로 조직의 정책 작성 기능을 제공합니다. Caveonix에서는 기본적으로 조직당 세 가지 유형의 기계 학습 작업을 제공합니다. 해당 작업은 편집할 수 없으며 추가 작업은 아직 지원되지 않습니다. 현재 지원되는 기계 학습 작업의 유형은 다음과 같습니다.
  -	Caveo 로그
  -	Caveo 네트워크
  -	Caveo 스캔
-	**이상 항목(Anomaly):** 데이터에서 발견한 이상 항목을 기반으로 사용자 정의 조건에 따라 조치를 취하도록 정책을 구성할 수 있습니다. 작업 유형을 선택하고 이상 항목 점수의 부울 조건을 구성하며 조건이 참인 경우 조치를 정의할 수 있습니다. 예를 들어 다음과 같습니다.
```
작업: "Caveo 로그" 이상 항목 점수가 > 90이면 격리하도록 자산에 표시히고 슬랙 채널에 알림을 보냅니다.`
작업: "Caveo 네트워크" 이상 항목 점수가 > 95이면 자산을 격리하고 이메일 알림을 보내며 UI 알림도 보냅니다.
```

## 관련 링크
{: #caveonix-terminology-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)

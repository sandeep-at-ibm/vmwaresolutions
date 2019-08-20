---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-23"

keywords: Mission Critical VMware, request Mission Critical, tech specs Mission Critical

subcollection: vmware-solutions


---

# Mission Critical VMware on IBM Cloud
{: #mcv_overview}

Mission Critical VMware on {{site.data.keyword.cloud}}는 다중 구역 클라우드 아키텍처를 제공하여 엔터프라이즈에서 클라우드 애플리케이션에 대한 가동 중단 시간이 발생하지 않도록 지원하고 클라우드 지역 내에서 장애 복구를 자동화합니다.

이 클라우드 아키텍처를 사용하면, 고객들은 대부분의 VMware 클라이언트가 온프레미스 환경 또는 경쟁 클라우드 플랫폼에서 달성할 수 있는 것보다 더 높은 가용성 및 장애 복구 성공률을 달성할 수 있습니다.

이 아키텍처는 99.99%의 목표 집계 가용성으로 비클라우드 고유 애플리케이션을 포함한 기존의 미션 크리티컬, 레거시 워크로드를 지원합니다. {{site.data.keyword.cloud_notm}} 다중 구역 지역(MZR)은 사이트 가동 중단이 발생하는 경우에도 미션 크리티컬 워크로드를 온라인 상태로 유지하도록 설계되었습니다. 장애가 발생한 사이트의 워크로드는 거의 실시간으로 자동으로 다시 시작되며 인접 사이트의 워크로드는 사용 가능한 온라인 상태로 유지됩니다.

이 아키텍처에는 클라우드 기반 애플리케이션의 모니터링 및 문제점 해결을 위해 구축된 네트워크, 스토리지, 복원 및 기타 도구를 포함하여 다양한 엔터프라이즈 서비스가 포함됩니다. 또한 서비스를 폭넓게 사용할 수 있도록 {{site.data.keyword.cloud_notm}}에 구축된 IBM Services Platform with Watson과 이 아키텍처를 통합할 수 있습니다. 클라이언트는 플랫폼의 코그너티브 기능을 사용하여 지속적인 운영을 유지하는 데 도움이 되도록 새로운 비즈니스 인사이트를 위해 보다 효과적으로 데이터를 마이닝할 수 있습니다.

## Mission Critical VMware on IBM Cloud의 기술 스펙
{: #mcv_overview-specs}

Mission Critical VMware on {{site.data.keyword.cloud_notm}} 아키텍처는 고객 워크로드에 대한 자동화된 장애 복구 기능을 제공하는 엔드-투-엔드 참조 아키텍처입니다. 이 제품은 다음 컴포넌트를 포함하는 IBM 관리 서비스와 함께 {{site.data.keyword.cloud_notm}} 다중 구역 지역(MZR)을 사용합니다.

* 컴퓨팅 아키텍처(VMware vSphere)
* 네트워크 아키텍처(현재는 NSX-V)
* 스토리지 아키텍처(VMware vSAN)
* 서비스 사용이 가능하도록 IBM Services Platform with Watson과 통합
* 모니터링, 문제점 해결, 성능 및 용량 관리를 위한 도구:
  * vRealize Suite 패턴(오퍼레이션, 로그 인사이트 및 네트워크 인사이트)
  * Active Directory 패턴
  * 자동 티켓팅, 경보 작성 및 이벤트 보강을 위한 Netcool/Bluecare와의 통합
  * 복원 패턴(백업 및 복구)

Mission Critical VMware on {{site.data.keyword.cloud_notm}}는 다음 지역에서 사용할 수 있습니다.
* 미국: 북미 남부 - 댈러스에 있는 모든 {{site.data.keyword.cloud_notm}} 데이터 센터, 북미 동부: 워싱턴 DC에 있는 모든 {{site.data.keyword.cloud_notm}} 데이터 센터
* 유럽: 프랑크푸르트 및 런던에 있는 모든 {{site.data.keyword.cloud_notm}} 데이터 센터
* 아시아 태평양: 시드니 및 도쿄에 있는 모든 {{site.data.keyword.cloud_notm}} 데이터 센터

### 기본 인프라 아키텍처 스펙
{: #mcv_overview-base-specs}

기본 인프라에는 다음과 같은 스펙이 포함되어 있습니다.
* 각 사이트에 자체 전용 에지 및 관리 클러스터 포함
* 리소스 클러스터는 vSphere + vSAN 확장 클러스터임
* 감시 사이트에 감시 ESXi 호스트 포함
* 단일 vCenter 및 NSX Manager 아키텍처
* L3 네트워크 아키텍처에서 vCenter High Availability(HA)를 사용하는 PSC(Platform Services Controller)가 임베디드 vCenter Server Appliance
* NSX Manager 복구는 백업 파일을 동기화하는 Hot/Standby 방법 사용

### 도구 및 기술 아키텍처 스펙
{: #mcv_overview-tooling-specs}

도구 및 기술 아키텍처에는 다음과 같은 스펙이 포함되어 있습니다.
* 사용되는 VMware 제품(예: NSX, vSAN 및 vSphere)에 특정한 운영 및 관리 기능을 제공하는 vRealize Operations, vRealize Log Insight 및 vRealize Network Insight
* 우수 사례 및 보안 정책에 대해 배치의 유효성 검증을 위한 IBM Software Defined Environment Automation Tool Health Check(SAT HC)
* 지역 {{site.data.keyword.cloud_notm}} 사이트 외부에 대한 선택적 DR(Disaster Recovery)
* 인터넷 액세스를 안전하게 보호하고 온프레미스 네트워크와 활성-활성 네트워크의 통합을 용이하게 하는 Fortigate Security Appliance 또는 유사 서비스

### vSphere + vSAN 확장 클러스터 아키텍처 스펙
{: #mcv_overview-stretched-cluster-specs}

vSphere + vSAN 확장 클러스터 아키텍처에는 다음과 같은 스펙이 포함되어 있습니다.
* 클러스터는 두 개 사이트에 걸쳐 있는 스토리지 및 컴퓨팅 기능을 제공하여 향상된 가용성을 제공합니다.
* 가상 머신(VM)의 쓰기 요청은 두 개 사이트에 동시에 작성되며 사이트 간 네트워크 지연이 발생합니다.
* VM의 읽기 요청은 VM이 있는 실제 위치에 로컬로 실행되므로 추가 대기 시간은 발생하지 않습니다.
* 감시 사이트 및 감시 호스트는 분할된 브레인/쿼럼 역할을 합니다.
* vSAN 기본 암호화(나머지 암호화에 대해)를 이 아키텍처와 결합하여 사용할 수 있습니다.

### 네트워크 아키텍처 스펙
{: #mcv_overview-network-specs}

네트워크 아키텍처에는 다음과 같은 스펙이 포함되어 있습니다.
* Edge/DLR/VXLAN을 BGP 메트릭 기반 라우팅과 결합하여 자동화된 장애 복구로 활성-활성 사이트 디자인을 쉽게 사용할 수 있습니다.
* 각 사이트에는 자체 Edges/DLR 및 VXLAN 세트에 대한 개념이 포함되어 있습니다.
* 일반적인 환경에서 DLR-A에 연결된 VM(예: VM-A)은 {{site.data.keyword.cloud_notm}} 가용성 구역 #1에 있으며 트래픽 방향은 로컬로 유입 및 유출 둘 다 해당됩니다.
* VM-A에 대한 vMotion 활동 중에 트래픽은 {{site.data.keyword.cloud_notm}} 가용성 구역 #1을 통해 계속 유입 및 유출됩니다.
* 사이트 또는 에지 장애가 발생하는 경우 트래픽은 남아 있는 사용 가능한 사이트 외부로 라우팅됩니다.

## Mission Critical VMware on IBM Cloud 요청 프로시저
{: #mcv_overview-proc}

1. {{site.data.keyword.vmwaresolutions_full}} 콘솔의 왼쪽 탐색 분할창에서 **시작하기**를 클릭하십시오.
2. 페이지를 아래로 스크롤하여 **VMware 관리 서비스**에서 **Mission Critical VMware on IBM Cloud** 카드를 클릭하십시오.
3. Mission Critical VMware on {{site.data.keyword.cloud_notm}} 페이지에서 **Mission Critical VMware에 대해 문의하기** 상자에 있는 **컨설팅 요청**을 클릭하십시오.
4. IBM Services Expert Hub 페이지에서 **상담 스케줄링**을 클릭하여 서비스 전문가와 30분을 예약하십시오.

  {{site.data.keyword.cloud_notm}} 담당자가 사용자에게 필요한 솔루션에 대한 도움을 드리기 위해 사용자의 {{site.data.keyword.cloud_notm}} 연락처 정보를 사용하여 연락을 드립니다.

## 관련 링크
{: #mcv_overview-related}

* [IMI의 관리 서비스](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_imi)
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

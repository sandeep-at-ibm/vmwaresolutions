---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 용량 스케일링

초기 배치 이후에 사용자는 {{site.data.keyword.vmwaresolutions_full}} 콘솔에서 컴퓨팅 용량을 확장할 수 있습니다. 이 디자인에서는 다음의 용량 확장 경로를 지원합니다.
* 개별 vCenter Server가 관리하는 새 사이트 추가
* 새 클러스터 추가
* 기존 클러스터에 새 호스트 추가

## 더 많은 사이트 추가

{{site.data.keyword.vmwaresolutions_short}}는 해당 인프라를 맨 처음부터 빌드하는 데 걸리는 시간보다 빠르게 다양한 지역 간 유스 케이스가 배치되고 작동되도록 하기 위해 {{site.data.keyword.cloud_notm}} 전세계 데이터 센터 존재와 통합 네트워크 백본을 최대한 활용할 수 있습니다.

이 디자인에서 다중 사이트 배치의 정의는 다음으로 구성되어 있습니다.
* 제공될 새 DNS/AD 루트 도메인, 하위 도메인, SSO 도메인 및 SSO 사이트 이름을 포함하여 초기 또는 기본 VMware 배치.
* 다음 구성을 필요로 하는 기본 사이트 SSO 도메인으로 프로비저닝되는 단일 또는 다중 보조 사이트:
   * 새 SSO 사이트 이름
   * 기본 도메인의 루트에 결합된 새 DNS 사이트/하위 도메인
   * 보조 및 기본 사이트 AD VM 간의 DNS 및 AD 복제 설정
   * 기본 사이트 PSC와 동기화하도록 구성되고 배치된 PSC
   * 기본 사이트 vCenter에 대한 향상된 연결 모드로 vCenter 설정

또한 보조 사이트의 NSX 관리자는 기본 사이트에서 NSX 관리자의 보조 NSX 관리자로 설정될 수 있습니다.

## 새 클러스터 추가

{{site.data.keyword.vmwaresolutions_short}} 콘솔에서 새 클러스터를 작성하고 새 클러스터에 자동으로 추가되는 새 호스트를 주문하여 컴퓨팅 용량을 확장할 수도 있습니다.

이 방법을 사용하면 다음과 같은 작업을 완료할 수 있습니다.
* 환경에서 추가로 개별 클러스터를 작성합니다.
* 관리 워크로드를 애플리케이션 워크로드와 물리적 및 논리적으로 분리합니다.
* 기타 특성을 기반으로 워크로드를 분리합니다(예: Microsoft SQL 데이터베이스 클러스터).
* 고가용성 토폴로지에 애플리케이션을 배치합니다.

초기 클러스터가 관리 전용 클러스터로 변환되는 경우 기존 워크로드를 마이그레이션하는 데에는 사용자가 취할 수동 단계가 포함됩니다. 여기에는 새 클러스터로 데이터 저장소의 재연결 또는 스토리지 마이그레이션이 포함될 수 있습니다. 새 클러스터가 다른 {{site.data.keyword.cloud_notm}} 팟(Pod)에 상주하거나 이에 다른 VLAN ID가 지정된 경우에는 워크로드의 IP 주소가 변경될 수 있습니다.
{:note}

## 기존 클러스터에 ESXi 호스트 추가

{{site.data.keyword.vmwaresolutions_short}} 콘솔에서 호스트를 주문하여 기존 클러스터의 용량을 확장할 수 있습니다.  새 호스트는 자동으로 클러스터에 추가됩니다. 참고로, 예약 요구사항에 따라 클러스터에 대한 HA 예약 정책을 조정해야 할 수 있습니다.

### 관련 링크

* [솔루션 개요](/docs/services/vmwaresolutions/archiref/solution/solution_overview.html)
* [디자인 개요](/docs/services/vmwaresolutions/archiref/solution/design_overview.html)
* [컴포넌트 백업](/docs/services/vmwaresolutions/archiref/solution/solution_backingup.html)

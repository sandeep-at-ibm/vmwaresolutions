---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 인프라 관리 디자인
{: #design_infrastructuremgmt}

인프라 관리는 VMware 인프라를 관리하는 컴포넌트를 의미합니다. 이 디자인은 단일 외부 PSC(Platform Services Controller) 인스턴스와 단일 vCenter Server 인스턴스를 사용합니다.
* vCenter Server는 vSphere 환경 관리를 위한 중앙 집중식 플랫폼이며 이 솔루션의 기반 컴포넌트 중 하나입니다.
* 이 솔루션에서 PSC를 사용하여 VMware vCenter 싱글 사인온, 라이센스 서비스, 검색 서비스 및 VMware 인증 기관을 포함하는 인프라 서비스 세트를 제공할 수 있습니다.

PSC 인스턴스와 vCenter Server 인스턴스는 개별 가상 머신(VM)입니다.

## PSC 디자인
{: #design_infrastructuremgmt-psc}

이 디자인은 VM과 연관된 사설 VLAN에서 포터블 서브넷의 가상 어플라이언스로서 단일 외부 PSC를 배치합니다. 이의 기본 게이트웨이는 백엔드 고객 라우터(BCR)로 설정됩니다. 가상 어플라이언스는 다음 표의 스펙으로 구성되어 있습니다.

이러한 값은 배치 시에 설정되며 변경할 수 없습니다.
{:note}

표 1. Platform Services Controller 스펙

| 속성                    | 스펙                  |
|------------------------------|--------------------------------|
|Platform Services Controller | 가상 어플라이언스              |
| vCPU 수              | 2                              |
|메모리                       | 4GB                           |
| 디스크                         | 로컬 VMFS 데이터 저장소에서 114GB |
| 디스크 유형                    | 씬 프로비저닝됨               |

기본 인스턴스에 있는 PSC에는 `vsphere.local`의 기본 SSO 도메인이 지정됩니다.

## vCenter Server 디자인
{: #design_infrastructuremgmt-vcenter}

또한 vCenter Server는 가상 어플라이언스로서 배치됩니다. 또한 vCenter Server는 관리 VM과 연관된 사설 VLAN의 포터블 서브넷에 설치됩니다. 이의 기본 게이트웨이는 해당 특정 서브넷에 대한 BCR에서 지정된 IP 주소로 설정됩니다. 가상 어플라이언스는 다음 표의 스펙으로 구성되어 있습니다.

표 2. vCenter Server Appliance 스펙

| 속성                    | 스펙                       |
|------------------------------|-------------------------------------|
|vCenter Server               | 가상 어플라이언스                   |
| 어플라이언스 설치 크기  | 중간(최대 400개 호스트, 4,000개 VM) |
|Platform Services Controller | 외부                            |
| vCPU 수              |8                                   |
|메모리                       | 24GB                               |
| 디스크                         | 로컬 데이터 저장소에서 400GB           |
| 디스크 유형                    | 씬 프로비저닝됨                    |

### vCenter Server 데이터베이스
{: #design_infrastructuremgmt-vcenter-db}

vCenter Server 구성에서는 어플라이언스에 포함된 로컬, 임베디드 PostgreSQL 데이터베이스를 사용합니다. 임베디드 데이터베이스는 외부 데이터베이스와 라이센싱의 종속성을 제거하는 데 사용됩니다.

### vCenter Server 클러스터 스펙
{: #design_infrastructuremgmt-vcenter-cluster}

이 디자인을 사용하면 솔루션을 통해 프로비저닝되는 vSphere ESXi 호스트를 클러스터링할 수 있습니다. 그러나 클러스터가 작성되기 전에, 데이터 센터 내의 팟(Pod)은 물론 vSphere ESXi 호스트의 위치를 나타내는 데이터 센터 오브젝트가 작성됩니다. 클러스터는 데이터 센터 오브젝트가 작성된 후에 작성됩니다. 클러스터는 VMware vSphere HA(High Availability) 및 VMware vSphere DRS(Distributed Resource Scheduler)가 사용되어 배치됩니다.

### vSphere Distributed Resource Scheduler
{: #design_infrastructuremgmt-vsphere-drs}

이 디자인에서는 초기 클러스터의 vSphere DRS(Distributed Resource Scheduling)를 사용하여 VM을 배치하며, 추가 클러스터의 DRS을 사용하여 VM을 동적으로 마이그레이션함으로써 밸런스가 유지된 클러스터를 구성합니다. 자동화 레벨은 vSphere에서 초기 배치 및 마이그레이션 권장사항을 실행할 수 있도록 완전히 자동화되도록 설정됩니다. 또한 vCenter가 우선순위 1, 2, 3 권장사항을 적용하여 클러스터의 로드 밸런싱에서 최소한의 적절한 개선이 이루어질 수 있도록, 마이그레이션 임계값이 적절하게 설정됩니다.

**Distributed Power Management** 기능을 통한 전력 관리는 이 디자인에서는 사용되지 않습니다.
{:note}

### vSphere High Availability
{: #design_infrastructuremgmt-vsphere-ha}

이 디자인은 초기 클러스터와 추가 클러스터에서 vSphere High Availability(HA)를 사용하여 컴퓨팅 장애를 감지하고 클러스터 내에서 실행되는 VM을 복구합니다. 이 디자인의 vSphere HA 기능은 클러스터에서 사용으로 설정된 **호스트 모니터링** 및 **허가 제어** 옵션을 모두 사용하여 구성됩니다. 또한 초기 클러스터는 1개 노드의 리소스를 허가 제어 정책을 위한 여유 용량으로서 예약합니다.

클러스터가 나중에 확장되거나 축소될 때 사용자는 허가 제어 정책을 조정해야 합니다.
{:note}

기본적으로, **VM 재시작 우선순위** 옵션은 "중간"으로 설정되어 있으며 **호스트 격리 응답** 옵션은 사용되지 않습니다. 또한 **VM 모니터링**은 사용되지 않으며 **데이터 저장소 하트비트** 기능은 클러스터 데이터 저장소를 포함하도록 구성되어 있습니다. 이 접근 방법에서는 NAS 데이터 저장소를 사용합니다(존재하는 경우).

## 자동화
{: #design_infrastructuremgmt-automation}

이러한 솔루션의 초석은 자동화입니다. 자동화는 다음과 같은 이점을 제공합니다.
* 배치의 복잡도를 줄입니다.
* 배치 시간을 획기적으로 줄입니다.
* VMware 인스턴스가 일관된 방식으로 배치되도록 보장합니다.

{{site.data.keyword.IBM}} CloudBuilder, IBM CloudDriver 및 SDDC Manager VM은 함께 작동하여 새 VMware 인스턴스를 시작하고 라이프사이클 관리 기능을 수행합니다.

### IBM CloudBuilder 및 IBM CloudDriver
{: #design_infrastructuremgmt-cloud-builder-driver}

IBM CloudBuilder 및 IBM CloudDriver VSI(Virtual Server Instance)는 IBM이 개발한 컴포넌트이며, 사용자는 이에 액세스할 수 없습니다.
* IBM CloudBuilder는 프로비저닝된 베어메탈 ESXi 호스트 내에서 솔루션 컴포넌트의 배치, 구성 및 유효성 검증을 부트스트랩하는 임시 {{site.data.keyword.cloud_notm}} VSI(Virtual Server Instance)입니다.
* IBM CloudDriver VSI는 인스턴스 작성을 위해 배치된 후에 추가 노드, 클러스터 또는 서비스 배치 등의 오퍼레이션을 위한 최신 {{site.data.keyword.cloud_notm}} for VMware 코드를 사용하여 필요에 따라 주기적으로 배치됩니다. IBM CloudDriver는 인스턴스 관리 용도로 배타적으로 배치된 VMware NSX Edge Services Gateway를 통해 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 통신하며 인스턴스를 유지보수하기 위한 에이전트의 역할을 수행합니다. IBM CloudDriver는 지속적인 조치(예: 클러스터에 새 베어메탈 호스트 추가 및 인스턴스에 추가 기능 서비스 배치)를 담당합니다. Cloud Foundation 인스턴스의 경우, IBM CloudDriver는 VMware SDDC Manager VM과 통신하여 호스트 추가 및 패치 등의 기능을 수행합니다.

다음 섹션에서 설명하는 VM을 사용자가 삭제하거나 손상시킬 수 있습니다. VM이 제거되거나 종료되거나 작동이 불가능해지는 경우, {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 다음의 Cloud Foundation 또는 vCenter Server 오퍼레이션이 인터럽트됩니다.
* 인스턴스 또는 호스트 상태 보기
* 클러스터 추가 또는 제거
* ESXi 호스트 추가 또는 제거
* 서비스 추가 또는 제거
* 패치

### SDDC Manager
{: #design_infrastructuremgmt-sddc-manager}

Cloud Foundation 인스턴스의 경우, SDDC Manager VM은 VMware에 의해 개발되고 유지보수되는 컴포넌트입니다. 이는 전체 라이프사이클 중에 인스턴스의 일부로서 유지됩니다. 이는 인스턴스의 다음 라이프사이클 기능을 담당합니다.
* VMware 컴포넌트 관리: IP 주소 할당 및 호스트 이름 분석을 포함하여 vCenter Server, PSC(Platform Services Controller), vSAN 및 NSX.
* NSX VTEP, vSAN 및 리소스 풀 등의 영향을 받는 서비스를 포함하여 클러스터 내에서 ESXi 호스트의 확장 및 축소.

vCenter Server 인스턴스의 경우, SDDC Manager가 없으므로 이러한 활동은 IBM CloudDriver에 의해 수행됩니다.

### 자동화 플로우
{: #design_infrastructuremgmt-auto-flow}

다음의 프로시저에서는 {{site.data.keyword.vmwaresolutions_short}} 콘솔을 통해 VMware 인스턴스의 순서가 지정될 때 이벤트의 순서를 설명합니다.
1.  {{site.data.keyword.cloud_notm}}에서 네트워킹에 대한 VLAN 및 서브넷의 순서 지정.
2.  vSphere Hypervisor가 설치된 {{site.data.keyword.baremetal_short}}의 순서 지정.
3.  해당되는 경우, Active Directory 도메인 제어기로서 서비스하기 위한 Microsoft Windows VSI(Virtual Server Instance)의 순서 지정.
4.  네트워킹 및 배치된 하드웨어의 유효성 검증.
5.  해당되는 경우, 단일 노드 vSAN의 초기 구성.
6.  해당되는 경우, Active Directory 도메인 제어기 역할을 수행하기 위한 2개의 Microsoft Windows 가상 머신의 배치 및 구성.
7.  vCenter, PSC 및 NSX의 배치 및 구성.
8.  나머지 ESXi 노드의 클러스터링, vSAN의 확장(해당되는 경우) 및 NSX 컴포넌트의 구성(VTEP).
9.  VMware Cloud Foundation SDDC Manager VM(해당되는 경우) 및 IBM CloudDriver VSI 배치.
10.  환경의 설치와 구성에 대한 유효성 검증.
11. CloudBuilder VSI의 제거.
12. 백업 서버와 스토리지 등의 선택적 서비스의 배치.

## 관련 링크
{: #design_infrastructuremgmt-related}

* [실제 인프라 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_physicalinfrastructure)
* [가상 인프라 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_virtualinfrastructure)
* [공통 서비스 디자인](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-design_commonservice)

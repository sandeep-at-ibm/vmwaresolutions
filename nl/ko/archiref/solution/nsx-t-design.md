---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

subcollection: vmware-solutions


---

# VMware NSX-T 디자인
{: #nsx-t-design}

NSX-V(NSX on vSphere)와는 달리 VMware NSX-T는 이기종 엔드포인트와 기술 스택이 있는 애플리케이션 프레임워크와 아키텍처를 다루도록 설계되었습니다. 이러한 환경에는 vSphere 외에도 다른 하이퍼바이저, KVM, 컨테이너 및 베어메탈이 포함될 수 있습니다. VMware NSX는 vSphere만이 아닌 플랫폼에서 소프트웨어 정의 네트워크 및 보안 인프라를 확장하도록 설계되었습니다. vSphere 없이 NSX-T 컴포넌트를 배치할 수 있으나 이 디자인은 vCenter Server vSphere 자동화 배치 내에서 주로 NSX-T 및 해당 통합에 중점을 둡니다.

방화벽 정책 내의 Guest Introspection 및 고급 넷 플로우 추적을 포함하여 NSX-T 내에 방화벽 정책과 같은 다수의 고급 기능이 있습니다. 이러한 기능에 대한 설명은 이 문서에서 다루지 않습니다. NSX-T는 VMware 문서를 참조하십시오. 이 디자인에서 NSX-T 관리 인프라는 NSX-V 대신 초기 vCenter Server 클러스터 배치 중에 배치됩니다.

## NSX-T 대 NSX-V
{: #nsx-t-design-nsx-t-nsx-v}

vSphere 원시 NSX(NSX-V)의 경우 다음과 같이 잘 알려진 NSX-T 오브젝트(NSX-V와 유사한 기능이 포함됨)를 검토하십시오. vSphere 환경 내의 제한사항 및 차이점도 논의됩니다. 다음은 대응되는 T와 V 간에 일반적으로 사용되는 기능을 표시한 표입니다.

표 1. NSX-V 대 NSX-T 용어

NSX-V 또는 vSphere 원시 |NSX-T
--|:---|:--
**가상 분배 스위치** | 네트워크 가상 분배 스위치(N-VDS)
**NSX 전송 구역** | 전송 구역(오버레이 또는 VLAN 지원)
**포트 그룹(vDS)** | 논리 스위치
**VXLAN(L2 캡슐화)** | GENEVE(L2 캡슐화)
**에지 게이트웨이** | T0 게이트웨이(v2.4부터 변경됨)
**Distributed Logical Router** | T1 게이트웨이(v2.4부터 변경됨)
**ESXi 서버(vTEP)** | 전송 노드(ESXi, KVM, 베어메탈 T0 게이트웨이)

NSX-T에 대한 이 디자인을 구현하기 위해 이해하고 있어야 할 NSX-V 기능에는 해당되지 않는 주요 NSX-T 개념이 있습니다.

다음과 같습니다.
- 에지 클러스터는 NSX-T 가상 패브릭에 참여하는 하나 이상의 VM 또는 실제 머신입니다. 이는 오버레이 네트워크 전송 구역 및 VLAN 지원 전송 구역에 대한 엔드포인트입니다. 에지 클러스터는 다중 T-0 게이트웨이 인스턴스를 지원할 수 있습니다.
- T-0 게이트웨이는 VM이 아닌 가상 라우터 인스턴스입니다. 다중 T-0 게이트웨이 인스턴스는 에지 클러스터(각 자체 라우팅 테이블 및 기능 포함) 내에서 실행될 수 있습니다. 이는 T-0 라우터 인스턴스를 작성하기 전에 에지 클러스터가 존재해야 함을 의미합니다.
- 전송 구역은 여러 플랫폼 및 다중 vSphere vCenter 인스턴스에서 엔드포인트를 확장할 수 있습니다. 교차 vCenter 연결 NSX가 필요하지 않습니다. 전송 구역은 특정 엔드포인트에서 제외될 수 있습니다. N-VDS는 전송 구역과 직접 연관되고 전송 구역이 작성될 때 작성됩니다.
- 업링크 장애 복구 순서는 "업링크 프로파일"로서 프로파일에 작성되고 VLAN 기반의 특정 논리 스위치에 적용됨에 따라 특정 논리 스위치와는 관계 없이 작성됩니다. 동일한 VLAN에 대해 장애 복구 순서 또는 실제 업링크의 로드 밸런싱이 달라야 할 수 있으므로, 특정 VLAN에 대한 업링크 프로파일에는 장애 복구 순서 및 로드 밸런싱이 다른 "팀"에 대한 항목이 포함될 수 있습니다. 업링크 프로파일을 논리 스위치에 지정하는 경우 특정 팀 프로파일이 선택됩니다.

- NSX-T 2.4부터 관리자 VM과 제어기 VM 기능이 결합됩니다. 이로 인해 세 개의 컨트롤러 관리자 VM이 배치됩니다. 동일한 서브넷에 있으면 내부 네트워크 로드 밸런서를 사용합니다. 다른 서브넷에 있는 경우 외부 로드 밸런서가 필요합니다.

## 리소스 요구사항
{: #nsx-t-design-resource-req}

이 디자인에서 NSX-T Manager-제어기가 초기 클러스터에 배치됩니다. 또한 각 제어기 관리자에는 관리 컴포넌트용으로 지정되며 섹션 0에서 논의된 DNS 및 NTP 서버로 구성되어 있는 사설 포터블 주소 블록의 VLAN 지원 IP 주소가 지정됩니다. NSX Manager 설치에 대한 요약은 다음 표에 표시되어 있습니다.

표 2. NSX-T Manager-제어기 스펙

 속성 | 스펙
--|--
**NSX Manager/제어기** | 3개의 가상 어플라이언스
**vCPU 수** | 4
**메모리** | 16GB
**디스크** |60GB
**디스크 유형** | 씬 프로비저닝됨
**네트워크 사설 A** | 사설 A

다음 그림에서는 이 아키텍처의 기타 컴포넌트와 연관된 NSX Manager-제어기의 배치를 보여줍니다.

![NSX-T Manager 네트워크 개요](../../images/vcsv4radiagrams-ra-vcs-nsx-overview.svg "NSX-T Manager 네트워크 개요")

## 배치 고려사항
{: #nsx-t-design-deployment}

NSX-T on vSphere를 사용하여 N-VDS에 호스트 내의 실제 어댑터가 지정되어야 합니다. N-VDS는 NSX-T Manager 내에서만 구성될 수 있습니다. 그러므로 이는 중복성이 유지보수될 경우 NSX-T 컴포넌트와 연관된 오버레이 네트워크 컴포넌트를 모두 수용하는 클러스터에는 고유한 논리 스위치 또는 vDS 지정에 사용 가능한 실제 어댑터가 없음을 의미합니다.

이러한 이유로 NSX-T 설치 및 구성 중에 하나의 어댑터에 있는 하나의 실제 NIC 포트는 로컬 vSphere vSwitch 또는 가상 분배 스위치(vDS)에 지정된 상태로 유지되어야 합니다. NSX-T 배치 이후에 ESX 커널 포트는 N-VDS로 마이그레이션되고 로컬 vSwitch 또는 VDS를 해제해야 합니다. 커널 포트가 제거된 후 남아 있는 실제 NIC 포트는 N-VDS의 중복성을 달성하는 N-VDS 업링크로 지정될 수 있습니다.

초기 배치 이후 {{site.data.keyword.cloud_notm}} 자동화는 초기 클러스터 내에 3개의 NSX-T Manager/제어기 가상 어플라이언스를 배치합니다. 제어기에는 관리 컴포넌트용으로 지정된 사설 A 포터블 서브넷의 VLAN 지원 IP 주소가 지정됩니다. 또한 VM–VM 반유사성(anti–affinity) 규칙은 제어기가 클러스터의 호스트 간에 분리되는 방식으로 작성됩니다.

Manager/제어기에 대한 고가용성을 보장할 수 있도록 최소한 3개의 노드로 초기 클러스터를 배치해야 합니다. Manager/제어기에 추가하여, {{site.data.keyword.cloud_notm}} 자동화는 NSX-T 전송 노드로서 배치된 vSphere 호스트를 준비합니다. 제어기에는 VLAN 및 서브넷 요약으로부터 파생되는 NSX IP 풀 범위로 지정된 사설 A 포터블 IP 주소에서 VLAN 지원 IP 주소가 지정됩니다. 전송 노드 트래픽은 태그가 지정되지 않은 VLAN에 상주하며 사설 NSX-T 가상 분배 스위치(N-VDS)에 지정됩니다.

NSX-T 토폴로지가 배치되도록 선택한 고객에 따라 NSX-T Edge 클러스터는 VM 쌍으로 배치되거나 베어메탈 클러스터 노드에 배치되는 소프트웨어로 배치됩니다. 클러스터 쌍이 가상인지 아니면 실제인지에 따라 업링크는 {{site.data.keyword.cloud_notm}} 공용 및 사설 네트워크를 위해 N-VDS 스위치로 구성됩니다.

다음 표는 중형 환경에 대한 요구사항을 요약합니다.

표 3. NSX-T 컴포넌트 스펙

리소스 | 관리자 제어기 x3 | 에지 클러스터 x2 | 베어메탈 에지
-----------|:---------|:-------|:---------
**중형** | 가상 어플라이언스 | 가상 어플라이언스 | 실제 서버
**vCPU 수** | 4 | 4 |8
**메모리** | 16GB | 8GB |32GB
**디스크** | 120GB VSAN/관리 NFS | 120GB VSAN/관리 NFS |200GB
**디스크 유형** | 씬 프로비저닝됨 | 씬 프로비저닝됨 |실제
**네트워크** | 사설 A | 사설 A | 사설 A

## 전송 구역 및 N-VDS
{: #nsx-t-design-transport-zones}

전송 구역은 특정 네트워크 사용에 참여할 수 있는 호스트와 VM을 지정합니다. 전송 구역은 논리 스위치를 "볼" 수 있는 호스트를 제한하여 이를 수행할 수 있습니다. 이에 따라 VM은 논리 스위치에 연결될 수 있습니다. 전송 구역은 하나 이상의 호스트 클러스터를 확장할 수 있습니다. 이 디자인에는 다음과 같이 작성될 전송 구역이 필요합니다.

표 4. NSX-T 전송 구역 및 N-VDS

전송 구역 이름 | VLAN/VXLAN | N-VDS 이름 |업링크 팀 정책
--|:-------|:------|:-----
**Private-Overlay** |VXLAN | SDDC-Overlay | 기본값
**Public-VLAN** |VLAN | SDDC-Public | 기본값
**Private-VLAN** |VLAN | SDDC-Private | NFS,vSAN,iSCSI-A 및 B 기본값

## 전송 노드
{: #nsx-t-design-transport-nodes}

전송 노드는 가상 네트워크 패브릭에 참여하는 실제 서버 오브젝트 또는 VM을 정의합니다. 디자인을 이해하려면 다음 표를 검토하십시오.

표 5. NSX-T 전송 노드

전송 노드 유형 |N-VDS |업링크 프로파일 | IP 지정 |실제 NIC
--|:--------|:--------|:---
**ESXi** | SDDC-Private | SDDC-Private-uplink | IP 풀 | vmnic0, vmnic2
**에지 클러스터** | SDDC-Overlay | SDDC-Overlay-uplink | IP 풀 |해당사항 없음
**실제 에지** | SDDC-Private | SDDC-Private-uplink | IP 풀 | eth0, eth2

## 업링크 프로파일
{: #nsx-t-design-uplink-profiles}

업링크 프로파일은 하이퍼바이저 호스트에서 NSX-T 논리 스위치까지 또는 NSX 에지 노드에서 ToR(Top of Rack) 스위치까지의 링크에 대한 정책을 정의합니다.

표 6. NSX-T 업링크 프로파일

업링크 프로파일 이름 |VLAN | 포함된 팀 | MTU
--|:-----|:---|:---
**SDDC-Private-Uplink** | 기본값 | 기본값, 관리 |9000
**SDDC-Public-Uplink** | 기본값| 기본값 | 1500
**SDDC-Storage-Uplink** | 스토리지 VLAN | vSAN, iSCSI-A 및 B, NFS |9000

##  팀 구성
{: #nsx-t-design-teaming}

표 7. NSX-T NIC 포트 팀 스펙

팀 이름 | 장애 복구 또는 로드 밸런스 | 활성 NIC | 대기 NIC
--|:----|:---|:---
**기본값** | 로드 밸런스 소스 | 업링크 1, 2 |해당사항 없음
**관리** | 장애 복구| 업링크 1 | 업링크 2
**TEP** | 장애 복구| 업링크 1 | 업링크 1
**vSAN** | 장애 복구| 업링크 2 | 업링크 1
**iSCSI-A** | 장애 복구| 업링크 1 |해당사항 없음
**iSCSI-B** | 장애 복구| 업링크 2 |해당사항 없음
**NFS** | 로드 밸런스 소스 | 업링크 1, 2 | 업링크 1
**vMotion** | 장애 복구| 업링크 2 | 업링크 1

## VNI 풀
{: #nsx-t-design-vni-pools}

VNI(Virtual Network Identifiers)는 실제 네트워크에 대한 VLAN과 유사합니다. 이는 논리 스위치가 풀 또는 ID 범위에서 작성될 때 자동으로 작성됩니다. 이 디자인은 NSX-T로 배치되는 기본 VNI 풀을 사용합니다.

## 논리 스위치
{: #nsx-t-design-logical-switches}

NSX-T 논리 스위치는 기본 하드웨어에서 완전히 분리되는 가상 환경에서 기능, 브로드캐스트, 알 수 없는 유니캐스트, 멀티캐스트(BUM) 트래픽 전환을 재현합니다.

표 8. NSX-T 논리 스위치

논리 스위치 이름 |VLAN |전송 구역 |업링크 팀 정책
--|:---|:----|:---
**SDDC-LS-Mgmt** | 기본값 | Private-VLAN |관리
**SDDC-LS-NFS** | 기본값 | Private-VLAN |NFS
**SDDC-LS-vMotion** | 기본값 | Private-VLAN | vMotion
**SDDC-LS-VSAN** | 태그가 지정된 스토리지 VLAN | Private-VLAN |vSAN
**SDDC-LS-iSCSI-A** | 태그가 지정된 스토리지 VLAN | Private-VLAN| iSCSI-A
**SDDC-LS-iSCSi-B** | 태그가 지정된 스토리지 VLAN | Private-VLAN| iSCSi-B
**SDDC-LS-TEP** | 기본값 | Private-VLAN| TEP
**SDDC-LS-External** | 기본값 | Public-VLAN | 기본값

### 에지 클러스터
{: #nsx-t-design-edge-cluster}

이 디자인 내에서 단일 가상 에지 클러스터는 관리 및 고객 워크로드의 사용을 위해 프로비저닝됩니다. 가상 에지 클러스터는 T0 게이트웨이의 다중 인스턴스를 수용할 수 있습니다. 앞에서 설명한 대로, 다중 T0 에지 게이트웨이 인스턴스는 자체 라우팅 테이블을 포함하여 단일 에지 클러스터에서 인스턴스화될 수 있습니다. NSX-T Edge 클러스터의 기능 컴포넌트를 보여주는 다음 그림을 참조하십시오.

![T0 - T1 스케일의 NSX-T Edge 클러스터 예](../../images/vcsv4radiagrams-ra-nsx-t-edge-cluster-t0-to-t1-scale.svg "T0 - T1 스케일의 NSX-T Edge 클러스터 예")

![관리 T0 게이트웨이](../../images/vcsv4radiagrams-topology-0.svg "관리 T0 게이트웨이")

#### 티어 0 논리 게이트웨이
{: #nsx-t-design-tier-0}

NSX-T 티어 0 논리 라우터는 논리 네트워크와 실제 네트워크 간에 게이트웨이 서비스의 설정 및 해제를 제공합니다. 이 디자인의 경우 다중 T-0 게이트웨이는 관리, 추가 제품 및 토폴로지를 선택한 고객(선택사항)의 요구사항을 충족하도록 배치됩니다.

#### 티어 1 논리 게이트웨이
{: #nsx-t-design-tier-1}

NSX-T 티어 1 논리 게이트웨이에는 NSX-T 데이터 센터 논리 스위치에 연결할 다운링크 포트와 NSX-T 데이터 센터 티어 0 논리 라우터에만 연결할 업링크 포트만 있습니다. 구성되는 하이버파이저(가상 또는 실제 머신으로서가 아님)의 커널 레벨에서 실행됩니다. 이 디자인의 경우 하나 이상의 T-1 논리 게이트웨이는 토폴로지를 선택한 고객의 요구사항을 충족하도록 작성됩니다.

#### 티어 1 대 티어 0의 라우트 알림
{: #nsx-t-design-tier-1-tier-0}

다른 티어 1 논리 게이트웨이에 연결되는 논리 스위치에 연결된 VM 간의 계층 3 연결을 제공하려면 티어 0에 대한 티어 1 라우트 알림을 사용으로 설정해야 합니다. 티어 1 및 티어 0 논리 라우터 간의 라우팅 프로토콜 또는 정적 라우트를 구성할 필요가 없습니다. NSX-T는 라우트 알림을 사용으로 설정할 때 정적 라우트를 자동으로 작성합니다. 이 디자인의 경우 라우트 알림은 항상 T-1 게이트웨이가 작성된 IC4V 자동화에서 사용으로 설정되어야 합니다.

### 사전 구성된 토폴로지
{: #nsx-t-design-preconfig-topo}

T1 대 T0 게이트웨이 워크로드 - 가상 에지 클러스터

![NSX-T 배치 토폴로지 가상 T0 에지 게이트웨이](../../images/vcsv4radiagrams-topology-1.svg "NSX-T 배치 토폴로지 가상 T0 에지 게이트웨이")

IC4V 배치 토폴로지 1은 기본적으로 NSX-V DLR 및 에지 게이트웨이로 배치된 동일한 토폴로지입니다. NSX-T를 사용하면 T1과 T0 간의 동적 라우팅 프로토콜 구성이 없습니다. RFC-1891 IP 주소 공간은 워크로드 오버레이 네트워크와 전송 오버레이 네트워크에 사용됩니다. 고객 사설 및 공용 포터블 IP 공간은 고객 사용을 위해 지정됩니다. 고객이 지정한 {{site.data.keyword.cloud_notm}} 사설 및 공용 포터블 IP 공간은 고객 사용을 위해 T0에 지정됩니다.

이 디자인에는 vCenter Server 인스턴스가 사용 중지되고 삭제되는 경우 이 IP 범위를 삭제하지 않는 옵션이 있습니다.

T1 대 T0 게이트웨이에 대한 워크로드 - 실제 에지 클러스터:

![NSX-T 배치 토폴로지 실제 T0 에지 게이트웨이](../../images/vcsv4radiagrams-ra-vcs-nsx-overview.svg "NSX-T 배치 토폴로지 실제 T0 에지 게이트웨이")

배치된 토폴로지 2는 VM 기반 에지 클러스터를 Red Hat Server가 실행되는 베어메탈 서버 쌍으로 대체하는 예외와 유사합니다. 고객이 지정한 {{site.data.keyword.cloud_notm}} 사설 및 공용 포터블 IP 공간은 고객 사용을 위해 T0에 지정됩니다. 이 디자인에는 vCenter Server 인스턴스가 사용 중지되고 삭제되는 경우 이 IP 범위를 삭제하지 않는 옵션이 있습니다.

하드웨어 및 OS 스펙의 명세서에 대한 개별 문서 또는 링크를 참조하십시오.

ICP 대 T0 게이트웨이가 있는 워크로드 - 실제 에지 클러스터:

![ICP NSX-T 통합 및 가상 T0 에지 게이트웨이가 있는 NSX-T 배치 토폴로지](../../images/vcsv4radiagrams-topology-3.svg "ICP NSX-T 통합 및 가상 T0 에지 게이트웨이가 있는 NSX-T 배치 토폴로지")

배치 토폴로지 3에는 ICP 배치 내의 기본 네트워킹 스택인 Calico 대신 NSX-T 통합을 특징으로 하는 ICP 배치가 추가된 토폴로지 1이 포함됩니다. 고객은 ICP 내의 추가 컨테이너 이름 공간을 프로비저닝할 수 있으며, 이를 통해 각 네임스페이스마다 논리 스위치, IP 서브넷 및 T1 게이트웨이 인스턴스의 작성이 자동화됩니다.

vCenter Server에서 ICP가 작동하는 방법을 완전히 이해하려면 ICP on vCenter Server 아키텍처 문서를 참조하십시오. 고객이 지정한 {{site.data.keyword.cloud_notm}} 사설 및 공용 포터블 IP 공간은 고객 사용을 위해 각 T0에 지정됩니다.

이 디자인에는 vCenter Server 인스턴스가 사용 중지되고 삭제되는 경우 이 IP 범위를 삭제하지 않는 옵션이 있습니다.

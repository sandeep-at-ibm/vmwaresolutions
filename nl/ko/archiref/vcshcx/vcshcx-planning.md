---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-22"

subcollection: vmware-solutions


---

# 사전 배포 계획
{: #vcshcx-planning}

HCX를 배포하는 데 소요하는 대부분의 시간은 사전 배포 단계에서 사용합니다. 정보 시스템 마이그레이션 프로젝트는 일반적으로 몇 달에서 몇 년이 걸리지만 HCX를 사용하면 배치 후 즉시 클라우드에 네트워크 연결 및 마이그레이션을 시작할 수 있습니다.

엔터프라이즈 레벨
고객용으로 HCX를 배치하려면 대개 보안, 네트워크, 스토리지 및
vSphere 인프라 팀이 관여해야 하므로, 가능한 경우 이 팀이
POC에 관여하는 것이 적합합니다. 효율적으로 프로젝트를
관리하고 이해 당사자를 조기에 포함시키는 것이 HCX를 빠르게 배포하고
운영하는 데 중요합니다.

## 분석 마비(analysis paralysis) 방지
{: #vcshcx-planning-avoiding}

애플리케이션 환경의 일부를 수정해야 하는 필요성, 해당 변경의 디자인
및 해당 변경에 필요한 가동 중단 시간 스케줄 때문에 가상 머신(VM) 또는
VM 그룹을 마이그레이션하는 데 시간이 많이 걸리고 장애가
많이 있습니다. 이러한 변경을 마치고 나면 마이그레이션을 되돌리기가 어려워지므로 분석 마비가 심화됩니다. 마이그레이션의 모든 측면을 파악하고 팀 간에 조정하며 주요 지분 보유자를 변경하면 프로젝트를 지연시킬 수 있습니다.

HCX를 사용하면 애플리케이션을 수정하지 않고 특정 또는 전체
컴포지트 애플리케이션을 나타내는 VM 그룹 또는 VM의 교차 vSphere
인스턴스 마이그레이션이 가능합니다. 따라서
마이그레이션을 취소하면 VM을 뒤로 이동하거나 네트워크를
재확장합니다. 따라서 마이그레이션 계획의 대부분이
필요하지 않게 되며 계획 프로세스에서 병렬 처리가 가능합니다. 이동할
애플리케이션을 선택하고 상위 레벨 네트워크 디자인을 작성하고 나면
최종 네트워크 연결 및 디자인이 작동하는 동안 클라우드
인스턴스에서 최소 구성을 사용하여 애플리케이션이
마이그레이션을 시작할 수 있습니다.

## 확장 네트워크
{: #vcshcx-planning-stretched-net}

HCX Fleet의 네트워크 확장 컴포넌트는 매우 안정적입니다. 한 특정
고객에게 다른 트래픽 및 HCX 마이그레이션 터널과 공유하는
1Gbps WAN 전체에서 {{site.data.keyword.cloud}}로 확장된
VLAN이 20개가 넘게 있어도 네트워크로 인한 애플리케이션 문제가 없습니다. 이 방식을 사용하면 네트워크 링크가 6개월 이상 동안 작동합니다.

아무 문제 없이 확장 네트워크를 추가하거나 제거할 수 있습니다. 근접하여(이 특정 고객의 경우 < 6ms 대기 시간) {{site.data.keyword.CloudDataCent_notm}}를
선택하면 확장 네트워킹의 네트워크 안정성에도
기여합니다. 대역폭이 충분하고 애플리케이션의 대기 시간이
충분히 낮은 경우 확장 네트워크를 오랜 기간 동안 가동한 상태로
두어도 디자인에 부정적인 영향을 주지 않아야 합니다.

## 마이그레이션 라이프사이클
{: #vcshcx-planning-mig-lifecycle}

다음 절에서는 일반 HCX 마이그레이션 라이프사이클의
단계를 설명하며 작업 스트림을 병렬로 수행할 수 있는 경우를
나타냅니다.

## vSphere 인벤토리
{: #vcshcx-planning-vsphere-planning}

- 마이그레이션할 애플리케이션에서 대략적으로 VM 분류. 대략적이란 애플리케이션에 참여하는 VM을 심층적으로
분석하지 않고 이해하는 것을 나타냅니다.
- 여러 VM을 마이그레이션할 계획이고 네트워크 대역폭이
소스와 클라우드 사이트 간에 한정된 경우, 소스에서 NSX를
사용하면 VLAN이나 VXLAN별로 VM을 그룹화합니다. 그러면 VLAN별 VM 그룹이 마이그레이션되고 해당 그룹이 있는 L2 네트워크가 VLAN이 릴리스되는 지점까지만 확장되는 계단식 HCX 마이그레이션 계획을 사용할 수 있습니다.

즉, 관련 L2 확장
네트워크의 초기 그룹은 클라우드 측 네트워크 디자인이
완료되고 배치될 때만 확장 해제할 수 있습니다. 확장 해제란
클라우드 인스턴스 NSX 인프라를 통해 라우팅하도록 특정
VXLAN 트래픽을 전환하는 것을 나타냅니다.

## 기준선 네트워크 구성
{: #vcshcx-planning-baseline-net-config}

클라우드 측 vSphere 인스턴스 내에 안전한 주변 네트워크를 작성하십시오. 이 네트워크는 일반적으로 NSX DLR 또는 Edge 어플라이언스로 구성됩니다. HCX 근접 라우팅을 사용하는 경우 확장 L2 트래픽에
영향을 주지 않고 나중에 또는 동시에 완료할 수 있으므로
방화벽 규칙 또는 업링크 토폴로지를 작성할 필요가
없습니다.

## 	네트워크 확장
{: #vcshcx-planning-net-extension}

네트워크를 확장하면 가상 분산 스위치 포트
그룹(vDS)으로 표시된 소스 vSphere 환경에서 기존 VLAN
또는 VXLAN을 HCX의 클라우드 측에서 NSX VXLAN으로
확장하는 것입니다.

## 이동 전 테스트
{: #vcshcx-planning-preflight-tests}

이동 전 테스트에서는 기준선 전송 속도를 설정하기 위해
vMotion과 대량 마이그레이션 기능을 모두 사용하여 HCX 마이그레이션을
수행합니다.

## 비프로덕션 앱 마이그레이션
{: #vcshcx-planning-mig-non-prod-apps}

이 시점에서 VM 마이그레이션은 일련의 계획된 덜 중요한 VM 단계로 시작합니다. 개발과 테스트 등에서는 마이그레이션과 확장 L2 트래픽에 인터넷 연결을 사용합니다.

## 클라우드 네트워크 디자인 및 구현 시작
{: #vcshcx-planning-cloud-net-begins}

마이그레이션이 계속되는 동안 클라우드 측 네트워크 디자인이
클라우드 측 vSphere 인스턴스에서 완료되고 구현됩니다.

## 추가 네트워크 연결 고려사항
{: #vcshcx-planning-connect-considerations}

일반적으로 클라우드 제공자와 연결을 설정하는 데 몇 주에서
몇 달이 걸리므로 마이그레이션을 계속하는 동안 사설 WAN 네트워크
연결을 주문합니다. 사설 네트워크 연결이 완료되고 나면
HCX에서 마이그레이션과 확장 L2 트래픽에 전용 사설 네트워크 링크와
인터넷을 모두 사용하도록 구성할 수 있습니다.

## 실제 서버
{: #vcshcx-planning-physical-servers}

데이터 센터를 클라우드로 마이그레이션하려는 목표가 있으면
마이그레이션되는 VM과 상호작용하는 실제 서버를 VM(P2V) 또는 베어메탈로
{{site.data.keyword.cloud_notm}}에 마이그레이션할 수 있는지 아니면 소스에 그대로 남아 있는지
평가할 수 있습니다. 실제 서버가 소스에 그대로 남아 있고
전용 네트워크가 설정될 때까지만 마이그레이션 중에 HCX를
사용하는 경우 해당 서버가 HCX로 클라우드에 확장되는 네트워크에
있는지 파악하는 것이 중요합니다. 이 시나리오에서는
HCX에서 VM뿐 아니라 전체 서브넷을 클라우드로 마이그레이션할 수
있습니다.

물리적 디바이스와 마이그레이션된 VM 간에 연결이 유지보수되는 경우
마이그레이션을 종료할 때 HCX를 제거하려면 서브넷이 소스와 대상에
없어야 합니다. 즉, 확장 L2 네트워크에 있는
소스 사이트에 남겨진 모든 물리적 디바이스는 클라우드 측으로
라우팅될 수 있는 다른 네트워크 서브넷으로 마이그레이션해야
합니다. 단, NSX L2 VPN과 같은 다른 확장 L2 기술을
사용하여 HCX 확장 L2 엔드포인트를 대체하는 경우는
예외입니다.

## 프로덕션 및 복잡한 애플리케이션 마이그레이션
{: #vcshcx-planning-mig-prod-complex-app}

Oracle RAC 또는 MS Exchange / SQL 클러스터와 같은 공유 다중
기록기 VMDK가 있는 VM 또는 원시 디바이스 맵핑이 있는 VM은
마이그레이션 전에 추가 고려사항이 있는 VM의 예입니다.

## 네트워크 전환(Swing)
{: #vcshcx-planning-net-swing}

네트워크 전환은 소스 측 네트워크에서 VM 내보내기가
완료되고 클라우드 측에서 네트워크 디자인/구현이 완료된 후에
발생합니다. 일련의 마이그레이션 세트에서 완료된 VM과 관련하여
네트워크의 확장을 취소하도록 HCX를 구성하면 마이그레이션된 VM이
클라우드 측 NSX 인프라를 사용하여 네트워크 트래픽을
라우팅할 수 있습니다.

## 지원되는 클라이언트 플랫폼
{: #vcshcx-planning-client-platforms}

네트워크 확장의 경우 vSphere vDS(virtual Distributed Switch)가
있는 포트 그룹만 지원됩니다. 즉, vCenter에서 ESXi 호스트를 관리할 때만
vDS가 있을 수 있으므로 독립형 ESXi 호스트는 지원되지 않습니다.
- vSphere 5.1(API를 통한 vCenter 5.1의 명령행만)
- vSphere 5.5(vCenter 5.5u3 이상에서 지원되는 웹 클라이언트 UI)
- vSphere 6.0
- vSphere 6.5(vDS는 6.0 레벨이어야 함)

## 지원되는 클라우드 플랫폼
{: #vcshcx-planning-cloud-platforms}

HCX 클라우드 측은 {{site.data.keyword.cloud_notm}} 자동화를 통해 프로비저닝됩니다.

## 연결 옵션
{: #vcshcx-planning-connect-options}

### 표준 HCX 연결
{: #vcshcx-planning-standard-connect}

{{site.data.keyword.vmwaresolutions_short}} 자동화를 통해 배치된 대로
HCX 클라우드 측 설치는 기본적으로 공용 인터넷을 통해 연결하도록
구성됩니다.

### 선택적 연결성
{: #vcshcx-planning-optional-connect}

{{site.data.keyword.cloud_notm}} 사설 네트워크를 통한 연결은
주문 시 선택할 수 있습니다.

## 관련 링크
{: #vcshcx-planning-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 개요](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)   

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 컴포넌트 용어집
{: #hcxclient-components}

HCX는 클라우드 측(대상/VCD 환경)과 하나 이상의 클라이언트(소스)로 구성됩니다. HCX가 배치된 vCenter가 클라이언트나 클라우드 측의
동일한 SSO 도메인에 링크된 경우에도 vCenter당 하나의 HCX 인스턴스가
배치되어야 합니다. HCX에서 지원하는 구성은 일대일,
일대다, 다대일 및 다대다입니다.

## 대상 측 및 클라이언트 측
{: #hcxclient-components-cloud-client-side}

HCX에는 클라우드 측(대상/VCD 환경)과 클라이언트 측(소스)의 개념이 있습니다.

- 대상 측 - HCX 클라우드 관리자는 사전 배치되고 서비스 메시 작성을 위해 준비된 컴퓨팅 프로파일과 네트워크로 구성되어 있습니다.   
- 클라이언트 측 - 설치 및 조작의 전제조건을 충족하는
vSphere 인스턴스입니다. HCX의 클라이언트 측은
vCenter 웹 클라이언트 사용자 인터페이스(UI) 스냅인을 통해 클라우드 측 슬레이브
인스턴스를 제어하는 마스터입니다.

## HCX Manager
{: #hcxclient-components-hcx-manager}

- 클라우드 측 - HCX 클라우드 관리자는 수신되는 클라이언트 측 등록, 관리 및 제어 트래픽을 청취하도록 구성됩니다.
- 클라이언트 측 HCX 엔터프라이즈 관리자는 HCX를 관리하고 운영하는 UI 기능을 제공하는 클라이언트 측 고유 OVA 이미지 파일입니다. 클라이언트 측
HCX 관리자는 클라우드 측 HCX 관리자에 등록하고
클라이언트와 클라우드 측 사이의 관리 플레인을 작성할
책임이 있습니다. 또한 클라이언트 측 서비스 메시를 배치하고 클라우드 측에 동일한 작업을 수행하도록 지시할 책임이 있습니다.

## 서비스 메시 컴포넌트
{: #hcxclient-components-fleet}

HCX 서비스 메시 컴포넌트는 클라이언트와 클라우드 측 사이에 데이터와 제어 플레인을 작성할 책임이 있습니다. 미러링된 쌍에서 가상 머신(VM)으로 배치된 서비스 메시는 다음 컴포넌트로 구성됩니다.

- 상호연결 어플라이언스(HCX-IX) - 상호연결 어플라이언스는 vMotion 및 복제(대량 마이그레이션) 트래픽을 지원하는 암호화된 터널을 작성합니다. 
- WAN 최적화 프로그램 어플라이언스(HCX-WAN) - HCX에는 선택적으로 배치된 Silver Peak™ WAN 최적화 어플라이언스가 포함됩니다. 이는 VM 어플라이언스로 배치됩니다. 배치 시
CGW 터널 트래픽은 WAN 최적화 프로그램을 순회하도록 경로가 재지정됩니다. WAN 최적화 프로그램이 연결 안정성을 높이는 반면 WAN 전체의 트래픽을
현저히 줄이므로(일반적으로 3:1 ~ 6:1로 관찰됨) 항상 CGW와 함께 WAN
최적화 프로그램을 배치하는 것이 좋습니다. WAN 최적화 프로그램을
배치하면 VM 마이그레이션 트래픽에서 사용하는 WAN 대역폭이 제한된다는
이점이 추가됩니다. WAN 최적화 프로그램
관리 인터페이스는 기본적으로 구성되지 않습니다.
- 네트워크 확장(HCX-NE) - 가상 머신의 IP를 다시 지정할 필요가 있는 온프레미스 위치와 vSphere 환경 간의 마이그레이션을 사용으로 설정하여 계층 2 네트워크 확장 기능을 제공합니다. 
- 프록시 ESXi 호스트 - HCX-IX가 클라우드 측 HCX 사이트에 연결하도록 구성할 때마다 클러스터 외부의 vCenter에 프록시 ESXi 호스트가 표시됩니다. 이 ESXi 호스트에는 해당 HCX-IX 어플라이언스와 같은 관리 및 vMotion IP 주소가 있습니다. 따라서
로컬 vMotion을 수행하는 것처럼 클라이언트와 클라우드 측 모두에서
vSphere 환경이 작동할 수 있습니다. 이 방법을 사용하면 다음과 같은 이점이 있습니다.
  - 기능은 손실되지 않으면서 양측에 있는 관리
IP 범위가 겹칠 수 있습니다.
  - 클라우드 측에서 클라이언트 측의 vSphere를 볼 수 없으므로 보안이 강화됩니다.

## HCX 사용자 포털
{: #hcxclient-components-hcx-user-portals}

- 클라이언트 웹 UI - HCX 클라이언트 웹 포털은 HCX의 기본 UI입니다. 클라이언트 측 HCX 관리자가 설치되면
vCenter 웹 UI에 스냅인으로 표시됩니다. 원격 클라우드 HCX 등록(사이트 페어링),
Fleet 컴포넌트 배치, 네트워크 확대 및 클라우드에/에서 VM 마이그레이션을 제어합니다.
- 클라우드 측 UI – 클라우드 측 HCX UI는 HCX 클라이언트 등록에 지정된
공용 등록 URL을 통해 액세스할 수 있습니다. 기본적으로 클라우드 측 vCenter 관리자 인증 정보 ` administrator@vsphere.local`을 사용합니다. 일반적으로
설치를 업그레이드하고 네트워크 구성을 수정하는 데 사용합니다.

## 관련 링크
{: #hcxclient-components-related}

* [VMware HCX on IBM Cloud에 대한 포트 액세스 요구사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req)
* [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 클라이언트 배치](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [HCX 온프레미스 서비스 메시](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 하이브리드 클라우드 마이그레이션](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [매개변수 및 컴포넌트 모니터링](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---
# 설치 환경 준비
{: #hcx-archi-prep-install}

VMware HCX on IBM Cloud를 설치하려면 다음 소프트웨어 요구사항이 필요합니다.
* vSphere 5.5 U3 또는 vSphere 6.0u2 이상
* NSX가 사용된 경우 버전 6.2.2 이상이 필요합니다. 정책 마이그레이션에 NSX가 필요합니다.
* 교차 클라우드 vMotion을 사용하기 위해 동일한 유사성 제한사항이 온프레미스에서와 같이 클라우드에 적용됩니다. 자세한 정보는 [VMware EVC 및 CPU 호환성 FAQ](http://bit.ly/2vK6Sp5)를 참조하십시오.

## 네트워크 연결 구성
{: #hcx-archi-port-req-config-net}

HCX는 공용 인터넷 및 사설 회선을 순회하고 네트워크, 스위치 및 포트 그룹과 같은 데이터 센터 컴포넌트에 연결해야 합니다.
* [포트 액세스 요구사항](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req)에는 HCX 가상 어플라이언스가 설치될 수 있도록 열려 있어야 하는 포트가 나열되어 있습니다.
* 온프레미스 vSphere 환경 및 VCF/VCS HCX Cloud 환경은 모두 vSphere 온프레미스 디바이스와 VCF/VCS HCX 디바이스 사이에 NTP(Network Time Protocol) 클록 동기화를 허용해야 합니다. UDP 포트 123은 HCX 가상 어플라이언스 및 네트워크에 액세스할 수 있어야 합니다.

## 온프레미스 환경
{: #hcx-archi-port-req-on-prem-env}

HCX를 설치하기 전에 사용자의 환경이 수행할 태스크를 지원할 수 있는지 확인하십시오. 온프레미스 환경은 HCX를 설치하기 전에 다음 태스크를 지원해야 합니다.
* vSphere 5.5 Update 3 또는 6.0 Update 2가 포함된 Virtual Center
* vMotion 및 정책 마이그레이션 기능에는 NSX 버전 6.2.2 이상이 필요합니다.
* 관리자 vCenter Server 시스템 역할이 지정된 vSphere 서비스 계정
* vCenter에서 HCX 어플라이언스를 설치할 수 있는 충분한 디스크 공간
* 설치 중에 온프레미스 VM을 프로비저닝할 수 있는 충분한 IP 주소
* 포트 액세스 요구사항에 설명된 대로 필요에 따라 열려 있는 포트 및 방화벽
* 싱글 사인온(SSO) 서버가 원격인 경우 vCenter의 URL, 외부 SSO Server 또는 외부 검색 서비스를 실행하는 PSC(Platform Services Controller)가 식별되어야 합니다. HCX Manager가 vCenter에 등록되어 있으면 이 URL을 제공해야 합니다.
* vCenter에 검색 서비스의 자체 내부 인스턴스가 없는 경우 이유는 다음 중 하나일 수 있습니다.
  * vCenter 6.0u2가 외부 Platform Services Controller를 실행하고 있습니다.
  * vCenter는 연결 모드에 있습니다(보조 vCenter가 기본 vCenter의 SSO 서비스를 사용하거나 외부 SSO 서비스를 사용함).

## 계층 2 설치 환경 확인
{: #hcx-archi-port-req-verify-layer-2-inst}

계층 2 네트워크 확장의 요구사항은 다음과 같습니다.
* vSphere Enterprise Plus Edition
* vSphere vCenter는 계층 2 확장을 지원하기 위해 다음 요구사항을 충족해야 합니다.
  * vSphere Enterprise Plus 라이센스
  * vDS(vSphere Distributed Switch)가 있어야 합니다. 분배 스위치는 vSphere Enterprise Plus Edition에 사용 가능합니다.
  * 설치된 경우 온프레미스 Layer 2 Concentrator 서비스 어플라이언스에는 확장될 vNIC 포트 및 VLAN에 액세스할 수 있는 권한이 있어야 합니다.
  * 네트워크가 공용 인터넷 또는 VPN(대체 경로게 있음)을 통해 확장될 경우 VCF/VCS의 L2C 가상 머신에는 IP 주소가 필요합니다. Layer 2 Concentrator를 구성하려면 원격 IP 주소가 필요합니다.
  * 다중 Layer 2 Concentrator가 필요한 경우 각 Layer 2 Concentrator에는 온프레미스 및 클라우드에 IP 주소가 있어야 합니다.

## 관련 링크
{: #hcx-archi-port-req-related}

* [소스에 HCX 설치 및 구성](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [VMware EVC 및 CPU 호환성 FAQ](http://bit.ly/2vK6Sp5)

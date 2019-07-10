---

copyright:

  years:  2019, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 온프레미스 서비스 메시
{: #hcxclient-vcs-mesh-deployment}

다음 섹션에서는 HCX 클라이언트 인스턴스를 구성하는 단계를 자세히 설명합니다. 
  1. 사이트 페어링 IBM Cloud for VMware Solutions 환경
  2. HCX 온프레미스 네트워크 프로파일 작성
  3. HCX 온프레미스 컴퓨팅 프로파일 작성
  4. HCX 서비스 메시 작성
  5. 네트워크 확장

## 사이트 페어링 IBM Cloud for VMware Solutions 환경
{: #hcxclient-vcs-mesh-deployment-sitepair}

1. vSphere Web Client에 로그인하십시오. 
2. **홈** 메뉴에서 **HCX** 옵션을 선택하십시오. 
3. **인프라** -> **상호연결** 아래에서 **사이트 페어링 추가**를 클릭하십시오.
   1. 사이트 URL: HCX 클라우드 관리자 URL
     * 예: `https://x.x.x.x.x`
   2. 사용자 이름 및 비밀번호: HCX Manager 관리 세부사항
     * 관리/비밀번호
   3. 이전 세부사항은 HCX on IBM Cloud** for the IBM Cloud for VMware 솔루션 인스턴스의 **서비스** 아래에 있는 IBM Cloud Portal에서 가져올 수 있습니다. 
4. **연결**을 클릭하십시오. 

### 결과
{: #hcxclient-vcs-mesh-deployment-sitepair-results}

사이트 페어링이 성공적으로 등록되었으며 UI에 표시됩니다.

## HCX 온프레미스 프로파일 작성
{: #hcxclient-vcs-mesh-deployment-profiles}

## 온프레미스 서비스 메시 네트워크 프로파일
{: #hcxclient-vcs-mesh-deployment-profiles-network}

1. vSphere Web Client에 로그인하십시오. 
2. **홈** 메뉴에서 **HCX** 옵션을 선택하십시오. 
3. **인프라** -> **상호연결** 아래에서
4. 다중 사이트 서비스 메시 아래에서 **네트워크 프로파일**을 클릭하십시오. 
5. 시작 지점: **네트워크 프로파일 작성**
   1. 분배 포트 그룹(예: 외부)을 선택하십시오. 
   2. 외부 IP의 IP 주소 범위를 제공하십시오. 
   3. 외부 서브넷 접두부 길이를 제공하십시오.
   4. 외부 게이트웨이를 제공하십시오.
   5. DNS 세부사항을 제공하십시오.
   6. MTU를 1500으로 설정하십시오.
   7. 작성을 클릭하십시오.
6. 관리 및 vMotion 네트워크에 대한 이전 단계를 반복하십시오.
   참조: MTU는 9000으로 설정되어야 합니다. 

## 결과
{: #hcxclient-vcs-mesh-deployment-profiles-network-results}

| 네트워크 이름 | MTU |
| -----| ----|
| 외부 | 1500|
| 관리 |9000|
| vMotion |9000|

## 온프레미스 서비스 메시 컴퓨팅 프로파일
{: #hcxclient-vcs-mesh-deployment-profiles-compute}

1. vSphere Web Client에 로그인하십시오. 
2. **홈** 메뉴에서 **HCX** 옵션을 선택하십시오. 
3. **인프라** -> **상호연결** 아래에서
4. 다중 사이트 서비스 메시 아래에서 **컴퓨팅 프로파일**을 클릭하십시오. 
5. 시작 지점: **컴퓨팅 프로파일 작성**
   1. 컴퓨팅 프로파일 이름을 제공하십시오.
   2. 사용으로 설정할 모든 서비스를 선택하고 **계속**을 클릭하십시오. 
   3. 클러스터를 선택하고 **계속**을 클릭하십시오. 
   4. 데이터 저장소를 선택하고 **계속**을 클릭하십시오. 
   5. 관리를 위한 네트워크 프로파일을 선택하고 **계속**을 클릭하십시오. 
   6. 외부/업링크를 위한 네트워크 프로파일을 선택하고 **계속**을 클릭하십시오. 
   7. vMotion을 위한 네트워크 프로파일을 선택하고 **계속**을 클릭하십시오. 
   8. vSphere 복제(관리)를 위한 네트워크 프로파일을 선택하고 **계속**을 클릭하십시오. 
   9. 확장을 위한 분배 스위치(예: 사설-스위치)를 선택하십시오.
   10. 완료를 클릭하십시오.

## 결과
{: #hcxclient-vcs-mesh-deployment-profiles-compute-results}

클러스터/스토리지 조합을 위한 컴퓨팅 프로파일이 작성되었으며 서비스 메시 작성에 사용할 수 있습니다. 

## HCX 온프레미스 서비스 메시
{: #hcxclient-vcs-mesh-deployment-servicemesh}

## 온프레미스 서비스 메시 작성
{: #hcxclient-vcs-mesh-deployment-servicemesh-creation}

1. vSphere Web Client에 로그인하십시오. 
2. **홈** 메뉴에서 **HCX** 옵션을 선택하십시오. 
3. **인프라** -> **상호연결** 아래에서
4. 다중 사이트 서비스 메시 아래에서 **서비스 메시**를 클릭하십시오. 
5. 시작 지점: **서비스 메시 작성**
   1. 사이트 즉, 온프레미스 및 vCloud 조직을 선택하고 계속을 클릭하십시오. 
   2. 소스 컴퓨팅 프로파일을 선택하십시오.
   3. 원격 컴퓨팅 프로파일을 선택하십시오. 예를 들면, CloudCompute입니다.
   4. 모든 서비스를 선택하고 계속을 클릭하십시오.
   5. 고급 구성 - 대체 업링크 네트워크 프로파일 페이지에서 계속을 클릭하십시오(선택사항). 
   6. 계속을 클릭하십시오. 
   7. 계속을 클릭하고 고급 구성 - WAN 활성화 서비스 대역폭 한계 페이지에서 기본값을 계속 사용하십시오. 
   8. 서비스 이름을 제공하고 **완료**를 클릭하십시오. 
6. 서비스 메시 작성을 위해 태스크 목록을 살펴보십시오. 마지막에는 온프레미스 위치에서 세 개의 HCX 어플라이언스, 클라우드 위치에서 세 개의 HCX 어플라이언스가 있어야 합니다. 

## 결과
{: #hcxclient-vcs-mesh-deployment-servicemesh-results}

HCX 서비스 메시는 소스 및 대상 사이트에 유효한 HCX 서비스 구성입니다. 서비스 메시는 두 사이트 모두에서 유효한 컴퓨팅 프로파일을 작성한 연결된 사이트 페어링에 추가될 수 있습니다. 

서비스 메시를 추가하면 두 사이트 모두에서 HCX 상호연결 가상 어플라이언스의 배치가 시작됩니다. 상호연결 서비스 메시는 항상 소스 사이트에 작성됩니다.

## 네트워크 확장
{: #hcxclient-vcs-mesh-deployment-network-stretching}

## 네트워크를 확장하는 프로세스
{: #hcxclient-vcs-mesh-deployment-stretching-process-stretch}

HCX를 사용하여 네트워크(VLAN 또는 VXLAN)를 확장하려면 클라이언트 측 vCenter 웹 UI에서 다음 단계를 완료하십시오.

1. vSphere Web Client에 로그인하십시오. 
2. **홈** 메뉴에서 **HCX** 옵션을 선택하십시오. 
3. 왼쪽 메뉴의 **서비스** -> **네트워크 확장** 아래에서 
4. **네트워크 확장**을 클릭하십시오. 
   1. 확장할 네트워크를 선택하십시오.
   2. 현재 기본 게이트웨이와 서브넷 마스크를 CIDR 형식으로 입력하십시오.
   3. 화면의 맨 아래에서 **확장**을 클릭하여 네트워크 확장 워크플로우를 시작하십시오.

네트워크 진행상태는 vCenter 클라이언트 태스크 분할창에서 모니터링합니다.

## 네트워크 확장의 개념 및 우수 사례
{: #hcxclient-vcs-mesh-deployment-stretching-best-practices-network}

클라이언트 측 네트워크를 클라우드 측 VXLAN에 연결하는 접점은 전용 HCX 기술로 구성된 정교한 다중 터널 VPN입니다. NSX를 기반으로 하지 않지만 NSX와 함께 작동하며 기능을 확장합니다. 이 프로세스는 클라이언트 측 vCenter 웹 사용자 인터페이스(UI)를 통해 제어하며 배포를 자동화하고 클라이언트와 클라우드 측의 두 엔드포인트를 모두 표시하는 데 사용합니다. 확장할 네트워크는 개별적 또는 일괄처리를 통해 선택합니다.

또한 네트워크 확장 워크플로우의 일부로, 클라우드 측의 NSX에 VXLAN을 빌드하도록 지시하면 VXLAN이 지정된 클라우드 측 L3 디바이스(연결되지 않은 상태로 남아 있는 DLR 또는 ESG) 및 클라우드 측 네트워크 확장 어플라이언스에 작성된 인터페이스에 연결됩니다.

특정 애플리케이션을 마이그레이션할 때 적용 가능한 가상 머신(VM)에서 사용 중인 모든 네트워크는 일반적으로 {{site.data.keyword.cloud}} 인스턴스로 확장되어야 합니다.

왜 항상 확장되지 않고 일반적으로 확장되는 것입니까? VM을 마이그레이션한 후 클라이언트 측에서 특정 트래픽의 연결을 끊으면 유리할 수 있습니다. 예를 들어 클라우드로 이동할 때 대역폭 사용을 높일 수 있는 VM 게스트 백업 클라이언트가 있습니다. 게스트 내 백업 클라이언트는 클라우드 측의 최신 블록 레벨 백업에서 자동으로 수집되므로 VM을 마이그레이션할 때 필요하지 않습니다.

클라이언트의 백업 네트워크 어댑터에 액세스되어 있지 않습니다. 이는 게스트 클라이언트 백업 스케줄을 종료하기 위해 각 VM에 액세스하는 것을 의미하기 때문입니다. 따라서 백업 네트워크가 사용되는 경우 백업에 실패할 수 있습니다. 이 상황은 모든 VM이 사후 마이그레이션에 도달하여 게스트 내 백업 클라이언트를 사용 안함으로 설정할 수 있을 때까지 임시로 발생합니다.

단일 네트워크 확장의 대역폭은 이론적으로 4Gbps이지만, 단일 네트워크 확장 쌍에 있는 모든 확장 네트워크의 한계일 수 있으며 단일 확장 네트워크에서 달성할 수 없습니다. 언더레이 대역폭이 충분히 할당되어 있으며 대기 시간이 낮은 경우(<~10ms) 단일 확장 네트워크는 ~1Gbps를 달성할 수 있습니다.

### 근접 라우팅 옵션
{: #hcxclient-vcs-mesh-deployment-stretching-prox-routing}

어떠한 유형의 라우트 최적화도 없이 확장된 네트워크는 모든 L3 액세스를 위해 클라이언트 측으로 다시 라우팅됩니다. 이 Trombone-ing에서는 소스와 대상 VM이 모두 클라우드에 있는 경우에도 패킷이 클라이언트(소스)와 클라우드 사이를 왔다갔다 이동해야 하므로 트래픽 패턴이 비효율적이게 됩니다. HCX의 근접 라우팅 기능은 이 문제와 트래픽의 로컬 유출을 해결하도록 설계되었습니다.

## 관련 링크
{: #hcxclient-vcs-mesh-deployment-deployment-related}

* [HCX 컴포넌트 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 클라이언트 배치](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-client-deployment)
* [VMware 하이브리드 클라우드 마이그레이션](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [매개변수 및 컴포넌트 모니터링](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-17"

subcollection: vmware-solutions


---

# HCX 클라이언트 배치
{: #hcxclient-vcs-client-deployment}

최소 HCX 설치는 단일 클라우드 및 클라우드 측 배치로 구성됩니다.

클라이언트와 클라우드 측 간에
네트워크 연결이 있다는 가정 하에 HCX 클라이언트 측은 HCX에서 지원하는
모든 버전의 vSphere에 설치할 수 있습니다.

## 요구사항
{: #hcxclient-vcs-client-deployment-req}

| 컴포넌트 | CPU 수 |  메모리(GB) | 디스크(GB) |
|--------|--------|---------|-------|
|HCX Manager |4 | 12G |  60G |
| HCX 상호연결(HCX-IX) |4 | 3G |  2G |
| HCX 네트워크 확장(HCX-NE) |4 | 3G |  2G |
| HCX WAN 최적화 프로그램(HCX-WAN) |8 | 14G |  100G |

## 클라이언트 라이센싱
{: #hcxclient-vcs-client-deployment-licensing}

HCX는 서비스입니다. HCX는 VMware에서 유지보수하는 라이센싱 서버를 통해
관리되는 가상 머신(VM) 및 사이트별로 라이센스가 부여됩니다. HCX 클라우드와
클라이언트 측 인스턴스는 라이프사이클 동안 VMware 등록 사이트와
통신해야 합니다.
- 80 및 443에서의 트래픽은
`https://connect.hybridity.vmware.com`에 허용되어야 합니다.
- 일회성 사용 등록 키는 {{site.data.keyword.vmwaresolutions_full}} 콘솔에서 제공하는 클라이언트 측 설치용으로 제공됩니다. 이 키는 각 클라이언트 측
HCX 설치에 필수입니다.

### 온프레미스 HCX 라이센스를 주문하는 프로시저
{: #hcxclient-vcs-client-deployment-license-ordering-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **온프레미스 HCX 라이센스** 테이블로 스크롤하여 **새로 프로비저닝**을 클릭하십시오.
3. 라이센스 이름을 지정하십시오.
4. 주문에 적용되는 이용 약관의 링크를 클릭하고 라이센스를 주문하기 전에 이 이용 약관에 동의하는지 확인하십시오.
5. **프로비저닝**을 클릭하십시오.

## IP 주소 요구사항
{: #hcxclient-vcs-client-deployment-client-ip-reqs}

HCX를 배치하려면 온프레미스와 대상 IBM Cloud 모두에서 적절한 수의 IP 주소를 사용할 수 있어야
합니다.

* vMotion 주소
  vMotion에 개별 네트워크를 유지하는 것은 온프레미스 데이터 센터의 공통 사례입니다. 클라우드 게이트웨이에는 vMotion 네트워크에 대한 액세스 권한이 있어야 합니다. 그렇지 않으면, vMotion 네트워크와 통신하기 위한 추가 IP 주소가 필요합니다.

* 온프레미스
  * HCX Manager 어플라이언스에 하나의 IP 주소
  * 각 상호연결 어플라이언스에 하나의 IP 주소, 개별 vMotio 네트워크가 있는 경우 하나의 IP 주소를 추가합니다.
  * 각 표준 네트워크 확장에 하나의 IP 주소

* IBM Cloud
  * IBM Cloud에 연결되는 HCX Manager 어플라이언스당 두 개의 IP 주소. 주소는 인터넷 또는 하나 이상의 Direct Connect 회선에 연결하는 데 사용될 수 있습니다.
  * 개별 vMotion 네트워크 연결이 있는 경우 하나를 추가합니다.

## 클라이언트 측 OVA 다운로드
{: #hcxclient-vcs-client-deployment-client-ova}

클라이언트 측 HCX는 사용자가 배치하며 소스 vCenter에 대한 관리자 레벨 권한이 필요합니다. 이 문서 작성 당시, HCX 클라이언트-서버
관리자 ova는 약 1.7GB입니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하여
HCX를 주문하면 클라우드 측에 배치된 HCX 버전과 일치하는
클라이언트 측의 HCX 버전을 다운로드하는 링크가 포함된
URL이 제공됩니다. 이 링크는 클라우드 측 HCX Manager 사용자 인터페이스(UI)에 제공됩니다.

일회성 사용 등록 키도 제공됩니다. 다음 단계를 사용하여 사용 등록을 구성하십시오.

1. 클라우드 측 HCX UI에 제공된 링크에서 HCX 클라이언트(엔터프라이즈)
OVA를 다운로드하십시오.
    1. IBM에서 제공한 HCX 등록 UI를 사용하여 클라우드 측 HCX UI에 로그인합니다.
    2. 클라우드 vCenter ID와 비밀번호를 사용하여 UI에 로그인합니다.
    3. **관리** 탭에서 **요청 다운로드 링크**를 선택하여 클라이언트 측 OVA를 다운로드하십시오. OVA가 배치된 소스 vCenter에 로컬인 “점프 상자”를 사용하여 이 단계를 완료하십시오.

## 소스에 HCX 설치 및 구성
{: #hcxclient-vcs-client-deployment-install-cfg-src}

온프레미스 설치에는 HCX 관리 어플라이언스 배치와 vCenter 환경에 HCX 관리 어플라이언스 등록이 포함됩니다.

### HCX Manager 어플라이언스 설치
{: #hcxclient-vcs-client-deployment-install-cfg-src-install-hma}

온프레미스 vCenter에 HCX Manager 어플라이언스를 설치하십시오.
1. **내 VMware**에 로그인하고 제품 다운로드 페이지에서 하이브리드 클라우드 서비스 OVA 파일을 다운로드하십시오.
2. 브라우저를 열고 vSphere Web Client에 로그인하십시오. **홈** 탭을 클릭하십시오.
3. **인벤토리 트리** 목록에서 **호스트 및 클러스터**를 클릭하십시오.
4. 계층 구조를 펼쳐 데이터 센터를 표시하십시오.
5. 대상 데이터 센터를 마우스 오른쪽 단추로 클릭하고 메뉴에서 **OVF 템플리트 배치**를 선택하십시오. **OVF 템플리트 배치** 메뉴 항목이 표시되는 데 몇 초가 걸릴 수 있습니다.
6. **OVF 템플리트 배치**를 선택하십시오.
  1. **로컬 파일**을 선택하고 **찾아보기**를 클릭하여 컴퓨터에 다운로드된 OVA 파일을 찾으십시오 **다음**을 클릭하십시오.
  2. **세부사항 검토** 페이지에서 **추가 구성 옵션 허용** 상자를 선택하고 **다음**을 클릭하십시오.
  3. **EULA 허용** 페이지에서 VMware 사용자 라이센스 계약을 검토하려면 아래로 스크롤하십시오. **동의**와 **다음**을 클릭하십시오.
  4. **이름 및 폴더** 를 선택하십시오. 필요한 경우 이름을 편집하고 하이브리드 클라우드 서비스의 위치를 선택하십시오. **다음**을 클릭하십시오.
  5. **리소스 선택** 페이지에서 설치 위치를 선택하십시오.
  6. **스토리지 선택** 페이지에서 하이브리드 클라우드 서비스의 스토리지를 선택하고 **다음**을 클릭하십시오. **가상 디스크 형식 선택** 목록에서 **씬 프로비저닝** 또는 **thick 프로비저닝**을 선택할 수 있습니다.
  7. **네트워크 설정** 페이지에서 하이브리드 클라우드 서비스 어댑터를 **대상** 목록에서 선택한 호스트 네트워크에 맵핑하십시오.
7. **사용자 정의된 템플리트** 페이지에서 환경에 특정한 값을 입력하십시오.
  * 비밀번호의 경우 명령행 인터페이스(CLI)및 웹 사용자 인터페이스의 기본 사용자 이름은 모두 **admin**입니다. 웹 사용자 인터페이스에 로그인하려면 **admin** 사용자 및 비밀번호가 필요합니다(설정될 수 있는 비밀번호에 있는 **root** 사용자 계정이기도 함).
  * CLI **admin** 사용자 비밀번호를 입력하고 다시 입력하십시오.
  * **root** 사용자 비밀번호를 입력하고 다시 입력하십시오. 나중에 VMware GSS(Global Support Services)의 도움이 필요한 경우 시스템의 문제점을 해결하기 위해 이 비밀번호가 공유되어야 할 수 있습니다.
  * 네트워크 특성의 경우 HCX Manager VM의 호스트 이름을 입력하십시오. 네트워크 IPv4 주소, IPv4 접두부(CIDR) 및 기본 게이트웨이를 입력하십시오. 다음 표에는 샘플 값이 표시됩니다.

표 1. 네트워크 특성의 샘플 값

| 필드                    |값           |
|--------------------------|-----------------|
|호스트 이름                 | HCM_1           |
| 네트워크 1 IPv4 주소   | 192.168.200.101 |
| 네트워크 1 IPv4 접두부    | 24              |
| 기본 IPv4 게이트웨이     | 192.168.200.1   |
| 네트워크 1 IPv6 주소   |                 |
| 네트워크 1 IPv6 접두부    |                 |

8. vService 바인딩 페이지를 검토하십시오. 계속하려면 **다음**을 클릭하십시오.
9. **완료 준비** 페이지에서 다음 단계를 수행하십시오.
  * **배치 후 전원 켜기** 상자를 선택하십시오.
  * 하이브리드 클라우드 서비스 설정을 검토하고 **완료**를 클릭하십시오. 하이브리드 클라우드 서비스 어플라이언스의 전원을 켜는 데 몇 분이 걸릴 수 있습니다.
  * 상태를 확인하려면 vSphere Web Client 홈 페이지로 이동하고 **홈** 탭에서 **인벤토리**로 이동한 후 **호스트 및 클러스터**를 클릭하십시오. 데이터 센터 계층 구조를 펼치고 하이브리드 클라우드 서비스 서비스 가상 머신을 클릭하여 센터 분할창에 요약을 표시하십시오.
  * **요약** 탭을 보십시오. 콘솔에 **전원 켜짐**이 표시되고 **재생** 단추는 녹색입니다.
10. HCX Manager의 전원이 켜지고 온프레미스 vCenter에 등록할 준비가 됩니다.

## HCX Manager 어플라이언스의 초기 구성
{: #hcxclient-vcs-client-deployment-inital-config}

1. 하이브리드 클라우드 서비스 가상 어플라이언스에 `https://connect.hcx.vmware.com`에 대한 아웃바운드 액세스 권한이 있는지 확인하십시오.
2. 하이브리드 클라우드 서비스 가상 어플라이언스 관리 인터페이스 `https://<IP>:9443`에 **admin**으로 로그인하십시오.
3. 클라이언트 측 전제조건에 수집된 라이센스 키를 제공하십시오.
4. HCX 클라우드 데이터 센터 위치
    - HCX 클라우드 인스턴스가 있는 데이터 센터에서 가장 가까운 도시를 입력하십시오. 도시가 없으면 가장 가까운 주요 도시를 선택하십시오.
5. 시스템 이름을 제공하십시오.

## vSphere Server 인증서 가져오기
{: #hcxclient-vcs-client-deployment-import-cert}

1. HCX Manager 관리 인터페이스 `https://<IP>:9443`에 로그인하십시오.
2. **인증서** -> **신뢰할 수 있는 CA 인증서** 아래에 있는 **관리** 탭을 선택하십시오.
3. vSphere Server 웹 사이트를 가져오십시오.
   1. URL에서 인증서를 가져오고 HCX 클라우드 측 등록 URL의 키를 가져오도록 선택하십시오.
     * 상파울루: `https://ssao01dirhcx01.vmware-solutions.cloud.ibm.com`

## vCenter/SSO/NSX에 HCX Manager를 등록하는 프로시저
{: #hcxclient-vcs-client-deployment-reg-vcenter}

1. 하이브리드 클라우드 서비스 서비스 가상 어플라이언스에 로그인하십시오.
2. **설정 관리** 타일을 클릭하십시오.
  1. 왼쪽 분할창의 **시스템 구성**에서 vCenter를 선택하십시오.
  2. 오른쪽 상단의 **vCenter 추가**를 클릭하십시오.
  3. `https://vCenter-host-name` 또는 `https://vCenter-IP-address` 양식으로 vCenter Server의 IP 주소를 입력하십시오.
    * 예를 들면, `https://My-vCenter` 또는 `https://10.108.26.211`입니다.
  4. vCenter Server 사용자 이름 및 비밀번호를 입력하십시오. 사용된 계정에는 vCenter 관리자 역할이 있어야 합니다.
  5. **확인**을 클릭하십시오. _앱을 다시 시작해야 합니다._ 메시지가 표시되면 다시 시작하지 마십시오.
3. SSO/검색 서비스를 구성하십시오.
  6. **관리** 탭을 클릭하십시오.
  7. **검색 서비스 URL** 텍스트 상자 옆에 있는 **편집**을 클릭하십시오.
  8. 다음 양식으로 검색 네트워크 서비스 엔드포인트를 입력하십시오.
    * vCenter Server 6.5: `https://psc/`
  9.  필요에 따라 NSX 세부사항을 제공하십시오.
  10. **확인**을 클릭하십시오. 웹 엔진을 다시 시작해야 하는 메시지가 표시되면 다시 시작하지 마십시오.
4. **요약** 탭을 클릭하고 **하이브리디티 관리 컴포넌트** 섹션을 찾으십시오. 애플리케이션 엔진과 웹 엔진을 모두 중지한 후 시작하십시오.
5. 등록을 완료하려면 vSphere Web Client를 로그아웃하십시오. vSphere Web Client에 다시 로그인하여 HCX 탭이 있는지 확인하십시오.

## 결과
{: #hcxclient-vcs-client-deployment-reg-vcenter-results}

기존의 **하이브리드 클라우드** 아이콘과 왼쪽에 있는 **하이브리드 클라우드 서비스** 메뉴 항목에 유의하십시오. 하이브리드 클라우드 서비스 등록에서 이 레이블을 업데이트합니다. 인벤토리에서 아이콘 레이블은 **하이브리드 클라우드 서비스**가 됩니다.

## 관련 링크
{: #hcxclient-vcs-client-deployment-related}

* [HCX 컴포넌트 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-components)
* [설치 환경 준비](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-planning-prep-install)
* [HCX 온프레미스 서비스 메시](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-vcs-mesh-deployment)
* [VMware 하이브리드 클라우드 마이그레이션](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-migrations)
* [매개변수 및 컴포넌트 모니터링](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-monitoring)
* [HCX 문제점 해결](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcxclient-troubleshooting)

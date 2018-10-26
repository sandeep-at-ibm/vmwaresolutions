---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-21"

---

# NSX Edge Services Gateway 정보

VMware NSX Edge Services Gateway(ESG) 솔루션은 현재 {{site.data.keyword.cloud_notm}}에서 사용할 수 있는 VMware Cloud Foundation on {{site.data.keyword.cloud}} 및 vCenter Server on {{site.data.keyword.cloud_notm}} 오퍼링의 확장입니다. Cloud Foundation 및 vCenter Server에 대한 솔루션 아키텍처는 디자인에 있는 각 컴포넌트의 상위 레벨 구성 및 솔루션의 컴포넌트를 자세히 보여줍니다.

Cloud Foundation 및 vCenter Server 디자인에 대한 자세한 정보는 [솔루션 개요](../solution/solution_overview.html)를 참조하십시오.

## NSX Edge Services Gateway 개요

NSX Edge Services Gateway는 DHCP(Dynamic Host Configuration Protocol), 가상 사설망(VPN), NAT(Network Address Translation), 동적 라우팅 및 로드 밸런싱과 같은 공통 게이트웨이 서비스를 제공하여 격리된 스텁 네트워크를 공유(업링크) 네트워크에 연결합니다. NSX Edge의 공통 배치에는 DMZ(DeMilitarized Zone), VPN 엑스트라넷 및 NSX Edge가 각 테넌트, 워크로드 또는 관리 컴포넌트에 대한 가상 경계를 작성하는 다중 테넌트 클라우드 환경이 포함됩니다. NSX Edge Service Gateway 내에서 다음 기능을 사용할 수 있습니다.

표 1. NSX Edge Service Gateway에 사용 가능한 기능

|기능 |설명 |
|:------- |:----------- |
|NSX Edge 서비스 라우팅 |계층 2 브로드캐스트 도메인 간에 필요한 전달 정보를 제공하여 계층 2 브로드캐스트 도메인을 줄이고 네트워크 효율성 및 스케일을 향상시킬 수 있습니다. NSX는 동쪽-서쪽 라우팅을 수행하기 위해 이 인텔리전스를 워크로드가 상주하는 위치로 확장합니다. 이를 통해 비용이 많이 들거나 시기적절하게 홉을 확장해야 할 필요 없이 가상 머신 대 가상 머신의 직접 연결이 가능합니다. 동시에 NSX는 북쪽-남쪽 연결을 제공하여 테넌트가 공용 네트워크에 액세스할 수 있도록 합니다. |
|방화벽 |지원되는 방화벽 규칙에는 모든 프로토콜에 대한 상태 기반 검사를 위한 IP 및 포트 범위가 포함된 IP 5-튜플 구성이 포함됩니다. |
|NAT |소스 및 대상 IP 주소와 포트 변환에 대한 별도의 제어를 제공합니다. |
|DHCP |IP 풀, 게이트웨이, DNS 서버 및 검색 도메인의 구성을 제공합니다. |
|사이트 간 VPN |표준화된 IPSec 프로토콜 설정을 사용하여 모든 주요 VPN 공급업체와 상호 작동합니다. |
|L2VPN |L3 토폴로지에서 L2 네트워크를 확장할 수 있는 기능을 제공합니다. |
|SSL VPN-Plus |SSL VPN-Plus를 사용하면 원격 사용자가 NSX Edge 게이트웨이 뒤에 있는 사설 네트워크에 안전하게 연결할 수 있습니다. |
|로드 밸런싱 |단순하고 동적으로 구성 가능한 가상 IP 주소 및 서버 그룹을 제공합니다. |
|고가용성 |기본 NSX Edge 가상 머신이 사용 불가능한 경우 네트워크에서 NSX Edge가 활성화되도록 보장합니다. |

### 관련 링크

* [솔루션 개요](../solution/solution_overview.html)

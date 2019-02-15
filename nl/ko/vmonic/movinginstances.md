---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V1.4 이전 릴리스에서 인스턴스 업그레이드

## 문제점

V1.4 이상 릴리스의 인스턴스 네트워크 토폴로지는 V1.4 이전 릴리스와 다릅니다. 이러한 변경으로 인해 현재 릴리스의 상태에서 V1.4 이전 릴리스에 배치된 인스턴스를 사용할 수 없습니다.

## 해결

V1.4 이상 릴리스에서 여러 네트워크 토폴로지 개선사항이 인스턴스에 사용 가능합니다.
* (모든 인스턴스에 적용됨): 최적화된 네트워킹 구성. 사용 중인 {{site.data.keyword.cloud}} 계정이 VRF(Virtual Routing and Forwarding) 계정이어야 하거나 IBM Cloud 계정이 클래식(VRF 아님) 계정인 경우 VLAN Sanning이 사용으로 설정되어야 하므로 두 번째 포터블 IP 주소가 필요하지 않습니다. 배치에는 기본 {{site.data.keyword.cloud_notm}} 인프라 포터블 IP 주소만 필요합니다.
* (Cloud Foundation 인스턴스에만 적용됨): Microsoft Windows AD SSO(Active Directory Single Sign-On) 및 DNS(Domain Name System) 서버가 사용된 다중 사이트 배치 기능

V1.4 이전 릴리스에서 인스턴스를 마이그레이션하거나 삭제하지 않은 경우 보기 전용 모드로 계속해서 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 표시될 수 있습니다. 이 인스턴스는 경고 기호 아이콘을 사용하여 **더 이상 사용되지 않음**으로 사용자 인터페이스에 표시됩니다.

인스턴스 특성에 표시되는 정보는 V1.4 릴리스 날짜 기준으로 데이터를 반영하고 더 이상 새로 고쳐지지 않습니다.
{:note}

다음 조치는 V1.4 이전 인스턴스에서 사용할 수 있습니다.
*  인스턴스 세부사항 페이지의 정보를 봅니다.
*  인스턴스 백업 정보를 봅니다.
*  vSphere Web Client를 열어 vCenter의 인스턴스를 사용합니다.
*  {{site.data.keyword.cloud_notm}} 지원 티켓을 열어 인스턴스 복원을 요청합니다.
*  인스턴스를 삭제합니다.

V1.4 이전 인스턴스의 기타 모든 조치는 더 이상 사용할 수 없습니다.

V1.4 이전 인스턴스가 있고 계속해서 이를 사용할 계획인 경우 새 인스턴스를 작성하고 기존 구성을 새 인스턴스로 이동하여 V1.4 이전 인스턴스를 업그레이드할 수 있습니다.

V1.4 이전 인스턴스를 새 인스턴스로 이동하려면 vSphere Web Client에서 다음 단계를 완료하십시오.
1. V1.4 이전 인스턴스에서 모든 가상 머신(VM)을 내보내십시오,
2. 현재 릴리스에서 인스턴스를 작성하십시오.
3. **1단계**에서 내보낸 모든 VM을 가져오십시오.
4. 새 인스턴스를 사용하십시오.

VM 내보내기 및 가져오기에 대한 자세한 정보는 VMware vSphere 문서를 참조하십시오.

{{site.data.keyword.vmwaresolutions_short}}에 대한 지원이 필요하면 지원 채널 중 하나를 통해 [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic/trbl_support.html)하십시오.

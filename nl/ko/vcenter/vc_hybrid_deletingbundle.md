---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-16"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 인스턴스에서 Hybridity Bundle 제거
{: #vc_hybrid_deletingbundle}

vCenter Server 인스턴스에서 Hybridity Bundle 라이센스를 제거하려면, VMware vSphere Web Client에서 VMware NSX 및 VMware vSAN 임대 라이센스 키를 BYOL(Bring Your Own License) 키로 대체해야 합니다. 또한 임대 라이센스 비용을 취소하려면 지원 티켓을 열어야 합니다.

라이센스를 다운그레이드하면 vCenter Server 인스턴스가 실패할 수 있습니다. 사용자 책임 하에 라이센스를 다운그레이드하도록 선택할 수 있지만 먼저 다운그레이드하는 경우 사용할 수 없는 기능에 대해 고려하십시오. 자세한 정보는 [VMware 컴포넌트 에디션의 비교 차트](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution-appendix)를 참조하십시오.
{:important}

## 다중 사이트 환경에서 Hybridity Bundle을 제거하기 전의 중요한 고려사항
{: #vc_hybrid_deletingbundle-considerations}

다중 사이트 환경에서 Hybridity Bundle을 제거하기 전에 다음 고려사항을 검토하십시오.

* 임대 라이센스를 제거하기 전에 모든 다중 사이트 배치에 BYOL 라이센스를 적용해야 합니다.
* VMware NSX 라이센스를 결합해야 하고 모든 다중 사이트 배치에서 사용하기에 충분한 용량이 있어야 합니다.
* 모든 다중 사이트 배치에서 Hybridity Bundle을 제거하려면 단일 지원 티켓을 작성해야 합니다.

다중 사이트 환경에서 Hybridity Bundle을 제거하기 전에 BYOL 라이센스가 적용됩니다. 다중 사이트 구성의 모든 사이트에서 라이센스 에디션이 일치하는지 확인해야 합니다.
{:note}

## Hybridity Bundle을 제거하기 전에
{: #vc_hybrid_deletingbundle-prereq}

Hybridity Bundle을 제거하기 전에 다음 요구사항을 확인하십시오.

* Hybridity Bundle이 사용으로 설정되어 있는 V2.4 이상의 vCenter Server 인스턴스가 있습니다.
* vCenter Server 인스턴스에 설치된 {{site.data.keyword.cloud_notm}} 서비스에 VMware HCX가 없습니다.
* VMware vSphere Web Client에 대한 관리자 권한이 있습니다.
* 이미 적용되지 않은 경우 VMware NSX 및 각 VMware vSAN 클러스터에 적용할 수 있는 BYOL키가 있습니다.
* 선택사항으로 이미 적용되지 않은 경우 VMware vCenter Server 및 각 VMware vSphere Enterprise Plus 라이센스에 적용하는 데 사용 가능한 BYOL키가 있습니다.

## Hybridity Bundle을 제거하는 프로시저
{: #vc_hybrid_deletingbundle-procedure}

1. **관리자**로 Hybridity Bundle을 제거할 VMware vSphere Web Client에 로그인하십시오.
2. **홈 > 관리 > 라이센싱 > 라이센스**를 클릭하십시오.
3. **자산** 탭을 클릭하십시오.
4. VMware NSX BYOL을 설치하려면 다음 단계를 완료하십시오.
   1. **솔루션** 탭을 클릭하십시오.
   2. NSX for vSphere를 선택한 후 **모든 조치 > 라이센스 지정**을 클릭하십시오.
   3. **추가** 아이콘을 클릭하고 라이센스 키를 입력하십시오. **다음**을 클릭하십시오.
   4. 라이센스에 대한 이름을 입력하고 **다음**을 클릭하십시오. **완료**를 클릭하여 라이센스를 추가하십시오.
   5. 새 라이센스 키를 선택하십시오.
   6. 적용되는 라이센스와 대체되는 라이센스 둘 다에 대한 전체 라이센스 키를 기록해 두십시오.

   이 프로시저에서 나중에 사용할 수 있도록 라이센스 세부사항이 있어야 합니다.
   {:important}
   7. **완료**를 클릭하여 라이센스를 지정하십시오.
5. VMware vSAN BYOL을 설치하려면 다음 단계를 완료하십시오.
   1. **클러스터** 탭을 클릭하십시오.
   2. vCenter Server 인스턴스와 연관된 각 vSAN 클러스터에 대해 다음 단계를 완료하십시오.
    1. vSAN 클러스터를 선택한 후 **모든 조치 > 라이센스 지정**을 클릭하십시오.
    2. **추가** 아이콘을 클릭하고 라이센스 키를 입력하십시오. **다음**을 클릭하십시오.
    3. 라이센스에 대한 이름을 입력하고 **다음**을 클릭하십시오. **완료**를 클릭하여 라이센스를 추가하십시오.
    4. 새 라이센스 키를 선택하십시오.
    5. 적용되는 라이센스와 대체되는 라이센스 둘 다에 대한 전체 라이센스 키 및 클러스터 이름을 기록해 두십시오.

이 프로시저에서 나중에 사용할 수 있도록 라이센스 세부사항이 있어야 합니다.
    {:important}
    6. **완료**를 클릭하여 라이센스를 지정하십시오.
6. 선택적으로 VMware vCenter Server BYOL을 설치하려면 다음 단계를 완료하십시오.
   1. **vCenter Server 시스템** 탭을 클릭하십시오.
   2. vCenter Server를 선택한 후 **모든 조치 > 라이센스 지정**을 클릭하십시오.
   3. **추가** 아이콘을 클릭하고 라이센스 키를 입력하십시오. **다음**을 클릭하십시오.
   4. 라이센스에 대한 이름을 입력하고 **다음**을 클릭하십시오. **완료**를 클릭하여 라이센스를 추가하십시오.
   5. 새 라이센스 키를 선택하십시오.
   6. 적용되는 라이센스와 대체되는 라이센스 둘 다에 대한 전체 라이센스 키를 기록해 두십시오.

   이 프로시저에서 나중에 사용할 수 있도록 라이센스 세부사항이 있어야 합니다.
   {:important}

   7. **완료**를 클릭하여 라이센스를 지정하십시오.
7. 선택적으로 VMware vSphere Enterprise Plus BYOL을 설치하려면 다음 단계를 완료하십시오.
  1. **호스트** 탭을 클릭하십시오.
  2. vCenter Server 인스턴스와 연관된 각 클러스터에 대해 다음 단계를 완료하거나 vCenter Server와 연관된 모든 클러스터에 동일한 라이센스가 적용되고 있다면 동시에 모든 클러스터에 대해 완료하십시오.
    1. 클러스터와 연관된 모든 호스트를 선택하고 **모든 조치 > 라이센스 지정**을 클릭하십시오.
    2. **추가** 아이콘을 클릭하고 라이센스 키를 입력하십시오. **다음**을 클릭하십시오.
    3. 라이센스에 대한 이름을 입력하고 **다음**을 클릭하십시오. **완료**를 클릭하여 라이센스를 추가하십시오.
    4. 새 라이센스 키를 선택하십시오.
    5. 적용되는 라이센스와 대체되는 라이센스 둘 다에 대한 전체 라이센스 키 및 클러스터 이름을 기록해 두십시오.

    이 프로시저에서 나중에 사용할 수 있도록 라이센스 세부사항이 있어야 합니다. 모든 클러스터에서 라이센스 키가 동일하지 않은 경우, 각 라이센스 키와 연관된 클러스터 이름을 기록해야 합니다.
    {:important}

    6. **완료**를 클릭하여 라이센스를 지정하십시오.
8. 임대 라이센스를 제거하십시오.
   1. **라이센스** 탭을 클릭하십시오.
   2. 4 - 7단계에서 대체한 라이센스를 선택하십시오.
   3. **라이센스 제거** 아이콘을 클릭하십시오.
9. 임대 라이센스의 비용을 취소하려면 지원 티켓을 열고 다음 정보를 제공하십시오.
  * vCenter Server 인스턴스의 이름
  * vCenter Server 인스턴스와 연관된 ID
  * 이 프로시저에서 설치한 BYOL 라이센스 키의 목록입니다. 적용 가능한 경우 vSphere 및 vSAN 클러스터에 대한 라이센스 키가 있는 인스턴스 및 클러스터 이름을 제공하십시오.
  * 이 프로시저에서 제거한 임대 라이센스 키의 목록입니다. 적용 가능한 경우 vSphere 및 vSAN 클러스터에 대한 라이센스 키가 있는 인스턴스 및 클러스터 이름을 제공하십시오.

  IBM 지원 센터 및 운영 팀에서는 {{site.data.keyword.cloud_notm}} 인프라 계정의 vCenter 관리 계층에 액세스하여 Hybridity Bundle 임대 라이센스 비용을 취소하기 전에 임대 라이센스가 제거되었는지 확인합니다.
  {:note}

## 관련 링크
{: #vc_hybrid_deletingbundle-related}

* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [vCenter Server with Hybridity Bundle 인스턴스 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

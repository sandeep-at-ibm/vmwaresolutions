---

copyright:

  years:  2016, 2019

lastupdated: "2018-10-30"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Federal 인스턴스 보호

배치된 VMware Federal 인스턴스를 보안하려면, 즉 인스턴스에 지속적으로 액세스하기 위해 열린 관리 연결을 제거하려면 다음 프로시저를 완료하십시오.

## 시작하기 전에

배치된 VMware Federal 인스턴스 보안의 결과를 이해하려면 다음 정보를 검토하십시오.

* 이 프로시저를 완료하기 전에 환경에 필요할 수 있는 모든 인증 정보를 기록하고 저장하십시오. 환경의 모든 인증 정보가 {{site.data.keyword.vmwaresolutions_full}} 데이터베이스에서 지워지며 보안 조치가 시작되고 나면 검색할 수 없습니다.
* 전체 인스턴스 삭제를 제외하고 보안 조치가 시작되고 나면 다른 모든 관리 기능이 사용 안함으로 설정됩니다.

## VMware Federal 인스턴스를 보호하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 보호할 인스턴스를 클릭하십시오.
3. **vCenter 콘솔** 옆에 있는 오버플로우 메뉴 아이콘을 클릭하십시오.
4. **인스턴스 보호**를 클릭하십시오.
5. **확인**을 클릭하여 자동화에서 인스턴스의 연결 끊기를 확인하십시오.

  이 단계를 완료하기 전에 **시작하기 전에** 섹션에 있는 정보를 검토했는지 확인하십시오.
  {:note}

6. 사용자 환경에서 공개용 관리 서비스 VMware NSX ESG(Edge Services Gateway)를 제거하고 선택적으로 자동화 중에 배치된 클라이언트 관리 ESG를 제거하십시오.
7. IBM 자동화에서 사용하는 모든 계정의 비밀번호와 키를 재설정하십시오. 자세한 정보는 [How can I secure my environment to remove access by IBM automation and support?](https://developer.ibm.com/answers/questions/452354/how-can-i-secure-my-environment-to-remove-access-b/)를 참조하십시오.

## 결과

인스턴스의 상태가 **수정 중**으로 변경됩니다.

인스턴스가 보호되면 인스턴스의 상태가 **보호됨**으로 변경되고 인스턴스 특성 및 배치 히스토리만 사용할 수 있습니다.

### 관련 링크

* [VMware Federal on {{site.data.keyword.cloud_notm}} 개요](vc_fed_overview.html)
* [VMware Federal 인스턴스 주문](vc_fed_orderinginstance.html)
* [VMware Federal 인스턴스 보기](vc_fed_viewinginstance.html)
* [VMware Federal 인스턴스 삭제](vc_fed_deletinginstance.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)

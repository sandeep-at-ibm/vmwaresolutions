---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-27"

---

# VMware Federal 인스턴스 삭제

VMware Federal 인스턴스에서 주문한 컴포넌트를 릴리스하려면 인스턴스를 삭제하십시오.

VMware Federal 인스턴스를 삭제하는 경우 다음 컴포넌트가 순차적으로 릴리스됩니다.

1. 지원 및 서비스 요금
2. VMware 제품 라이센스
3. ESXi 서버
4. 서브넷

리소스 종속성으로 인해 인스턴스 삭제 시 인스턴스의 컴포넌트가 즉시 릴리스되지 않습니다. 예를 들어, {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 발생하는 {{site.data.keyword.cloud}} 인프라로 ESXi 서버가 완전히 재확보될 때까지 서브넷을 삭제할 수 없습니다. {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 일반적으로 청구 주기는 30일이고 서브넷이 삭제되며 인스턴스 삭제가 완료됩니다.

**주의**: 삭제된 인스턴스에 대한 {{site.data.keyword.cloud_notm}} 인프라 비용 청구 주기 종료 시 비용이 청구됩니다.

## 배치된 인스턴스 페이지에서 인스턴스를 삭제하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 삭제할 인스턴스를 찾으십시오.
3. **조치** 열에서 삭제 아이콘을 클릭하십시오.
   인스턴스의 상태가 **삭제 중**으로 변경됩니다. 인스턴스가 삭제되면 인스턴스의 컴포넌트가 릴리스되고 인스턴스의 상태가 **삭제됨**으로 변경됩니다.
4. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스 레코드를 제거하려면 다음 단계를 완료하십시오.
   1. **조치** 열에서 삭제 아이콘을 다시 클릭하십시오.
   2. **인스턴스 삭제** 창에서 **확인**을 클릭하십시오.

## 인스턴스 세부사항 페이지에서 인스턴스를 삭제하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 삭제할 인스턴스를 클릭하십시오.
3. **vCenter 콘솔** 옆에 있는 오버플로우 메뉴 아이콘을 클릭하고 **인스턴스 삭제**를 클릭하십시오.
   인스턴스의 상태가 **삭제 중**으로 변경됩니다. 인스턴스가 삭제되면 인스턴스의 컴포넌트가 릴리스되고 인스턴스의 상태가 **삭제됨**으로 변경됩니다.
4. {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 인스턴스 레코드를 제거하려면 다음 단계를 완료하십시오.
   1. **vCenter 콘솔** 옆에 있는 오버플로우 메뉴 아이콘을 다시 클릭하고 **인스턴스 삭제**를 클릭하십시오.
   2. **인스턴스 삭제** 창에서 **확인**을 클릭하십시오.

### 관련 링크

* [VMware Federal on {{site.data.keyword.cloud_notm}} 개요](vc_fed_overview.html)
* [VMware Federal 인스턴스 주문](vc_fed_orderinginstance.html)
* [VMware Federal 인스턴스 보호](vc_fed_securinginstance.html)
* [VMware Federal 인스턴스 보기](vc_fed_viewinginstance.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)

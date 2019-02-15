---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-24"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud 인스턴스에 대한 인증서 추가, 보기 및 삭제

KMIP for VMware on {{site.data.keyword.cloud}} 인스턴스가 준비되면 인증서를 추가해야 합니다. 인증서가 더 이상 필요하지 않은 경우 인스턴스에서 삭제하십시오.

## KMIP for VMware on IBM Cloud 인스턴스에 인증서를 추가하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **KMIP for VMware on IBM Cloud 인스턴스** 테이블을 아래로 스크롤하여 인증서를 추가할 인스턴스를 클릭하십시오.
3. **추가**를 클릭하십시오.
4. **클라이언트 SSL 인증서 추가** 창에 인증서 이름 및 컨텐츠를 입력하십시오.

   인증서 이름은 선택한 인스턴스 내에서 재사용될 수 없습니다. 인증서 컨텐츠는 유효해야 하고 BEGIN CERTIFICATE 및 END CERTIFICATE 태그가 포함되어야 하며, 인증서는 인스턴스가 배치된 선택한 지역에서 재사용될 수 없습니다.
   {:note}
5. **추가**를 클릭하십시오.

## KMIP for VMware on IBM Cloud 인스턴스에 대한 인증서를 보는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **KMIP for VMware on IBM Cloud 인스턴스** 테이블을 아래로 스크롤하여 인증서를 보려는 인스턴스를 클릭하십시오.
3. **클라이언트 SSL 인증서** 섹션 아래에서 추가된 인증서의 목록을 보십시오.
4. 특정 인증서의 컨텐츠를 보려면 **다운로드**를 클릭하십시오.

## KMIP for VMware on IBM Cloud 인스턴스에서 인증서를 삭제하는 프로시저

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
2. **KMIP for VMware on IBM Cloud 인스턴스** 테이블을 아래로 스크롤하여 인증서를 삭제할 인스턴스를 클릭하십시오.
3. **클라이언트 SSL 인증서** 테이블에서 삭제할 인증서를 찾고 **삭제** 아이콘을 클릭하십시오.

   클라이언트는 데이터 또는 백업 데이터의 암호화 및 복호화를 목적으로 한 모든 키의 액세스 권한을 즉시 잃게 됩니다. 클라이언트가 다시 액세스 권한을 얻으려면 클라이언트 SSL 인증서를 다시 추가해야 합니다.
   {:note}

### 관련 링크

* [KMIP for VMware on IBM Cloud 인스턴스 보기](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [KMIP for VMware on IBM Cloud 인스턴스 주문](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html)
* [KMIP for VMware on IBM Cloud 인스턴스 삭제](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [활성 트래커 이벤트](/docs/services/vmwaresolutions/vmonic/at-events.html)

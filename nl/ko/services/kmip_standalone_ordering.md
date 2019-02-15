---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

# KMIP for VMware on IBM Cloud 인스턴스 주문

서비스 및 인스턴스의 유연한 관리를 위해 VMware 인스턴스에 액세스하지 않고 KMIP for VMware on {{site.data.keyword.cloud}} 인스턴스를 주문할 수 있습니다.

## 시작하기 전에

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정](/docs/services/vmwaresolutions/vmonic/useraccount.html)을 참조하십시오.
*  [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 설치 시 고려사항](/docs/services/vmwaresolutions/services/kmip_standalone_considerations.html)의 모든 고려사항을 검토했습니다.

## KMIP for VMware on IBM Cloud 인스턴스 주문

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **시작하기**를 클릭하십시오.
2. **추가 서비스 주문** 영역에서 **KMIP for VMware on IBM Cloud**를 클릭하십시오.
3. **KMIP for VMware on IBM Cloud** 페이지에서 필요에 따라 서비스 설정을 구성하십시오.
4. **프로비저닝**을 클릭하십시오.

## KMIP for VMware on IBM Cloud 서비스 구성

이 서비스를 주문할 때 다음 설정을 제공하십시오.

### 인스턴스 이름

KMIP for VMware {{site.data.keyword.cloud_notm}} 인스턴스의 이름을 지정하십시오.

### 서비스 지역

KMIP for VMware {{site.data.keyword.cloud_notm}} 인스턴스를 호스팅할 {{site.data.keyword.cloud_notm}} 지역을 선택하십시오.

{{site.data.keyword.cloud_notm}}는 서비스가 사용 가능한 각 지역에서 고가용성 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 엔드포인트를 유지보수합니다.

표 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 엔드포인트 지역

|지역         |엔드포인트               |
|:---------------|:-----------------------|
|독일        |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|도쿄          | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
|미국 남부       |  <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### 서비스 ID의 API 키

IBM Key Protect Service 인스턴스에 액세스하는 데 사용되는 {{site.data.keyword.cloud_notm}} 서비스 ID의 API 키를 입력하십시오.

### Key Protect 인스턴스

**검색**을 클릭하여 사용 가능한 IBM Key Protect Service 인스턴스의 목록을 가져온 후 키 관리에 사용할 인스턴스를 선택하십시오.

### 고객 루트 키

**검색**을 클릭하여 선택된 IBM Key Protect 인스턴스에 저장된 고객 루트 키를 가져오십시오.

## 결과

인스턴스 주문이 자동으로 시작됩니다. 주문이 처리 중이라는 확인을 받은 후 인스턴스 세부사항을 보고 주문의 상태를 확인할 수 있습니다.

인스턴스를 사용할 준비가 되면 인스턴스의 상태가 **설치됨**으로 변경되고 이메일로 알림을 받습니다.

## 수행할 작업

주문한 KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스에 대한 클라이언트 인증서를 추가하십시오. 자세한 정보는 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스에 대한 인증서 추가, 보기 및 삭제](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html)를 참조하십시오.

### 관련 링크

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 보기](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 삭제](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [활성 트래커 이벤트](/docs/services/vmwaresolutions/vmonic/at-events.html)

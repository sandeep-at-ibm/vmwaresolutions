---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud 개요

KMIP for VMware on {{site.data.keyword.cloud}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware에서 사용되는 암호화 키를 관리하기 위해 고가용성 서비스를 연중무휴로 제공합니다. 이 서비스는 고객이 암호화 키를 작성, 검색, 활성화, 취소 및 영구 삭제할 수 있도록 하는 런타임 기능을 제공합니다. 또한 클라이언트 인증 정보와 암호화 키 간의 연관을 유지보수하는 관리 기능도 제공합니다.

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스는 VMware 인스턴스와 연관되지 않고 독립형 서비스로 사용할 수 있습니다. 서비스의 각 인스턴스는 하나 이상의 Cloud Foundation 인스턴스, vCenter Server 인스턴스 또는 vSphere 클러스터를 제공할 수 있습니다.

**참고**: 이 릴리스에서 KMIP for VMware on {{site.data.keyword.cloud_notm}}는 vSphere 암호화로만 제한됩니다. 

## KMIP for VMware on IBM Cloud의 기술 스펙

다음 스펙이 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 포함되어 있습니다.

* VMware 호환 가능 KMIP(Key Management Interoperability Protocol)
* 관리 서비스
* 전세계 여러 지리적 지역에서 사용 가능
* 고가용성을 위해 각 지역에 제공되는 두 개의 KMIP 서비스 엔드포인트

## KMIP for VMware on IBM Cloud 인스턴스 설치 시 고려사항

KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스를 설치하기 전에 다음 고려사항을 검토하십시오.

* KMIP for VMware on {{site.data.keyword.cloud_notm}}는 암호화 키를 작성, 암호화 및 복호화하는 데 IBM Key Protect for {{site.data.keyword.cloud_notm}} 서비스를 사용합니다. 따라서 KMIP for VMware on {{site.data.keyword.cloud_notm}}를 설치하기 전에 다음 항목을 확인하십시오.
   * KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스를 호스팅할 {{site.data.keyword.cloud_notm}} 지역에서 사용 가능한 서비스를 주문했습니다. 자세한 정보는 [서비스 프로비저닝](/docs/services/key-protect/provision.html)을 참조하십시오.
   * [서비스 ID 작성](/docs/iam/serviceid.html)의 단계에 따라 {{site.data.keyword.cloud_notm}} 서비스 ID를 작성했습니다. 이 서비스 ID는 작성한 Key Protect 서비스 인스턴스에 액세스하는 데 사용됩니다.
   * 서비스 ID에 다음 액세스 레벨을 부여했습니다.
      * 플랫폼 액세스 레벨: IBM Key Protect 인스턴스에 대한 뷰어 권한
      * 서비스 액세스 레벨: IBM Key Protect 인스턴스에 대한 관리자 권한
   * 작성된 서비스 ID에 대한 API 키가 있습니다. 이 키는 서비스를 주문할 때 필요합니다.
   * [루트 키 작성](/docs/services/keymgmt/keyprotect_create_root.html)의 단계를 따르거나 [IBM Key Protect](https://cloud.ibm.com/apidocs/key-protect)의 RESTful API를 사용하여 Key Protect 사용자 인터페이스에서 하나 이상의 고객 루트 키(CRK)를 작성했습니다.

     **중요:** CRK 없이는 서비스를 주문할 수 없습니다. 기존 키 자료를 사용하여 CRK를 작성하는 방법을 사용하고 작성하는 키 자료를 백업하는 것이 좋습니다. 이렇게 하면 CRK를 저장하기 위해 IBM Key Protect가 적용된 데이터 센터에 장애가 발생하는 경우 키를 복구할 수 있습니다.
* {{site.data.keyword.cloud_notm}} 인프라 계정이 VRF(Virtual Routing and Forwarding) 및 서비스 엔드포인트에 대한 연결에 사용 가능한지 확인하십시오. 자세한 정보는 다음을 참조하십시오.
   * [IBM Cloud의 VRF(Virtual Routing and Forwarding) 개요](/docs/infrastructure/direct-link/vrf-on-ibm-cloud.html)
   * [IBM Cloud CLI를 사용하여 서비스 엔드포인트에 사용할 계정 사용](/docs/services/service-endpoint/enable-servicepoint.html#getting-started)
* 사설 연결만 지원되므로, vCenter Server에서 KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스의 엔드포인트까지 네트워크를 연결하기 위해 vCenter Server에 방화벽 또는 SNAT 규칙을 구성할 필요가 없습니다.

자세한 정보는 [KMIP for VMware on IBM Cloud 솔루션 아키텍처](/docs/services/vmwaresolutions/archiref/kmip/overview.html)를 참조하십시오.

## KMIP for VMware on IBM Cloud 인스턴스 삭제 시 고려사항

암호화된 백업을 포함하여 KMIP for VMware on IBM Cloud 서비스로 보호되는 모든 데이터는 서비스를 제거한 후 복호화될 수 없습니다.

### 관련 링크

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 주문](/docs/services/vmwaresolutions/services/kmip_standalone_ordering.html)
* [KMIP for VMware on IBM Cloud 인스턴스에 대한 인증서 추가, 보기 및 삭제](/docs/services/vmwaresolutions/services/kmip_standalone_addingdeletingcert.html)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 보기](/docs/services/vmwaresolutions/services/kmip_standalone_viewing.html)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 삭제](/docs/services/vmwaresolutions/services/kmip_standalone_deleting.html)
* [활성 트래커 이벤트](/docs/services/vmwaresolutions/vmonic/at-events.html)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic/trbl_support.html)

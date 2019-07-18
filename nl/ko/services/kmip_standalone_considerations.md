---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-28"

keywords: KMIP for VMware, KMIP stand-alone, tech specs KMIP

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# KMIP for VMware on IBM Cloud 개요
{: #kmip_standalone_considerations}

KMIP for VMware on {{site.data.keyword.cloud}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware에서 사용되는 암호화 키를 관리하기 위해 고가용성 서비스를 연중무휴로 제공합니다. 이 서비스는 고객이 암호화 키를 작성, 검색, 활성화, 취소 및 영구 삭제할 수 있도록 하는 런타임 기능을 제공합니다. 또한 클라이언트 인증 정보와 암호화 키 간의 연관을 유지보수하는 관리 기능도 제공합니다.

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스는 VMware 인스턴스와 연관되지 않고 독립형 서비스로 사용할 수 있습니다. 서비스의 각 인스턴스는 하나 이상의 vCenter Server 인스턴스 또는 vSphere 클러스터를 제공할 수 있습니다.

## KMIP for VMware on IBM Cloud의 기술 스펙
{:#technical-specifications-for-kmip-for-vmware-on-ibm-cloud}

다음 스펙이 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 포함되어 있습니다.

* VMware 호환 가능 KMIP(Key Management Interoperability Protocol)
* 두 개의 관리 서비스: [IBM Key Protect for {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/catalog/services/key-protect){:external} 및 [{{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services){:external}
* 전세계 여러 지리적 지역에서 사용 가능
* 고가용성을 위해 각 지역에 제공되는 두 개의 KMIP 네트워크 서비스 엔드포인트

## KMIP for VMware on IBM Cloud 인스턴스 설치 시 고려사항
{: #kmip_standalone_considerations-install}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스를 설치하기 전에 다음 고려사항을 검토하십시오.

* KMIP for VMware on {{site.data.keyword.cloud_notm}}는 IBM Key Protect for {{site.data.keyword.cloud_notm}}(Key Protect) 서비스 또는 {{site.data.keyword.cloud_notm}} Hyper Protect Crypto Services(HPCS) 서비스를 사용하여 암호화 키를 작성하고, 암호화 및 복호화합니다. 따라서 KMIP for VMware on {{site.data.keyword.cloud_notm}}를 설치하기 전에 다음 항목을 확인하십시오.
   * KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스를 호스팅할 {{site.data.keyword.cloud_notm}} 지역에서 사용 가능한 Key Protect 또는 HPCS 서비스 인스턴스를 주문했습니다.
      * Key Protect 인스턴스 작성에 대한 자세한 정보는 [서비스 프로비저닝](/docs/services/key-protect?topic=key-protect-provision)을 참조하십시오.
      * HPCS 인스턴스 작성에 대한 자세한 정보는 [서비스 프로비저닝](/docs/services/hs-crypto?topic=hs-crypto-provision#provision)을 참조하십시오. HPCS 서비스 프로비저닝 외에 HPCS가 키 관련 기능을 제공할 수 있도록 [암호화 인스턴스도 초기화](/docs/services/hs-crypto?topic=hs-crypto-initialize-hsm#initialize-hsm)해야 합니다.
   * [서비스 ID 작성](/docs/iam?topic=iam-serviceids)의 단계에 따라 {{site.data.keyword.cloud_notm}} 서비스 ID를 작성했습니다. 이 서비스 ID는 작성한 Key Protect 또는 HPCS 서비스 인스턴스에 액세스하는 데 사용됩니다.
   * 서비스 ID에 다음 액세스 레벨을 부여했습니다.
      * 플랫폼 액세스 레벨: Key Protect 또는 HPCS 서비스 인스턴스에 대한 뷰어 권한
      * 서비스 액세스 레벨: Key Protect 또는 HPCS 서비스 인스턴스에 대한 관리자 권한
   * 작성된 서비스 ID에 대한 API 키가 있습니다. 이 키는 서비스를 주문할 때 필요합니다.
   * Key Protect 또는 HPCS의 GUI 또는 API를 사용하여 하나 이상의 고객 루트 키(CRK)를 작성했습니다.
      * Key Protect GUI 또는 API를 사용한 루트 키 작성에 대한 자세한 정보는 [루트 키 작성](/docs/services/key-protect?topic=key-protect-create-root-keys#create-root-keys) 또는 [IBM Key Protect API](https://cloud.ibm.com/apidocs/key-protect){:external}를 참조하십시오.
      * HPCS GUI 또는 API를 사용한 루트 키 작성에 대한 자세한 정보는 [루트 키 작성](/docs/hs-crypto/get-started?topic=hs-crypto-create-root-keys) 또는 [IBM Cloud Hyper Protect Crypto Services API](https://cloud.ibm.com/apidocs/hs-crypto){:external}를 참조하십시오.

     **중요:** CRK 없이는 서비스를 주문할 수 없습니다. 기존 키 자료를 사용하여 CRK를 작성하는 방법을 사용하고 작성하는 키 자료를 백업하는 것이 좋습니다. 이렇게 하면 CRK를 저장하기 위해 Key Protect 또는 HPCS가 적용된 데이터 센터에 장애가 발생하는 경우 키를 복구할 수 있습니다.
* {{site.data.keyword.cloud_notm}} 인프라 계정이 VRF(Virtual Routing and Forwarding) 및 서비스 엔드포인트에 대한 연결에 사용 가능한지 확인하십시오. 자세한 정보는 다음을 참조하십시오.
   * [IBM Cloud의 VRF(Virtual Routing and Forwarding) 개요](/docs/infrastructure/direct-link?topic=direct-link-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud)
   * [IBM Cloud CLI를 사용하여 서비스 엔드포인트를 사용할 계정 사용](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)
* 사설 연결만 지원되므로, vCenter Server에서 KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스의 엔드포인트까지 네트워크를 연결하기 위해 vCenter Server에 방화벽 또는 SNAT 규칙을 구성할 필요가 없습니다.

자세한 정보는 [KMIP for VMware on IBM Cloud 솔루션 아키텍처](/docs/services/vmwaresolutions/archiref/kmip?topic=vmware-solutions-kmip-overview)를 참조하십시오.

## KMIP for VMware on IBM Cloud 인스턴스 삭제 시 고려사항
{: #considerations-when-deleting-kmip-for-vmware-on-ibm-cloud-instances}

암호화된 백업을 포함하여 KMIP for VMware on IBM Cloud 서비스로 보호되는 모든 데이터는 서비스를 제거한 후 복호화될 수 없습니다.

## 관련 링크
{: #kmip_standalone_considerations-related}

* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering)
* [KMIP for VMware on IBM Cloud 인스턴스에 대한 인증서 추가, 보기 및 삭제](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 보기](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [KMIP for VMware on {{site.data.keyword.cloud_notm}} 인스턴스 삭제](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [활성 트래커 이벤트](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

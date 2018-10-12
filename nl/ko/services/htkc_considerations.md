---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-11"

---

# HyTrust KeyControl on IBM Cloud 개요

HyTrust KeyControl on {{site.data.keyword.cloud}} 서비스는 키 스토리지, 키 분배, 키 순환, 키 취소를 포함하는 암호화 키의 라이프사이클을 자동화 및 간소화하여 암호화된 워크로드의 관리를 간소화합니다. 엔터프라이즈는 FIPS 140-2 준수 암호화를 사용하여 암호화 키를 규모에 맞게 쉽게 관리할 수 있습니다. 

**가용성:** 이 서비스는 vSphere 6.5를 실행하며 V2.5 이상 릴리스로 배치된(또는 이 릴리스로 업그레이드된) 인스턴스에서만 사용할 수 있습니다.

## HyTrust KeyControl on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### HyTrust KeyControl 어플라이언스

* CPU: 2개의 vCPU
* RAM: 8GB
* 디스크: 통합 클러스터의 vSAN에 상주하는 20GB VMDK
* 네트워크: 관리용으로 지정된 VLAN 지원 사설 포터블 네트워크에 배치됨

### 고가용성

기본적으로, 두 개의 KeyControl 어플라이언스가 클러스터링된 활성-활성 구성에 배치됩니다.

선택적으로, 두 개의 KeyControl 어플라이언스를 클러스터링되지 않은 독립형 구성에 배치하도록 지정할 수 있습니다.

### 라이센스 및 요금

각각의 인스턴스 설치를 위해 HyTrust KeyControl 라이센스가 주문됩니다.

## HyTrust KeyControl on IBM Cloud 제거 시 고려사항

HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 KeyContol 사용에서 모든 클라이언트를 분리했는지 확인하십시오. 서비스를 제거하면 키가 삭제될 수 있으며 VM에 액세스하지 못하게 될 수 있습니다.

### 관련 링크

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 주문](htkc_ordering.html)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 관리](managinghtkc.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

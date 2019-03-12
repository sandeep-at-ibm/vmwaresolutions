---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# HyTrust KeyControl on IBM Cloud 개요
{: #hytrust-keycontrol-on-ibm-cloud-overview}

HyTrust KeyControl on {{site.data.keyword.cloud}} 서비스는 암호화된 워크로드의 관리를 간소화합니다. 이 서비스는 키 스토리지, 키 분배, 키 순환 및 키 취소를 포함하는 암호화 키의 라이프사이클을 자동화하고 간소화합니다. 엔터프라이즈는 FIPS 140-2 준수 암호화를 사용하여 암호화 키를 규모에 맞게 쉽게 관리할 수 있습니다.

이 서비스는 vSphere 6.5를 실행 중이며 V2.5 이상에 배치된(또는 업그레이드된) 인스턴스에 대해서만 사용할 수 있습니다. 설치되어 있는 현재 HyTrust KeyControl 버전은 4.2입니다.
{:note}

## HyTrust KeyControl on IBM Cloud의 기술 스펙
{: #htkc_considerations-specs}

다음 컴포넌트가 주문되고 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### HyTrust KeyControl 어플라이언스
{: #htkc_considerations-appliance}

* CPU: 2개의 vCPU
* RAM: 8GB
* 디스크: 통합 클러스터의 vSAN에 상주하는 20GB VMDK
* 네트워크: 관리용으로 지정된 VLAN 지원 사설 포터블 네트워크에 배치됨

### 고가용성
{: #htkc_considerations-ha}

기본적으로, 두 개의 KeyControl 어플라이언스가 클러스터링된 활성-활성 구성에 배치됩니다.

선택적으로, 두 개의 KeyControl 어플라이언스를 클러스터링되지 않은 독립형 구성에 배치하도록 지정할 수 있습니다.

### 라이센스 및 요금
{: #htkc_considerations-licenses}

각각의 인스턴스 설치를 위해 HyTrust KeyControl 라이센스가 주문됩니다.

## HyTrust KeyControl on IBM Cloud 제거 시 고려사항
{: #htkc_considerations-remove}

HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 KeyContol 사용에서 모든 클라이언트를 분리했는지 확인하십시오. 서비스를 제거하면 키가 삭제될 수 있으며 VM에 액세스하지 못하게 될 수 있습니다.

## 관련 링크
{: #htkc_considerations-related}

* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_ordering)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

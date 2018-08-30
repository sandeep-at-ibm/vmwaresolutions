---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust CloudControl on IBM Cloud 개요

HyTrust CloudControl on {{site.data.keyword.cloud}} 서비스는 보안 표준에 대한 준수를 강제하고 제어하며, 상세한 역할 기반 액세스 제어(RBAC), 승인 및 감사 기능을 제공합니다. HyTrust DataControl과 결합되면, 서비스는 가상 머신 및 워크로드 데이터가 특정 지역, 클러스터 또는 {{site.data.keyword.CloudDataCent_notm}} 내의 ESXi 서버를 벗어나지 않도록 할 수 있습니다.

**가용성:** 이 서비스는 vSphere 6.5를 실행하며 V2.3 이상 릴리스로 배치된(또는 이 릴리스로 업그레이드된) 인스턴스에서만 사용할 수 있습니다.

## HyTrust CloudControl on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### HyTrust CloudControl 어플라이언스

* CPU: 4 vCPU
* RAM: 16GB
* 디스크: 통합 클러스터의 vSAN에 상주하는 70GB VMDK
* 네트워크: 관리용으로 지정된 VLAN-지원 사설 포터블 네트워크에 배치됨

### 고가용성

2개의 CloudControl 어플라이언스가 활성-수동 구성에 배치됩니다.

### 라이센스 및 요금

호스트별 라이센스: HyTrust CloudControl 라이센스는 환경의 각 호스트마다 주문됩니다.

## HyTrust CloudControl on IBM Cloud 제거 시 고려사항

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에, **루트 비밀번호 보관**이 구성된 경우 이를 사용 안함으로 설정했는지 확인하고, HyTrust CloudControl에서 보호된 호스트를 모두 삭제했는지 확인하십시오.

### 관련 링크

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 주문](htcc_ordering.html)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 관리](managinghtcc.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

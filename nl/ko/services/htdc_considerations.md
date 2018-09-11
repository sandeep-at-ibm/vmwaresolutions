---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-27"

---

# HyTrust DataControl on IBM Cloud 개요

HyTrust DataControl on {{site.data.keyword.cloud}}는 워크로드를 해당 라이프사이클 동안 보호하기 위해 통합된 키 관리 기능을 포함한 강력한 암호화를 제공합니다. 이 서비스는 운영 체제 레벨 및 데이터 레벨 모두에서 암호화를 제공할 수 있으며, 이는 워크로드 내의 모든 디렉토리, 폴더 및 파일이 암호화되거나 복호화될 수 있음을 의미합니다.

**가용성:** 이 서비스는 vSphere 6.5를 실행하며 V2.3 이상 릴리스로 배치된(또는 이 릴리스로 업그레이드된) 인스턴스에서만 사용할 수 있습니다.

## HyTrust DataControl on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 HyTrust DataControl on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### HyTrust DataControl 어플라이언스
* CPU: 2개의 vCPU
* RAM: 8GB
* 디스크: 통합 클러스터의 vSAN에 상주하는 20GB VMDK
* 네트워크: 관리용으로 지정된 VLAN 지원 사설 포터블 네트워크에 배치됨

### 고가용성
2개의 DataControl 어플라이언스가 활성-활성 구성에 배치됩니다.

### 라이센스 및 요금

호스트별 라이센스: HyTrust DataControl 라이센스는 환경의 각 호스트마다 주문됩니다.

## HyTrust DataControl on IBM Cloud 제거 시 고려사항

HyTrust DataControl on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 DataControl로부터 모든 디스크를 암호화하거나 백업했는지 확인하십시오. 서비스를 제거하면 키가 삭제될 수 있으며 VM에 액세스하지 못하게 될 수 있습니다.

### 관련 링크

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 주문](htdc_ordering.html)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 관리](managinghtcc.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

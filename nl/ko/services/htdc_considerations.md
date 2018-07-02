---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# HyTrust DataControl on IBM Cloud 개요

HyTrust DataControl on {{site.data.keyword.cloud}}는 워크로드를 해당 라이프사이클 동안 보호하기 위해 통합된 키 관리 기능을 포함한 강력한 암호화를 제공합니다. 이 서비스는 운영 체제 레벨 및 데이터 레벨 모두에서 암호화를 제공할 수 있으며, 이는 워크로드 내의 모든 디렉토리, 폴더 및 파일이 암호화되거나 복호화될 수 있음을 의미합니다.

**가용성:** 이 서비스는 vSphere 6.5를 실행하며 V2.3 이상 릴리스로 배치되거나 V2.3 릴리스로 업그레이드된 인스턴스에서만 사용할 수 있습니다.

## HyTrust DataControl on IBM Cloud의 컴포넌트

HyTrust DataControl(HTDC) 어플라이언스의 고가용성(HA) 쌍이 활성-활성 모드로 기본 클러스터에 배치됩니다. HTDC 어플라이언스에는 워크로드에 HyTrust KeyControl 기능을 제공할 수 있도록 라이센스가 부여됩니다.

각 HTDC 어플라이언스 쌍은 NSX Manager, vCenter Server Appliance 및 Platform Services Controller와 같은 관리 가상 머신(VM)에 지정된 포터블 서브넷과 동일한 서브넷에 배치됩니다. 어플라이언스는 {{site.data.keyword.cloud_notm}} 백엔드 고객 라우터(BCR)를 통해 라우팅되며 관리 VM 서브넷과 연관된 게이트웨이가 지정됩니다. 또한 어플라이언스는 기본 클러스터의 기본 스토리지에 배치됩니다.

## HyTrust DataControl on IBM Cloud 제거 시 고려사항

HyTrust DataControl on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 DataControl로부터 모든 디스크를 암호화하거나 백업했는지 확인하십시오. 서비스를 제거하면 키가 삭제될 수 있으며 VM에 액세스하지 못하게 될 수 있습니다.

## 관련 링크

* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 주문](htdc_ordering.html)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 관리](managinghtcc.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

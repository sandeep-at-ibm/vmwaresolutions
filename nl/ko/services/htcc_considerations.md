---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# HyTrust CloudControl on IBM Cloud 개요

HyTrust CloudControl on {{site.data.keyword.cloud}} 서비스는 보안 표준에 대한 준수를 강제하고 제어하며, 상세한 역할 기반 액세스 제어(RBAC), 승인 및 감사 기능을 제공합니다. HyTrust DataControl과 결합되면, 서비스는 가상 머신 및 워크로드 데이터가 특정 지역, 클러스터 또는 {{site.data.keyword.CloudDataCent_notm}} 내의 ESXi 서버를 벗어나지 않도록 할 수 있습니다.

**가용성:** 이 서비스는 vSphere 6.5를 실행하며 V2.3 이상 릴리스로 배치되거나 V2.3 릴리스로 업그레이드된 인스턴스에서만 사용할 수 있습니다.

## HyTrust CloudControl on IBM Cloud의 컴포넌트

HyTrust CloudControl(HTCC) 어플라이언스의 고가용성(HA) 쌍이 활성-수동 모드로 기본 클러스터에 배치됩니다.

각 HTCC 어플라이언스 쌍은 NSX Manager, vCenter Server Appliances 및 Platform Services Controller와 같은 관리 가상 머신(VM)에 대해 지정된 개인용 포터블 서브넷과 동일한 서브넷에 배치됩니다. 어플라이언스의 쌍은 vSphere 호스트의 프록시, vCenter Server Appliance 및 인스턴스의 NSX Manager 역할을 합니다. 따라서 사용자는 IBM Cloud에서 지정한 실제 IP 주소(RIP) 대신 관리자가 지정한 공개된 IP(PIP)를 통해 vSphere 호스트, vCenter Server Appliance 및 NSX Manager에 액세스합니다.

HTCC 어플라이언스는 Microsoft Active Directory와 통합하여 역할 기반 액세스 제어를 강제 수행합니다.

## HyTrust CloudControl on IBM Cloud 제거 시 고려사항

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 **루트 비밀번호 보관**을 사용 안함으로 설정하고 구성된 경우 CloudControl에서 보호된 호스트를 모두 삭제했는지 확인하십시오.

## 관련 링크

* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 주문](htcc_ordering.html)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 관리](managinghtcc.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [HyTrust 웹 사이트](https://www.hytrust.com/)

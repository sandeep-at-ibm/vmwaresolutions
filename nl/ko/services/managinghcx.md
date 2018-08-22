---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-19"

---

# VMware HCX on IBM Cloud 관리

## HCX on IBM Cloud 관리 콘솔에 액세스

HCX on {{site.data.keyword.cloud}} 서비스를 관리하려면 다음을 수행하여 HCX Cloud 콘솔 또는 HCX Manager 관리 콘솔에 액세스해야 합니다.
1. {{site.data.keyword.cloud_notm}} 인프라 VPN 또는 점프 서버를 사용하여 HCX Manager 가상 어플라이언스(HCX Manager)의 IP 주소에 대한 액세스를 허용하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 HCX on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 IP 주소를 찾을 수 있습니다.
2. HCX Cloud 콘솔에 액세스하려면 HCX on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 **HCX Cloud 콘솔 보기**를 클릭한 후 vCenter Server 신임 정보를 사용하여 로그인하십시오.
3. HCX Manager 관리 콘솔에 액세스하려면 HCX on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 **HCX Manager 관리 콘솔 보기**를 클릭한 후 동일한 서비스 세부사항 페이지에 나열된 HCX Manager 신임 정보를 사용하여 로그인하십시오.

자세한 정보는 [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_hybrid_addingremovingservices.html)를 참조하십시오.

## HCX on IBM Cloud에 업데이트 적용

HCX on {{site.data.keyword.cloud_notm}}는 VMware Hybrid Cloud Extension 기술의 최신 테스트된 빌드를 통해 배치됩니다. VMware는 이러한 빌드에 대한 업데이트를 정기적으로 제공하며, 여기에는 중요 수정사항 및 새 기능이 포함됩니다. 이러한 빌드는 온프레미스 HCX 설치를 포함한 HCX on {{site.data.keyword.cloud}} 설치로 자동으로 푸시됩니다.

사용자 환경에 푸시된 유지보수 수정사항을 적용하려면 온프레미스 데이터 센터 및 vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 인스턴스에서 HCX Manager 관리 콘솔을 사용해야 합니다.

예상하는 빌드 업데이트가 표시되지 않거나 HCX에 문제점이 있거나 최신 HCX 빌드를 시스템으로 즉시 푸시하려는 경우 [IBM 지원 센터에 문의](../vmonic/trbl_support.html)의 단계를 수행하여 지원 티켓을 여십시오.

### 관련 링크

* [HCX on {{site.data.keyword.cloud_notm}} 개요](hcx_considerations.html)
* [HCX 용어집](hcx_glossary.html)
* [VMware Hybrid Cloud Extension 개요](https://cloud.vmware.com/vmware-hcx)
* [VMware Hybrid Cloud Extension 문서](https://hcx.vmware.com/#vm-documentation)

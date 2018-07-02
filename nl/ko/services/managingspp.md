---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# IBM Spectrum Protect Plus on IBM Cloud 관리

## IBM Spectrum Protect Plus 관리 콘솔에 액세스

IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud}} 서비스를 관리하려면 다음 단계를 완료하여 IBM Spectrum Protect Plus 관리 콘솔에 액세스해야 합니다.
1. {{site.data.keyword.cloud_notm}} 인프라 VPN 또는 점프 서버를 사용하여 IBM Spectrum Protect Plus 가상 머신의 IP 주소에 대한 액세스를 허용하십시오. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}에 대한 서비스 세부사항 페이지에서 IP 주소를 찾을 수 있습니다.
2. IBM Spectrum Protect Plus 관리 콘솔에 액세스하려면 IBM Spectrum Protect Plus on {{site.data.keyword.cloud}}에 대한 서비스 세부사항 페이지에서 **IBM Spectrum Protect Plus 콘솔 보기**를 클릭한 후 동일한 서비스 세부사항 페이지에 나열된 신임 정보를 사용하여 로그인하십시오.

## IBM Spectrum Protect Plus on IBM Cloud에 대한 수정사항 적용

사용자는 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스를 최신 버전으로 유지보수해야 합니다. [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} Support](https://www.ibm.com/mysupport/s/topic/0TO50000000IQWtGAO/spectrum-protect-plus) 페이지에서 필수 업데이트를 다운로드할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)

## IBM Spectrum Protect Plus 가상 머신의 운영 체제 업데이트

IBM Spectrum Protect Plus 가상 머신의 운영 체제를 업데이트하려면 **루트** 사용자로 로그인해야 합니다. **루트** 사용자 비밀번호는 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}에 대한 서비스 세부사항 페이지에서 찾을 수 있는 비밀번호와 동일합니다.

## IBM Spectrum Protect Plus on IBM Cloud가 설치된 인스턴스에 대한 관리 컴포넌트 백업 및 복원

 **참고**: 다음 정보는 V2.3 이상으로 배치된(또는 이러한 버전으로 업그레이드된) 인스턴스의 IBM Spectrum Protect Plus 설치에 적용됩니다. V2.2 인스턴스의 경우 이 서비스는 워크로드 가상 머신에 대한 데이터 보호만 제공합니다.

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스는 최대 7개의 복원 지점을 설정하여 다음 관리 컴포넌트를 매일 백업하도록 자동으로 실행되는 관리 백업 작업으로 사전 구성되어 있습니다.
* VMware vCenter Server
* PSC(Platform Services Controller)
* IBM CloudDriver
* **Cloud Foundation 인스턴스에만 해당**: VMware SDDC Manager
* **HA AD/DNS를 사용하는 vCenter Server 인스턴스에만 해당**: AD/DNS의 고가용성 쌍

관리 컴포넌트에 장애가 발생하는 경우에는 [IBM 지원 센터에 문의](../vmonic/trbl_support.html)하여 티켓을 열어 관리 컴포넌트를 이전 백업으로 복원하도록 요청할 수 있습니다.

## 관련 링크

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 개요](spp_considerations.html)
* [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)
* [IBM Spectrum Protect Plus 문서](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# Veeam on IBM Cloud 관리

서비스가 인스턴스에 배치된 후 RDP를 통해 Veeam 콘솔에 액세스하여 환경에 있는 모든 가상 머신의 백업 및 복원(관리 컴포넌트의 백업 및 복원 포함)을 관리할 수 있습니다. 또한 Veeam 웹 사이트에서 Veeam 업데이트를 다운로드하고 설치하여 서비스를 업그레이드할 수도 있습니다.

이전 V1.8 이전의 릴리스에 배치된 인스턴스의 경우, Veeam on {{site.data.keyword.cloud}} 서비스를 사용하려면 인스턴스에서 기존 Veeam VSI를 대체해야 합니다. 자세한 정보는 이 주제의 _V1.8 이전 인스턴스의 Veeam VSI를 Veeam on IBM Cloud로 대체_ 절을 참조하십시오. 

## RDP를 사용하여 Veeam 콘솔에 액세스

Veeam on {{site.data.keyword.cloud_notm}} 서비스를 관리하려면 다음 단계를 완료하여 Veeam 콘솔에 액세스하십시오. 
1. RDP(Remote Desktop Protocol)를 사용하여 Windows IP 주소에 연결하십시오. 
2. 관리자 신임 정보를 사용하여 Windows 콘솔에 로그인하십시오. 
3. 관리자 신임 정보를 사용하여 Windows 콘솔에서 Veeam 콘솔에 액세스하십시오. 

Windows IP 주소 및 관리자 신임 정보는 Veeam on {{site.data.keyword.cloud_notm}} 서비스 세부사항 페이지에서 찾을 수 있습니다. 

자세한 정보는 다음 주제를 참조하십시오.
* [Cloud Foundation 인스턴스에 대한 서비스 주문, 보기 및 제거](../sddc/sd_addingremovingservices.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](../vcenter/vc_addingremovingservices.html)

## Veeam on IBM Cloud가 설치된 인스턴스에 대한 관리 컴포넌트 백업 및 복원

Veeam on {{site.data.keyword.cloud_notm}} 서비스에는 자동으로 실행되는 관리 백업 작업이 사전 구성되어 있습니다. 이 작업은 최대 14개의 복원 지점을 설정하여 관리 컴포넌트를 매일 백업합니다. 

Veeam 콘솔을 사용하여 수동으로 관리 컴포넌트도 백업할 수 있습니다.

V1.8 이상 릴리스로 배치된(또는 이러한 릴리스로 업그레이드된) 인스턴스의 경우에는 환경에 대한 구성 변경사항이 자동으로 백업되지 않습니다. 그러므로 환경의 구성을 변경하기 전에 Veeam 콘솔에서 사전 구성된 관리 백업 작업을 실행하여 수동으로 관리 컴포넌트를 백업하는 것이 좋습니다. 수동 백업에 대한 자세한 정보는 [Veeam 기술 지시사항](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}을 참조하십시오. 

관리 컴포넌트에서 실패가 발생하는 경우 Veeam 콘솔을 사용하여 관리 컴포넌트를 이전 백업으로 복원할 수 있습니다. 수동 복원에 대한 자세한 정보는 [Veeam 기술 지시사항]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}을 참조하십시오. 

## Veeam on IBM Cloud에 업데이트 적용

사용자는 Veeam이 항상 최신 버전으로 업데이트되어 있도록 유지보수해야 합니다. Veeam을 최신 버전으로 업그레이드하려면 Veeam 웹 사이트에서 Veeam 업데이트를 다운로드하여 Veeam VSI에 복사한 후 설치하십시오. 

## V1.8 이전 인스턴스의 Veeam VSI를 Veeam on IBM Cloud로 대체

관리 컴포넌트와 워크로드를 모두 백업할 수 있는 Veeam on {{site.data.keyword.cloud_notm}} 서비스는 관리 컴포넌트의 백업을 목적으로만 V1.8 이전 릴리스에서 VMware Cloud Foundation 및 VMware vCenter Server로 통합된 이전 Veeam VSI를 대체합니다.

이 변경으로 인해, 인스턴스 세부사항 페이지의 이전 **백업 및 복원** 탭이 제거되었으며 인스턴스의 복원 지점은 더 이상 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 사용할 수 없게 되었습니다. 그러나 V1.8 이전 인스턴스의 Veeam VSI는 계속 작동합니다. 

복원에 대한 지원을 받으려면 {{site.data.keyword.cloud_notm}} 지원 티켓을 작성해야 합니다. 또한 V1.8 이전 인스턴스의 Veeam VSI 라이센스가 2017년 10월 14일에 만료되었습니다. 그러므로 이전 Veeam VSI를 새 Veeam on {{site.data.keyword.cloud_notm}} 서비스로 대체해야 합니다.

다음 단계를 완료하십시오.
1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭한 후 대상 인스턴스를 클릭하십시오.
2. 인스턴스 세부사항 페이지에서 **업데이트 및 패치** 탭을 클릭하십시오. 인스턴스를 V1.8 릴리스로 업그레이드했는지 확인하십시오.
3. **서비스** 탭을 클릭하십시오.
4. **서비스 추가** 탭에서 Veeam on {{site.data.keyword.cloud_notm}} 서비스를 설치하십시오.

새 Veeam on {{site.data.keyword.cloud_notm}} 서비스가 배치되고 관리 컴포넌트의 백업이 완료된 후 {{site.data.keyword.cloud_notm}} 지원 티켓을 작성하여 계정에서 기존 Veeam VSI를 제거할 수 있습니다. 그런 다음 IBM 지원 센터는 기존 Veeam VSI 및 스토리지를 식별하고 삭제합니다.

## 관련 링크

* [Veeam on {{site.data.keyword.cloud_notm}} 개요](veeam_considerations.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam.com 웹 사이트](https://www.veeam.com/)
* [Veeam 기술 문서](https://www.veeam.com/documentation-guides-datasheets.html)

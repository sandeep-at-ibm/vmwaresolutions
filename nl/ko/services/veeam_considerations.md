---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-07"

---

# Veeam on IBM Cloud 개요

Veeam on {{site.data.keyword.cloud}} 서비스는 엔터프라이즈가 고가용성을 달성할 수 있도록 VMware 하이퍼바이저와 직접 원활하게 통합합니다. 이 서비스는 애플리케이션 및 데이터에 대한 복구 지점 및 시간 목표를 제공할 수 있습니다. 복구 지점 및 시간 목표는 구성이 완료된 후 15분 내에 제공될 수 있습니다. 이 서비스를 사용하여 Veeam 콘솔에서 인프라에 대한 모든 가상 머신의 백업 및 복원을 모두 직접 제어할 수 있습니다.

**가용성**: 이 서비스는 V1.8 이상 릴리스에 배치된 인스턴스에서만 사용 가능합니다.

## Veeam on IBM Cloud의 컴포넌트

다음 컴포넌트가 주문되고 Veeam on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.
* 기본 사설 IP 주소 및 1GbE 인터페이스가 포함된 하나의 Windows Server 2016 VSI
* {{site.data.keyword.cloud_notm}} 서비스 주문 시 선택하는 크기 및 성능의 Endurance 블록 스토리지

## Veeam on IBM Cloud 설치 시 고려사항

* 서비스가 다음 관리 컴포넌트를 백업합니다.
  - VMware vCenter Server
  - PSC(Platform Services Controller)
  - IBM CloudDriver
  - **Cloud Foundation 인스턴스에만 해당**: VMware SDDC Manager
  - **HA AD/DNS를 사용하는 vCenter Server 인스턴스에만 해당**: AD/DNS 서버의 고가용성 쌍

* ESXi 서버의 구성은 Veeam on {{site.data.keyword.cloud_notm}} 서비스로 백업되지 않습니다.

* 기본적으로, NSX Controller 및 NSX Edge의 구성은 최대 14개의 복원 지점으로 NSX Manager를 사용하여 매일 백업됩니다. NSX 구성의 전체 복원의 경우, NSX 구성의 백업이 {{site.data.keyword.vmwaresolutions_full}}의 내부에 있는 스토리지에 저장되므로 {{site.data.keyword.cloud_notm}} 지원 티켓을 작성해야 합니다. NSX Manager를 사용한 NSX 구성 백업 관리에 대한 자세한 정보는 [VMware 기술 지시사항](https://pubs.vmware.com/NSX-6/index.jsp#com.vmware.nsx.admin.doc/GUID-72EFCAB1-0B10-4007-A44C-09D38CD960D3.html)을 참조하십시오.
* 스토리지의 저장소와 Veeam 서버는 원래의 팟(Pod) 및 데이터 센터에 있습니다. 이러한 이유로, 원격 클러스터에 대한 백업 오퍼레이션의 성능이 저하될 수 있습니다.

## Veeam on IBM Cloud 제거 시 고려사항

Veeam on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에, 이 서비스를 제거하면 모든 백업(관리 VM의 백업 포함)이 중지되고 모든 이전 백업이 삭제되는 점(삭제는 되돌릴 수 없음)에 유의하십시오. 이후에 관리 VM이 손상되면 복원할 수 없습니다.

## 관련 링크

* [Veeam on {{site.data.keyword.cloud_notm}} 주문](veeam_ordering.html)
* [Veeam on {{site.data.keyword.cloud_notm}} 관리](managingveeam.html)
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](managing_veeam_services.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Veeam 웹 사이트](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

---

copyright:

  years:  2016, 2018

lastupdated: "2018-12-14"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V2.7의 릴리스 정보
{: #relnotes_v27}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## SAP 인증 6140 서버 지원

V2.7 릴리스부터 다음의 새 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 모델을 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 및 VMware vSphere on {{site.data.keyword.cloud_notm}} 인스턴스 및 클러스터의 배치에 사용할 수 있습니다.
* 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 192GB RAM
* 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.2GHz / 384GB RAM
* 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 768GB RAM

자세한 정보는 다음의 *{{site.data.keyword.baremetal_short_sing}} 설정* 섹션을 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## 추가 서비스에 대한 업데이트

### IBM Cloud Private Hosted

이제 {{site.data.keyword.cloud_notm}} Private Hosted 서비스는 이제 VMware vCenter Server with Hybridity Bundle 인스턴스 및 V2.5 이상 릴리스에 배치되는(또는 업그레이드되는) VMware vCenter Server 인스턴스에 사용 가능합니다. 이제 vCenter Server 인스턴스 또는 vCenter Server with Hybridity Bundle 인스턴스를 포함된 서비스와 함께 주문할 수 있습니다. 초기 배치 이후에 기존 vCenter Server 인스턴스 또는 vCenter Server with Hybridity Bundle 인스턴스에 서비스를 추가할 수도 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [{{site.data.keyword.cloud_notm}} Private Hosted 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)
* [{{site.data.keyword.cloud_notm}} Private Hosted 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)

### Mission Critical VMware on IBM Cloud

이제 Mission Critical VMware on {{site.data.keyword.cloud_notm}} 서비스는 V2.7 이상 릴리스에 배치되거나 업그레이드된 인스턴스에 사용할 수 있습니다.

Mission Critical VMware on {{site.data.keyword.cloud_notm}}는 다중 구역 클라우드 아키텍처를 제공하여 엔터프라이즈에서 클라우드 애플리케이션에 대한 가동 중단 시간을 방지하도록 지원하고 클라우드 지역 내에서 장애 복구를 자동화합니다. 이 클라우드 아키텍처를 사용하면, 대부분의 VMware 클라이언트가 온프레미스 환경 또는 경쟁 클라우드 플랫폼에서 달성할 수 있는 것보다 더 높은 가용성 및 장애 복구 성공률을 달성할 수 있습니다.

자세한 정보는 [Mission Critical VMware on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-mcv_overview)를 참조하십시오.

### F5 on IBM Cloud

이제 F5 on {{site.data.keyword.cloud_notm}} 서비스를 주문할 때 F5에서 공용 네트워크 또는 사설 네트워크를 통해 프록시 서버에 라이센스를 적용할지를 선택할 수 있습니다. 자세한 정보는 [F5 on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)을 참조하십시오.

### FortiGate Virtual Appliance on IBM Cloud

2018년 3분기에 Fortinet에서 구독 번들을 변경했습니다. 자세한 정보는 [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)을 참조하십시오.

V2.7 이상에 배치되는 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스의 경우 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스, FortiOS 6.0.3이 프로비저닝됩니다.

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}를 주문할 때 FortiGuard에서 공용 네트워크 또는 프록시 서버를 사용하는 사설 네트워크를 통해 라이센스 및 보안 업데이트를 적용하도록 할지 선택할 수 있습니다. 자세한 정보는 [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_ordering)을 참조하십시오.

### Zerto on IBM Cloud 서비스 컴포넌트 업데이트

V2.7 이상에 배치되는 Zerto on {{site.data.keyword.cloud_notm}} 서비스의 경우 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스, Zerto Virtual Replication 6.0 update 3이 프로비저닝됩니다. 자세한 정보는 [Zerto on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)를 참조하십시오.

### IBM Cloud Activity Tracker와 KMIP for VMware on IBM Cloud 통합

이제 VMware 인스턴스 이벤트 외에도 키 작성, 키 삭제 및 키 액세스 등의 KMIP for VMware on {{site.data.keyword.cloud_notm}}에 대한 이벤트가 {{site.data.keyword.cloud_notm}} Activity Tracker 인스턴스와 통합됩니다. KMIP for WMware on {{site.data.keyword.cloud_notm}}에 대한 자세한 정보는 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services/kmip_considerations.html)를 참조하십시오.

### KMIP for VMware on IBM Cloud - 더 이상 사용되지 않음

(2018년 12월 14일에 업데이트됨) KMIP for VMware on {{site.data.keyword.cloud_notm}}의 현재 버전은 더 이상 사용되지 않습니다. 자세한 정보는 [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)하십시오.
{:deprecated}

## 새로 작성되고 업데이트된 문서

### 참조 아키텍처 문서

이제 다음 기술 문서는 사용자 문서의 *참조서* 섹션에서 사용할 수 있습니다.

* [NSX Edge Services Gateway 솔루션 아키텍처](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx_overview)
* [VMware Update Manager 안내서](/docs/services/vmwaresolutions/archiref/vum?topic=vmware-solutions-vum-intro)
* [vCenter Server 네트워킹 안내서](/docs/services/vmwaresolutions/archiref/vcsnsxt?topic=vmware-solutions-vcsnsxt-intro)
* [vCenter Server 및 {{site.data.keyword.cloud_notm}} Private 안내서](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [vCenter Server 및 IBM Kubernetes Service 안내서](/docs/services/vmwaresolutions/archiref/vcsiks?topic=vmware-solutions-vcsiks-intro)
* [VMware 및 Skate Advisor Concept Car 안내서](/docs/services/vmwaresolutions/archiref/vcscar?topic=vmware-solutions-vcscar-intro)
* [VMware - Stock Trader의 현대화 과정](/docs/services/vmwaresolutions/archiref/vcscontent?topic=vmware-solutions-vcscontent-modjourney)

## 사용자 인터페이스 업데이트 및 개선사항

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* 인스턴스를 주문할 때 {{site.data.keyword.baremetal_short_sing}} 설정에 대한 CPU 모델과 RAM을 지정하는 **사용자 정의됨** 탭은 서버 선택 시 도움이 되도록 서버 유형을 기반으로 **Skylake** 및 **Broadwell** 탭으로 나뉩니다.
* Bare Metal Server 구성에 대한 **사전 구성됨** 옵션은 더 이상 사용할 수 없습니다.
* **유형** 열은 이제 vCenter Server, vCenter Server with Hybridity Bundle 및 vCenter Limited Test Drive 인스턴스를 식별하기 위해 **배치된 인스턴스** 페이지의 **vCenter Server 인스턴스** 테이블에 포함됩니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

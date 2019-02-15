---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud 인프라 계정에 대한 요구사항

{{site.data.keyword.vmwaresolutions_full}}를 사용하여 인스턴스를 주문하려면 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 있어야 합니다. 인스턴스에 주문된 컴포넌트의 비용이 해당 {{site.data.keyword.cloud_notm}} 계정으로 청구됩니다.

{{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정을 이전에는 IBM SoftLayer 계정이라고 했습니다.
{:note}

## IBM Cloud 인프라 계정에 대한 권한

사용 중인 {{site.data.keyword.cloud_notm}} 인프라 계정에는 인스턴스의 컴포넌트를 주문하고 사용자를 대신해 오퍼레이션을 수행할 수 있는 특정 권한이 있어야 합니다. 권한 요구사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 주문 중인 모든 유형의 인스턴스와 서비스에 적용할 수 있습니다.

권한 부여된 사용자는 {{site.data.keyword.slportal}}에서 {{site.data.keyword.cloud_notm}} 인프라 계정에 대한 권한을 확인하고 업데이트할 수 있습니다. 자세한 정보는 [사용자의 고객 포털 권한 편집](/docs/customer-portal/cpmanuserprof.html#cp_editusercpperm){:new_window}을 참조하십시오.

표 1. {{site.data.keyword.cloud_notm}} 인프라 계정에 대한 필수 권한

|권한         |세부사항                                 |
|:------------------ |:--------------------------------------- |
|서버 추가 |이 권한은 VMware ESXi가 실행되는 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}를 주문하고 인스턴스 구성, 유지보수 및 지원 오퍼레이션에 사용되는 가상 서버를 매시간 프로비저닝하는 데 필요합니다. |
|서버 취소 |이 권한은 VMware ESXi가 실행되는 {{site.data.keyword.baremetal_short}}를 릴리스하고 재확보하는 데 필요합니다. 인스턴스를 삭제하면 올바른 종속성 순서로 주문된 컴포넌트가 자동으로 릴리스됩니다. |
|Virtual Server 세부사항 보기 |이 권한은 주문 유효성 검증 및 자동화된 구성에 필요한 서버 프로비저닝 세부사항을 검색하는 데 필요합니다. |
|스토리지 추가 |이 권한은 인스턴스에 대한 백업 스토리지 및 공유 스토리지를 주문하는 데 필요합니다. |
|스토리지 관리 |이 권한은 인스턴스에 대한 백업 스토리지 및 공유 스토리지를 관리하는 데 필요합니다. |
|Hardware Firewall |이 권한은 Fortinet on {{site.data.keyword.cloud_notm}} 서비스가 설치된 경우 이에 대한 방화벽 로그 파일 및 설정을 편집하거나 보는 데 필요합니다. |
| 공용 네트워크 포트가 포함된 컴퓨팅 추가 |이 권한은 공용 네트워크 포트가 포함된 하드웨어 및 VSI(Virtual Server Instances)를 주문하는 데 필요합니다. |
|IP 주소 추가 |이 권한은 사용자 대신 포터블 사설 서브넷 범위를 주문하는 데 필요하며, 이는 vSphere 클러스터에서 실행되는 가상 머신을 관리하는 데 필요합니다. 더 많은 서비스가 인스턴스에 추가되는 경우 VMware ESXi 서버에 포터블 사설 IP 주소를 지정하여 대역폭을 분리하고 할당하십시오. |
|티켓 추가 |이 권한은 사용자 대신 서비스 티켓을 여는 데 필요합니다. 티켓은 복원 오퍼레이션을 시작하고 문제가 발견될 때 자동으로 문제 해결 프로세스를 시작하기 위해 작성되었을 수 있습니다. |
|티켓 편집 |이 권한은 사용자 대신 작성되는 서비스 티켓을 편집하는 데 필요합니다. |
|티켓 보기 |이 권한은 {{site.data.keyword.cloud_notm}} 인프라 프로비저닝 지연 및 문제점에 대해 인스턴스의 컴포넌트와 관련된 서비스 티켓을 모니터링하는 데 필요합니다. |
|하드웨어 세부사항 보기 |이 권한은 주문 유효성 검증 및 자동화된 구성에 필요한 하드웨어 세부사항을 검색하는 데 필요합니다. |
|라이센스 보기 |이 권한은 인스턴스에서 사용되는 라이센스를 검색하고 유효성 검증하는 데 필요합니다. |
|비밀번호 보기 |이 권한은 주문된 VSI를 관리하는 데 필요합니다. |
| 서버 모니터링 관리 |이 권한은 주문하는 데 필요하지 않지만 인스턴스에서 VMware ESXi 서버가 실행되는 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}의 모니터링 상태를 검색하고 유효성 검증하는 데 필요합니다. |

## VRF(Virtual Routing and Forwarding) 요구사항

{{site.data.keyword.cloud_notm}} 인프라 계정은 VRF 계정이어야 합니다. 또는 VRF 계정이 아니면 VLAN Spanning이 사용으로 설정되어야 합니다. 비-VRF 계정에서 VRF 계정으로의 변환에 대한 자세한 정보는 [IBM Cloud의 VRF 개요](/docs/infrastructure/direct-link/vrf-on-ibm-cloud.html)를 참조하십시오. 

## 비-VRF 계정에 대한 VLAN Spanning

비-VRF {{site.data.keyword.cloud_notm}} 인프라 계정을 사용 중이면 VLAN Spanning이 사용으로 설정되어야 합니다. 비-VRF 계정에 대해 VLAN Spanning이 사용으로 설정되지 않으면 VMware 가상화 환경의 다양한 컴포넌트가 서로 간에 통신할 수 없습니다. 

계정에서 VLAN Spanning을 사용으로 설정하려면 [VLAN Spanning](/docs/infrastructure/vlans/vlan-spanning.html){:new_window}을 참조하십시오. 

### 관련 링크

* [Cloud Foundation 인스턴스에 대한 요구사항](/docs/services/vmwaresolutions/sddc/sd_planning.html)
* [vCenter Server 인스턴스에 대한 요구사항](/docs/services/vmwaresolutions/vcenter/vc_planning.html)
* [사용자 계정 및 설정](/docs/services/vmwaresolutions/vmonic/useraccount.html)
* [IBM Cloud의 VRF 개요](/docs/infrastructure/direct-link/vrf-on-ibm-cloud.html)

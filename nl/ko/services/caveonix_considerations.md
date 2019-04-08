---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud의 Caveonix RiskForesight 개요
{: #caveonix_considerations}

{{site.data.keyword.cloud}}의 Caveonix RiskForesight 서비스는 위협으로부터 보호하고 업계 또는 정부 규제를 충족하도록 하기 위해 사전 모니터링 및 자동화된 방어 제어를 통해 사이버 및 규제 준수 위험을 관리하는 데 도움이 될 수 있습니다.

이 서비스는 V2.9 이상 릴리스에 배치된 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 인스턴스에만 사용 가능합니다.
{:note}

## IBM Cloud의 Caveonix RiskForesight 기술 스펙
{: #caveonix_considerations-specs}

다음 컴포넌트가 주문되고 {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스에 포함됩니다.

### vCenter 리소스
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32GB
* 디스크: 80GB

### 네트워크
{: #caveonix_considerations-tech-specs-network}

64개의 IP 주소가 있는 데디케이티드 사설 서브넷이 주문됩니다.

### 라이센스 및 요금
{: #caveonix_considerations-tech-specs-license-fee}

Caveonix RiskForesight 라이센스 키는 서비스의 각 인스턴스에 대해 주문됩니다.

## IBM Cloud의 Caveonix RiskForesight 설치 시 고려사항
{: #caveonix_considerations-install}

{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스를 설치하기 전에 서비스 인스턴스의 기본 클러스터에 있는 CPU 및 메모리가 Caveonix RiskForesight 가상 머신에 충분한지 확인하십시오.

## IBM Cloud의 Caveonix RiskForesight 제거 시 고려사항
{: #caveonix_considerations-remove}

{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스를 제거하기 전에 다음 고려사항을 검토하십시오.
* {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스를 제거해도 Caveonix RiskForesight 라이센스가 취소되지는 않습니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 **리소스** 페이지에 있는 **Caveonix RiskForesight 라이센스** 테이블에서 Caveonix RiskForesight 라이센스를 삭제해야 합니다.
* 서비스를 제거하면 {{site.data.keyword.vmwaresolutions_short}} 자동화는 배치되어 있는 단일 "일체형" Caveonix VM 및 이를 위해 주문된 데디케이티드 사설 서브넷만 삭제합니다. 따라서 다음에 유의하십시오.
   * Caveonix VM을 여러 VM으로 확장한 경우, 이러한 추가 VM은 제거되지 않습니다.
   * 추가 VM에서 데디케이티드 사설 서브넷의 IP 주소를 사용한 경우에는 기능을 계속 수행하도록 이러한 VM에 새 IP 주소를 지정해야 합니다.
   * {{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 서비스가 설치되어 있는 vCenter Server 인스턴스 A를 삭제할 경우 vCenter Server 인스턴스 B의 서비스에 대해 주문된 데디케이티드 사설 서브넷의 IP 주소를 사용했다면 vCenter Server  인스턴스 A 삭제 시에 데디케이티드 사설 서브넷이 취소됩니다.

## 관련 링크
{: #caveonix_considerations-related}

* [{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [{{site.data.keyword.cloud_notm}}의 Caveonix RiskForesight 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)

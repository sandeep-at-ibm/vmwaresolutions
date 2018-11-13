---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-25"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# FortiGate Virtual Appliance on IBM Cloud 개요

FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 서비스는 가상 인프라 내에서 중요한 보안 제어를 구현하여 위험을 줄일 수 있는 FortiGate Virtual Appliances 쌍을 사용자 환경에 배치합니다.

필요에 따라 이 서비스의 다중 인스턴스를 설치할 수 있습니다. SSH를 통해 FortiOS Web Client 또는 명령 인터페이스를 사용하여 이 서비스를 관리할 수 있습니다.

이 서비스는 V2.0 이상 릴리스에 배치된 인스턴스에 대해서만 사용 가능합니다. 설치된 현재 서비스 버전은 6.0.3입니다.
{:note}

## FortiGate Virtual Appliance on IBM Cloud의 기술 스펙

다음 컴포넌트가 주문되고 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### 가상 머신

* 모든 옵션에는 가상 머신의 고가용성(HA) 쌍이 포함됨
* 배치 크기와 구독 유형에 따라 가상 머신당 2, 4 또는 8개 vCPU
* 배치 크기와 구독 유형에 따라 가상 머신당 4, 6 또는 12GB RAM

### 고가용성

2개의 가상 머신이 배치되어 있으며 HA 또는 VRRP(Virtual Router Redundancy Protocol) 구성을 위해 준비되어 있습니다.

### 네트워킹

FortiGate® 콘솔에 대한 액세스는 사설 관리 네트워크를 통해 제공됩니다.

### 라이센스 및 요금

각 가상 머신에 대한 라이센스 요금은 선택된 배치 크기와 월별 구독 라이센스 모델에 따라 각 청구 주기에 적용됩니다.

서비스 설치 후에는 라이센싱 레벨을 변경할 수 없습니다. 라이센싱 레벨을 변경하려면 기존 서비스를 제거하고 다른 라이센싱 옵션을 사용하여 서비스를 다시 설치해야 합니다.
{:important}

## FortiGate Virtual Appliance on IBM Cloud 설치 시 고려사항

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 다음 고려사항을 검토하십시오.
* FortiGate 가상 머신(VM)은 기본 클러스터에만 배치됩니다.
* 2개의 FortiGate VM이 네트워크 통신의 데이터 플레인에 있으며 반드시 이에 대해 여전히 리소스를 사용할 수 있어야 하므로, 이러한 VM에 대한 100% 의 CPU 및 RAM 역시 예약되어 있습니다.

  단일 FortiGate VM에 대한 CPU 및 RAM 예약을 계산하려면 다음 공식을 사용하십시오.
   * `CPU 예약 = ESXi 서버의 CPU 속도 * vCPU 수`
   * `RAM 예약 = RAM 크기`
* FortiGate Virtual Appliances의 HA 쌍을 인스턴스에 배치하는 경우, 라이센스 활성화와 최신 보안 정책 및 컨텐츠 확보를 위해 인스턴스와 공용 네트워크 간의 아웃바운드 HTTPS 통신을 허용하도록 SNAT 및 방화벽 규칙이 관리 NSX Edge Services Gateway(ESG)에서 FortiGate Virtual Appliances의 정적 라우트와 함께 정의됩니다.
* 서비스 설치 후 라이센스 레벨을 변경할 수 없습니다. 라이센스 레벨을 변경하려면 기존 서비스를 제거한 후 다른 라이센스 옵션을 선택하여 서비스를 다시 설치해야 합니다.
* FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}가 실패하지 않으려면 다음 요구사항을 충족해야 합니다.
   * 개별 서버에 VM을 유지하는 연관관계 방지 규칙으로 두 FortiGate VM이 최소 두 개의 활성 ESXi 서버를 배치할 수 있습니다.
   * CPU 및 RAM이 100% 예약된 상태로 각 ESXi 서버에 하나의 FortiGate VM을 호스팅할 수 있도록 두 개의 활성 서버에 사용할 수 있는 충분한 리소스가 있습니다.
   * VMware vSphere HA에는 CPU 및 RAM이 100% 상태로 두 FortiGate VM을 호스팅할 수 있는 충분한 리소스가 있습니다.

  이러한 요구사항이 있으므로, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}에 필요한 공간은 주의깊게 계획되어야 합니다. 필요한 경우에는 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}를 주문하기 전에 1 - 2개의 ESXi 서버를 인스턴스에 추가하거나, 장애 복구를 위한 vSphere HA CPU 예약을 줄이십시오(또는 둘 다 수행).

## FortiGate Virtual Appliance on IBM Cloud 주문 예

2.10GHz의 16개 코어(각 128GB RAM 포함)로 구성된 두 개의 ESXi 서버와 VMware vCenter Server **소형** 인스턴스를 주문합니다. FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}의 경우 배치 크기 및 구독 라이센스 모델에 **대형**(8개의 vCPU / 12GB RAM)을 선택합니다.

이 경우, 각 서버에 단일 FortiGate VM이 필요합니다.
* 2.1GHz * 8개의 vCPU = 16.8GHz CPU
* 12GB RAM

두 FortiGate VM에 총 33.6GHz CPU 및 24GB RAM이 필요합니다.

각 ESXi 서버에는 16개의 코어 * 2.1GHz = 33.6GHz의 용량이 있습니다. 그러므로 두 서버가 활성이고 각 서버에서 최소 16.8GHz CPU와 12GB RAM을 사용할 수 있는 경우 처음 두 가지 요구사항이 충족됩니다.

그러나 기본적으로 vSphere HA는 두 개의 ESXi 서버로 초기에 배치된 vCenter Server 인스턴스의 장애 복구를 위해 50%의 CPU 및 RAM을 예약하므로 다음 용량만 사용 가능합니다.

`50% 2개 * 16개의 코어 * 2.1GHz = 33.6GHz 사용 가능`

VMware vCenter Server, VMware NSX Controller 또는 VMware NSX Edge 등의 다른 워크로드가 ESXi 서버에 존재하므로, 이러한 리소스를 사용하여 세 번째 요구사항을 충족시킬 수 없습니다. 이는 두 FortiGate VM에 대해 33.6GHz의 CPU와 24GB의 RAM이 필요하기 때문입니다.

이 경우, 두 FortiGate VM에 대해 충분한 리소스를 확보하기 위해 하나 이상의 ESXi 서버를 환경에 추가하고 vShpere HA 장애 복구 예약을 적절히 업데이트하지 않으면 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 설치가 실패할 수 있습니다.

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스를 실행하는 데 추가 리소스가 필요한 경우에는 이 서비스를 설치하기 전에 더 많은 ESXi 서버를 추가할 수 있습니다.

## FortiGate Virtual Appliance on IBM Cloud 제거 시 고려사항

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 기존 FortiGate Virtual Appliances의 구성이 올바르게 제거되었는지 확인하십시오. 특히, FortiGate Virtual Appliances를 통하는 대신 FortiGate Virtual Appliances 주변에서 네트워크 트래픽을 라우트해야 합니다. 그렇지 않으면, 기존 데이터 그래픽은 환경 내에서 영향을 받을 수 있습니다.

### 관련 링크

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 주문](fortinetvm_ordering.html)
* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 관리](managingfortinetvm.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)
* [FAQ](../vmonic/faq.html)
* [Fortinet 웹 사이트](https://www.fortinet.com/){:new_window}
* [Fortinet Document Library](http://docs.fortinet.com/fortigate/admin-guides){:new_window}

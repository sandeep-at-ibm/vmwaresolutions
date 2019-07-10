---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: F5 BIG-IP, F5 install, tech specs F5

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 on IBM Cloud 개요
{: #f5_considerations}

F5 on {{site.data.keyword.cloud}} 서비스(F5 BIG-IP® Virtual Edition)는 로컬 및 글로벌 스케일의 인텔리전트 L4-L7 로드 밸런싱 및 트래픽 관리 서비스, 강력한 네트워크 및 웹 애플리케이션 방화벽 보호, 안전하고 연합된 애플리케이션 액세스를 제공합니다.

필요에 따라 이 서비스의 인스턴스를 두 개 이상 설치할 수 있습니다.

이 서비스는 V1.9 이상에 배치되는 인스턴스에 대해서만 사용 가능합니다. 설치되어 있는 현재 BIG-IP VE 버전은 v14.1.0.2입니다.
{:note}

## F5 on IBM Cloud의 기술 스펙
{: #f5_considerations-specs}

다음 컴포넌트가 F5 on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### 가상 머신
{: #f5_considerations-specs-vms}

* 모든 옵션이 사용 가능한 2개의 가상 머신(VM).
* 라이센싱 옵션에 따라 가상 머신당 2, 4 또는 8개 vCPU
* 라이센싱 옵션에 따라 가상 머신당 4, 8 또는 16GB RAM

### 네트워킹
{: #f5_considerations-specs-network}

* 고가용성(HA) 동기화를 위한 사설 VXLAN(Virtual Extensible LAN)
* 사설 관리 네트워크를 통한 TMSH(Traffic Management Shell) 및 관리 콘솔에 대한 액세스

### 라이센스 및 요금
{: #f5_considerations-specs-license}

각 VM에 대한 라이센스 요금은 라이센싱 옵션(양호, 우수 또는 최상) 및 선택된 대역폭에 따라 각 청구 주기에 적용됩니다.

서비스 설치 후에는 라이센싱 레벨을 변경할 수 없습니다. 라이센싱 레벨을 변경하려면 기존 서비스를 제거하고 다른 라이센싱 옵션을 사용하여 서비스를 다시 설치해야 합니다.
{:important}

## F5 on IBM Cloud의 설치 고려사항
{: #f5_considerations-install}

F5 on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 다음 고려사항을 검토하십시오.

선택한 라이센스 모델 및 대역폭에 따라 다음 구성으로 두 BIG-IP VE 가상 머신(VM)이 배치됩니다.

표 1. 다양한 대역폭 및 라이센스 모델 선택사항에 대한 CPU 및 RAM 배치

|최대 대역폭 |라이센스 모델: 양호 |라이센스 모델: 나음 |라이센스 모델: 최적 |
|:------------------|:--------------------|:----------------------|:--------------------|
|25Mbps           |2개의 vCPU, 4GB RAM    |4개의 vCPU, 8GB RAM      |8개의 vCPU, 16GB RAM   |
|200Mbps          |2개의 vCPU, 4GB RAM    |4개의 vCPU, 8GB RAM      |8개의 vCPU, 16GB RAM   |
|1Gbps            |2개의 vCPU, 4GB RAM    |4개의 vCPU, 8GB RAM      |8개의 vCPU, 16GB RAM   |
|3Gbps            |8개의 vCPU, 16GB RAM   |8개의 vCPU, 16GB RAM     |8개의 vCPU, 16GB RAM   |
|5Gbps            |8개의 vCPU, 16GB RAM   |8개의 vCPU, 16GB RAM     |8개의 vCPU, 16GB RAM   |
|10Gbps           |8개의 vCPU, 16GB RAM   |8개의 vCPU, 16GB RAM     |8개의 vCPU, 16GB RAM   |

### 추가 고려사항
{: #f5_considerations-additional}

* F5 BIG–IP는 선택한 최대 대역폭에 따라 어플라이언스 처리량을 제한합니다. 네트워크 성능이 많은 요소의 영향을 받기 때문에 모든 구성 및 토폴로지가 선택한 최대 대역폭을 수행할 수 있는 것은 아닙니다.
* BIG-IP VE VM의 HA(High Availability) 쌍이 기본 클러스터에만 배치됩니다.

  또한 VM이 네트워크 통신의 데이터 플레인 상태에 있고 계속해서 네트워크 통신에 리소스를 사용할 수 있는 점이 중요하므로 두 BIG-IP VE VM에 대한 CPU 및 RAM도 100% 예약됩니다.

  단일 BIG-IP VE VM에 대한 CPU 및 RAM 예약을 계산하려면 다음 공식을 사용하십시오.

  `CPU 예약 = ESXi 서버의 CPU 속도 * vCPU 수`(표 1에서)

  `RAM 예약 = RAM 크기`(표 1에서)

### 플랜 고려사항
{: #f5_considerations-planning}

F5 on {{site.data.keyword.cloud_notm}}가 실패하지 않으려면 다음 요구사항을 충족해야 합니다.
* 개별 서버에 VM을 유지하는 비유사성 규칙으로 두 BIG-IP VE VM을 배치하는 데 최소 두 개의 활성 ESXi 서버를 사용할 수 있습니다.
* CPU 및 RAM이 100% 예약된 상태로 각 ESXi 서버에 하나의 BIG-IP VE VM을 호스팅할 수 있도록 두 개의 활성 서버에 사용할 수 있는 충분한 리소스가 있습니다.
* VMware vSphere HA에는 CPU 및 RAM이 100% 상태로 두 BIG-IP VM을 호스팅할 수 있는 충분한 리소스가 있습니다.

이러한 요구사항으로 인해 F5 on {{site.data.keyword.cloud_notm}}에 필요한 공간을 계획해야 합니다. 필요한 경우 F5 on {{site.data.keyword.cloud_notm}}를 주문하기 전에 1 - 2개의 ESXi 서버를 인스턴스에 추가하거나 장애 복구에 대한 vSphere HA CPU 예약을 줄이십시오. 또는 두 가지 모두를 수행하십시오.

## F5 on IBM Cloud 주문 예
{: #f5_considerations-example}

2.10GHz의 16개 코어(각 128GB RAM 포함)로 구성된 두 개의 ESXI 서버와 VMware vCenter Server **소형** 인스턴스를 주문합니다. F5 on {{site.data.keyword.cloud_notm}}의 경우 **최상**의 라이센스 모델을 선택하고 **최대 대역폭**에 5Gbps 값을 선택합니다.

이 경우, 각 서버에 단일 BIG-IP VM이 필요합니다.
* 2.1GHz * 8개의 vCPU = 16.8GHz CPU
* 16GB RAM

두 BIG-IP VM에 총 33.6GHz CPU 및 32GB RAM이 필요합니다.

각 ESXi 서버에는 16개의 코어 * 2.1GHz = 33.6GHz의 용량이 있습니다. 그러므로 두 서버가 활성이고 각 서버에서 최소 16.8GHz CPU와 16GB RAM을 사용할 수 있는 경우 처음 두 가지 요구사항이 충족됩니다.

그러나 기본적으로 vSphere HA는 두 개의 ESXi 서버로 초기에 배치된 vCenter Server 인스턴스의 장애 복구를 위해 CPU 및 RAM의 50%를 예약합니다. 이 예제의 경우 다음을 사용할 수 있습니다.

`50% 2개 * 16개의 코어 * 2.1GHz = 33.6GHz 사용 가능`

ESXi 서버에 VMware vCenter Server, VMware NSX Controller, VMware NSX Edge와 같은 다른 워크로드가 있으므로 이 리소스를 사용하여 세 번째 요구사항을 충족시킬 수 없습니다. 두 BIG-IP VM에 33.6GHz CPU 및 32GB RAM이 필요하기 때문입니다.

이 경우, 최소 하나의 ESXi 서버가 환경에 추가되고 vShpere HA 장애 복구 예약이 두 BIG-IP VE VM에 충분한 리소스가 있도록 적절하게 업데이트되지 않는 한 F5 on {{site.data.keyword.cloud_notm}} 설치에 실패할 수 있습니다. F5 on {{site.data.keyword.cloud_notm}} 서비스를 실행하는 데 추가 리소스가 필요한 경우 F5 on {{site.data.keyword.cloud_notm}}를 설치하기 전에 더 많은 ESXi 서버를 추가할 수 있습니다.

## F5 on IBM Cloud 제거 시 고려사항
{: #f5_considerations-remove}

F5 on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 기존 BIG-IP VE 구성이 올바르게 제거되었는지 확인하십시오. 특히, BIG-IP VE를 통하는 대신 BIG-IP VE 주변에서 네트워크 트래픽을 라우트해야 합니다. 그렇지 않으면 사용자 환경의 기존 데이터 트래픽이 영향을 받을 수 있습니다.

## 관련 링크
{: #f5_considerations-related}

* [F5 on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [F5 on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [F5 웹 사이트](https://www.f5.com/){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: vSphere order cluster, order vSphere, order vSphere cluster

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 새 vSphere 클러스터 주문
{: #vs_orderinginstances}

원하는 대로 사용자 정의할 수 있는 VMware 가상화된 플랫폼을 배치하려면 VMware vSphere on {{site.data.keyword.cloud}} 클러스터를 주문하십시오. 새 vSphere 클러스터를 정의하려면 이 프로시저를 수행하십시오.

이 프로시저는 새 클러스터를 작성하기 위해 VMware 컴포넌트, {{site.data.keyword.cloud_notm}} Bare Metal Server 설정, 스토리지 설정 및 네트워킹 선택사항을 선택하는 과정을 안내합니다. 주문 후 필요에 따라 돌아와서 클러스터 스케일링을 계속할 수 있도록 클러스터 구성이 캡처됩니다. 주문이 완료되면 자신의 요구사항에 따라 수동으로 VMware 클러스터를 구성할 수 있습니다.

## 요구사항
{: #vs_orderinginstances-req}

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정 관리](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)를 참조하십시오.
*  [vSphere 클러스터에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning)의 요구사항 및 고려사항을 검토했습니다.

## 시스템 설정
{: #vs_orderinginstances-sys-settings}

새 vSphere 클러스터를 주문할 때 다음 시스템 설정을 지정해야 합니다.

### 클러스터 이름
{: #vs_orderinginstances-cluster-name}

클러스터 이름은 계정 내에서 고유해야 합니다.

## 라이센스 부여 설정
{: #vs_orderinginstances-licensing-settings}

클러스터와 함께 주문할 VMware 컴포넌트를 선택하고, 해당 컴포넌트에 대한 라이센싱 옵션을 지정하십시오.

### IBM 비즈니스 파트너 사용자용 컴포넌트 번들
{: #vs_orderinginstances-component-bundles-for-bp-users}

IBM 비즈니스 파트너인 경우 새 vSphere 클러스터를 주문할 때 컴포넌트 라이센스 번들을 선택할 수 있습니다. 다음 번들이 사용 가능합니다.

표 1. vSphere 클러스터에 대한 IBM 비즈니스 파트너 컴포넌트 번들

|번들 |컴포넌트                   |
|:------------------------- |:----------------------- |
|관리가 포함된 표준 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
|고급                 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
|네트워킹이 포함된 고급 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
|네트워킹 및 관리가 포함된 고급 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

다음 VMware 컴포넌트를 주문에 포함할 수도 있습니다.
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

IBM 비즈니스 파트너 사용자의 경우 BYOL(Bring Your Own License) 옵션은 사용할 수 없습니다.
{:note}

### 비즈니스 파트너가 아닌 사용자를 위한 개별 컴포넌트
{: #vs_orderinginstances-individual-components-for-non-bp-users}

비즈니스 파트너가 아닌 사용자는 vSphere 클러스터에 대해 다음 컴포넌트를 선택할 수 있습니다.
* VMware vSphere Enterprise Plus 6.7 U1 또는 6.5 U2
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

VMware vSphere Enterprise Plus 6.0을 주문할 때 VMware vSAN 컴포넌트를 사용할 수 없습니다. VMware vSphere Enterprise Plus 6.0에 고유한 라이센스를 사용하려는 경우 사용자를 대신해 {{site.data.keyword.cloud_notm}} 인프라 티켓이 열립니다. 티켓은 주문된 {{site.data.keyword.baremetal_short}}의 vSphere 라이센스를 제공된 라이센스로 대체하도록 요청합니다.
{:note}

### 라이센싱 옵션
{: #vs_orderinginstances-licensing-options}

선택된 VMware 컴포넌트에 라이센스를 부여하기 위한 다음 옵션이 제공됩니다.
* **구매가 포함된 라이센스 포함**: 이 옵션의 경우, 사용자 대신 VMware 컴포넌트의 새 라이센스가 구매됩니다. 주문의 클러스터 크기와 일치하도록 결합된 VMware 라이센스가 생성됩니다.
* **라이센스를 제공함**: 이 경우 VMware 컴포넌트에 고유한 라이센스를 사용합니다.

vSphere Enterprise Plus 및 vCenter Server를 제외한 라이센스를 구매하도록 선택하고 다중 ESXi 서버를 주문하는 경우 사용자 대신 라이센스 키를 결합하도록 {{site.data.keyword.cloud_notm}} 티켓이 자동으로 열립니다. DevOps 팀이 생성한 라이센스 키만 사용하도록 티켓으로 후속 조치를 수행해야 합니다.

결합 라이센스 키와 개별 라이센스 키를 함께 사용하면 필요한 라이센스의 지불 요구사항이 충족되지 않습니다.
{:important}

## Bare Metal Server 설정
{: #vs_orderinginstances-bare-metal-settings}

### 데이터 센터 위치
{: #vs_orderinginstances-dc-location}

클러스터가 호스팅될 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.

**참고:**
* vSAN 컴포넌트를 선택하는 경우 SSD 가용성을 기준으로 위치 목록이 필터링됩니다.
* Broadwell Bare Metal Server는 **FRA05 - 프랑크푸르트** 데이터 센터 위치에서 사용할 수 없습니다.
* SAP 인증 및 Broadwell Bare Metal Server는 **LON05 - 런던** 데이터 센터 위치에서 사용할 수 없습니다.

### Skylake
{: #vs_orderinginstances-skylake}

**Skylake**를 선택하는 경우 필요에 따라 Bare Metal Server의 CPU 및 RAM 조합을 선택할 수 있습니다. 사용 가능한 옵션은 선택한 VMware vSAN 컴포넌트에 따라 달라집니다.

표 2. Skylake {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

### SAP 인증
{: #vs_orderinginstances-sap}

이전에 VMware vSAN을 선택한 경우에는 **SAP 인증** 탭을 사용할 수 없습니다. **SAP 인증**을 선택하는 경우 CPU 또는 RAM 설정을 변경할 수 없습니다.

자신의 요구사항에 따라 Bare Metal Server 구성을 선택하십시오.
  * 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 192GB RAM
  * 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 384GB RAM
  * 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 768GB RAM
  * 듀얼 Intel Xeon E5-2690 v4 프로세서 / 총 28개의 코어, 2.6GHz / 512GB RAM
  * 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.2GHz / 1024GB RAM
  * 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.2GHz / 2048GB RAM
  * 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.2GHz / 4096GB RAM

### Broadwell
{: #vs_orderinginstances-broadwell}

**Broadwell**을 선택하는 경우 필요에 따라 Bare Metal Server의 CPU 및 RAM 조합을 선택할 수 있습니다. 사용 가능한 옵션은 선택한 VMware vSAN 컴포넌트에 따라 달라집니다.

표 3. Broadwell {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 쿼드 Intel Xeon E7-4820 v4 / 총 40개의 코어, 2.0GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |
| 쿼드 Intel Xeon E7-4850 v4 / 총 64개의 코어, 2.1GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |

### Bare Metal Server 수
{: #vs_orderinginstances-bare-metal-number}

vSphere 클러스터에 추가할 ESXi 서버의 수입니다. 모든 ESXi 서버는 동일한 구성을 갖습니다.
* VMware NSX 컴포넌트를 선택한 경우 최소 세 개의 서버가 필요합니다.
* VMware vSAN 컴포넌트를 선택한 경우 최소 네 개의 서버가 필요합니다.

## 스토리지 설정
{: #vs_orderinginstances-storage-settings}

vSAN을 제외한 주문의 경우, 12개의 디스크 섀시, ESXi 운영 체제(OS)용 2개의 디스크와 함께 ESXi 서버가 주문됩니다.

vSAN이 포함된 주문의 경우, 주문된 12개의 디스크 섀시와 4개의 디스크(ESXi OS용 2개, 캐싱용으로 예약된 2개)와 함께 ESXi 서버가 주문됩니다. 이 설정은 기본적으로 구성되어 있으며 변경될 수 없습니다. **vSAN 용량 디스크의 디스크 유형 및 크기** 및 **vSAN 용량 디스크 수**를 선택하여 추가 용량 디스크를 주문할 수 있습니다.

클러스터용 VMware vSAN 컴포넌트를 선택하고 나면 다음 설정을 지정하십시오.
* **vSAN 용량 디스크의 디스크 유형 및 크기**: 필요한 용량 디스크에 대한 옵션을 선택하십시오.
* **vSAN 용량 디스크 수**: 추가할 용량 디스크 수를 지정하십시오.
* 용량 디스크를 8개 한계 이상으로 추가하려는 경우 **고성능 Intel Optane** 상자를 선택하십시오. 이 옵션은 총 10개 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공하며 짧은 대기 시간과 높은 IOPS 처리량이 필요한 워크로드에 유용합니다.

  **고성능 Intel Optane** 옵션은 Skylake CPU 모델에 대해서만 사용 가능합니다.
  {:note}

* **vSAN 캐시 디스크의 디스크 유형** 및 **vSAN 캐시 디스크 수** 값을 검토하십시오. 이러한 값은 **고성능 Intel Optane** 상자를 선택했는지 여부에 따라 달라집니다.

## 네트워크 인터페이스 설정
{: #vs_orderinginstances-network-interface-settings}

새 vSphere 클러스터를 주문할 때 다음 네트워크 인터페이스 설정을 지정해야 합니다.

### 호스트 이름 접두부
{: #vs_orderinginstances-host-name-prefix}

호스트 이름은 베어메탈 서버 주문에 사용됩니다. vCenter Server 및 NSX와 같이 모든 관리 가상 머신에 호스트 이름을 사용하는 것이 좋습니다.

호스트 이름 접두부는 다음 요구사항을 충족해야 합니다.
* 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 최대 길이는 10자입니다.

### 하위 도메인 레이블
{: #vs_orderinginstances-subdomain-label}

하위 도메인 레이블은 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  하위 도메인 레이블은 영숫자 문자로 시작하고 끝나야 합니다.
*  하위 도메인 레이블의 최대 길이는 10자입니다.

### 도메인 이름
{: #vs_orderinginstances-domain-name}

도메인 이름이 모든 {{site.data.keyword.baremetal_short}}에 사용되고 다음 요구사항을 충족해야 합니다.
* 이름은 마침표(.)로 구분된 두 개 이상의 문자열로 구성되어야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 각 문자열은 영문자로 시작하고 영숫자로 끝나야 하며 마지막 문자열에는 영문자만 포함될 수 있습니다.
* 마지막 문자열의 길이는 2 - 24자 사이여야 합니다.
* 기타 문자열의 길이는 1 - 63자 사이여야 합니다.
* 도메인 이름의 최대 길이는 189자입니다.

### 공용 또는 사설 네트워크
{: #vs_orderinginstances-public-private-network}

네트워크 인터페이스 카드(NIC) 인에이블먼트 설정은 **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 사용자의 선택을 기반으로 합니다.

### VLAN
{: #vs_orderinginstances-vlans}

네트워크 설정은 **새 VLAN 주문** 또는 **기존 VLAN 선택**의 선택에 따라 달라집니다.

클러스터 주문에 한 개의 공용 VLAN 및 두 개의 사설 VLAN이 필요합니다. 두 개의 사설 VLAN이 각 Bare Metal Server에 선택됩니다.

#### 새 VLAN 주문
{: #vs_orderinginstances-new-vlans}

하나의 새 공용 VLAN 및 두 개의 새 사설 VLAN 주문을 선택하십시오.

#### 기존 VLAN 선택
{: #vs_orderinginstances-existing-vlans}

선택한 {{site.data.keyword.CloudDataCent_notm}}에 따라 기존 공용 및 사설 VLAN을 사용할 수 있습니다.

  기존 공용 및 사설 VLAN을 재사용하도록 선택하는 경우에는 VLAN 및 서브넷을 지정하십시오.
  * **공용 VLAN**은 공용 네트워크 액세스를 위한 것입니다.
  * **사설 VLAN**은 {{site.data.keyword.cloud_notm}} 내의 데이터 센터 및 서비스 간의 연결을 위한 것입니다.
  * **보조 사설 VLAN**은 vSAN과 같은 VMware 기능을 위한 것입니다.
  * **기본 서브넷**은 공용 네트워크 액세스를 위한 실제 호스트에 지정됩니다.
  * **사설 기본 서브넷**은 관리 트래픽을 위한 실제 호스트에 지정됩니다.

**중요:**
* 선택된 VLAN의 방화벽 구성이 관리 데이터 트래픽을 차단하지 않는지 확인하십시오.
* 선택한 모든 VLAN이 동일한 팟(Pod)에 있는지 확인하십시오. 혼합 팟(pod) VLAN에서 ESXi 서버를 프로비저닝할 수 없습니다.

#### FortiGate Physical Appliance 300 시리즈 HA 이중화
{: #vs_orderinginstances-fortigate-physical-appliance}

클라우드 환경을 보호하기 위해 FortiGate Physical Appliance 300 Series HA 이중화를 포함시킬지 선택할 수도 있습니다. 자세한 정보는 [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)를 참조하십시오.

## 주문 요약
{: #vs_orderinginstances-order-summary}

선택한 구성에 따라 예상 비용이 즉시 생성되어 **주문 요약** 오른쪽 분할창에 표시됩니다. **가격 세부사항**을 클릭하여 {{site.data.keyword.vmwaresolutions_short}} 리소스에 대한 비용 요약이 포함된 PDF 문서를 생성하십시오. 

**예상 금액에 추가**를 클릭하여 {{site.data.keyword.cloud_notm}} 예상 도구에 프로비저닝된 리소스를 추가할 수도 있습니다. 구매를 고려할 수 있는 기타 {{site.data.keyword.cloud_notm}} 리소스와 함께 선택된 {{site.data.keyword.vmwaresolutions_short}} 리소스의 비용을 예상하려는 경우 유용합니다. 

## vSphere 클러스터를 주문하는 프로시저
{: #vs_orderinginstances-procedure}

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 다음 **가상 데이터 센터** 섹션에 있는 **VMware vSphere**를 클릭하십시오.
2. **VMware vSphere on IBM Cloud** 페이지에서 **작성**을 클릭하십시오.  
   사용자가 **새로 작성** 탭에 있으며 **클러스터 구성** 목록에 **새 클러스터**가 표시되어 있는지 확인하십시오.
3. 클러스터 이름을 입력하십시오.
4. VMware 컴포넌트를 선택하십시오.
  * IBM 비즈니스 파트너의 경우 라이센스 번들과 추가로 사용 가능한 VMware 컴포넌트를 선택하십시오.
  * 비즈니스 파트너가 아닌 사용자의 경우에는 컴포넌트, 에디션(있는 경우)을 선택하고 라이센싱 옵션을 지정하십시오.
  VMware vSphere Enterprise Plus에 대해 고유한 라이센스를 가져오도록(BYOL) 선택한 경우 주문한 {{site.data.keyword.baremetal_short}}에 대한 기본 vSphere 라이센스를 사용자가 제공하는 라이센스로 대체하도록 요청하기 위해 {{site.data.keyword.cloud_notm}} 티켓이 사용자를 대신하여 자동으로 열립니다.   

    **중요:** 새로 주문된 ESXi 서버에서 vSphere 라이센스를 대체하도록 티켓을 추적해야 합니다. {{site.data.keyword.cloud_notm}} 인프라는 초기에 제공된 {{site.data.keyword.cloud_notm}} 인프라 vSphere 라이센스 비용 취소를 승인합니다. ESXi vSphere 라이센스를 대체하려면 [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}를 참조하십시오.
5. Bare Metal Server 설정을 완료하십시오.
   1. 클러스터를 호스팅할 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.
   2. Bare Metal Server 구성을 선택하십시오.
      * **Skylake** 또는 **Broadwell**을 선택하는 경우 CPU 모델 및 RAM 크기를 지정하십시오.
      * **SAP 인증**을 선택하는 경우, 사전 설정된 구성 중 하나를 선택하십시오.
   3. Bare Metal Server의 수를 지정하십시오.
6. **VMware vSAN** 컴포넌트를 선택한 경우 vSAN 스토리지 구성을 완료하십시오. 용량 및 캐시 디스크에 대한 디스크 유형과 디스크 수를 지정하십시오. 더 많은 스토리지를 원하는 경우 **고성능 Intel Optane** 상자를 선택하십시오.
7. 네트워크 인터페이스 설정을 완료하십시오.
   1. 호스트 이름 접두부, 하위 도메인 레이블 및 도메인 이름을 입력하십시오.
   2. **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 네트워크 설정을 선택하십시오.
   3. 사용할 네트워크 인터페이스를 선택하십시오.
    * 새 공용 및 사설 VALN을 주문하려면 **새 VLAN 주문**을 클릭하십시오.
    * 기존 공용 및 사설 VLAN이 사용 가능한 경우 이들을 재사용하려면 **기존 VLAN 선택**을 클릭하고 VLAN 및 서브넷(선택사항)을 지정하십시오.
    4. 클라우드 환경을 보호하기 위해 FortiGate Physical Appliance 300 Series HA 이중화를 적용할지 지정하십시오.  
8. **주문 요약** 분할창에서 클러스터 구성 및 예상 비용을 확인하십시오.
   * 주문하지 않고 구성을 템플리트로 저장하려면 **구성 저장**을 클릭하십시오.
   * 주문하려는 경우에는 비용이 청구될 계정이 올바른지 확인하고, 이용 약관을 검토하고 이에 동의한 후 **프로비저닝**을 클릭하십시오.

   {{site.data.keyword.baremetal_short}}만 설치됩니다. 클러스터 배치 후 VMware vCenter, VMware NSX, VMware vSAN과 같이 다양한 컴포넌트를 설치하고 구성해야 합니다.
   {:note}

### vSphere 클러스터를 주문한 후의 결과
{: #vs_orderinginstances-results}

클러스터 구성을 템플리트로 저장한 경우에는 구성이 저장되었다는 콘솔 알림을 받은 후 **클러스터 구성** 목록에서 해당 템플리트를 찾을 수 있습니다.

주문한 경우 클러스터의 배치가 자동으로 시작되고 주문이 처리 중이라는 이메일 확인을 수신합니다. 클러스터를 사용할 준비가 되면 이메일로 알림을 받습니다.

vSphere 클러스터는 vCenter Server 인스턴스와 달리 **리소스** 페이지에 표시되지 않습니다.
{:note}

## 관련 링크
{: #vs_orderinginstances-related}

* [기존 구성에 따라 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [기존 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_scalingexistingclusters)
* [콘솔 외부에서 작성된 클러스터 스케일링](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)

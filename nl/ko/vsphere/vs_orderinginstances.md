---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-20"

---

{:tip: .tip}

# 새 vSphere 클러스터 주문

원하는 대로 사용자 정의할 수 있는 VMware 가상화된 플랫폼을 배치하려면 VMware vSphere on {{site.data.keyword.cloud}} 클러스터를 주문하십시오. 새 VMware vSphere 클러스터를 정의하려면 이 프로시저를 수행하십시오.

이 프로시저는 새 클러스터를 작성하기 위해 VMware 컴포넌트, {{site.data.keyword.cloud_notm}} Bare Metal Server 설정, 스토리지 설정 및 네트워킹 선택사항을 선택하는 과정을 안내합니다. 주문 후 필요에 따라 돌아와서 클러스터 스케일링을 계속할 수 있도록 클러스터 구성이 캡처됩니다. 주문이 완료되면 자신의 요구사항에 따라 수동으로 VMware 클러스터를 구성할 수 있습니다.

## 요구사항

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 신임 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정 관리](../vmonic/useraccount.html)를 참조하십시오.
*  [vSphere 클러스터에 대한 요구사항 및 계획](vs_planning.html)의 요구사항 및 고려사항을 검토했습니다.

## 시스템 설정

새 vSphere 클러스터를 주문할 때는 다음 시스템 설정을 지정해야 합니다.

### 클러스터 이름

클러스터 이름은 계정 내에서 고유해야 합니다.

## 라이센스 부여 설정

클러스터와 함께 주문할 VMware 컴포넌트를 선택하고, 해당 컴포넌트에 대한 라이센싱 옵션을 지정하십시오.

### (비즈니스 파트너 사용자만 해당) 컴포넌트 번들

비즈니스 파트너 사용자는 새 vSphere 클러스터를 주문할 때 컴포넌트 라이센스 번들을 선택할 수 있습니다. 사용 가능한 번들은 다음과 같습니다.

표 1. vSphere 클러스터에 대한 비즈니스 파트너 컴포넌트 번들

|번들 |컴포넌트                   |
|:-------------------------|:-----------------------|
|관리가 포함된 표준 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise |
|고급                 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vCloud Director, NSX Base |
|네트워킹이 포함된 고급 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, NSX Advanced |
|네트워킹 및 관리가 포함된 고급 |vSphere Enterprise Plus, vCenter Server Standard, vRealize Log Insight, vRealize Operations Enterprise, vCloud Director, NSX Enterprise |

다음 추가 VMware 컴포넌트를 주문에 포함할 수도 있습니다.
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise

**참고:** 비즈니스 파트너에게는 BYOL(Bring Your Own License) 옵션이 없습니다. 주문을 완료할 때 **라이센스를 제공함** 옵션을 사용할 수 없습니다.

### (비즈니스 파트너가 아닌 사용자만 해당) 개별 번들

비즈니스 파트너가 아닌 사용자는 자신의 vSphere 클러스터에 대해 다음 VMware 컴포넌트를 유연하게 선택할 수 있습니다.
* VMware vSphere Enterprise Plus
* VMware vCenter Server
* VMware NSX
* VMware vSAN
* VMware Site Recovery Manager
* VMware vRealize Automation Enterprise
* VMware vRealize Operation Enterprise
* VMware vRealize Log Insight

**참고:** VMware vSphere Enterprise Plus 6.0을 주문할 때 VMware vSAN 컴포넌트를 사용할 수 없습니다. VMware vSphere Enterprise Plus 6.0에 고유한 라이센스를 사용할 계획인 경우 사용자 대신 주문된 {{site.data.keyword.baremetal_short}}의 vSphere 라이센스를 제공된 라이센스로 대체하도록 요청하여 {{site.data.keyword.cloud_notm}} 인프라 티켓이 열립니다.

### 라이센싱 옵션

선택된 VMware 컴포넌트에 라이센스를 부여하기 위한 다음 옵션이 제공됩니다.
* **구매가 포함된 라이센스 포함**: 이 옵션의 경우, 사용자 대신 VMware 컴포넌트의 새 라이센스가 구매됩니다. 주문의 클러스터 크기와 일치하도록 결합된 VMware 라이센스가 생성됩니다.
* **라이센스를 제공함**: 이 옵션의 경우, VMware 컴포넌트에 고유한 라이센스를 사용합니다.

vSphere Enterprise Plus 및 vCenter Server를 제외한 라이센스를 구매하도록 선택하고 다중 ESXi 서버를 주문하는 경우 사용자 대신 라이센스 키를 결합하도록 {{site.data.keyword.cloud_notm}} 티켓이 자동으로 열립니다. DevOps 팀이 생성한 라이센스 키만 사용하도록 티켓으로 후속 조치를 수행해야 합니다.

**중요**: 결합 라이센스 키와 개별 라이센스 키를 함께 사용하면 필요한 라이센스의 지불 요구사항이 충족되지 않습니다.

## Bare Metal Server 설정

### 데이터 센터 위치

클러스터가 호스팅될 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.

**참고:** vSAN 컴포넌트를 선택하면 위치 목록이 SSL 가용성별로 필터링됩니다.

### CPU 모델 및 RAM

Bare Metal Server의 CPU 모델 및 RAM을 지정하십시오.

표 2. 사용자 정의된 {{site.data.keyword.baremetal_short}}의 옵션

|CPU 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 듀얼 Intel Xeon E5-2620 v4 / 총 16개의 코어, 2.1GHz | 64GB, 128GB, 256GB, 384GB, 512GB, 768GB, 1.5TB |
| 듀얼 Intel Xeon E5-2650 v4 / 총 24개의 코어, 2.2GHz | 64GB, 128GB, 256GB, 384GB, 512GB, 768GB, 1.5TB |
| 듀얼 Intel Xeon E5-2690 v4 / 총 28개의 코어, 2.6GHz | 64GB, 128GB, 256GB, 384GB, 512GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

사용 가능한 옵션은 선택한 VMware vSAN 컴포넌트에 따라 달라집니다.

### Bare Metal Server 수

vSphere 클러스터에 추가할 ESXi 서버의 수입니다. 모든 ESXi 서버는 동일한 구성을 공유합니다.
* VMware NSX 컴포넌트를 선택한 경우 최소 세 개의 서버가 필요합니다.
* VMware vSAN 컴포넌트를 선택한 경우 최소 네 개의 서버가 필요합니다.

## 스토리지 설정

vSAN을 제외한 주문의 경우, 12개의 디스크 섀시, ESXi 운영 체제(OS)용 2개의 디스크와 함께 ESXi 서버가 주문됩니다.

vSAN이 포함된 주문의 경우, 주문된 12개의 디스크 섀시와 4개의 디스크(ESXi OS용 2개, 캐싱용으로 예약된 2개)와 함께 ESXi 서버가 주문됩니다. 이 설정은 기본적으로 구성되어 있으며 변경될 수 없습니다. **vSAN 용량 디스크의 디스크 유형 및 크기** 및 **vSAN 용량 디스크 수**를 선택하여 추가 용량 디스크를 주문할 수 있습니다.

클러스터의 VMware vSAN 컴포넌트를 선택하고 나면 다음 설정을 지정하십시오.

### vSAN 용량 디스크의 디스크 유형 및 크기

이 옵션은 VMware vSAN 컴포넌트를 선택한 경우에만 사용 가능합니다.

다음 디스크 유형이 사용 가능합니다.
* 960GB SSD SED
* 1.9TB SSD SED
* 3.8TB SSD SED(3.8TB SSD SED 드라이브는 데이터 센터에서 일반적으로 사용 가능하게 되면 지원됨)

### vSAN 용량 디스크 수

이 옵션은 VMware vSAN 컴포넌트를 선택한 경우에만 사용 가능합니다. 디스크 양 옵션에는 2, 4, 6 및 8이 포함됩니다.

## 네트워크 인터페이스 설정

새 vSphere 클러스터를 주문할 때는 다음 네트워크 설정을 지정해야 합니다.

### 호스트 이름 접두부

호스트 이름은 베어메탈 서버 주문에 사용됩니다. vCenter Server, NSX와 같이 모든 관리 가상 머신의 호스트 이름을 사용하는 것이 좋습니다.

호스트 이름 접두부는 다음 요구사항을 충족해야 합니다.
* 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 최대 길이는 10자입니다.

### 하위 도메인 레이블

하위 도메인 레이블은 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  하위 도메인 레이블은 영숫자 문자로 시작하고 끝나야 합니다.
*  하위 도메인 레이블의 최대 길이는 10자입니다.
*  하위 도메인 레이블은 계정 내에서 고유해야 합니다.

### 도메인 이름

도메인 이름이 모든 {{site.data.keyword.baremetal_short}}에 사용되고 다음 요구사항을 충족해야 합니다.
* 이름은 마침표(.)로 구분된 두 개 이상의 문자열로 구성되어야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 각 문자열은 영문자로 시작하고 영숫자로 끝나야 하며 마지막 문자열에는 영문자만 포함될 수 있습니다.
* 마지막 문자열의 길이는 2 - 24자 사이여야 합니다.
* 기타 문자열의 길이는 1 - 63자 사이여야 합니다.
* 도메인 이름의 최대 길이는 189자입니다.

### VLAN

네트워크 설정은 **새 VLAN 주문** 또는 **기존 VLAN 선택**의 선택에 따라 달라집니다.

클러스터 주문에 한 개의 공인 VLAN 및 두 개의 사설 VLAN이 필요합니다. 두 개의 사설 VLAN이 각 Bare Metal Server에 선택됩니다.

#### 새 VLAN 주문
하나의 새 공인 VLAN 및 두 개의 새 사설 VLAN 주문을 선택하십시오.

#### 기존 VLAN 선택  
선택한 {{site.data.keyword.CloudDataCent_notm}}에 따라 기존 공인 및 사설 VLAN을 사용할 수 있습니다.

  기존 공인 및 사설 VLAN을 재사용하도록 선택하는 경우에는 VLAN 및 서브넷을 지정하십시오.
  * **공인 VLAN**은 공용 네트워크 액세스를 위한 것입니다.
  * **사설 VLAN**은 {{site.data.keyword.cloud_notm}} 내의 데이터 센터 및 서비스 간의 연결을 위한 것입니다.
  * **보조 사설 VLAN**은 vSAN과 같은 VMware 기능을 위한 것입니다.
  * **기본 서브넷**은 공용 네트워크 액세스를 위한 실제 호스트에 지정됩니다.
  * **사설 기본 서브넷**은 관리 트래픽을 위한 실제 호스트에 지정됩니다.

**중요:**
* 선택된 VLAN의 방화벽 구성이 관리 데이터 트래픽을 차단하지 않는지 확인하십시오.
* 혼합 팟(Pod) VLAN에서 ESXi 서버를 프로비저닝할 수 없으므로 선택하는 모든 VLAN이 동일한 팟(Pod)에 있는지 확인하십시오.

#### FortiGate Physical Appliance 300 시리즈 HA 쌍

클라우드 환경을 보호하기 위해 FortiGate Physical Appliance 300 Series HA 쌍을 포함시킬지 선택할 수도 있습니다. 자세한 정보는 [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 개요](../services/fsa_considerations.html)를 참조하십시오. 

## 주문 요약

구성에 따라 예상 비용이 즉시 생성되어 오른쪽에 있는 **주문 요약** 분할창에 표시됩니다. 예상 세부사항을 제공하는 PDF 문서를 생성하려면 분할창 맨 아래에 있는 **가격 책정 세부사항**을 클릭하십시오.

## 프로시저

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 후 **가상 데이터 센터** 섹션에 있는 **VMware vSphere**를 클릭하십시오.
2. **VMware vSphere on IBM Cloud** 페이지에서 **작성**을 클릭하십시오.  
   사용자가 **새로 작성** 탭에 있으며 **클러스터 구성** 목록에 **새 클러스터**가 표시되어 있는지 확인하십시오.
3. 클러스터 이름을 입력하십시오.
4. VMware 컴포넌트를 선택하십시오.
  * 비즈니스 파트너 사용자의 경우에는 라이센스 번들과 추가로 사용 가능한 VMware 컴포넌트를 선택하십시오.
  * 비즈니스 파트너가 아닌 사용자의 경우에는 컴포넌트, 에디션(있는 경우)을 선택하고 라이센싱 옵션을 지정하십시오.
  VMware vSphere Enterprise Plus에 대해 고유한 라이센스를 가져오도록(BYOL) 선택한 경우 주문한 {{site.data.keyword.baremetal_short}}에 대한 기본 vSphere 라이센스를 사용자가 제공하는 라이센스로 대체하도록 요청하기 위해 {{site.data.keyword.cloud_notm}} 티켓이 사용자를 대신하여 자동으로 열립니다.   

    **중요:** 사용자는 {{site.data.keyword.cloud_notm}} 인프라가 처음 제공된 {{site.data.keyword.cloud_notm}} 인프라 vSphere 라이센스 비용의 취소를 승인하도록 하기 위해 새로 주문한 ESXi 서버에 대한 vSphere 라이센스가 대체되도록 티켓에 대한 후속 조치를 수행해야 합니다. ESXi vSphere 라이센스를 대체하려면 [Configure License Settings for an ESXi Host](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.vcenterhost.doc/GUID-1B128360-0060-40F2-A6F0-43CD2534B034.html){:new_window}를 참조하십시오.

5. Bare Metal Server 설정을 완료하십시오.
   1. 클러스터를 호스팅할 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.
   2. CPU 모델 및 RAM 크기를 선택하십시오.
   3. Bare Metal Server의 수를 지정하십시오.
6. **VMware vSAN** 컴포넌트를 선택한 경우에는 **vSAN 용량 디스크의 디스크 유형 및 크기** 및 **vSAN 용량 디스크 수**를 선택하여 vSAN 스토리지 설정을 완료하십시오.
7. 네트워크 인터페이스 설정을 완료하십시오.
   1. 호스트 이름 접두부, 하위 도메인 레이블 및 도메인 이름을 입력하십시오.
   2. 사용할 네트워크 인터페이스를 선택하십시오.
    * 새 공인 및 사설 VALN을 주문하려면 **새 VLAN 주문**을 클릭하십시오.
    * 기존 공인 및 사설 VLAN이 사용 가능한 경우 이들을 재사용하려면 **기존 VLAN 선택**을 클릭하고 VLAN 및 서브넷(선택사항)을 지정하십시오.
    3. 클라우드 환경을 보호하기 위해 FortiGate Physical Appliance 300 Series HA 쌍을 적용할지 지정하십시오.  
8. **주문 요약** 분할창에서 클러스터 구성 및 예상 비용을 확인하십시오.
   * 주문하지 않고 구성을 템플리트로 저장하려면 **구성 저장**을 클릭하십시오.
   * 주문하려는 경우에는 비용이 청구될 계정이 올바른지 확인하고, 이용 약관을 검토하고 이에 동의한 후 **프로비저닝**을 클릭하십시오.

   **참고**: {{site.data.keyword.baremetal_short}}만 설치됩니다. 클러스터 배치 후 VMware vCenter, VMware NSX, VMware vSAN과 같이 다양한 컴포넌트를 설치하고 구성해야 합니다.

### 결과

클러스터 구성을 템플리트로 저장한 경우에는 구성이 저장되었다는 콘솔 알림을 받은 후 **클러스터 구성** 목록에서 해당 템플리트를 찾을 수 있습니다.

주문한 경우 클러스터의 배치가 자동으로 시작되고 주문이 처리 중이라는 이메일 확인을 수신합니다. 클러스터를 사용할 준비가 되면 이메일로 알림을 받습니다.

**참고:** vSphere 클러스터는 vCenter Server 및 Cloud Foundation 인스턴스와 달리 **배치된 인스턴스** 페이지에 표시되지 않습니다.

### 관련 링크

* [기존 구성에 따라 vSphere 클러스터 주문](vs_orderingbasedonexistingconfig.html)
* [기존 클러스터 스케일링](vs_scalingexistingclusters.html)
* [콘솔 외부에서 작성된 클러스터 스케일링](vs_orderingforclustersoutside.html)

---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-12"

---

# vCenter Server 인스턴스 주문

워크로드 요구사항에 가장 적합한 유연하고 사용자 정의할 수 있는 VMware 가상화된 플랫폼을 배치하려면 VMware vCenter Server 인스턴스를 주문하십시오. 초기 주문 중에는 재해 복구를 위한 [Zerto on {{site.data.keyword.cloud}}](../services/addingzertodr.html)와 같은 서비스를 추가할 수도 있습니다.

## 요구사항

다음 태스크를 완료했는지 확인하십시오.
* **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 신임 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정](../vmonic/useraccount.html)을 참조하십시오.
* [vCenter Server 인스턴스에 대한 요구사항 및 계획](vc_planning.html)의 정보를 검토했습니다.
* 인스턴스 및 도메인 이름 형식을 검토했습니다. 도메인 이름 및 하위 도메인 레이블은 인스턴스의 사용자 이름 및 서버 이름을 생성하는 데 사용됩니다.

표 1. 인스턴스 및 도메인 이름의 값 형식

|이름        |값 형식      |
  |:------------- |:------------- |
  |도메인 이름 | `<root_domain>` |  
  |vCenter Server 로그인 사용자 이름 | `<user_id>@<root_domain>`(Microsoft Active Directory 사용자) 또는 `administrator@vsphere.local` |
  |vCenter Server FQDN |`vcenter.<subdomain_label>.<root_domain>`. 최대 길이는 50자입니다. |
  |SSO(Single Sign-On) 사이트 이름 | `<subdomain_label>` |
  |완전한 ESXi 서버 이름 | `<host_prefix><n>.<subdomain_label>.<root_domain>`, 여기서 `<n>`은 ESXi 서버의 순서입니다. 최대 길이는 50자입니다. |  
  |PSC FQDN |`psc-<subdomain_label>.<subdomain_label>.<root_domain>`. 최대 길이는 50자입니다. |

**중요**: 주문 및 인스턴스 배치 중에 설정된 값을 수정하지 마십시오. 수정하면 인스턴스를 사용할 수 없게 됩니다. 예를 들면 공용 네트워킹의 작동이 중단되거나, 프로비저닝 중에 서버 및 VSI(Virtual Server Instance)가 Vyatta 뒤로 이동할 수 있거나 IBM CloudBuilder VSI가 중지되거나 삭제될 수 있습니다.

## 시스템 설정

vCenter Server 인스턴스를 주문할 때는 다음 시스템 설정을 지정해야 합니다.

### 인스턴스 이름

인스턴스 이름은 다음 요구사항을 충족해야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 인스턴스 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 인스턴스 이름의 최대 길이는 10자입니다.
* 인스턴스 이름은 계정 내에서 고유해야 합니다.

### 기본 또는 보조

새 기본 인스턴스를 주문할지 또는 기존 기본 인스턴스의 보조 인스턴스를 주문할지 선택하십시오.

## 라이센스 부여 설정

인스턴스의 다음 VMware 컴포넌트에 대한 라이센싱 옵션을 지정하십시오.
* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.3

비즈니스 파트너 사용자의 경우, vCenter Server 라이센스(Standard 에디션), vSphere 라이센스(Enterprise Plus 에디션) 및 NSX 라이센스가 사용자를 대신하여 포함 및 구매됩니다. 그러나 NSX 라이센스의 에디션은 지정해야 합니다.

비즈니스 파트너가 아닌 사용자의 경우에는 **구매에 포함**을 선택하여 이 컴포넌트에 대해 IBM 제공 VMware 라이센스를 사용하거나, **라이센스를 제공함**을 선택하고 고유한 라이센스 키를 입력하여 고유한 라이센스를 가져올(BYOL) 수 있습니다.

**주의**:
* 최소 여덟 개의 CPU가 있는 라이센스가 필요합니다. 즉, 서버당 두 개의 CPU가 있는 네 개의 서버입니다. 각 VMware 컴포넌트의 라이센스 선택사항은 기본 인스턴스와 나중에 라이센스에 추가하는 ESXi 서버에 적용됩니다. 그러므로 인프라의 라이센스가 이후의 용량 확장을 지원하는지 확인해야 합니다.
* 최소 라이센스 에디션은 사용자 인터페이스에 표시됩니다. 다른 컴포넌트 에디션이 지원되는 경우 원하는 에디션을 선택할 수 있습니다. 선택한 각 VMware 컴포넌트에 올바른 라이센스 키가 제공되었는지 확인해야 합니다.
* vSphere의 경우 라이센스 비용은 주문 시 발생하지만 라이센스 비용이 나중에 사용자 계정으로 청구됩니다.
* 인스턴스 배치가 완료된 후 VMware vSphere Web Client를 사용하여 제공한 모든 라이센스를 변경할 수 있습니다.
* 라이센스를 제공하는 VMware 컴포넌트에 대한 지원은 IBM 지원 센터가 아닌 VMware에서 직접 제공됩니다.

## Bare Metal Server 설정

Bare Metal Server 설정은 사용자의 데이터 센터 선택, 그리고 사전 구성됨 또는 사용자 정의됨 구성의 선택 여부에 따라 달라집니다.

### 데이터 센터 위치

인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.<!-- Only the {{site.data.keyword.CloudDataCents_notm}} that meet the {{site.data.keyword.baremetal_long}} specification you selected previously are displayed.-->

### 사전 구성됨

**사전 구성됨**을 선택하는 경우에는 CPU 또는 RAM 설정을 변경할 수 없습니다.

자신의 요구사항에 따라 Bare Metal Server 구성을 선택하십시오.
  * 소형(듀얼 Intel Xeon E5-2620 v4 / 총 16개의 코어, 2.1GHz / 128GB RAM / 2개의 드라이브)
  * 중형(듀얼 Intel Xeon E5-2650 v4 / 총 24개의 코어, 2.2GHz / 256GB RAM / 2개의 드라이브)
  * 대형(듀얼 Intel Xeon E5-2690 v4 / 총 28개의 코어, 2.6GHz / 512GB RAM / 2개의 드라이브)

### 사용자 정의됨

**사용자 정의됨**을 선택하는 경우에는 필요에 따라 CPU 및 RAM 조합을 선택할 수 있습니다.

Bare Metal Server의 CPU 모델 및 RAM을 선택하십시오.

표 2. 사용자 정의된 {{site.data.keyword.baremetal_short}}의 옵션

|CPU 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 듀얼 Intel Xeon E5-2620 v4 / 총 16개의 코어, 2.1GHz |64GB, 128GB, 256GB, 512GB, 768GB, 1.5TB |
| 듀얼 Intel Xeon E5-2650 v4 / 총 24개의 코어, 2.2GHz |64GB, 128GB, 256GB, 512GB, 768GB, 1.5TB |
| 듀얼 Intel Xeon E5-2690 v4 / 총 28개의 코어, 2.6GHz |64GB, 128GB, 256GB, 512GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

### Bare Metal Server 수

인스턴스에 있는 초기 클러스터의 경우 다음과 같이 ESXi 서버의 수를 구성할 수 있습니다.
* **사전 구성됨**을 선택한 경우 ESXi 서버의 수를 2 - 10의 범위로 구성할 수 있습니다.
* **사용자 정의됨**을 선택한 경우 ESXi 서버의 수를 2 - 20의 범위로 구성할 수 있습니다.

모든 ESXi 서버는 동일한 구성을 공유합니다. 초기 배치 후에는 네 개의 클러스터를 추가할 수 있습니다. vSAN에 대한 **사용자 정의됨** 구성을 선택한 경우 초기 및 사후 배치 클러스터 모두에 네 개의 ESXi 서버가 필요합니다. 최소 ESXi 서버에 대한 자세한 정보는 [두 개의 노드 vCenter Server 인스턴스가 고가용성입니까?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)를 참조하십시오.

## 스토리지 설정

스토리지 설정은 Bare Metal Server 구성의 선택 및 스토리지 유형에 따라 달라집니다.

### vSAN 스토리지

vSAN은 **사용자 정의됨** Bare Metal Server 구성을 선택하는 경우에만 사용 가능합니다. 다음 vSAN 옵션을 지정하십시오.

* **vSAN 용량 디스크 수**: 추가할 vSAN 공유 스토리지에 대한 디스크 수를 지정하십시오. 디스크 양은 2, 4, 6 또는 8개여야 합니다.
* **vSAN 용량 디스크의 디스크 유형 및 크기**: 공유 스토리지 요구사항을 충족하는 용량을 선택하십시오.
* **vSAN 라이센스**: **구매에 포함**을 선택하여 vSAN 컴포넌트에 대한 IBM 제공 VMware 라이센스를 사용하거나, **라이센스를 제공함**을 선택하고 고유한 라이센스 키를 입력하여 고유한 라이센스를 가져오십시오(BYOL).

### NFS 스토리지

**NFS 스토리지**를 선택할 때 모든 공유가 동일한 설정을 사용하는 인스턴스에 대한 파일 레벨 공유 스토리지를 추가하거나 각 파일 공유에 서로 다른 구성 설정을 지정할 수 있습니다. 다음 NFS 옵션을 지정하십시오.

**참고:** 파일 공유의 수는 1 - 32 범위에 있어야 합니다.

* **파일 공유 개별 구성**: 각 파일 공유에 서로 다른 구성 설정을 지정하도록 선택하십시오.
* **공유 수**: 각 파일 공유에 동일한 구성 설정을 사용하는 경우 추가할 NFS 공유 스토리지에 대한 파일 공유 수를 지정하십시오.
* **크기**: 공유 스토리지 요구사항을 충족하는 용량을 선택하십시오.
* **성능**: 워크로드 요구사항에 기반한 GB당 IOPS(Input/output Operations Per Second)를 선택하십시오.
* **NFS 추가**: 여러 구성 설정을 사용하는 개별 파일 공유를 추가하도록 선택하십시오.

표 3. NFS 성능 레벨 옵션

|옵션        |세부사항       |
  |:------------- |:------------- |
  |2IOPS/GB |이 옵션은 가장 일반적인 워크로드를 위해 설계되었습니다. 애플리케이션 예로 소형 데이터베이스 호스팅, 웹 애플리케이션 백업 또는 하이퍼바이저용 가상 머신 디스크 이미지가 있습니다. |
  |4IOPS/GB |이 옵션은 동시에 활성 데이터의 높은 백분율을 보유한 고강도 워크로드를 위해 설계되었습니다. 애플리케이션 예로 트랜잭션 데이터베이스가 있습니다. |
  |10IOPS/GB |이 옵션은 분석과 같이 가장 처리가 어려운 워크로드 유형을 위해 설계되었습니다. 애플리케이션 예로 높은 트랜잭션 데이터베이스 및 기타 성능에 민감한 데이터베이스가 있습니다. 이 성능 레벨은 파일 공유당 4TB의 최대 용량으로 제한됩니다. |

## 네트워크 인터페이스 설정

vCenter Server 인스턴스를 주문할 때는 다음 네트워크 인터페이스 설정을 지정해야 합니다.

### 호스트 이름 접두부

호스트 이름 접두부는 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  호스트 이름 접두부는 영숫자 문자로 시작하고 끝나야 합니다.
*  호스트 이름 접두부의 최대 길이는 10자입니다.

### 하위 도메인 레이블

하위 도메인 레이블은 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  하위 도메인 레이블은 영숫자 문자로 시작하고 끝나야 합니다.
*  하위 도메인 레이블의 최대 길이는 10자입니다.
*  하위 도메인 레이블은 계정 내에서 고유해야 합니다.

### 도메인 이름

루트 도메인 이름은 다음 요구사항을 충족해야 합니다.
* 도메인 이름은 마침표(.)로 구분된 두 개 이상의 문자열로 구성되어야 합니다.
* 첫 번째 문자열은 영문자로 시작하고 영숫자로 끝나야 합니다.
* 마지막 문자열을 제외한 모든 문자열은 영숫자 및 대시(-) 문자만 포함할 수 있습니다.
* 마지막 문자열은 영문자만 포함할 수 있습니다.
* 마지막 문자열의 길이는 2 - 24자 사이여야 합니다.

**참고:** 호스트 및 VM의 완전한 도메인 이름(FQDN)의 최대 길이는 50자입니다. 도메인 이름은 이 최대 길이를 포함할 수 있어야 합니다.

### VLAN

네트워크 설정은 **새 VLAN 주문** 또는 **기존 VLAN 선택**의 선택에 따라 달라집니다.

인스턴스 주문에 한 개의 공인 VLAN 및 두 개의 사설 VLAN이 필요합니다. 두 개의 사설 VLAN이 각 Bare Metal Server에 선택됩니다.

**새 VLAN 주문**  
하나의 새 공인 VLAN 및 두 개의 새 사설 VLAN 주문을 선택하십시오.

**기존 VLAN 선택**  
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

### DNS 구성

인스턴스에 대한 DNS(Domain Name System) 구성을 선택하십시오.

* **Active Directory/DNS용 단일 공용 Windows VSI**: 호스트 및 VM이 등록된 인스턴스를 위한 DNS로 작동하는 단일 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되고 검색될 수 있습니다. 기본적으로 이 옵션은 V1.9 이상 인스턴스를 위해 배치됩니다.
* **관리 클러스터에 있는 두 개의 고가용성 전용 Windows Server VM**: 두 개의 Microsoft Windows VM이 배치되어 보안 및 강력한 추진력을 향상시킵니다.

**중요:** 두 개의 Microsoft Windows VM을 사용하도록 인스턴스를 구성하는 경우 두 개의 Microsoft Windows Server 2012 R2 라이센스를 제공해야 합니다. Microsoft Windows Server 2012 R2 Standard 에디션 라이센스, Microsoft Windows Server 2012 R2 Datacenter 에디션 라이센스 또는 둘 다 사용하십시오.

각 라이센스는 하나의 실제 서버에만 지정될 수 있고 최대 두 개의 실제 프로세서에 적용됩니다. 하나의 Standard 에디션 라이센스는 두 개의 프로세서 서버당 두 개의 가상화된 Microsoft Windows VM을 실행할 수 있습니다. 그러므로 두 개의 Microsoft Windows VM이 두 개의 서로 다른 호스트에 배치되기 때문에 두 개의 라이센스가 필요합니다.

VM을 활성화할 수 있는 30일의 기간이 제공됩니다.

Windows 라이센싱에 대한 자세한 정보는 [Windows Server 2012 R2 문서](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)를 참조하십시오.

## 서비스 설정

vCenter Server 인스턴스를 주문하는 경우 추가 서비스도 주문할 수 있습니다. 서비스에 대한 자세한 정보는 [vCenter Server 인스턴스에 대한 사용 가능 서비스](vc_addingremovingservices.html#available-services-for-vcenter-server-instances)를 참조하십시오.

## 주문 요약

인스턴스 및 추가 기능 서비스에 대해 선택한 구성에 따라 예상 비용이 즉시 생성되어 오른쪽 분할창에 있는 **주문 요약** 섹션에 표시됩니다. 예상 세부사항을 제공하는 PDF 문서를 생성하려면 오른쪽 분할창 하단에 있는 **가격 책정 세부사항**을 클릭하십시오.

## 프로시저

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에 있는 **VMware**를 클릭한 후 **가상 데이터 센터** 섹션에 있는 **vCenter Server**를 클릭하십시오.
2. **VMware vCenter Server on IBM Cloud** 페이지에서 **vCenter Server** 카드를 클릭하고 **작성**을 클릭하십시오.
3. **vCenter Server** 페이지에서 인스턴스 이름을 입력하십시오.
4. 인스턴스 유형을 선택하십시오.
   * 환경에 하나의 인스턴스를 배치하거나 다중 사이트 토폴로지에 첫 번째 인스턴스를 배치하려면 **기본 인스턴스**를 클릭하십시오.
   * 고가용성을 위해 인스턴스를 환경의 기존(기본) 인스턴스에 연결하려면 **보조 인스턴스**를 클릭하고 다음 단계를 완료하십시오.
     1. 보조 인스턴스를 연결할 기본 인스턴스를 선택하십시오.
     2. 기본 인스턴스의 PSC 관리자 비밀번호를 입력하십시오.
5. 인스턴스 컴포넌트에 대한 라이센스 설정을 완료하십시오.  
   *  IBM 제공 라이센스를 사용하려면 **구매에 포함**을 선택하고 필요한 경우 라이센스 에디션을 선택하십시오.
   *  자신의 라이센스를 사용하려면 **라이센스를 제공함**을 선택하고 라이센스 키를 입력하십시오.
6. Bare Metal Server 설정을 완료하십시오.
    1. {{site.data.keyword.CloudDataCent_notm}}를 선택하여 인스턴스를 호스팅하십시오.
    2. Bare Metal Server 구성을 선택하십시오.
       * **사전 구성됨**을 선택한 경우에는 구성에 대해 **소형**, **중형** 또는 **대형**을 선택하십시오.
       * **사용자 정의됨**을 선택한 경우에는 CPU 모델 및 RAM 크기를 지정하십시오.
    3. {{site.data.keyword.baremetal_short}}의 수를 지정하십시오. 스토리지 솔루션으로 vSAN을 사용할 계획인 경우 최소 네 개의 {{site.data.keyword.baremetal_short}}가 필요합니다.  

7. 스토리지 설정을 완료하십시오.
   * **vSAN 스토리지**를 선택하는 경우 **vSAN 용량 디스크 수**, **vSAN 용량 디스크의 디스크 유형 및 크기** 및 **vSAN 라이센스**를 제공하는 방법을 지정하십시오.
   * **NFS 스토리지**를 선택하는 경우 **공유 수**, **크기** 및 **성능**을 지정하십시오. 이 설정은 모든 파일 공유에 적용됩니다.
   * 파일 공유를 개별적으로 추가하고 구성하려면 **사용자 정의 NFS 스토리지** 탭을 선택한 다음 **NFS 추가** 레이블 옆에 있는 **+** 아이콘을 클릭하고 각 파일 공유에 대해 **크기** 및 **성능**을 선택하십시오. 하나 이상의 파일 공유를 선택해야 합니다.

8. 네트워크 인터페이스 설정을 완료하십시오.
   1. 호스트 이름 접두부, 하위 도메인 레이블 및 루트 도메인 이름을 입력하십시오. 보조 인스턴스의 경우에는 도메인 이름이 자동으로 채워집니다.
   2. VLAN 설정을 선택하십시오.
      * 새 공인 및 사설 VALN을 주문하려면 **새 VLAN 주문**을 클릭하십시오.
      * 기존 공인 및 사설 VLAN이 사용 가능한 경우 이들을 재사용하려면 **기존 VLAN 선택**을 클릭하고 VLAN 및 서브넷을 지정하십시오.
   3. DNS 구성을 지정하십시오.

9. 추가 기능 서비스 카드를 클릭하여 인스턴스에 배치할 해당 추가 기능 서비스를 선택하십시오. 서비스가 구성을 필요로 하는 경우에는 서비스 고유 설정을 완료하고 카드의 **서비스 추가**를 클릭하십시오.
서비스의 설정을 제공하는 방법에 대한 정보는 해당 서비스 주문 주제를 참조하십시오.

10. 주문하기 전에 **주문 요약** 페이지에서 인스턴스 구성을 확인하십시오.
   1. 인스턴스의 설정을 검토하십시오.
   2. 인스턴스의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 책정 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   3. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 인스턴스를 주문하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   4. **프로비저닝**을 클릭하십시오.

## 결과

인스턴스의 배치가 자동으로 시작됩니다. 주문이 처리 중이라는 확인을 받은 후 인스턴스 세부사항을 보고 배치의 상태를 확인할 수 있습니다.

인스턴스가 배치되면 [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)의 _vCenter Server 기술 스펙_ 섹션에 설명되어 있는 컴포넌트가 VMware 가상 플랫폼에 설치됩니다. 기본적으로 주문한 ESXi 서버는 **cluster1**로 그룹화됩니다. 추가 서비스를 주문한 경우 주문이 완료된 후 서비스의 배치가 시작됩니다.

인스턴스를 사용할 준비가 되면 인스턴스의 상태가 **사용할 준비**로 변경되고 이메일로 알림을 받습니다.

보조 인스턴스를 주문하는 경우 보조 인스턴스 주문이 완료된 후 기본 인스턴스(보조 인스턴스로 링크됨)의 VMware vSphere Web Client가 다시 시작될 수 있습니다.

## 수행할 작업

주문한 vCenter Server 인스턴스를 보고 관리하십시오.

**중요**: {{site.data.keyword.slportal}} 또는 콘솔 외부의 다른 방법이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 {{site.data.keyword.cloud_notm}} 계정에서만 작성된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다.
{{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.

**주의**: {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트(인스턴스를 주문했을 때 {{site.data.keyword.cloud_notm}} 계정에 설치됨)를 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기
*  서비스 다시 시작

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

## 관련 링크

* [{{site.data.keyword.cloud_notm}} 계정 등록](../vmonic/signing_softlayer_account.html)
* [vCenter Server 인스턴스 보기](vc_viewinginstances.html)
* [vCenter Server 인스턴스에 대한 다중 사이트 구성](vc_multisite.html)
* [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](vc_addingviewingclusters.html)
* [vCenter Server 인스턴스에 대한 용량 확장 및 축소](vc_addingremovingservers.html)
* [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](vc_addingremovingservices.html)
* [vCenter Server 인스턴스 삭제](vc_deletinginstance.html)
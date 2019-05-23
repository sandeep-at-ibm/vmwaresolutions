---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle 인스턴스 주문
{: #vc_hybrid_orderinginstance}

워크로드 요구사항에 가장 적합한 유연하고 사용자 정의할 수 있는 VMware 가상화된 플랫폼을 배치하려면 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 인스턴스를 주문하십시오. vCenter Server with Hybridity Bundle 인스턴스 주문에는 VMware Hybrid Cloud Extension(HCX) 라이센싱이 포함되며, 이는 사용자에게 VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 사용할 수 있는 자격을 부여합니다. 재해 복구를 위한 [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)와 같은 서비스를 추가할 수도 있습니다.

## vCenter Server with Hybridity Bundle 인스턴스 주문 요구사항
{: #vc_hybrid_orderinginstance-req}

다음 태스크를 완료했는지 확인하십시오.
*  **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정 관리](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)를 참조하십시오.
*  [vCenter Server with Hybridity Bundle에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)의 정보를 검토했습니다.
* 인스턴스 및 도메인 이름 형식을 검토했습니다. 도메인 이름 및 하위 도메인 레이블은 인스턴스의 사용자 이름 및 서버 이름을 생성하는 데 사용됩니다.

표 1. 인스턴스 및 도메인 이름의 값 형식

|이름        |값 형식      |
  |:------------- |:------------- |
  |도메인 이름 | `<root_domain>` |  
  |vCenter Server 로그인 사용자 이름 | `<user_id>@<root_domain>`(Microsoft Active Directory 사용자) 또는 `administrator@vsphere.local` |
  |vCenter Server(임베디드 PSC 포함) FQDN | `vcenter-<subdomain_label>.<subdomain_label>.<root_domain>`. 최대 길이는 50자입니다. |
  |SSO(Single Sign-On) 사이트 이름 | `<subdomain_label>` |
  |완전한 ESXi 서버 이름 | `<host_prefix><n>.<subdomain_label>.<root_domain>`, 여기서 `<n>`은 ESXi 서버의 순서입니다. 최대 길이는 50자입니다. |

인스턴스 주문 또는 배치 중에 설정되는 값은 수정하지 마십시오. 수정하는 경우 인스턴스를 사용할 수 없게 됩니다. 예를 들어, 공용 네트워킹이 종료되는 경우, 서버 및 가상 서버 인스턴스(VSI)가 Vyatta 뒤로 이동하는 경우, IBM CloudBuilder VSI가 중지하거나 삭제된 경우입니다.
{:important}

## 시스템 설정
{: #vc_hybrid_orderinginstance-sys-settings}

vCenter Server with Hybridity Bundle 인스턴스를 주문할 때는 다음 시스템 설정을 지정해야 합니다.

### 인스턴스 이름
{: #vc_hybrid_orderinginstance-inst-name}

인스턴스 이름은 다음 요구사항을 충족해야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 인스턴스 이름은 영문자로 시작하고 영숫자로 끝나야 합니다.
* 인스턴스 이름의 최대 길이는 10자입니다.
* 인스턴스 이름은 계정 내에서 고유해야 합니다.

### VMware vSphere 라이센스
{: #vc_hybrid_orderinginstance-vsphere-license}

vSphere Enterprise Plus 6.7u1 또는 vSphere Enterprise Plus 6.5u2를 주문할 것인지 여부를 선택하십시오.

vSphere Enterprise Plus 6.7u1은 Broadwell 및 Skylake {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}용으로만 사용 가능합니다.
{:note}

### 기본 또는 보조
{: #vc_hybrid_orderinginstance-primary-secondary}

새 기본 인스턴스를 주문할지 또는 기존 기본 인스턴스의 보조 인스턴스를 주문할지 선택하십시오.

## 라이센스 부여 설정
{: #vc_hybrid_orderinginstance-licensing-settings}

vCenter Server with Hybridity Bundle 인스턴스 주문에는 다음 VMware 라이센스가 포함됩니다. NSX 및 vSAN 라이센스에 대한 에디션을 지정해야 합니다.

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5 또는 6.7
* NSX Service Providers 6.4(Advanced 또는 Enterprise 에디션)
* vSAN 6.6(Advanced 또는 Enterprise 에디션)

### 주의
{: #vc_hybrid_orderinginstance-attention}

* vCenter Server with Hybridity Bundle 인스턴스는 고유한 라이센스 가져오기(BYOL)를 지원하지 않습니다.
* 최소 라이센스 에디션은 사용자 인터페이스에 표시됩니다. 다른 컴포넌트 에디션이 지원되는 경우 원하는 에디션을 선택할 수 있습니다.

## Bare Metal Server 설정
{: #vc_hybrid_orderinginstance-bare-metal-settings}

Bare Metal Server 설정은 {{site.data.keyword.CloudDataCent_notm}}의 선택 및 Bare Metal Server 구성을 기반으로 합니다.

vSAN 구성의 초기 및 사후 배치 클러스터 모두에 네 개의 ESXi 서버가 필요합니다. 모든 ESXi 서버는 동일한 구성을 공유합니다. 사후 배치에서 네 개의 추가 클러스터를 추가할 수 있습니다.

### 데이터 센터 위치
{: #vc_hybrid_orderinginstance-dc-location}

인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.

### Skylake
{: #vc_hybrid_orderinginstance-skylake}

**Skylake**를 선택하는 경우 필요에 따라 Bare Metal Server의 CPU 및 RAM 조합을 선택할 수 있습니다.

표 2. Skylake {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

### Broadwell
{: #vc_hybrid_orderinginstance-broadwell}

**Broadwell**을 선택하는 경우 필요에 따라 Bare Metal Server의 CPU 및 RAM 조합을 선택할 수 있습니다.

표 3. Broadwell {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 쿼드 Intel Xeon E7-4820 v4 / 총 40개의 코어, 2.0GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |
| 쿼드 Intel Xeon E7-4850 v4 / 총 64개의 코어, 2.1GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |

### Bare Metal Server 수
{: #vc_hybrid_orderinginstance-bare-metal-number}

* 주문하는 모든 서버는 동일한 구성을 갖습니다.
* 4 - 20개의 서버를 주문할 수 있습니다.

## 스토리지 설정
{: #vc_hybrid_orderinginstance-storage-settings}

vCenter Server with Hybridity Bundle 인스턴스 주문에는 VMware vSAN 6.6이 포함됩니다. 다음 vSAN 옵션을 지정하십시오.
* **vSAN 용량 디스크의 디스크 유형 및 크기**: 필요한 용량 디스크에 대한 옵션을 선택하십시오.
* **vSAN 용량 디스크 수**: 추가할 용량 디스크 수를 지정하십시오.
* 용량 디스크를 10개 한계 이상으로 추가하려는 경우 **고성능 Intel Optane** 상자를 선택하십시오. 이 옵션은 총 12개 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공하며 짧은 대기 시간과 높은 IOPS 처리량이 필요한 워크로드에 유용합니다.

  **고성능 Intel Optane** 옵션은 Skylake CPU 모델에 대해서만 사용 가능합니다.
  {:note}

* **vSAN 캐시 디스크의 디스크 유형** 및 **vSAN 캐시 디스크 수** 값을 검토하십시오. 이러한 값은 **고성능 Intel Optane** 상자를 선택했는지 여부에 따라 달라집니다.

## 네트워크 인터페이스 설정
{: #vc_hybrid_orderinginstance-network-interface-settings}

vCenter Server with Hybridity Bundle 인스턴스를 주문할 때는 다음 네트워크 인터페이스 설정을 지정해야 합니다.

### 호스트 이름 접두부
{: #vc_hybrid_orderinginstance-host-name-prefix}

  호스트 이름 접두부는 다음 요구사항을 충족해야 합니다.
  *  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
  *  호스트 이름 접두부는 영숫자 문자로 시작하고 끝나야 합니다.
  *  호스트 이름 접두부의 최대 길이는 10자입니다.

### 하위 도메인 레이블
{: #vc_hybrid_orderinginstance-subdomain-label}

하위 도메인 레이블은 다음 요구사항을 충족해야 합니다.
*  영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
*  하위 도메인 레이블은 영문자로 시작하고 영숫자로 끝나야 합니다.
*  하위 도메인 레이블의 최대 길이는 10자입니다.
*  하위 도메인 레이블은 계정 내에서 고유해야 합니다.

### 도메인 이름
{: #vc_hybrid_orderinginstance-domain-name}

루트 도메인 이름은 다음 요구사항을 충족해야 합니다.
* 도메인 이름은 마침표(.)로 구분된 두 개 이상의 문자열로 구성되어야 합니다.
* 첫 번째 문자열은 영문자로 시작하고 영숫자로 끝나야 합니다.
* 마지막 문자열을 제외한 모든 문자열은 영숫자 및 대시(-) 문자만 포함할 수 있습니다.
* 마지막 문자열은 영문자만 포함할 수 있습니다.
* 마지막 문자열의 길이는 2 - 24자 사이여야 합니다.

호스트 및 가상 머신(VM)에 대한 FQDN(Fully Qualified Domain Name)의 최대 길이는 50자입니다. 도메인 이름은 이 최대 길이를 포함할 수 있어야 합니다.
{:note}

### 공용 또는 사설 네트워크
{: #vc_hybrid_orderinginstance-public-private-network}

네트워크 인터페이스 카드(NIC) 인에이블먼트 설정은 **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 사용자의 선택을 기반으로 합니다.

**사설 네트워크 전용** 옵션을 선택하는 경우:
* VMware NSX ESG(Edge Services Gateway)는 프로비저닝되지 않습니다(관리 서비스 ESG 또는 고객 관리 ESG 모두).
* 공용 NIC가 필요한 다음 추가 서비스는 사용할 수 없습니다.
  * F5 on {{site.data.keyword.cloud_notm}}
  * Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
  * Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### 새 VLAN 주문
{: #vc_hybrid_orderinginstance-new-vlans}

**새 VLAN 주문**을 선택하여 하나의 새 공용 VLAN 및 두 개의 새 사설 VLAN을 주문하십시오.

인스턴스 주문에 한 개의 공용 VLAN 및 두 개의 사설 VLAN이 필요합니다. 두 개의 사설 VLAN이 각 Bare Metal Server에 선택됩니다.

### 기존 VLAN 선택
{: #vc_hybrid_orderinginstance-existing-vlans}

선택한 {{site.data.keyword.CloudDataCent_notm}}에 따라 기존 공용 및 사설 VLAN을 사용할 수 있습니다.

인스턴스 주문에 한 개의 공용 VLAN 및 두 개의 사설 VLAN이 필요합니다. 두 개의 사설 VLAN이 각 Bare Metal Server에 선택됩니다.

**기존 VLAN 선택**을 선택하여 기존 공용 및 사설 VLAN을 재사용하며 사용 가능한 VLAN 및 서브넷 중에서 선택하십시오.

* 선택된 VLAN의 방화벽 구성이 관리 데이터 트래픽을 차단하지 않는지 확인하십시오.
* ESXi 서버는 혼합 팟(Pod) VLAN에서 프로비저닝될 수 없으므로 선택한 모든 VLAN이 동일한 팟(Pod)에 있는지 확인하십시오.
{:important}

### DNS 구성
{: #vc_hybrid_orderinginstance-dns-config}

인스턴스에 대한 DNS(Domain Name System) 구성을 선택하십시오.

* **Active Directory/DNS용 단일 공용 Windows VSI**: 호스트 및 VM이 등록된 인스턴스를 위한 DNS로 작동하는 단일 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되고 검색될 수 있습니다.
* **관리 클러스터에 있는 두 개의 고가용성 전용 Windows Server VM**: 두 개의 Microsoft Windows VM이 배치되어 보안 및 강력한 추진력을 향상시킵니다.

두 개의 Microsoft Windows VM을 사용하도록 인스턴스를 구성하는 경우 두 개의 Microsoft Windows Server 2016 라이센스를 제공해야 합니다. Microsoft Windows Server 2016 Standard 에디션 라이센스, Microsoft Windows Server 2016 Datacenter 에디션 라이센스 또는 둘 다 사용하십시오.
{:important}

각 라이센스는 하나의 실제 서버에만 지정될 수 있고 최대 두 개의 실제 프로세서에 적용됩니다. 하나의 Standard 에디션 라이센스는 두 개의 프로세서 서버당 두 개의 가상화된 Microsoft Windows VM을 실행할 수 있습니다. 그러므로 두 개의 Microsoft Windows VM이 두 개의 서로 다른 호스트에 배치되기 때문에 두 개의 라이센스가 필요합니다.

VM을 활성화할 수 있는 30일의 기간이 제공됩니다.

Windows Server 2016 라이센스 주문에 대한 자세한 정보는 [Get started with Windows Server 2016](https://docs.microsoft.com/en-us/windows-server/get-started/server-basics){:new_window}을 참조하십시오.

## 서비스 설정
{: #vc_hybrid_orderinginstance-addon-services}

vCenter Server with Hybridity Bundle 인스턴스를 주문할 때 추가 서비스도 주문할 수 있습니다. 서비스에 대한 자세한 정보는 [vCenter Server with Hybridity Bundle 인스턴스에 대한 사용 가능 서비스](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)를 참조하십시오.

## 주문 요약
{: #vc_hybrid_orderinginstance-order-summary}

인스턴스 및 추가 기능 서비스에 대해 선택한 구성에 따라 예상 비용이 즉시 생성되어 오른쪽 분할창에 있는 **주문 요약** 섹션에 표시됩니다. 예상 세부사항을 제공하는 PDF 문서를 생성하려면 오른쪽 분할창 하단에 있는 **가격 세부사항**을 클릭하십시오.

## vCenter Server with Hybridity Bundle 인스턴스를 주문하는 프로시저
{: #vc_hybrid_orderinginstance-procedure}

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에서 **VMware**를 클릭한 후 **가상 데이터 센터** 섹션에 있는 **vCenter Server**를 클릭하십시오.
2. **VMware vCenter Server on IBM Cloud** 페이지에서 **vCenter Server with Hybridity Bundle** 카드를 클릭하고 **작성**을 클릭하십시오.
3. **vCenter Server** 페이지에서 인스턴스 이름을 입력하십시오.
5. vSphere 버전을 선택하십시오.
4. 인스턴스 유형을 선택하십시오.
   * 환경에 하나의 인스턴스를 배치하거나 다중 사이트 토폴로지에 첫 번째 인스턴스를 배치하려면 **기본 인스턴스**를 클릭하십시오.
   * 고가용성을 위해 인스턴스를 환경의 기존(기본) 인스턴스에 연결하려면 **보조 인스턴스**를 클릭하고 다음 단계를 완료하십시오.
     1. 보조 인스턴스를 연결할 기본 인스턴스를 선택하십시오.
     2. 기본 인스턴스 V2.8 이상의 경우 기본 인스턴스의 vCenter Server 관리자 비밀번호를 입력하십시오.
     3. 기본 인스턴스 V2.7 이상의 경우 기본 인스턴스의 PSC 관리자 비밀번호를 입력하십시오.
6. NSX 라이센스 에디션 및 vSAN 라이센스 에디션을 선택하십시오.
7. Bare Metal Server 설정을 완료하십시오.
  1. {{site.data.keyword.CloudDataCent_notm}}를 선택하여 인스턴스를 호스팅하십시오.
  2. **Skylake** 또는 **Broadwell** CPU 모델 및 **RAM** 크기를 선택하십시오.
8. 스토리지 구성을 완료하십시오. 용량 및 캐시 디스크에 대한 디스크 유형과 디스크 수를 지정하십시오. 더 많은 스토리지를 원하는 경우 **고성능 Intel Optane** 상자를 선택하십시오.
9. 네트워크 인터페이스 구성을 완료하십시오.
  1. 호스트 이름 접두부(프로비저닝되는 인스턴스용), 하위 도메인 레이블 및 루트 도메인 이름을 입력하십시오.
  2. **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 네트워크 설정을 선택하십시오.
  3. VLAN 구성을 선택하십시오.
     *  새 공용 및 사설 VALN을 주문하려면 **새 VLAN 주문**을 클릭하십시오.
     *  기존 공용 및 사설 VALN이 사용 가능한 경우 이들을 재사용하려면 **기존 VLAN 선택**을 클릭한 후 공용 VLAN, 기본 서브넷, 사설 VLAN, 사설 기본 서브넷 및 보조 사설 VLAN을 선택하십시오.
  4. DNS 구성을 선택하십시오.
10. 포함된 HCX on {{site.data.keyword.cloud_notm}} 서비스에 대해 구성을 완료하십시오. 서비스에 대한 설정을 제공하는 데 대한 자세한 정보는 [VMware HCX on IBM Cloud 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering#vmware-hcx-on-ibm-cloud-configuration)의 _VMware HCX on IBM Cloud 구성_ 섹션을 참조하십시오.
11. 추가 기능 서비스 카드를 클릭하여 인스턴스에 배치할 해당 추가 기능 서비스를 선택하십시오. 서비스가 구성을 필요로 하는 경우에는 서비스 고유 설정을 완료하고 카드의 **서비스 추가**를 클릭하십시오.  
서비스의 설정을 제공하는 방법에 대한 자세한 정보는 해당 서비스 주문 주제를 참조하십시오.

12. 주문하기 전에 **주문 요약** 페이지에서 인스턴스 구성을 확인하십시오.
   1. 인스턴스의 설정을 검토하십시오.
   2. 인스턴스의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   3. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 인스턴스를 주문하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   4. **프로비저닝**을 클릭하십시오.

## 결과
{: #vc_hybrid_orderinginstance-results}

인스턴스의 배치가 자동으로 시작됩니다. 주문이 처리 중이라는 확인을 받은 후 인스턴스 세부사항을 보고 배치의 상태를 확인할 수 있습니다.

인스턴스가 성공적으로 배치된 경우에는 [Hybridity Bundle 인스턴스의 기술 스펙](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview#specs)에서 설명된 컴포넌트가 VMware 가상 플랫폼에 설치됩니다. 기본적으로 주문한 ESXi 서버는 **cluster1**로 그룹화됩니다. 추가 기능 서비스를 주문한 경우 주문이 완료된 후 서비스의 배치가 시작됩니다.

인스턴스를 사용할 준비가 되면 인스턴스의 상태가 **사용할 준비가 됨**으로 변경되고 이메일로 알림을 받습니다.

보조 인스턴스를 주문하는 경우 보조 인스턴스 주문이 완료된 후 기본 인스턴스(보조 인스턴스로 링크됨)의 VMware vSphere Web Client가 다시 시작될 수 있습니다.

## 수행할 작업
{: #vc_hybrid_orderinginstance-next}

주문한 vCenter Server with Hybridity Bundle 인스턴스를 보고 관리하십시오.

{{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌, {{site.data.keyword.vmwaresolutions_short}} 콘솔에서만 {{site.data.keyword.cloud_notm}} 계정에 작성되는 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다.
{{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.
{:important}

**주의:** {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트(인스턴스 주문 시 {{site.data.keyword.cloud_notm}} 계정에 설치된)를 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기
*  서비스 다시 시작

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

## 관련 링크
{: #vc_hybrid_orderinginstance-related}

* [{{site.data.keyword.cloud_notm}} 계정 등록](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_softlayer_account)
* [vCenter Server with Hybridity Bundle 인스턴스 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 다중 사이트 구성](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_multisite)
* [vCenter Server with Hybridity Bundle 인스턴스의 클러스터 추가 및 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingviewingclusters)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [vCenter Server with Hybridity Bundle 인스턴스 삭제](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletinginstance)

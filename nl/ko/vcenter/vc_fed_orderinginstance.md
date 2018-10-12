---

copyright:

  years:  2016, 2018

lastupdated: "2018-09-25"

---

# VMware Federal 인스턴스 주문

워크로드 요구사항에 가장 적합한 유연하고 사용자 정의할 수 있는 VMware 가상화된 플랫폼을 배치하려면 VMware Federal 인스턴스를 주문하십시오. VMware Federal 인스턴스는 열린 관리 연결을 끊고 배치된 인스턴스를 보호하는 데 도움을 줍니다. 

**참고:** 현재 vCenter Server 인스턴스만 VMware Federal on {{site.data.keyword.cloud}}를 지원합니다.

## VMware Federal 인스턴스를 주문하기 위한 요구사항

다음 태스크를 완료했는지 확인하십시오.
* **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성했습니다. 자세한 정보는 [사용자 계정 및 설정 관리](../vmonic/useraccount.html)를 참조하십시오.
* [VMware Federal 인스턴스에 대한 요구사항 및 계획](vc_fed_planning.html)의 정보를 검토했습니다.
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

**중요**: 인스턴스 주문 또는 배치 중에 설정된 값을 수정하지 마십시오. 수정하는 경우 인스턴스를 사용할 수 없게 됩니다. 예를 들어, 공용 네트워킹이 종료되는 경우, 서버 및 가상 서버 인스턴스(VSI)가 Vyatta 뒤로 이동하는 경우, IBM CloudBuilder VSI가 중지하거나 삭제된 경우입니다. 

## 시스템 설정

VMware Federal 인스턴스를 주문할 때는 다음 시스템 설정을 지정해야 합니다.

### 인스턴스 이름

인스턴스 이름은 다음 요구사항을 충족해야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 인스턴스 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 인스턴스 이름의 최대 길이는 10자입니다.
* 인스턴스 이름은 계정 내에서 고유해야 합니다.

### 기본 또는 보조

새 기본 인스턴스를 주문하십시오. 고가용성을 위한 보조 인스턴스 배치는 현재 지원되지 않습니다.

## 라이센스 부여 설정

다음 VMware 컴포넌트에 대한 IBM 제공 라이센스:

* vCenter Server 6.5
* vSphere Enterprise Plus 6.5u1
* NSX Service Providers 6.4(Base, Advanced 또는 Enterprise 에디션)
* (vSAN 클러스터의 경우) vSAN 6.6(Advanced 또는 Enterprise 에디션)

**주의:**

* 최소 라이센스 에디션은 사용자 인터페이스에 표시됩니다. 다른 컴포넌트 에디션이 지원되는 경우 원하는 에디션을 선택할 수 있습니다. 선택한 각 VMware 컴포넌트에 올바른 라이센스 키가 제공되었는지 확인해야 합니다.
* vSphere의 경우 라이센스 비용은 주문 시 발생하지만 라이센스 비용이 나중에 사용자 계정으로 청구됩니다.

## Bare Metal Server 설정

베어메탈 설정은 사용자 정의된 구성을 기반으로 합니다. 사전 구성된 구성을 선택하는 옵션은 현재 지원되지 않습니다.

### 데이터 센터 위치

인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.

### 사용자 정의됨

Bare Metal Server의 CPU 모델 및 RAM을 지정하십시오.

표 2. 사용자 정의된 {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 듀얼 Intel Xeon E5-2620 v4 / 총 16개의 코어, 2.1GHz | 64GB, 128GB, 256GB, 512GB |
| 듀얼 Intel Xeon E5-2650 v4 / 총 24개의 코어, 2.2GHz | 64GB, 128GB, 256GB, 512GB |
| 듀얼 Intel Xeon E5-2690 v4 / 총 28개의 코어, 2.6GHz | 64GB, 128GB, 256GB, 512GB |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

### Bare Metal Server 수

ESXi 서버의 수를 2 - 20의 범위로 구성할 수 있습니다.

모든 ESXi 서버는 동일한 구성을 공유합니다. 사후 배치에서 네 개의 추가 클러스터를 추가할 수 있습니다. vSAN 스토리지 설정의 경우에는 초기 및 사후 배치 클러스터 모두에 네 개의 서버가 필요합니다. 최소 ESXi 서버에 대한 자세한 정보는 [두 개의 노드 vCenter Server 인스턴스가 고가용성입니까?](../vmonic/faq.html#is-a-two-node-vcenter-server-instance-highly-available-)를 참조하십시오.

## 스토리지 설정

스토리지 설정은 Bare Metal Server 구성의 선택 및 스토리지 유형에 따라 달라집니다.

### vSAN 스토리지

다음 vSAN 옵션을 지정하십시오.

* **vSAN 용량 디스크의 디스크 유형 및 크기**: 필요한 용량 디스크에 대한 옵션을 선택하십시오.
* **vSAN 용량 디스크 수**: 추가할 용량 디스크 수를 지정하십시오. 
* **vSAN 캐시 디스크의 디스크 유형**: 필요한 캐시 디스크에 대한 옵션을 선택하십시오.

    **참고**: 용량 디스크를 8개 한계 이상으로 추가하려는 경우 **고성능 Intel Optane** 상자를 선택하십시오. 이 옵션은 총 10개 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공하며 짧은 대기 시간과 높은 IOPS 처리량이 필요한 워크로드에 유용합니다. **고성능 Intel Optane** 옵션은 듀얼 Intel Xeon Gold 5120 및 6140 프로세서에 대해서만 사용 가능합니다.
* **vSAN 캐시 디스크 수**: 추가할 캐시 디스크 수를 지정하십시오. 
* **vSAN 라이센스**: vSAN 6.6 라이센스 에디션(Advanced 또는 Enterprise)을 선택하십시오.

### NFS 스토리지

**NFS 스토리지**를 선택할 때 모든 공유가 동일한 설정을 사용하는 인스턴스에 대한 파일 레벨 공유 스토리지를 추가하거나 각 파일 공유에 서로 다른 구성 설정을 지정할 수 있습니다. 다음 NFS 옵션을 지정하십시오.

**참고:** 파일 공유의 수는 1 - 32 범위에 있어야 합니다.

* **공유 개별 구성**: 각 파일 공유에 대해 서로 다른 구성 설정을 지정하려면 선택하십시오.
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

### DNS 구성

인스턴스에 대한 DNS(Domain Name System) 구성을 선택하십시오.

* **Active Directory/DNS용 단일 공용 Windows VSI**: 호스트 및 가상 머신이 등록된 인스턴스를 위한 DNS로 작동하는 단일 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되고 검색될 수 있습니다.
* **관리 클러스터에 있는 두 개의 고가용성 전용 Windows Server VM**: V2.3 이상 릴리스의 경우 두 개의 Microsoft Windows 가상 머신이 배치되어 보안 및 강력한 추진력을 향상시킵니다.

**중요:** 두 개의 Microsoft Windows 가상 머신을 사용하도록 인스턴스를 구성하는 경우 두 개의 Windows Server 2012 R2 라이센스를 제공해야 합니다. Microsoft Windows Server 2012 R2 Standard 에디션 라이센스, Microsoft Windows Server 2012 R2 Datacenter 에디션 라이센스 또는 둘 다 사용하십시오.

현재 각 라이센스는 단 하나의 실제 서버에 지정될 수 있으며 최대 두 개의 실제 프로세서를 포함합니다. 하나의 Standard 에디션 라이센스를 사용하면 2 프로세서 서버당 두 개의 가상화된 Microsoft Windows 가상 머신(VM)을 실행할 수 있습니다. 따라서 두 개의 Microsoft Windows 가상 머신이 두 개의 다른 호스트에 배치되기 때문에 두 개의 라이센스가 필요합니다.

가상 머신을 활성화할 수 있는 30일의 기간이 제공됩니다.

Windows 라이센싱 주문에 대한 자세한 정보는 [Windows Server 2012 R2 문서](https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx#tab=2)를 참조하십시오.

## 주문 요약

인스턴스에 대해 선택한 구성에 따라 예상 비용이 즉시 생성되어 오른쪽 분할창에 있는 **주문 요약** 섹션에 표시됩니다. 예상 세부사항을 제공하는 PDF 문서를 생성하려면 오른쪽 분할창 하단에 있는 **가격 세부사항**을 클릭하십시오.

## VMware Federal 인스턴스를 주문하는 프로시저

1. {{site.data.keyword.cloud_notm}} 카탈로그의 왼쪽 탐색 분할창에서 **VMware**를 클릭한 후 **가상 데이터 센터** 섹션에 있는 **vCenter Server**를 클릭하십시오.
2. **VMware vCenter Server on IBM Cloud** 페이지에서 **vCenter Server** 카드를 클릭하고 **작성**을 클릭하십시오.
3. **vCenter Server** 페이지에서 인스턴스 이름을 입력하십시오.
4. 환경에 하나의 인스턴스를 배치하려면 **기본 인스턴스**를 클릭하십시오.
5. VMware NSX 라이센스 에디션을 지정하십시오.
6. Bare Metal Server 구성을 완료하십시오.
  1. {{site.data.keyword.CloudDataCent_notm}}를 선택하여 인스턴스를 호스팅하십시오.
  2. **사용자 정의됨** CPU 모델 및 **RAM** 양을 선택하십시오.
7. 스토리지 구성을 완료하십시오.
  * **vSAN 스토리지**를 선택하는 경우 용량 및 캐시 디스크의 디스크 유형과 디스크 수 및 vSAN License 에디션을 지정하십시오. 더 많은 스토리지를 원하는 경우 **고성능 Intel Optane** 상자를 선택하십시오.
  * **NFS 스토리지**를 선택하고 모든 파일 공유에 동일한 설정을 추가하여 구성하려는 경우에는 **공유 수**, **크기** 및 **성능**을 지정하십시오.
  * **NFS 스토리지**를 선택하고 파일 공유를 개별적으로 추가하여 구성하려는 경우에는 **공유 개별 구성**을 선택한 후, **NFS 추가** 레이블 옆에 있는 **+** 아이콘을 클릭하고 각 개별 파일 공유에 대한 **크기** 및 **성능**을 선택하십시오. 하나 이상의 파일 공유를 선택해야 합니다.
8. 네트워크 인터페이스 구성을 완료하십시오.
   1. 호스트 이름 접두부, 하위 도메인 레이블 및 루트 도메인 이름을 입력하십시오.
   2. DNS 구성을 선택하십시오.
9. 주문하기 전에 **주문 요약** 페이지에서 인스턴스 구성을 확인하십시오.
   1. 인스턴스의 설정을 검토하십시오.
   2. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 인스턴스를 주문하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   3. **비용 계산**에서 비용 링크를 클릭하여 인스턴스의 예상 비용을 검토하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   4. **프로비저닝**을 클릭하십시오.

## 결과

인스턴스의 배치가 자동으로 시작됩니다. 주문이 처리 중이라는 확인을 받은 후 인스턴스 세부사항을 보고 배치의 상태를 확인할 수 있습니다.

인스턴스가 성공적으로 배치된 경우에는 [VMware Federal on {{site.data.keyword.cloud_notm}} 인스턴스의 기술 스펙](vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances)에서 설명된 컴포넌트가 VMware 가상 플랫폼에 설치됩니다. 기본적으로 주문한 ESXi 서버는 **cluster1**로 그룹화됩니다.

인스턴스를 사용할 준비가 되면 인스턴스의 상태가 **사용할 준비가 됨**으로 변경되고 이메일로 알림을 받습니다.

## 수행할 작업

주문한 VMware Federal 인스턴스를 보고, 관리하고 보호하십시오.

**중요:** {{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서만 {{site.data.keyword.cloud_notm}} 계정에 작성된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다.
{{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.

**주의:** {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트(인스턴스 주문 시 {{site.data.keyword.cloud_notm}} 계정에 설치된)를 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

### 관련 링크

* [{{site.data.keyword.cloud_notm}} 계정 등록](../vmonic/signing_softlayer_account.html)
* [VMware Federal 인스턴스 보기](vc_fed_viewinginstance.html)
* [VMware Federal 인스턴스에 대한 용량 확장 및 축소](vc_fed_addingremovingservers.html)
* [VMware Federal 인스턴스의 클러스터 추가, 보기 및 삭제](fed_addviewdeleteclusters.html)
* [VMware Federal 인스턴스 보호](vc_fed_securinginstance.html)
* [VMware Federal 인스턴스 삭제](vc_fed_deletinginstance.html)
* [IBM 지원 센터에 문의](../vmonic/trbl_support.html)

---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제
{: #vc_addingviewingclusters}

인스턴스를 주문할 때 구성한 ESXi 서버는 기본적으로 **cluster1**로 그룹화됩니다.

클러스터를 VMware vCenter Server 인스턴스에 추가하여 컴퓨팅 및 스토리지 용량을 확장할 수 있습니다. 클러스터 내에서 향상된 리소스 할당 및 고가용성을 위해 ESXi 서버를 관리할 수 있습니다. 더 이상 필요하지 않은 경우에는 인스턴스에서 추가된 클러스터를 삭제하십시오.

클러스터 삭제 기능은 V2.3 이상에 배치되는(또는 업그레이드되는) 인스턴스에 대해서만 사용 가능합니다.
{:note}

## vCenter Server 인스턴스에 클러스터 추가
{: #vc_addingviewingclusters-adding}

### 클러스터를 추가하기 전에
{: #vc_addingviewingclusters-before-add}

* 가능하면 {{site.data.keyword.vmwaresolutions_full}} 콘솔을 사용하여 클러스터를 추가하십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않기 때문입니다. 따라서 온프레미스 클러스터 서버 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 관리할 수 없거나 관리하지 않을 클러스터에 대해서만 클러스터를 vCenter Server에 추가하십시오.
* V2.5 이상에 배치된(또는 업그레이드된) 인스턴스의 경우에는 클러스터, 호스트 및 VM 수가 추가할 수 있는 클러스터 수의 최대 제한을 결정합니다. 배치를 위해 VMware 크기 조정 가이드라인 및 제한사항을 계속 준수해야 합니다. 최대 제한에 대한 자세한 정보는 [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}를 참조하십시오.
* V2.2, 2.3 또는 2.4 이상에 배치된(또는 업그레이드된) 인스턴스의 경우에는 최대 10개의 클러스터를 추가할 수 있습니다.
* V2.1 이하에 배치된 인스턴스의 경우 최대 5개의 클러스터를 추가할 수 있습니다.

### 시스템 설정
{: #vc_addingviewingclusters-adding-sys-settings}

vCenter Server 인스턴스에 클러스터를 추가할 때는 다음 설정을 지정해야 합니다.

#### 클러스터 이름
{: #vc_addingviewingclusters-adding-cluster-name}

클러스터 이름은 다음 요구사항을 충족해야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 클러스터 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 최대 문자 수는 30자입니다.
* 클러스터 이름은 vCenter Server 인스턴스 내에서 고유해야 합니다.

#### 데이터 센터 위치
{: #vc_addingviewingclusters-adding-dc-location}

기본적으로 클러스터의 {{site.data.keyword.CloudDataCent}} 위치는 vCenter Server 인스턴스의 {{site.data.keyword.CloudDataCent_notm}}로 설정됩니다. 배치된 인스턴스와 다른 {{site.data.keyword.CloudDataCent_notm}}에 클러스터를 배치할 수 있으나 두 {{site.data.keyword.CloudDataCents_notm}} 간의 네트워크 대기 시간이 150밀리초 미만인지 확인해야 합니다. 네트워크 대기 시간을 확인하기 위해 [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass)와 같은 도구를 사용할 수 있습니다.

다른 {{site.data.keyword.CloudDataCent_notm}} 또는 {{site.data.keyword.cloud_notm}} 인프라 팟(Pod)에 클러스터를 배치하는 경우에는 주문된 {{site.data.keyword.baremetal_short}}와 함께 사용할 세 개의 추가 VLAN이 주문됩니다.

### Bare Metal Server 설정
{: #vc_addingviewingclusters-bare-metal-settings}

**Skylake**, **SAP 인증** 또는 **Broadwell**을 선택할 수 있습니다. 옵션은 인스턴스가 처음에 배치된 버전에 따라 다를 수 있습니다.

#### Skylake
{: #vc_addingviewingclusters-adding-skylake}

**Skylake** 설정의 경우 **CPU 모델** 및 **RAM**에 대한 옵션이 있습니다. 사용 가능한 옵션은 인스턴스가 처음에 배치된 버전에 따라 다를 수 있습니다.

표 1. Skylake {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

#### SAP 인증
{: #vc_addingviewingclusters-adding-sap}

**SAP 인증**을 선택하는 경우 CPU 또는 RAM 설정을 변경할 수 없습니다.

자신의 요구사항에 따라 Bare Metal Server 구성을 선택하십시오.
* 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 192GB RAM
* 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 384GB RAM
* 듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개 코어, 2.3GHz / 768GB RAM
* 듀얼 Intel Xeon E5-2690 v4 프로세서 / 총 28개의 코어, 2.6GHz / 512GB RAM
* 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.2GHz / 1024GB RAM
* 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.2GHz / 2048GB RAM
* 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.2GHz / 4096GB RAM

#### Broadwell
{: #vc_addingviewingclusters-adding-broadwell}

**Broadwell** 설정의 경우 **CPU 모델** 및 **RAM**에 대한 몇 가지 옵션이 있습니다. 사용 가능한 옵션은 인스턴스가 처음에 배치된 버전에 따라 다를 수 있습니다.

표 2. Broadwell {{site.data.keyword.baremetal_short}}의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 쿼드 Intel Xeon E7-4820 v4 / 총 40개의 코어, 1.9GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |
| 쿼드 Intel Xeon E7-4850 v4 / 총 64개의 코어, 2.2GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |

#### Bare Metal Server 수
{: #vc_addingviewingclusters-adding-bare-metal-number}

* 주문하는 모든 서버는 동일한 구성을 갖습니다.
* vSAN 스토리지의 경우 4 - 59개의 서버를 주문할 수 있습니다.
* NFS 스토리지의 경우 2 - 59개의 서버를 주문할 수 있습니다. 그러나 프로덕션 워크로드의 경우 최소 3개의 서버가 권장됩니다. 자세한 정보는 [두 개의 노드 vCenter Server 인스턴스는 고가용성입니까?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#is-a-two-node-vcenter-server-instance-highly-available-)를 참조하십시오.

### 스토리지 설정
{: #vc_addingviewingclusters-adding-storage-settings}

스토리지 설정은 Bare Metal Server 구성의 선택 및 스토리지 유형에 따라 달라집니다.

#### vSAN 스토리지
{: #vc_addingviewingclusters-adding-vsan-storage}

다음 vSAN 옵션을 지정하십시오.
* **vSAN 용량 디스크의 디스크 유형 및 크기**: 필요한 용량 디스크에 대한 옵션을 선택하십시오.
* **vSAN 용량 디스크 수**: 추가할 용량 디스크 수를 지정하십시오.
* 용량 디스크를 10개 한계 이상으로 추가하려는 경우 **고성능 Intel Optane** 상자를 선택하십시오. 이 옵션은 총 12개 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공하며 짧은 대기 시간과 높은 IOPS 처리량이 필요한 워크로드에 유용합니다.

  **고성능 Intel Optane** 옵션은 Skylake CPU 모델에 대해서만 사용 가능합니다.
  {:note}

* **vSAN 캐시 디스크의 디스크 유형** 및 **vSAN 캐시 디스크 수** 값을 검토하십시오. 이러한 값은 **고성능 Intel Optane** 상자를 선택했는지 여부에 따라 달라집니다.
* **vSAN 라이센스**: **구매에 포함**을 선택하여 vSAN 컴포넌트에 대한 IBM 제공 VMware 라이센스를 사용하거나, **라이센스를 제공함**을 선택하고 고유한 라이센스 키를 입력하여 고유한 라이센스를 가져오십시오(BYOL).

초기 클러스터가 vSAN 클러스터인 경우 추가 vSAN 클러스터는 초기 vSAN 클러스터와 동일한 vSAN 라이센스를 사용하며 동일한 구성을 갖습니다. 인스턴스의 클러스터가 클러스터(초기 또는 추가)에 배치되도록 선택된 vSAN을 보유하고 있는 경우에도 true입니다. 처음에는 vSAN 라이센스(BYOL 또는 구매함) 및 에디션에 대한 프롬프트가 표시됩니다. 그 다음에 새 클러스터에 대한 vSAN을 선택하면 처음에 선택한 항목이 다시 사용됩니다.

#### NFS 스토리지
{: #vc_addingviewingclusters-adding-nfs-storage}

**NFS 스토리지**를 선택할 때 모든 공유가 동일한 설정을 사용하는 인스턴스에 대한 파일 레벨 공유 스토리지를 추가하거나 각 파일 공유에 서로 다른 구성 설정을 지정할 수 있습니다. 다음 NFS 옵션을 지정하십시오.

파일 공유의 수는 1 - 32 사이여야 합니다.
{:note}

* **공유 개별 구성**: 각 파일 공유에 대해 서로 다른 구성 설정을 지정하려면 선택하십시오.
* **공유 수**: 각 파일 공유에 동일한 구성 설정을 사용하려는 경우 추가할 NFS 공유 스토리지에 대한 파일 공유 수를 지정하십시오.
* **크기**: 공유 스토리지 요구사항을 충족하는 용량을 선택하십시오.
* **성능**: 워크로드 요구사항에 기반한 GB당 IOPS(Input/output Operations Per Second)를 선택하십시오.
* **NFS 추가**: 다른 구성 설정을 사용하는 개별 파일 공유를 추가하도록 선택하십시오.

표 3. NFS 성능 레벨 옵션

|옵션        |세부사항       |
  |:------------- |:------------- |
  |0.25 IOPS/GB |이 옵션은 자주 사용되지 않는 워크로드를 위해 설계되었습니다. 예제 애플리케이션에는 보관된 데이터, 호스팅하는 대형 데이터베이스(레거시 데이터 포함) 또는 백업으로서의 가상 메모리 시스템의 가상 디스크 이미지가 포함됩니다. |
  |2IOPS/GB |이 옵션은 가장 일반적인 워크로드를 위해 설계되었습니다. 애플리케이션 예로 소형 데이터베이스 호스팅, 웹 애플리케이션 백업 또는 하이퍼바이저용 가상 머신(VM) 디스크 이미지가 있습니다. |
  |4IOPS/GB |이 옵션은 동시에 활성 데이터의 높은 백분율을 보유한 고강도 워크로드를 위해 설계되었습니다. 애플리케이션 예로 트랜잭션 데이터베이스가 있습니다. |
  |10IOPS/GB |이 옵션은 분석과 같이 가장 처리가 어려운 워크로드 유형을 위해 설계되었습니다. 애플리케이션 예로 높은 트랜잭션 데이터베이스 및 기타 성능에 민감한 데이터베이스가 있습니다. 이 성능 레벨은 파일 공유당 4TB의 최대 용량으로 제한됩니다. |

### 로컬 디스크
{: #vc_addingviewingclusters-adding-local-disks}

로컬 디스크 옵션은 **SAP 인증** 쿼드 Intel Xeon E7-8890 v4 프로세서 베어메탈 구성에만 사용할 수 있습니다. 다음 옵션을 지정하십시오.
* **디스크 수**: 추가할 용량 디스크 수를 선택하십시오.
* **디스크 유형**: 필요한 디스크 유형에 대한 옵션을 선택하십시오.

### 라이센스 부여 설정
{: #vc_addingviewingclusters-adding-licensing-settings}

클러스터에 있는 VMware vSphere 컴포넌트에 대한 라이센싱 옵션을 지정하십시오.
* 비즈니스 파트너 사용자의 경우, vSphere 라이센스(Enterprise Plus 에디션)가 사용자를 대신하여 포함 및 구매됩니다.
* 비즈니스 파트너가 아닌 사용자의 경우에는 **구매에 포함**을 선택하여 이 컴포넌트에 대해 IBM 제공 VMware 라이센스를 사용하거나, **라이센스를 제공함**을 선택하고 자신의 라이센스 키를 입력하여 BYOL(Bring Your Own License)을 사용할 수 있습니다.

### 네트워크 인터페이스 설정
{: #vc_addingviewingclusters-adding-network-interface-settings}

네트워크 인터페이스 카드(NIC) 인에이블먼트 설정은 **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 사용자의 선택을 기반으로 합니다. 다음과 같은 추가 기능 서비스에는 공용 NIC가 필요하며 개인용 옵션을 선택하는 경우에는 서비스를 사용할 수 없습니다.

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### 주문 요약
{: #vc_addingviewingclusters-adding-order-summary}

클러스터에 대해 선택한 구성에 따라 예상 비용이 즉시 생성되어 **주문 요약** 오른쪽 분할창에 표시됩니다.

## vCenter Server 인스턴스에 클러스터를 추가하는 프로시저
{: #vc_addingviewingclusters-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 클러스터를 추가할 인스턴스를 클릭하십시오.

   인스턴스가 **사용할 준비가 됨** 상태인지 확인하십시오. 그렇지 않으면, 클러스터를 인스턴스에 추가할 수 없습니다.
   {:note}
3. 왼쪽 탐색 분할창의 **인프라**를 클릭하고 **클러스터** 테이블의 오른쪽 상단 모서리에 있는 **추가**를 클릭하십시오.
4. **클러스터 추가** 페이지에서 인스턴스 이름을 입력하십시오.
5. 인스턴스가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}와 다른 IBM Cloud Data Center에서 클러스터를 호스팅하려면 **Bare Metal Server**에서 **다른 위치 선택** 선택란을 선택하고 인스턴스를 호스팅할 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.
6. 베어메탈 구성을 완료하십시오.
   * **Skylake** 또는 **Broadwell**을 선택한 경우 **CPU 모델**, **RAM** 크기 및 **{{site.data.keyword.baremetal_short}} 수**를 지정하십시오.
   * **SAP 인증**을 선택한 경우 CPU 모델을 지정하십시오.
7. 스토리지 구성을 완료하십시오.
  * **vSAN 스토리지**를 선택하는 경우 용량 및 캐시 디스크의 디스크 유형과 디스크 수 및 vSAN License 에디션을 지정하십시오. 더 많은 스토리지를 원하는 경우 **고성능 Intel Optane** 상자를 선택하십시오.
  * **NFS 스토리지**를 선택하고 모든 파일 공유에 동일한 설정을 추가하여 구성하려는 경우에는 **공유 수**, **성능** 및 **크기(GB)**를 지정하십시오.
  * **NFS 스토리지**를 선택하고 개별적으로 파일 공유를 추가하고 구성하려는 경우에는 **개별 공유 구성**을 선택하십시오. 그런 다음, **공유 스토리지 추가** 레이블 옆에 있는 **+** 아이콘을 클릭하고 각 파일 공유에 대해 **성능** 및 **크기(GB)**를 선택하십시오. 하나 이상의 파일 공유를 선택해야 합니다.
  * **로컬 디스크**를 선택하는 경우 디스크 수와 디스크 유형을 지정하십시오.
8. 네트워크 인터페이스 설정을 완료하십시오.
8. vSphere 라이센스 키의 제공 방법을 지정하십시오.
  * 비즈니스 파트너 사용자의 경우, vSphere 라이센스(Enterprise Plus 에디션)가 사용자를 대신하여 포함 및 구매됩니다.
  * 비즈니스 파트너가 아닌 사용자의 경우에는 다음 옵션 중 하나를 선택할 수 있습니다.
      * 사용자 대신 새 라이센스를 구매하도록 하려는 경우에는 컴포넌트에 대해 **구매에 포함**을 선택하십시오.
      * 컴포넌트에 대해 자신의 VMware 라이센스를 사용하려는 경우에는 **라이센스를 제공함**을 선택하고 라이센스 키를 입력하십시오.
9. **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 네트워크 설정을 선택하십시오.
10. 클러스터를 추가하기 전에 **주문 요약** 페이지에서 클러스터 구성을 확인하십시오.
   1. 클러스터의 설정을 검토하십시오.
   2. 클러스터의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   3. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 클러스터를 추가하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   4. **프로비저닝**을 클릭하십시오.

### vCenter Server 인스턴스에 클러스터를 추가한 후의 결과
{: #vc_addingviewingclusters-adding-results}

1. 클러스터의 배치가 자동으로 시작되며 클러스터의 상태가 **초기화 중**으로 변경됩니다. 인스턴스의 **요약** 페이지에서 배치 히스토리를 보고 배치의 상태를 확인할 수 있습니다.
2. 클러스터를 사용할 준비가 되면 클러스터의 상태가 **사용할 준비가 됨**으로 변경됩니다. 새로 추가된 클러스터는 vSphere HA(High Availability) 및 vSphere DRS(Distributed Resource Scheduler)로 사용 가능합니다.

클러스터 이름은 변경할 수 없습니다. 클러스터 이름을 변경하면 클러스터의 ESXi 서버 오퍼레이션을 추가하거나 제거하는 데 실패할 수 있습니다.
{:important}

## vCenter Server 인스턴스의 클러스터를 보는 프로시저
{: #vc_addingviewingclusters-viewing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 클러스터를 볼 인스턴스를 클릭하십시오.
3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오. **CLUSTERS** 테이블에서 클러스터에 대한 요약을 보십시오.
  * **이름**: 클러스터의 이름입니다.
  * **ESXi 서버**: 클러스터에 있는 ESXi 서버의 수입니다.
  * **CPU**: 클러스터에 있는 ESXi 서버의 CPU 스펙입니다.
  * **사용자 정의된 vSAN 디스크**: 클러스터에 있는 vSAN 디스크의 수로, 디스크 유형 및 용량이 포함됩니다.
  * **메모리**: 클러스터에 있는 ESXi 서버의 총 메모리 크기입니다.
  * **데이터 센터 위치**: 클러스터가 호스팅되는 {{site.data.keyword.CloudDataCent_notm}}입니다.
  * **팟(Pod)**: 클러스터가 배치된 팟(Pod)입니다.
  * **상태**: 클러스터의 상태입니다. 상태는 다음 값 중 하나를 포함할 수 있습니다.
    <dl class="dl">
        <dt class="dt dlterm">초기화 중</dt>
        <dd class="dd">클러스터가 작성 및 구성 중입니다.</dd>
        <dt class="dt dlterm">수정 중</dt>
        <dd class="dd">클러스터가 수정 중입니다.</dd>
        <dt class="dt dlterm">사용할 준비가 됨</dt>
        <dd class="dd">인스턴스를 사용할 준비가 되었습니다.</dd>
        <dt class="dt dlterm">삭제 중</dt>
        <dd class="dd">클러스터가 삭제되는 중입니다.</dd>
        <dt class="dt dlterm">삭제됨</dt>
        <dd class="dd">클러스터가 삭제되었습니다.</dd>
    </dl>
  * **조치**: **삭제** 아이콘을 클릭하여 클러스터를 삭제하십시오.
4. 클러스터 이름을 클릭하여 ESXi 서버, 스토리지 및 네트워크 인터페이스 세부사항을 보십시오.

표 4. ESXi 서버 세부사항

| 항목        | 설명       |  
|:------------- |:------------- |
|이름 | ESXi 서버의 이름은 다음 형식으로 되어 있습니다.<br> `<host_prefix><n>.<subdomain_label>.<root_domain>` <br> 여기서,<br> `host_prefix`는 호스트 이름 접두부이고<br> `n`은 서버의 순서이며<br> `subdomain_label`은 하위 도메인 레이블이고<br> `root_domain`은 루트 도메인 이름입니다. |
|버전 |ESXi 서버의 버전입니다. |
|인증 정보 |ESXi 서버에 액세스하는 데 사용되는 사용자 이름 및 비밀번호입니다. |
|사설 IP |ESXi 서버의 사설 IP 주소입니다. |
|상태 |ESXi 서버의 상태이며, 다음 값 중 하나일 수 있습니다.<br> **추가됨** ESXi 서버가 추가되었으며 사용할 준비가 되었습니다.<br> **추가 중** ESXi 서버가 추가되고 있습니다.<br> **삭제 중** ESXi 서버가 삭제되고 있습니다. |

표 5. 스토리지 세부사항

| 항목        | 설명       |  
|:------------- |:------------- |
|이름 |데이터 저장소 이름입니다. |
|크기 |스토리지의 용량입니다. |
|IOPS/GB |스토리지의 성능 레벨입니다. |
|NFS 프로토콜 |스토리지의 NFS 버전입니다. |

표 6. 네트워크 인터페이스 - VLAN 세부사항

| 항목        | 설명       |  
|:------------- |:------------- |
| VLAN 번호 | 고유한 VLAN 번호입니다.  |
| 설명 | VLAN의 설명입니다.  |
| 위치 | 데이터 센터 위치입니다. |
| 기본 라우트 | VLAN의 기본 라우트입니다. |

VLAN 세부사항에 액세스하려면 **리소스 보기**를 클릭하십시오.

표 7. 네트워크 인터페이스 - 서브넷 세부사항

| 항목        | 설명       |  
|:------------- |:------------- |
|이름 | 서브넷 이름입니다. 서브넷 세부사항에 액세스하려면 이름을 클릭하십시오. |
|유형 | 서브넷의 유형: 기본 또는 포터블. |
|설명 | 서브넷의 설명입니다. |

표 8. 네트워크 인터페이스 - IP 세부사항

| 항목        | 설명       |  
|:------------- |:------------- |
| IP | IP 주소입니다. |
|상태 | IP 주소의 상태입니다. |
|설명 | IP 주소의 설명입니다.  |

## vCenter Server 인스턴스에서 클러스터 삭제
{: #vc_addingviewingclusters-deleting}

더 이상 필요하지 않은 경우 인스턴스에서 클러스터를 삭제할 수 있습니다.

### 클러스터를 삭제하기 전에
{: #vc_addingviewingclusters-deleting-prereq}

* 이 프로시저를 사용하여 V2.3 이상으로 배치되는 인스턴스에서 클러스터를 삭제하십시오.
* V2.2 이하 인스턴스에 배치된 클러스터의 경우에는 인스턴스에 추가한 클러스터를 삭제하려면 인스턴스를 V2.3으로 업그레이드해야 합니다.
* 가능하면 {{site.data.keyword.vmwaresolutions_full}} 콘솔을 사용하여 클러스터를 삭제하십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다. 따라서 온프레미스 클러스터 서버 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 관리할 수 없거나 관리하지 않을 클러스터에 대해서만 클러스터를 vCenter Server에서 제거하십시오.
* 한 번에 하나의 클러스터를 삭제할 수 있습니다. 둘 이상의 클러스터를 삭제하려면 순서대로 수행해야 합니다. 다음 클러스터를 삭제하기 전에 이전 클러스터가 삭제될 때까지 대기하십시오.
* 클러스터를 삭제하기 전에 클러스터의 모든 노드가 켜져 있으며 가동 상태인지 확인하십시오.
* 클러스터를 삭제하면 클러스터의 모든 VM도 삭제되며 이는 복구할 수 없습니다. VM을 보존하려는 경우에는 이들을 다른 클러스터로 마이그레이션하십시오.
* 기본 클러스터는 삭제할 수 없습니다.

### vCenter Server 인스턴스에서 클러스터를 삭제하는 프로시저
{: #vc_addingviewingclusters-deleting-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 클러스터를 삭제할 인스턴스를 클릭하십시오.

   인스턴스가 **사용할 준비가 됨** 상태인지 확인하십시오. 그렇지 않으면 인스턴스에서 클러스터를 삭제할 수 없습니다.
   {:note}

3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오. **클러스터** 테이블에서 삭제할 클러스터를 찾고 **조치** 열에서 **삭제** 아이콘을 클릭하십시오.
4. 필요한 경우에는 다른 클러스터로의 VM 마이그레이션을 완료했는지 확인하고, 클러스터를 삭제할지 확인하십시오.

## 관련 링크
{: #vc_addingviewingclusters-related}

* [vCenter Server 인스턴스 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)

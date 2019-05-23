---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-18"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with Hybridity Bundle 인스턴스의 클러스터 추가, 보기 및 삭제
{: #vc_hybrid_addingviewingclusters}

인스턴스를 주문할 때 구성한 ESXi 서버는 기본적으로 **cluster1**로 그룹화됩니다.

클러스터를 VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle 인스턴스에 추가하여 컴퓨팅 및 스토리지 용량을 확장할 수 있습니다. 클러스터 내에서 향상된 리소스 할당 및 고가용성을 위해 ESXi 서버를 관리하십시오. 더 이상 필요하지 않은 경우에는 추가된 클러스터를 인스턴스에서 삭제하십시오.

## vCenter Server with Hybridity Bundle 인스턴스에 클러스터 추가
{: #vc_hybrid_addingviewingclusters-adding}

### 클러스터를 추가하기 전에
{: #vc_hybrid_addingviewingclusters-before-add}

* 가능하면 {{site.data.keyword.vmwaresolutions_full}} 콘솔을 사용하여 클러스터를 추가하십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않기 때문입니다. 따라서 온프레미스 클러스터 서버 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 관리할 수 없거나 관리하지 않을 클러스터에 대해서만 클러스터를 vCenter Server에 추가하십시오.
* V2.5 이상에 배치된(또는 업그레이드된) 인스턴스의 경우에는 클러스터, 호스트 및 VM 수가 추가할 수 있는 클러스터 수의 최대 제한을 결정합니다. 배치를 위해 VMware 크기 조정 가이드라인 및 제한사항을 계속 준수해야 합니다. 최대 제한에 대한 자세한 정보는 [VMware Configuration Maximums](https://configmax.vmware.com/home){:new_window}를 참조하십시오.
* V2.3 및 V2.4에 배치된(또는 업그레이드된) 인스턴스의 경우에는 최대 10개의 클러스터를 추가할 수 있습니다.

### 시스템 설정
{: #vc_hybrid_addingviewingclusters-adding-sys-settings}

vCenter Server with Hybridity Bundle 인스턴스에 클러스터를 추가할 때 다음 설정을 지정해야 합니다.

#### 클러스터 이름
{: #vc_hybrid_addingviewingclusters-adding-cluster-name}

클러스터 이름은 다음 요구사항을 충족해야 합니다.
* 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
* 클러스터 이름은 영숫자 문자로 시작하고 끝나야 합니다.
* 클러스터 이름의 최대 길이는 30자입니다.
* 클러스터 이름은 vCenter Server with Hybridity Bundle 인스턴스 내에서 고유해야 합니다.

#### 데이터 센터 위치
{: #vc_hybrid_addingviewingclusters-adding-dc-location}

기본적으로 클러스터의 {{site.data.keyword.CloudDataCent_notm}} 위치는 vCenter Server 인스턴스의 {{site.data.keyword.CloudDataCent_notm}}로 설정됩니다. 배치된 인스턴스와 다른 {{site.data.keyword.CloudDataCent_notm}}에 클러스터를 배치할 수 있으나 두 {{site.data.keyword.CloudDataCents_notm}} 간의 네트워크 대기 시간이 150밀리초 미만인지 확인해야 합니다. 네트워크 대기 시간을 확인하기 위해 [Looking Glass](/docs/infrastructure/network-tools?topic=network-tools-about-looking-glass#about-looking-glass)와 같은 도구를 사용하십시오.

클러스터를 다른 {{site.data.keyword.CloudDataCent_notm}} 또는 {{site.data.keyword.cloud_notm}} 인프라 팟(Pod)에 배치하는 경우에는 주문된 {{site.data.keyword.baremetal_short}}와 함께 사용할 세 개의 추가 VLAN이 주문됩니다.

### Bare Metal Server 설정
{: #vc_hybrid_addingviewingclusters-adding-bare-metal}

**Skylake** 또는 **Broadwell**을 선택할 수 있습니다. 옵션은 인스턴스가 처음에 배치된 버전에 따라 다를 수 있습니다.

#### Skylake
{: #vc_hybrid_addingviewingclusters-adding-skylake}

**Skylake**를 선택하는 경우 필요에 따라 CPU 및 RAM 조합을 선택할 수 있습니다.

표 1. Skylake Bare Metal Server의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
|듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |
|듀얼 Intel Xeon Gold 6140 프로세서 / 총 36개의 코어, 2.3GHz |64GB, 96GB, 128GB, 192GB, 384GB, 768GB, 1.5TB |

#### Broadwell
{: #vc_hybrid_addingviewingclusters-adding-broadwell}

**Broadwell**을 선택하는 경우 필요에 따라 CPU 및 RAM 조합을 선택할 수 있습니다.

표 2. Broadwell Bare Metal Server의 옵션

| CPU 모델 옵션        |RAM 옵션       |
|:------------- |:------------- |
| 쿼드 Intel Xeon E7-4820 v4 / 총 40개의 코어, 1.9GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |
| 쿼드 Intel Xeon E7-4850 v4 / 총 64개의 코어, 2.2GHz |128GB, 256GB, 512GB, 1TB, 2TB, 3TB |

#### Bare Metal Server 수
{: #vc_hybrid_addingviewingclusters-adding-bare-metal-number}

* 주문하는 모든 서버는 동일한 구성을 갖습니다.
* 4 - 59개의 서버를 주문할 수 있습니다.

### vSAN 스토리지 설정
{: #vc_hybrid_addingviewingclusters-adding-vsan-storage-settings}

vCenter Server with Hybridity Bundle 인스턴스 주문에는 VMware vSAN 6.6이 포함됩니다. 다음 vSAN 옵션을 지정하십시오.
* **vSAN 용량 디스크의 디스크 유형 및 크기**: 필요한 용량 디스크에 대한 옵션을 선택하십시오.
* **vSAN 용량 디스크 수**: 추가할 용량 디스크 수를 지정하십시오.
* 용량 디스크를 10개 한계 이상으로 추가하려는 경우 **고성능 Intel Optane** 상자를 선택하십시오. 이 옵션은 총 12개 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공하며 짧은 대기 시간과 높은 IOPS 처리량이 필요한 워크로드에 유용합니다.

  **고성능 Intel Optane** 옵션은 Skylake CPU 모델에 대해서만 사용 가능합니다.
  {:note}

* **vSAN 캐시 디스크의 디스크 유형** 및 **vSAN 캐시 디스크 수** 값을 검토하십시오. 이러한 값은 **고성능 Intel Optane** 상자를 선택했는지 여부에 따라 달라집니다.
* **vSAN 라이센스**: VMware vSAN 6.6 라이센스 에디션(Advanced 또는 Enterprise)을 선택하십시오.

### 라이센스 부여 설정
{: #vc_hybrid_addingviewingclusters-adding-licensing-settings}

다음 VMware 컴포넌트에 대한 IBM 제공 라이센스:
  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4(Advanced 또는 Enterprise 에디션)

### 네트워크 인터페이스 설정
{: #vc_hybrid_addingviewingclusters-adding-network-interface-settings}

네트워크 인터페이스 카드(NIC) 설정은 **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 사용자의 선택을 기반으로 합니다. 다음과 같은 추가 기능 서비스에는 공용 NIC가 필요하며 개인용 옵션과 함께 사용할 수 없습니다.

* F5 on {{site.data.keyword.cloud_notm}}
* Fortigate Security Appliance on {{site.data.keyword.cloud_notm}}
* Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}

### 주문 요약
{: #vc_hybrid_addingviewingclusters-adding-order-summary}

클러스터에 대해 선택한 구성에 따라 예상 비용이 즉시 생성되어 **주문 요약** 오른쪽 분할창에 표시됩니다.

## vCenter Server with Hybridity Bundle 인스턴스에 클러스터를 추가하는 프로시저
{: #vc_hybrid_addingviewingclusters-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 클러스터를 볼 인스턴스를 클릭하십시오.

   인스턴스가 **사용할 준비가 됨** 상태인지 확인하십시오. 그렇지 않으면, 클러스터를 인스턴스에 추가할 수 없습니다.
   {:note}

3. 왼쪽 탐색 분할창의 **인프라**를 클릭하고 **클러스터** 테이블의 오른쪽 상단 모서리에 있는 **추가**를 클릭하십시오.
4. **클러스터 추가** 페이지에서 인스턴스 이름을 입력하십시오.
5. 인스턴스가 호스팅되는 위치와 다른 {{site.data.keyword.CloudDataCent_notm}}에서 클러스터를 호스팅할 수 있습니다. 이를 수행하려면, **Bare Metal Server** 아래에서 **다른 위치 선택** 선택란을 선택하고 인스턴스를 호스팅할 {{site.data.keyword.CloudDataCent_notm}}를 선택하십시오.
6. Bare Metal Server 구성의 **CPU 모델**, **RAM**의 양 및 **Bare Metal Server 수**를 선택하십시오.
7.  **vSAN 스토리지**를 선택하고 용량 및 캐시 디스크의 디스크 유형 및 디스크 수를 지정하십시오. 더 많은 스토리지를 원하는 경우 **고성능 Intel Optane** 상자를 선택하십시오.
8. 라이센스 구성을 위해 VMware vSAN의 라이센스 에디션을 선택하십시오.
9. **공용 및 사설 네트워크** 또는 **사설 네트워크 전용** 중 네트워크 설정을 선택하십시오.
10. 클러스터를 추가하기 전에 **주문 요약** 페이지에서 클러스터 구성을 확인하십시오.
   1. 클러스터의 설정을 검토하십시오.
   2. 클러스터의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   3. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 클러스터를 추가하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   4. **프로비저닝**을 클릭하십시오.

### vCenter Server with Hybridity Bundle 인스턴스에 클러스터를 추가한 후의 결과
{: #vc_hybrid_addingviewingclusters-adding-results}

1. 클러스터의 배치가 자동으로 시작되며 클러스터의 상태가 **초기화 중**으로 변경됩니다. 인스턴스의 **요약** 페이지에서 배치 히스토리를 보고 배치의 상태를 확인할 수 있습니다.
2. 클러스터를 사용할 준비가 되면 클러스터의 상태가 **사용할 준비가 됨**으로 변경됩니다. 새로 추가된 클러스터는 vSphere HA(High Availability) 및 vSphere DRS(Distributed Resource Scheduler)로 사용 가능합니다.

클러스터 이름은 변경할 수 없습니다. 클러스터 이름을 변경하면 클러스터의 ESXi 서버 오퍼레이션을 추가하거나 제거하는 데 실패할 수 있습니다.
{:important}

## vCenter Server with Hybridity Bundle 인스턴스의 클러스터를 보는 프로시저
{: #vc_hybrid_addingviewingclusters-viewing-procedure}

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
4. 클러스터 이름을 클릭하여 ESXi 서버, 스토리지 및 네트워크 인터페이스 세부사항을 보십시오.

  * ESXi 서버 세부사항:
     * **이름**: ESXi 서버의 이름은 `<host_prefix><n>.<subdomain_label>.<root_domain>` 형식으로 되어 있습니다. 여기서,

       `host_prefix`는 호스트 이름 접두부이고

       `n`은 서버의 순서이며

       `subdomain_label`은 하위 도메인 레이블이고

       `root_domain`은 루트 도메인 이름입니다.

     * **버전**: ESXi 서버의 버전입니다.
     * **인증 정보**: ESXi 서버에 액세스하는 데 사용되는 사용자 이름 및 비밀번호입니다.
     * **사설 IP**: ESXi 서버의 사설 IP 주소입니다.
     * **상태**: ESXi 서버의 상태이며, 다음 값 중 하나가 될 수 있습니다.
        <dl class="dl">
        <dt class="dt dlterm">추가됨</dt>
        <dd class="dd">ESXi 서버가 추가되었으며 사용할 준비가 되었습니다. </dd>
        <dt class="dt dlterm">추가 중</dt>
        <dd class="dd">ESXi 서버가 추가 중입니다. </dd>
        <dt class="dt dlterm">삭제 중</dt>
        <dd class="dd">ESXi 서버가 삭제 중입니다.</dd>
        </dl>
  * 스토리지 세부사항:
    * **이름**: 데이터 저장소 이름입니다.
    * **크기**: 스토리지의 용량입니다.
    * **IOPS/GB**: 스토리지의 성능 레벨입니다.
    * **NFS 프로토콜**: 스토리지의 NFS 버전입니다.
  * 네트워크 인터페이스 - VLAN 세부사항:
    * **VLAN 번호**: 고유한 VLAN 번호입니다.
    * **설명**: VLAN의 설명입니다.
    * **위치**: 데이터 센터 위치입니다.
    * **기본 라우트**: VLAN의 기본 라우트입니다.
    VLAN 세부사항에 액세스하려면 **리소스 보기**를 클릭하십시오.
  * 네트워크 인터페이스 - 서브넷 세부사항:
    * **이름**: 서브넷 이름입니다. 서브넷 세부사항에 액세스하려면 이름을 클릭하십시오.
    * **유형**: 서브넷의 유형: 기본 또는 포터블.
    * **설명**: 서브넷의 설명입니다.
  * 네트워크 인터페이스 - IP 세부사항:
    * **IP**: IP 주소입니다.
    * **상태**: IP 주소의 상태입니다.
    * **설명**: IP 주소의 설명입니다.

## vCenter Server with Hybridity Bundle 인스턴스에서 클러스터 삭제
{: #vc_hybrid_addingviewingclusters-deleting}

더 이상 필요하지 않은 경우 인스턴스에서 클러스터를 삭제할 수 있습니다.

### 삭제하기 전에
{: #vc_hybrid_addingviewingclusters-deleting-prereq}

* 가능하면 {{site.data.keyword.vmwaresolutions_full}} 콘솔을 사용하여 클러스터를 삭제하십시오. VMware vSphere Web Client에서 수행하는 변경사항은 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 동기화되지 않습니다. 따라서 온프레미스 클러스터 서버 또는 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 관리할 수 없거나 관리하지 않을 클러스터에 대해서만 클러스터를 vCenter Server에서 제거하십시오.
* 한 번에 하나의 클러스터를 삭제할 수 있습니다. 여러 클러스터를 삭제하려면, 순서대로 수행해야 합니다(즉, 다음 클러스터를 삭제하려고 시도하기 전에 이전 클러스터가 삭제되기를 기다려야 함).
* 클러스터를 삭제하기 전에 클러스터의 모든 노드가 켜져 있으며 가동 상태인지 확인하십시오.
* 클러스터를 삭제하면 클러스터의 모든 가상 머신(VM)도 삭제되며 이는 복구할 수 없습니다. VM을 보존하려는 경우에는 이들을 다른 클러스터로 마이그레이션하십시오.
* 기본 클러스터는 삭제할 수 없습니다.

## vCenter Server with Hybridity Bundle 인스턴스에서 클러스터를 삭제하는 프로시저
{: #vc_hybrid_addingviewingclusters-deleting-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **리소스**를 클릭하십시오.
2. **vCenter Server 인스턴스** 테이블에서 클러스터를 삭제할 인스턴스를 클릭하십시오.

   인스턴스가 **사용할 준비가 됨** 상태인지 확인하십시오. 그렇지 않으면 인스턴스에서 클러스터를 제거할 수 없습니다.
   {:note}

3. 왼쪽 탐색 분할창에서 **인프라**를 클릭하십시오. **클러스터** 테이블에서 삭제할 클러스터를 찾고 **조치** 열에서 **삭제** 아이콘을 클릭하십시오.

## 관련 링크
{: #vc_hybrid_addingviewingclusters-related}

* [vCenter Server with Hybridity Bundle 인스턴스 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)

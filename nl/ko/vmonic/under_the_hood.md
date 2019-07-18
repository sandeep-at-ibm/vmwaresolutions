---

copyright:

  years:  2019

lastupdated: "2019-06-28"

keywords: about vmware solutions, product overview, benefits

subcollection: vmware-solutions

---
{:external: target="_blank" .external}

# IBM Cloud for VMware Solutions: 자세히 알아보기
{: #under_the_hood}

## VMware 가상화 환경 배치 및 관리
{: #under_the_hood-deploy}

{{site.data.keyword.vmwaresolutions_full}}, 즉 VMware 가상화 환경의 배치 및 관리를 제공하는 {{site.data.keyword.cloud_notm}} 오퍼링의 아키텍처에 대해 자세히 알아보십시오. 이 튜토리얼에서는 오퍼링의 컴포넌트가 함께 작동하여 퍼블릭 클라우드에서 환경을 프로비저닝하고 유지보수하는 방법을 볼 수 있도록 이러한 오퍼링 컴포넌트를 보여줍니다.

## 2개의 회사, 하나의 간소화된 솔루션
{: #under_the_hood-two-companies}

한동안 사용자는 스스로 또는 전문적 서비스를 이용하여 VMware 가상화 환경을 IBM Public Cloud에 배치해 왔습니다. 2016년 2월에 [IBM과 VMware는 파트너십을 발표](https://www-03.ibm.com/press/us/en/pressrelease/49154.wss){:external}하여 {{site.data.keyword.cloud_notm}}에서 VMware 소프트웨어 및 VMware 환경을 배치하는 프로세스를 자동화했습니다. 이 파트너십의 초기 성과 중 하나는 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 다양한 VMware 제품 배치 및 라이센스와 이후 {{site.data.keyword.cloud_notm}}의 오퍼링 [VMware Horizon Air](https://www-03.ibm.com/press/us/en/pressrelease/49932.wss){:external}를 주문하는 기능이었습니다. 또한 IBM과 VMware는 함께 작업하여 IBM Public Cloud에서 [VMware를 위한 표준 참조 아키텍처 및 배치 방안](https://www.ibm.com/cloud/garage/architectures/virtualizationArchitecture){:external}을 공동으로 만들었습니다.

2016년 가을에는 IBM과 VMware가 공동으로 {{site.data.keyword.vmwaresolutions_short}}를 출시했습니다. 이 오퍼링 세트는 가상화된 컴퓨팅(VMware vSphere), 네트워킹(VMware NSX), 가상화된 스토리지(VMware vSAN)(선택사항)를 포함한 VMware의 가상화 기술을 기반으로 합니다. 이러한 환경은 소프트웨어 정의 데이터 센터라고 합니다.

{{site.data.keyword.vmwaresolutions_short}}는 IBM Public Cloud에서 이러한 소프트웨어 정의 데이터 센터의 배치 및 관리를 크게 간소화하기 위해 VMware 기술을 기반으로 빌드됩니다. {{site.data.keyword.vmwaresolutions_short}}를 사용하면 수동이 아닌 자동으로 {{site.data.keyword.cloud_notm}}에 표준 참조 아키텍처의 일부를 배치할 수 있습니다. 이전에 배치하고 구성하는 데 몇 주가 소요된 환경을 몇 시간 내에 프로비저닝할 수 있습니다.

이러한 배치의 용이성을 통해 사용자 환경을 빌드하지 않고 VMware의 맨 위에서 솔루션을 구현하는 데 집중할 수 있습니다. 사용자의 빠른 처리 환경에서는 IBM Public Cloud의 클라우드 기본 솔루션뿐만 아니라 개인용 클라우드와 IBM Public Cloud에 걸친 하이브리드 클라우드 솔루션을 둘 다 빌드할 수 있습니다. 여러 배치를 결합하여 재해 복구 또는 고가용성 기능을 솔루션에 쉽게 추가할 수 있습니다.

이제 {{site.data.keyword.vmwaresolutions_short}} 아키텍처에 대해 자세히 살펴봅니다. 솔루션의 파트인 여러 컴포넌트 및 {{site.data.keyword.cloud_notm}}에서 이러한 컴포넌트가 함께 작동하여 소프트웨어 정의 데이터 센터를 프로비저닝하고 관리하는 방법을 파악합니다. 또한 사용자 환경에 연결하는 데 필요한 여러 옵션 및 네트워크 토폴로지에 대해 알아봅니다.

## IBM Cloud for VMware Solutions 기본

소프트웨어 정의 데이터 센터는 [{{site.data.keyword.vmwaresolutions_short}} 콘솔](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}을 사용하여 프로비저닝되고 관리됩니다. IBM ID 계정을 사용하여 콘솔에 로그인합니다.

VMware Solutions 카탈로그에서 여러 종류의 가상화 환경 중 하나를 프로비저닝할 수 있습니다. 주요 가상화 솔루션은 *VMware vCenter Server on {{site.data.keyword.cloud_notm}}*이며, VMware의 vSphere Hypervisor, VMware vCenter Server, VMware NSX 및 선택적으로 VMware vSAN을 제공합니다. 또한 백업, 재해 복구, 마이그레이션, 보안, 준수 및 네트워킹 서비스를 제공하는 추가 기능 서비스와 함께 이 환경을 프로비저닝할 수 있습니다.

vCenter Server 인스턴스를 주문하려면 먼저 VMware Solutions 카탈로그에서 {{site.data.keyword.cloud_notm}} 인프라 API 키를 구성해야 합니다. 이렇게 하려면 콘솔의 왼쪽 메뉴에서 [설정](https://cloud.ibm.com/infrastructure/vmware-solutions/console/settings){:external} 링크를 클릭하고, {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 입력하도록 프롬프트가 표시되면 사용자 이름 및 API 키를 입력하십시오. 시스템은 API 키와 계정에 인스턴스를 배치하는 적절한 권한과 설정이 있는지 확인합니다.

vCenter Server 인스턴스를 주문할 때 먼저 이름과 VMware vSphere 버전을 선택합니다. 모든 VMware 인스턴스는 Microsoft Active Directory 도메인 제어기와 함께 배치되며 싱글 사인온 용도로 인스턴스를 기본 또는 보조 사이트로 지정해야 합니다. 기본 인스턴스가 싱글 사인온 도메인의 첫 번째 또는 유일한 인스턴스입니다. 추가 보조 인스턴스를 배치하고 이를 기존 기본 인스턴스의 동일한 싱글 사인온 도메인과 연관시킬 수 있습니다. 그런 다음 고유 VMware 라이센스를 가져올지 여부 또는 {{site.data.keyword.cloud_notm}}에서 임대할 라이센스의 개정판을 선택합니다. 마지막으로 클러스터에 있는 호스트의 CPU 및 메모리 특성뿐만 아니라 인스턴스의 {{site.data.keyword.cloud_notm}} 지역 및 데이터 센터를 선택합니다.

주문 페이지의 다음 파트에서는 인스턴스에 대한 스토리지 및 네트워킹 특성을 입력합니다. 클러스터에 대해 vSAN과 NFS 스토리지 간에 선택할 수 있으며, vSAN 플래시 디스크와 vSAN 라이센스 에디션의 크기와 수 또는 NFS 스토리지 볼륨의 크기와 개수 및 성능을 선택할 수 있습니다. 네트워킹을 위해 호스트의 호스트 이름 접두부와 클러스터의 하위 도메인 및 도메인을 선택합니다. Active Directory 제어기를 단일 {{site.data.keyword.cloud_notm}} 가상 서버 인스턴스(VSI)로 배치하는 옵션 또는 라이센싱 및 활성화를 제공해야 하는 클러스터 내 두 개의 가상 머신이 있습니다.

vCenter Server 주문 페이지의 맨 아래에서는 VMware 인스턴스에 대해 배치할 수 있고 {{site.data.keyword.cloud_notm}} 계정에 비용 청구되는 다양한 추가 기능 서비스 중에서 선택할 수 있습니다. 일부 서비스에는 주문 양식의 일부로 지정한 추가 구성이 필요합니다.

주문 양식은 선택사항에 따라 예상 가격을 계산하고 표시합니다. 주문을 제출하기 전에 이 예상과 다양한 이용 약관을 검토할 수 있습니다.

### 배치 옵션
{: #under_the_hood-deploy-options}

vCenter Server 주문 양식에는 인스턴스에 대한 다양한 CPU, 메모리 및 스토리지 옵션이 표시됩니다. 새 옵션은 정기적으로 사용 가능하므로 최신 가용성 정보는 {{site.data.keyword.cloud_notm}} 카탈로그를 확인하십시오.

{{site.data.keyword.cloud_notm}}는 3개의 VLAN(공용 하나와 개인용 두 개)을 사용하여 vCenter Server 인스턴스를 배치합니다. 공용 VLAN은 듀얼 10GbE 인터페이스에 연결되어 있으며 고유 워크로드 배치의 공용 연결 또는 터널링을 위해 원하는 대로 사용하도록 예약되어 있습니다. 하지만 배치 시 NSX Edge Services Gateway 쌍은 일부 추가 기능 서비스가 라이센싱 및 비용 청구를 위해 공용 네트워크에 연결할 수 있도록 공용 VLAN에 배치됩니다. 사설 VLAN은 개별 듀얼 10GbE 인터페이스에 연결됩니다. 첫 번째 사설 VLAN은 관리 통신 및 NSX VTEP에 사용되고 두 번째는 vMotion 및 NFS 스토리지 트래픽에 사용됩니다.

VMware 인스턴스는 35개의 서로 다른 {{site.data.keyword.CloudDataCents_notm}}에서 프로비저닝될 수 있습니다. {{site.data.keyword.cloud_notm}}는 때때로 새 데이터 센터를 프로비저닝합니다. 사용 가능한 최신 위치 목록은 {{site.data.keyword.cloud_notm}} 카탈로그를 선택하십시오.

### 인스턴스 배치
{: #under_the_hood-inst-deploy}

새 VMware vCenter 인스턴스를 주문하면 인스턴스 위치와 스펙을 선택합니다. {{site.data.keyword.vmwaresolutions_short}}는 이전에 선택한 {{site.data.keyword.cloud_notm}} 사용자 이름 및 API 키를 사용하여 가상화 환경 주문, 설치 및 구성의 전체 프로세스를 오케스트레이션합니다. 다음이 포함됩니다.

1. 네트워킹을 위한 VLAN 및 서브넷 주문.
2. vSphere Hypervisor가 설치된 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}의 주문.
3. 임베디드 Platform Services Controller, VMware NSX Manager, 제어기 및 Edge Services Gateway를 사용하여 VMware vCenter Server 배치 및 구성.
4. VMware vSAN 또는 {{site.data.keyword.cloud_notm}} Endurance 스토리지를 포함하여 클러스터 스토리지 주문 및 구성.
5. IBM CloudDriver라는 IBM 관리 컴포넌트 배치.
6. 인스턴스에 대해 선택한 추가 기능 서비스 배치 및 구성.
7. 환경의 설치와 구성에 대한 유효성 검증.

인스턴스를 프로비저닝할 {{site.data.keyword.CloudDataCent_notm}}를 선택합니다. 하드웨어가 선택된 {{site.data.keyword.CloudDataCent_notm}}에서 사용 가능한 경우 인스턴스 프로비저닝 프로세스는 일반적으로 24시간 미만으로 소요됩니다.

인스턴스가 프로비저닝되면 VPN을 통해 {{site.data.keyword.cloud_notm}} 계정에 연결된 경우 워크스테이션 웹 브라우저에서 직접 vCenter 서버에 연결할 수 있습니다.

일반적으로 인스턴스 컴포넌트는 IP 주소가 아니라 호스트 이름으로 액세스됩니다. vCenter에 연결하고 인증하기 위해 목록 1에 표시된 대로 워크스테이션의 호스트 파일에 추가하여 워크스테이션에서 vCenter 및 PSC(Platform Services Controller) 호스트 이름을 분석할 수 있습니다. 인스턴스의 **요약** 탭에서 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 호스트 이름과 IP 주소를 찾을 수 있습니다. vSphere 호스트의 호스트 이름과 IP 주소를 호스트 파일에 추가할 수도 있습니다.

*목록 1. 호스트 파일*

<pre># Dallas site vCenter and Platform Services Controller (PSC)
10.208.85.196  vcenter-dallas.dallas.example.com
# Dallas site hosts
10.208.85.171  host0.dallas.example.com
10.208.85.153  host1.dallas.example.com
10.208.85.137  host2.dallas.example.com</pre>

인스턴스를 배치한 후 콘솔에서 관리할 수 있습니다. 관리 기능에는 다음을 각각 수행할 수 있는 기능이 있습니다.

* 클러스터에서 노드 배치 및 제거
* 동일한 데이터 센터 및 팟(Pod) 또는 대체 데이터 센터 및 팟(Pod)에서 추가 클러스터 배치 및 제거
* 인스턴스의 추가 기능 서비스 배치 및 제거
* 인스턴스의 특정 라이센스 개정판 업그레이드

{{site.data.keyword.vmwaresolutions_short}} 콘솔은 각 vCenter Server 인스턴스의 자세한 보기를 제공합니다. 각 인스턴스에 대해 **요약** 탭에는 인스턴스 및 관리 컴포넌트에 대한 vCenter 콘솔 및 기타 세부사항에 대한 링크가 포함되어 있습니다. **인프라** 탭에는 인스턴스의 클러스터, 호스트, 스토리지 및 네트워킹에 대한 세부사항이 표시되며 이 탭을 통해 클러스터, 호스트 및 스토리지를 추가하거나 제거할 수 있습니다. **업데이트 및 패치** 탭에서 특정 라이센스 개정판을 업그레이드할 수 있습니다. **서비스** 탭에서 인스턴스에 배치된 추가 기능 서비스를 보고 관리할 수 있습니다. **배치 히스토리** 탭에는 인스턴스에서 수행되는 모든 조치의 히스토리가 표시됩니다.

## IBM Cloud for VMware Solutions 컴포넌트
{: #under_the_hood-comp}

여러 다양한 컴포넌트가 함께 작동하여 사용자 환경을 프로비저닝하고 관리합니다. 이러한 구성요소의 대부분은 {{site.data.keyword.cloud_notm}} 계정에 배치됩니다. 솔루션은 함께 작동하는 이러한 모든 구성요소에 종속되므로 {{site.data.keyword.cloud_notm}} 계정에서 이러한 구성요소를 수정하거나 취소하면 안됩니다. 실행 중인 인스턴스를 제거하는 올바른 방법은 개별 컴포넌트를 취소하지 않고 콘솔을 사용하는 것입니다.

이는 통합된 가상화 환경인 반면, 다양한 가상화 컴포넌트(예: VMware 라이센스), 인프라 컴포넌트(베어 메탈 서버, VLAN, 서브넷 및 스토리지) 및 관리 컴포넌트의 비용은 {{site.data.keyword.cloud_notm}}에서 수신하는 청구서로 제공됩니다.

### IBM Cloud for VMware Solutions 콘솔
{: #under_the_hood-console}

[{{site.data.keyword.vmwaresolutions_short}} 콘솔](https://cloud.ibm.com/infrastructure/vmware-solutions/console){:external}에 로그인하여 인스턴스를 작성하고 관리합니다. 이 솔루션 부분은 사용자 환경의 초기 주문 및 프로비저닝과 사용자 환경에 대한 지속적 관리를 담당합니다. 배치 인스턴스는 {{site.data.keyword.cloud_notm}} Private 네트워크를 사용하여 콘솔과 통신합니다.

### IBM CloudBuilder 컴포넌트
{: #under_the_hood-ibm-cb}

새 인스턴스를 프로비저닝하면 콘솔이 임시 가상 서버 인스턴스(VSI)를 {{site.data.keyword.cloud_notm}} 계정에 배치합니다. 이 가상 서버는 IBM CloudBuilder로 알려져 있습니다. 이는 모든 인스턴스 컴포넌트의 설치 및 구성과 환경 유효성 검증을 수행합니다. 프로비저닝이 완료되면 CloudBuilder가 삭제됩니다.

### IBM CloudDriver 컴포넌트
{: #under_the_hood-ibm-cd}

CloudBuilder와 마찬가지로 IBM CloudDriver는 인스턴스에서 후속 오퍼레이션을 수행하기 위해 {{site.data.keyword.cloud_notm}} 계정에 배치된 임시 가상 서버 인스턴스(VSI)입니다. 이는 필요에 따라 인스턴스에서 호스트, 클러스터, 스토리지 또는 서비스를 구성하거나 제거하기 위해 배치됩니다.

### VMware 컴포넌트
{: #under_the_hood-vmware-comp}

모든 인스턴스의 경우 vSphere Hypervisor는 베어 메탈 서버에 설치됩니다. {{site.data.keyword.cloud_notm}}는 통합된 Platform Services Controller(PSC), NSX Manager, 3개의 NSX Controller 및 2개의 NSX Edge Services Gateway 쌍이 있는 vCenter Server Appliance를 VMware 관리 클러스터에 배치합니다.

### 추가 컴포넌트
{: #under_the_hood-add-comp}

선택에 따라 하나의 Microsoft Windows VSI 또는 두 개의 Microsoft Windows 가상 머신이 함께 배치되거나 클러스터에 관리 컴포넌트를 위한 Active Directory 서버로서 배치됩니다. 선택적으로 고유 Active Directory 서버를 관리 액세스를 위한 추가 ID 소스로서 추가할 수 있습니다.

고유 워크로드에 비즈니스 연속성을 제공하도록 선택하는 방법에 관계없이 {{site.data.keyword.cloud_notm}}는 인스턴스의 관리 컴포넌트를 백업하는 것이 좋습니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔을 사용하면 인스턴스와 함께 통합된 IBM Spectrum Protect Plus 백업 서버 또는 Veeam Backup & Replication 백업 서버를 배치할 수 있습니다. 이러한 백업 서비스는 인스턴스의 [완전한 백업 솔루션](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_backingup)의 일부로 사용할 수 있습니다.

### 라이센스
{: #under_the_hood-licenses}

{{site.data.keyword.cloud_notm}}는 인스턴스에 설치되고 {{site.data.keyword.cloud_notm}} 계정으로 비용 청구되는 여러 VMware 라이센스(예: vCenter Server 및 NSX)를 제공합니다.

## IBM Cloud for VMware Solutions 네트워크 아키텍처
{: #under_the_hood-network}

vCenter Server 인스턴스는 배치된 워크로드에 사용하기 위해 공용 VLAN에 연결됩니다. 공용 VLAN은 원하는 대로 사용할 수 있도록 예약되어 있지만 NSX Edge Services Gateway 쌍은 특정 추가 기능 서비스가 라이센싱 및 비용 청구를 위해 아웃바운드에서 통신할 수 있도록 공용 VLAN에 연결되어 있습니다. 일부 추가 기능 서비스가 지원되지 않는 경우 공용 네트워크를 사용하지 않고 인스턴스를 배치할 수 있으며, 특정 추가 기능 서비스를 사용할 수 있도록 웹 프록시를 제공해야 할 수 있습니다.

vCenter Server 인스턴스에 하이퍼바이저의 사설 네트워크 인터페이스에서 함께 선택된 두 개의 사설 VLAN이 있습니다. 첫 번째 사설 VLAN은 관리 연결을 위해(예: 하이퍼바이저와의 vCenter 통신) 그리고 배치된 워크로드에 대한 모든 VXLAN 트래픽을 터널링하기 위해 NSX에서 사용됩니다. 두 번째 사설 VLAN은 vMotion 및 스토리지 트래픽에 사용됩니다. 스토리지 트래픽은 NFS 또는 vSAN 프로토콜입니다.

{{site.data.keyword.cloud_notm}}는 이러한 사설 VLAN에 특정 추가 서비스를 제공합니다. Active Directory 서버는 사설 관리 VLAN을 통해 {{site.data.keyword.cloud_notm}} DNS 서버와 통신합니다. 호스트 및 기타 컴포넌트는 사설 관리 VLAN을 통해 {{site.data.keyword.cloud_notm}} NTP 서버와 통신합니다. IBM CloudBuilder 및 CloudDriver는 이 VLAN을 통해 {{site.data.keyword.vmwaresolutions_short}} 콘솔과 통신합니다. 호스트는 사설 스토리지 VLAN을 통해 {{site.data.keyword.cloud_notm}} Endurance 스토리지에 연결됩니다.

### 인스턴스에 연결
{: #under_the_hood-connect-inst}

인스턴스에 연결하기 위한 여러 옵션이 있습니다. [{{site.data.keyword.cloud_notm}} VPN](https://www.softlayer.com/VPN-Access){:external}을 사용하여 인스턴스(예: vCenter)에서 사설 IP 주소에 직접 연결할 수 있습니다. 또한 [{{site.data.keyword.cloud_notm}} 네트워크 어플라이언스](https://www.ibm.com/cloud/network-appliances){:external} 및 [{{site.data.keyword.cloud_notm}} 하드웨어 또는 가상 방화벽](https://www.ibm.com/cloud/network-security)(예: 계정에 대한 FortiGate 및 vSRX)을 주문할 수 있습니다. {{site.data.keyword.cloud_notm}}는 {{site.data.keyword.cloud_notm}} 계정의 네트워크와 VLAN 간 [직접 링크](https://www.ibm.com/cloud/direct-link){:external}를 제공합니다.

배치된 VM에 대한 액세스를 위해 VM에 직접 공인 IP 주소를 적용할 수 있습니다. 하지만 NAT 및 방화벽을 사용하여 VM에 대한 더 안전한 공용 액세스를 설정하기 위해 {{site.data.keyword.cloud_notm}} 네트워크 어플라이언스 및 방화벽 기능을 사용할 수 있습니다. 또한 NSX Edge 서버를 배치하고 이러한 서버를 사용하여 VM에 대한 VPN 또는 NAT 연결을 설정할 수 있습니다.

## 결론
{: #under_the_hood-conclusion}

이 튜토리얼에서는 퍼블릭 클라우드에서 표준화된 VMware 가상화 환경을 배치하고 관리하는 {{site.data.keyword.vmwaresolutions_short}}의 기본 기능에 대해 알아보았습니다. 이러한 환경을 이전보다 빠르게 프로비저닝할 수 있으므로 애플리케이션 및 솔루션을 해당 환경 맨 위에 배치하고 장애 복구 또는 고가용성을 위해 클라우드를 함께 연결하는 데 중점을 둘 수 있습니다.

{{site.data.keyword.cloud_notm}} 청구서에 표시되는 {{site.data.keyword.cloud_notm}} 계정에 배치되며 사용자 환경 실행을 지속하도록 함께 작동되는 다양한 컴포넌트를 살펴보았습니다. 마지막으로, 통신을 비공개로 유지하기 위해 다양한 보안 연결 옵션을 사용하거나 공용 인터넷 연결을 위한 다양한 옵션을 사용하여 환경에 대한 연결을 설정하는 몇 가지 옵션과 함께 솔루션의 네트워크 아키텍처를 고려했습니다.

시작하기 위해 알아야 할 모든 것을 갖췄으므로 {{site.data.keyword.cloud_notm}}에서 다음 VMware 가상화 환경을 시작하고 배치하십시오.

## 관련 링크
{: #under_the_hood-related}

* [시작하기](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [VMware Solutions 아키텍처](/docs/services/vmwaresolutions?topic=vmware-solutions-solution_overview)

---

copyright:

  years:  2016, 2017

lastupdated: "2017-08-28"

subcollection: vmware-solutions


---

# V1.8 릴리스 정보
{: #relnotes_v18}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## Fortinet on IBM Cloud 서비스
{: #relnotes_v18-fortinet}

Fortinet on {{site.data.keyword.cloud_notm}} 서비스는 이제 Cloud Foundation 및 vCenter Server 인스턴스 모두에 사용 가능합니다. 이 서비스는 고가용성 모드에서 방화벽, 라우팅, NAT 및 VPN 서비스를 제공하도록 FSA(FortiGate Security Appliance) 300 시리즈 디바이스의 쌍을 배치하여 인스턴스의 공용 VLAN에서 모든 서버 및 가상 머신을 보호합니다. 인스턴스를 주문할 때 포함된 Fortinet 서비스와 함께 인스턴스를 주문하거나 인스턴스 세부사항 페이지에서 나중에 이 서비스를 기존 인스턴스에 추가할 수 있습니다.

Fortinet 서비스가 설치된 후 FortiGate 콘솔에서 FSA의 방화벽 규칙을 관리하고 구성할 수 있습니다. FSA 방화벽 규칙이 인터넷을 통해 IBM Bluemix®의 외부 관리 데이터베이스와 통신하기 위해 관리 컴포넌트(예: IBM CloudDriver 가상 머신 또는 Zerto Virtual Manager)로 시작되는 아웃바운드 HTTPS 통신을 허용하도록 정의되어 있는지 확인해야 합니다. 아웃바운드 HTTPS 통신은 인스턴스에 있는 관리 서비스 VMware NSX Edge Services Gateway(ESG)의 공인 IP 주소에서 시작됩니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Fortinet on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [Fortinet on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)

## Veeam on IBM Cloud 서비스
{: #relnotes_v18-veeam}

이 릴리스에서는 관리 컴포넌트 및 워크로드 모두를 백업할 수 있는 Veeam on {{site.data.keyword.cloud_notm}} 서비스를 도입했습니다. 새 서비스는 관리 컴포넌트의 백업을 목적으로만 V1.8 이전 릴리스로 통합된 이전 Veeam VSI를 대체합니다.

이 변경으로 인해, V1.8 이전 인스턴스의 Veeam VSI가 계속 작동 중이더라도 인스턴스의 백업 지점이 더 이상 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 사용 가능하지 않고 지원 티켓을 작성하여 복원에 대한 지원을 받아야 합니다.

또한 V1.8 이전 인스턴스의 Veeam VSI 라이센스가 2017년 10월 14일에 만료되었습니다. 그러므로 가능한 빨리 이전 Veeam VSI를 새 Veeam 서비스로 대체해야 합니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Veeam on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## VMware Cloud Foundation 인스턴스에 대한 업데이트
{: #relnotes_v18-vcf}

### Cloud Foundation 인스턴스 주문 시 고유한 VMware 라이센스 가져오기(BYOL)
{: #relnotes_v18-byol}

V1.8 릴리스부터 Cloud Foundation 인스턴스를 주문하는 경우 vSphere, vCenter Server, NSX 및 vSAN을 포함한 인스턴스의 VMware 컴포넌트에 대한 라이센스 부여를 위해 두 가지 옵션이 제공됩니다. 사용자 대신 구매할 새 라이센스를 사용하도록 선택할 수 있습니다.

라이센스 키를 제공해야 하는 경우 컴포넌트에 고유한 VMware 라이센스를 사용하도록 선택할 수도 있습니다. 이 경우, 라이센스를 제공하는 VMware 컴포넌트에 대한 지원은 IBM 지원 센터가 아닌 VMware에서 제공됩니다.

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v18-vcs}

### 인스턴스 CPU 및 메모리 사용자 정의
{: #relnotes_v18-custom-cpu}

사용자 정의 서버 옵션은 사전 빌드되고 테스트된 소형, 중형 및 대형 옵션과 함께 사용할 수 있습니다. RAM 양 외에도, 듀얼 CPU 및 총 코어 수에 따라 VMware HCL 호환 가능 서버의 목록에서 선택할 수 있습니다. 로컬 스토리지는 사용자 정의할 수 없습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

### 여덟 개 이상의 NFS 파일 공유를 추가하는 지원
{: #relnotes_v18-nfs}

 클러스터의 모든 ESXi 서버에서 최대 32개의 파일 공유에 연결할 수 있습니다.

 자세한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

### 데이터 센터에 대한 업데이트
{: #relnotes_v18-dc}

새 데이터 센터 즉, **DAL-09, DAL-12, DAL-13 - 달라스**, **LON-04, LON-06 - 런던**, **SJC-04 - 산호세**, **WDC-06, WDC-07 - 워싱턴, DC**를 배치에 사용할 수 있습니다.

자세한 정보는 [vCenter Server 인스턴스에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)을 참조하십시오.

## 사용성 개선사항
{: #relnotes_v18-ui}

개선사항은 사용자 인터페이스를 통해 수행됩니다.
* 왼쪽 탐색 분할창의 **시작하기** 페이지에서 서비스에 대해 알아보고 인스턴스를 주문할 수 있습니다.
* 인스턴스 세부사항 페이지의 오버플로우 메뉴를 사용하여 **사용할 준비가 됨** 상태의 인스턴스를 삭제하십시오.
* NSX 라이센스 에디션을 업그레이드하는 옵션은 이제 **업데이트 및 패치** 탭에서 사용할 수 있습니다. 라이센스 업그레이드는 IBM SoftLayer 계정에 있는 기존의 모든 라이센스를 새 라이센스로 대체합니다.
* 인스턴스 세부사항 페이지의 **백업 및 복원** 탭은 더 이상 사용할 수 없습니다.
* 주문 시작 시 다중 서비스를 선택하여 배치할 수 있습니다. Zerto on {{site.data.keyword.cloud_notm}} 서비스에 추가하여, Veeam on {{site.data.keyword.cloud_notm}} 서비스 및 Fortinet on {{site.data.keyword.cloud_notm}} 서비스를 선택하는 옵션도 사용 가능합니다.
* 인스턴스 세부사항 페이지에 있는 **서비스** 탭의 **사용 가능한 서비스** 탭은 **서비스 추가**로 이름이 변경되었습니다.

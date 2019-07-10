---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-13"

keywords: IBM Cloud Private, ICP, tech specs ICP

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted 개요
{: #icp_overview}

{{site.data.keyword.cloud}} Private Hosted 서비스는 {{site.data.keyword.cloud_notm}} Private Hosted 및 {{site.data.keyword.cloud_notm}} Automation Manager를 VMware vCenter Server 인스턴스에 자동으로 배치합니다. 이 서비스는 마이크로서비스 및 컨테이너의 기능을 {{site.data.keyword.cloud_notm}}의 VMware 환경에 제공합니다. 이 서비스를 사용하면 익숙한 동일 VMware 및 {{site.data.keyword.cloud_notm}} Private 운영 모델과 도구를 온프레미스에서 {{site.data.keyword.cloud_notm}}로 확장할 수 있습니다.

이 서비스는 다음 인스턴스에 사용할 수 있습니다.
* V2.7 이상에 배치되는(또는 업그레이드되는) vCenter Server with Hybridity Bundle 인스턴스
* V2.5 이상에 배치되는(또는 업그레이드되는) vCenter Server 인스턴스

V3.0 이상에 배치되는(또는 업그레이드되는) 인스턴스의 경우 {{site.data.keyword.cloud_notm}} Automation Manager는 {{site.data.keyword.cloud}} Private Hosted 서비스 주문의 일부로도 배치됩니다.
{:note}

## IBM Cloud Private Hosted의 기술 스펙
{: #icp_overview-specs}

다음 표에는 **프로덕션에 사용 가능** 환경 및 **개발/테스트** 환경에 대한 IBM Cloud Private Hosted 서비스를 주문하는 데 필요한 최소 요구사항이 나열되어 있습니다.

표 1. 프로덕션에 사용 가능 및 개발/테스트 환경에 대한 최소 요구사항

|환경 | 코어 수 |  메모리(GB) | 호스트 수 | 스토리지(GB) |
|:---------- |:---- |:------ |:---- |:------- |
| 프로덕션에 사용 가능 | 52 | 640 | 3 | 8,000 |
| 개발/테스트 | 30 | 200 | 3 | 4,000 |

### IBM Cloud Private Hosted에 대한 리소스 요구사항
{: #icp_overview-resource-req}

다음 표에는 프로덕션에 사용 가능 및 개발/테스트 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 서비스에 대한 리소스 요구사항이 나열되어 있습니다.

표 2. 프로덕션에 사용 가능 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 리소스 요구사항

| 노드 유형  | CPU 코어 수   |  메모리(GB) | 디스크 1(GB) | 디스크 2(GB) | VM 수 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 부트       | 12 | 24 | 100 |1 |1 |   
| 관리 |8 | 64 | 500 | 3 | 3 |
| 마스터     |8 | 64 | 200 | 3 | 3 |  
| 프록시      |2 | 4  | 150 | 3 | 3 |
| 작업자     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability Advisor |8 | 16 | 500 |1 |1 |
| GlusterFS  |8 | 16 | 150 | 50 | 3 |
| NFS 서버 |8 | 4  | 350 |1 |1 |
| NSX Edge Services Gateway |2 |1 | 0.5 | 0.5 |2 |
| 문서화된 제한조건 | 52 | 640 |  | 8,000 |   |

표 3. 개발/테스트 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 리소스 요구사항

| 노드 유형  | CPU 코어 수   |  메모리(GB) | 디스크 1(GB) | 디스크 2(GB) | VM 수 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 부트       | 12 | 24 | 100 |1 |1 |   
| 관리 |8 | 16 | 150 |1 |1 |
| 마스터     |8 | 16 | 200 |1 |1 |  
| 프록시      |2 | 4  | 150 |1 |1 |
| 작업자     | 4 | 16 | 200 | 300 | 3 |
| Vulnerability Advisor |8 | 16 | 150 |1 |1 |
| GlusterFS  |8 | 16 | 150 | 50 | 3 |
| NFS 서버 |8 | 4  | 350 |1 |1 |
| NSX Edge Services Gateway |2 |1 | 0.5 | 0.5 |2 |
| 문서화된 제한조건 | 30 | 200 |  | 4,000 |  |

### IBM Cloud Private Hosted 공간 요구사항을 계산하기 위한 공식
{: #icp_overview-formulas}

다음 공식이 IBM Cloud Private 및 관리 오버헤드의 공간 요구사항을 계산하는 데 사용됩니다.

#### 사용 가능한 코어 수를 계산하는 공식
{: #icp_overview-formulas-1}

`AvailableCores = [HostCoreCount - HostOverheadCores - (HostVSanOverheadCorePercentage * HostCoreCount)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadCores`

표 4. 공식 1의 변수에 대한 설명

| 변수 |설명 |단위 |vSAN 예제 | NFS 예제 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |환경에서 워크로드 및 서비스에 사용 가능한 실제 코어의 수 | 코어 수 | 38 | 43 |
| HostCount | 기본 클러스터에 있는 호스트 수 | 호스트 수 | 4 | 4 |
| HostCoreCount | 기본 클러스터의 각 호스트에서 사용 가능한 원시 코어의 수 | 코어 수 | 16 | 16 |
| HostOverheadCores | ESXi 서버에 의해 오버헤드로 예약되는 코어의 수, 0.1 코어와 같음 | 코어 수 | 0.1 | 0.1 |
| MgmtOverheadCores |vCenter Server 관리 컴포넌트(vCenter Server, PSC, AD/DNS, Edges)에 의해 예약되는 코어의 수(5개 코어와 동일함) | 코어 수 |5 |5 |
| vSphereHAHostTolerance |vSphere HA 구성에서 허용하는 호스트 수(하나의 호스트와 동일함) |	 호스트 수	 |1 |1 |
| HostVsanOverheadCorePercentage | vSAN에서 사용되는 호스트 코어의 백분율이며 10%이거나 호스트가 비vSAN인 경우 0% | % | 10% |0% |

#### 사용 가능한 메모리를 계산하는 공식
{: #icp_overview-formulas-2}

`AvailableMemory = [HostMemory - HostOverheadMemory - HostVsanOverheadMemory - (HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize)] * (HostCount - vSphereHAHostTolerance) - MgmtOverheadMemory`

표 5. 공식 2의 변수에 대한 설명

| 변수 |설명 |단위 |vSAN 예제 | NFS 예제 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory | 환경에서 워크로드 및 서비스에 사용 가능한 메모리 크기(GB) | GB | 693 | 860 |
| HostCount | 기본 클러스터에 있는 호스트 수 | 호스트 수  | 6 | 6 |
| HostMemory |기본 클러스터의 각 호스트에서 사용 가능한 원시 메모리의 크기(GB) | GB | 192 | 192 |
| HostVsanCapacityDiskSize | 이 호스트의 각 vSAN 용량 SSD 디스크의 용량 크기(GB)이며 960, 1,946 또는 3,891이거나 호스트가 비vSAN인 경우 0GB임 | GB |960 | 0 |
| HostOverheadMemory |ESXi 서버에 의해 오버헤드로 예약되는 메모리의 크기(GB)이며 4.6GB와 같음 | GB | 4.6 | 4.6 |
| MgmtOverheadMemory |vCenter Server 관리 컴포넌트(vCenter Server, PSC, AD/DNS, Edges)에 의해 예약되는 메모리 크기(GB)이며 77GB임 | GB | 77 | 77 |
| vSphereHAHostTolerance |vSphere HA 구성에서 허용하는 호스트 수(하나의 호스트와 동일함) | 호스트 수	|1 |1 |
| HostVsanOverheadMemoryDiskPercentage | vSAN 관리(용량 vSAN 디스크 중 하나의 백분율로 표시됨)에 의해 예약되는 메모리의 크기(GB)이며 2.75%와 같음 | % | 2.75% | 2.75% |
| HostVsanOverheadMemory | 디스크 크기와 상관없이 vSAN 관리에 의해 예약되는 메모리의 크기(GB)이며 7GB이거나 호스트가 비vSAN인 경우 0GB임 | GB |7 | 0 |

## IBM Cloud Private Hosted 설치 시 고려사항
{: #icp_overview-install}

* {{site.data.keyword.cloud_notm}} Private Hosted 서비스를 설치하기 전에 필수 라이센스를 수집하십시오. 여기에는 {{site.data.keyword.cloud_notm}} Private 및 {{site.data.keyword.cloud_notm}} Automation Manager 라이센스가 모두 포함됩니다. 라이센스가 초기 서비스 배치뿐만 아니라 인프라에서 향후에 크기를 늘리는 경우도 지원되는지 확인하십시오.
* 프로덕션에 사용 가능 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 배치의 경우 호스트당 64GB RAM이 지원되지 않습니다. 따라서 **RAM**에 대해 64GB보다 높은 옵션을 선택해야 합니다.
* {{site.data.keyword.cloud_notm}} Private Hosted 서비스가 환경에 설치되기 전에 환경에 있는 기본 클러스터의 사용 가능한 용량에 대한 검사가 수행되어 서비스 컴포넌트가 적합한지 확인합니다. 용량 검사에 실패하면 서비스가 설치되지 않고 콘솔에서 서비스 상태가 **용량 유효성 검증 실패**로 설정됩니다. 또한 세부사항이 포함된 콘솔 메시지가 표시되고 이메일로 알림을 받습니다. 서비스를 설치하려면 더 많은 호스트를 추가하거나 RAM, CPU 또는 디스크 공간을 해제한 후 콘솔에서 서비스를 다시 추가하여 기본 클러스터의 용량을 늘려야 합니다. 이후 옆에 있는 **삭제** 아이콘을 클릭하여 **용량 유효성 검증 실패** 상태의 기존 서비스를 제거할 수 있습니다.
* 추가 노드를 배치하려면 [추가 노드 배치](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering-deploy-nodes#icp_ordering-deploy-nodes)를 참조하십시오.

## IBM Cloud Private Hosted 제거 시 고려사항
{: #icp_overview-remove}

* {{site.data.keyword.cloud_notm}} Private Hosted 서비스의 초기 설치 중에 배치된 가상 머신(VM)만 삭제합니다. 설치 이후에 배치된 노드는 정리되지 않습니다.
* {{site.data.keyword.cloud_notm}}는 {{site.data.keyword.cloud_notm}} Private Hosted의 초기 설치 중에 작성된 에지 게이트웨이, DLR 및 VXLAN을 삭제합니다. {{site.data.keyword.cloud_notm}} Private Hosted 서비스가 시작되면 VXLAN에 배치한 VM의 연결은 끊어집니다.

## 관련 링크
{: #icp_overview-related}

* [{{site.data.keyword.cloud_notm}} Private Hosted 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_ordering)
* [vCenter Server 및 {{site.data.keyword.cloud_notm}} Private 안내서](/docs/services/vmwaresolutions/archiref/vcsicp?topic=vmware-solutions-vcsicp-intro)
* [{{site.data.keyword.cloud_notm}} Private의 티켓 열기](https://www.ibm.com/mysupport/s/?language=en_US){:new_window}
* [{{site.data.keyword.cloud_notm}} Automation Manager 라이센스 부여](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/licensing.html){:new_window}
* [{{site.data.keyword.cloud_notm}} Automation Manager 컴포넌트](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_managed_components.html){:new_window}

---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Cloud Private Hosted 개요

{{site.data.keyword.cloud}} Private Hosted 서비스는 {{site.data.keyword.cloud_notm}} Private Hosted를 VMware vCenter Server 인스턴스에 자동으로 배치합니다. 이 서비스는 마이크로서비스 및 컨테이너의 기능을 {{site.data.keyword.cloud_notm}}의 VMware 환경에 제공합니다. 이 서비스를 사용하면 익숙한 동일 VMware 및 {{site.data.keyword.cloud_notm}} Private 운영 모델과 도구를 온프레미스에서 {{site.data.keyword.cloud_notm}}로 확장할 수 있습니다.

이 서비스는 다음과 같이 사용할 수 있습니다.
* V2.5 이상에 배치되거나 업그레이드되는 vCenter Server 인스턴스
* V2.7 이상에 배치되거나 업그레이드되는 vCenter Server with Hybridity Bundle 인스턴스
{:note}

## IBM Cloud Private Hosted의 기술 스펙

다음 표에는 **프로덕션 준비** 환경 및 **개발/테스트** 환경에 대한 IBM Cloud Private Hosted 서비스를 주문하는 데 필요한 최소 요구사항이 나열되어 있습니다.

표 1. 프로덕션 준비 및 개발/테스트 환경에 대한 최소 요구사항

|환경| 코어 | 메모리 | 호스트 |스토리지 |
|:---------- |:---- |:------ |:---- |:------- |
| 프로덕션 준비 | 52 | 640 | 3 | 8000 |
| 개발/테스트 | 30 | 200 | 3 | 4000 |

### IBM Cloud Private Hosted에 대한 리소스 요구사항

다음 표에는 프로덕션 준비 및 개발/테스트 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 서비스에 대한 리소스 요구사항이 나열되어 있습니다.

표 2. 프로덕션 준비 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 리소스 요구사항

| 노드 유형  | CPU 코어   |  메모리(GB) | 디스크 1(GB) | 디스크 2(GB) | VM 수 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 부트       |8 | 16 | 100 |1 |1 |   
|관리 |8 | 64 | 500 | 3 | 3 |
| 마스터 |8 | 64 | 200 | 3 | 3 |  
| 프록시      |2 | 4  | 150 | 3 | 3 |
| 작업자     | 4 | 16 | 200 | 300 | 6 |
| Vulnerability Advisor |8 | 16 | 500 | 3 | 3 |
| GlusterFS  |8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 |32 | 250 |1 |1 |
| NFS 서버 |8 | 4개  | 350 |1 |1 |
|에지 |2 |1 | 0.5 | 0.5 |2 |
| 총계 | 162 | 642 | 6401 | 1951 | 26 |
| 문서화된 제한조건 | 52 | 640 |  | 8000 |   |
|   | 1:3 비율 | 1:1 비율 |  | 1:1 비율 |  |

표 3. 개발/테스트 환경의 {{site.data.keyword.cloud_notm}} Private Hosted 리소스 요구사항

| 노드 유형  | CPU 코어   |  메모리(GB) | 디스크 1(GB) | 디스크 2(GB) | VM 수 |
|:---------- |:----------- |:------------ |:----------- |:----------- |:------------- |
| 부트       |8 | 16 | 100 |1 |1 |   
|관리 |8 | 16 | 150 |1 |1 |
| 마스터 |8 | 16 | 200 |1 |1 |  
| 프록시      |2 | 4개  | 150 |1 |1 |
| 작업자     | 4개 | 16 | 200 | 300 | 3 |
| Vulnerability Advisor |8 | 16 | 150 |1 |1 |
| GlusterFS  |8 | 16 | 150 | 50 | 3 |
| Bootstrap ICP/CAM | 16 |32 | 250 |1 |1 |
| NFS 서버 |8 | 4개  | 350 |1 |1 |
|에지 |1 | 0.5 | 0.5 |2 |2 |
| 총계 | 96 | 201 | 2401 | 1050 | 15 |
| 문서화된 제한조건 | 30 | 200 |  | 4000 |  |
|  | 1:3 비율 | 1:1 비율 |  | 1:1 비율 |  |

### IBM Cloud Private Hosted 공간 요구사항을 계산하기 위한 공식

다음 공식이 IBM Cloud Private 및 관리 오버헤드의 공간 요구사항을 계산하는 데 사용됩니다.

공식 1: `AvailableCores = [ HostCoreCount - HostOverheadCores - ( HostVSanOverheadCorePercentage * HostCoreCount) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadCores`

표 4. 공식 1의 변수에 대한 설명

| 변수	|설명 |	단위 |	vSAN 예제 | NFS 예제 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableCores |	환경에서 워크로드 및 서비스에 사용 가능한 실제 코어의 수 |	코어 |	38	| 43 |
| HostCount	| 기본 클러스터에 있는 호스트 수 | 호스트 | 4	| 4개 |
| HostCoreCount	| 기본 클러스터의 각 호스트에서 사용 가능한 원시 코어의 수 |	코어 |	16 | 16 |
| HostOverheadCores	| ESXi 서버에 의해 오버헤드로 예약되는 코어의 수, 0.1 코어와 같음 | 코어 | 0.1 |	0.1 |
| MgmtOverheadCores |vCenter Server 관리 컴포넌트(vCenter Server, PSC, AD/DNS, Edges)에 의해 예약되는 코어의 수(5개 코어와 동일함) | 코어 | 5	|5 |
| vSphereHAHostTolerance |	vSphere HA 구성에서 허용하는 호스트 수(1개의 호스트와 동일함) |	호스트 |1 |1 |
| HostVsanOverheadCorePercentage | vSAN에서 활용하는 호스트 코어의 백분율이며 vSAN 호스트가 아닌 경우 10% 또는 0% | % | 10% |	0% |

공식 2: `AvailableMemory = [ HostMemory - HostOverheadMemory - HostVsanOverheadMemory - ( HostVsanOverheadMemoryDiskPercentage * HostVsanCapacityDiskSize) ] * ( HostCount - vSphereHAHostTolerance ) - MgmtOverheadMemory`

표 5. 공식 2의 변수에 대한 설명

| 변수	|설명 |	단위 |	vSAN 예제 | NFS 예제 |
|:--------- |:----------- |:---- |:------------- |:----------- |
| AvailableMemory	| 환경에서 워크로드 및 서비스에 사용 가능한 메모리 크기(GB) | GB | 	693	| 860 |
| HostCount	| 기본 클러스터에 있는 호스트 수 | 호스트 | 6	| 6 |
| HostMemory |	기본 클러스터의 각 호스트에서 사용 가능한 원시 메모리의 크기(GB) |	GB	| 192 |	192 |
| HostVsanCapacityDiskSize | 이 호스트의 각 vSAN 용량 SSD 디스크의 용량 크기(GB)이며 960, 1946 또는 3891이거나 비vSAN의 경우 0GB임 | GB |	960 | 0 |
| HostOverheadMemory |	ESXi 서버에 의해 오버헤드로 예약되는 메모리의 크기(GB)이며 4.6GB임 |	GB	| 4.6 |	4.6 |
| MgmtOverheadMemory |	vCenter Server 관리 컴포넌트(vCenter Server, PSC, AD/DNS, Edges)에 의해 예약되는 메모리 크기(GB)이며 77GB임 | GB | 77 | 77 |
| vSphereHAHostTolerance | vSphere HA 구성에서 허용하는 호스트 수(1개의 호스트와 동일함) |호스트 |1 |1 |
| HostVsanOverheadMemoryDiskPercentage | vSAN 관리(용량 vSAN 디스크 중 하나의 백분율로 표시됨)에 의해 예약되는 메모리의 크기(GB)이며 2.75%와 같음 |	% | 2.75%	| 2.75% |
| HostVsanOverheadMemory | 디스크 크기와 상관없이 vSAN 관리에 의해 예약되는 메모리의 크기(GB)이며 7GB이거나 비vSAN의 경우 0GB임 | GB |  7	| 0 |

## IBM Cloud Private Hosted 설치 시 고려사항

{{site.data.keyword.cloud_notm}} Private Hosted 서비스를 설치하기 전에 필수 라이센스를 수집하십시오. 보유한 라이센스가 초기 {{site.data.keyword.cloud_notm}} Private Hosted 배치뿐만 아니라 인프라에서 향후 {{site.data.keyword.cloud_notm}} Private Hosted의 크기를 늘리는 경우도 지원할 수 있는지 확인하는 것이 좋습니다. 

## IBM Cloud Private Hosted 제거 시 고려사항

* {{site.data.keyword.cloud_notm}}는 {{site.data.keyword.cloud_notm}} Private Hosted 서비스의 초기 설치 중에 배치된 가상 머신(VM)만 삭제합니다. 설치 이후에 배치된 노드는 정리되지 않습니다. 
* {{site.data.keyword.cloud_notm}}는 {{site.data.keyword.cloud_notm}} Private Hosted 서비스의 초기 설치 중에 작성된 에지 게이트웨이, DLR 및 VXLAN을 삭제합니다. {{site.data.keyword.cloud_notm}} Private Hosted 서비스가 시작되면 VXLAN에 배치한 VM의 연결은 끊어집니다. 

### 관련 링크

* [IBM Cloud Private Hosted 주문](../services/icp_ordering.html)
* [IBM Cloud Private Hosted](https://www.ibm.com/developerworks/community/files/form/anonymous/api/library/eafb752c-55f3-4b07-9b20-b61c8ea980b9/document/af203658-30c0-40ba-81b5-46c393fb723f/media/IBM_Cloud_Private_Hosted-IBM_Cloud.pdf)(PDF 다운로드)
* [IBM Cloud Private의 티켓 열기](https://www.ibm.com/mysupport/s/?language=en_US)

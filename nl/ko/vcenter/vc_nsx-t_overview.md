---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-02"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T 개요
{: #vc_nsx-t_overview}

VMware vCenter Server with NSX-T on {{site.data.keyword.cloud}}는 서비스로 VMware vSphere 스택을 제공하는 호스팅된 프라이빗 클라우드입니다. VMware 환경은 최소 세 개의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 맨 위에 빌드되고, 공유 네트워크 연결 스토리지와 전용 소프트웨어 정의 스토리지 옵션을 제공하며, VMware 환경에는 자동화 배치와 VMware NSX-T로 작동되며 관리하기 쉬운 논리적 에지 방화벽의 구성이 포함됩니다.

대부분의 경우 전체 환경은 하루 내에 프로비저닝할 수 있으며, 베어메탈 인프라는 필요에 따라 신속하고 탄력적으로 컴퓨팅 용량을 늘리거나 줄이도록 스케일링할 수 있습니다.

배치 후 {{site.data.keyword.slportal}}에서 추가 NFS(Network File System) 파일 공유를 주문하고 클러스터의 모든 ESXi 서버에 해당 파일 공유를 수동으로 연결하여 공유 스토리지를 늘릴 수 있습니다.

또한 VMware vSAN은 전용 스토리지 옵션으로도 사용할 수 있습니다. vSAN 클러스터의 vSAN 기반 스토리지 용량을 늘리기 위해 배치 후 더 많은 ESXi 서버를 추가할 수 있습니다.

vCenter Server with NSX-T 인스턴스는 개념 증명(POC) 또는 샌드박스 테스트 전용입니다. 이 환경에 프로덕션 워크로드를 실행하지 마십시오. 추가 기능 서비스 주문 및 업데이트 적용과 같은 관리 기능은 지원되지 않습니다.
{:important}

## vCenter Server with NSX-T 아키텍처
{: #vc_nsx-t_overview-archi}

다음 그림은 3-노드 vCenter Server with NSX-T 배치의 상위 레벨 아키텍처 및 컴포넌트를 나타냅니다.

![vCenter Server with NSX-T 아키텍처](../images/vc_nsx-t_architecture.svg "vCenter Server with NSX-T 아키텍처")

### 실제 인프라
{: #vc_nsx-t_overview-physical-infras}

이 계층은 가상 인프라에서 사용할 실제 인프라(컴퓨팅, 스토리지 및 네트워크 리소스)를 제공합니다.

### 가상화 인프라(컴퓨팅 및 네트워크)
{: #vc_nsx-t_overview-virtualization-infras}

이 계층은 다른 VMware 제품을 통해 실제 인프라를 가상화합니다.
* VMware vSphere는 실제 컴퓨팅 리소스를 가상화합니다.
* VMware NSX-T는 논리 네트워킹 컴포넌트 및 가상 네트워크를 제공하는 네트워크 가상화 플랫폼입니다.

### 가상화 관리
{: #vc_nsx-t_overview-virtualization-mgmt}

이 계층은 임베디드 PSC(Platform Services Controller)가 있는 vCSA(vCenter Server Appliance), 3개의 NSX 노드, 3개의 NSX Edge Services Gateway(ESG) 및 IBM CloudDriver 가상 서버 인스턴스(VSI)로 구성됩니다. CloudDriver VSI는 환경에 호스트 추가 등과 같은 특정 오퍼레이션에 필요하면 요청 시에 배치됩니다.

기본 오퍼링은 최대 400개의 호스트와 최대 4000개의 VM이 포함된 환경을 지원하도록 크기가 조정된 vCenter Server 어플라이언스로 배치됩니다. 동일한 vSphere API 호환 도구 및 스크립트는 IBM 호스팅 VMware 환경을 관리하는 데 사용될 수 있습니다.

기본 오퍼링에는 가상화 관리 계층에 대해 예약된 총 38개의 vCPU와 128GB vRAM이 필요합니다. VM에 남아 있는 호스트 용량은 초과 구독 비율, 가상 머신(VM) 크기 조정 및 워크로드 성능 요구사항과 같은 여러 요인에 따라 달라집니다.

아키텍처에 대한 자세한 정보는 [{{site.data.keyword.vmwaresolutions_short}} 아키텍처 참조](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)를 참조하십시오.

## vCenter Server with NSX-T 인스턴스의 기술 스펙
{: #vc_nsx-t_overview-specs}

다음 컴포넌트가 vCenter Server with NSX-T 인스턴스에 포함됩니다.

표준화된 하드웨어 구성의 가용성 및 가격은 배치에 선택된 {{site.data.keyword.CloudDataCent_notm}}에 따라 달라질 수 있습니다.
{:note}

### Bare Metal Server
{: #vc_nsx-t_overview-bare-metal}

다음 구성 중 하나로 세 개 이상의 {{site.data.keyword.baremetal_short}}를 주문할 수 있습니다.
* **Skylake**: 선택한 CPU 모델 및 RAM 크기를 사용하는 두 개의 CPU Intel Skylake 세대 서버(Intel Xeon 4100/5100/6100 시리즈)  
* **Broadwell**: 선택한 CPU 모델 및 RAM 크기를 사용하는 네 개의 Intel Broadwell 세대 서버(Intel Xeon E7-4800 시리즈)

vSAN 스토리지를 사용하려는 경우 구성에 최소 4개의 {{site.data.keyword.baremetal_short}}가 필요합니다.
{:note}

### 네트워킹
{: #vc_nsx-t_overview-networking}

다음 네트워킹 컴포넌트가 주문됩니다.
*  10Gbps 듀얼 공용 및 사설 네트워크 업링크
*  세 개의 VLAN(Virtual LANs): 한 개의 공용 VLAN 및 두 개의 사설 VLAN
* 계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위한 T1 및 T0 라우터가 있는 하나의 오버레이 네트워크. 이는 수정, 빌드 또는 제거할 수 있는 샘플 라우팅 토폴로지로 배치됩니다.
*  3개의 VMware NSX-T Edge Services Gateway:
  * 관리 네트워킹 토폴로지의 일부로 IBM에서 배치되는 아웃바운드 HTTP 관리 트래픽을 위한 1개의 보안 관리 서비스 VMware NSX ESG. 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 VM에서 사용됩니다. 자세한 정보는 [VM에서 고객 관리 NSX ESG를 사용하도록 네트워크 구성](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config)을 참조하십시오.
  * 아웃바운드 및 인바운드 HTTPS 워크로드 트래픽에 대한 2개의 보안 고객 관리 VMware NSX ESG. 이 게이트웨이는 VPN 액세스 또는 공용 액세스를 제공하기 위해 사용자가 수정할 수 있는 템플리트로 IBM에 의해 배치됩니다. 자세한 정보는 [고객 관리 NSX Edge는 보안 문제점을 발생시킵니까?](/docs/services/vmwaresolutions?topic=vmware-solutions-faq#faq-customer-nsx)를 참조하십시오.

  이 ESG는 **mgmt-nsx-edge0**으로 이름이 지정되었습니다. 사용자는 이 ESG에 액세스할 수 없고 사용할 수 없습니다. 수정하는 경우 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 vCenter Server 인스턴스를 관리하지 못할 수 있습니다. 또한 방화벽을 사용하거나 외부 IBM 관리 컴포넌트에 대한 ESG 통신을 사용 안함으로 설정하면 {{site.data.keyword.vmwaresolutions_short}}를 사용할 수 없게 됩니다.
  {:important}

### Virtual Server 인스턴스
{: #vc_nsx-t_overview-vsi}

다음 VSI(Virtual Server Instance)가 주문됩니다.
* 인스턴스 배치가 완료된 후 시스템이 종료되는 IBM CloudBuilder용 VSI
* 보안 및 강력한 추진력 향상을 위해 하나의 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI 또는 관리 클러스터에 있는 두 개의 고가용성 Microsoft Windows VM을 배치하도록 선택할 수 있습니다.

### 스토리지
{: #vc_nsx-t_overview-storage}

초기 배치 중에 vSAN과 NFS 스토리지 옵션 중에서 선택할 수 있습니다.

배치 후 기존 NFS 또는 vSAN 클러스터에 NFS 스토리지 공유를 추가할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)의 *NFS 스토리지를 vCenter Server 인스턴스에 추가* 섹션을 참조하십시오.
{:note}

#### vSAN 스토리지
{: #vc_nsx-t_overview-vsan-storage}

vSAN 옵션은 디스크 유형, 크기 및 양에 대한 다양한 옵션을 포함하여 사용자 정의된 구성을 제공합니다.
* 디스크 양: 2, 4, 6 또는 8
* 스토리지 디스크: 960GB SSD SED, 1.9TB SSD SED 또는 3.8TB SSD SED

  또한 호스트당 960GB의 두 개 캐시 디스크도 주문됩니다.

  3.8TB SSD(Solid State Disk) 드라이브는 데이터 센터에서 일반적으로 사용 가능하게 되는 경우 지원됩니다.
  {:note}
* 고성능 Intel Optane 옵션은 총 12개의 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공합니다. 이 옵션은 CPU 모델에 따라 달라집니다.

#### NFS 스토리지
{: #vc_nsx-t_overview-nfs-storage}

NFS 옵션은 크기 및 성능에 대한 다양한 옵션을 포함하여 워크로드의 사용자 정의된 공유 파일 스토리지를 제공합니다.
* 크기: 20GB - 24TB
* 성능: 0.25, 2, 4 또는 10IOPS/GB
* 파일 공유의 개별 구성

  10 IOPS/GB 성능 레벨은 파일 공유당 4TB의 최대 용량으로 제한됩니다.
  {:note}

NFS 옵션을 선택한 경우에는 관리 컴포넌트용으로 하나의 2TB 및 4 IOPS/GB 파일 공유가 주문됩니다.

### 라이센스(IBM 제공 또는 BYOL) 및 요금
{: #vc_nsx-t_overview-license-and-fee}

* VMware vSphere Enterprise Plus 6.7u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.4(IBM 제공만 해당)
* (vSAN 클러스터의 경우) VMware vSAN Advanced 또는 Enterprise 6.6
* 지원 및 서비스 요금(노드당 한 개의 라이센스)

## vCenter Server with NSX-T 확장 노드의 기술 스펙
{: #vc_nsx-t_overview-expansion-node-specs}

각 vCenter Server with NSX-T 확장 노드가 {{site.data.keyword.cloud_notm}} 계정에서 다음 컴포넌트를 배치하고 이에 대한 비용을 부과합니다.

### 확장 노드를 위한 하드웨어
{: #vc_nsx-t_overview-expansion-node-hardware}

[vCenter Server with NSX-T 인스턴스의 기술 스펙](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_nsx-t_overview#vc_nsx-t_overview-specs)에 제시된 구성을 사용하는 하나의 Bare Metal Server.

### 확장 노드의 라이센스 및 요금
{: #vc_nsx-t_overview-expansion-node-license-and-fee}

* 하나의 VMware vSphere Enterprise Plus 6.7u1
* 하나의 VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.4
* 하나의 지원 및 서비스 요금
* (vSAN 클러스터의 경우) VMware vSAN Advanced 또는 Enterprise 6.6

{{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌, {{site.data.keyword.vmwaresolutions_short}} 콘솔에서만 {{site.data.keyword.cloud_notm}} 계정에 작성되는 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.
인스턴스를 주문했을 때 {{site.data.keyword.cloud_notm}} 계정에 설치된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기
*  서비스 다시 시작
   이러한 활동의 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.
   {:important}

## 관련 링크
{: #vc_nsx-t_overview-related}

* [vCenter Server 소프트웨어 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server 인스턴스 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [VMware vCenter Server with NSX-T 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [vCenter Server의 연결된 스토리지 ](/docs/services/vmwaresolutions/services?topic=vmware-solutions-storage-benefits#storage-benefits)
* [파일 공유 용량 확장](/docs/infrastructure/FileStorage?topic=FileStorage-expandCapacity#expandCapacity)

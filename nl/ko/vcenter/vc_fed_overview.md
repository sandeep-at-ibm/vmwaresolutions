---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Federal on IBM Cloud 개요

VMware Federal on {{site.data.keyword.cloud}}를 사용하면 미국 연방 정부 기관에 배치된 vCenter Server 인스턴스를 보호하는 옵션을 제공할 뿐만 아니라 기본 vCenter Server 인스턴스를 주문할 수 있습니다. 배치된 인스턴스에 보안을 설정하면 저장되어 있는 인스턴스에 대한 민감한 정보는 제거됩니다. 또한 인스턴스 액세스를 위한 열린 연결이 제거됩니다. 즉, 호스트 및 클러스터 추가 및 제거와 같은 관리 기능을 더 이상 사용할 수 없습니다. 보안 옵션을 선택하고 나면 인스턴스 삭제 기능만 사용할 수 있습니다.

vCenter Server on {{site.data.keyword.cloud_notm}} 및 vCenter Server 아키텍처에 대한 자세한 정보는 [vCenter Server 개요](/docs/services/vmwaresolutions/vcenter/vc_vcenterserveroverview.html)를 참조하십시오.

VMware Federal on {{site.data.keyword.cloud_notm}}는 vCenter Server 오퍼링의 서브세트만 제공합니다. 다중 사이트 구성, BYOL(Bring Your Own License) 및 추가 기능 서비스 주문 옵션은 지원되지 않습니다.
{:note}

## VMware Federal on IBM Cloud 인스턴스의 기술 스펙

다음 컴포넌트가 포함됩니다.

### Bare Metal Server

다음 구성 중 하나를 사용하여 두 개 이상의 {{site.data.keyword.baremetal_short}}를 주문할 수 있습니다.

* 두 개의 CPU Intel Broadwell 세대(Intel Xeon E5-2600 v4 시리즈)
* 두 개의 CPU Intel Skylake 세대(Intel Xeon 4100/5100/6100 시리즈)

NFS 스토리지 구성의 경우 {{site.data.keyword.baremetal_short}}의 권장 수는 기본값인 3으로 설정됩니다.

vSAN 스토리지를 선택하는 경우 구성에 4개의 {{site.data.keyword.baremetal_short}}가 필요합니다.
{:note}

### 네트워킹

다음 네트워킹 컴포넌트가 주문됩니다.
*  세 개의 VLAN(Virtual LANs): 한 개의 공용 VLAN 및 두 개의 사설 VLAN
*  계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 DLR(Distributed Logical Router)이 포함된 하나의 VXLAN(Virtual eXtensible LAN). VXLAN은 VXLAN을 수정하거나 VXLAN에 빌드하거나 VXLAN을 제거할 수 있는 샘플 라우팅 토폴로지로 배치됩니다. 또한 DLR의 새 논리 인터페이스에 추가 VXLAN을 연결하여 보안 구역을 추가할 수 있습니다.
*  두 개의 VMware NSX Edge Services Gateway:
  * 관리 네트워킹 토폴로지의 일부로 IBM에서 배치되는 아웃바운드 HTTPS 관리 트래픽을 위한 보안 관리 서비스 VMware NSX Edge Services Gateway(ESG). 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 가상 머신에서 사용됩니다. 자세한 정보는 [고객 관리 ESG를 사용하도록 네트워크 구성](/docs/services/vmwaresolutions/vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)을 참조하십시오.

    사용자는 이 ESG에 액세스할 수 없고 사용할 수 없습니다. 수정하는 경우 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 vCenter Server 인스턴스를 관리하지 못할 수 있습니다. 또한 방화벽을 사용하거나 외부 IBM 관리 컴포넌트와의 ESG 통신을 사용 안함으로 설정하면 {{site.data.keyword.vmwaresolutions_short}}를 사용할 수 없게 됩니다.
    {:important}
  * VPN 액세스 또는 공용 액세스를 제공하도록 사용자가 수정할 수 있는 템플리트로 IBM에서 배치되는 아웃바운드 및 인바운드 HTTPS 워크로드 트래픽을 위한 보안 고객 관리 VMware NSX Edge Services Gateway. 자세한 정보는 [고객 관리 NSX Edge는 보안 문제점을 발생시킵니까?](/docs/services/vmwaresolutions/vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)를 참조하십시오.

  아웃바운드 HTTPS 관리 트래픽을 위한 VMware NSX ESG(Edge Services Gateway)가 배치된 VMware Federal 인스턴스를 보호하는 조치의 일부로 제거됩니다. 자세한 정보는 [VMware Federal 인스턴스 보호](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)를 참조하십시오.
  {:note}

### Virtual Server 인스턴스

다음 VSI(Virtual Server Instances)가 주문됩니다.
* 인스턴스 배치가 완료된 후 시스템이 종료되는 IBM CloudBuilder용 VSI
* (인스턴스 V2.3 이상의 경우) 보안 및 신뢰성 향상을 위해 하나의 Microsoft Active Directory(AD)용 Microsoft Windows Server VSI 또는 관리 클러스터에 있는 두 개의 고가용성 Microsoft Windows VM을 배치하도록 선택할 수 있습니다.
* (V2.2 인스턴스의 경우) Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되며 검색할 수 있습니다. 이 VSI는 호스트와 가상 머신이 등록되는 인스턴스에 대한 DNS의 역할을 합니다.

### 스토리지

초기 배치 중에 vSAN과 NFS 스토리지 옵션 중에서 선택할 수 있습니다.

#### vSAN 스토리지

vSAN 옵션은 디스크 유형과 양에 대한 다양한 옵션을 포함하여 사용자 정의된 구성을 제공합니다.
* 디스크 양: 2, 4, 6 또는 8.
* 스토리지 디스크: 960GB SSD SED, 1.9TB SSD SED 또는 3.8TB SSD SED

  또한 호스트당 960GB의 두 개 캐시 디스크가 주문됩니다.
* 고성능 Intel Optane 옵션은 총 10개의 용량 디스크에 대해 2개의 추가 용량 디스크 베이를 제공합니다. 이 옵션은 CPU 모델에 따라 달라집니다.

#### NFS 스토리지

NFS 옵션은 크기 및 성능에 대한 다양한 옵션을 포함하여 워크로드의 사용자 정의된 공유 파일 스토리지를 제공합니다.
* 크기: 1, 2, 4, 8 또는 12TB.
* 성능: 2, 4 또는 10IOPS/GB.
* 개별적으로 파일 공유 구성

NFS 옵션을 선택한 경우 관리 컴포넌트용 하나의 2TB, 4IOPS/GB 파일 공유가 주문됩니다.

### IBM 제공 라이센스 및 요금

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.4
* (vSAN 클러스터의 경우) VMware vSAN Advanced 또는 Enterprise 6.6

## VMware Federal on IBM Cloud 확장 노드의 기술 스펙

각 vCenter Server 확장 노드가 배치되고 {{site.data.keyword.cloud_notm}} 계정에서 다음 컴포넌트에 대한 비용이 발생합니다.

### 확장 노드를 위한 하드웨어

[VMware Federal on {{site.data.keyword.cloud_notm}} 인스턴스의 기술 스펙](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html#technical-specifications-for-vmware-federal-on-ibm-cloud-instances)에 제시된 구성을 지닌 하나의 Bare Metal Server.

### 확장 노드의 라이센스 및 요금

* 하나의 VMware vSphere Enterprise Plus 6.5u1
* 하나의 VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.4
* (vSAN 클러스터의 경우) VMware vSAN Advanced 또는 Enterprise 6.6

{{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌, {{site.data.keyword.vmwaresolutions_short}} 콘솔에서만 {{site.data.keyword.cloud_notm}} 계정에 작성되는 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.
{:important}

**주의:** 인스턴스를 주문했을 때 {{site.data.keyword.cloud_notm}} 계정에 설치된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴 또는 제거
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  컴포넌트 전원 끄기

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

### 관련 링크

* [VMware Federal 인스턴스에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html)
* [VMware Federal 인스턴스 주문](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html)
* [VMware Federal 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions/vcenter/fed_addviewdeleteclusters.html)
* [VMware Federal 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter/vc_fed_addingremovingservers.html)
* [VMware Federal 인스턴스 보호](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)
* [{{site.data.keyword.cloud_notm}} file and block storage](https://www.ibm.com/cloud/garage/content/architecture/virtualizationArchitecture/shared-storage){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-07-01"

keywords: single-node trial, data protection DR, tech specs data protection DR

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 개요
{: #dr_backup_bundle_overview}

데이터 보호 및 재해 복구를 위한 단일 노드 평가판을 통해 {{site.data.keyword.cloud}}를 시범 작동하여
VMware 워크로드를 {{site.data.keyword.cloud_notm}}에 마이그레이션하고 복구할 수 있습이니다. 또한 데이터 보호 및 재해 복구를 위한 단일 노드 평가판에는 Veeam on {{site.data.keyword.cloud_notm}}, VMware HCX on {{site.data.keyword.cloud_notm}} 및 Zerto on {{site.data.keyword.cloud_notm}} 서비스가 포함되어 있습니다.

단일 노드 평가판은 온프레미스 환경과 동일한 도구를 사용하여 관리될 수 있는 싱글 테넌트 VMware 플랫폼을 제공하는 VMware vCenter Server on {{site.data.keyword.cloud_notm}}의 평가판 버전입니다. 온프레미스로 제공되는 동일한 레벨의 제어 및 가시성을 유지하면서 클라우드의 속도와 스케일의 이점을 이용할 수 있습니다.

평가판은 최대 20개의 단순 개발에 대한 마이그레이션 또는 vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle을 사용한 워크로드 테스트를 위해 설계되었습니다. 자동화는 몇 시간 내에 {{site.data.keyword.cloud_notm}}에서 VMware HCX를 설치 및 구성하고, Veeam on {{site.data.keyword.cloud_notm}} 및 Zerto on {{site.data.keyword.cloud_notm}}를 설치합니다. Veeam on {{site.data.keyword.cloud_notm}} 및 Zerto on {{site.data.keyword.cloud_notm}}를 사용하여 20개의 가상 머신(VM)을 백업하고 복제할 수 있습니다. 

데이터 보호 및 재해 복구를 위한 단일 노드 평가판은 개념 증명(POC)에만 사용됩니다. 이 환경에 프로덕션 워크로드를 실행하지 마십시오. 호스트 및 클러스터 추가 및 제거, 추가 기능 서비스 추가 주문 및 업데이트 적용과 같은 관리 기능은 지원되지 않습니다.
{:important}

단일 노드 평가판 인스턴스가 배치된 후 인스턴스에 대한 지원을 받기 위해 [IBM Analytics Cloud Expert Services](https://www.ibm.com/analytics/us/en/services/cloud-expert-services.html){:external}에서 [IBM On Demand Consulting for Hybrid Cloud](https://public.dhe.ibm.com/software/data/sw-library/services/ODC.pdf){:external}를 사용할 수 있습니다. 또한 [{{site.data.keyword.cloud_notm}} Garage Services](https://www.ibm.com/cloud/garage/){:external}는 최신 클라우드 기본 사례를 통해 애플리케이션 현대화를 가속화하는 데 유용합니다.

이 평가판은 최대 90일 동안 사용할 수 있습니다. 매월 반복되는 비용은 인스턴스가 주문되는 시점이 아닌 비용 청구 스케줄에 따라 청구됩니다. 청구 주기의 마지막 날 또는 이전에 인스턴스가 취소되지 않으면 다음 달에 청구됩니다. 네 번째 달이 시작되기 전에 취소가 완료되지 않으면 90일 간의 평가로 4개월의 비용 청구가 발생할 수 있습니다.
{:note}

평가판 사용이 완료되면 이 환경을 삭제한 다음 용량 요구사항을 충족하는 새 환경을 프로비저닝할 수 있습니다.

## 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스의 기술 스펙
{: #dr_backup_bundle_overview-tech-specs}

다음 컴포넌트는 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스에 포함됩니다.

표준화된 하드웨어 구성의 가용성 및 가격은 배치에 선택된 {{site.data.keyword.CloudDataCent_notm}}에 따라 달라질 수 있습니다.
{:note}

### Bare Metal Server
{: #dr_backup_bundle_overview-bare-metal}

Skylake 듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2 GHz 및 최대 20개의 VM을 위한 384GB RAM

#### CPU 과다 할당
{: #dr_backup_bundle_overview-cpu}

16:1 CPU 과다 할당(vCenter Server 관리, HCX 및 20개의 고객 워크로드용)

#### RAM 과다 할당
{: #dr_backup_bundle_overview-ram}

* 1.22:1 RAM 과다 할당(각 8GB인 20개의 워크로드 VM의 고객 배치용)
* 1:1(과다 할당 없음)(각 8GB인 9개의 워크로드 VM의 고객 배치용)

### NFS 스토리지
{: #dr_backup_bundle_overview-nfs-storage}

* 관리를 위한 2TB
* 고객 워크로드를 위한 1TB(20개의 고객 VM용)

### 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스의 네트워킹 스펙
{: #dr_backup_bundle_overview-networking-specs}

다음 네트워킹 컴포넌트가 주문됩니다.
*  10Gbps 듀얼 공용 및 사설 네트워크 업링크
*  세 개의 VLAN(Virtual LANs): 한 개의 공용 VLAN 및 두 개의 사설 VLAN
*  계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 DLR(Distributed Logical Router)이 포함된 하나의 VXLAN(Virtual eXtensible LAN). VXLAN은 VXLAN을 수정하거나 VXLAN에 빌드하거나 VXLAN을 제거할 수 있는 샘플 라우팅 토폴로지로 배치됩니다. 또한 DLR의 새 논리 인터페이스에 추가 VXLAN을 연결하여 보안 구역을 추가할 수 있습니다.
*  두 개의 VMware NSX Edge Services Gateway:
  * 관리 네트워킹 토폴로지의 일부로 IBM에서 배치되는 아웃바운드 HTTPS 관리 트래픽을 위한 보안 관리 서비스 VMware NSX Edge Services Gateway(ESG). 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 VM에서 사용됩니다.

    사용자는 이 ESG에 액세스할 수 없고 사용할 수 없습니다. 수정하는 경우 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스를 관리하지 못할 수 있습니다. 또한 방화벽을 사용하거나 외부 IBM 관리 컴포넌트와의 ESG 통신을 사용 안함으로 설정하면 {{site.data.keyword.vmwaresolutions_short}}를 사용할 수 없게 됩니다.
    {:important}
  * VPN 액세스 또는 공용 액세스를 제공하도록 사용자가 수정할 수 있는 템플리트로 IBM에서 배치되는 아웃바운드 및 인바운드 HTTPS 워크로드 트래픽을 위한 보안 고객 관리 VMware NSX Edge Services Gateway.

### Virtual Server 인스턴스
{: #dr_backup_bundle_overview-vsi}

다음 VSI(Virtual Server Instance)가 주문됩니다.

* IBM CloudBuilder용 VSI는 인스턴스 배치가 완료된 후 취소됩니다.
* Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되어 있으며 검색할 수 있습니다. VSI는 호스트와 VM이 등록되는 인스턴스에 대한 DNS의 역할을 합니다.
* VSI for Zerto on {{site.data.keyword.cloud_notm}} - Zerto Virtual Manager
* Veeam Backup and Replication 9.5 OS 추가 기능 및 Veeam Availability Suite 9.5가 포함된 VSI

### IBM 제공 라이센스 및 요금
{: #dr_backup_bundle_overview-license-and-fee}

다음 라이센스는 데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스 주문에 포함됩니다.

* vCenter Server with Hybridity Bundle 라이센스:
  * VMware vSphere Enterprise Plus 6.7u1
  * VMware vCenter Server 6.5
  * VMware NSX Service Providers Advanced Edition 6.4
* {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2

데이터 보호 및 재해 복구를 위한 단일 노드 평가판 인스턴스는 BYOL(Bring Your Own License)을 지원하지 않습니다.
{:note}

## VMware HCX on IBM Cloud의 기술 스펙
{: #dr_backup_bundle_overview-hcx-tech-specs}

데이터 보호 및 재해 복구를 위한 단일 노드 평가판에는 HCX on {{site.data.keyword.cloud_notm}}가 포함되어 있습니다. 다음 컴포넌트가 주문되고 HCX on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

온프레미스 HCX 인스턴스에는 라이센싱 및 활성화만 포함됩니다.
{:note}

### HCX 관리를 위한 VMware NSX Edge Services Gateway의 활성/수동 쌍
{: #dr_backup_bundle_overview-esg}

* CPU: 6개의 vCPU
* RAM: 8GB
* 디스크: 3GB VMDK

### HCX 관리 어플라이언스 - 가상 머신
{: #dr_backup_bundle_overview-hcx-mgmt-appliance}

* CPU: 4개의 vCPU
* RAM: 12GB
* 디스크: 60GB VMDK

L2 연결, WAN 최적화 및 게이트웨이 연결을 위해 필요에 따라 구성 중에 추가로 HCX 어플라이언스가 배치됩니다.

### HCX on IBM Cloud의 네트워킹 스펙
{: #dr_backup_bundle_overview-hcx-networking-specs}

* 16개 IP 주소가 포함된 한 개의 공인 포터블 서브넷
* 64개 IP 주소가 포함된 두 개의 사설 포터블 서브넷
* 사설 포터블 vMotion 서브넷의 8개 IP 주소

## Veeam on {{site.data.keyword.cloud_notm}}의 기술 스펙
{: #dr_backup_bundle_overview-veeam-tech-specs}

데이터 보호 및 재해 복구를 위한 단일 노드 평가판에는 Veeam on {{site.data.keyword.cloud_notm}}가 포함되어 있습니다. 다음 컴포넌트가 주문되고 Veeam on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

* Veeam Availability Suite의 25팩 라이센스
* 4000GB 스토리지
* 0.25 IOPS/GB 스토리지 성능
* Windows Server 2016 Standard Edition(64비트)
* 4 x 2.0GHz 코어
* 8GB RAM
* 1Gbps 사설 네트워크 업링크
* 100GB 디스크(SAN)

## Zerto on {{site.data.keyword.cloud_notm}}의 기술 스펙
{: #dr_backup_bundle_overview-zerto-tech-specs}

데이터 보호 및 재해 복구를 위한 단일 노드 평가판에는 Zerto on {{site.data.keyword.cloud_notm}}가 포함되어 있습니다. 다음 컴포넌트가 주문되고 Zerto on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

* Zerto Virtual Replication V6.5u3 라이센스
* 하나의 VSI(Virtual Service Instance) - ZVM(Zerto Virtual Manager)
* 2 x 2.0GHz 코어
* 4GB RAM
* Windows Server 2016 Standard Edition(64비트)
* 100GB (SAN) 디스크

## IBM Cloud Automation Manager의 기술 스펙
{: #dr_backup_bundle_overview-cam-tech-specs}

{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2는 데이터 보호 및 재해 복구를 위한 모든 단일 노드 평가판 인스턴스의 문서/테스트 토폴로지를 사용하여 설치됩니다. {{site.data.keyword.cloud_notm}} Automation Manager에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} Automation Manager 문서](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/kc_welcome.html){: external}를 참조하십시오.

## 관련 링크
{: #dr_backup_bundle_overview-related}

* [VMware HCX 리소스](https://hcx.vmware.com/#/docs){:external}
* [VMware HCX User Guide](https://docs.vmware.com/en/VMware-HCX/services/user-guide/GUID-BFD7E194-CFE5-4259-B74B-991B26A51758.html){:external}
* [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingveeam) 관리
* [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions?topic=vmware-solutions-managingzertodr) 관리

---

copyright:

  years:  2016, 2019

lastupdated: "2019-06-18"

keywords: Veeam, Veeam install, tech specs Veeam

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Veeam on IBM Cloud 개요
{: #veeam_considerations}

Veeam on {{site.data.keyword.cloud}} 서비스는 엔터프라이즈가 고가용성을 달성할 수 있도록 VMware 하이퍼바이저와 직접 원활하게 통합합니다. 이 서비스는 애플리케이션 및 데이터에 대한 복구 지점 및 시간 목표를 제공합니다. 복구 지점 및 시간 목표는 구성이 완료된 후 15분 내에 제공될 수 있습니다. 이 서비스를 사용하여 Veeam 콘솔에서 인프라에 대한 모든 가상 머신(VM)의 백업과 복원을 모두 직접 제어합니다.

이 서비스는 V1.8 이상에 배치되는 인스턴스에 대해서만 사용 가능합니다. 설치된 현재 Veeam 버전은 9.5u4입니다.
{:note}

## Veeam on IBM Cloud의 기술 스펙
{: #veeam_considerations-specs}

다음 컴포넌트가 주문되고 Veeam on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

### VSI
{: #veeam_considerations-specs-vsi}

* Veeam Backup and Replication 9.5 OS 추가 기능 및 Veeam Availability Suite 9.5가 포함된 단일 VSI
* Windows Server 2016 Standard Edition(64비트)
* 4 x 2.0GHz 코어
* 8 vCPU, 32GB RAM
* 1Gbps 사설 네트워크 업링크
* 100GB 디스크(SAN)

### 백업용 스토리지
{: #veeam_considerations-specs-storage}

* Endurance iSCSI 스토리지(2,000, 4,000, 8,000 또는 12,000GB)
* 스토리지 성능(0.25, 2 또는 4IOPS/GB)

Veeam 서비스 설치 및 구성의 일부로 다음 저장소가 작성됩니다.
* Veeam 구성 백업 파일의 경우, 저장소 이름은 `IC4V Default Config Backup Repository`입니다. Veeam 백업이 저장되는 폴더의 경로는 <Drive>:\ConfigBackup\`입니다.
* 스케일 확장의 경우, 저장소 이름은 `IC4V Scale-Out Repository`입니다. 자세한 정보는 [스케일 확장 저장소 추가](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icos_ordering#icos_ordering-scale-repo)를 참조하십시오.
* 가상 머신(VM) 백업의 경우, 저장소 이름은 ``IC4V Default VM Backup Repository``입니다. VM 백업이 저장되는 폴더의 경로는 ``<Drive>:\VMBackup\`입니다. 이 저장소는 범위로 ``IC4V Scale-Out repository`에 추가됩니다.

### 네트워킹
{: #veeam_considerations-specs-networking}

하나의 기본 사설 IP 주소.

### 라이센스 및 요금
{: #veeam_considerations-specs-licenses}

* Veeam Availability Suite 9.5(10, 25, 50, 100 또는 200 VM 라이센스)

## Veeam on IBM Cloud 설치 시 고려사항
{: #veeam_considerations-install}

스토리지 저장소와 Veeam 서버는 원래 팟(Pod) 및 데이터 센터에 있습니다. 따라서 원격 클러스터에 대한 백업 오퍼레이션의 성능이 저하될 수 있습니다.

## Veeam KeyControl on IBM Cloud 제거 시 고려사항
{: #veeam_considerations-remove}

Veeam on {{site.data.keyword.cloud_notm}} 서비스를 제거하면 모든 백업이 중지되고 이전 백업이 모두 삭제됩니다. 관리 VM의 백업이 중지되고 이전 백업의 삭제를 되돌릴 수 없습니다. 관리 VM이 손상되면 복원할 수 없습니다.

## 관련 링크
{: #veeam_considerations-related}

* [Veeam on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Veeam on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam 웹 사이트](https://www.veeam.com/){:new_window}
* [Veeam Help Center](https://www.veeam.com/documentation-guides-datasheets.html){:new_window}

---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

subcollection: vmwaresolutions


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

* Veeam Backup and Replication 9.5 OS 추가 기능이 포함된 단일 VSI
* Windows Server 2016 Standard Edition(64비트)
* 4 x 2.0GHz 코어
* 8GB RAM
* 1Gbps 사설 네트워크 업링크
* 100GB 디스크(SAN)

### 백업용 스토리지
{: #veeam_considerations-specs-storage}

* Endurance iSCSI 스토리지(2000, 4000, 8000 또는 12000GB)
* 스토리지 성능(0.25, 2 또는 4IOPS/GB)

### 네트워킹
{: #veeam_considerations-specs-networking}

하나의 기본 사설 IP 주소.

### 라이센스 및 요금
{: #veeam_considerations-specs-licenses}

Veeam Backup and Replication 9.5 Enterprise Plus(10, 25, 50, 100 또는 200VM 라이센스).

### 관리
{: #veeam_considerations-specs-mgmt}

기본적으로 최대 5개의 VM 및 2000GB의 스토리지로 구성된 관리 백업.

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

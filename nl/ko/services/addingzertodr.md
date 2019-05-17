---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud 개요
{: #addingzertodr}

Zerto on {{site.data.keyword.cloud}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware virtual 환경에서 데이터를 보호하고 복구하도록 복제 및 재해 복구 기능을 배치 오퍼링에 통합합니다.

이 서비스는 V1.2 이상에 배치되는 인스턴스에 대해서만 사용 가능합니다. 설치된 현재 Zerto 버전은 6.5 update 3입니다.
{:note}

## Zerto on IBM Cloud의 기술 스펙
{: #addingzertodr-specs}

다음 컴포넌트가 주문되고 Zerto on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

Zerto VRA(Virtual Replication Appliance) 컴포넌트는 기본 클러스터에만 배치됩니다.
{:note}

### VSI
{: #addingzertodr-specs-vsi}

* 하나의 VSI(Virtual Service Instance) - ZVM(Zerto Virtual Manager)
* 2 x 2.0GHz 코어
* 4GB RAM
* Windows Server 2016 Standard Edition(64비트)

### 스토리지
{: #addingzertodr-specs-storage}

100GB (SAN) 디스크

### 네트워킹
{: #addingzertodr-specs-network}

* 한 개의 기본 사설 IP 주소
* 1Gbps 사설 네트워크 업링크

### 라이센스 및 요금
{: #addingzertodr-specs-licenses}

Zerto Replication V6.5 업데이트 3 라이센스

## 관련 링크
{: #addingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Zerto on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com 웹 사이트](https://www.zerto.com){:new_window}
* [Zerto 기술 문서](https://www.zerto.com/myzerto/technical-documentation/){:new_window}

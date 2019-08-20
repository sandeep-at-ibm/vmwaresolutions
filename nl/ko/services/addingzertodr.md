---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-02"

keywords: Zerto, Zerto components, tech specs Zerto

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Zerto on IBM Cloud 개요
{: #addingzertodr}

Zerto on {{site.data.keyword.cloud}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware 가상 환경에서 데이터를 보호하고 복구하도록 복제 및 재해 복구 기능을 배치 오퍼링에 통합합니다.

설치된 현재 Zerto on {{site.data.keyword.cloud_notm}} 버전은 6.5 Update 4입니다.
{:note}

## 시작하기 전에
{: #addingzertodr-req}

* {{site.data.keyword.cloud_notm}} 계정이 청구 가능하며 인스턴스가 배치된 {{site.data.keyword.cloud_notm}} 인프라 계정에 링크되어 있는지 확인하십시오. 자세한 정보는 [Zerto 복제 청구](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-billing)를 참조하십시오.
* 이 서비스는 V1.2 이상에 배치되는 인스턴스에 대해서만 사용 가능합니다. 설치된 현재 Zerto 버전은 6.5 update 3입니다.

## Zerto on IBM Cloud의 기술 스펙
{: #addingzertodr-specs}

다음 컴포넌트가 주문되고 Zerto on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

Zerto VRA(Virtual Replication Appliance) 컴포넌트는 기본 클러스터에만 배치됩니다.
{:note}

### Virtual Service Instance
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

* VSI
  * 한 개의 기본 사설 IP 주소
  * 1Gbps 사설 네트워크 업링크
* VRA(Virtual Replication Appliances)
  * VRA 배치를 위한 하나의 사설 포터블 서브넷

### 라이센스 및 요금
{: #addingzertodr-specs-licenses}

Zerto Replication V6.5 업데이트 3 라이센스

## 관련 링크
{: #addingzertodr-related}

* [Zerto on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering)
* [Zerto on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingzertodr)
* [Zerto on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)
* [zerto.com 웹 사이트](https://www.zerto.com){: external}
* [Zerto 기술 문서](https://www.zerto.com/myzerto/technical-documentation/){: external}

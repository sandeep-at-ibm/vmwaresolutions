---

copyright:

  years:  2016, 2018

lastupdated: "2018-07-18"

---

# NetApp ONTAP Select 개요

{{site.data.keyword.cloud}} 배치 시 NetApp ONTAP Select의 아키텍처 및 컴포넌트를 검토하십시오.

## NetApp ONTAP Select 아키텍처

NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 오퍼링은 스토리지 가상화 서비스를 제공하여 vCenter Server 배치를 보완합니다.

다음 그림은 NetApp ONTAP Select on vCenter Server 배치의 전체 아키텍처에 대해 설명합니다.

그림 1. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}의 상위 레벨 아키텍처

![NetApp ONTAP Select 아키텍처](np_architecture.svg "NetApp ONTAP Select on IBM Cloud의 상위 레벨 아키텍처")

### 실제 인프라

이 계층은 가상 인프라에서 사용할 실제 인프라(컴퓨팅, 네트워크 및 스토리지 리소스)를 제공합니다.

### 가상화 인프라(컴퓨팅, 네트워크 및 NetApp ONTAP Select)

이 계층은 다음의 VMware 제품 및 NetApp ONTAP Select 제품을 통해 실제 인프라를 가상화합니다. 
* VMware vSphere는 실제 컴퓨팅 리소스를 가상화합니다.
* VMware NSX는 논리 네트워킹 컴포넌트 및 가상 네트워크를 제공하는 네트워크 가상화 플랫폼입니다.
* NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}는 4개의 호스트에 대해 4개의 VM으로 구성된 ONTAP Select 클러스터를 배치합니다.

다음 그림은 NetApp ONTAP Select 배치의 컴포넌트에 대해 설명합니다.

그림 2. NetApp ONTAP Select 컴포넌트

![NetApp ONTAP Select 컴포넌트](np_netappcomponents.svg "NetApp ONTAP Select의 컴포넌트")

### 가상화 관리

이 계층은 vCenter Server 가상 어플라이언스, NSX Manager, 두 개의 NSX ESG, 세 개의 NSX Controller, PSC(Platform Services Controller) 가상 어플라이언스, vCSA(vCenter Server Appliance) 및 IBM CloudDriver 가상 머신으로 구성됩니다.

NetApp ONTAP Select는 VMware 클러스터에서 실행되고 호스트의 로컬 스토리지를 가상화합니다. NetApp ONTAP Select는 전용 모델에 배치되며, 여기서 기타 워크로드는 이와의 클러스터 공유가 예상되지 않습니다. 결과적으로 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 오퍼링의 하드웨어 구성은 NetApp ONTAP Select의 요구사항에 따라서만 크기가 조정됩니다.

## NetApp ONTAP Select 인스턴스의 기술 스펙

다음 컴포넌트는 NetApp ONTAP Select 인스턴스에 포함됩니다.

**참고**: 표준화된 구성의 가용성 및 가격 책정은 배치에 선택된 {{site.data.keyword.CloudDataCent_notm}}에 따라 달라질 수 있습니다.

### 스토리지

* 세 개의 옵션: **고성능(중형)**, **고성능(대형)** 및 **고용량**
* 핫 스페어가 포함된 RAID 5
* 두 개의 1-TB SATA 드라이브 ESXi OS – RAID 1
* 관리 데이터 저장소 – 관리 VM용 500GB

### 사전 설정 구성

다음의 구성 옵션이 포함된 4개의 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}가 제공됩니다. 
* **고성능(중형)** – 프리미엄 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 128GB RAM / 노드당 22개의 1.9TB SSD 드라이브 용량 / 네 개의 노드 클러스터의 유효한 용량 – 59TB
* **고성능(대형)** – 프리미엄 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 128GB RAM / 노드당 22개의 3.8TB SSD 드라이브 용량 / 네 개의 노드 클러스터의 유효한 용량 – 118TB
* **고용량** – 표준 라이센스 / 듀얼 Intel Xeon E5-2650 v4(총 24개의 코어, 2.2GHz) / 64GB RAM / 노드당 34개의 4TB SATA 드라이브 용량 / 네 개의 노드 클러스터의 유효한 용량 – 190TB

**참고:** 3.8TB SSD(Solid State Disk) 드라이브는 일반적으로 데이터 센터에서 사용 가능할 때 지원됩니다.

### 하드웨어

* 세 개의 RAM 및 디스크 옵션: **고성능(중형)**, **고성능(대형)** 및 **고용량**
* 두 개의 1TB SATA 드라이브 ESXi OS
* 한 개의 RAID 디스크 제어기
* VMware Server Virtualization 6.5

### 네트워킹

* 10Gbps 듀얼 공용 및 사설 네트워크 업링크
* 세 개의 VLAN(Virtual LANs): 한 개의 공인 VLAN 및 두 개의 사설 VLAN
* 하나의 안전한 VMware NSX Edge Services Gateway

### Virtual Server 인스턴스

두 개의 VSI(Virtual Server Instances):
* Microsoft Active Directory(AD) 및 DNS(Domain Name System) 서비스용 VSI
* 인스턴스 배치가 완료된 후 시스템이 종료되는 IBM CloudBuilder용 VSI

### 라이센스 및 요금

*  네 개의 Premium/Standard Edition NetApp ONTAP Select 라이센스(사용자가 제공함)
*  VMware vSphere 6.5 Enterprise Plus 에디션
*  VMware vCenter Server 6.5
*  VMware NSX Service Providers Edition(Base, Advanced 또는 Enterprise) 6.4
*  지원 및 서비스 요금(노드당 한 개의 라이센스)

**중요**: {{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서만 {{site.data.keyword.cloud_notm}} 계정에서 작성된 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 관리해야 합니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항은 콘솔과 동기화되지 않습니다.

**주의**: {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트(인스턴스를 주문했을 때 {{site.data.keyword.cloud_notm}} 계정에 설치됨)를 관리하면 환경이 불안정해질 수 있습니다. 이러한 관리 활동에는 다음이 포함됩니다.
*  컴포넌트 추가, 수정, 리턴, 제거 또는 전원 끄기
*  ESXi 서버 추가 또는 제거를 통한 인스턴스 용량의 확장 또는 축소
*  서비스 다시 시작

   이 활동에 대한 예외에는 {{site.data.keyword.slportal}}의 공유 스토리지 파일 공유 관리가 포함됩니다. 이러한 활동에는 공유 스토리지 파일 공유 주문, 삭제(마운트된 경우 데이터 저장소에 영향을 줄 수 있음), 권한 부여 및 마운트가 포함됩니다.

### 관련 링크

* [NetApp ONTAP Select 인스턴스 계획](np_planning.html)
* [NetApp ONTAP Select 인스턴스 주문](np_orderinginstances.html)
* [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)
* [NetApp ONTAP Documentation Center](http://docs.netapp.com/ontap-9/index.jsp?topic=%2Fcom.netapp.doc.exp-clus-peer%2Fhome.html){:new_window}

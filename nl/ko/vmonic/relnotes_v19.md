---

copyright:

  years:  2016, 2018

lastupdated: "2017-10-13"

---

# V1.9 릴리스 정보

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 추가 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VMware vSphere on IBM Cloud

이 릴리스에서는 선택된 VMware 컴포넌트를 기반으로 VMware 호환 가능 컴퓨팅, 스토리지 및 네트워크 리소스를 사용자 정의하고 주문하여 자체 IBM 호스팅 VMware 가상 환경을 빌드할 수 있도록 허용하는 VMware vSphere on {{site.data.keyword.cloud_notm}} 오퍼링을 도입했습니다. vSphere on {{site.data.keyword.cloud_notm}}가 선택적 VMware 컴포넌트의 설치, 구성 및 가져오기를 자동화하지는 않지만, 사용자는 비즈니스 요구사항에 가장 적합한 환경을 디자인하고 구축하기 위한 최대한의 유연성을 보유합니다. {{site.data.keyword.CloudDataCent_notm}}에서 기존 vSphere 클러스터를 확장하거나 ESXi 서버의 새 vSphere 클러스터를 작성하여 시작할 수 있습니다. 

자세한 정보는 다음을 참조하십시오.
* [새 vSphere 클러스터 주문](../vsphere/vs_orderinginstances.html)
* [기존 vSphere 클러스터 스케일링](../vsphere/vs_scalingexistingclusters.html)

## NetApp ONTAP Select on IBM Cloud

이 릴리스에서는 IBM Cloud의 전용 {{site.data.keyword.baremetal_short}}의 서비스로서 NetApp ONTAP Select를 구현하는 소프트웨어 정의 스토리지에 대한 가상 어플라이언스인 NetApp ONTAP Select on {{site.data.keyword.cloud_notm}} 오퍼링을 도입했습니다. NetApp ONTAP Select on {{site.data.keyword.cloud_notm}}는 고성능(모두 SSD) 및 고용량(모두 SATA) 구성 모두에서 제공됩니다.
전용 인프라에서 스토리지를 호스팅하고 NetApp 기능(예: 유휴 데이터의 중복 제거, 압축 및 암호화)을 제공합니다. 이 오퍼링을 통해 빠르고 효율적인 NetApp Snapshot® 사본, FlexClone® 사본 및 SnapMirror® 복제와 같은 고급 데이터 관리 기능을 사용하여 데이터를 보호하면서 민첩성과 유연성으로 스토리지 리소스를 프로비저닝할 수 있습니다.

자세한 정보는 다음을 참조하십시오.
* [NetApp ONTAP Select 개요](../netapp/np_netappoverview.html)
* [NetApp ONTAP Select 인스턴스 주문](../netapp/np_orderinginstances.html)

## F5 on IBM Cloud 서비스:

F5 BIG-IP Virtual Edition(VE) on {{site.data.keyword.cloud_notm}} 서비스는 이제 VMware Cloud Foundation 및 VMware vCenter Server 인스턴스 모두에 사용 가능합니다. 이 서비스는 로컬 및 글로벌 스케일의 인텔리전트 L4-L7 로드 밸런싱 및 트래픽 관리 서비스, 강력한 네트워크 및 웹 애플리케이션 방화벽 보호, 안전하고 연합된 애플리케이션 액세스를 제공합니다.
인스턴스를 주문할 때 포함된 F5 BIG-IP Virtual Edition (VE) on {{site.data.keyword.cloud_notm}} 서비스와 함께 인스턴스를 주문하거나 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 인스턴스 특성 세부사항 페이지에 있는 **서비스** 탭에서 나중에 이 서비스를 기존 인스턴스에 추가할 수 있습니다. 사용자의 요구사항에 따라 BIG-IP VE에 대한 세 개의 라이센스 부여 옵션 중 하나를 선택할 수 있습니다.

자세한 정보는 다음을 참조하십시오.
* [F5 on {{site.data.keyword.cloud_notm}}에 대한 고려사항](../services/f5_considerations.html)
* [F5 on {{site.data.keyword.cloud_notm}} 관리](../services/managing_f5.html)

## IBM Integrated Managed Infrastructure의 관리 서비스

IBM Integrated Managed Infrastructure(IMI)의 관리 서비스는 이제 VMware Cloud Foundation 인스턴스에 사용 가능합니다. IMI는 모듈화 서비스로 VMware 가상 인프라 관리를 간소화할 수 있고 신뢰할 수 있는 단일 제공자의 역할을 수행하여 가상 IT 인프라에 대한 모니터링 및 관리의 복잡성을 줄일 수 있습니다. 더 높은 값의 이니셔티브에 초점을 지정할 수 있도록 IMI에 대한 특정 일별 오퍼레이션(예: 모니터링)을 오프로드하십시오.

**시작하기** 페이지에서 언제든지 컨설팅 및 견적을 요청할 수 있습니다.
자세한 정보는 [IMI의 관리 서비스 요청](../services/managing_imi.html#requesting-managed-services-from-imi)을 참조하십시오.

## vCenter Server 및 NetApp ONTAP Select 인스턴스에 대한 인스턴스 이름 제한사항

인스턴스 주문 시 {{site.data.keyword.vmwaresolutions_short}}에 입력된 인스턴스 이름에는 특수 문자(예: 대시 문자)를 포함할 수 없습니다. 영숫자 문자만 사용할 수 있습니다. 이 제한사항은 Cloud Foundation 인스턴스에 적용되지 않습니다.

자세한 정보는 다음을 참조하십시오.
* [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)
* [NetApp ONTAP Select 인스턴스 주문](../netapp/np_orderinginstances.html)

## VMware Cloud Foundation 인스턴스에 대한 업데이트

### 인스턴스 CPU 및 메모리 사용자 정의

사용자 정의 서버 옵션은 사전 빌드되고 테스트된 소형 및 표준 옵션과 함께 사용할 수 있습니다. 워크로드의 CPU 대 RAM 비율을 VMware 호환 가능 하드웨어와 좀 더 많이 일치하도록 이제 듀얼 CPU 서버의 총 코어 수와 RAM의 양을 별도로 선택할 수 있습니다. 로컬 스토리지는 사용자 정의할 수 없습니다.

자세한 정보는 [Cloud Foundation 인스턴스 주문](../sddc/sd_orderinginstance.html)을 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트

### 교차 데이터 센터 클러스터 지원

호스팅된 VMware 환경의 용량 확장을 개선하기 위해, 이제는 인스턴스에 배치된 초기 클러스터가 아닌 다른 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 팟(Pod) 또는 다른 {{site.data.keyword.CloudDataCent_notm}}에서 새 클러스터를 작성할 수 있습니다. 

자세한 정보는 [vCenter Server 인스턴스에 대한 클러스터 추가 및 보기](../vcenter/vc_addingviewingclusters.html)를 참조하십시오.

### 컴포넌트 변경

이 릴리스는 Single Sign-On 관리자가 원시 VMware 도구에서 특정 vCenter Server 리소스를 변경할 때 {{site.data.keyword.vmwaresolutions_short}} 콘솔 내 오퍼레이션에 대한 영향을 제거할 수 있습니다. 예를 들어, VMware vSphere Web Client에서 VMware 가상 데이터 센터, 클러스터, 스위치, 포트 그룹 및 데이터 저장소 이름을 수정하여 회사 또는 개인 이름 지정 규칙에 대한 배치를 사용자 정의할 수 있고 다운스트림 없이 {{site.data.keyword.vmwaresolutions_short}} 콘솔 내에서 오퍼레이션에 영향을 줄 수 있습니다.

자세한 정보는 [vCenter Server 인스턴스에 대한 컴포넌트 변경의 영향](../vcenter/vcenter_chg_impact.html)을 참조하십시오.

### 추가 RAM 크기

vCenter Server 인스턴스를 주문하거나 vCenter Server 인스턴스에 대한 클러스터를 추가하는 경우 이제 워크로드의 CPU 대 RAM 비율을 하드웨어와 일치시키기 위해 선택할 수 있는 추가 RAM 크기가 있습니다. 다음 옵션은 {{site.data.keyword.vmwaresolutions_short}} 콘솔: 64GB, 128GB, 256GB, 384GB, 512GB, 768GB, 1.5TB에서 서버를 주문할 때 **사용자 정의된 사용자** 구성 옵션에서 사용할 수 있습니다.

자세한 정보는 [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)을 참조하십시오.

### Network File System 버전 업데이트

Network File System(NFS) 버전 4.1은 사용자 인터페이스의 스토리지 설정으로 더 이상 사용할 수 없습니다. 모든 vCenter Server 인스턴스는 NFS V3으로 배치됩니다. NFS V3가 이전 프로토콜 버전이지만, VMware SDRS(Storage Distributed Resource Scheduler) 및 SIOC(Storage I/O Control)에 대한 지원으로 VMware 환경의 향상된 기능을 사용으로 설정합니다.

자세한 정보는 [vCenter Server 인스턴스 주문](../vcenter/vc_orderinginstance.html)을 참조하십시오.

### 단일 사이트 Domain Name Server 도메인 이름

이제 주문 중에 vCenter Server 인스턴스에 대한 DNS(Domain Name Server) 도메인 이름을 제공할 수 있습니다. 호스트 및 가상 머신이 등록된 인스턴스용 DNS로 작동하는 Microsoft Windows Server Virtual Server Instance(VSI)가 배치되고 검색될 수 있습니다. 또한 Microsoft Active Directory(AD)는 Microsoft Windows VSI에 설정되고 DNS 도메인 이름은 AD 도메인 포리스트 루트입니다. 이 Microsoft Windows VSI는 V1.9 이상에서만 사용할 수 있습니다.

자세한 정보는 다음을 참조하십시오.
* [vCenter Server 개요](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server 인스턴스 보기](../vcenter/vc_viewinginstances.html)

## Windows Server 자동 업데이트 설치에 대한 요구사항

Microsoft Active Directory(AD)/DNS(Domain Name Server)는 업데이트만 다운로드하도록 자동으로 설정됩니다. 이 업데이트를 자동으로 설치하고 다시 부팅하지 않습니다. 지속적인 Active Directory 서버 구성 및 기타 백업 작업의 중단이 발생하지 않도록 스케줄된 시간에 업데이트를 수동으로 설치하고 다시 부팅해야 합니다. Windows 업데이트를 적용하려면 업데이트를 수동으로 설치하십시오.

## 새로 작성되고 업데이트된 문서

* 공용 {{site.data.keyword.cloud_notm}} 서비스를 사용하기 위해 VMware 애플리케이션을 확장하는 동안 사설 다중 사이트 VCF 인스턴스를 보호하는 방법을 알아보십시오. 자세한 정보는 [{{site.data.keyword.cloud_notm}}에서 사설 VMware 워크로드의 보안 연결](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}을 참조하십시오. 
* 추가 문서는 IBM CloudDriver 및 SDDC Manager 가상 머신에서 모든 프로토콜 통신을 허용하는 방화벽을 구성하기 위해 제공됩니다. 자세한 정보는 [Fortinet on {{site.data.keyword.cloud_notm}}에 대한 컴포넌트 및 고려사항](../services/fsa_considerations.html)을 참조하십시오. 

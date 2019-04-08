---

copyright:

  years:  2016, 2018

lastupdated: "2018-08-30"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.5의 릴리스 정보
{: #relnotes_v25}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 스펙터(Spectre) 및 멜트다운(Meltdown) 조치 방안
{: #relnotes_v25-spectre}

{{site.data.keyword.vmwaresolutions_short}}가 스펙터(Spectre) 및 멜트다운(Meltdown)(CVE-2017-5753, CVE-2017-5715 및 CVE-2017-5754)으로 알려진 취약점에 대한 응답으로 VMware에서 패치를 릴리스했습니다.

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## NSX 컴포넌트 업데이트
{: #relnotes_v25-nsx}

이 릴리스에서는 VMware vCenter Server on {{site.data.keyword.cloud_notm}}, VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 및 NetApp ONTAP Select의 새 배치를 위한 VMware NSX for vSphere 6.4.1을 설치합니다.

## 기본 백업 구성의 제거
{: #relnotes_v25-default-backup}

{{site.data.keyword.vmwaresolutions_short}}에서는 백업을 위한 2개의 통합 추가 기능 서비스(IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 및 Veeam on {{site.data.keyword.cloud_notm}})를 제공합니다. 이러한 서비스를 사용하면 관리 인프라 및 워크로드 모두의 복구를 계획하고 제공할 수 있습니다. 또한 IBM Resiliency Services는 Veeam 백업을 위한 관리 서비스도 제공합니다.

V2.5 릴리스 이상에서 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 및 Veeam on {{site.data.keyword.cloud_notm}} 서비스는 배치 시에 더 이상 VM의 백업을 사전 구성하지 않습니다. 이러한 변경에 따라 스케줄, 보존 기간, 중복 제거 사용, 모니터링 및 경보, 그리고 암호화 키 관리를 포함하여 백업 작업의 모든 측면에 대해 일맞은 구성을 보장할 수 있습니다. 또한 IBM CloudDriver VM은 더 이상 NSX 백업을 위한 지속적 파일 서버로서 구성되지 않습니다.

사용자는 관리 인프라 및 워크로드의 백업과 가용성을 포함하여 모든 소프트웨어 컴포넌트의 구성, 관리 및 모니터링에 책임이 있습니다. 자세한 정보는 [컴포넌트 백업](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup#backing-up-components)을 참조하십시오.

이 변경사항은 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 또는 Veeam on {{site.data.keyword.cloud_notm}} 서비스가 설치된 V2.5 전에 배치된 인스턴스에는 적용되지 않습니다.
{:note}

## IBM CloudDriver 복원성
{: #relnotes_v25-cloud-driver}

V2.5 이상 릴리스에 배치되거나 이로 업그레이드된 인스턴스의 경우, IBM CloudDriver 컴포넌트는 더 이상 vSphere 클러스터 내에서 가상 머신(VM)으로서 구성되지 않습니다. 대신 이는 추가 노드, 클러스터 또는 서비스 배치 등의 오퍼레이션을 위한 최신 {{site.data.keyword.cloud_notm}} for VMware 코드로 필요에 따라 {{site.data.keyword.cloud_notm}} 인프라 VSI(Virtual Server Instance)로서 배치됩니다. 또한 IBM CloudDriver는 {{site.data.keyword.cloud_notm}} 사설 네트워크를 사용하여 {{site.data.keyword.cloud_notm}} 관리 플레인과 통신하도록 변경됩니다. 이 변경에 따라 IBM CloudDriver의 공용 네트워크에 대한 아웃바운드 통신을 허용하는 관리 NSX Edge Services Gateway(ESG) 방화벽 및 네트워크 주소 변환(NAT) 규칙이 제거됩니다.

F5 on {{site.data.keyword.cloud_notm}}, FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 및 Zerto on {{site.data.keyword.cloud_notm}} 등의 일부 추가 기능 서비스가 여전히 공용 네트워크 액세스를 필요로 하므로, 관리 NSX ESG는 모든 인스턴스에 계속 배치되어 있습니다.

## IAM-사용 사용자 및 액세스 관리
{: #relnotes_v25-iam}

V2.5 릴리스 이상에서 {{site.data.keyword.vmwaresolutions_short}}는 {{site.data.keyword.cloud_notm}} 계정 내에서 사용자 계정과 사용자 액세스를 관리하기 위한 통합 접근 방법을 제공하기 위해 IBM IAM(Identity and Access Management)과 통합되어 있습니다. 이로 인해,
* 이제 협업을 위해 {{site.data.keyword.cloud_notm}} 계정에 복수의 사용자를 추가할 수 있으며, 이러한 사용자에게 서로 다른 플랫폼 액세스 역할을 지정하여 계정에서 프로비저닝되는 서비스와 리소스에 대한 해당 액세스를 관리할 수 있습니다.  
* V2.5 이상 릴리스에 배치된 인스턴스는 인스턴스 주문 시에 사용 중인 사용자 계정에 자동으로 링크됩니다.
* V2.4 이하 릴리스에 배치된 인스턴스의 경우, 이를 지정된 {{site.data.keyword.cloud_notm}} 계정으로 마이그레이션한 후에 역시 IAM을 사용하여 이를 관리할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [서비스 및 리소스에 액세스하기 위한 사용자 초대](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [IAM에서 사용자 액세스 관리](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam)

## VMware vCenter Server 및 VMware Cloud Foundation 인스턴스의 사용자 계정 및 그룹에 대한 변경사항
{: #relnotes_v25-user-acct}

**ic4v-vCenter** 사용자 그룹이 Microsoft Active Directory 서버에서 작성되었으며 NSX Manager의 사용자 그룹 및 vCenter Server의 글로벌 권한에 추가되었습니다. 이 그룹에는 vCenter Server 인스턴스의 **자동화** 사용자 계정과 vCenter Server 및 Cloud Foundation 인스턴스의 서비스 특정 사용자 계정이 포함되어 있습니다.

VMware vSphere Web Client의 **사용자 및 그룹** 페이지에서 **ic4v-vCenter** 그룹의 글로벌 권한을 편집하지 마십시오. 그러면 관리 오퍼레이션에 영향을 줄 수 있습니다.

Cloud Foundation 인스턴스의 경우에는 **root** 호스트 사용자 ID 대신에 **customerroot** 호스트 사용자 ID를 사용하십시오.

vCenter Server 인스턴스에 대해서는 계속해서 **root** 호스트 사용자 ID를 사용하십시오. **ic4vroot** 호스트 사용자 ID는 IBM 전용으로 작성되었습니다.

사용자 계정에 대한 자세한 정보는 [vCenter Server 아티팩트 변경에 대한 고려사항](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vcenter_chg_impact)을 참조하십시오.

## 추가 서비스에 대한 업데이트
{: #relnotes_v25-services}

### IBM Cloud Private Hosted(2018년 8월 30일에 업데이트됨)
{: #relnotes_v25-scp-hosted}

이제 {{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} 서비스는 V2.5 이상 릴리스에 배치된(또는 업그레이드된) vCenter Server 인스턴스에서 사용할 수 있습니다.

{{site.data.keyword.cloud_notm}} Private Hosted는 마이크로서비스 및 컨테이너의 기능을 {{site.data.keyword.cloud_notm}}의 VMware 환경에 제공합니다. 이 서비스를 사용하면 익숙한 동일 VMware 및 {{site.data.keyword.cloud_notm}} Private 운영 모델과 도구를 온프레미스에서 {{site.data.keyword.cloud_notm}}로 확장할 수 있습니다.

vCenter Server 인스턴스를 주문한 후 이 서비스를 요청할 수 있습니다.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v25-spp}

V2.5 릴리스부터는 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스가 우수 사례를 기반으로 2개의 개별 VM으로서 배치됩니다. 하나의 VM은 IBM Spectrum Protect Plus 서버를 실행하며 다른 하나의 VM은 vSnap 서버와 VADP 프록시를 실행합니다.

이제 최대 10개의 백업 데이터 저장소를 주문할 수 있으며, 최대 120TB의 백업 스토리지를 허용할 수 있습니다. vSnap 및 VADP VM은 [IBM Spectrum Protect Plus 블루프린트](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)의 정보에 따라, 그리고 선택된 백업 스토리지 크기에 의존하여 크기가 지정됩니다.

### KMIP for VMware on IBM Cloud
{: #relnotes_v25-kmip}

KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스에 대해 이제 새 엔드포인트가 독일어로 사용 가능합니다.

## 새로 작성되고 업데이트된 문서
{: #relnotes_v25-new-docs}

### 연결된 스토리지 문서
{: #relnotes_v25-docs-storage}

vCenter Server on IBM Cloud의 연결 스토리지 기술 문서를 이제 사용자 문서의 *참조* 섹션에서 사용할 수 있습니다. 자세한 정보는 [vCenter Server on IBM Cloud의 연결 스토리지](/docs/services/vmwaresolutions/archiref/attached-storage?topic=vmware-solutions-storage-benefits)를 참조하십시오.

### 기술 스펙
{: #relnotes_v25-docs-tech-specs}

모든 인스턴스 유형과 서비스 유형에 대한 기술 스펙이 이제 사용자 문서에서 사용 가능하며 사용자 인터페이스에서 링크되어 있습니다. 자세한 정보는 인스턴스 및 서비스의 해당되는 개요 주제를 참조하십시오.

### 서비스 문서
{: #relnotes_v25-docs-services}

사용 가능하던 릴리스 번호를 기반으로 서비스 지원을 손쉽게 식별할 수 있도록 서비스 정보가 개선되었습니다.

자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server 인스턴스에 사용 가능한 서비스](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices#available-services-for-vcenter-server-instances)
* [vCenter Server with Hybridity Bundle 인스턴스에 사용 가능한 서비스](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices#available-services-for-vcenter-server-with-hybridity-bundle-instances)

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v25-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* {{site.data.keyword.cloud_notm}} 계정에 링크된 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정이 있는 경우에는 이제 **설정** 페이지에서 새로 추가된 **검색** 단추를 클릭하여 {{site.data.keyword.cloud_notm}} 인프라(SoftLayer) 계정에 대한 사용자 이름과 API 키를 자동으로 가져올 수 있습니다.
* 사용자가 인스턴스의 배치 히스토리를 확인할 수 있도록 새 **배치 히스토리** 탭이 인스턴스 세부사항 페이지의 왼쪽 탐색 분할창에서 추가되었습니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

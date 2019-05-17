---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# V3.0 릴리스 정보
{: #relnotes_v30}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## VMware Cloud Foundation on IBM Cloud의 지원 종료
{: #relnotes_v30-vcf-eos}

보다 나은 고객 경험을 제공하도록 오퍼링을 통합하기 위해 {{site.data.keyword.vmwaresolutions_short}} 플랫폼에서는 2019년 5월 13일부터 더 이상 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}를 제공하지 않습니다. 

앞으로 모든 고객은 IBM에서 주력하는 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}의 VMware 소프트웨어 정의 데이터 센터 솔루션인 VMware vCenter Server on {{site.data.keyword.cloud_notm}}로 이동합니다. 

VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}를 사용하는 기존 고객은 지원 종료 날짜인 2019년 5월 13일까지 VMware vCenter Server on {{site.data.keyword.cloud_notm}}로의 변환을 지원받게 됩니다.

5월 13일 이후에는 VMware vCenter Server on {{site.data.keyword.cloud_notm}}로 변환될 때까지 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서의 VMware Cloud Foundation on {{site.data.keyword.cloud_notm}}에 대한 관리 기능이 고정(freezing)됩니다. VMware Cloud Foundation on {{site.data.keyword.cloud_notm}} 인스턴스가 VMware vCenter Server on {{site.data.keyword.cloud_notm}}로 마이그레이션되거나 변환되도록 선택하지 않은 고객은 {{site.data.keyword.cloud_notm}} 인프라 콘솔에서 인스턴스에 액세스할 수 있습니다. 

## Broadwell 2-CPU 서버에 대한 지원이 제거됨
{: #relnotes_v30-broadwell}

V3.0 릴리스부터 Broadwell 2-CPU 서버는 더 이상 vCenter Server, vCenter Server with Hybridity Bundle, vCenter Server 및 vSphere on {{site.data.keyword.cloud_notm}} 인스턴스 및 클러스터의 새 배치에 사용할 수 없습니다. 계속해서 서버를 기존 클러스터에 추가할 수 있습니다. 

## 네트워크 파일 시스템 오퍼레이션 개선사항
{: #relnotes_v30-nfs}

V3.0 릴리스부터 여러 클러스터에서 네트워크 파일 시스템(NFS) 스토리지를 동시에 추가하거나 제거할 수 있습니다. 이는 모든 vCenter Server 및 vCenter Server with NSX-T에 적용됩니다. 

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v30-vcs}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.7 Update 1(빌드 6.7.0-13004448)
* vSphere ESXi 6.5 Update 2(빌드 6.5.0-13004031)
* vCenter Server Appliance 6.7 Update 1b(빌드 6.7.0-11727113)
* Platform Services Controller 6.7 Update 1b(빌드 6.7.0-11727113) 

자세한 정보는 [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)를 참조하십시오.

Microsoft Active Directory(AD) 및 DNS(Domain Name System) 서비스에 대해 주문된 Windows 소프트웨어는 VM의 구성 옵션 즉, VSI(Virtual Server Instances) 및 두 개의 고가용성 Windows VM을 위해 Windows Server 2016으로 업그레이드됩니다. VMware 컴포넌트 선택에 대한 자세한 정보는 [vCenter Server 인스턴스에 대한 소프트웨어 BOM](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_bom#vc_bom-software)을 참조하십시오.

### vSAN 스토리지 개선사항
{: #relnotes_v30-vcs-vsan}

* vSAN 스토리지를 사용할 때 주문할 수 있는 Bare Metal Server의 수는 5개 이상일 수 있습니다. 이는 모든 vCenter Server, vCenter Server with Hybridity 및 vCenter Server with NSX-T 인스턴스에 적용됩니다. 
* V3.0 릴리스부터 M.2 SSD(Solid-State Drive)는 vSAN 스토리지 인스턴스와 함께 주문됩니다. **Intel Optaine을 사용한 고성능** 옵션을 선택하는 경우 최대 10개의 용량 디스크 또는 총 12개의 용량 디스크를 주문할 수 있습니다. 

자세한 정보는 다음의 *스토리지 설정* 섹션을 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_orderinginstance#vc_orderinginstance-storage-settings)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_hybrid_orderinginstance#vc_hybrid_orderinginstance-storage-settings)
* [VMware vCenter Server with NSX-T 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_orderinginstance#vc_nsx-t_orderinginstance-storage-settings)

## 추가 서비스에 대한 업데이트
{: #relnotes_v30-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v30-services-htcc}

현재 릴리스에서는 새로 배치된 모든 인스턴스에 HyTrust CloudControl 5.5가 설치되어 있습니다. HyTrust CloudControl 5.5의 새 기능에 대한 자세한 정보는 [HyTrust CloudControl 버전 5.5의 새로운 기능](https://docs.hytrust.com/CloudControl/5.5.0/Online/Content/HTCC_Admin_Guide/_FrontMatter/Whats-New.html){:new_window}을 참조하십시오.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v30-services-htdc}

현재 릴리스는 새로 배치된 모든 인스턴스에 HyTrust DataControl 4.3을 설치합니다. HyTrust DataControl 4.3의 새 기능에 대한 자세한 정보는 [KeyControl 및 DataControl 버전 4.3의 새로운 기능](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}을 참조하십시오.

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v30-services-htkc}

현재 릴리스는 새로 배치된 모든 인스턴스에 HyTrust KeyControl 4.3을 설치합니다. HyTrust KeyControl 4.3의 새 기능에 대한 자세한 정보는 [KeyControl 및 DataControl 버전 4.3의 새로운 기능](https://docs.hytrust.com/DataControl/4.3/Online/Content/Books/aaCommon/New-Changed-4x.html){:new_window}을 참조하십시오.

### IBM Cloud Private Hosted
{: #relnotes_v30-services-icp}

현재 릴리스는 새로 배치된 인스턴스에 {{site.data.keyword.cloud_notm}} Private Hosted 3.1.2와 {{site.data.keyword.cloud_notm}} Automation Manager 3.1.2를 함께 설치합니다. 

{{site.data.keyword.cloud_notm}} Private v3.1.2의 새 기능에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} Private v3.1.2의 새로운 기능](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.1.2/getting_started/whats_new.html){:new_window}을 참조하십시오.
{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2의 새 기능에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} Automation Manager 3.1.2의 새로운 기능](https://www.ibm.com/support/knowledgecenter/en/SS2L37_3.1.2.0/cam_whatisnew.html){:new_window}을 참조하십시오.

### KMIP for VMware on IBM Cloud
{: #relnotes_v30-services-kmip}

이제 VMware on {{site.data.keyword.cloud_notm}} 서비스에 대해 KMIP용으로 런던 및 미국 동부에서 두 개의 새 엔드포인트를 사용할 수 있습니다. 자세한 정보는 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스 구성](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_ordering-config#kmip_standalone_ordering-config)을 참조하십시오.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v30-services-spp}

현재 릴리스는 새로 배치된 모든 인스턴스에 IBM Spectrum Protect™ Plus V10.1.3을 설치합니다. IBM Spectrum Protect Plus V10.1.3의 새 기능에 대한 자세한 정보는 [IBM Spectrum Protect Plus 업데이트](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.3/spp/r_techchg_spp.html){:new_window}를 참조하십시오.

### Zerto on IBM Cloud
{: #relnotes_v30-services-zerto}

이제 사설 전용인 인스턴스에서 Zerto on {{site.data.keyword.cloud_notm}}를 추가할 수 있습니다. 사설 전용 인스턴스에서 Zerto를 설치하도록 선택하는 경우 고유한 프록시 서버를 설정하고 Zerto용 콜홈 기능도 구성해야 합니다. 자세한 정보는 [사설 네트워크 전용인 인스턴스에 대한 Zerto on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-zerto_ordering#zerto_ordering-private-only)을 참조하십시오.

## 새로 작성되고 업데이트된 문서

* 이제 {{site.data.keyword.vmwaresolutions_short}} 컴포넌트를 VMware vSphere 6.7로 업그레이드하는 데 도움이 되는 문서를 사용할 수 있습니다. 계속해서 {{site.data.keyword.vmwaresolutions_short}} 자동화 혜택을 받으려면 이 업그레이드는 필수입니다. 자세한 정보는 [vCenter Server vSphere 소프트웨어를 VMware vSphere 6.5에서 6.7로 업그레이드](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_vsphere_upgrade#vc_vsphere_upgrade)를 참조하십시오.
* {{site.data.keyword.cloud_notm}} 자동화에 사용되도록 {{site.data.keyword.vmwaresolutions_short}}가 관리하는 사용자 ID를 사용자에게 제공하는 데 참조 문서를 사용할 수 있습니다. 인스턴스 히스토리 로그에 표시되는 메시지는 검토용으로도 사용할 수 있습니다. 자세한 정보는 [IBM 사용자 ID 및 vCenter Server 인스턴스의 배치 히스토리 메시지](/docs/services/vmwaresolutions?topic=vmware-solutions-ibm_use#ibm_use)를 참조하십시오.
* **Reboot/Control** 권한이 IBM Cloud 인프라 계정에 필요한 권한을 설명하는 표에 추가되었습니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 인프라 계정에 대한 권한](/docs/services/vmwaresolutions/services?topic=vmware-solutions-slaccountrequirement#slaccountrequirement-permissions)을 참조하십시오.
* 다음 API에 대한 새 참조 문서를 사용할 수 있습니다. 자세한 정보는 [API 참조](https://cloud.ibm.com/apidocs/vmware-solutions){:new_window}를 참조하십시오.
  * 지정된 VMware vCenter Server 인스턴스에 대한 모든 히스토리 메시지 나열
  * 공유 스토리지를 지정된 클러스터에 추가
  * 지정된 클러스터에서 NFS 스토리지 삭제

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v30-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-19"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.2 릴리스 정보
{: #relnotes_v22}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 스펙터(Spectre) 및 멜트다운(Meltdown) 조치 방안
{: #relnotes_v22-spectre}

{{site.data.keyword.vmwaresolutions_short}}가 스펙터(Spectre) 및 멜트다운(Meltdown)(CVE-2017-5753, CVE-2017-5715 및 CVE-2017-5754)으로 알려진 취약점에 대한 응답으로 VMware에서 패치를 릴리스했습니다.

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## IBM CloudDriver 가상 머신 업그레이드
{: #relnotes_v22-cloud-driver}

V2.2 업그레이드 프로세스 중에 IBM CloudDriver 가상 머신이 CentOS Linux 릴리스 7.4.1708로 다시 배치됩니다. 또한 새로 프로비저닝된 모든 인스턴스에는 IBM CloudDriver의 CentOS Linux 릴리스 7.4.1708이 포함됩니다.

**중요:**

* IBM CloudDriver 가상 머신을 참조하는 백업 솔루션을 사용 중인 경우 V2.2로 업그레이드한 후 백업 솔루션이 새 IBM CloudDriver 가상 머신을 참조하고 있는지 확인하십시오.
* V2.2로 업그레이드하기 전에 Legacy Veeam VSI를 Veeam on {{site.data.keyword.cloud_notm}} 서비스로 대체하는지 확인하십시오. Legacy Veeam은 더 이상 V2.2 및 이후 릴리스에서 지원되지 않으며 이에 따라 Legacy Veeam과 연관된 관리 컴포넌트 백업을 복원에 사용할 수 없습니다.

Veeam on {{site.data.keyword.cloud_notm}} 서비스 사용에 대한 자세한 정보는 다음 주제를 참조하십시오.
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 컴포넌트 및 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Veeam on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## ESXi 서버의 고급 구성 설정
{: #relnotes_v22-config-esxi}

V2.2 이상 릴리스에서 새 인스턴스는 ESXi 서버에 대한 새 고급 구성 설정 세트와 함께 주문됩니다.
이전 릴리스에서 V2.2 이상 릴리스로 업그레이드되는 인스턴스의 경우 일부 설정은 ESXi 서버를 다시 부팅해야 합니다. 따라서 구성 설정의 서브세트만 자동으로 적용됩니다.

모든 인스턴스의 일관성과 스토리지 확장에 필요한 충분한 지원을 허용하기 위해 남아 있는 구성 설정을 새 값으로 변경하는 것이 좋습니다. IBM은 모든 {{site.data.keyword.cloud_notm}} for VMware Solutions 이후 릴리스의 새 설정에 대해서만 테스트하도록 계획하고 있습니다.

자세한 정보는 [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#advanced-configuration-settings-for-esxi-servers)의 _ESXi 서버의 고급 구성 설정_을 참조하십시오.

## 초기 클러스터에 최대 51개의 ESXi 서버를 지원하고 추가 클러스터에 최대 59개의 ESXi 서버를 지원함
{: #relnotes_v22-esxi-cluster}

V2.2 이상 릴리스의 경우, 초기 클러스터에 ESXi 서버 수를 최대 51개까지 늘리고 추가 클러스터에 ESXi 서버 수를 최대 59개까지 늘릴 수 있습니다.

V2.1 이전 릴리스에 배치된 인스턴스의 경우, 필요한 vSAN 지원을 사용으로 설정하여 32개가 초과하도록 클러스터 크기를 늘려야 합니다. ESXi 서버 수를 늘리는 단계에 대한 자세한 정보는 [ESXi 서버에 대한 FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq_esxi#how-many-esxi-servers-can-i-add-to-a-cluster-)의 _몇 개의 ESXi 서버를 클러스터에 추가할 수 있습니까?_를 참조하십시오.
{:important}

## vCenter Server 및 Cloud Foundation 인스턴스에 대한 추가 네트워크 구성 옵션
{: #relnotes_v22-network-config}

vCenter Server 및 Cloud Foundation 인스턴스 주문의 경우, 이제 네트워크 구성을 위해 기존의 공용 및 사설 VLAN을 다시 사용할 수 있습니다. 기존 VLAN을 사용할 수 없는 경우에는 하나의 공용 VLAN 및 두 개의 사설 VLAN을 새로 주문할 수 있습니다.

기존 VLAN을 선택하기 전의 중요한 고려사항은 [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)의 *네트워크 인터페이스 설정* 섹션을 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v22-vcs}

### NSX 컴포넌트 및 포트 그룹 구성 설정 업데이트
{: #relnotes_v22-nsx}

현재 릴리스에서는 VMware NSX for vSphere 6.3.5 컴포넌트 업데이트가 적용되었습니다. 컴포넌트에 대한 자세한 정보는 [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)를 참조하십시오.

V2.2 이상 릴리스에 배치된 VMware vCenter Server 인스턴스의 경우, NSX 및 포트 그룹 구성 설정이 변경되었습니다. 자세한 정보는 [vCenter Server 소프트웨어 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom#nsx-and-port-group-configuration-settings)의 *NSX 및 포트 그룹 구성 설정* 섹션을 참조하십시오.

### DNS 구성에 대한 새 옵션
{: #relnotes_v22-dns}

이제 Microsoft Active Directory(AD)용 하나의 Microsoft Windows Server Virtual Server Instance(VSI) 또는 관리 클러스터에 있는 두 개의 고가용성 Microsoft Windows 가상 머신의 배치를 선택할 수 있습니다. V2.2 이전 릴리스의 경우, 기본적으로 Microsoft AD용 Microsoft Windows VSI 하나가 자동으로 배치되었습니다. 두 개의 Microsoft Windows 가상 머신을 선택하는 새 옵션은 더 많은 개인정보 보호를 제공하고 Veeam 서비스를 사용하여 가상 머신을 백업하고 복원하는 옵션을 제공합니다.

두 개의 Microsoft Windows 가상 머신을 사용하도록 인스턴스를 구성하는 경우 두 개의 Windows Server 2012 R2 라이센스를 제공해야 합니다. Microsoft Windows Server 2012 R2 Standard 에디션 라이센스 및/또는 Microsoft Windows Server 2012 R2 Datacenter 에디션 라이센스를 사용하십시오. 가상 머신을 활성화할 수 있는 30일의 기간이 제공됩니다.
{:note}

자세한 정보는 [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#system-settings)의 *시스템 설정* 절을 참조하십시오.

### 인스턴스당 늘어난 클러스터 수
{: #relnotes_v22-clusters-per-inst}

이제 V2.2 이상 릴리스에 배치되거나 V2.2 이상 릴리스로 업그레이드된 VMware vCenter Server 인스턴스에 최대 10개의 클러스터를 추가할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 대한 클러스터 추가 및 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)​를 참조하십시오.

## VMware vSphere 클러스터에 대한 업데이트
{: #relnotes_v22-vss}

### 비즈니스 파트너 고객이 사용할 수 있는 컴포넌트 라이센스 번들
{: #relnotes_v22-license-bundles}

이제 비즈니스 파트너 사용자는 새 vSphere 클러스터를 주문할 때 네 개의 컴포넌트 라이센스 번들에서 선택할 수 있습니다. 관리가 포함된 표준, 고급, 네트워킹이 포함된 고급 또는 네트워킹 및 관리가 포함된 고급 중에서 선택하십시오. 또한 주문에 추가 VMware 컴포넌트를 포함할 수 있습니다. 그러나 고유한 라이센스 가져오기 옵션은 사용할 수 없습니다.

자세한 정보는 [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)의 *라이센싱 설정*을 참조하십시오.

## NetApp ONTAP Select 인스턴스에 대한 업데이트
{: #relnotes_v22-netapp}

현재 릴리스에서는 NetApp ONTAP Select 9.3의 업데이트가 적용되었습니다.

### 고용량 IBM Cloud Bare Metal Servers에 대해 늘어난 SATA 드라이브 수
{: #relnotes_v22-sata-drives}

이제 34개의 SATA 드라이브는 NetApp ONTAP Select 고용량 {{site.data.keyword.baremetal_short}}에 사용할 수 있습니다. 자세한 정보는 [NetApp ONTAP Select 인스턴스의 기술 스펙](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview#specs)을 참조하십시오.

## 추가 서비스에 대한 업데이트
{: #relnotes_v22-services}

### F5 on IBM Cloud에 대해 늘어난 대역폭
{: #relnotes_v22-bandwidth}

이제 Cloud Foundation 및 vCenter Server 인스턴스를 위한 F5 on {{site.data.keyword.cloud_notm}} 서비스를 설치할 때 최대 10Gbps의 대역폭을 선택할 수 있습니다. 자세한 정보는 [F5 on {{site.data.keyword.cloud_notm}}에 대한 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)을 참조하십시오.

### KMIP for VMware on IBM Cloud
{: #relnotes_v22-kmip}

이제 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스가 포함된 Cloud Foundation 또는 vCenter Server 인스턴스를 주문하거나 초기 배치 후 서비스를 기존 Cloud Foundation 또는 vCenter Server 인스턴스에 추가할 수 있습니다.

이 서비스는 {{site.data.keyword.cloud_notm}}의 VMware에서 사용되는 암호화 키를 관리하기 위해 고가용성 서비스를 연중무휴로 제공합니다. 이 서비스는 고객이 암호화 키를 작성, 검색, 활성화, 취소 및 영구 삭제할 수 있는 런타임 기능을 제공합니다. 또한 이 서비스는 클라이언트 인증 정보와 암호화 키 간의 연관을 유지보수하는 관리 기능도 제공합니다.

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v22-spp}

이제 IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스는 V2.2 이상 릴리스에 배치된(또는 업그레이드된) 인스턴스에 사용할 수 있습니다.

이 서비스는 가상 환경에서의 데이터 보호, 데이터 재사용 및 데이터 복구를 위한 효율적이고 스케일링 가능한 솔루션을 제공합니다. 사용자는 장기 저장 및 데이터 통제를 위해 사본을 오프로드하기 위하여 이를 독립형 솔루션으로 구현하거나 자신의 IBM Spectrum Protect&trade; Plus 환경과 통합할 수 있습니다.

IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 서비스는 워크로드 VM 전용의 데이터 보호를 제공합니다.

자세한 정보는 [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)를 참조하십시오.

### 관리 서비스
{: #relnotes_v22-managed-services}

이제 Veeam on {{site.data.keyword.cloud_notm}}에 대한 관리 서비스와 Zerto on {{site.data.keyword.cloud_notm}}는 VMware vCenter Server 및 VMware Cloud Foundation 인스턴스에 사용할 수 있습니다. 자체 솔루션 및 환경의 복잡성을 관리하지 않으려는 경우 이러한 관리 서비스를 요청하십시오.

Veeam on {{site.data.keyword.cloud_notm}} 서비스는 엔터프라이즈가 고가용성(HA)을 달성할 수 있도록 VMware 하이퍼바이저와 원활하게 통합합니다. Veeam 백업 소프트웨어 및 IBM Resiliency Backup as a Service를 모두 사용하여 완전히 관리된 백업 환경을 배치할 수 있습니다.

Zerto on {{site.data.keyword.cloud_notm}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware virtual 환경에서 데이터를 보호하고 복구하도록 배치 오퍼링으로 통합될 수 있는 복제 및 재해 복구 기능을 제공합니다. Zerto DR 소프트웨어 및 IBM Resiliency Services를 모두 사용하여 완전히 관리된 재해 복구(DR) 환경을 배치할 수 있습니다.

새 인스턴스를 주문하거나 서비스를 기존 인스턴스에 추가하여 **시작하기** 페이지에서 인스턴스를 위한 관리 서비스를 요청할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [Veeam on {{site.data.keyword.cloud_notm}}에 대한 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Zerto on {{site.data.keyword.cloud_notm}}에 대한 서비스 요청](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_zerto_services)

## 새로 작성되고 업데이트된 문서
{: #relnotes_v22-new-docs}

* 이제 문서에서 VMware vSphere 클러스터를 비롯한 Cloud Foundation 및 vCenter Server 인스턴스에 지원되는 기능이 포함된 비교 표를 볼 수 있습니다. 각 인스턴스 유형이 제공하는 기능 간의 차이점을 한 눈에 볼 수 있습니다. 자세한 정보는 [오퍼링 비교 차트](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-inst_comp_chart)를 참조하십시오.

* 이제 VLAN 및 소프트웨어 명세서(BOM)가 Cloud Foundation, vCenter Server 및 VMware vSphere 클러스터에 대한 문서에 제공됩니다.

  자세한 정보는 다음 주제를 참조하십시오.

  * [vCenter Server 명세서](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
  * [VMware vSphere 명세서](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_bom)

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v22-ui}

개선사항은 사용자 인터페이스를 통해 수행됩니다.

* 이제 인스턴스를 주문할 때 모든 하드웨어 옵션이 위치별로 필터링되고 사용할 수 없는 옵션이 사용 안함 상태로 표시됩니다.
* 이제 기존 구성을 기반으로 vSphere 클러스터를 주문할 때 **{{site.data.keyword.baremetal_short}}** 구성이 자동으로 채워집니다. 사용자의 요구사항에 따라 구성을 업데이트할 수 있습니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

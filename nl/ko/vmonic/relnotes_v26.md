---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-01"

subcollection: vmware-solutions


---

# V2.6의 릴리스 정보
{: #relnotes_v26}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함되어 있습니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 스펙터(Spectre) 및 멜트다운(Meltdown) 조치 방안
{: #relnotes_v26-spectre}

{{site.data.keyword.vmwaresolutions_short}}가 스펙터(Spectre) 및 멜트다운(Meltdown)(CVE-2017-5753, CVE-2017-5715 및 CVE-2017-5754)과 관련된 취약점에 대한 응답으로 VMware에서 패치를 릴리스했습니다.

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## Intel Optane 옵션을 사용하는 고성능
{: #relnotes_v26-optane}

이 릴리스는 새 인스턴스를 주문할 때 또는 초기 배치 후 새 vSAN 클러스터를 추가할 때 vSAN 스토리지에 대한 고성능 캐시를 추가하는 옵션을 제공합니다.

이 옵션을 통해 스토리지 용량 디스크를 8개에서 최대 10개까지 늘릴 수 있습니다.

Intel Optane 옵션을 사용한 고성능 옵션은 듀얼 Intel Xeon Gold 5120 및 듀얼 Intel Xeon Gold 6140 프로세서가 포함된 사용자 정의된 구성에서만 사용할 수 있습니다.

자세한 정보는 인스턴스 또는 클러스터 유형에 해당되는 주문 주제를 참조하십시오.

## 공용 또는 사설 네트워크 사용
{: #relnotes_v26-pub-private-network}

이제 공용 및 사설 네트워크 인터페이스 카드(NIC) 또는 전용 NIC가 사용 가능한 VMware vSphere 클러스터뿐만 아니라 vCenter Server 및 vCenter Server with Hybridity Bundle 인스턴스를 배치할 수 있습니다. 또한 이 옵션은 새 클러스터를 vCenter Server 및 vCenter Server with Hybridity Bundle 인스턴스에 추가할 때도 사용 가능합니다.

일부 추가 기능 서비스에는 공용 NIC가 필요하며 사설 전용 네트워크를 사용하도록 선택하는 경우에는 서비스를 사용할 수 없습니다.

자세한 정보는 다음 주제에서 _네트워크 인터페이스 설정_ 섹션을 참조하십시오.

* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#network-interface-settings)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#network-interface-settings)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#network-interface-settings)

## ESXi 서버 삭제
{: #relnotes_v26-delete-esxi}

이제 인스턴스의 최소 요구사항을 충족하는 경우 vCenter Server, vCenter Server with Hybridity Bundle 또는 Cloud Foundation 인스턴스에서 ESXi 서버를 삭제할 수 있습니다.

ESXi 서버 요구사항에 대한 자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservers)

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v26-vcs}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## VMware vCenter Server with Hybridity Bundle에 대한 업데이트
{: #relnotes_v26-vcs-hybrid}

### vCenter Server 인스턴스에서 Hybridity Bundle 제거
{: #relnotes_v26-remove-bundle}

이제 vCenter Server 인스턴스에서 Hybridity Bundle 라이센스를 제거할 수 있습니다. 이렇게 하려면 VMware NSX 및 VMware vSAN 임대 라이센스 키를 BYOL(Bring Your Own License) 키로 대체하고 지원 티켓을 열어 임대 라이센스에 대한 비용을 취소해야 합니다.

자세한 정보는 [vCenter Server 인스턴스에서 Hybridity Bundle 제거](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_deletingbundle)를 참조하십시오.

### vCenter Server with Hybridity Bundle 가용성
{: #relnotes_v26-bundle-available}

이제 비즈니스 파트너는 vCenter Server with Hybridity Bundle 인스턴스를 주문할 수 있습니다. 비즈니스 파트너는 기존 vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드할 수 없으며, vCenter Server with Hybridity Bundle 인스턴스에서 Hybridity Bundle을 제거할 수 없습니다.

자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server with Hybridity Bundle 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## VMware Cloud Foundation 인스턴스에 대한 업데이트
{: #relnotes_v26-vcf}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.5 Update 2c
* vCenter Server Appliance 6.5 Update 2c
* Platform Services Controller 6.5 Update 2c
* NSX for vSphere 6.4.1

## 추가 서비스에 대한 업데이트
{: #relnotes_v26-services}

### HyTrust KeyControl on IBM Cloud
{: #relnotes_v26-htkc}

이제 HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스는 vSphere 6.5에서 실행 중이고 V2.5 이상 릴리스에 배치되거나 업그레이드되는 VMware vCenter Server 인스턴스 및 VMware Cloud Foundation 인스턴스에 사용 가능합니다. 이 서비스는 암호화 키의 라이프사이클을 자동화 및 단순화하여 암호화된 워크로드의 관리를 단순화합니다. 이 서비스는 FIPS 140-2 준수 암호화를 사용하여 암호화 키를 규모에 맞게 쉽게 관리할 수 있습니다. 이 서비스를 사용하면 모든 가상 머신 및 암호화된 데이터 저장소에 대한 암호화 키를 관리하고 대규모 배치에서 수천 개의 암호화된 워크로드를 지원하도록 확장할 수 있습니다.

인스턴스를 주문할 때 포함된 서비스와 함께 인스턴스를 주문하거나 나중에 이 서비스를 기존 인스턴스에 추가할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [{{site.data.keyword.cloud_notm}}의 HyTrust KeyControl에 대한 컴포넌트 및 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)
* [HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtkc)

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v26-htcc}

현재 릴리스는 새로 배치된 모든 인스턴스에 HyTrust CloudControl 5.4를 설치합니다. HyTrust CloudControl 5.4의 새 기능에 대한 자세한 정보는 [HyTrust CloudControl v 5.4 온라인 문서 설정](https://docs.hytrust.com/CloudControl/5.4.0/Online/index.html)을 참조하십시오.

### HyTrust DataControl on IBM Cloud
{: #relnotes_v26-htdc}

현재 릴리스는 새로 배치된 모든 인스턴스에 HyTrust DataControl 4.2를 설치합니다. HyTrust DataControl 4.2의 새 기능에 대한 자세한 정보는 [HyTrust DataControl 4.x의 새로운 기능](https://docs.hytrust.com/DataControl/4.2/Admin_Guide-4.2/Content/Books/aaCommon/New-Changed-4x.htm)을 참조하십시오.

### vSphere ESXi V6.5 update 2c에 대한 Veeam on IBM Cloud 지원
{: #relnotes_v26-veeam}

V2.6부터 새 인스턴스와 새 호스트는 vSphere ESXi V6.5 Update 2c를 사용하여 프로비저닝됩니다. Veeam Backup and Replication을 사용 중인 경우 vSphere ESXi 6.5 Update 2c와 최상의 호환성을 보장하기 위해 Veeam on {{site.data.keyword.cloud_notm}} 인스턴스를 V9.5u3a 이상으로 업데이트하는 것이 좋습니다.

Veeam on {{site.data.keyword.cloud_notm}}가 설치되어 있는 기존 Cloud Foundation 인스턴스도 V9.5u3a 이상으로 업데이트하는 것이 좋습니다.

Veeam on {{site.data.keyword.cloud_notm}}에 대한 자세한 정보는 [Veeam on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)를 참조하십시오.

### VMware HCX on IBM Cloud
{: #relnotes_v26-hcx}

현재 릴리스는 새로 배치된 모든 인스턴스에 VMware HCX 3.5.1을 설치합니다. HCX 3.5.1의 새 기능에 대한 자세한 정보는 [VMware HCX 문서](https://docs.vmware.com/en/VMware-HCX/index.html)를 참조하십시오.

### vSphere ESXi V6.5 update 2c에 대한 Zerto on IBM Cloud 지원
{: #relnotes_v26-zerto}

기존 호스트를 vSphere ESXi V6.5 update 2로 업데이트하고 이전에 Zerto on {{site.data.keyword.cloud_notm}}를 설치한 경우 Zerto Virtual Replication 콘솔의 VRA(Virtual Replication Appliance) 상태 아래에 `지원되지 않는 ESX 버전` 경고 메시지가 표시될 수 있습니다.

이 경고 메시지를 해결하는 방법에 대한 자세한 정보는 다음을 참조하십시오.

* [Zerto Virtual Replication Interoperability Matrix](http://s3.amazonaws.com/zertodownload_docs/6.0_Latest/Zerto%20Virtual%20Replication%20Operability%20Matrix.pdf)
* [Updating a ZVM to Support Zerto-Approved Host Releases Prior to a Full ZVR Update](https://www.zerto.com/myzerto/knowledge-base/updating-a-zvm-to-support-zerto-approved-host-releases-prior-to-a-full-zvr-update/)

## 새로 작성되고 업데이트된 문서
{: #relnotes_v26-new-docs}

### 참조 아키텍처 문서
{: #relnotes_v26-ref-archi}

{{site.data.keyword.vmwaresolutions_short}} 아키텍처 문서는 VMware 인스턴스 관리 및 운영에 대한 책임을 이해하는 데 중요한 고려사항을 포함하도록 업데이트됩니다.

자세한 정보는 [VMware 인스턴스에 대한 사후 배치 고려사항](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_considerations)을 참조하십시오.

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v26-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

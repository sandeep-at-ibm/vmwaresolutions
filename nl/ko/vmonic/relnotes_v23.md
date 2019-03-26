---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-28"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V2.3 릴리스 정보
{: #relnotes_v23}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 스펙터(Spectre) 및 멜트다운(Meltdown) 조치 방안
{: #relnotes_v23-spectre}

{{site.data.keyword.vmwaresolutions_short}}가 스펙터(Spectre) 및 멜트다운(Meltdown)(CVE-2017-5753, CVE-2017-5715 및 CVE-2017-5754)으로 알려진 취약점에 대한 응답으로 VMware에서 패치를 릴리스했습니다.

* CVEID: [CVE-2017-5753](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)
* CVEID: [CVE-2017-5715](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5715)
* CVEID: [CVE-2017-5754](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)

## VMware vCenter Server on IBM Cloud with Hybridity Bundle
{: #relnotes_v23-vcs-hybrid}

이 릴리스에서는 VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 오퍼링이 도입되었습니다. vCenter Server with Hybridity Bundle은 온프레미스 인프라를 클라우드로 쉽고 빠르게 확장하는 데 도움을 주는 프라이빗 클라우드에서 호스팅됩니다. VMware 환경은 IBM 제공 VMware 소프트웨어 정의 데이터 센터 라이센스를 기반으로 하며 원활한 인프라 하이브리디티 및 진정한 애플리케이션 이동성을 위해 온프레미스 vSphere 5.0+ 환경을 {{site.data.keyword.cloud_notm}} 사이트와 손쉽고 안전하게 연결하는 VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 포함합니다.

HCX on {{site.data.keyword.cloud_notm}} 서비스는 vCenter Server with Hybridity Bundle 인스턴스를 통해서만 사용 가능합니다. 먼저 기본 vCenter Server V2.3 소프트웨어 업데이트를 적용한 후 기존 vCenter Server 인스턴스를 vCenter Server with Hybridity Bundle 인스턴스로 업그레이드할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 업데이트 적용](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)을 참조하십시오.

vCenter Server with Hybridity Bundle에 대한 자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server with Hybridity Bundle 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 요구사항 및 계획](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_planning)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)

## vCenter Server 및 Cloud Foundation 인스턴스에 대한 클러스터 삭제 지원
{: #relnotes_v23-delete-cluster}

이제 전체 인스턴스를 삭제할 필요없이 인스턴스에서 클러스터를 삭제할 수 있습니다. V2.2 이하 인스턴스에 배치된 클러스터의 경우에는 인스턴스에 추가한 클러스터를 삭제하려면 인스턴스를 V2.3으로 업그레이드해야 합니다.

자세한 정보는 [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances#deleting-clusters-from-vcenter-server-instances)를 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v23-vcs}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.
*	VMware vSphere ESXi 6.5 U1g(패치 레벨 ESXi650-201803001이 적용된 ESXi 6.5u1)
*	VMware vCenter Server 6.5 업데이트 1g

V2.3 릴리스부터, **사용자 정의됨** Bare Metal Server 설정을 선택할 때 배치에 다음 새 CPU 모델을 사용할 수 있습니다.
* 듀얼 Intel Xeon Silver 4110 프로세서 / 총 16개의 코어, 2.1GHz
* 듀얼 Intel Xeon Gold 5120 프로세서 / 총 28개의 코어, 2.2GHz

자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server 인스턴스의 클러스터 추가, 보기 및 삭제](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-adding-and-viewing-clusters-for-vcenter-server-instances)

## VMware Cloud Foundation 인스턴스에 대한 업데이트
{: #relnotes_v23-vcf}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.
*	VMware vSphere ESXi 6.5 U1g(패치 레벨 ESXi650-201803001이 적용된 ESXi 6.5u1)
*	VMware vCenter Server 6.5 업데이트 1g
*	VMware NSX for vSphere 6.3.5

## 추가 서비스에 대한 업데이트
{: #relnotes_v23-services}

### HyTrust CloudControl on IBM Cloud
{: #relnotes_v23-htcc}

HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스는 이제 vSphere 6.5를 실행하며 V2.3 이상 릴리스로 배치되거나 V2.3 이상 릴리스로 업그레이드된 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스에 사용할 수 있습니다. 이 서비스는 보안 표준에 대한 준수를 강제하고 제어하며, 역할 기반 액세스 제어(RBAC)를 제공합니다. HyTrust DataControl과 결합되면, 이 서비스는 가상 머신 및 워크로드 데이터가 특정 지역, 클러스터 또는 {{site.data.keyword.cloud_notm}} 데이터 센터 내의 ESXi 서버를 벗어나지 않도록 할 수 있습니다.

인스턴스를 주문할 때 포함된 서비스와 함께 인스턴스를 주문하거나 나중에 이 서비스를 기존 인스턴스에 추가할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}의 컴포넌트 및 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)
* [HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtcc)

### HyTrust DataControl on IBM Cloud
{: #relnotes_v23-htdc}

HyTrust DataControl on {{site.data.keyword.cloud_notm}} 서비스는 이제 vSphere 6.5를 실행하며 V2.3 이상 릴리스로 배치되거나 V2.3 이상 릴리스로 업그레이드된 VMware Cloud Foundation 인스턴스 및 VMware vCenter Server 인스턴스에 사용할 수 있습니다. 이 서비스는 워크로드를 해당 라이프사이클 동안 보호하기 위해 통합된 키 관리 기능을 포함한 강력한 암호화를 제공합니다. 이 서비스는 운영 체제 레벨 및 데이터 레벨 모두에서 암호화를 제공할 수 있으며, 이는 워크로드 내의 모든 디렉토리, 폴더 및 파일이 암호화되거나 복호화될 수 있음을 의미합니다.

인스턴스를 주문할 때 포함된 서비스와 함께 인스턴스를 주문하거나 나중에 이 서비스를 기존 인스턴스에 추가할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}}의 컴포넌트 및 고려사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)
* [HyTrust DataControl on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghtdc)

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v23-spp}

현재 릴리스는 기본 백업 서비스로서 새로 배치된 모든 인스턴스에 IBM Spectrum Protect&trade; Plus on V10.1.1을 설치합니다. IBM Spectrum Protect Plus V10.1.1의 새 기능에 대한 자세한 정보는 [IBM Spectrum Protect Plus 업데이트](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.1/spp/r_techchg_spp.html){:new_window}를 참조하십시오.

## 새로 작성되고 업데이트된 문서
{: #relnotes_v23-new-docs}

배치 후 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}에 스토리지를 추가하는 방법에 대한 단계별 지시사항을 포함하는 새 developerWorks 지침이 사용 가능합니다. 자세한 정보는 [How to increase vsnap storage for IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} post deployment](https://developer.ibm.com/recipes/tutorials/how-to-increase-vsnap-storage-for-ibm-spectrum-protect-plus-on-ibm-cloud-post-deployment/)를 참조하십시오.

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v23-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.
* **일관성**: 이제 사용자 인터페이스는 {{site.data.keyword.cloud_notm}}에서 기타 서비스와 일관적인 룩앤필을 제공합니다.
* **쉬운 액세스**: 이제 {{site.data.keyword.cloud_notm}} **카탈로그**에서 직접 VMware 오퍼링에 액세스할 수 있습니다.
* **간결하고 단순해진 주문 경험**: 이제 하나의 인터페이스에서 VMware 인스턴스 주문 및 해당 추가 기능 서비스 배치를 완료할 수 있습니다. 또한, 비용 계획에 따라 구성을 조정할 수 있도록 동일한 인터페이스에서 예상 비용이 즉시 계산되어 표시됩니다.
* 비즈니스 파트너 사용자는 인스턴스 주문 또는 클러스터 추가 시에 BYOL(Bring Your Own License) 옵션을 사용할 수 없습니다.
* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

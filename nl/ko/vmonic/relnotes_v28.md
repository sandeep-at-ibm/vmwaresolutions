---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-08"

---

# V2.8 릴리스 정보
{: #relnotes_v28}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## 마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 인스턴스
{: #relnotes_v28-single-node-trial}

마이그레이션 및 앱 현대화를 위한 단일 노드 평가판은 {{site.data.keyword.cloud_notm}}를 시범 작동하여 VMware 워크로드를 {{site.data.keyword.cloud_notm}}에 마이그레이션한 후 컨테이너를 사용하여 워크로드를 현대화할 수 있는 가장 빠른 방법입니다. 이 팽가판은 컨테이너를 위한 Kubernetes 관리 플랫폼 및 온프레미스 환경과 동일한 익숙한 도구를 사용하여 관리될 수 있는 싱글 테넌트 VMware 플랫폼을 제공하는 {{site.data.keyword.cloud_notm}}의 {{site.data.keyword.icpfull_notm}} Hosted on VMware vCenter Server 버전입니다.

자세한 정보는 [마이그레이션 및 앱 현대화를 위한 단일 노드 평가판 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-single-node-trial-for-migration-and-app-modernization-overview)를 참조하십시오.

## 네트워크 파일 시스템 스토리지 추가 및 제거
{: #relnotes_v28-nfs}

V2.8 릴리스부터 네트워크 파일 시스템(NFS) 스토리지 공유를 기존 NFS 또는 vSAN vCenter Server 클러스터에 추가하고 기존 vCenter Server 클러스터에서 NFS 파일 공유를 제거할 수 있습니다.

사용자 정의된 공유 파일 레벨 스토리지에 대해 다음 옵션이 현재 사용 가능합니다.

* 1GB 증분으로 20GB에서 시작하여 최대 12TB까지의 NFS 공유 크기
* 0.25 IOPS/GB

자세한 정보는 [vCenter Server 인스턴스에 대한 용량 확장 및 축소](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers#adding-nfs-storage-to-vcenter-server-instances)의 *NFS 스토리지를 vCenter Server 인스턴스에 추가* 및 *vCenter Server 인스턴스에서 NFS 스토리지 제거* 섹션을 참조하십시오.

## SAP 인증 Broadwell E5-2690 및 E7-8890 서버 지원
{: #relnotes_v28-broadwell-e5-e7}

V2.8 릴리스부터 다음의 새 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 모델을 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 및 VMware vSphere on {{site.data.keyword.cloud_notm}} 인스턴스 및 클러스터의 배치에 사용할 수 있습니다.

* 듀얼 Intel Xeon E5-2690 v4 프로세서 / 총 28개의 코어, 2.60GHz / 512GB RAM
* 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.20GHz / 1024GB RAM
* 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.20GHz / 2048GB RAM
* 쿼드 Intel Xeon E7-8890 v4 프로세서 / 총 96개의 코어, 2.20GHz / 4096GB RAM

자세한 정보는 다음의 *{{site.data.keyword.baremetal_short_sing}} 설정* 섹션을 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## Broadwell E7-4820 및 E7-4850 서버 지원
{: #relnotes_v28-broadwell-e7}

V2.8 릴리스부터 다음의 새 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short_sing}} CPU 모델을 vCenter Server, vCenter Server with Hybridity Bundle, Cloud Foundation 및 vSphere on {{site.data.keyword.cloud_notm}} 인스턴스 및 클러스터의 배치에 사용할 수 있습니다.

* 쿼드 Intel Xeon E7-4820 v4 / 총 40개의 코어, 2.0GHz
* 쿼드 Intel Xeon E7-4850 v4 / 총 64개의 코어, 2.1GHz

자세한 정보는 다음의 *{{site.data.keyword.baremetal_short_sing}} 설정* 섹션을 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance#bare-metal-server-settings)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance#bare-metal-server-settings)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances#bare-metal-server-settings)

## 임베드된 Platform Services Controller
{: #relnotes_v28-psc}

V2.8 릴리스부터 vCenter Server는 임베드된 PSC(Platform Services Controller)로 배치됩니다. 즉, vCenter Server, vCenter Server 컴포넌트 및 PSC는 단일 가상 머신에 배치됩니다. 이 변경사항은 모두 새로 배치된 vCenter Server, vCenter Server with Hybridity 및 NetApp 인스턴스에 적용됩니다.

이전 릴리스에서 V2.8로 업그레이드되는 인스턴스의 경우 PSC는 vCenter Server에서 임베드되지 않습니다. 임베드된 PSC를 사용할 경우 외부에서 임베드된 PSC로 자체 변환해야 합니다.

PSC를 외부에서 임베드된 PSC로 수동 변환하는 기본 인스턴스가 업그레이드된 인스턴스인 다중 사이트에서 새로 배치된 V2.8 보조 인스턴스에는 임베드된 PSC가 있습니다.

자세한 정보는 [vCenter Server 개요](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#vcenter-server-architecture)에서 *vCenter Server 아키텍처* 섹션을 참조하십시오.

## VMware vCenter Server 인스턴스에 대한 업데이트
{: #relnotes_v28-vcs}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.5 Update P3(6.5.0-10884925 빌드)
* vCenter Server 6.5 U2d(6.5.0-10964411 빌드)
* Platform Services Controller 6.5 U2d(6.5.0-10964411 빌드)

## VMware Cloud Foundation 인스턴스에 대한 업데이트
{: #relnotes_v28-cf}

이 릴리스는 다음 업그레이드 및 개선사항을 적용합니다.

* vSphere ESXi 6.5 Update EP11(6.5.0-10719125 빌드)
* vCenter Server 6.5 U2c(6.5.0-9451637 빌드)
* Platform Services Controller 6.5 U2c(6.5.0-9451637 빌드)

## 추가 서비스에 대한 업데이트
{: #relnotes_v28-services}

### IBM Spectrum Protect Plus on IBM Cloud
{: #relnotes_v28-spp}

현재 릴리스는 새로 배치된 모든 인스턴스에 IBM Spectrum Protect™ Plus V10.1.2를 설치합니다. IBM Spectrum Protect Plus V10.1.2의 새 기능에 대한 자세한 정보는 [IBM Spectrum Protect Plus 업데이트](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ_10.1.2/spp/r_techchg_spp.html){:new_window}를 참조하십시오.

### KMIP for VMware on IBM Cloud
{: #relnotes_v28-kmip}

이전에는 KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스가 포함된 Cloud Foundation 또는 vCenter Server 인스턴스를 주문하거나 초기 배치 후 서비스를 기존 Cloud Foundation 또는 vCenter Server 인스턴스에 추가할 수 있었습니다.

V2.8 릴리스부터 서비스는 VMware 인스턴스와 연관되지 않고 독립형 서비스로 사용할 수 있습니다. 서비스의 각 인스턴스는 하나 이상의 Cloud Foundation 인스턴스, vCenter Server 인스턴스 또는 vSphere 클러스터를 제공할 수 있습니다.

자세한 정보는 [KMIP for VMware on {{site.data.keyword.cloud_notm}} 개요](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)를 참조하십시오.

## 참조 아키텍처 문서
{: #relnotes_v28-ref}

(2019년 2월 8일에 업데이트) 이제 다음 기술 문서는 사용자 문서의 *참조서* 섹션에서 사용할 수 있습니다.

* [{{site.data.keyword.vmwaresolutions_short}}(NSX-T 아키텍처 사용)](/docs/services/vmwaresolutions/archiref/vcsarch?topic=vmware-solutions-vcsarch-overview)
* [Caveonix RiskForesight 참조 아키텍처](/docs/services/vmwaresolutions/archiref/caveonix?topic=vmware-solutions-caveonix-on-vcs)
* [HCX on {{site.data.keyword.cloud_notm}} 배치 및 오퍼레이션 안내서](/docs/services/vmwaresolutions/archiref/vcshcx?topic=vmware-solutions-vcshcx-intro)

## 사용자 인터페이스 업데이트 및 개선사항
{: #relnotes_v28-ui}

사용자 인터페이스가 업데이트되었으며 다음 개선사항을 제공합니다.

* 사용자 인터페이스에서 적절한 설정을 선택하는 데 도움이 되는 다양한 오류 메시지 및 도구 팁 개선사항을 사용할 수 있습니다.

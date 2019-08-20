---

copyright:

  years:  2016, 2019

lastupdated: "2019-08-05"

keywords: VMware HCX, HCX, tech specs HCX

subcollection: vmware-solutions


---

{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud 개요
{: #hcx_considerations}

HCX on {{site.data.keyword.cloud}} 서비스는 온프레미스 데이터 센터의 네트워크를 {{site.data.keyword.cloud_notm}}로 원활하게 확장하며, 이를 통해 변환이나 변경 없이 {{site.data.keyword.cloud_notm}} 간에 가상 머신(VM)을 마이그레이션할 수 있습니다. HCX는 안전하게 확장된 네트워크를 통해 애플리케이션 이동성 및 인프라 하이브리디티를 사용으로 설정하는 추상 계층을 작성합니다. HCX를 통해 이 원활한 변환이 가능하기 때문에 기존 애플리케이션을 리팩토링하거나 수정할 필요 없이 vSphere 5.1에서 최신 vSphere 버전으로 VMware 환경을 간단히 현대화할 수 있습니다. HCX를 사용하면 엔드-투-엔드 스위트 B 암호화를 통해 상위 레벨의 보안을 제공하는 동시에 하이브리드 배치를 통해 IP 일관성을 보장하여 IP 서브넷 범위를 {{site.data.keyword.cloud_notm}}로 가져올 수 있습니다.

HCX on {{site.data.keyword.cloud_notm}}에서는 {{site.data.keyword.cloud_notm}}를 통해 NSX Advanced 또는 Enterprise를 이용하거나 BYOL(Bring Your Own License)을 사용하여 동등한 버전을 이용해야 합니다. VMware HCX on {{site.data.keyword.cloud_notm}} 서비스를 주문할 때 12개월 약정이 필요합니다. 초기 HCX 배치 후 12개월 연속 비용이 청구됩니다. 추가 노드는 초기 프로비저닝 만기 날짜 내에 포함됩니다. 12개월 약정이 만료된 후 HCX on {{site.data.keyword.cloud_notm}} 서비스를 설치하고 설치 제거할 수 있으며 제한사항 없이 호스트 및 클러스터를 추가하고 제거할 수 있습니다. 그런 다음 사용자 계정에 월별로 비용이 청구되며 언제든지 취소할 수 있습니다.

12개월 약정 만기 날짜는 HCX on {{site.data.keyword.cloud_notm}} 세부사항 페이지에서 볼 수 있습니다. 서비스 세부사항 확인에 대한 자세한 정보는 [vCenter Server 인스턴스에 대한 서비스 주문, 보기 및 제거](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_addingremovingservices#vc_addingremovingservices-viewing-procedure)를 참조하십시오.
{:note}

HCX on {{site.data.keyword.cloud_notm}}의 vCenter Server 인스턴스는 온프레미스 사이트의 세 개의 동시 연결로 제한됩니다.

HCX on {{site.data.keyword.cloud_notm}}는 다음 플랫폼에서 지원됩니다.

* vSphere 5.1(API를 사용한 vCenter 5.1의 명령행만)
* vSphere 5.5(vCenter 5.5u3 이상에서 지원되는 웹 클라이언트 UI)
* vSphere 6.0
* vSphere 6.5(vDS는 6.0 레벨이어야 함)
*  vSphere 6.7

## HCX on IBM Cloud의 기술 스펙
{: #hcx_considerations-specs}

다음 컴포넌트가 주문되고 HCX on {{site.data.keyword.cloud_notm}} 서비스에 포함됩니다.

온프레미스 HCX 인스턴스에는 라이센싱 및 활성화만 포함됩니다.
{:note}

### HCX 관리를 위한 VMware NSX Edge Services Gateway의 활성/수동 쌍
{: #hcx_considerations-nsx}

* CPU: 6개의 vCPU
* RAM: 8GB
* 디스크: 3GB VMDK

### HCX 관리 어플라이언스 - 가상 머신
{: #hcx_considerations-vm}

* CPU: 4개의 vCPU
* RAM: 12GB
* 디스크: 60GB VMDK

L2 연결, WAN 최적화 및 게이트웨이 연결을 위해 필요에 따라 구성 중에 추가로 HCX 어플라이언스가 배치됩니다.

### 네트워킹
{: #hcx_considerations-networking}

* 16개 IP 주소가 포함된 한 개의 공인 포터블 서브넷
* 64개 IP 주소가 포함된 두 개의 사설 포터블 서브넷
* 사설 포터블 vMotion 서브넷의 8개 IP 주소

## HCX on IBM Cloud 설치 시 고려사항
{: #hcx_considerations-install}

HCX on {{site.data.keyword.cloud_notm}}를 설치하기 전에 다음 고려사항을 검토하십시오.

### ESXi 서버의 수에 대한 요구사항
{: #hcx_considerations-esxi-servers}

HCX on {{site.data.keyword.cloud_notm}} 서비스는 기본 클러스터에 52개 이상의 ESXi 서버가 있는 인스턴스에 설치될 수 없습니다. HCX on {{site.data.keyword.cloud_notm}}에서는 기본 클러스터의 vMotion 서브넷에 8개의 IP 주소가 필요하므로 ESXi 서버의 수가 51개를 초과하면 HCX on {{site.data.keyword.cloud_notm}}에 vMotion 서브넷의 IP 주소를 사용할 수 없습니다.

### 방화벽 규칙에 대한 요구사항
{: #hcx_considerations-firewall}

HCX on {{site.data.keyword.cloud_notm}} 서비스를 설치하기 전에 HCX Manager 가상 어플라이언스(HCX Manager)가 자체적으로 등록할 수 있도록 모든 아웃바운드 HTTPS 트래픽을 허용하려면 방화벽 규칙을 기존 방화벽에 추가해야 합니다. HCX Manager 설치가 완료되면 방화벽 규칙을 제거할 수 있습니다. 또한 HCX가 올바르게 작동하도록 방화벽 규칙을 구성해야 합니다. 자세한 정보는 [VMware HCX on {{site.data.keyword.cloud_notm}} 포트 액세스 요구사항](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req)을 참조하십시오.

## HCX on IBM Cloud 제거 시 고려사항
{: #hcx_considerations-delete}

HCX on {{site.data.keyword.cloud_notm}} 서비스를 제거하기 전에 다음 고려사항을 검토하십시오.
* 온프레미스 소스 사이트와 {{site.data.keyword.cloud_notm}} 대상 사이트 간의 상호연결 및 확장된 네트워크가 제거되었는지 확인하십시오. 상호연결 및 확장된 네트워크를 제거하려면 온프레미스 VMware vSphere Web Client에서 HCX 사용자 인터페이스를 사용하십시오.
* 온프레미스 소스 사이트와 {{site.data.keyword.cloud_notm}} 대상 사이트 간의 사이트 페어링이 제거되었는지 확인하십시오. 사이트 페어링을 제거하려면 온프레미스 VMware vSphere Web Client에서 HCX 사용자 인터페이스를 사용하십시오.
* HCX on {{site.data.keyword.cloud_notm}}의 제거가 자동화됩니다. 이 서비스를 제거하려면 다음 프로시저를 완료하십시오.
   * 클라우드 측 HCX Manager에 대해 주문된 HCX 라이센스를 비활성화합니다.
   * HCX Manager를 삭제합니다.
   * HCX에 대해 예약된 vMotion IP 주소를 해제합니다.
   * HCX 관련 리소스 풀이 비어 있는 경우 이를 제거합니다.
   * HCX 관련 폴더가 비어 있는 경우 이를 제거합니다.
   * HCX 관리 에지 어플라이언스를 삭제합니다.

## 관련 링크
{: #hcx_considerations-related}

* [HCX on {{site.data.keyword.cloud_notm}} 주문](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [HCX on {{site.data.keyword.cloud_notm}} 관리](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [VMware HCX on IBM Cloud guided demo: Learn how to migrate a VM by using HCX](https://www.ibm.com/cloud/garage/dte/producttour/vmware-hcx-ibm-cloud-guided-demo-learn-how-migrate-vm-using-hcx){:external}
* [HCX 용어집](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [IBM 지원 센터에 문의](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [VMware Hybrid Cloud Extension 개요](https://cloud.vmware.com/vmware-hcx){:external}
* [VMware Hybrid Cloud Extension 문서](https://cloud.vmware.com/vmware-hcx/resources){:external}

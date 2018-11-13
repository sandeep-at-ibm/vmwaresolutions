---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-26"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server on IBM Cloud 인스턴스에 대한 단일 노드 평가판 주문 및 삭제

VMware vCenter Server on {{site.data.keyword.cloud}}에 대한 단일 노드 평가판은 서비스로 VMware vSphere 스택을 제공하는 단일 테넌트 호스팅 프라이빗 클라우드입니다. 일반적으로 클라이언트 관리 환경은 최소 3개의 노드로 배치되지만, 이 단일 노드 평가판은 하이브리드 클라우드 구현의 이점을 경험할 수 있는 저비용 경로를 제공합니다.

이 평가판은 초기 배치에 대한 IBM의 고급 자동화 속도 및 간단한 비프로덕션 워크로드를 클라우드로 쉽게 이동하는 기능을 보여주는 개념 증명에 이상적입니다. VMware HCX(Hybrid Cloud Extension)를 사용하여 상호 연결을 구성하는 데 따른 네트워크 복잡도를 줄여 주면서 온프레미스 데이터 센터 네트워크를 {{site.data.keyword.CloudDataCent_notm}}에 안전하게 확장할 수 있습니다. HCX는 가상 머신(VM)의 IP를 다시 지정할 필요 없이 양방향으로 워크로드를 원활하게 이동할 수 있도록 공용 인터넷에서 통과하도록 기본 네트워킹 리소스를 추출합니다. HCX를 사용하면 VMware NSX를 온프레미스로 설치할 필요가 없으며 이전 버전의 vSphere와 역호환이 가능합니다.  

단일 노드 평가판은 개념 증명을 위한 것입니다. 이 환경에서 프로덕션 워크로드를 실행하지 마십시오. 호스트 및 클러스터 추가 및 제거, 추가 기능 서비스 추가 주문 및 업데이트 적용과 같은 관리 기능은 지원되지 않습니다.
{:important}

이 평가판은 최대 90일 동안 사용할 수 있습니다. 평가판 사용이 완료되면 이 환경을 삭제한 다음 용량 요구 사항을 충족하는 고가용성 환경을 프로비저닝할 수 있습니다. 자세한 정보는 [vCenter Server with Hybridity Bundle 인스턴스 주문](vc_hybrid_orderinginstance.html)을 참조하십시오.

## vCenter Server 인스턴스에 대한 단일 노드 평가판의 기술 스펙

다음 컴포넌트가 vCenter Server 인스턴스에 대한 단일 노드 평가판에 포함됩니다. 

표준화된 하드웨어 구성의 가용성 및 가격은 배치에 선택된 {{site.data.keyword.CloudDataCent_notm}}에 따라 달라질 수 있습니다.
{:note}

### Bare Metal Server

듀얼 Intel Xeon Gold 5120 (28개 코어, 2.20GHz) 프로세서, 384GB RAM 포함.

### 네트워킹

다음 네트워킹 컴포넌트가 주문됩니다.
*  10Gbps 듀얼 공용 및 사설 네트워크 업링크
*  세 개의 VLAN(Virtual LANs): 한 개의 공용 VLAN 및 두 개의 사설 VLAN
*  계층 2(L2) 네트워크에 연결된 로컬 워크로드 간의 잠재적인 동쪽-서쪽 통신을 위해 DLR(Distributed Logical Router)이 포함된 하나의 VXLAN(Virtual eXtensible LAN). VXLAN은 VXLAN을 수정하거나 VXLAN에 빌드하거나 VXLAN을 제거할 수 있는 샘플 라우팅 토폴로지로 배치됩니다. 또한 추가 VXLAN을 연결하여 DLR의 새 논리 인터페이스에 보안 구역을 추가할 수 있습니다.
*  두 개의 VMware NSX Edge Services Gateway:
  * 관리 네트워킹 토폴로지의 일부로 IBM에서 배치되는 아웃바운드 HTTPS 관리 트래픽을 위한 보안 관리 서비스 VMware NSX Edge Services Gateway(ESG). 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 VM에서 사용됩니다. 자세한 정보는 [고객 관리 ESG를 사용하도록 네트워크 구성](../vcenter/vc_esg_config.html#configuring-your-network-to-use-the-customer-managed-nsx-esg-with-your-vms)을 참조하십시오.

    사용자는 이 ESG에 액세스할 수 없고 사용할 수 없습니다. 이를 수정하면 {{site.data.keyword.vmwaresolutions_short}} 콘솔에서 vCenter Server with Hybridity Bundle 인스턴스를 관리하지 못하게 될 수 있습니다. 또한 방화벽을 사용하거나 외부 IBM 관리 컴포넌트와의 ESG 통신을 사용 안함으로 설정하면 {{site.data.keyword.vmwaresolutions_short}}를 사용할 수 없게 됩니다.
    {:important}
  * VPN 액세스 또는 공용 액세스를 제공하도록 사용자가 수정할 수 있는 템플리트로 IBM에서 배치되는 아웃바운드 및 인바운드 HTTPS 워크로드 트래픽을 위한 보안 고객 관리 VMware NSX Edge Services Gateway. 자세한 정보는 [고객 관리 NSX Edge는 보안 문제점을 발생시킵니까?](../vmonic/faq.html#does-the-customer-managed-nsx-edge-pose-a-security-risk-)를 참조하십시오.

HCX on {{site.data.keyword.cloud_notm}} 서비스를 배치할 떄 주문한 네트워킹 컴포넌트에 대한 자세한 정보는 [HCX on {{site.data.keyword.cloud_notm}} 개요](../services/hcx_considerations.html)를 참조하십시오.

### Virtual Server 인스턴스

다음 VSI(Virtual Server Instance)가 주문됩니다.

* 인스턴스 배치가 완료된 후 시스템이 종료되는 IBM CloudBuilder용 VSI
* Microsoft Active Directory(AD)용 Microsoft Windows Server VSI가 배치되어 있으며 검색할 수 있습니다. VSI는 호스트와 가상 머신이 등록되는 인스턴스에 대한 DNS의 역할을 합니다.

### IBM 제공 라이센스 및 요금

다음 라이센스가 vCenter Server 인스턴스 주문에 대한 단일 노드 평가판에 포함됩니다.

* VMware vSphere Enterprise Plus 6.5u1
* VMware vCenter Server 6.5
* VMware NSX Service Providers Advanced Edition 6.4

vCenter Server 인스턴스에 대한 단일 노드 평가판은 BYOL(Bring Your Own License)을 지원하지 않습니다.
{:note}

추가 지원 및 서비스 요금이 적용될 수 있습니다.

## HCX on IBM Cloud의 기술 스펙

HCX on {{site.data.keyword.cloud_notm}}에 대한 기술 스펙 및 고려사항에 대한 정보는 [VMware HCX on IBM Cloud 개요](../services/hcx_considerations.html)를 참조하십시오.

## vCenter Server 인스턴스에 대한 단일 노드 평가판 주문의 요구사항 및 계획

다음 태스크를 완료하십시오.
* 사용 중인 {{site.data.keyword.cloud_notm}} 계정은 특정 요구사항을 충족해야 합니다. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 계정에 대한 요구사항](../vmonic/slaccountrequirement.html)을 참조하십시오.
*  **설정** 페이지에서 {{site.data.keyword.cloud_notm}} 인프라 인증 정보를 구성하십시오. 자세한 정보는 [사용자 계정 및 설정 관리](../vmonic/useraccount.html)를 참조하십시오.
* 인스턴스 이름 요구사항을 검토하십시오.  
 * 영숫자 문자 및 대시(-) 문자만 사용할 수 있습니다.
 * 인스턴스 이름은 영숫자 문자로 시작하고 끝나야 합니다.
 * 인스턴스 이름의 최대 길이는 10자입니다.
 * 인스턴스 이름은 계정 내에서 고유해야 합니다.
* 물리적 인프라에 대한 요구사항을 충족하는지 {{site.data.keyword.CloudDataCents_notm}}를 검토하십시오. 자세한 정보는 *{{site.data.keyword.CloudDataCent_notm}} availability* section in [vCenter Server with Hybridity Bundle 인스턴스 요구사항 및 계획](../vcenter/vc_hybrid_planning.html#ibm-cloud-data-center-availability)을 참조하십시오.
<!--* Ensure the that you meet the following prerequisites for the on-premises HCX instance:
 * VMware vSphere and vCenter 5.5 or higher
 * The VMware HCX Manager must reside in the same security zone as the on-premises vSphere environment
 * The VMware HCX Manager must be able to reach the public Internet to update firewall rules to allow outbound traffic
 * The vSphere environment must have distributed switches-->

## vCenter Server 인스턴스에 대한 단일 노드 평가판의 주문 프로시저

1. **VMware vCenter Server on {{site.data.keyword.cloud_notm}}에 대한 단일 노드 평가판** 페이지에서 **vCenter Server** 카드를 클릭하고 **구성**을 클릭하십시오.
2. **VMware vCenter Server에 대한 단일 노드 평가판** 페이지에서 {{site.data.keyword.cloud_notm}} 인프라 계정을 요청하는 단계를 완료하거나 기존의 **사용자 이름** 및 **API 키**를 제공하고 **검색**을 클릭하십시오.
3. 인스턴스 이름을 입력하십시오.
4. {{site.data.keyword.CloudDataCent_notm}}를 선택하여 인스턴스를 호스팅하십시오.  

 {{site.data.keyword.CloudDataCent_notm}}가 미리 선택되어 있습니다. 필요한 경우 다른 {{site.data.keyword.CloudDataCent_notm}} 위치를 선택하십시오.
 {:note}
5. 주문하기 전에 **주문 요약** 페이지에서 인스턴스 구성을 확인하십시오.
   1. 인스턴스의 설정을 검토하십시오.
   2. 인스턴스의 예상 비용을 검토하십시오. PDF 요약을 생성하려면 **가격 세부사항**을 클릭하십시오. 주문 요약을 저장하거나 인쇄하려면 PDF 창의 오른쪽 상단에 있는 **인쇄** 또는 **다운로드** 아이콘을 클릭하십시오.
   3. 주문에 적용되는 이용 약관에 대한 링크를 클릭하고, 인스턴스를 주문하기 전에 이러한 이용 약관에 동의하는지 확인하십시오.
   4. **프로비저닝**을 클릭하십시오.

### 결과

인스턴스의 배치가 자동으로 시작되고 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 서비스 활성 키가 주문됩니다. 

#### HCX on IBM Cloud에 대한 배치 프로세스

HCX on {{site.data.keyword.cloud_notm}}의 배치가 자동화됩니다. 다음 단계는 {{site.data.keyword.vmwaresolutions_short}} 자동화 프로세스에 의해 완료됩니다.
1. {{site.data.keyword.cloud_notm}} 인프라에서 HCX에 대해 3개의 서브넷이 주문됩니다.
   * HCX 관리를 위한 하나의 사설 포터블 서브넷.
   * HCX 상호연결을 위한 하나의 사설 포터블 서브넷. **사설 네트워크** 옵션이 **HCX 상호연결 유형**에 대해 선택된 경우 이 서브넷이 사용됩니다.
   * VMware의 활성화와 유지보수를 위한 하나의 공인 포터블 서브넷. **공인 네트워크** 옵션이 **HCX 상호연결 유형**에 대해 선택된 경우 이 서브넷도 HCX 상호연결에 사용됩니다.

   HCX에 대해 주문된 서브넷의 IP 주소는 VMware on {{site.data.keyword.cloud_notm}} 자동화로 관리되어야 합니다. 사용자가 작성한 VMware 리소스(예: VM 및 NSX Edge)에 이 IP 주소를 지정할 수 없습니다. VMware 아티팩트에 대한 추가 IP 주소가 필요한 경우 {{site.data.keyword.cloud_notm}}에서 고유한 서브넷을 주문해야 합니다.
   {:important}
2. **사설 네트워크**가 **HCX 상호연결 유형**으로 선택된 경우에는 사설 DVS(Distributed Virtual Switch)에서 **SDDC-DPortGroup-HCX-Private**이 작성됩니다.
3. VMware에서 HCX 정품 인증 키가 주문됩니다.
4. HCX 상호연결, 로컬 HCX 컴포넌트 및 원격 HCX 컴포넌트에서 필요로 하는 3개의 HCX용 리소스 풀 및 VM 폴더가 작성됩니다.
5. HCX 관리 트래픽을 위한 VMware NSX ESG(Edge Services Gateway)의 쌍이 배치되고 구성됩니다.
   * 주문된 서브넷을 사용하여 공용 및 사설 업링크 인터페이스가 구성됩니다.
   * ESG가 고가용성(HA)을 사용하는 추가 대형 에지 어플라이언스의 쌍으로 구성됩니다.
   * HCX Manager 간에 인바운드 및 아웃바운드 HTTPS 트래픽을 허용하도록 방화벽 규칙 및 네트워크 주소 변환(NAT) 규칙이 구성됩니다.
   * 로드 밸런서 규칙 및 리소스 풀이 구성됩니다. 이러한 규칙은 HCX Manager, vCenter Server 및 PSC(Platform Services Controller)의 적절한 가상 어플라이언스로 HCX 관련 인바운드 트래픽을 전달하는 데 사용되는 리소스 풀입니다.
   * ESG를 통해 수신되는 HCX 관련 인바운드 HTTPS 트래픽을 암호화하는 SSL 인증서가 적용됩니다.

   HCX 관리 에지는 온프레미스 HCX 컴포넌트와 클라우드 측 HCX 컴포넌트 간의 HCX 관리 트래픽에만 사용됩니다. HCX 관리 에지를 수정하거나 HCX 네트워크 확장에 이를 사용하지 마십시오. 대신, 네트워크 확장을 위한 별도의 에지를 작성하십시오. 또한 방화벽을 사용하거나 사설 IBM 관리 컴포넌트 또는 공용 인터넷과의 HCX 관리 에지 통신을 사용 안함으로 설정하면 HCX 기능에 부정적인 영향을 줄 수 있습니다.
   {:important}

6. HCX Manager on {{site.data.keyword.cloud_notm}}가 배치되고 활성화되고 구성됩니다.
   * HCX Manager는 vCenter Server에 등록됩니다.
   * HCX Manager, vCenter Server, PSC 및 NSX Manager가 구성됩니다.
   * HCX Fleet가 구성됩니다.
   * 로컬 및 원격 HCX 배치 컨테이너가 구성됩니다.
7. HCX Manager의 호스트 이름 및 IP 주소가 VMware vCenter Server on {{site.data.keyword.cloud_notm}}의 DNS 서버에 등록됩니다.

#### 인스턴스 세부사항 보기

인스턴스 세부사항을 보고 배치 상태를 확인할 수 있습니다. 인스턴스 세부사항 보기에 대한 정보는 다음을 참조하십시오.

* [vCenter Server 인스턴스 보기](vc_viewinginstances.html)
* [온프레미스 VMware HCX on IBM Cloud 인스턴스 보기](../services/standalone_viewingserviceinstances.html)

인스턴스가 성공적으로 배치되는 경우 이 주제의 *기술 스펙* 섹션에 설명되어 있는 컴포넌트가 VMware 가상 플랫폼에 설치되며, 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 서비스 정품 인증 키는 온프레미스 HCX on {{site.data.keyword.cloud_notm}} 세부사항 페이지에서 사용할 수 있습니다.

인스턴스의 상태가 **사용할 준비가 됨**으로 변경되고 이메일로 알림을 받습니다. 

### 수행할 작업

HCX on {{site.data.keyword.cloud_notm}} 서비스를 구성하고 온프레미스 정품 인증 키를 설치하십시오.

1. **배치된 인스턴스** 페이지에서 온프레미스 정품 인증 키를 찾으십시오.
  1. {{site.data.keyword.vmwaresolutions_short}} 콘솔의 왼쪽 탐색 분할창에서 **배치된 인스턴스**를 클릭하십시오.
  2. **vCenter Server 인스턴스** 테이블에서 **유형** 열을 검토하여 단일 노드 평가판 인스턴스를 찾고 인스턴스 이름을 기록해 두십시오. 
  3. **온프레미스 HCX 인스턴스** 테이블로 스크롤하고 **이름** 열을 검토하여 단일 노드 인스턴스와 동일한 이름을 가진 인스턴스를 찾으십시오. 
  4. **정품 인증 키** 필드에 있는 키를 기록해 두십시오.
2. [VMware HCX](https://hcx.vmware.com/#/vm-documentation)로 이동한 후 정품 인증 키를 사용하여 온프레미스 VMware HCX on {{site.data.keyword.cloud_notm}} 인스턴스를 설치하고 설정 프로세스를 완료하십시오. 자세한 정보는 *프로시저 출시 예정*을 참조하십시오.

{{site.data.keyword.slportal}} 또는 콘솔 이외의 다른 수단이 아닌 {{site.data.keyword.vmwaresolutions_short}} 콘솔의 {{site.data.keyword.cloud_notm}} 계정에만 작성되는 {{site.data.keyword.vmwaresolutions_short}} 인프라 컴포넌트 관리해야 합니다.
{{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 컴포넌트를 변경하는 경우 변경사항이 콘솔과 동기화되지 않으며 환경을 불안정하게 할 수 있습니다.
{:important}

## vCenter Server 인스턴스에 대한 단일 노드 평가판 삭제 프로시저

vCenter Server 인스턴스에 대한 단일 노드 평가판에서 주문한 컴포넌트를 릴리스하려면 인스턴스를 삭제하십시오.

자세한 정보는 [vCenter Server 인스턴스 삭제](vc_deletinginstance.html)를 참조하십시오.

### 관련 링크

* [{{site.data.keyword.cloud_notm}} 계정 등록](../vmonic/signing_softlayer_account.html)
* [HCX 용어집](../services/hcx_glossary.html)
* [VMware Hybrid Cloud Extension 문서](https://hcx.vmware.com/#/vm-documentation)
* [vCenter Server with Hybridity Bundle 개요](vc_hybrid_overview.html)
* [vCenter Server with Hybridity Bundle 인스턴스에 대한 네트워킹 고려사항](vc_hybrid_networkingonvcenterserver.html)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](vc_hybrid_orderinginstance.html)

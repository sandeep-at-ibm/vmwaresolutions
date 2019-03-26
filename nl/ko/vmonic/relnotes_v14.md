---

copyright:

  years:  2016, 2017

lastupdated: "2017-03-08"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# V1.4 릴리스 정보
{: #relnotes_v14}

이 릴리스에는 새 기능, 컴포넌트 업데이트, 사용성 개선사항 및 버그 수정이 포함됩니다. 다른 릴리스에서 수정된 문제, 제품에 대해 알려진 문제 및 {{site.data.keyword.vmwaresolutions_full}}에 사용할 팁의 목록은 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}를 참조하십시오.

## Cloud Foundation 인스턴스에 대한 컴포넌트 업데이트
{: #relnotes_v14-vcf-comp}

다음 컴포넌트가 새로 작성되거나 업데이트됩니다.

* VC 및 PSC(vCenter 및 Platform Services Controller) 6.0U2a
* VMware Tools 10.1.0
* SDDC Manager (SP) 2.2
* VMware ESXi 6.0 u2 p04
* 새 Windows VSI(Virtual Server Instance)는 이 릴리스의 다중 사이트 구성 지원에 필요한 Microsoft Active Directory(AD) 및 DNS(Domain Name System) 서비스에 대해 주문됩니다. 이 VSI 스펙은 Windows 2012 R2(8GB RAM / 두 개의 CPU 코어 / 100GB 디스크 / 듀얼 1Gbps 사설 업링크)입니다.

## vCenter Server 인스턴스에 대한 컴포넌트 업데이트
{: #relnotes_v14-vcs-comp}

다음 컴포넌트가 새로 작성되거나 업데이트됩니다.

### VMware NSX for vSphere 6.2.4
{: #relnotes_v14-nsx}

기본적으로 VMware NSX for vSphere 6.2.4는 이제 모든 vCenter Server 인스턴스(이전에는 Cloud Foundation 인스턴스에서만)에 설치됩니다.

NSX 설치의 일부로 NSX Manager가 배치된 모든 새 인스턴스에 설치되고 라이센스가 부여됩니다. 또한 NSX Edge는 인스턴스 관리를 위해 작성되지만 필요한 경우 고유한 NSX Edge 컴포넌트를 작성할 수 있습니다. NSX Edge에 대한 자세한 정보는 이 페이지의 _VMware NSX Edge_ 절을 참조하십시오.

NSX Controller는 vCenter Server 인스턴스에 설치되어 있지 않습니다(Cloud Foundation 인스턴스에 설치된 방법으로). VXLAN 또는 vCenter Server 인스턴스에 대한 분배된 논리 라우터를 사용하는 경우 자체적으로 NSX Controller를 설치해야 합니다.
{:note}

VMware NSX for vSphere 6.2.4에 도입된 개선사항, 요구사항 및 알려진 문제에 대한 자세한 정보는 [NSX for vSphere 6.2.4 릴리스 정보](http://pubs.vmware.com/Release_Notes/en/nsx/6.2.4/releasenotes_nsx_vsphere_624.html){:new_window}를 참조하십시오.

### VMware NSX Edge
{: #relnotes_v14-nsx-edge}

NSX Edge는 이제 주문 중인 새 vCenter Server 인스턴스의 일부로 포함됩니다. NSX Edge는 네트워크 에지 보안 및 게이트웨이 서비스를 제공하여 가상화된 네트워크를 격리합니다.

인스턴스 배치 중에 IBM에서 관리 VMware NSX Edge Services Gateway(ESG)가 배치됩니다. 이 ESG는 자동화와 관련된 특정 외부 IBM 관리 컴포넌트와 통신하기 위해 IBM 관리 가상 머신에서 사용됩니다. 이 ESG는 2개의 인터페이스를 포함하기 위해 배치됩니다. 하나의 인터페이스는 {{site.data.keyword.cloud_notm}} 사설 VLAN에 연결되고, 다른 하나의 인터페이스는 {{site.data.keyword.cloud_notm}} 공용 VLAN에 연결됩니다.

보안을 보장하기 위해 관리 가상 머신에서 시작된 아웃바운드 HTTPS 통신만 허용하도록 방화벽 규칙이 제공됩니다. 이 ESG는 대형 구성에 배치되고 IBM 지원 센터만 구성을 수정할 수 있습니다. 자세한 정보는 다음 주제를 참조하십시오.

* [vCenter Server 기술 스펙](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview#specs)
* [관리 서비스 NSX Edge는 보안 문제점을 발생시킵니까?](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)
* [VMware NSX Documentation](https://pubs.vmware.com/NSX-6/index.jsp?topic=%2Fcom.vmware.nsx.admin.doc%2FGUID-3F96DECE-33FB-43EE-88D7-124A730830A4.html){:new_window}

### NSX 라이센스
{: #relnotes_v14-nsx-license}

노드당 VMware NSX Base for Service Providers Edition 라이센스가 주문됩니다.

### 새 서브넷 주소 블록
{: #relnotes_v14-subnet}

노드당 16개의 공인 포터블 주소의 서브넷 블록이 주문됩니다.

## 서비스 비용 모델 업데이트
{: #relnotes_v14-svc-charge}

서비스 비용 모델이 간소화되었습니다.

* Cloud Foundation 인스턴스의 경우, _VMware Cloud Foundation 인스턴스 서비스_, _VMware Cloud Foundation 스토리지 서비스_ 및
   _VMware Solutions 하이퍼바이저_ 요금 부과가 중단됩니다.
* vCenter Server 인스턴스의 경우, _VMware vCenter Server 인스턴스_ 및 _VMware Solutions 하이퍼바이저_ 요금 부과가 중단됩니다.
* 두 인스턴스 유형의 경우, 각 노드에 적용되는 월별 요금인 새 _지원 및 서비스_ 요금이 도입되었습니다.

## 인스턴스 네트워킹 토폴로지에 대한 업데이트
{: #relnotes_v14-netwok-topo}

이 릴리스에는 인스턴스에 대한 다음 토폴로지 개선사항이 포함되어 있습니다.

* Cloud Foundation 인스턴스 및 vCenter Server 인스턴스의 경우: 최적화된 네트워킹 구성 즉, SoftLayer®로 지정된 기본 공용 및 사설 IP 주소만 ESXi 서버에 연결됩니다. 포터블 사설 주소가 더이상 관리 트래픽에 대해 배치되지 않습니다.
* Cloud Foundation 인스턴스만의 경우: Windows AD SSO(Active Directory Single Sign-On) 및 DNS(Domain Name System) 서버

이 변경으로 인해 현재 릴리스에서 기존의 V1.4 이전 인스턴스를 사용할 수 없습니다. 기존 인스턴스의 구성을 다시 사용하려면 기존 인스턴스를 현재 버전으로 업그레이드해야 합니다.
{:note}

## Cloud Foundation 인스턴스에 대한 다중 사이트 구성 지원
{: #relnotes_v14-vcf-multisite}

이제 이전 릴리스에서와 같이 단일 Cloud Foundation 인스턴스를 배치하거나 기본 인스턴스에 연결된 보조 인스턴스를 배치할 수 있습니다. 다중 사이트 구성 모델은 기본 사이트와 최대 일곱 개의 보조 사이트로 허브 및 스포크 토폴로지를 사용합니다.

## Zerto 재해 복구의 배치에 대한 개선사항
{: #relnotes_v14-zerto}

* Cloud Foundation 인스턴스의 경우, Zerto 재해 복구의 배치가 지원 티켓을 통해 처리되지 않고 자동화됩니다. 주문하기 전에 검토할 수 있도록 예상 비용에 모든 Zerto 컴포넌트(예: 사설 포터블 서브넷), Windows VSI(Virtual Service Instance) 및 Zerto 라이센스 비용이 나열됩니다.
* vCenter Server 인스턴스의 경우, 이전 릴리스에서와 같이 Zerto 재해 복구의 배치가 지원 티켓을 통해 수행됩니다. 그러나 NSX Edge 및 공인 포터블 서브넷이 이제 기본 배치에 포함되므로 더 이상 필요하지 않습니다. 사설 포터블 서브넷, Windows VSI(Virtual Service Instance) 및 Zerto 라이센스의 비용이 계속해서 적용됩니다.

자세한 정보는 [Zerto 재해 복구](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)를 참조하십시오.

## 인스턴스 주문 프로세스
{: #relnotes_v14-inst-order}

인스턴스 주문 프로세스가 크게 간소화되었습니다.

* 두 Cloud Foundation 인스턴스 및 vCenter Server 인스턴스의 경우, 주문 프로세스 중에 SoftLayer 인증 정보 페이지가 더 이상 표시되지 않습니다. 설정 페이지에 정의된 SoftLayer 인증 정보가 기본적으로 사용되고 SoftLayer 인증 정보가 요구사항을 충족하지 않는 경우에만 업데이트하도록 프롬프트됩니다.
* 또한 vCenter Server 인스턴스의 경우, 이제 **하드웨어** 유형의 **대형** 옵션과 **업링크 포트 속도**의 **10Gbps 듀얼** 설정만 사용 가능하며 이를 통해 주문 시 지정할 설정의 수가 줄어듭니다.

자세한 정보는 [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)을 참조하십시오.

## 인스턴스 관리
{: #relnotes_v14-inst-mgmt}

인스턴스 관리 프로세스에 대한 새 기능 및 개선사항은 다음과 같습니다.

* Cloud Foundation 인스턴스의 경우, 인스턴스 세부사항 페이지에서 여러 인스턴스 컴포넌트에 대한 사용자 이름 및 비밀번호를 볼 수 있습니다.
* vCenter Server 인스턴스의 경우, 이제 콘솔에서 직접 IBM 컴포넌트용 소프트웨어 업데이트 및 패치를 설치할 수 있습니다. 자세한 정보는 [vCenter Server 인스턴스에 업데이트 및 패치 적용](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_applyingupdates)을 참조하십시오.

## 콘솔 알림
{: #relnotes_v14-console-notif}

이제 **설정** 페이지에서 콘솔 알림을 구성할 수 있습니다. 기본적으로 설정은 사용으로 설정되며, 이는 콘솔에서 모든 이벤트에 대한 알림을 받음을 의미합니다. 또한 **설정** 페이지에서 콘솔의 알림을 사용 안함으로 설정할 수 있습니다.

자세한 정보는 다음 주제를 참조하십시오.

* [사용자 계정 및 설정](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)
* [알림](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-notifications)

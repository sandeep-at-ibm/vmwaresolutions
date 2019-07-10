---

copyright:

  years: 2016, 2019

lastupdated: "2019-05-31"

keywords: IBM Cloud for VMware Solutions, getting started, vmware solutions offerings, add-on services for vmwaresolutions, vmwaresolutions use cases

subcollection: vmware-solutions


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:important: .important}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# 시작하기 튜토리얼
{: #getting-started}

이 시작하기 튜토리얼에서 인스턴스 및 이에 대한 몇 가지 추가 기능 서비스 주문 프로세스를 안내합니다.
{:shortdesc}

## 시작하기 전에
{: #getting-started-prereqs}

{{site.data.keyword.vmwaresolutions_full}}에 대한 작업을 시작하려면 먼저 브라우저 요구사항, 사용자 계정, 배치 옵션 및 추가 기능 서비스에 대한 다음 중요 정보를 검토하십시오.

### 브라우저 요구사항
{: #getting-started-browser-req}

지원되는 브라우저는 다음과 같습니다.
  *  Mozilla Firefox
  *  Google Chrome
  *  Apple Safari

Microsoft Internet Explorer가 지원되지 않습니다.
{:note}

{{site.data.keyword.vmwaresolutions_short}} 콘솔에서 보기 및 작업을 최적화하려면 최소 1024 픽셀 너비 x 500 픽셀 높이로 화면 해상도를 설정하십시오.

### 사용자 계정
{: #getting-started-user-accts}

{{site.data.keyword.cloud_notm}} 계정 및 {{site.data.keyword.cloud_notm}} 인프라 계정이 있어야 합니다. 이러한 계정은 특정 요구사항을 충족해야 합니다.

   표 1. 필수 사용자 계정
   <table>
   <tr>
      <th>계정</th>
      <th>설명</th>
   </tr>
   <tr>
      <td>IBM ID</td>
      <td>**IBM ID**를 사용하면 {{site.data.keyword.cloud_notm}}를 포함하여 사용하는 모든 IBM 제품과 서비스에 하나의 로그인 사용자 이름을 사용할 수 있습니다. {{site.data.keyword.vmwaresolutions_short}}는 {{site.data.keyword.cloud_notm}} 카탈로그의 인프라 솔루션으로 제공됩니다. {{site.data.keyword.vmwaresolutions_short}} 콘솔에 액세스하려면 **IBM ID**가 있어야 합니다.<br><br>**IBM ID**를 사용하여 {{site.data.keyword.vmwaresolutions_short}} 콘솔에 로그인하려면 **IBM ID**를 {{site.data.keyword.cloud_notm}} 계정과 연관시켜야 합니다. 처음 콘솔에 로그인하면 기존 **IBM ID**를 {{site.data.keyword.cloud_notm}} 계정과 연관시키거나 새 {{site.data.keyword.cloud_notm}} 계정을 등록하도록 안내를 받습니다. 새 {{site.data.keyword.cloud_notm}} 계정은 **IBM ID**와 자동으로 연관됩니다. 이 프로세스를 한 번만 수행해야 합니다.<br><br>**IBMid**를 {{site.data.keyword.cloud_notm}} 계정과 연관시키는 데 문제점이 있는 경우, [{{site.data.keyword.cloud_notm}} 액세스의 문제점 해결](/docs/account?topic=account-accessing#accessing)을 참조하십시오.</td>
   </tr>
   <tr>
      <td>IBM Cloud 계정</td>
      <td>{{site.data.keyword.cloud_notm}} 서비스를 주문하고 사용하려면 {{site.data.keyword.cloud_notm}} 계정이 필요합니다. 청구 정보는 {{site.data.keyword.cloud_notm}} 계정과 연관되어 있습니다. 실제 및 가상 인프라의 비용과 결과 라이센스는 {{site.data.keyword.cloud_notm}} 계정에 비용이 청구됩니다.</td>
   </tr>
   <tr>
      <td>IBM Cloud 인프라 계정</td>
      <td>{{site.data.keyword.cloud_notm}} 인프라 계정의 요구사항에 대한 자세한 정보는 [{{site.data.keyword.cloud_notm}} 인프라 계정에 대한 요구사항](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-cloud-infra-acct-req)을 참조하십시오.<br><br>{{site.data.keyword.cloud_notm}} 인프라 계정과 {{site.data.keyword.cloud_notm}} 계정을 링크하여 결합된 IaaS(Infrastructure as a Service) 및 PaaS(Platform as a Service) 리소스를 사용할 수 있습니다. 그리고 단일 로그인에서 IaaS 리소스와 PaaS 리소스에 액세스할 수 있습니다. 또한 계정을 연결하면 사용하는 모든 PaaS 및 IaaS 리소스에 대한 하나의 송장이 사용자에게 제공됩니다.<ul><li>{{site.data.keyword.cloud_notm}} 인프라 계정이 없는 경우에는 [IBM Cloud 인프라 계정 등록](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-signing_required_accounts#signing_required_accounts-infra)의 프로시저에 따라 계정을 요청한 후에 [IBM ID로 전환 및 계정 연결](/docs/account?topic=account-unifyingaccounts#unifyingaccounts)의 프로시저에 따라 {{site.data.keyword.cloud_notm}} 인프라 계정을 {{site.data.keyword.cloud_notm}} 계정과 링크하십시오.</li><li>{{site.data.keyword.cloud_notm}} 인프라 계정이 있는 경우에는 [IBM ID로 전환 및 계정 연결](/docs/account?topic=account-unifyingaccounts#unifyingaccounts)의 프로시저에 따라 이를 {{site.data.keyword.cloud_notm}} 계정과 연결할 수 있습니다.</li></ul></td>
   </tr>
   </table>

### 배치 오퍼링
{: #getting-started-depl-offerings}

배치 오퍼링을 검토하고 선택하십시오.

  표 2. 배치 오퍼링
  <table>
    <tr>
       <th>배치 오퍼링</th>
       <th>설명</th>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_vcenterserveroverview)</td>
       <td>vCenter Server 오퍼링을 사용하면 비즈니스 요구사항에 가장 적합하도록 사용자 정의 컴퓨팅, 스토리지 및 네트워크 리소스를 사용하여 VMware 가상 환경을 배치할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[VMware vCenter Server on IBM Cloud with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)</td>
       <td>vCenter Server with Hybridity 오퍼링은 온프레미스 인프라를 클라우드로 손쉽고 빠르게 확장하는 데 도움을 주는 호스팅된 프라이빗 클라우드입니다. VMware 환경은 IBM 제공 VMware 소프트웨어 정의 데이터 센터 라이센스를 기반으로 하며 VMware Hybrid Cloud Extension(HCX)를 포함합니다. HCX를 사용하면 원활한 인프라 하이브리디티 및 진정한 애플리케이션 이동성을 위해 온프레미스 vSphere 5.0+ 환경을 {{site.data.keyword.cloud_notm}} 사이트와 안전하게 연결할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[VMware vSphere on IBM Cloud](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_vsphereclusteroverview)</td>
       <td>vSphere on {{site.data.keyword.cloud_notm}} 오퍼링은 고유한 IBM 호스팅 VMware 환경을 빌드할 수 있도록 VMware 호환 가능 {{site.data.keyword.baremetal_short}}, 하드웨어 컴포넌트 및 라이센스를 결합하는 사용자 정의 가능한 가상화 서비스를 제공합니다.</td>
    </tr>
    <tr>
       <td>[NetApp ONTAP Select](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_netappoverview)</td>
       <td>NetApp ONTAP Select 오퍼링은 NetApp ONTAP Select 기반의 전용 및 고가용성 스토리지 어플라이언스에 대한 사용자의 요구사항을 처리하는 소프트웨어 정의 스토리지 클러스터를 배치할 수 있도록 허용합니다.</td>
    </tr>
  </table>

### 추가 기능 서비스
{: #getting-started-add-on-services}

배치 오퍼링의 추가 기능 서비스를 검토하고 선택하십시오.

  표 3. 배치 오퍼링의 사용 가능한 추가 기능 서비스
  <table>
    <tr>
       <th> 서비스 이름</th>
       <th>설명</th>
    </tr>
    <tr>
       <td>[F5 on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations)</td>
       <td>F5 on {{site.data.keyword.cloud_notm}} 서비스(F5 BIG-IP® Virtual Edition)는 로컬 및 글로벌 스케일의 인텔리전트 L4-L7 로드 밸런싱 및 트래픽 관리 서비스, 강력한 네트워크 및 웹 애플리케이션 방화벽 보호, 안전하고 연합된 애플리케이션 액세스를 제공합니다.</td>
    </tr>
    <tr>
       <td>[FortiGate Security Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)</td>
       <td>FortiGate Security Appliance on {{site.data.keyword.cloud_notm}} 서비스는 고가용성 모드에서 방화벽, 라우팅, NAT 및 VPN 서비스를 제공하도록 FSA(FortiGate Security Appliance) 300 시리즈 디바이스의 쌍을 배치하여 인스턴스의 공용 VLAN에서 모든 서버 및 가상 머신을 보호합니다.</td>
    </tr>
    <tr>
       <td>[FortiGate Virtual Appliance on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)</td>
       <td>FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 서비스는 가상 인프라 내에서 중요한 보안 제어를 구현하여 위험을 줄일 수 있는 FortiGate Virtual Appliances 쌍을 사용자 환경에 배치합니다.</td>
    </tr>
    <tr>
       <td>[HyTrust CloudControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)</td>
       <td>HyTrust CloudControl on {{site.data.keyword.cloud_notm}} 서비스는 보안 표준에 대한 준수를 강제하고 제어하며, 상세한 역할 기반 액세스 제어(RBAC), 승인 및 감사 기능을 제공합니다. HyTrust DataControl과 결합되면, 서비스는 가상 머신 및 워크로드 데이터가 특정 지역, 클러스터 또는 {{site.data.keyword.CloudDataCent_notm}} 내의 ESXi 서버를 벗어나지 않도록 할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[HyTrust DataControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)</td>
       <td>HyTrust DataControl on {{site.data.keyword.cloud_notm}}는 워크로드를 해당 라이프사이클 동안 보호하기 위해 통합된 키 관리 기능을 포함한 강력한 암호화를 제공합니다. 이 서비스는 운영 체제 레벨 및 데이터 레벨 모두에서 암호화를 제공할 수 있으며, 이는 워크로드 내의 모든 디렉토리, 폴더 및 파일이 암호화되거나 복호화될 수 있음을 의미합니다.</td>
    </tr>
    <tr>
       <td>[HyTrust KeyControl on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)</td>
       <td>HyTrust KeyControl on {{site.data.keyword.cloud_notm}} 서비스는 암호화 키의 라이프사이클을 자동화 및 간소화하여 암호화된 워크로드의 관리를 간소화합니다. 이 서비스는 FIPS 140-2 준수 암호화를 사용하여 암호화 키를 규모에 맞게 쉽게 관리할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[IBM Cloud Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview)</td>
       <td>{{site.data.keyword.cloud_notm}} Private Hosted on vCenter Server on {{site.data.keyword.cloud_notm}} 서비스는 마이크로서비스 및 컨테이너의 기능을 {{site.data.keyword.cloud_notm}}의 VMware 환경에 제공합니다. 이 서비스를 사용하면 익숙한 동일 VMware 및 {{site.data.keyword.cloud_notm}} Private 운영 모델과 도구를 온프레미스에서 {{site.data.keyword.cloud_notm}}로 확장할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[IBM Spectrum Protect Plus on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)</td>
       <td>IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} 서비스는 가상 환경에서의 데이터 보호, 데이터 재사용 및 데이터 복구를 위한 효율적이고 스케일링 가능한 솔루션을 제공합니다. 사용자는 독립형 솔루션으로서 서비스를 구현하거나 장기 저장 및 데이터 통제를 위한 사본을 오프로드하기 위해 이를 IBM Spectrum Protect 환경과 통합할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[KMIP for VMware on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations)</td>
       <td>KMIP for VMware on {{site.data.keyword.cloud_notm}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware에서 사용되는 암호화 키를 관리하기 위해 고가용성 서비스를 제공합니다. 이 서비스는 고객이 암호화 키를 작성, 검색, 활성화, 취소 및 영구 삭제할 수 있도록 하는 런타임 기능을 제공합니다. 또한 클라이언트 인증 정보와 암호화 키 간의 연관을 유지보수하는 관리 기능도 제공합니다.</td>
    </tr>
    <tr>
       <td>[Veeam on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)</td>
       <td>Veeam on {{site.data.keyword.cloud_notm}} 서비스는 엔터프라이즈가 고가용성을 달성할 수 있도록 VMware 하이퍼바이저와 직접 원활하게 통합합니다. 이 서비스는 애플리케이션 및 데이터에 대한 복구 지점 및 시간 목표를 제공할 수 있습니다. 복구 지점 및 시간 목표는 구성이 완료된 후 15분 내에 제공될 수 있습니다. 이 서비스를 사용하여 Veeam 콘솔에서 인프라에 대한 모든 가상 머신의 백업 및 복원을 모두 직접 제어할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[VMware HCX on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)</td>
       <td>HCX on {{site.data.keyword.cloud_notm}} 서비스는 {{site.data.keyword.cloud_notm}}로 온프레미스 데이터 센터의 네트워크를 원활하게 확장할 수 있으며, 이를 통해 변환이나 변경 없이 {{site.data.keyword.cloud_notm}}에서 가상 머신(VM)을 마이그레이션할 수 있습니다.</td>
    </tr>
    <tr>
       <td>[Zerto on IBM Cloud](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)</td>
       <td>Zerto on {{site.data.keyword.cloud_notm}} 서비스는 {{site.data.keyword.cloud_notm}}의 VMware virtual 환경에서 데이터를 보호하고 복구하도록 배치 오퍼링으로 통합될 수 있는 복제 및 재해 복구 기능을 제공합니다.</td>
    </tr>
   </table>

## 1단계: IBM Cloud for VMware Solutions 콘솔에 액세스
{: #getting-started-step1}

{{site.data.keyword.vmwaresolutions_short}} 콘솔은 배치를 주문하고 관리하는 인터페이스입니다. 각 배치는 콘솔의 인스턴스로 관리됩니다. 콘솔은 {{site.data.keyword.cloud_notm}} 인프라 고객 포털에서 분리된 독립형 사용자 인터페이스입니다.

{{site.data.keyword.vmwaresolutions_short}} 콘솔에 액세스하려면 다음을 수행하십시오.
1. https://cloud.ibm.com/infrastructure/vmware-solutions/console로 이동하십시오.
2. **IBM ID**로 콘솔에 로그인하십시오.

## 2단계: 사용자 계정 및 설정 구성
{: #getting-started-step2}

인스턴스를 주문하기 전에 콘솔의 **설정** 페이지에 {{site.data.keyword.cloud_notm}} 인프라 계정의 사용자 이름 및 API 키를 입력해야 합니다.

사용자 계정 및 설정을 구성하는 방법에 대한 정보는 [사용자 계정 및 설정 관리](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount)를 참조하십시오.

## 3단계: 인스턴스 주문
{: #getting-started-step3}

콘솔에서 인스턴스로 관리되는 배치 오퍼링을 결정한 후 주문 프로세스를 시작하십시오.

인스턴스를 주문하는 방법에 대한 정보는 선택한 배치 오퍼링에 따라 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [vCenter Server with Hybridity Bundle 인스턴스 주문](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_orderinginstance)
* [새 vSphere 클러스터 주문](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [NetApp ONTAP Select 인스턴스 주문](/docs/services/vmwaresolutions/netapp?topic=vmware-solutions-np_orderinginstances)

## 4단계: 인스턴스 보기
{: #getting-started-step4}

**3단계**에서 인스턴스를 주문하면 인스턴스 배치가 자동으로 시작됩니다. 인스턴스 세부사항을 보고 배치 상태를 추적할 수 있습니다. 인스턴스 배치가 완료되면 인스턴스 세부사항 페이지에서 인스턴스 및 해당 추가 기능 서비스의 요약 및 자세한 정보를 볼 수 있습니다.

주문한 인스턴스를 보는 방법에 대한 정보는 다음 주제를 참조하십시오.
* [vCenter Server 인스턴스 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [vCenter Server with Hybridity Bundle 인스턴스 보기](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_viewinginstances)
* [NetApp ONTAP Select 인스턴스 보기](/docs/services/vmwaresolutions/services?topic=vmware-solutions-np_viewinginstances#np_viewinginstances)
